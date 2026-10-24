# RetailBI — Entrega 1: Estrategia y Diagnóstico de Business Intelligence

## 1. Descripción del proyecto
RetailBI es un proyecto académico de Business Intelligence (BI) orientado al análisis y la organización de información para apoyar la toma de decisiones en una empresa minorista ficticia con cinco tiendas ubicadas en Bogotá, Colombia.

El proyecto parte de una situación en la que la información se encuentra dispersa, existen diferencias en los formatos de los datos y no hay definiciones uniformes para algunos indicadores del negocio. Estas dificultades limitan la posibilidad de realizar análisis consistentes y comparar los resultados entre tiendas y periodos.

Como propuesta, se plantea una solución de BI que permita integrar las fuentes de información, organizar los datos mediante una arquitectura por capas y facilitar el análisis de las ventas a través de un modelo dimensional.

---

## 2. Objetivo general
Diseñar una propuesta inicial de solución de Business Intelligence para una empresa minorista, a partir de la identificación de necesidades del negocio, el análisis de las fuentes de datos, la evaluación de su nivel de madurez y el diseño de una arquitectura y un modelo dimensional que permitan apoyar la toma de decisiones.

---

## 3. Caso de negocio
La empresa objeto de estudio presenta dificultades relacionadas con la dispersión de la información, la inconsistencia de algunos formatos y la falta de estandarización de indicadores. A partir de esta situación, el proyecto busca establecer una base para integrar los datos y facilitar el seguimiento de las ventas, los descuentos y los resultados comerciales.

### Principales síntomas identificados
* *S1. Inconsistencia en las fechas:* existen diferencias en los formatos de fecha y problemas de calidad en algunos registros.
* *S2. Información dispersa:* los datos se encuentran en distintas fuentes y requieren un proceso de integración.
* *S3. Definiciones no uniformes:* algunos indicadores pueden interpretarse o calcularse de manera diferente, lo que dificulta la comparación de resultados.

---

## 4. Preguntas de negocio
El proyecto plantea una pregunta principal y cuatro preguntas secundarias para orientar el análisis:
* *P0:* ¿Cómo evolucionan los ingresos y las unidades vendidas por tienda, categoría y mes?
* *P1:* ¿Qué productos y categorías generan mayores ingresos netos?
* *P2:* ¿Qué tiendas presentan mayor volumen de unidades vendidas?
* *P3:* ¿Qué meses muestran aumentos o disminuciones en las ventas?
* *P4:* ¿Qué nivel de ventas podría esperarse para los próximos meses a partir del historial?

---

## 5. Fuentes de datos
Para el desarrollo del proyecto se consideran tres fuentes de información:

| Fuente | Descripción | Tipo |
| :--- | :--- | :--- |
| *F1* | Estadísticas de la Encuesta Mensual de Comercio (EMC) del DANE. | Datos públicos |
| *F2* | Datos abiertos de Bogotá relacionados con la dinámica empresarial. | Datos públicos |
| *F3* | Conjunto de datos sintéticos de ventas minoristas con 50.000 registros, correspondientes al periodo 2023–2025. | Datos sintéticos |

Las fuentes públicas aportan información contextual para el análisis, mientras que el conjunto sintético permite representar las operaciones de venta de la empresa ficticia.

---

## 6. Calidad de los datos
Durante la revisión de las fuentes se identificaron situaciones que deben considerarse en el proceso de preparación e integración de los datos:
* Diferencias en los formatos de fecha.
* Valores faltantes o inconsistentes.
* Códigos de actividad económica que requieren conservar su formato original.
* Registros con categorías o localidades sin información estandarizada.

---

## 7. Diagnóstico de madurez BI
* *Fase actual:* Fase 2 (Datos accesibles sin BI).
* *Fase objetivo:* Fase 4 (Data warehouse).

La evolución propuesta busca superar la fragmentación de los datos mediante la integración, la organización en un almacén y la habilitación de consultas analíticas.

---

## 8. Arquitectura propuesta
La solución se organiza en cinco capas:
1. *Fuentes de datos:* archivos y conjuntos de datos utilizados como entrada.
2. *Integración y transformación:* procesos ETL con Pentaho Data Integration (PDI).
3. *Almacén de datos:* esquema relacional centralizado en PostgreSQL.
4. *Consumo y visualización:* Power BI Desktop y Metabase.
5. *Gobierno y calidad de los datos:* metadatos, bitácoras y seguridad.

---

## 9. Modelo dimensional
El modelo utiliza un esquema en estrella compuesto por:
* *Tabla de hechos:* FactVentas (granularidad a nivel de línea de venta; incluye métricas de cantidad, precio, ventas brutas, descuentos, ventas netas, costos y márgenes simulados).
* *Dimensiones:* DimFecha, DimTienda, DimProducto y DimDescuento.

---

## 10. Estructura del repositorio
```text
RetailBI/
├── BI-Entrega-1-Equipo.506241931-506241056-506241129.pdf
├── README.md
├── datos/
│   ├── diccionarios/
│   ├── muestras/
│   └── raw/
├── docs/
│   └── diagramas/
├── DW/
└── ETL/