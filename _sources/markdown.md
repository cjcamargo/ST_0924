## Bonus Teoricos
Se presentan 4 Bonus teoricos, por : Carlos Camargo.

## Bonus 1: Derivación del error estándar

El error estándar del coeficiente de autocorrelación \( r_k \) se obtiene tomando la raíz cuadrada de la varianza. A partir de la expresión aproximada de la varianza en el Paso 5, tenemos que:

$$
\text{se}(r_k) = \sqrt{\text{Var}(r_k)} = \sqrt{\frac{1}{T} \left( 1 + 2 \sum_{v=1}^{q} \rho_v^2 \right)}.
$$

### Simplificación para grandes \( k \)

Cuando el rezago \( k \) es lo suficientemente grande, es decir, \( k > q \), las autocorrelaciones \( \rho_v \) para \( v > q \) son insignificantes, ya que:

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

### Interpretación del resultado

Este resultado tiene una interpretación importante. Para rezagos grandes \( k \), las autocorrelaciones \( \rho_k \) son prácticamente cero, lo que implica que los valores de la serie temporal son casi independientes. En este caso, el error estándar del estimador \( r_k \) es similar al error estándar de una estimación basada en datos independientes, que es inversamente proporcional a la raíz cuadrada del tamaño de la muestra \( T \).

Por lo tanto, para grandes valores de \( k \), el error estándar del coeficiente de autocorrelación estimado es:

$$
\text{se}(r_k) \approx \frac{1}{\sqrt{T}}.
$$

## Bonus 2: Estadisticos de Box-Pierce

### Demostración: Similitud entre \( Q_{LB} \) y \( Q_{BP} \) cuando \( T \) es grande

### Definiciones de los estadísticos

El **estadístico de Box-Pierce** (\( Q_{BP} \)) se define como:

$$
Q_{BP} = T \sum_{k=1}^{K} r_k^2,
$$

donde:
- \( T \) es el tamaño de la muestra.
- \( r_k \) es el coeficiente de autocorrelación muestral en el rezago \( k \).
- \( K \) es el número de rezagos a considerar en la prueba.

El **estadístico de Ljung-Box** (\( Q_{LB} \)) se define como:

$$
Q_{LB} = T (T+2) \sum_{k=1}^{K} \left( \frac{1}{T - k} \right) r_k^2.
$$

### Paso 1: Comparación de las fórmulas

La diferencia entre los dos estadísticos está en el factor de ponderación. En \( Q_{LB} \), los coeficientes \( r_k^2 \) se ponderan por:

$$
\frac{T(T+2)}{T-k}.
$$

En \( Q_{BP} \), el coeficiente es simplemente \( T \). Ahora, vamos a estudiar el comportamiento asintótico de este factor cuando \( T \) es muy grande.

### Paso 2: Comportamiento asintótico cuando \( T \to \infty \)

Para \( T \) grande, observamos lo siguiente:
- \( T(T+2) \) se aproxima a \( T^2 \):
  
  $$
  T(T+2) = T^2 + 2T \approx T^2 \quad \text{cuando} \ T \ \text{es grande}.
  $$
  
- \( T - k \) también se aproxima a \( T \), ya que \( k \) es mucho menor que \( T \):
  
  $$
  T - k \approx T \quad \text{cuando} \ T \ \text{es grande}.
  $$

Por lo tanto, la fracción \( \frac{T(T+2)}{T-k} \) se simplifica para \( T \) grande:

$$
\frac{T(T+2)}{T-k} \approx \frac{T^2}{T} = T \quad \text{cuando} \ T \ \text{es grande}.
$$

### Paso 3: Simplificación del estadístico \( Q_{LB} \)

Cuando \( T \) es muy grande, podemos aproximar el estadístico de Ljung-Box \( Q_{LB} \) de la siguiente manera:

$$
Q_{LB} \approx T \sum_{k=1}^{K} r_k^2.
$$

Esta expresión es exactamente la misma que la fórmula del estadístico de Box-Pierce \( Q_{BP} \).

### Conclusión

Por lo tanto, cuando \( T \) es muy grande, los estadísticos \( Q_{LB} \) y \( Q_{BP} \) se vuelven prácticamente idénticos:

$$
Q_{LB} \approx Q_{BP}.
$$

Esto significa que, para muestras grandes, ambas pruebas producirán resultados muy similares.

## Bonus 3: Intervalos de predicción

### Modelo de tendencia lineal

El modelo de tendencia lineal está dado por:

$$
y_t = \hat{\beta}_0 + \hat{\beta}_1 t + \epsilon_t,
$$

donde \( \epsilon_t \sim N(0, \sigma^2_\epsilon) \).

El pronóstico para el tiempo \( T + \tau \) es:

$$
\hat{y}_{T+\tau} = \hat{y}_T + \hat{\beta}_1 \tau.
$$

