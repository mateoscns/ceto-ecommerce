# Ceto BHB — e-commerce (backend)

Tienda online para una vendedora de Córdoba que vende un suplemento dietario. La compra se hace en la web y el cierre y la atención, por WhatsApp. Este repo tiene el backend; el frontend todavía no está empezado.

## Qué resuelve

- **Catálogo y stock** con reserva al crear el pedido, para no vender lo que no hay.
- **Ciclo de vida del pedido:** reserva, pago, cancelación y vencimiento automático por job.
- **API pública de la tienda y del checkout** con límites por IP y por teléfono, tope de tamaño del cuerpo y cabeceras de seguridad.
- **API de administración** (`/api/admin/*`): login con sesión, CSRF, límite de intentos, auditoría de solo inserción, y gestión de pedidos, stock y catálogo.

## Stack

Java 21 · Spring Boot 4.1 · Spring Data JPA · Spring Security · Flyway · PostgreSQL · Docker

## Calidad

- Tests de integración contra **Postgres real** con Testcontainers.
- Reglas de arquitectura verificadas con **ArchUnit**.
- Pruebas de mutación con **PIT** para medir qué tan bien detectan errores los tests ([docs/testing.md](docs/testing.md)).
- Las reglas críticas (stock, dinero, estados del pedido) se garantizan con restricciones en la base o con tests, no solo con código.

## Correr en local

Requisitos: Java 21 y Docker encendido (para los tests con Testcontainers).

```bash
cd backend
./mvnw clean verify     # compila y corre todos los tests
./mvnw spring-boot:run  # levanta la API (necesita un Postgres; ver application.yml)
```

## Documentación

- [docs/API.md](docs/API.md) — rutas de la API
- [docs/DECISIONES.md](docs/DECISIONES.md) — decisiones de diseño
- [docs/operacion-admin.md](docs/operacion-admin.md) — operación del panel

## Estado

Backend en desarrollo. Pendiente: frontend (Next.js), Mercado Pago, cupones, reseñas y avisos por mail.
