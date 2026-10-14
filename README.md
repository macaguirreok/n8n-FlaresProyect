# ☀️ Solar Flare Alert System — NASA API

Sistema de automatización que consulta datos de llamaradas solares mediante la API DONKI de la NASA y envía alertas por correo electrónico cuando detecta eventos de clase **M o X**, dos categorías de llamaradas solares de alta intensidad.

## 📌 Descripción del proyecto

Las llamaradas solares son explosiones de energía en la atmósfera del Sol que emiten radiación electromagnética, incluidos los rayos X. Se clasifican según la intensidad de sus emisiones de rayos X, en categorías como A, B, C, M y X.

Las llamaradas de clase M y X pueden provocar efectos en el entorno espacial y en sistemas tecnológicos terrestres, como alteraciones en las comunicaciones por radio. Las de clase X corresponden a la categoría de mayor intensidad.

Este proyecto utiliza la API **DONKI (Space Weather Database Of Notifications, Knowledge, Information)** para consultar información sobre llamaradas solares y automatizar el envío de notificaciones por correo electrónico según su clasificación.

El objetivo es reducir la necesidad de revisar manualmente los datos y facilitar el seguimiento de eventos solares relevantes mediante un flujo automatizado.

## 🎯 Objetivos

- Consultar automáticamente información sobre llamaradas solares.
- Obtener datos de eventos registrados en la API DONKI.
- Evaluar la clasificación de cada llamarada.
- Enviar notificaciones por correo electrónico para los eventos de clase M y X.
- Practicar la integración de APIs, el procesamiento de datos y la automatización de tareas mediante n8n.

## 🛠️ Tecnologías utilizadas

- **n8n:** creación y ejecución del flujo de automatización.
- **NASA DONKI API:** consulta de datos sobre llamaradas solares.
- **HTTP Request:** realización de solicitudes HTTP a la API.
- **IF:** evaluación de condiciones según la clasificación del evento.
- **Send Email:** envío automatizado de notificaciones por correo electrónico.

## 🔄 Flujo de automatización

El workflow está compuesto por los siguientes nodos:

1. **Schedule Trigger:** inicia el flujo de acuerdo con la programación configurada.
2. **HTTP Request:** consulta la API de llamaradas solares.
3. **IF:** evalúa la clasificación de los eventos y filtra aquellos de clase M o X.
4. **Send Email:** envía una notificación por cada evento que cumple la condición, utilizando la información disponible de la llamarada.

### Diagrama del proceso

```text
Schedule Trigger
       |
       v
  HTTP Request
       |
       v
   IF: Clase M o X
       |
       +---- True ----> Send Email
       |
       +---- False ---> Sin notificación
```

## 📊 Información de las alertas

Las notificaciones pueden incluir los siguientes datos del evento, cuando están disponibles:

- Identificador de la llamarada (`flrID`).
- Fecha y hora de inicio (`beginTime`).
- Momento de máxima intensidad (`peakTime`).
- Fecha y hora de finalización (`endTime`).
- Clasificación (`classType`).
- Ubicación de origen (`sourceLocation`).
- Número de región activa (`activeRegionNum`).
- Enlace al registro del evento (`link`).

## 🌐 Fuente de datos

**NASA CCMC — DONKI API**

Endpoint utilizado:

`https://ccmc.gsfc.nasa.gov/DONKI-API/get/FLR`

Documentación y recursos:

- [NASA Space Weather Database Of Notifications, Knowledge, Information (DONKI)](https://ccmc.gsfc.nasa.gov/tools/DONKI/)
- [NASA Open APIs](https://api.nasa.gov/)

## ⚙️ Configuración

Para ejecutar el workflow:

1. Contar con una instancia de n8n.
2. Configurar el nodo **Schedule Trigger** con la frecuencia deseada.
3. Configurar el nodo **HTTP Request** para consultar el endpoint de DONKI.
4. Definir en el nodo **IF** la condición que permite continuar únicamente a los eventos de clase M o X.
5. Configurar el nodo **Send Email** con las credenciales del servicio de correo y los campos que se incluirán en el mensaje.
6. Ejecutar pruebas y verificar que los eventos que cumplen la condición generen las notificaciones esperadas.

**Importante:** las credenciales del correo y cualquier otra información sensible deben mantenerse fuera del repositorio público.

## 🧠 Aprendizajes

Durante el desarrollo de este proyecto se trabajó con:

- Consumo de APIs mediante solicitudes HTTP.
- Interpretación de respuestas con datos estructurados.
- Evaluación de condiciones y filtrado de información.
- Automatización de tareas programadas.
- Integración de servicios para el envío de notificaciones.
- Diseño de flujos orientados a reducir tareas manuales.

## 🚀 Posibles mejoras futuras

- Evitar el envío de alertas duplicadas en ejecuciones sucesivas.
- Añadir filtros por fecha, intensidad u otros criterios.

---

**Proyecto personal de automatización desarrollado con n8n e integrado con la API DONKI de la NASA.**
