
# Proyecto: Transformación Digital - Perfulandia SPA

Este repositorio contiene el desarrollo técnico del sistema basado en microservicios para la empresa Perfulandia SPA, como parte de la Evaluación Parcial 2 de la asignatura Desarrollo Full Stack I.

## Descripción General del Proyecto

Perfulandia SPA, una empresa chilena de perfumería con varias sucursales, enfrentaba problemas de rendimiento y escalabilidad con su antiguo sistema monolítico. El presente proyecto propone una solución basada en microservicios, permitiendo una mayor eficiencia, escalabilidad, tolerancia a fallos y facilidad de mantenimiento. Esta transformación digital mejora tanto la gestión interna como la experiencia del cliente final.

## Arquitectura de Microservicios

El sistema está estructurado en microservicios independientes, cada uno responsable de una funcionalidad específica. Estos servicios se comunican entre sí usando APIs REST, lo que permite escalar y desplegar cada módulo de forma aislada.

### Microservicios Desarrollados

- usuarioservice: Gestiona usuarios, incluyendo creación, modificación, autenticación y roles.
- productoservice: Administra el inventario y catálogo de productos disponibles para la venta.
- pedidoservice: Maneja los pedidos de los clientes, desde su creación hasta la actualización de su estado.
- logisticaservice: Se encarga de la gestión de envíos, planificación de rutas y seguimiento del estado de entrega de productos.
- carritoservice: Permite la gestión de carritos de compra por parte de los clientes.

## Tecnologías Utilizadas

- Java 17
- Spring Boot
- Laragon (Base de Datos MySQL)
- Postman
- GitHub
- IntelliJ IDEA

## Configuración de Bases de Datos

Se utilizó MySQL como sistema de gestión de bases de datos. Cada microservicio tiene su propia base de datos para lograr un bajo acoplamiento y mayor independencia.

Cada servicio define sus propias entidades. Por ejemplo:

- usuarioservice: Tabla `usuarios` con campos como id, nombre, correo, rol, etc.
- productoservice: Tabla `productos` con campos como id, nombre, precio, stock.
- pedidoservice: Tabla `pedidos` con campos como id, usuarioId, productos, estado.
- logisticaservice: Tabla `envios` con campos como id, pedidoId, estado, direccion, fechaEntrega.
- carritoservice: Tabla `carritos` con campos como id, usuarioId, productos, total.

## Endpoints y Pruebas

Cada microservicio implementa endpoints REST para operaciones CRUD. Ejemplos:

usuarioservice:
- GET /usuarios
- POST /usuarios
- GET /usuarios/{id}
- DELETE /usuarios/{id}

productoservice:
- GET /productos
- POST /productos
- PUT /productos/{id}

pedidoservice:
- GET /pedidos
- POST /pedidos
- PUT /pedidos/{id}/estado

logisticaservice:
- GET /envios
- POST /envios
- PUT /envios/{id}/estado

carritoservice:
- GET /carrito
- POST /carrito
- PUT /carrito/{id}
- DELETE /carrito/{id}

## CI/CD (Integración y Entrega Continua)

Se utilizó GitHub Actions para automatizar los flujos de integración y despliegue:

1. Push al repositorio.
2. Ejecución de pruebas automatizadas.
3. Conexión de los microservicios mediante pull requests.
4. Prueba del sistema en su conjunto.

## Integrantes del Equipo

| Nombre              | Rol en el proyecto                     | Servicio principal trabajado |
|---------------------|----------------------------------------|------------------------------|
| Carlos Moil         | Líder del equipo                       | pedidoservice                |
| Mayckol Mardones    | Encargado de Backend y Base de Datos   | carritoservice               |
| Francisco Vera      | Encargado de Backend y Base de Datos   | logisticaservice             |

## Estructura del Repositorio

perfulandia-microservices
├── .idea
├── carritoservice
│   └── src
│       └── pom.xml
├── logisticaservice
│   └── src
│       └── pom.xml
├── pedidoservice
│   └── src
│       └── pom.xml
├── productservice
│   └── src
│       └── pom.xml
├── usuarioservice
│   └── src
│       └── pom.xml
└── README.md

Cada microservicio contiene su propio archivo `pom.xml`, configuración de base de datos, controladores REST, entidades y repositorios.

## Colaboración en GitHub

El equipo organizó el trabajo utilizando una rama principal (`master`) y ramas individuales por integrante:

- `master`: rama principal del repositorio, donde se integran los microservicios completos y estables.
- `carlos-moil`: rama de desarrollo del microservicio `pedidoservice`.
- `francisco-vera`: rama de desarrollo del microservicio `logisticaservice`.
- `mayckol-mardones`: rama de desarrollo del microservicio `carritoservice`.

Cada integrante trabajó de forma independiente en su respectiva rama para evitar conflictos, lo cual permitió avanzar en paralelo sin afectar el desarrollo de otros módulos.

Una vez completadas las funcionalidades, se realizaron pull requests desde cada rama hacia `master`. Estos fueron revisados y fusionados por el equipo, resolviendo conflictos si era necesario.

Se realizaron commits frecuentes y descriptivos para mantener un historial de cambios claro y facilitar la integración.

## Lecciones Aprendidas

Durante el desarrollo del proyecto aprendimos:

- Cómo diseñar e implementar una arquitectura basada en microservicios desde cero.
- La importancia del trabajo colaborativo y el control de versiones en equipo.
- Cómo realizar pruebas efectivas de endpoints RESTful utilizando Postman.
