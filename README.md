# Reporte de bonificaciones de confirming en Power BI

**Dashboard interactivo desarrollado en Power BI para analizar los importes de las facturas anticipadas por los proveedores y las bonificaciones económicas que estas operaciones generan para Grupo Prisma, un holding empresarial ficticio.**

El informe permite pasar de una visión global a un análisis detallado **por sociedad, banco y proveedor**, combinando indicadores, gráficos, mapas, tablas y filtros interactivos.

> **Nota:** Grupo Prisma, sus sociedades, bancos, proveedores, facturas e importes son datos **simulados**. Este proyecto tiene fines demostrativos y de portfolio; no representa operaciones de una empresa real.

## Contenido

1. [Contexto y origen de los datos](#1-contexto-y-origen-de-los-datos)
2. [Funcionamiento del dashboard](#2-funcionamiento-del-dashboard)
3. [Resumen: visión global](#3-resumen-visión-global)
4. [Sociedad: análisis por empresa del holding](#4-sociedad-análisis-por-empresa-del-holding)
5. [Banco: análisis por entidad financiera](#5-banco-análisis-por-entidad-financiera)
6. [Proveedor: análisis individualizado](#6-proveedor-análisis-individualizado)
7. [Tecnologías utilizadas](#7-tecnologías-utilizadas)
8. [Cómo abrir el informe](#8-cómo-abrir-el-informe)

---

## 1. Contexto y origen de los datos

En el *confirming*, una entidad financiera gestiona pagos a proveedores y estos pueden optar por **anticipar el cobro de sus facturas**. En el escenario simulado de Grupo Prisma, determinados anticipos generan **bonificaciones económicas a favor del holding**.

Este informe es la **fase de visualización** de un proyecto más amplio. Utiliza el histórico de operaciones previamente procesadas y revisadas por el repositorio complementario:

**[Pipeline_Auditoria_Confirming](https://github.com/jjserranogarcia/Pipeline_Auditoria_Confirming)**

Se trata de un pipeline desarrollado en **Python** que automatiza la extracción, normalización, comprobación y monitorización de bonificaciones de confirming. Emplea **Google Drive** para la entrada y salida de documentos y **GitHub Actions** para ejecutar periódicamente el proceso. El programa comprueba los importes comunicados por los bancos y consolida los datos tratados en un **histórico en formato CSV**, que sirve como origen de este dashboard.

El caso de estudio contempla **8 sociedades y 8 bancos**, equivalentes a **64 combinaciones sociedad-banco** en una ejecución mensual completa del pipeline.

**Flujo de trabajo:**

```text
Documentos de confirming (bancos)
                ↓
Pipeline de auditoría en Python
(extracción → normalización → comprobación)
                ↓
Histórico de operaciones revisadas (CSV)
                ↓
Power BI: análisis y visualización
```

Así, ambos repositorios son complementarios: **el pipeline prepara y comprueba los datos; este informe permite explorarlos y obtener información útil para su seguimiento financiero**.

---

## 2. Funcionamiento del dashboard

El informe contiene **cuatro páginas**, accesibles mediante los botones de navegación inferiores:

| Página | Objetivo |
|---|---|
| **Resumen** | Consultar indicadores generales y distribución territorial y bancaria. |
| **Sociedad** | Comparar las ocho sociedades y revisar sus operaciones. |
| **Banco** | Analizar las bonificaciones y el número de facturas por entidad financiera. |
| **Proveedor** | Identificar los proveedores con mayores anticipos y estudiar sus facturas. |

### Filtros e interacciones

Los controles de la cabecera y el lateral permiten modificar el contexto de análisis:

- **Indicador:** alterna entre **Importes** (valor de las facturas anticipadas) y **Bonificaciones** (beneficio económico generado para el holding). Las visualizaciones cambian según la magnitud seleccionada.
- **Proveedor:** permite estudiar un proveedor específico o mantener todos los proveedores.
- **Región:** acota las operaciones a una comunidad autónoma.
- **Sector:** permite analizar proveedores de un sector determinado.
- **Fecha:** delimita el intervalo temporal.
- **Sociedad y Banco:** permiten seleccionar una o varias entidades mediante los controles laterales.
- **Borrar filtros:** facilita volver a una visión sin las selecciones aplicadas.

Las páginas incorporan gráficos y tablas que permiten pasar de resultados agregados a operaciones concretas. Las **cifras descritas a continuación corresponden a los filtros visibles en cada captura**; cambian cuando se modifica la selección.

---

## 3. Resumen: visión global

La página **Resumen** ofrece una primera lectura del volumen de operaciones y de los beneficios obtenidos, con tres indicadores principales, un gráfico de clasificación por banco y un mapa de distribución por región. El selector **Indicador** permite cambiar entre ambas magnitudes sin abandonar la página.

### 3.1. Importes anticipados

![Página Resumen de Power BI con el indicador Importes seleccionado](imagenes/1_1_Resumen.png)

**Qué se observa en la captura:**

- **Periodo seleccionado:** del **21/10/2025 al 28/01/2026**, sin filtros adicionales de proveedor, región ni sector.
- **N.º de facturas anticipadas:** **19.733**.
- **Importe total anticipado:** **42.827.760 €**.
- **Importe medio por factura anticipada:** **2.170 €** (valor mostrado redondeado).
- **Banco con mayor importe anticipado:** **Rubí**, con **8.636.504 €**; le siguen **Perla** (**8.587.743 €**) y **Oro** (**8.359.590 €**).
- El **mapa por regiones** muestra cómo se distribuyen territorialmente los anticipos. **Andalucía aparece con el tono más intenso**, por lo que se utiliza después como ejemplo para profundizar en una región concreta.

La comparación permite detectar en qué entidades se concentra el mayor volumen de facturas anticipadas y orientar el análisis hacia bancos o territorios de especial interés.

### 3.2. Bonificaciones

![Página Resumen de Power BI con el indicador Bonificaciones seleccionado](imagenes/1_2_Resumen.png)

**Qué se observa en la captura:**

- Se mantiene el periodo **21/10/2025–28/01/2026** y el mismo total de **19.733 facturas**.
- **Bonificaciones totales:** **1.545.048 €**.
- **Bonificación media por factura:** **78 €** (valor mostrado redondeado).
- **Banco con mayores bonificaciones:** **Platino**, con **849.877 €**, seguido de **Oro** (**220.800 €**) y **Perla** (**219.231 €**).
- El mapa cambia para representar la distribución regional de las **bonificaciones**, en lugar de los importes anticipados.

**Conclusión relevante:** el banco con más anticipos no coincide con el que genera más bonificaciones. **Rubí lidera el importe anticipado, pero Platino lidera ampliamente las bonificaciones**. Esta diferencia justifica estudiar ambas variables por separado, en lugar de considerar que un mayor volumen anticipado implica necesariamente un mayor beneficio para el holding.

### 3.3. Ventana de ayuda «Sobre el informe»

![Ventana explicativa del informe sobre el significado de Importes y Bonificaciones](imagenes/2_Explicacion.png)

El botón de información de la cabecera abre una ventana que explica la finalidad del dashboard y diferencia los dos conceptos principales:

- **Importes:** valor de las facturas cuyo cobro anticipan los proveedores a través de los bancos.
- **Bonificaciones:** beneficio económico que esas operaciones generan para Grupo Prisma.

Esta ayuda permite interpretar correctamente las métricas antes de explorar los datos.

---

## 4. Sociedad: análisis por empresa del holding

La página **Sociedad** permite comparar el peso de cada empresa del grupo, estudiar la evolución temporal de los anticipos y consultar tanto el detalle agregado por sociedad como las facturas que componen los resultados.

Incluye un **gráfico combinado de importes y número de facturas**, un **gráfico de evolución apilado** y **dos tablas de detalle**.

![Página Sociedad con importes anticipados, evolución y detalle de facturas](imagenes/3_Sociedad.png)

**Qué se observa en la captura:**

- **Filtros aplicados:** **Región = Andalucía**, **Fecha = 01/12/2025–28/12/2025** e **Indicador = Importes**. Se mantienen todas las sociedades, bancos, proveedores y sectores para poder comparar el conjunto de operaciones de la región.
- **Total anticipado para esta selección:** **9.829.405 €**.
- **Sociedad con mayor importe anticipado:** **Escarlata**, con **1.349.580 €**, prácticamente empatada con **Rojo**, con **1.349.419 €**.
- **Sociedad con mayor número de facturas anticipadas:** **Púrpura**, con **623 facturas**. Esto permite distinguir entre el volumen económico y la cantidad de operaciones.
- El gráfico inferior muestra **cómo evoluciona la contribución de las sociedades a los anticipos durante diciembre**.
- Las tablas de la derecha permiten revisar los **importes por sociedad**, los responsables y otros atributos incluidos en el modelo, además de consultar **facturas individuales** con su proveedor, banco, fecha, plazo e importe.

**¿Por qué se filtra Andalucía?** Tras observar su relevancia visual en el mapa del resumen, se utiliza como **caso de análisis territorial** para comprobar qué sociedades concentran los anticipos y cómo evoluciona su actividad durante un periodo concreto.

---

## 5. Banco: análisis por entidad financiera

La página **Banco** se centra en el comportamiento de las entidades financieras. Permite comparar las bonificaciones obtenidas y el número de facturas anticipadas, observar su evolución diaria y consultar los registros que explican los resultados.

Contiene un **gráfico combinado de bonificaciones y número de facturas**, un **gráfico de áreas apiladas por banco** y **tablas de detalle de entidades y facturas**.

![Página Banco con bonificaciones por entidad financiera y evolución temporal](imagenes/4_Banco.png)

**Qué se observa en la captura:**

- **Filtros aplicados:** **Región = Andalucía**, **Fecha = 01/12/2025–28/12/2025** e **Indicador = Bonificaciones**, manteniendo el conjunto de bancos para compararlos entre sí.
- **Bonificaciones totales de la selección:** **228.346 €**.
- **Banco con mayores bonificaciones:** **Platino**, con **65.977 €**, seguido de **Oro** (**51.792 €**) y **Perla** (**48.133 €**).
- La línea del gráfico permite comparar estos importes con el **número de facturas**: **Rubí** registra **1.019 facturas** y **Perla**, **984**, mientras que **Platino** presenta **121 facturas** en la selección mostrada.
- El gráfico inferior muestra la **evolución temporal de las bonificaciones por banco**, útil para apreciar diferencias de comportamiento y concentraciones en determinados días.
- Las tablas permiten examinar el desglose bancario y llegar hasta las **facturas individuales** que originan las bonificaciones.

**¿Por qué se utilizan estos filtros?** Se conserva Andalucía y el mismo intervalo temporal que en la página Sociedad para **analizar ese territorio desde otra dimensión**. Al cambiar a Bonificaciones, se puede comprobar que **la entidad con más facturas no tiene por qué generar el mayor importe bonificado**.

---

## 6. Proveedor: análisis individualizado

La página **Proveedor** permite identificar qué proveedores concentran más anticipos, consultar sus datos descriptivos, revisar la evolución temporal y acceder al detalle de sus facturas. También permite **filtrar un proveedor concreto** para estudiar sus operaciones en profundidad.

### 6.1. Clasificación de proveedores

![Página Proveedor con clasificación por importe anticipado y detalle de operaciones](imagenes/5_1_Proveedor.png)

**Qué se observa en la captura:**

- **Filtros aplicados:** **Región = Andalucía**, **Fecha = 01/12/2025–28/12/2025** e **Indicador = Importes**, sin seleccionar todavía un proveedor específico.
- **Importe total anticipado en la selección:** **9.829.405 €**.
- **Proveedor con mayor importe anticipado:** **Piedras Modernizados S.A.**, con **86.163 €**.
- Le siguen **Condensadores Virtuales S.A.** (**79.377 €**) y **Adoquines Ágiles S.A.** (**78.406 €**). También destacan **Acumuladores Bajos S.L.** (**77.735 €**) y **Procesos Antifuego S.L.** (**70.384 €**).
- La tabla superior aporta información de los proveedores, como **región, CIF y sector**, junto a los importes; la inferior muestra el **detalle de las facturas anticipadas**.
- El gráfico de líneas permite observar la **evolución diaria de los importes del conjunto seleccionado**.

Esta vista facilita identificar a los proveedores más relevantes por volumen y elegir uno para investigar sus operaciones con mayor detalle.

### 6.2. Estudio de un proveedor concreto

![Página Proveedor filtrada por Piedras Modernizados S.A.](imagenes/5_2_Proveedor.png)

**Qué se observa en la captura:**

- Se mantienen **Andalucía**, **01/12/2025–28/12/2025** e **Importes**, y se aplica el filtro adicional **Proveedor = Piedras Modernizados S.A.**.
- La clasificación se reduce al proveedor seleccionado y muestra **86.163 €** de facturas anticipadas.
- El gráfico temporal se recalcula para representar **únicamente sus anticipos**, lo que permite apreciar cuándo se producen los picos de actividad.
- La tabla de detalle muestra las **sociedades del grupo**, los **bancos** y las **facturas** asociados a este proveedor, junto con fechas, plazos e importes.

**¿Por qué se elige este proveedor?** Porque **Piedras Modernizados S.A. es el que más importe anticipa en la selección anterior**. El filtro permite pasar del ranking general al detalle de sus operaciones, comprobando cómo se distribuyen en el tiempo y entre las distintas sociedades y entidades financieras.

---

## 7. Tecnologías utilizadas

| Herramienta | Uso en el proyecto |
|---|---|
| **Microsoft Power BI Desktop** | Desarrollo del informe y de las visualizaciones interactivas. |
| **Power Query / modelo de datos de Power BI** | Preparación y organización de los datos utilizados en el informe. |
| **Histórico CSV del pipeline** | Fuente de las operaciones de confirming previamente procesadas y comprobadas. |
| **Python, Google Drive y GitHub Actions** | Tecnologías del proyecto previo que automatiza la revisión y generación del histórico. |
| **GitHub** | Publicación y documentación de ambos proyectos. |

Este repositorio se centra en el **análisis visual**. El desarrollo de la automatización y las comprobaciones de confirming se documenta en **[Pipeline_Auditoria_Confirming](https://github.com/jjserranogarcia/Pipeline_Auditoria_Confirming)**.

---

## 8. Cómo abrir el informe

1. Descarga el archivo [`Report_Auditoria_Confirming.pbix`](Report_Auditoria_Confirming.pbix) de este repositorio.
2. Ábrelo con **Microsoft Power BI Desktop**.
3. Utiliza los botones inferiores para navegar por **Resumen**, **Sociedad**, **Banco** y **Proveedor**.
4. Prueba los filtros para explorar diferentes periodos, regiones y entidades.
5. Si deseas trabajar con un histórico actualizado, comprueba la **configuración del origen de datos** en Power BI Desktop y actualiza el modelo. En otro equipo puede ser necesario ajustar la ruta al archivo histórico.

### Estructura del repositorio

```text
Report_Auditoria_Confirming/
├── README.md
├── Report_Auditoria_Confirming.pbix
└── imagenes/
    ├── 1_1_Resumen.png
    ├── 1_2_Resumen.png
    ├── 2_Explicacion.png
    ├── 3_Sociedad.png
    ├── 4_Banco.png
    ├── 5_1_Proveedor.png
    └── 5_2_Proveedor.png
```

> **Importante:** las imágenes documentan **ejemplos de filtros y resultados**, no valores fijos del informe. Tanto los datos como las entidades representadas son ficticios.

---

**Proyecto relacionado:** [Pipeline_Auditoria_Confirming — Extracción, comprobación y monitorización automatizada de bonificaciones de confirming](https://github.com/jjserranogarcia/Pipeline_Auditoria_Confirming).
