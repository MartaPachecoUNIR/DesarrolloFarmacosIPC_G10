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
- [Entradas y Salidas](#Entradas-y-Salidas)
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

El programa partiría de un análisis de los resultados brutos de un RNAseq, de manera que podrían seleccionarse los principales candidatos a diana para el diseño de posibles los fármacos que pudieran permitir tratar la enfermedad.

El análisis del bruto del RNAseq se compone de 3 ficheros.
  -  El primero, llamado `calidad_y_filtrado.py` se encargaría de comprobar los distintos parámetros de calidad de cada uno de las lecturas de los transcritos secuenciados. De esta manera, el programa podría pasar al filtrado y la eliminación de aquellas lecturas, o fragmentos de estas, que no lleguen a los requisitos mínimos previstos, así como la eliminación de adaptadores y demás elementos ajenos a las propias secuencias, mejorando la calidad del secuenciado.
  -  El segundo, llamado `alineamiento.py` se encargaría del alineamiento de las lecturas con el genoma de referencia, reconstruyendo los distintos transcritos y, con gran probabilidad, permitiendo su identificación.
  -  El tercero, llamado `cuantificación_y_selección.py` se encargaría de cuantificar los distintos transcritos. Esto permitiría el cálculo de la expresión diferencial de los transcritos respecto a sus referencias en célula sana, pudiéndose seleccionar aquellos con las variaciones más significativas como posibles dianas para los posteriores análisis.

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

### 4. Cribado Virtual y Docking Molecular
El proceso de acoplamiento molecular y cribado virtual se compone de 4 ficheros, estos se encuentran en el directorio cribado_y_docking.

- El primero, llamado `1_preparacion_proteina.py` se encargaría de la adecuación de la estructura tridimensional de la diana, añadiendo hidrógenos y eliminando moléculas de H2O o ligandos.
- El segundo, llamado `2_optimizacion _ligando.py` se encargaría de ajustar el estado de ionización del ligando a pH fisiológico , añadiendo hidrógenos y minimizando su energía para lograr una conformación estable.
- El tercero, llamado, `3_docking_molecular.py` se encargaría de ejecutar el acoplamiento molecular en el sitio de unión y evaluar la afinidad teórica y la precisión geométrica de las poses.
- El cuarto, llamado `4_cribado_virtual.py` se encargaría del cribado masivo de quimiotecas frente a la diana preparada para seleccionar a las mejores moléculas candidatas.

### 5. Análisis LADMET

Este módulo tiene como objetivo clasificar y priorizar las moléculas candidatas procedentes del módulo anterior según su perfil LADMET (Liberación, Absorción, Distribución, Metabolismo, Excreción y Toxicidad). 

Para ello, utilizará como datos de entrada los identificadores SMILES de los compuestos seleccionados y llevará a cabo las siguientes funciones:

  1. Cálculo de descriptores moleculares mediante `molecular_descriptors.py`, que permitirá obtener las principales propiedades fisicoquímicas de cada molécula (MW, LogP, TPSA, HBD, HBA)
  2. Entrenamiento y evaluación de un modelo de Machine Learning mediante `model_training.py`, utilizando datos de referencia para desarrollar un modelo predictivo de las propiedades LADMET 
  3. Predicción de las propiedades LADME (Liberación, Absorción, Distribución, Metabolismo y Excreción) mediante `ladme_prediction.py`
  4. Predicción de toxicidad mediante `toxicity_prediction.py`
  5. Evaluación y clasificación final de los candidatos mediante `ladmet_scoring.py`, combinando los resultados obtenidos para establecer un ranking de prioridad según su perfil LADMET

---

## Entradas y Salidas

### Entradas

El programa abriría una ventana en la que el usuario podría señalar el directorio donde se encuentre el input del RNAseq que desea analizar. O bien podrá introducir directamente la ruta en la que se encuentra dicho directorio en el correspondiente lugar del fichero `main`.

### Salidas

Este programa creará finalmente un archivo llamado 'final_candidates(n).csv' dentro de una carpeta de resultados en la ruta especificada por el usuario (de no existir previemente la carpeta de resultados en dicha ruta, el programa la crearía). Este archivo contendrá los resultados de las predicciones LADMET de cada compuesto, incluyendo sus propiedades fisicoquímicas, farmacocinéticas y toxicológicas, así como una puntuación global que permitirá establecer un ranking de los candidatos más prometedores.

Los compuestos priorizados podrán seleccionarse para futuras fases de investigación en el desarrollo de fármacos. 

---

## Interpretación biológica

Desde un punto de vista biológico, este proyecto plantea una estrategia integrada de descubrimiento de nuevos candidatos terapéuticos frente a una patología, partiendo de la identificación de posibles dianas moleculares hasta la selección de compuestos con potencial farmacológico.

En primer lugar, el análisis de RNA-seq permite identificar genes y transcritos que presentan alteraciones en sus niveles de expresión respecto a las condiciones de referencia. Estas diferencias pueden estar relacionadas con los mecanismos moleculares implicados en el desarrollo de la patología y permiten seleccionar proteínas potencialmente relevantes como dianas terapéuticas.

Posteriormente, mediante AlphaFold se predice la estructura tridimensional de las proteínas seleccionadas, lo que permite estudiar su organización espacial, identificar regiones funcionales y valorar la fiabilidad de los modelos estructurales. La incorporación de herramientas de IA generativa permite explorar posibles cambios conformacionales y mejorar los modelos estructurales disponibles, teniendo en cuenta la flexibilidad natural de las proteínas.

Una vez definidas las estructuras de las posibles dianas, el cribado virtual y el docking molecular permiten estudiar las interacciones entre estas proteínas y diferentes moléculas candidatas, identificando aquellas que presentan una mayor compatibilidad estructural y una afinidad de unión teórica favorable.

Finalmente, el análisis LADMET permite evaluar las propiedades farmacocinéticas y toxicológicas de los compuestos seleccionados, estimando su liberación, absorción, distribución, metabolismo, excreción y posibles efectos tóxicos.

En conjunto, el proyecto integra análisis transcriptómico, modelado estructural, inteligencia artificial generativa, simulación molecular y aprendizaje automático para establecer un flujo de trabajo computacional orientado a identificar y priorizar moléculas con potencial terapéutico.

---

## Limitaciones y consideraciones

A pesar de que las herramientas computacionales empleadas permiten identificar y priorizar posibles dianas terapéuticas y moléculas candidatas de forma eficiente, es importante tener en cuenta que todos los resultados obtenidos mediante este proyecto son predicciones in silico y, por tanto, presentan ciertas limitaciones. Los resultados obtenidos deben interpretarse como una herramienta de priorización y generación de hipótesis que requiere posteriores procesos de validación biológica y farmacológica, incluyendo ensayos in vitro, estudios celulares y, cuando proceda, modelos in vivo, para confirmar la relevancia de las dianas seleccionadas, la actividad terapéutica de los compuestos y su seguridad antes de considerar cualquier posible aplicación clínica.

## Licencia

Este programa usa una Licencia Pública General GNU (GPLv3). Más información en el fichero `LICENSE`.
