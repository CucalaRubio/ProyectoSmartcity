import requests
import datetime
import random

HEADERS = {
    "Content-Type": "application/json",
    "Fiware-Service": "smartcity",
    "Fiware-ServicePath": "/"
}

URL = "http://localhost:1026/v2/entities/{}/attrs"

def send_value(entity_id, attr_name, value):
    payload = {
        attr_name: {
            "value": value,
            "type": "Number"
        }
    }
    r = requests.post(URL.format(entity_id), json=payload, headers=HEADERS)
    if not r.ok:
        print(f"Error [{r.status_code}]: {r.text}")

start = datetime.datetime(2025, 3, 1)
end = datetime.datetime(2025, 4, 30)
delta = (end - start) / 400

for i in range(400):
    ts = start + i * delta

    # Sensor 001: humedad y temperatura
    send_value("sensor001", "humidity", round(random.uniform(30, 70), 2))
    send_value("sensor001", "temperatura", round(random.uniform(20, 40), 2))

    # Sensor 002: CO2
    send_value("sensor002", "C02", round(random.uniform(300, 600), 2))

    # Sensor 003: Ph, cloro, temperatura
    send_value("sensor003", "Ph", round(random.uniform(6.5, 8.5), 2))
    send_value("sensor003", "cloro", round(random.uniform(0.5, 3.0), 2))
    send_value("sensor003", "temperatura", round(random.uniform(20, 35), 2))
