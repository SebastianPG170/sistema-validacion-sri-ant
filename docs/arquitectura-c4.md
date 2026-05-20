# Arquitectura C4

## Nivel 1 - Diagrama de Contexto

En el nivel de contexto se representa al usuario, el sistema principal y los sistemas externos con los que interactúa.

Elementos principales:

- Usuario
- Sistema Web de Validación Tributaria y Vehicular
- SRI - Servicios REST
- ANT - Consulta Web de Citaciones

El usuario ingresa su correo electrónico, RUC/cédula y placa del vehículo.  
El sistema se comunica con el SRI para validar información tributaria y vehicular.  
También se comunica con la ANT para consultar los puntos de licencia.

## Nivel 2 - Diagrama de Contenedores

El sistema se divide en los siguientes contenedores:

- Frontend Web
- Backend/API Gateway
- Microservicio SRI
- Microservicio Vehicular
- Microservicio ANT
- Base de Datos Principal
- Redis Cache

El Frontend Web permite el ingreso de datos.  
El Backend/API Gateway coordina las solicitudes hacia los microservicios.  
Los microservicios se encargan de consultar los sistemas externos y devolver la información al usuario.

## Nivel 3 - Diagrama de Componentes del Microservicio ANT

El Microservicio ANT se divide en:

- Controlador de Licencia
- Servicio de Consulta ANT
- Circuit Breaker
- Cliente Web ANT
- Gestor de Caché

Este nivel permite explicar cómo se maneja la baja disponibilidad de la ANT mediante caché y Circuit Breaker.

## Patrón de disponibilidad

Se aplica el patrón Cache-Aside junto con Circuit Breaker.

Cuando la ANT responde correctamente, los datos se guardan en Redis Cache.  
Cuando la ANT falla, el sistema recupera la última respuesta válida desde Redis Cache.  
El Circuit Breaker evita llamadas repetidas hacia la ANT cuando el servicio externo presenta fallos continuos.
