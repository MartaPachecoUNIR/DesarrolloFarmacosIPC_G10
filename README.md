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

Esta carpeta contiene los scripts destinados al análisis computacional de proteínas mediante AlphaFold. Su finalidad es estudiar la estructura tridimensional de las proteínas y evaluar la fiabilidad de las predicciones estructurales, proporcionando información relevante para las etapas posteriores del descubrimiento y desarrollo de fármacos.

Por un lado, el fichero `simulacion_estructural.py` tiene como objetivo realizar el análisis de la estructura tridimensional de la proteína obtenida mediante AlphaFold. Permite estudiar su conformación espacial, identificar sus principales regiones estructurales y visualizar la disposición de sus aminoácidos. 

Este análisis proporciona información sobre la organización molecular de la proteína y permite identificar posibles regiones de interés para el estudio de interacciones con moléculas candidatas a fármacos.

Por otro lado, el fichero `prediccion_fiabilidad.py` tiene como objetivo evaluar la fiabilidad de la estructura tridimensional predicha mediante AlphaFold, a través del análisis de los principales indicadores de confianza: pLDDT (Predicted Local Distance Difference Test), PAE (Predicted Aligned Error), pTM (Predicted Template Modeling score) e ipTM (Interface Predicted Template Modeling score).

Estos parámetros permiten determinar el grado de confianza de la predicción a nivel local y global, identificar regiones estructuralmente inciertas y evaluar la confianza en las interfaces de interacción entre proteínas cuando se estudian complejos proteicos.

### 3. Optimización estructural mediante IA generativa

El objetivo principal de utilizar AlphaFold es predecir la estructura tridimensional de las proteínas seleccionadas como posibles dianas terapéuticas a partir de sus secuencias de aminoácidos. La carpeta alphafold/ se organiza en dos subcarpetas principales y un fichero independiente, cada uno destinado a almacenar una parte específica de la información necesaria para el análisis de las proteínas seleccionadas mediante AlphaFold.

El análisis mediante inteligencia artificial generativa se compone de 3 ficheros.
- El primero, llamado `structural_analysis.py` se encargaría de evaluar los modelos tridimensionales obtenidos mediante AlphaFold, identificando posibles regiones de baja confianza o imperfecciones estructurales.
- El segundo, llamado `conformational_generation.py` se encargaría de utilizar modelos de inteligencia artificial generativa para obtener conformaciones alternativas de las proteínas diana, explorando así su posible flexibilidad estructural.
- El tercero, llamado `validation_selection.py`, se encargaría de evaluar la calidad estructural de los modelos generados, comprobando su compatibilidad con la secuencia aminoacídica original y seleccionando aquellos más adecuados para su utilización en el posterior cribado virtual.

### 4. 

### 5. Análisis LADMET

Este módulo tiene como objetivo clasificar y priorizar las moléculas candidatas procedentes del módulo anterior según su perfil LADMET (Liberación, Absorción, Distribución, Metabolismo, Excreción y Toxicidad). 

Para ello, utilizará como datos de entrada los identificadores SMILES de los compuestos seleccionados y llevará a cabo las siguientes funciones:

  1. Cálculo de descriptores moleculares mediante 'molecular_descriptors.py', que permitirá obtener las principales propiedades fisicoquímicas de cada molécula (MW, LogP, TPSA, HBD, HBA)
  2. Entrenamiento y evaluación de un modelo de Machine Learning capaz de predecir las propiedades LADMET con 'model_training.py'
  3. Predicción de las propiedades LADME (Liberación, Absorción, Distribución, Metabolismo y Excreción) con 'ladme_prediction.py'
  4. Predicción de toxicidad con 'toxicity_prediction.py'
  5. Evaluación y clasificación final de los candidatos con 'ladmet_scoring.py'

---

## Salidas(outputs)

Este programa creará finalmente un archivo llamado 'final_candidates.csv' en la ruta indicada. Este archivo contendrá un ranking de los candidatos seleccionados según sus propiedades fisicoquímicas y farmacocinéticas que podrá ser utilizado para futuras fases de investigación en el desarrollo de fármacos. 

---

## Interpretación biológica


---

## Limitaciones y consideraciones

## Licencia

Este programa usa una Licencia Pública General GNU (GPLv3). Más información en el fichero `LICENSE`.
