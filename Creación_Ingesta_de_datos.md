import requests
import random
from datetime import datetime, timedelta

# Configuración
ORION_URL = "http://localhost:1026/v2/op/update"
HEADERS = {
    "Content-Type": "application/json",
    "Fiware-Service": "default",
    "Fiware-ServicePath": "/"
}

# Entidades
entities = [
    {"id": "sensor001", "type": "Sensor", "attrs": ["humidity", "temperatura"]},
    {"id": "sensor002", "type": "Sensor", "attrs": ["C02"]},
    {"id": "sensor003", "type": "Sensor", "attrs": ["Ph", "cloro", "temperatura"]}
]

# Rango de fechas
start_date = datetime(2025, 3, 1)
end_date = datetime(2025, 4, 30)
total_points = 400
time_step = (end_date - start_date) / total_points

# Generar y cargar datos
for entity in entities:
    for i in range(total_points):
        current_time = (start_date + i * time_step).isoformat() + "Z"

        # Generar valores aleatorios por atributo
        payload = {
            "actionType": "append",
            "entities": [
                {
                    "id": entity["id"],
                    "type": entity["type"],
                }
            ]
        }

        # Atributos específicos de la entidad
        for attr in entity["attrs"]:
            if attr == "humidity":
                value = round(random.uniform(30, 90), 2)
            elif attr == "temperatura":
                value = round(random.uniform(15, 35), 2)
            elif attr == "C02":
                value = random.randint(300, 1000)
            elif attr == "Ph":
                value = round(random.uniform(6.5, 8.5), 2)
            elif attr == "cloro":
                value = round(random.uniform(0.5, 2.5), 2)

            # Añadir atributo y timestamp
            payload["entities"][0][attr] = {
                "type": "Number",
                "value": value,
                "metadata": {
                    "timestamp": {
                        "type": "DateTime",
                        "value": current_time
                    }
                }
            }

        # Enviar la actualización a Orion
        response = requests.post(ORION_URL, json=payload, headers=HEADERS)
        print(f"Entidad {entity['id']} ({i+1}/400) - Status: {response.status_code}")
