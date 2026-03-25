# Django Tasks API

API REST para gestión de tareas, construida con **Django** y **Django REST Framework**.

## Tecnologías

- Python 3
- Django 6.0
- Django REST Framework 3.17
- SQLite (base de datos por defecto)
- django-cors-headers

## Instalación

```bash
# Clonar el repositorio
git clone https://github.com/fidehlg89/django_tasks-api.git
cd django_tasks-api

# Crear y activar entorno virtual
python -m venv venv
source venv/bin/activate

# Instalar dependencias
pip install -r requirements.txt

# Aplicar migraciones
python manage.py migrate

# Ejecutar servidor de desarrollo
python manage.py runserver
```

El servidor estará disponible en `http://localhost:8000`.

## Endpoints

Base URL: `/tasks/api/v1/`

| Método   | Endpoint          | Descripción              |
|----------|-------------------|--------------------------|
| `GET`    | `/tasks/`         | Listar todas las tareas  |
| `POST`   | `/tasks/`         | Crear una nueva tarea    |
| `GET`    | `/tasks/{id}/`    | Obtener una tarea        |
| `PUT`    | `/tasks/{id}/`    | Actualizar una tarea     |
| `DELETE` | `/tasks/{id}/`    | Eliminar una tarea       |

### Modelo Task

| Campo         | Tipo      | Descripción                      |
|---------------|-----------|----------------------------------|
| `id`          | Integer   | Identificador único (auto)       |
| `title`       | String    | Título de la tarea (max 200)     |
| `description` | Text      | Descripción (opcional)           |
| `done`        | Boolean   | Estado de completado (def: false)|

### Ejemplo de request

```json
POST /tasks/api/v1/tasks/
{
  "title": "Mi primera tarea",
  "description": "Descripción de la tarea",
  "done": false
}
```

## Estructura del proyecto

```
django_tasks-api/
├── django_crud_api/      # Configuración del proyecto Django
│   ├── settings.py
│   ├── urls.py
│   ├── wsgi.py
│   └── asgi.py
├── tasks/                # App principal
│   ├── models.py         # Modelo Task
│   ├── serializer.py     # Serializador DRF
│   ├── views.py          # ViewSet
│   ├── urls.py           # Rutas de la API
│   └── admin.py          # Registro en admin
├── manage.py
├── requirements.txt
└── .gitignore
```

## Admin

Accede al panel de administración en `/admin/` para gestionar tareas desde la interfaz de Django.

## CORS

Configurado para permitir requests desde `http://localhost:5173` (frontend en desarrollo).
