# Dashboard de Sensores de Temperatura

Este proyecto presenta un dashboard interactivo desarrollado en **Power BI** para visualizar y analizar datos de temperatura recogidos por sensores IoT.

## 📊 Descripción General

El dashboard muestra información sobre las mediciones de temperatura registradas por distintos sensores, facilitando la comparación y seguimiento de los datos a lo largo del tiempo.

### Componentes del Dashboard:

- **KPI Principal (Parte superior):**
  - **Suma de máximos:** Muestra la suma total de los valores máximos de los atributos registrados por los sensores seleccionados.

- **Gráfico de Barras (Izquierda):**
  - **Suma de mínimos por sensor y atributo:** Compara la suma de los valores mínimos de los atributos registrados por cada sensor (`sensor001`, `sensor002`, `sensor003`). En el caso de la imagen son los sensores001 y senores003

- **Gráfico de Líneas (Derecha):**
  - **Histórico de mediciones:** Muestra la evolución de las mediciones medias de los atributos por sensor a lo largo del tiempo (marzo y abril de 2025).

- **Filtros:**
  - **Medidas:** Permite seleccionar el tipo de medida a visualizar (actualmente se muestra "temperatura").
  - **Sensores:** Permite seleccionar uno o varios sensores para comparar sus datos.

## 🧪 Datos

Los datos utilizados provienen de sensores identificados como `sensor001` y `sensor003`, que reportan medidas de temperatura. Se espera que los datos incluyan campos como:

- `entity_id` (ID del sensor)
- `fecha` (fecha y hora de la medición)
- `temperatura` (valor numérico)
- `min`, `max`, `media` (valores calculados para cada sensor)

## 🚀 Objetivos

- Monitorizar los diferentes atributos medidos por distintos sensores.
- Comparar tendencias y comportamientos por sensor.
- Identificar patrones y posibles anomalías en las mediciones.

## 📌 Requisitos

- Power BI Desktop (versión reciente)
- Dataset en formato CSV, Excel o conexión a base de datos en tiempo real

## 📷 Vista previa

![Dashboard Preview](Captura%20de%20pantalla%202025-05-21%20132905.png)

