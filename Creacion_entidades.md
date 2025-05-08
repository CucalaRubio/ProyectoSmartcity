curl -X POST \
  http://localhost:1026/v2/entities \
  -H 'Content-Type: application/json' \
  -d '{
    "id": "sensor002",
    "type": "TemperaturaSensor",
    "humidity": {
      "value": 55,
      "type": "Number"
    },
    "temperatura": {
      "type": "Number",
      "value": "30"
    }
  }'

  curl -X POST   http://localhost:1026/v2/entities   -H 'Content-Type: application/json'   -d '{
    "id": "sensor001",
    "type": "C02Sensor",
    "C02": {
      "value": 55,
      "type": "Number"
    } 
  }'

  curl -X POST   http://localhost:1026/v2/entities   -H 'Content-Type: application/json'   -d '{
    "id": "sensor003",
    "type": "WaterQualitySensor",
    "Ph": {
      "value": 20,
      "type": "Number"
    }, "Temperatura": {"type": "Number", "value": "55"}, "Cloro": {"type": "Number", "value": "31"}
  }'
