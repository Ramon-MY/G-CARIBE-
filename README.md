# G-CARIBE

Plataforma de monitoreo de seguridad (SOC) que integra telemetría de endpoints, eventos de seguridad, alertas, inteligencia de amenazas (CTI), gestión de incidentes y acciones de respuesta automatizadas.

## Características principales

- Recepción y almacenamiento de eventos de seguridad provenientes de endpoints.
- Motor de detección basado en reglas sobre los eventos recibidos.
- Generación y seguimiento de alertas.
- Gestión de indicadores de compromiso (IoC) mediante un servicio de CTI.
- Creación y seguimiento de incidentes.
- Registro de acciones de respuesta.

## Stack tecnológico

- Python 3.11+
- FastAPI
- SQLAlchemy
- Pydantic
- SQLite / PostgreSQL
- Pytest

## Estructura del proyecto

```
G-CARIBE/
├── src/app/        # Código fuente de la aplicación
├── database/       # Scripts SQL de esquema y datos de prueba
├── tests/          # Pruebas automatizadas
├── docs/           # Documentación técnica
├── evidencias/     # Evidencias forenses (no versionar)
└── config/         # Archivos de configuración
```

## Instalación

```bash
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

## Ejecución

```bash
cp config/.env.example config/.env
uvicorn src.app.main:app --reload
```

La documentación interactiva estará disponible en `http://127.0.0.1:8000/docs`.

## Pruebas

```bash
pytest
```

## Documentación

- [Arquitectura](docs/architecture.md)
- [API](docs/api.md)
- [Base de datos](docs/database.md)
- [Seguridad](docs/security.md)

## Licencia

Este proyecto se distribuye bajo la licencia MIT. Consulte el archivo [LICENSE](LICENSE).