### Pronóstico en términos de suavización exponencial

El pronóstico en términos de los suavizadores exponenciales de primer y segundo orden se puede escribir como:

$$
\hat{y}_{T+\tau}(T) = \left( 2 + \frac{\lambda}{1 - \lambda} \tau \right) \tilde{y}^{(1)}_T - \left( 1 + \frac{\lambda}{1 - \lambda} \tau \right) \tilde{y}^{(2)}_T,
$$

donde \( \lambda \) es el parámetro de suavización.

### Intervalo de predicción

El \( 100(1 - \alpha/2) \) intervalo de predicción está dado por:

$$
\hat{y}_{T+\tau} \pm Z_{\alpha/2} \frac{c_\tau}{c_1} \hat{\sigma}_\epsilon,
$$

donde:

- \( Z_{\alpha/2} \) es el valor crítico de la distribución normal estándar.
- \( \hat{\sigma}_\epsilon \) es la desviación estándar estimada del error.
- \( c_\tau \) y \( c_1 \) son factores de ajuste relacionados con el horizonte de predicción \( \tau \) y el parámetro \( \lambda \).

### Cálculo de \( c_\tau \)

El término \( c_\tau^2 \) está dado por:

$$
c_\tau^2 = 1 + \frac{\lambda}{(2 - \lambda)^3} \left[ (10 - 14 \lambda + 5 \lambda^2) + 2 \tau \lambda (4 - 3 \lambda) + 2 \tau^2 \lambda^2 \right].
$$

Este término ajusta el intervalo para reflejar la incertidumbre asociada con la predicción a futuro.

### Conclusión

El intervalo de predicción para el horizonte \( \tau \) incluye tanto el pronóstico basado en suavización exponencial como un término que captura la incertidumbre del error de estimación.

### Bonus 4 : Error Estandar Coef. Autocorrelacion Muestral

## Derivación del error estándar del coeficiente de autocorrelación muestral \( r(k) \)

La fórmula precisa para la varianza del coeficiente de autocorrelación muestral \( r(k) \) es:

$$
\text{Var}(r(k)) \approx \frac{1}{N} \left( 1 + 2 \sum_{j=1}^{k-1} r(j)^2 \right),
$$

donde \( N \) es el tamaño de la muestra y \( r(j) \) son los coeficientes de autocorrelación muestral en retardos anteriores a \( k \).

### Análisis inicial del proceso autoregresivo

Según Bartlett (1946), para un proceso autoregresivo \( AR(1) \), la varianza del coeficiente de autocorrelación estimado en el retardo \( k \) puede expresarse como:

$$
\text{Var}(r_k) \approx \frac{1}{T} \sum_{v=-\infty}^{\infty} \left( \rho_v^2 + \rho_{v+k}\rho_{v-k} - 4\rho_k\rho_v\rho_{v-k} + 2\rho_v^2 \rho_k^2 \right),
$$

donde \( \rho_v \) representa los coeficientes de autocorrelación teóricos y \( T \) es el tamaño de la muestra.

### Simplificación para valores grandes de \( k \)

Cuando \( k \) es grande y las autocorrelaciones en retardos mayores a \( k \) se vuelven insignificantes, esta expresión se simplifica como:

$$
\text{Var}(r(k)) \approx \frac{1}{T} \left( 1 + 2 \sum_{v=1}^{q} \rho_v^2 \right), \quad k > q.
$$

Aquí, \( q \) es un valor suficientemente grande donde la autocorrelación teórica es pequeña.

### Incorporación de los coeficientes de autocorrelación muestral

Si no conocemos los coeficientes de autocorrelación teóricos \( \rho_v \), usamos los coeficientes de autocorrelación muestral \( r(j) \) como aproximación. Entonces, reemplazamos \( \rho_v \) por \( r(j) \), lo que resulta en:

$$
\text{Var}(r(k)) \approx \frac{1}{N} \left( 1 + 2 \sum_{j=1}^{k-1} r(j)^2 \right).
$$

### Relación con el término \( 1 + 2 \sum r(j)^2 \)

El término \( 1 + 2 \sum_{j=1}^{k-1} r(j)^2 \) proviene del análisis de la autocovarianza y la estructura de la matriz de covarianza de los coeficientes de autocorrelación. Captura cómo las autocorrelaciones en los retardos anteriores afectan la varianza de \( r(k) \).

### Conclusión

Finalmente, el error estándar del coeficiente de autocorrelación muestral \( r(k) \) es:

$$
\text{s.e.}(r(k)) = \frac{1}{\sqrt{N}} \left( 1 + 2 \sum_{j=1}^{k-1} r(j)^2 \right)^{1/2}.
$$

Esta fórmula es más precisa que \( 1/\sqrt{N} \), ya que considera la influencia de las autocorrelaciones en los retardos anteriores, ajustando el error estándar según la dependencia serial en la serie temporal.
