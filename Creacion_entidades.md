curl -X POST http://localhost:1026/v2/entities -H 'Content-Type: application/json' -d '{"id": "sensor001", "type": "Sensor", "humidity": { "value": 55, "type": "Number", "metadata": {
    "timestamp": {
      "type": "DateTime",
      "value": "2025-05-15T13:00:00Z"
    }
  } }, "Temperatura": { "type": "Number", "value": 30, "metadata": {
    "timestamp": {
      "type": "DateTime",
      "value": "2025-05-15T13:00:00Z"
        }
      } 
    } 
}'


curl -X POST   http://localhost:1026/v2/entities   -H 'Content-Type: application/json'   -d '{
  "id": "sensor002",
  "type": "Sensor",
  "CO2": {
    "value": 55,
    "type": "Number", "metadata": {
    "timestamp": {
      "type": "DateTime",
      "value": "2025-05-15T13:00:00Z"
        }
      }
  } 
}'

curl -X POST   http://localhost:1026/v2/entities   -H 'Content-Type: application/json'   -d '{
  "id": "sensor003",
  "type": "Sensor",
  "Ph": {
    "value": 20,
    "type": "Number", "metadata": {
    "timestamp": {
      "type": "DateTime",
      "value": "2025-05-15T13:00:00Z"
    }
  }
  }, 
  "Temperatura": {
    "type": "Number", 
    "value": 55, "metadata": {
    "timestamp": {
      "type": "DateTime",
      "value": "2025-05-15T13:00:00Z"
    }
  }
  }, 
  "cloro": {
    "type": "Number", 
    "value": 31, 
    "metadata": {
        "timestamp": {
          "type": "DateTime",
          "value": "2025-05-15T13:00:00Z"
        }
      }
  }
}'


**Suscripción**

curl -X POST http://localhost:1026/v2/subscriptions -H "Content-Type: application/json" \
  -d '{
    "description": "Suscripción a sensores con metadata.timestamp",
    "subject": {
      "entities": [
        { "idPattern": ".*", "type": "Sensor" }
      ]
    },
    "notification": {
      "http": {
        "url": "http://quantumleap:8668/v2/notify"
      },
      "attrs": ["Temperatura", "humidity", "CO2", "Ph", "cloro"],
      "metadata": ["timestamp"]
    },
    "throttling": 1
  }'

