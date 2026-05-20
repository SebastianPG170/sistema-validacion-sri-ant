# Microservicio ANT

Microservicio propuesto en Spring Boot.

Responsabilidad:

- Consultar puntos de licencia por cédula.
- Integrarse con la web de la ANT.
- Aplicar Circuit Breaker para manejar fallos del servicio externo.
- Guardar respuestas válidas en Redis Cache.
- Recuperar información desde caché cuando la ANT no esté disponible.
