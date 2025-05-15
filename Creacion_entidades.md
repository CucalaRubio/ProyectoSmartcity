curl -X POST http://localhost:1026/v2/entities -H 'Content-Type: application/json' -d '{"id": "sensor001", "type": "Sensor", "humidity": {"value": 55, "type": "Number"}, 
"Temperatura": { "type": "Number", "value": 30}
  }'

  curl -X POST   http://localhost:1026/v2/entities   -H 'Content-Type: application/json'   -d '{
    "id": "sensor002",
    "type": "Sensor",
    "C02": {
      "value": 55,
      "type": "Number"
    } 
  }'

  curl -X POST   http://localhost:1026/v2/entities   -H 'Content-Type: application/json'   -d '{
    "id": "sensor003",
    "type": "Sensor",
    "Ph": {
      "value": 20,
      "type": "Number"
    }, "Temperatura": {"type": "Number", "value": 55}, "cloro": {"type": "Number", "value": 31}
  }'


""""""""
*Suscripción

curl -X POST http://localhost:1026/v2/subscriptions \
  -H "Content-Type: application/json" \
  -d '{
    "description": "Suscripción a cambios en sensores",
    "subject": {
      "entities": [
        {
          "idPattern": "sensor*",
          "type": "Sensor"
        }
      ]
    },
    "notification": {
      "http": {
        "url": "http://quantumleap:8668/v2/notify"
      },
      "attrs": [
        "Temperatura", "humidity", "CO2", "Ph", "cloro"
      ],
      "metadata": ["dateCreated", "dateModified", "timestamp"]
    },
    "throttling": 1
  }'

