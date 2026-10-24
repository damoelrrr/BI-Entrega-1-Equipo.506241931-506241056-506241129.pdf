# Descarga y trazabilidad de las fuentes

Documento de trazabilidad de las tres fuentes del proyecto RetailBI (Entrega 1).
Fecha de descarga o generación de todas las fuentes: **23/10/2026**.

| Fuente | Procedencia | Archivo en `datos/raw/` | Formato | Registros / periodo | Licencia |
|---|---|---|---|---|---|
| F1 | DANE, Encuesta Mensual de Comercio (EMC) | `anex-EMC-ComercioMinorista-ago2026.xlsx` | XLSX | Hoja 2.1: 92 registros mensuales, enero de 2019 a agosto de 2026 | Uso, aprovechamiento, transformación y análisis autorizados con atribución al DANE; sujeto a los términos y condiciones del portal |
| F2 | Secretaría Distrital de Desarrollo Económico, Datos Abiertos Bogotá | `170b171a-19bb-46ca-83e8-3074fe7d74be.csv` | CSV | 39.941 registros, con corte a abril de 2026 | Creative Commons Attribution-ShareAlike 4.0 (CC BY-SA 4.0), según ficha del portal |
| F3 | Elaboración propia (datos sintéticos) | `RetailBI_ventas_sinteticas_50000.gpkg` | GPKG (GeoPackage, tabla sin geometría) | 50.000 filas, del 01/01/2023 al 31/12/2025 | Datos sintéticos creados para fines académicos; no corresponden a ventas reales |

## F1. DANE, Encuesta Mensual de Comercio (EMC)

- **Página de la encuesta:** https://www.dane.gov.co/index.php/estadisticas-por-tema/comercio-interno/encuesta-mensual-de-comercio-emc
- **Archivo descargado:** https://www.dane.gov.co/files/operaciones/EMC/anex-EMC-ComercioMinorista-ago2026.xlsx
- **Hoja utilizada:** `2.1` (índices de las ventas en valores nominales según grupo de mercancía, base 2019 = 100).

Pasos para obtenerla:

1. Entrar a la página de la encuesta y buscar el anexo de comercio minorista de agosto de 2026.
2. Descargar el archivo `anex-EMC-ComercioMinorista-ago2026.xlsx`.
3. Guardarlo sin modificarlo en `datos/raw/`.
4. Abrir la hoja `2.1`: los encabezados están en la fila 8 y los datos comienzan en la fila 9.

## F2. Datos Abiertos Bogotá, Dinámica empresarial

- **Conjunto de datos:** https://datosabiertos.bogota.gov.co/dataset/dinamica-empresarial-bogota
- **Recurso utilizado ("Empresas 2026"):** https://datosabiertos.bogota.gov.co/de/dataset/dinamica-empresarial-bogota/resource/170b171a-19bb-46ca-83e8-3074fe7d74be

Pasos para obtenerla:

1. Entrar al conjunto de datos y abrir el recurso "Empresas 2026".
2. Descargar el archivo del recurso (identificador `170b171a-19bb-46ca-83e8-3074fe7d74be`).
3. Guardarlo sin modificarlo en `datos/raw/`.
4. Comprobar que tiene 39.941 registros y las 12 columnas descritas en `datos/diccionarios/`.

## F3. RetailBI, ventas sintéticas

Fuente generada por el equipo con datos **sintéticos** (no son ventas reales de ninguna empresa). El generador usa la semilla 2026, por lo que produce siempre el mismo conjunto.

- **Archivo:** `datos/raw/RetailBI_ventas_sinteticas_50000.gpkg` (capa `ventas_sinteticas`).
- **Generador:** `datos/generar_ventas_sinteticas_gpkg.py`.

Pasos para regenerarla:

1. Instalar las dependencias: `pip install numpy pyogrio`.
2. Ejecutar: `python datos/generar_ventas_sinteticas_gpkg.py`.
3. Mover el archivo `RetailBI_ventas_sinteticas_50000.gpkg` resultante a `datos/raw/`.
4. Comprobar que la capa tiene 50.000 filas y que `total_venta_cop = cantidad × precio_unitario_cop − descuento_cop` en todas.

## Muestras y diccionarios

- `datos/muestras/`: 20 filas por fuente, en CSV.
- `datos/diccionarios/`: un diccionario por fuente (campo, tipo, descripción, ejemplo y problema de calidad).
