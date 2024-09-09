# Data Mining aplicando el algoritmo 'Apriori' y clustering no supervisado con 'k-means'.

---

### Creador:
- Wilbert Vong

---

**Este trabajo consiste en obtener patrones de frecuencia de compras en un supermercado, y segmentación de los datos por departamento.**

*El dataset fue tomado de [Kaggle](https://www.kaggle.com/datasets/hunter0007/ecommerce-dataset-for-predictive-marketing-2023).*

---

## **Funcionamiento del algoritmo 'Apriori'**:

El algoritmo 'Apriori' es un método de aprendizaje no supervisado utilizado para la minería de reglas de asociación en grandes bases de datos. La forma en que este algoritmo consiste en diferentes fases: 

#### *Frecuencia de elementos*:
El algoritmo comienza por identificar todos los itemsets *(conjuntos de elementos)* que ocurren con una frecuencia mínima, especificada por el parámetro de soporte mínimo. Un itemset es un conjunto de artículos que aparecen juntos en transacciones.

#### *Generación de candidatos*:
A partir de los itemsets frecuentes de tamaño 1 *(itemsets de un solo elemento)*, 'Apriori' genera candidatos para itemsets más grandes *(de tamaño 2, 3, etc.)*. Esta expansión se hace utilizando el principio de que cualquier subconjunto de un itemset frecuente también debe ser frecuente.

#### *Pruning*:
Para reducir el espacio de búsqueda, el algoritmo descarta inmediatamente los itemsets candidatos cuyos subconjuntos no sean frecuentes, ya que no podrán cumplir con el umbral de soporte mínimo.

#### *Soporte*:
El soporte de un itemset se calcula como la proporción de transacciones en las que aparece dicho conjunto. Se comparan los soportes de los candidatos con el umbral mínimo de soporte.
El cálculo de Soporte está dado con la siguiente fórmula:

$$
\text{Support}(X) = \frac{\text{Número de transacciones que contienen } X}{\text{Número total de transacciones}}
$$

#### *Generación de reglas de asociación*:
Para cada itemset frecuente, se generan reglas de la forma:

**$X⇒Y$**, donde $X$ y $Y$ son subconjuntos del itemset. La fuerza de la regla se mide mediante dos métricas principales:

- Confianza: Es la probabilidad condicional de que $Y$ ocurra dado que $X$ ya ha ocurrido. Se calcula de la siguiente manera:

$$
\text{Confidence}(X \Rightarrow Y) = \frac{\text{Support}(X \cup Y)}{\text{Support}(X)}
$$

- Lift: Indica cuán dependientes son $X$ y $Y$, comparando la confianza de la regla con la frecuencia esperada de $Y$. Esto se calcula así:

$$
\text{Lift}(X \Rightarrow Y) = \frac{\text{Support}(X \cup Y)}{\text{Support}(X) \times \text{Support}(Y)}
$$

#### *Iteración*:
El proceso se repite para itemsets más grandes hasta que no se puedan generar más itemsets frecuentes.

---

## **Funcionamiento del Clustering No Supervisado 'K-Means'**:

El algoritmo K-means es un método de agrupamiento (clustering) no supervisado que organiza un conjunto de datos en 
$𝐾$ grupos (o clusters) según la similitud entre los puntos. Aquí detallo la manera en que se aplica:

#### *Inicialización*:
Se elige un número $𝐾$ de clusters (grupos) que se desea crear. Luego, se seleccionan aleatoriamente $𝐾$ centroides iniciales, que son puntos en el espacio que representan temporalmente el centro de cada cluster.

#### *Asignación de puntos*:
Cada punto de datos se asigna al cluster cuyo centroide esté más cerca, utilizando una métrica de distancia, donde la más aplicada es la **distancia euclidiana**, cuya fórmula es la siguiente:

$$
d(x, y) = \sqrt{\sum_{i=1}^{n} (y_i - x_i)^2}
$$

Donde:

* $x = (x_1, x_2, \dots, x_n)$ y $y = (y_1, y_2, \dots, y_n)$ son los dos puntos en el espacio.
* $x_i$ y $y_i$ son las coordenadas de los puntos $x$ y $y$ en la dimensión $i$.
* $d(x, y)$ es la distancia euclidiana entre los puntos $x$ y $y$.

#### *Actualización de centroides*:
Después de asignar todos los puntos a clusters, se recalculan los centroides. El nuevo centroide de cada cluster se calcula como el promedio de todos los puntos asignados a ese cluster.
La fórmula para actualizar el centroide de un cluster es:

$$
\mu_j = \frac{1}{|C_j|} \sum_{x \in C_j} x
$$

Donde:

- $\mu_j$ es el nuevo centroide del cluster $j$.

- $C_j$ es el conjunto de puntos que pertenecen al cluster $j$.

- $|C_j|$ es el número de puntos en el cluster $j$.

+ $x$ son los puntos de datos asignados al cluster $j$.

La suma $\sum_{x \in C_j} x$ calcula la suma de todas las coordenadas de los puntos en $C_j$, y luego se divide por el número total de puntos en ese cluster para obtener el promedio.

#### *Iteración*:
El proceso de asignar puntos a clusters y recalcular los centroides se repite hasta que los centroides ya no cambien significativamente o hasta que se alcance un número máximo de iteraciones. Este estado se denomina *convergencia*.

---

## Notebooks

[Patrones de compras con el algoritmo 'Apriori'](https://colab.research.google.com/drive/1HU9Pfiey0P_gFSqGzk7NwkBN2wgTcf8J?usp=sharing)

[Clustering no supervisado con 'k-means'](https://colab.research.google.com/drive/1wZcWlbwfqtBLabGzNjXKYES0S1k3f0qW?usp=sharing)
