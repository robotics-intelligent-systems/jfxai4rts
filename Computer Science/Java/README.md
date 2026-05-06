# Reto de Codificación

## Posición: 
Backend Java Developer (Spring Boot + MySQL)

## Título: 
Sistema de Gestión de Candidatos en Proceso de Selección y Contratación

## Contexto:
Una empresa está desarrollando un sistema de gestión de clientes para  ofrecer una mejor experiencia a sus usuarios. Se requiere un microservicio  que permita manejar el registro, consulta y análisis de datos de clientes utilizando MySQL como base de datos.
El  objetivo es que este servicio sea escalable, seguro y cumpla con las mejores prácticas de desarrollo de software.

## Requerimientos:
- Crear nuevos clientes mediante un endpoint que permita registrar nombre, apellido, edad y fecha de nacimiento.
- Consultar un conjunto de métricas sobre los clientes existentes, como el promedio de edad y la desviación estándar de las edades.
- Listar todos los clientes registrados con sus datos completos y un cálculo derivado, como una fecha estimada para un evento futuro basado en los datos del cliente (por ejemplo, esperanza de vida).

## Puntos adicionales:
- Diseña el servicio utilizando un enfoque basado en buenas prácticas de diseño y patrones de arquitectura. Se espera una separación clara de responsabilidades entre las capas del sistema.
- Documenta la API con herramientas estándar de la industria para facilitar su consumo.
- Implementa un modelo de persistencia para almacenar los datos de los clientes.
- Aplica principios de seguridad para garantizar que solo usuarios autorizados puedan interactuar con el servicio.
- Diseña el sistema considerando su despliegue en un entorno en la nube.
- El servicio debe manejar adecuadamente las excepciones y devolver mensajes claros a los consumidores de la API, usando adecuadamente los HTTP Codes para esto (500, 401, 422, etc.).
- Se debe incluir un conjunto de pruebas que validen la funcionalidad implementada.
- Implementa un mecanismo que permita registrar y monitorear la actividad del servicio.
- Diseña el servicio de manera que pueda adaptarse a un aumento en el volumen de datos o peticiones.

## Recomendaciones:
- El microservicio debe ser funcional y cumplir con los requerimientos mencionados.
- Debe ser posible entender el diseño y las decisiones tomadas a través del código, documentación o comentarios.
- Se valorará el uso de patrones de diseño (por ejemplo, Factory, Builder, o  Repository) y patrones de arquitectura (por ejemplo, RESTful o event driven).
- La implementación debe ser eficiente y seguir las mejores prácticas para  aplicaciones en Java y Spring Boot
- Utiliza Spring Data JPA, Spring Security y Flyway.
- Usa un sistema de construcción como Maven o Gradle.
- Incluye instrucciones claras sobre cómo configurar y ejecutar la aplicación.
- Considera la modularidad y reutilización del código.

## Entregables:
- Repositorio de GitHub con el código fuente.
- URL de la API desplegada en AWS, Azure o GCP, brindando acceso como colaboradores para revisar código desplegado.
- Documentación de los endpoints en Swagger
- Una colección en Postman con las llamadas a cada una de las APIs, incluyendo un par de casos ya grabados (uno con HTTP Status 200, exitoso y uno con 500, para caso de error, 422 para errores de negocio) por cada endpoint.

## Opcionales:
- Implementar una cola de mensajería para manejar procesos asincrónicos relacionados con los clientes.
- Exponer métricas en un formato compatible con sistemas de monitoreo