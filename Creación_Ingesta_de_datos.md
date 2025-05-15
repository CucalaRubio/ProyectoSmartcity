```python
import requests
from datetime import datetime, timedelta

ORION_URL = "http://localhost:1026/v2/entities"
HEADERS = {"Content-Type": "application/json"}

# Sensores y sus atributos
entities = {
    "sensor001": ["Temperatura", "humidity"],
    "sensor002": ["CO2"],
    "sensor003": ["Ph", "Temperatura", "cloro"]
}

# Fechas
start_date = datetime(2025, 3, 1)
end_date = datetime(2025, 4, 30)
total_points = 400
interval = (end_date - start_date) / total_points  # tiempo entre cada punto

for entity_id, attributes in entities.items():
    timestamp = start_date
    for i in range(total_points):
        data = {}
        for attr in attributes:
            value = 10 + (i % 50)  # valor de ejemplo: entre 10 y 59
            data[attr] = {
                "type": "Number",
                "value": value,
                "metadata": {
                    "timestamp": {
                        "type": "DateTime",
                        "value": timestamp.isoformat() + "Z"
                    }
                }
            }

        url = f"{ORION_URL}/{entity_id}/attrs"
        response = requests.post(url, headers=HEADERS, json=data)
        print(f"{entity_id} | Registro {i+1}/{total_points} | Status: {response.status_code}")
        timestamp += interval

```
