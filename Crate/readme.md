# 📦 CrateDB - Almacenamiento de Datos de Sensores IoT

Este componente del proyecto está centrado en el uso de **CrateDB** como base de datos distribuida para almacenar y consultar datos generados por sensores IoT.

---

## 📁 Tablas en CrateDB

A continuación, se listan las principales tablas utilizadas:

### 1. `etsensorco2`
- **Descripción**: Datos de sensores de dióxido de carbono (CO₂).
- **Registros**: 400
- **Tamaño**: ~154.8 KiB

### 2. `etsensorqualitywater`
- **Descripción**: Datos de sensores de calidad del agua.
- **Registros**: 400
- **Tamaño**: ~313.3 KiB

### 3. `etsensortemperaturas`
- **Descripción**: Datos de sensores de temperatura y humedad ambiental.
- **Registros**: 400
- **Tamaño**: ~211.6 KiB

### 4. `md_ets_metadata`
- **Descripción**: Metadatos de las entidades/sensores registrados.
- **Registros**: 3
- **Tamaño**: ~25.1 KiB

---

## 🧠 Características Técnicas

- Cada tabla contiene **400 registros**, simulados en el rango de fechas del **01/03/2025 al 30/04/2025**.
- Todas las tablas están fragmentadas en **4 shards** con **2 réplicas** para alta disponibilidad.
- Datos insertados a través de un proceso automatizado (ETL o simulador de datos).

![Dashboard Preview](Captura%20desde%202025-05-20%2023-12-54.png)

