# Orion Context Broker: Entidades y Suscripciones

Este README proporciona los comandos `curl` necesarios para registrar entidades y crear suscripciones en **Orion Context Broker**. Estos datos pueden ser utilizados por otras componentes como **QuantumLeap** para análisis históricos y visualización.

> **Requisitos previos**:
> - Orion Context Broker corriendo en `http://localhost:1026`
> - QuantumLeap disponible en `http://quantumleap:8668/v2/notify`

---

## 📦 1. Creación de Entidades

### 🌡️ Sensor 001 - Temperatura y Humedad

```bash
curl -X POST http://localhost:1026/v2/entities -H 'Content-Type: application/json' -d '{
  "id": "sensor001",
  "type": "SensorTemperaturas",
  "humidity": {
    "value": 55,
    "type": "Number",
    "metadata": {
      "timestamp": {
        "type": "DateTime",
        "value": "2025-03-1T13:00:00Z"
      }
    }
  },
  "Temperatura": {
    "type": "Number",
    "value": 30,
    "metadata": {
      "timestamp": {
        "type": "DateTime",
        "value": "2025-03-1T13:00:00Z"
      }
    }
  }
}'
```

### 🏭 Sensor 002 - CO2

```bash
curl -X POST http://localhost:1026/v2/entities -H 'Content-Type: application/json' -d '{
  "id": "sensor002",
  "type": "SensorCO2",
  "CO2": {
    "value": 55,
    "type": "Number",
    "metadata": {
      "timestamp": {
        "type": "DateTime",
        "value": "2025-03-1T13:00:00Z"
      }
    }
  }
}'
```

### 💧 Sensor 003 - Calidad del Agua

```bash
curl -X POST http://localhost:1026/v2/entities -H 'Content-Type: application/json' -d '{
  "id": "sensor003",
  "type": "SensorQualityWater",
  "Ph": {
    "value": 20,
    "type": "Number",
    "metadata": {
      "timestamp": {
        "type": "DateTime",
        "value": "2025-03-1T13:00:00Z"
      }
    }
  },
  "Temperatura": {
    "type": "Number",
    "value": 55,
    "metadata": {
      "timestamp": {
        "type": "DateTime",
        "value": "2025-03-1T13:00:00Z"
      }
    }
  },
  "cloro": {
    "type": "Number",
    "value": 31,
    "metadata": {
      "timestamp": {
        "type": "DateTime",
        "value": "2025-03-1T13:00:00Z"
      }
    }
  }
}'
```

---

## 🔔 2. Suscripciones


> Las suscripciones incluyen:
> - `subject`: qué entidades observar
> - `notification`: a dónde enviar las actualizaciones
> - `metadata`: datos adicionales como `timestamp`

---

### 🔔 Sensor 001 - Temperatura y Humedad

```bash
curl -X POST http://localhost:1026/v2/subscriptions -H "Content-Type: application/json" -d '{
  "description": "Suscripción a sensores con metadata.timestamp",
  "subject": {
    "entities": [
      { "idPattern": "sensor001", "type": "SensorTemperaturas" }
    ]
  },
  "notification": {
    "http": {
      "url": "http://quantumleap:8668/v2/notify"
    },
    "attrs": ["Temperatura", "humidity"],
    "metadata": ["timestamp"]
  },
  "throttling": 1
}'
```

### 🔔 Sensor 002 - CO2

```bash
curl -X POST http://localhost:1026/v2/subscriptions -H "Content-Type: application/json" -d '{
  "description": "Suscripción a sensores con metadata.timestamp",
  "subject": {
    "entities": [
      { "idPattern": "sensor002", "type": "SensorCO2" }
    ]
  },
  "notification": {
    "http": {
      "url": "http://quantumleap:8668/v2/notify"
    },
    "attrs": ["CO2"],
    "metadata": ["timestamp"]
  },
  "throttling": 1
}'
```

### 🔔 Sensor 003 - Calidad del Agua

```bash
curl -X POST http://localhost:1026/v2/subscriptions -H "Content-Type: application/json" -d '{
  "description": "Suscripción a sensores con metadata.timestamp",
  "subject": {
    "entities": [
      { "idPattern": "sensor003", "type": "SensorQualityWater" }
    ]
  },
  "notification": {
    "http": {
      "url": "http://quantumleap:8668/v2/notify"
    },
    "attrs": ["Temperatura", "Ph", "cloro"],
    "metadata": ["timestamp"]
  },
  "throttling": 1
}'
```

---

## ✅ Verificación

Puedes verificar las entidades creadas con:

```bash
curl http://localhost:1026/v2/entities
```

Y las suscripciones activas con:

```bash
curl http://localhost:1026/v2/subscriptions
```
