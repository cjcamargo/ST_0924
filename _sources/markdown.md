## Bonus Teoricos
Se presentan 4 Bonus teoricos, por : Carlos Camargo.

## Bonus 1: Derivación del error estándar

El error estándar del coeficiente de autocorrelación $ ( r_k ) $ se obtiene tomando la raíz cuadrada de la varianza. A partir de la expresión aproximada de la varianza en el Paso 5, tenemos que:

$$
\text{se}(r_k) = \sqrt{\text{Var}(r_k)} = \sqrt{\frac{1}{T} \left( 1 + 2 \sum_{v=1}^{q} \rho_v^2 \right)}.
$$

### Simplificación para grandes \( k \)

Cuando el rezago \( k \) es lo suficientemente grande, es decir, \( k > q \), las autocorrelaciones $( \rho_v ) $ para \( v > q \) son insignificantes, ya que:

$$
\rho_v = \phi^v \quad \text{y} \quad \phi^{v} \text{ decrece exponencialmente}.
$$

Esto permite hacer la siguiente simplificación:

$$
\sum_{v=1}^{q} \rho_v^2 \approx 0 \quad \text{para grandes valores de } k.
$$

Por lo tanto, la varianza se aproxima a:

$$
\text{Var}(r_k) \simeq \frac{1}{T}.
$$

### Error estándar simplificado

Al tomar la raíz cuadrada de esta expresión, obtenemos el **error estándar**:

$$
\text{se}(r_k) \simeq \sqrt{\frac{1}{T}} = \frac{1}{\sqrt{T}}.
$$

Este resultado tiene una interpretación importante. Para rezagos grandes \( k \), las autocorrelaciones $ ( \rho_k ) $ son prácticamente cero, lo que implica que los valores de la serie temporal son casi independientes. En este caso, el error estándar del estimador $ ( r_k ) $ es similar al error estándar de una estimación basada en datos independientes, que es inversamente proporcional a la raíz cuadrada del tamaño de la muestra \( T \).

Por lo tanto, para grandes valores de \( k \), el error estándar del coeficiente de autocorrelación estimado es:

$$
\text{se}(r_k) \approx \frac{1}{\sqrt{T}}.
$$

## Bonus 2: Estadisticos de Box-Pierce

#### Demostración: Similitud entre $ ( Q_{LB} )  y  ( Q_{BP} ) $ cuando \( T \) es grande

### Definiciones de los estadísticos

El **estadístico de Box-Pierce** $ ( Q_{BP} ) $ se define como:

$$
Q_{BP} = T \sum_{k=1}^{K} r_k^2,
$$

donde:
-  \( T \) es el tamaño de la muestra.
- \( r_k \) es el coeficiente de autocorrelación muestral en el rezago \( k \).
- \( K \) es el número de rezagos a considerar en la prueba.

El **estadístico de Ljung-Box** $ ( Q_{LB} ) $ se define como:

$$
Q_{LB} = T (T+2) \sum_{k=1}^{K} \left( \frac{1}{T - k} \right) r_k^2.
$$

### Comparación de las fórmulas

La diferencia entre los dos estadísticos está en el factor de ponderación. En $ ( Q_{LB} ) $, los coeficientes $ ( r_k^2 ) $ se ponderan por:

$$
\frac{T(T+2)}{T-k}.
$$

En $ ( Q_{BP} ) $, el coeficiente es simplemente \( T \). Ahora, vamos a estudiar el comportamiento asintótico de este factor cuando \( T \) es muy grande.

###  Comportamiento asintótico cuando $ ( T \to \infty ) $

Para \( T \) grande, observamos lo siguiente:
- \( T(T+2) \) se aproxima a  \( T^2 \): 
  
  $$
  T(T+2) = T^2 + 2T \approx T^2 \quad \text{cuando} \ T \ \text{es grande}.
  $$
  
- \( T - k \) también se aproxima a \( T \), ya que \( k \) es mucho menor que \( T \):
  
  $$
  T - k \approx T \quad \text{cuando} \ T \ \text{es grande}.
  $$

Por lo tanto, la fracción $ ( \frac{T(T+2)}{T-k} ) $ se simplifica para \( T \) grande:

$$
\frac{T(T+2)}{T-k} \approx \frac{T^2}{T} = T \quad \text{cuando} \ T \ \text{es grande}.
$$

### Simplificación del estadístico $ ( Q_{LB} ) $

Cuando \( T \) es muy grande, podemos aproximar el estadístico de Ljung-Box $ ( Q_{LB} ) $ de la siguiente manera:

$$
Q_{LB} \approx T \sum_{k=1}^{K} r_k^2.
$$

Esta expresión es exactamente la misma que la fórmula del estadístico de Box-Pierce $ ( Q_{BP} ) $.

Por lo tanto, cuando \( T \) es muy grande, los estadísticos $ ( Q_{LB} ) y  ( Q_{BP} ) $ se vuelven prácticamente idénticos:

$$
Q_{LB} \approx Q_{BP}.
$$

Esto significa que, para muestras grandes, ambas pruebas producirán resultados muy similares.


### Bonus 3 : Error Estandar Coef. Autocorrelacion Muestral

### Derivación del error estándar del coeficiente de autocorrelación muestral $ ( r(k) ) $

La fórmula precisa para la varianza del coeficiente de autocorrelación muestral $ ( r(k) ) $ es:

$$
\text{Var}(r(k)) \approx \frac{1}{N} \left( 1 + 2 \sum_{j=1}^{k-1} r(j)^2 \right),
$$

