# Sistema Web de Validación Tributaria y Vehicular

Este proyecto presenta el diseño arquitectónico de un sistema web que permite validar información tributaria, vehicular y puntos de licencia de una persona natural en Ecuador.

## Funcionalidades principales

- Ingreso de correo electrónico, RUC/cédula y placa del vehículo.
- Validación de contribuyente mediante servicios REST del SRI.
- Consulta de información de persona natural.
- Consulta de información vehicular por placa.
- Consulta de puntos de licencia mediante la web de la ANT.
- Uso de caché para almacenar respuestas válidas de la ANT.
- Aplicación del patrón Circuit Breaker para manejar la baja disponibilidad de la ANT.

## Arquitectura C4

La arquitectura fue modelada usando C4 en IcePanel:

- Nivel 1: Diagrama de contexto.
- Nivel 2: Diagrama de contenedores.
- Nivel 3: Diagrama de componentes del Microservicio ANT.

## Tecnologías propuestas

- Frontend Web: React
- Backend/API Gateway: Spring Boot
- Microservicios: Spring Boot
- Base de Datos Principal: PostgreSQL
- Caché: Redis
- Integraciones externas: SRI Servicios REST y ANT Consulta Web

## Patrón aplicado

Para la integración con la ANT se utiliza el patrón Cache-Aside junto con Circuit Breaker.

Cuando la ANT responde correctamente, la información se almacena en Redis Cache.  
Si la ANT no está disponible, el sistema recupera la última respuesta válida desde caché.

## Estructura propuesta

```text
sistema-validacion-sri-ant/
│
├── README.md
├── docs/
│   └── arquitectura-c4.md
│
├── frontend-web/
│   └── README.md
│
├── backend-api-gateway/
│   └── README.md
│
├── microservicio-sri/
│   └── README.md
│
├── microservicio-vehicular/
│   └── README.md
│
└── microservicio-ant/
    └── README.md

Link de IcePanel: https://s.icepanel.io/id7lbjGiSY1FdZ/u1I8
