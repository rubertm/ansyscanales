# Metodología

En este capitulo se presenta la metodología para modelar canales abiertos en el **Computational Fluid Dynamic** `CFD` **ANSYS CFX v11.0** `` {cite}`ANSYS_Europe` ``, con el proposito de estimar sus caudales y profundidades. Las estructuras se configuraron en el módulo de flujos a superficie libre del **ANSYS**, donde se modelan los *flujos multifase*. Las fases modeladas son: la fase líquida, agua y la fase gaseosa, aire.
{cite}`ANSYS_Europe`.

Primero, se construye la geometría en tres dimensiones y la malla en el módulo  **ANSYS Workbench**. En esta parte se debe tener detalles y dimensiones de la estructura, y un estimativo de las dimensiones de la malla a generar. Esto es importante para tener una representación real de la estructura.

```{tip}
Se debe encontrar la malla optima, **ANSYS** da algunas recomendaciones para configurar el tamaño de malla.
```
Segundo, se importa la malla, se específica la física del flujo, las condiciones límites, los valores iniciales y los parámetros de solución. En esta parte se debe conocer las propiedades de las fases, y las condiciones fisicas e hidráulicas de las fronteras, **Módulo CFD Pre del ANSYS**.

Finalmente, se procesan los resultados para conocer el comportamiento hidráulico y obtener las eficiencias hidráulicas de la estructura. Módulos **CFD Solver** y **Post** del **ANSYS**.

Para más acerca de **ANSYS**, ver [Ansys](https://www.ansys.com/)


## Validación de modelos a flujo libre en ANSYS

Para  validar los modelos a flujo libre en **ANSYS** se tomó un caso estudiado en el libro *Hidráulica de Canales de Ven Te Chow*. El caso corresponde a la caída hidráulica gradual con su punto de inflexión en la sección media de la contracción `` {cite}`Ven_Te_Chow_1994` `` . El caso estudiado parte de las ecuaciones teóricas de los principios de energía y momento, y los estudios experimentales que se han hecho sobre la caída hidráulica. {cite}`Ven_Te_Chow_1994`.

### *Validación caída hidráulica*

El propósito de esta validación es confrontar los resultados numéricos de la caída hidráulica obtenidos por las bases teóricas `` {cite}`Ven_Te_Chow_1994` `` y por el modelado en **ANSYS CFX v11.0**. Las bases teóricas para calcular las características del flujo por el cambio en la sección transversal cuando pasa de un estado subcrítico a un estado supercrítico están dadas por las siguientes expresiones: 

$$
\begin{align}
y\left(c\right) &= E / 1.5  && \text{donde: y(c) es altura de flujo critico y E es la energía}\\ 
\end{align}
$$

$$
\begin{align}
E &= y + Q^{2} / (2 * g * (b * y)^{2}) && \text{donde: g es la gravedad, Q el caudal, 'y' el nivel del flujo, y b el ancho del canal}\\ 
\end{align}
$$

$$
\begin{align}
V\left(c\right) &= (y(c) * g)^{0.5}  && \text{donde: V(c) es velocidad de flujo critico}\\ 
\end{align}
$$

$$
\begin{align}
a &= Q / (V(c) * y(c))  && \text{donde: a es el ancho de la sección crítica}\\ 
\end{align}
$$

El modelo en **ANSYS** se construyó con los siguientes datos:

|           **sección**             | **dimensión** |
|:---------------------------------:|--------------:|
|ancho del canal aguas arriba       |         3.05 m|
|ancho del canal aguas abajo        |         2.44 m|
|ancho del canal en la contracción  |         0.87 m|
|longitud del canal                 |        15.22 m|
|profundidad del flujo aguas arriba |         1.52 m|
|caudal                             |      2.83 m3/s|

El modelo construido en **ANSYS** tiene la siguientes características: número de nodos `6370`, número de elementos tetraedros `29753`, para un volumen de `88.39 m3`. La simulación se configuró para estado estático, se utilizó el modelo *multifase homogéneo* y el modelo de *turbulencia K – Epsilon*.

El modelo se construyó con los cinco tipos de frontera que soporta el **ANSYS**. En la entrada fue asignada la presión hidrostática y la velocidad de flujo. El fondo del canal se tomó como frontera tipo pared con una rugosidad de `0.3 mm`, en el techo del canal se tomó como frontera tipo abierta con presión atmosférica en el límite y condición permanente de aire, y los laterales como frontera tipo simétrica.

Los resultados de la corrida se realizaron para un máximo de `200` iteraciones, con un criterio de convergencia residual de `1.E-4`, se hizo un refinamiento de malla en la interfase agua – aire en dos niveles con `50` iteraciones máximas por paso, para un solo número de paso.

```{figure} ../images/figura1.jpg
---
height: 350px
name: tesis-fig1
---
 muestra la malla generada para el canal donde se simuló la caída hidráulica.
```

```{bibliography}
```