donde \( N \) es el tamaño de la muestra y $ ( r(j) ) $ son los coeficientes de autocorrelación muestral en retardos anteriores a \( k \).

### Análisis inicial del proceso autoregresivo

Según Bartlett (1946), para un proceso autoregresivo $ ( AR(1) ) $, la varianza del coeficiente de autocorrelación estimado en el retardo \( k \) puede expresarse como:

$$
\text{Var}(r_k) \approx \frac{1}{T} \sum_{v=-\infty}^{\infty} \left( \rho_v^2 + \rho_{v+k}\rho_{v-k} - 4\rho_k\rho_v\rho_{v-k} + 2\rho_v^2 \rho_k^2 \right),
$$

donde $ ( \rho_v ) $ representa los coeficientes de autocorrelación teóricos y \( T \) es el tamaño de la muestra.

### Simplificación para valores grandes de \( k \)

Cuando \( k \) es grande y las autocorrelaciones en retardos mayores a \( k \) se vuelven insignificantes, esta expresión se simplifica como:

$$
\text{Var}(r(k)) \approx \frac{1}{T} \left( 1 + 2 \sum_{v=1}^{q} \rho_v^2 \right), \quad k > q.
$$

Aquí, \( q \) es un valor suficientemente grande donde la autocorrelación teórica es pequeña.

### Incorporación de los coeficientes de autocorrelación muestral

Si no conocemos los coeficientes de autocorrelación teóricos $ ( \rho_v ) $, usamos los coeficientes de autocorrelación muestral $ ( r(j) ) $ como aproximación. Entonces, reemplazamos $ ( \rho_v ) $ por $ ( r(j) ) $, lo que resulta en:

$$
\text{Var}(r(k)) \approx \frac{1}{N} \left( 1 + 2 \sum_{j=1}^{k-1} r(j)^2 \right).
$$

### Relación con el término $ ( 1 + 2 \sum r(j)^2 ) $

El término $ ( 1 + 2 \sum_{j=1}^{k-1} r(j)^2 ) $ proviene del análisis de la autocovarianza y la estructura de la matriz de covarianza de los coeficientes de autocorrelación. Captura cómo las autocorrelaciones en los retardos anteriores afectan la varianza de $ ( r(k) ) $.


Finalmente, el error estándar del coeficiente de autocorrelación muestral $ ( r(k) ) $ es:

$$
\text{s.e.}(r(k)) = \frac{1}{\sqrt{N}} \left( 1 + 2 \sum_{j=1}^{k-1} r(j)^2 \right)^{1/2}.
$$

Esta fórmula es más precisa que $ ( 1/\sqrt{N} ) $, ya que considera la influencia de las autocorrelaciones en los retardos anteriores, ajustando el error estándar según la dependencia serial en la serie temporal.

## Bonus 4: Significancia Estadistica del coeficiente de correlación muestral

### Derivación del límite de significancia estadística $ (\pm \frac{2}{\sqrt{N}}) $

###  Distribución de la autocorrelación parcial estimada
Cuando se calcula la autocorrelación parcial estimada $ (\hat{\phi}_{kk}) $, esta sigue aproximadamente una distribución normal para muestras grandes. Para un proceso $ (AR(p)) $, la varianza de $ (\hat{\phi}_{kk}) $ es inversamente proporcional al tamaño de la muestra \(N\):

$$
\hat{\phi}_{kk} \sim N\left(0, \frac{1}{N}\right)
$$

Esto implica que, en promedio, la autocorrelación parcial estimada será cero si no hay autocorrelación verdadera, con una varianza que disminuye al aumentar \(N\), lo que mejora la precisión de la estimación.

###  Relación entre varianza y desviación estándar
La varianza de $ (\hat{\phi}_{kk}) $ es $ (\frac{1}{N}) $, por lo que la desviación estándar es:

$$
\frac{1}{\sqrt{N}}
$$

Este comportamiento es típico en estimaciones basadas en muestras: a medida que \(N\) crece, la precisión de la estimación mejora.

###  Relación con el intervalo de confianza
Para establecer límites de confianza al 95%, usamos la fórmula:

$$
\text{Estimación} \pm \left(Z_{\alpha/2} \times \text{Desviación estándar}\right)
$$

Donde $ (Z_{\alpha/2} \approx 1.96) $ para un intervalo del 95%. Con la desviación estándar $ (\frac{1}{\sqrt{N}}) $, los límites de confianza se expresan como:

$$
\hat{\phi}_{kk} \pm \frac{2}{\sqrt{N}}
$$

Este es el límite comúnmente utilizado para muestras grandes, donde la aproximación normal es válida.

###  Significancia estadística
Si $ (\hat{\phi}_{kk}) $ cae fuera del rango $ (\pm \frac{2}{\sqrt{N}}) $, es estadísticamente significativa al 95%, indicando que la autocorrelación parcial no es cero.


En el trabajo de **Quenouille (1949)** se detalla que, en **muestras pequeñas**, los coeficientes de autocorrelación pueden tener **distribuciones más complejas** y que los límites de confianza deben ajustarse usando la **t de Student** para reflejar mejor la variabilidad. Quenouille sugiere que los límites de confianza en estas situaciones tienden a ser **asimétricos**.

Así: 

- Para **muestras grandes**, la aproximación normal con límite $ (\pm \frac{2}{\sqrt{N}}) $ es válida.
- Para **muestras pequeñas**, es más adecuado utilizar la **distribución t de Student**, que ajusta mejor la variabilidad e introduce límites asimétricos que mejor capturan la incertidumbre en la estimación.
