# Backend Ventas - Innovatech Chile

## ¿Qué hace este proyecto?
Gestiona las ventas de Innovatech Chile. Permite crear, ver, actualizar y eliminar ventas a través de una API REST.

## Tecnologías usadas
- Java 17
- Spring Boot 3.4.4
- MySQL 8.0
- Docker
- AWS EKS
- GitHub Actions

## Cómo correrlo localmente

Primero necesitas tener Docker instalado. Luego ejecuta:

```bash
docker run -d --name ventas-local \
  -e DB_ENDPOINT=host.docker.internal \
  -e DB_PORT=3306 \
  -e DB_NAME=innovatech \
  -e DB_USERNAME=admin \
  -e DB_PASSWORD=admin123 \
  -p 8080:8080 \
  innovatech-ventas:latest
```

Una vez corriendo, accede a la documentación en:
`http://localhost:8080/swagger-ui.html`

## Endpoints disponibles

| Método | Ruta | Descripción |
|--------|------|-------------|
| GET | /api/v1/ventas | Lista todas las ventas |
| GET | /api/v1/ventas/{id} | Busca una venta por ID |
| POST | /api/v1/ventas | Crea una nueva venta |
| PUT | /api/v1/ventas/{id} | Actualiza una venta |
| DELETE | /api/v1/ventas/{id} | Elimina una venta |

## Variables de entorno necesarias

El proyecto se conecta a MySQL mediante variables de entorno:

- `DB_ENDPOINT` — dirección del servidor MySQL
- `DB_PORT` — puerto (normalmente 3306)
- `DB_NAME` — nombre de la base de datos
- `DB_USERNAME` — usuario
- `DB_PASSWORD` — contraseña

## Despliegue automático

Cada vez que se hace push a la rama `deploy`, GitHub Actions construye la imagen Docker, la sube a Amazon ECR y la despliega automáticamente en el clúster EKS de AWS.