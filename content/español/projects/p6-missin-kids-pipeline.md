+++
title = "Pipeline para análisis de desapariciones infantiles en Chiapas (México)"
date = 2025-09-20
description = "Este proyecto es la implementación de un pipeline ELT (Extract, Load and Transform) completo y un dashboard sencillo para analizar datos sobre desapariciones de niños, niñas y adolescentes en Chiapas, México. El sistema está contenerizado utilizando Docker y orquestado mediante Apache Airflow, con PostgreSQL como base de datos y Chart.js para la visualización."
tags = ["python", "data", "airflow", "postgresql", "docker", "flask", "chart.js"]
# externalLink = "https://github.com/..." # User can use this to link directly out
+++

## Contenido
- [Resumen del Proyecto](#resumen-del-proyecto)
- [Contexto del Dataset](#contexto-del-dataset)
- [Arquitectura del Proyecto](#arquitectura-del-proyecto)
- [Dashboard](#dashboard)
- [Tecnologías Utilizadas](#tecnologías-utilizadas)

## Resumen del Proyecto

Este proyecto implementa un pipeline ELT (Extract, Load and Transform) completo y un dashboard interactivo para analizar datos sobre desapariciones de niños, niñas y adolescentes en Chiapas, México. El sistema está contenerizado utilizando Docker y orquestado mediante Apache Airflow, con PostgreSQL como base de datos y Flask para la visualización.

##### **El codigo de este proyecto se puede encontrar en Github, da click en el siguiente enlace: [GitHub](https://github.com/Frank3040/pipeline-desapariciones-chiapas.git)**

## Contexto del Dataset

El dataset proviene de la plataforma [datamx](https://datamx.io/about). Especificamente, el dataset usado es [DESAPARICIÓN DE NIÑAS, NIÑOS Y ADOLESCENTES EN CHIAPAS 2019-2025](https://datamx.io/dataset/desaparicion-de-ninas-ninos-y-adolescentes-en-chiapas-2019-2025).

### Relevancia Social
Este dataset es de crítica importancia social y humanitaria. La desaparición de menores es una crisis que afecta profundamente el tejido social, la seguridad y los derechos humanos fundamentales. Contar con datos estructurados y accesibles es el primer paso para visibilizar la magnitud del problema y movilizar recursos de manera efectiva.

### Problema a Resolver
El análisis de estos datos permite abordar la falta de información centralizada y procesable. Al identificar patrones, como los municipios con mayor incidencia, los grupos etarios más vulnerables o las tendencias temporales, se pueden diseñar estrategias de prevención más efectivas y optimizar los esfuerzos de búsqueda y localización.


## Arquitectura del Proyecto

![Arquitectura del proyecto](/project_images/p6-missing-kids/p6-1.jpg)

El proyecto utiliza una arquitectura moderna basada en contenedores:

1.  **Orquestación (Apache Airflow):** Gestiona el flujo de trabajo ETL.
    *   **Sensor:** Detecta la llegada de nuevos archivos de datos.
    *   **Preparación**: Prepara los datos para ser cargados. Pequeña transformación.
    *   **Carga:** Ingesta datos crudos CSV a PostgreSQL (`schema: raw`).
    *   **Transformación:** Limpieza y normalización de datos mediante SQL (`schema: processed`).
    *   **Modelado:** Creación de vistas analíticas (`schema: trusted`).
    *   **Permisos:** Gestión automática de roles de base de datos para seguridad.
2.  **Almacenamiento (PostgreSQL):** Base de datos relacional con esquema en capas (Raw -> Processed -> Trusted).
3.  **Visualización (Flask + Chart.js):** Dashboard web que consume las vistas confiables para mostrar KPIs y gráficos en tiempo real.
4.  **Infraestructura (Docker):** Todo el entorno se despliega mediante `docker-compose`.

## Dashboard

Debajo se muestra el dashboard resultante. Un dashboard sencillo que muestra KPIs relevantes y gráficos para explorar los datos.

![Dashboard Parte 1](/project_images/p6-missing-kids/p6-2.png)
![Dashboard Parte 2](/project_images/p6-missing-kids/p6-3.png)

Entre las principales conclusiones se encuentran:

## Tecnologías Utilizadas

*   Python
*   Apache Airflow
*   PostgreSQL
*   Flask
*   Chart.js
*   Docker


