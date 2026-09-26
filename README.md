# Sistema de Integración y Análisis de Información (BEPWR)


Motor ETL (Extract, Transform, Load) y ecosistema de Business Intelligence desarrollado para centralizar, estandarizar y visualizar la información operativa del estudio de Functional Training **BEPWR**.

Este sistema automatiza la recolección de datos de asistencias y reservas desde cuatro plataformas distintas (TotalPass, Fitpass, Wellhub y Fitco), eliminando el trabajo manual en hojas de cálculo y proporcionando métricas de negocio en tiempo real.

---

## Arquitectura del Proyecto

El proyecto está diseñado bajo un **Esquema en Estrella (Star Schema)** optimizado para analítica, dividiéndose en tres fases:

1. **Extracción (Extract):** 
   - Conexión vía API REST para TotalPass y Fitco.
   - Ingesta y lectura automatizada de archivos CSV para Wellhub y Fitpass.
2. **Transformación (Transform):** 
   - Homologación de formatos de fecha y hora.
   - Estandarización de estatus de asistencia.
   - Deduplicación de registros de clientes.
3. **Carga y Visualización (Load & BI):** 
   - Inyección de datos limpios en un Data Warehouse relacional (Tabla de Hechos y Dimensiones).
   - Conexión DirectQuery/Import a Microsoft Power BI para dashboards interactivos.

---

## 💻 Stack Tecnológico

* **Lenguaje Principal:** Python 3.x
* **Librerías ETL:** `pandas`, `requests`, `python-dotenv`, `SQLAlchemy`
* **Base de Datos:** PostgreSQL / MySQL
* **Business Intelligence:** Microsoft Power BI Desktop
* **Diseño UI/UX:** Figma
* **Control de Versiones:** Git / GitHub

---

##  Estructura del Repositorio

```text
bepwr-analitica-etl/
├── db/                     # Scripts de inicialización y migración SQL
│   └── 01_init_schema.sql  # Creación del modelo estrella (DDL)
├── etl/                    # Scripts modulares del motor de datos
│   ├── extract_api.py      # Conectores para TotalPass y Fitco
│   ├── process_csv.py      # Procesador de archivos planos
│   └── load_db.py          # Lógica de inserción a base de datos
├── docs/                   # Documentación técnica y evidencias
│   └── dashboard_mockup.png# Wireframes e interfaces
├── .env.example            # Plantilla de variables de entorno (Credenciales)
├── .gitignore              # Reglas de exclusión de seguridad
└── README.md               # Documentación principal
