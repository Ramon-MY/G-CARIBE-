# GUARDIÁN CARIBE

**Proyecto académico de monitoreo, detección y respuesta ante amenazas de ciberseguridad.**

## Descripción

GUARDIÁN CARIBE es una propuesta de plataforma ligera de monitoreo de seguridad (SOC) orientada a recopilar eventos, detectar comportamientos sospechosos, generar alertas, administrar indicadores de compromiso (IoC) y apoyar la gestión de incidentes. Se plantea para operar en entornos con recursos y conectividad limitados.

## Objetivo

Diseñar y desarrollar una solución que permita centralizar eventos de seguridad, identificar posibles amenazas, organizar alertas e incidentes y documentar acciones de respuesta, aplicando buenas prácticas de seguridad, trazabilidad y protección de información.

## Herramientas y tecnologías previstas

- **Lenguaje:** Python 3.11 o superior.
- **API:** FastAPI y Uvicorn.
- **Datos y validación:** SQLAlchemy, Pydantic y pydantic-settings.
- **Persistencia:** SQLite para desarrollo y PostgreSQL como alternativa de despliegue.
- **Pruebas:** Pytest y HTTPX.
- **Control de versiones y colaboración:** Git y GitHub (Issues y Projects).
- **Documentación:** Markdown y documentación OpenAPI generada por FastAPI.

## Estudiante

- **Nombre:** Ramón Martínez.
- **Proyecto:** GUARDIÁN CARIBE.
- **Repositorio:** [Ramon-MY/G-CARIBE-](https://github.com/Ramon-MY/G-CARIBE-).

## Estado inicial del proyecto

**Etapa: organización y preparación de la base del proyecto.**

El repositorio contiene la documentación inicial y los archivos de configuración de dependencias. La estructura de carpetas se está preparando. Los módulos funcionales, las pruebas y las integraciones deberán implementarse y verificarse antes de considerar el producto como terminado. Los requerimientos se gestionan mediante GitHub Issues; no se debe interpretar un Issue abierto como una funcionalidad ya implementada.

## Estructura del repositorio

```text
G-CARIBE-/
├── documentacion/   # Guías, planificación y documentación técnica
├── src/             # Código fuente de la aplicación
├── evidencias/      # Evidencias académicas; no incluir datos sensibles
├── tests/           # Pruebas unitarias e integración
├── database/        # Esquemas y scripts de base de datos
├── config/          # Plantillas de configuración sin secretos
├── README.md
├── requirements.txt
├── .gitignore
└── LICENSE
```

## Organización del trabajo

El trabajo se organizará con GitHub Issues y un tablero GitHub Projects. Cada tarea tendrá un título, descripción, prioridad, etiqueta y responsable cuando corresponda. El flujo de trabajo utilizará estos estados:

1. **Pendiente:** tarea registrada y aún no iniciada.
2. **En proceso:** tarea en desarrollo.
3. **En revisión:** tarea terminada, pendiente de comprobación.
4. **Completado:** tarea revisada y aceptada.

Los cambios se registrarán en commits pequeños con mensajes claros. Antes de cerrar un Issue se comprobarán sus criterios de aceptación y, cuando aplique, se adjuntarán pruebas o evidencias.

## Instalación del entorno

```bash
python -m venv .venv
# Windows PowerShell:
.venv\\Scripts\\Activate.ps1
# Linux/macOS:
source .venv/bin/activate

pip install -r requirements.txt
```

## Configuración

Copia `config/.env.example` a un archivo `.env` local y completa los valores necesarios. **Nunca publiques claves, contraseñas, tokens ni archivos `.env` reales.**

## Ejecución y pruebas

La ejecución de la API y la suite de pruebas se documentarán a medida que se implementen los módulos. Los comandos previstos son:

```bash
uvicorn src.app.main:app --reload
pytest
```

Estos comandos requieren que los módulos y pruebas correspondientes estén implementados.

## Seguimiento

- [Issues del proyecto](https://github.com/Ramon-MY/G-CARIBE-/issues)
- [Tablero GitHub Projects](https://github.com/users/Ramon-MY/projects/3/views/1?system_template=kanban)

## Licencia

Este proyecto utiliza la licencia MIT. Consulta el archivo [LICENSE](LICENSE).
