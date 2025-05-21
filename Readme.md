# Proyecto de Monitorización y Análisis de Datos IoT

## Descripción

Este proyecto tiene como objetivo el diseño e implementación de un sistema completo de adquisición, visualización, procesamiento y análisis de datos de sensores IoT. Incluye suscripción a entidades, generación de datos, paneles de control en **Grafana** y **Power BI**, y una ETL para alimentar un **Data Warehouse** (En mi caso he utilizado un archivo .csv).

---

## 🧩 Fase 1

### 1. Definición de Entidades

Se han definido tres entidades principales, cada una con múltiples atributos para representar distintos sensores o variables a monitorear.

### 2. Suscripción a Entidades

Se han creado suscripciones para recibir notificaciones en tiempo real sobre cambios en los atributos de cada entidad.

### 3. Generación de Datos

Se han generado 400 datos por atributo, por cada entidad, dentro del rango de fechas:
📅 **01/03/2025 - 30/04/2025**

---

## 📊 Visualización con Grafana

Se ha diseñado un panel de control interactivo con las siguientes características:

- ✅ **4 visualizaciones** representando diferentes atributos o KPIs
- 🎚️ **1 variable** para filtrar dinámicamente las visualizaciones (1 variable por visualización)
---

## 🔁 Proceso ETL y Almacenamiento

Una ETL personalizada ha sido desarrollada para calcular y almacenar en un .csv los siguientes valores por día y por atributo:

- 📈 Valor **máximo** del día  
- 📉 Valor **mínimo** del día  
- 📊 Valor **medio** del día  

---

## 📈 Cuadro de Mando en Power BI

Se ha creado un dashboard con:

- 📊 **2 visualizaciones** relevantes de tendencias y KPIs
- 🧮 **2 filtros** para explorar los datos por fechas y entidades

---

## 📄 Documentación

Este repositorio incluye un documento explicativo que detalla:

- Diseño de las entidades y atributos
- Arquitectura del sistema
- Proceso de generación y suscripción de datos
- Diseño del ETL y estructuras del Data Warehouse
- Desarrollo de los dashboards en Grafana y Power BI

---

## 📁 Estructura del Proyecto

├── data/ # Scripts y archivos de generación de datos

├── etl/ # Código de la ETL

├── grafana/ # Configuración del dashboard

├── powerbi/ # Reportes y visualizaciones en Power BI

├── docs/ # Documentación técnica y de diseño

└── README.md # Este archivo


---

## 🚀 Tecnologías Usadas

- **Grafana** para visualización en tiempo real
- **Power BI** para análisis de negocio
- **Python** para la ETL y generación de datos
- **SQL / Data Warehouse** para almacenamiento analítico
- **NGSI-LD / IoT Broker** para suscripciones

---
