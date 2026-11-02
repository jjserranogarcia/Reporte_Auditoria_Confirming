# Reporte de bonificaciones de confirming en Power BI

**Dashboard interactivo para analizar los importes de facturas anticipadas por proveedores y las bonificaciones que generan para Grupo Prisma**, un holding empresarial ficticio compuesto por ocho sociedades.

> **Datos simulados:** las empresas, los bancos, los proveedores y las operaciones representadas son ficticios.

## 1. 🔗 Contexto y origen de los datos

En el *confirming*, los proveedores pueden **anticipar el cobro de sus facturas** a través de una entidad financiera. Esta cobra por adelantar dichos **importes** y entrega una parte de los ingresos al holding en concepto de **bonificación**.

Este informe utiliza el histórico CSV generado por [**Pipeline_Auditoria_Confirming**](https://github.com/jjserranogarcia/Pipeline_Auditoria_Confirming/blob/main/README.md), un proyecto en **Python** que automatiza la extracción, comprobación y seguimiento de las operaciones mediante **Google Drive** y **GitHub Actions**. El pipeline revisa los datos y **Power BI permite analizarlos visualmente**.

## 2. 📊 Funcionamiento y resumen

El informe dispone de cuatro páginas : **Resumen, Sociedad, Banco y Proveedor**, y permite alternar entre **Importes** y **Bonificaciones**, aplicar filtros y consultar tanto resultados agregados como facturas individuales.

### Importes anticipados

![Resumen del dashboard: importes anticipados](imagenes/1_1_Resumen.png)

**Análisis de los datos**

- **Volumen:** 19.733 facturas anticipadas por **42.827.760 €**, con un importe medio de **2.170 €**.
- **Bancos:** los bancos que gestionan mayores importes adelantados son **Rubí** (8.636.504 €), **Perla** (8.587.743 €) y **Oro** (8.359.590 €).
- **Región:** la región donde más importe se adelanta es **Andalucía**, por lo que en las siguientes páginas la filtraremos para un análisis detallado.

### Bonificaciones

![Resumen del dashboard: bonificaciones](imagenes/1_2_Resumen.png)

**Análisis de los datos**

- **Volumen:** las 19.733 facturas generan **1.545.048 €** en bonificaciones, con una media de **78 €** por factura.
- **Bancos:** lidera **Platino** (849.877 €), seguido de **Oro** (220.800 €) y **Perla** (219.231 €).
- **Comparación:** mientras que **Rubí** tiene el mayor número de importes anticipados, el banco **Platino** lidera en las bonificaciones.

El botón de información ofrece una breve descripción del informe y explica la diferencia entre los indicadores **"Importes"** y **"Bonificaciones"**, facilitando la interpretación de los datos.

![Ventana de ayuda sobre el informe](imagenes/2_Explicacion.png)

## 3. 🏢 Sociedad

Esta página compara el volumen anticipado y el número de facturas por sociedad, su evolución diaria y el detalle de las operaciones.

![Análisis de importes anticipados por sociedad](imagenes/3_Sociedad.png)

**Análisis de los datos**

- **Selección:** en Andalucía, durante el mes de diciembre de 2025, se adelantaron importes de facturas por un valor total de **9.829.405 €**.
- **Importes:** la sociedad **Escarlata** concentra el mayor volumen de importe anticipado (**1.349.580 €**), seguida muy de cerca por **Rojo** (**1.349.419 €**).
- **Facturas:** la sociedad **Púrpura** registra el mayor número de facturas anticipadas (**623**), aunque no lidera el importe.

Las tablas permiten revisar el detalle de cada factura, así como información adicional sobre cada sociedad del Grupo Prisma.

## 4. 🏦 Banco

Esta página compara las bonificaciones generadas y el número de facturas anticipadas por banco, su evolución diaria y el detalle de las operaciones.

![Análisis de bonificaciones por banco](imagenes/4_Banco.png)

**Análisis de los datos**

- **Selección:** en Andalucía, durante el mes de diciembre de 2025, las facturas anticipadas generaron un total de **228.346 €** en bonificaciones.
- **Bonificaciones:** el banco **Platino** concentra el mayor importe (**65.977 €**), seguido de **Oro** (**51.792 €**) y **Perla** (**48.133 €**).
- **Facturas:** el banco **Rubí** registra el mayor número de facturas anticipadas (**1.019**), mientras que **Platino** contabiliza **121**, pese a liderar las bonificaciones.

Las tablas permiten consultar el detalle de cada factura adelantada, así como información adicional sobre los bancos.

## 5. 📦 Proveedor

Esta página compara los importes anticipados por proveedor, su evolución diaria y el detalle de las operaciones. Además, permite seleccionar un proveedor para estudiarlo en profundidad.

### Clasificación de proveedores

![Clasificación de proveedores por importe anticipado](imagenes/5_1_Proveedor.png)

**Análisis de los datos**

- **Selección:** en Andalucía, durante el mes de diciembre de 2025, se adelantaron importes de facturas por un valor total de **9.829.405 €**.
- **Importes:** **Piedras Modernizados S.A.** es el proveedor con mayor importe anticipado (**86.163 €**), seguido de **Condensadores Virtuales S.A.** (**79.377 €**) y **Adoquines Ágiles S.A.** (**78.406 €**).
- **Análisis:** se elige **Piedras Modernizados S.A.**, por ser el proveedor que más importe anticipa, para revisar sus operaciones individualmente.

Las tablas permiten consultar el detalle de cada factura adelantada, así como información adicional sobre los proveedores.

### Análisis de un proveedor concreto

![Análisis de Piedras Modernizados S.A.](imagenes/5_2_Proveedor.png)

**Análisis de los datos**

- **Selección:** se mantienen los filtros de Andalucía y diciembre de 2025, y se selecciona el proveedor **Piedras Modernizados S.A.**.
- **Importes:** este proveedor acumula **86.163 €** en facturas anticipadas durante el periodo analizado.
- **Evolución y detalle:** el gráfico muestra cómo se distribuyen los anticipos a lo largo del tiempo y la tabla identifica las facturas, sociedades y bancos relacionados.

Esta vista permite pasar de la clasificación general de proveedores al análisis detallado de sus operaciones.


## 6. 💻 Tecnologías y acceso

**Power BI Desktop** para el dashboard y **CSV** como fuente de datos revisados. 
Para explorar el informe, descarga [`Report_Auditoria_Confirming.pbix`](Report_Auditoria_Confirming.pbix) y ábrelo en **Power BI Desktop**.

El tratamiento automatizado previo se documenta en [Pipeline_Auditoria_Confirming](https://github.com/jjserranogarcia/Pipeline_Auditoria_Confirming/blob/main/README.md).

