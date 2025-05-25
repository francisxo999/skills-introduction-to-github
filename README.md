# 🧾 Proyecto: Transformación Digital - Perfulandia SPA

Este repositorio contiene el desarrollo técnico del sistema basado en microservicios para la empresa Perfulandia SPA, como parte de la Evaluación Parcial 2 de la asignatura Desarrollo Full Stack I.

## 📦 Descripción General del Proyecto

Perfulandia SPA, una empresa chilena de perfumería con varias sucursales, enfrentaba problemas de rendimiento y escalabilidad con su antiguo sistema monolítico. El presente proyecto propone una solución basada en microservicios, permitiendo una mayor eficiencia, escalabilidad, tolerancia a fallos y facilidad de mantenimiento. Esta transformación digital mejora tanto la gestión interna como la experiencia del cliente final.

## 🧩 Arquitectura de Microservicios

El sistema está estructurado en microservicios independientes, cada uno responsable de una funcionalidad específica. Estos servicios se comunican entre sí usando APIs REST, lo que permite escalar y desplegar cada módulo de forma aislada.

### Microservicios Desarrollados

- `usuarioservice`: Gestiona usuarios, incluyendo creación, modificación, autenticación (login) y asignación de roles.
- `productoservice`: Administra el inventario y catálogo de productos disponibles para venta.
- `pedidoservice`: Maneja los pedidos de los clientes, desde su creación hasta la actualización de su estado.
- `notificacionservice`: Encargado del envío de notificaciones como confirmaciones de pedido o alertas por correo.
- `logisticaservice`: Se encarga de la gestión de envíos, planificación de rutas y seguimiento del estado de entrega de productos.

## 🛠️ Tecnologías Utilizadas

- Java 17
- Spring Boot
- Maven
- MySQL
- Postman
- Docker
- Kubernetes
- GitHub + GitHub Actions
- IntelliJ IDEA / Eclipse

## 🗄️ Configuración de Bases de Datos

Se utilizó MySQL como sistema de gestión de bases de datos. Cada microservicio tiene su propia base de datos para lograr un bajo acoplamiento y mayor independencia.

Ejemplo de configuración (application.properties):

spring.datasource.url=jdbc:mysql://localhost:3306/usuarios
spring.datasource.username=root
spring.datasource.password=1234
spring.jpa.hibernate.ddl-auto=update

Cada servicio define sus propias entidades. Por ejemplo:

- usuarioservice: Tabla usuarios con campos id, nombre, correo, rol.
- productoservice: Tabla productos con campos id, nombre, precio, stock.
- pedidoservice: Tabla pedidos con id, usuarioId, productos, estado.
- logisticaservice: Tabla envios con id, pedidoId, estado, direccion, fechaEntrega.

## 📮 Endpoints y Pruebas

Cada microservicio implementa endpoints REST para operaciones CRUD. Ejemplos:

### usuarioservice:
- GET /usuarios
- POST /usuarios
- GET /usuarios/{id}
- DELETE /usuarios/{id}

### productoservice:
- GET /productos
- POST /productos
- PUT /productos/{id}

### pedidoservice:
- GET /pedidos
- POST /pedidos
- PUT /pedidos/{id}/estado

### logisticaservice:
- GET /envios
- POST /envios
- PUT /envios/{id}/estado

### Ejemplos de pruebas con Postman:
1. Crear un nuevo usuario → POST /usuarios → Respuesta: 201 Created.
2. Obtener todos los productos → GET /productos → Lista de productos en formato JSON.
3. Crear un pedido y verificar llamada al servicio de productos para validar stock.
4. Crear un envío para un pedido y actualizar su estado → PUT /envios/{id}/estado.

## 🔁 CI/CD (Integración y Entrega Continua)

Se utilizó GitHub Actions para automatizar los flujos de integración y despliegue:

1. push al repositorio.
2. Ejecución de pruebas automatizadas.
3. Construcción de imagen Docker.
4. Despliegue en contenedores gestionados con Kubernetes.

## 🧑‍💻 Integrantes del Equipo

| Nombre               | Rol en el proyecto         | Servicio principal trabajado |
|----------------------|----------------------------|------------------------------|
| Mayckol Mardones     | Backend - Usuarios         | usuarioservice               |
| Carlos Moil          | Backend - Productos        | productoservice              |
| Francisco Vera       | CI/CD y Backend - Logística| logisticaservice             |

## 📂 Estructura del Repositorio

📦 perfulandia-microservices
├── usuarioservice
│   └── src / pom.xml
├── productoservice
│   └── src / pom.xml
├── pedidoservice
│   └── src / pom.xml
├── logisticaservice
│   └── src / pom.xml
├── notificacionservice
│   └── src / pom.xml
└── README.md

Cada microservicio contiene su propio archivo pom.xml, configuración de base de datos, controladores REST, entidades y repositorios.

## 👥 Colaboración en GitHub

El equipo trabajó utilizando ramas específicas para cada microservicio:
- main: rama estable.
- develop: rama de desarrollo general.
- usuarioservice, productoservice, pedidoservice, logisticaservice: ramas específicas por microservicio.

Se realizaron commits frecuentes documentando avances, y se realizaron pull requests revisados antes de integrarse a develop y luego a main.

## 📈 Lecciones Aprendidas

Durante el desarrollo del proyecto aprendimos:

- Cómo diseñar e implementar una arquitectura basada en microservicios desde cero.
- Uso de herramientas modernas como Docker, Kubernetes y GitHub Actions para CI/CD.
- La importancia del trabajo colaborativo y control de versiones en equipo.
- Pruebas efectivas de endpoints RESTful con Postman.

