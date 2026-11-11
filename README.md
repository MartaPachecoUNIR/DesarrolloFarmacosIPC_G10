# DesarrolloFarmacos_G10

## Autoría: 
  Marta Pacheco Cacho,
  María Isabel Rivero Bernabé,
  Miguel Ángel García de Castro,
  Ricardo Vidal Rosales,
  Valeria Natalie Fernández Morocho.

---

## Descripción

Este es un repositorio que contiene programa ficticio basado en python de diseño de fármacos.

El programa ayudaría a los investigadores a diseñar fármacos frente a diversas patologías mediante la identificación automatizada de dianas a partir de información de RNAseq. Así como la utilización de modelos in-sílico generados por alpha-fold y depurados por inteligencia artificial generativa de estas para la búsqueda de los principios activos que pudieran generar efectos beneficiosos para el paciente. Por último, el programa también ofrecería un último análisis de la toxicidad de dichos principios activos sobre el paciente.

> **Importante**: Esta herramienta permitiría la búsqueda in sílico de dichos principios activos, pero **no** aseguraría el correcto funcionamiento de estos en condiciones reales, por lo que resultaría esencial su estudio experimental in-vitro e in-vivo.

---

## Índice

- [Guía de instalación](#Guía-de-instalación)
- [Workflow](#Workflow)
- [Funcionamiento interno](#Funcionamiento-interno)
- [Salidas(outputs)](#Salidas(outputs))
- [Interpretación biológica](#Interpretación-biológica)
- [Limitaciones y consideraciones](#Limitaciones-y-consideraciones)
- [Licencia](#Licencia)

---

## Guía de instalación

El usuario deberá descargar el repositorio completo de GitHub y colocarlo en el lugar que este prefiera dentro de su ordenador.

Tras esto, el usuario podrá ejecutar el código usando el gestor de código de su preferencia (Virtual Studio Code...).
También se recomienda el uso de un entorno virtual dedicado, para así poder evitar posibles futuras incompatibilidades entre librerías.

Una vez hecho lo anterior, el usuario tan solo deberá ejecutar el fichero main.py desde su gestor, con el input y los parámetros propicios para su análisis.

---

## Workflow


---

## Funcionamiento interno

### 1. Análisis de RNAseq

El análisis del bruto del RNAseq se compone de 3 ficheros.
  -  El primero, llamado `calidad_y_filtrado.py` se encargaría de comprobar la calidad de cada uno de los transcritos secuenciados, así como del filtrado y la eliminación de aquellos que no lleguen a los requisitos previstos
  -  El segundo, llamado `alineamiento.py` se encargaría del alineamiento de los transcritos con el genoma de referencia, para así poder identificarlos
  -  El tercero, llamado `cuantificación_y_selección.py` se encargaría de cuantificar los distintos transcritos y, a partir de la expresión diferencial respecto a sus referencias, la selección de aquellos más llamativos como posibles dianas en el diseño de fármacos frente a la patología

### 2. AlphaFold 

### 3.

### 4. Cribado Virtual y Docking Molecular
El proceso de acoplamiento molecular y cribado virtual se compone de 4 ficheros, estos se encuentran en el directorio cribado_y_docking.

El primero, llamado 1_preparacion_proteína.md se encargaría de la adecuación de la estructura tridimensional de la diana, añadiendo hidrógenos y eliminando moléculas de H2O o ligandos.
El segundo, llamado 2_optimizacion _ligando.md se encargaría de ajustar el estado de ionización del ligando a pH fisiológico , añadiendo hidrógenos y minimizando su energía para lograr una conformación estable.
El tercero, llamado, 3_docking_molecular.mdse encargaría de ejecutar el acoplamiento molecular en el sitio de unión y evaluar la afinidad teórica y la precisión geométrica de las poses.
El cuarto, llamado 4_cribado_virtual.md se encargaría del cribado masivo de quimiotecas frente a la diana preparada para seleccionar a las mejores moléculas candidatas.

### 5.

---

## Salidas(outputs)

---

## Interpretación biológica


---

## Limitaciones y consideraciones

## Licencia

Este programa usa una Licencia Pública General GNU (GPLv3). Más información en el fichero `LICENSE`.
