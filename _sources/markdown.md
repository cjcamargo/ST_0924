## Bonus Teoricos
Se presentan 4 Bonus teoricos, por : Andres Usma y Carlos Camargo.

# Bono 1: Demostración detallada del cálculo de la varianza de \(\hat{\rho}_k\) y obtención del error estándar para rezagos grandes

## Introducción

En esta demostración, realizaremos un análisis matemático detallado para calcular la varianza de la autocorrelación muestral \(\hat{\rho}_k\) en un proceso autorregresivo (AR) de orden \( q \) para rezagos grandes \( k > q \). Nos enfocaremos en los pasos algebraicos y matemáticos para llegar al resultado:

$$
\text{Var}(\hat{\rho}_k) \approx \frac{1}{n}
$$

y, por lo tanto, el error estándar:

$$
\text{SE}(\hat{\rho}_k) = \sqrt{\text{Var}(\hat{\rho}_k)} \approx \frac{1}{\sqrt{n}}
$$

donde \( n \) es el tamaño de la muestra.

## Objetivo

Calcular detalladamente la varianza de \(\hat{\rho}_k\) para \( k > q \) en un proceso AR(\( q \)) y demostrar que \(\text{Var}(\hat{\rho}_k) \approx \frac{1}{n}\).

## Desarrollo de la demostración

### 1. Definición del proceso AR(\( q \))

Un proceso autorregresivo de orden \( q \), AR(\( q \)), está dado por:

$$
X_t = \phi_1 X_{t-1} + \phi_2 X_{t-2} + \dots + \phi_q X_{t-q} + \varepsilon_t
$$

donde:

- \( \phi_i \) son los coeficientes autorregresivos.
- \( \varepsilon_t \) es un ruido blanco con media cero y varianza constante \( \sigma^2 \):

  $$
  E[\varepsilon_t] = 0, \quad E[\varepsilon_t^2] = \sigma^2, \quad E[\varepsilon_t \varepsilon_s] = 0 \text{ para } t \neq s
  $$

### 2. Propiedades de las autocorrelaciones en un proceso AR(\( q \))

Las autocorrelaciones teóricas \(\rho_k\) satisfacen las ecuaciones de Yule-Walker:

Para \( k = 1, 2, \dots, q \):

$$
\rho_k = \sum_{i=1}^q \phi_i \rho_{k - i}
$$

Con \( \rho_0 = 1 \).

Para \( k > q \):

Las autocorrelaciones \(\rho_k\) dependen de las anteriores, pero en procesos estacionarios, decaen exponencialmente hacia cero. Para \( k > q \), podemos asumir que \(\rho_k \approx 0\).

### 3. Definición de la autocorrelación muestral \(\hat{\rho}_k\)

La autocorrelación muestral para un rezago \( k \) se define como:

$$
\hat{\rho}_k = \frac{\sum_{t=1}^{n - k} (X_t - \bar{X})(X_{t + k} - \bar{X})}{\sum_{t=1}^{n} (X_t - \bar{X})^2}
$$

Donde \( \bar{X} \) es la media muestral:

$$
\bar{X} = \frac{1}{n} \sum_{t=1}^{n} X_t
$$

Sin pérdida de generalidad, podemos asumir que la serie tiene media cero (\( \bar{X} = 0 \)), lo cual simplifica los cálculos:

$$
\hat{\rho}_k = \frac{\sum_{t=1}^{n - k} X_t X_{t + k}}{\sum_{t=1}^{n} X_t^2}
$$

### 4. Cálculo de la varianza de \(\hat{\rho}_k\)

Queremos calcular:

$$
\text{Var}(\hat{\rho}_k) = E\left[ \left( \hat{\rho}_k - \rho_k \right)^2 \right]
$$

Dado que para \( k > q \), \(\rho_k \approx 0\), podemos aproximar:

$$
\text{Var}(\hat{\rho}_k) = E\left[ \hat{\rho}_k^2 \right]
$$

#### 4.1. Expansión de \(\hat{\rho}_k\)

Utilizando la definición:

$$
\hat{\rho}_k = \frac{\sum_{t=1}^{n - k} X_t X_{t + k}}{\sum_{t=1}^{n} X_t^2}
$$

Sea \( D = \sum_{t=1}^{n} X_t^2 \).

Entonces:

$$
\hat{\rho}_k = \frac{1}{D} \sum_{t=1}^{n - k} X_t X_{t + k}
$$

#### 4.2. Cálculo de \( E[\hat{\rho}_k^2] \)

Tenemos:

$$
E[\hat{\rho}_k^2] = E\left[ \left( \frac{1}{D} \sum_{t=1}^{n - k} X_t X_{t + k} \right)^2 \right]
$$

Como \( D \) es una constante dado que estamos condicionando en los datos, podemos extraer \( \frac{1}{D^2} \):

$$
E[\hat{\rho}_k^2] = \frac{1}{D^2} E\left[ \left( \sum_{t=1}^{n - k} X_t X_{t + k} \right)^2 \right]
$$

Expandiendo el cuadrado:

$$
\left( \sum_{t=1}^{n - k} X_t X_{t + k} \right)^2 = \sum_{t=1}^{n - k} \sum_{s=1}^{n - k} X_t X_{t + k} X_s X_{s + k}
$$

Entonces:

$$
E[\hat{\rho}_k^2] = \frac{1}{D^2} \sum_{t=1}^{n - k} \sum_{s=1}^{n - k} E\left[ X_t X_{t + k} X_s X_{s + k} \right]
$$

#### 4.3. Cálculo de la esperanza \( E[ X_t X_{t + k} X_s X_{s + k} ] \)

Consideramos dos casos:

1. **Cuando \( t = s \)**:

   $$
   E[ X_t X_{t + k} X_t X_{t + k} ] = E[ X_t^2 X_{t + k}^2 ] = E[ X_t^2 ] E[ X_{t + k}^2 ] \quad (\text{asumiendo incorrelación})
   $$

   Para \( k > q \), podemos aproximar que \( X_t \) y \( X_{t + k} \) están incorrelacionados (\( \rho_k \approx 0 \)).

   Por lo tanto:

   $$
   E[ X_t^2 X_{t + k}^2 ] \approx E[ X_t^2 ] E[ X_{t + k}^2 ] = (\gamma_0)^2
   $$

2. **Cuando \( t \neq s \)**:

   Si \( |t - s| \geq q \), entonces \( X_t \) es aproximadamente incorrelacionado con \( X_s \) y con \( X_{s + k} \).

   Entonces:

   $$
   E[ X_t X_{t + k} X_s X_{s + k} ] \approx E[ X_t ] E[ X_{t + k} ] E[ X_s ] E[ X_{s + k} ] = 0
   $$

   Porque \( E[X_t] = 0 \).

#### 4.4. Simplificación de la suma

Dado lo anterior, solo los términos donde \( t = s \) contribuyen significativamente:

$$
E[\hat{\rho}_k^2] \approx \frac{1}{D^2} \sum_{t=1}^{n - k} E[ X_t^2 X_{t + k}^2 ] = \frac{1}{D^2} (n - k) (\gamma_0)^2
$$

#### 4.5. Aproximación de \( D \)

Sabemos que:

$$
D = \sum_{t=1}^{n} X_t^2
$$

El valor esperado de \( D \) es:

$$
E[D] = n \gamma_0
$$

Podemos aproximar \( D \approx n \gamma_0 \) para \( n \) grande.

#### 4.6. Cálculo final de \( E[\hat{\rho}_k^2] \)

Sustituyendo en la expresión de \( E[\hat{\rho}_k^2] \):

$$
E[\hat{\rho}_k^2] \approx \frac{(n - k) (\gamma_0)^2}{(n \gamma_0)^2} = \frac{n - k}{n^2}
$$

Para \( n \) grande y \( k \ll n \), tenemos que \( n - k \approx n \), entonces:

$$
E[\hat{\rho}_k^2] \approx \frac{n}{n^2} = \frac{1}{n}
$$

Por lo tanto:

$$
\text{Var}(\hat{\rho}_k) = E[\hat{\rho}_k^2] \approx \frac{1}{n}
$$

### 5. Conclusión

Hemos demostrado que, para \( k > q \) y bajo los supuestos mencionados, la varianza de \(\hat{\rho}_k\) es aproximadamente:

$$
\text{Var}(\hat{\rho}_k) \approx \frac{1}{n}
$$

Por lo tanto, el error estándar es:

$$
\text{SE}(\hat{\rho}_k) = \sqrt{\text{Var}(\hat{\rho}_k)} \approx \frac{1}{\sqrt{n}}
$$

---

**Referencias**:

- **Bartlett, M. S. (1946)**. *On the Theoretical Specification and Sampling Properties of Autocorrelated Time-Series*. **Journal of the Royal Statistical Society**, 8(1), 27-41.

---

# Fin de la demostración


# Bono 2: Demostración de la Equivalencia Asintótica entre los Estadísticos de Ljung-Box y Box-Pierce

## Introducción

En el análisis de series temporales, las pruebas de **Ljung-Box** y **Box-Pierce** son métodos estadísticos utilizados para detectar la presencia de autocorrelación en los residuos de un modelo ajustado. Aunque sus formulaciones difieren ligeramente, se vuelven asintóticamente equivalentes a medida que el tamaño de la muestra \( n \) se hace grande.

## Definiciones

1. **Estadístico de Box-Pierce**:

   $$
   Q_{\text{BP}} = n \sum_{k=1}^h \hat{\rho}_k^2
   $$

2. **Estadístico de Ljung-Box**:

   $$
   Q_{\text{LB}} = n(n+2) \sum_{k=1}^h \frac{\hat{\rho}_k^2}{n - k}
   $$

Donde:

- \( n \) es el tamaño de la muestra.
- \( h \) es el número de rezagos analizados (típicamente \( h \ll n \)).
- \( \hat{\rho}_k \) es la autocorrelación muestral en el rezago \( k \).

## Objetivo

Nuestro objetivo es demostrar que:

$$
\lim_{n \to \infty} \left( Q_{\text{LB}} - Q_{\text{BP}} \right) = 0
$$

Esto demuestra que \( Q_{\text{LB}} \) y \( Q_{\text{BP}} \) son asintóticamente equivalentes cuando \( n \to \infty \).

## Demostración

### Paso 1: Reescribir \( Q_{\text{LB}} \) en términos de \( Q_{\text{BP}} \)

Comenzamos expresando \( Q_{\text{LB}} \) de una forma similar a \( Q_{\text{BP}} \):

$$
Q_{\text{LB}} = n(n+2) \sum_{k=1}^h \frac{\hat{\rho}_k^2}{n - k}
$$

Reescribimos el denominador:

$$
\frac{1}{n - k} = \frac{1}{n \left( 1 - \frac{k}{n} \right)} = \frac{1}{n} \cdot \frac{1}{1 - \frac{k}{n}}
$$

Por lo tanto,

$$
Q_{\text{LB}} = n(n+2) \sum_{k=1}^h \hat{\rho}_k^2 \left( \frac{1}{n} \cdot \frac{1}{1 - \frac{k}{n}} \right) = (n+2) \sum_{k=1}^h \hat{\rho}_k^2 \left( \frac{1}{1 - \frac{k}{n}} \right)
$$

### Paso 2: Expandir el denominador utilizando la serie de Taylor

Para \( n \) grande y pequeño \( \frac{k}{n} \), podemos usar la expansión en serie de Taylor:

$$
\frac{1}{1 - x} = 1 + x + x^2 + x^3 + \dots, \quad \text{para} \quad |x| < 1
$$

Sea \( x = \frac{k}{n} \), entonces:

$$
\frac{1}{1 - \frac{k}{n}} = 1 + \frac{k}{n} + \left( \frac{k}{n} \right)^2 + \left( \frac{k}{n} \right)^3 + \dots
$$

### Paso 3: Aproximar \( Q_{\text{LB}} \) utilizando la expansión

Sustituimos la expansión en \( Q_{\text{LB}} \):

$$
Q_{\text{LB}} = (n+2) \sum_{k=1}^h \hat{\rho}_k^2 \left( 1 + \frac{k}{n} + \left( \frac{k}{n} \right)^2 + \dots \right)
$$

Además, expresamos \( n+2 \) como:

$$
n+2 = n \left( 1 + \frac{2}{n} \right)
$$

Por lo tanto:

$$
Q_{\text{LB}} = n \left( 1 + \frac{2}{n} \right) \sum_{k=1}^h \hat{\rho}_k^2 \left( 1 + \frac{k}{n} + \left( \frac{k}{n} \right)^2 + \dots \right)
$$

### Paso 4: Multiplicar y simplificar términos

Multiplicando las expresiones y reteniendo términos hasta \( \frac{1}{n} \):

$$
Q_{\text{LB}} \approx n \left( 1 + \frac{2}{n} \right) \sum_{k=1}^h \hat{\rho}_k^2 \left( 1 + \frac{k}{n} \right)
$$

Simplificamos dentro de la suma:

$$
\left( 1 + \frac{2}{n} \right) \left( 1 + \frac{k}{n} \right) = 1 + \frac{2}{n} + \frac{k}{n} + \frac{2k}{n^2}
$$

Despreciando el término \( \frac{2k}{n^2} \):

$$
Q_{\text{LB}} \approx n \sum_{k=1}^h \hat{\rho}_k^2 \left( 1 + \frac{2 + k}{n} \right)
$$

### Paso 5: Separar la suma

Dividimos la expresión:

$$
Q_{\text{LB}} \approx n \sum_{k=1}^h \hat{\rho}_k^2 + \sum_{k=1}^h \hat{\rho}_k^2 (2 + k)
$$

Reconocemos que:

$$
Q_{\text{BP}} = n \sum_{k=1}^h \hat{\rho}_k^2
$$

Por lo tanto, la diferencia es:

$$
Q_{\text{LB}} - Q_{\text{BP}} \approx \sum_{k=1}^h \hat{\rho}_k^2 (2 + k)
$$

### Paso 6: Evaluar el valor esperado bajo la hipótesis nula

Bajo la hipótesis nula:

- \( E[\hat{\rho}_k] = 0 \)
- \( \text{Var}(\hat{\rho}_k) = \frac{1}{n} \)

Así:

$$
E[\hat{\rho}_k^2] = \text{Var}(\hat{\rho}_k) = \frac{1}{n}
$$

Entonces:

$$
E[Q_{\text{LB}} - Q_{\text{BP}}] \approx \sum_{k=1}^h \frac{1}{n} (2 + k)
$$

Calculamos la suma:

$$
E[Q_{\text{LB}} - Q_{\text{BP}}] = \frac{1}{n} \left( 2h + \frac{h(h+1)}{2} \right) = \frac{h^2 + 5h}{2n}
$$

### Paso 7: Conclusión

Cuando \( n \to \infty \):

$$
E[Q_{\text{LB}} - Q_{\text{BP}}] \to 0
$$

Por lo tanto:

$$
Q_{\text{LB}} - Q_{\text{BP}} \xrightarrow{P} 0
$$

---

# Fin de la Demostración

# Bono 3: Derivación del Error Estándar del Coeficiente de Autocorrelación Muestral \( r(k) \)

## Introducción

En el análisis de series temporales, el **coeficiente de autocorrelación muestral** \( r(k) \) es una estimación de la autocorrelación verdadera \( \rho(k) \) en el rezago \( k \). Conocer la **varianza** y el **error estándar** de \( r(k) \) es esencial para evaluar la significancia estadística de las autocorrelaciones estimadas y para construir intervalos de confianza.

Nuestro objetivo es **derivar matemáticamente** el error estándar de \( r(k) \), especialmente para rezagos grandes \( k \), bajo el supuesto de que las autocorrelaciones verdaderas más allá de un cierto rezago \( q \) son cero (\( \rho(k) = 0 \) para \( k > q \)). También incluiremos la **fórmula reducida que Bartlett encontró** para la varianza de \( r(k) \).

## Definiciones y Supuestos

1. **Serie Temporal**: Consideramos una serie temporal \( \{X_t\}_{t=1}^n \) con media cero (\( \bar{X} = 0 \)) y varianza constante \( \gamma_0 = \text{Var}(X_t) \).

2. **Coeficiente de Autocorrelación Muestral**:

   $$
   r(k) = \frac{\sum_{t=1}^{n - k} X_t X_{t + k}}{\sum_{t=1}^{n} X_t^2}
   $$

3. **Autocorrelaciones Verdaderas**: Suponemos que las autocorrelaciones verdaderas son cero para \( k > q \):

   $$
   \rho(k) = 0 \quad \text{para} \quad k > q
   $$

4. **Independencia Aproximada**: Para \( k > q \), asumimos que \( X_t \) y \( X_{t + k} \) son independientes.

## Objetivo

Demostrar que, para rezagos grandes \( k > q \):

1. La varianza del coeficiente de autocorrelación muestral es:

   $$
   \text{Var}[r(k)] \approx \frac{1}{n}
   $$

2. El error estándar es:

   $$
   \text{SE}[r(k)] = \sqrt{\text{Var}[r(k)]} \approx \frac{1}{\sqrt{n}}
   $$

## Demostración

### Paso 1: Expresión de \( r(k) \)

Con \( \bar{X} = 0 \), el coeficiente de autocorrelación muestral se simplifica a:

$$
r(k) = \frac{\sum_{t=1}^{n - k} X_t X_{t + k}}{\sum_{t=1}^{n} X_t^2}
$$

Sea:

$$
S = \sum_{t=1}^{n} X_t^2
$$

Entonces:

$$
r(k) = \frac{1}{S} \sum_{t=1}^{n - k} X_t X_{t + k}
$$

### Paso 2: Cálculo de la Varianza de \( r(k) \)

La varianza es:

$$
\text{Var}[r(k)] = E\left[ \left( r(k) - E[r(k)] \right)^2 \right]
$$

Para \( k > q \), \( \rho(k) = 0 \), y como \( E[X_t] = 0 \), tenemos:

$$
E[r(k)] = E\left[ \frac{1}{S} \sum_{t=1}^{n - k} X_t X_{t + k} \right] = \frac{1}{S} \sum_{t=1}^{n - k} E[X_t X_{t + k}] = 0
$$

Por lo tanto:

$$
\text{Var}[r(k)] = E\left[ r(k)^2 \right]
$$

### Paso 3: Expansión de \( r(k)^2 \)

Tenemos:

$$
r(k)^2 = \left( \frac{1}{S} \sum_{t=1}^{n - k} X_t X_{t + k} \right)^2 = \frac{1}{S^2} \left( \sum_{t=1}^{n - k} X_t X_{t + k} \right)^2
$$

Expandiendo el cuadrado:

$$
\left( \sum_{t=1}^{n - k} X_t X_{t + k} \right)^2 = \sum_{t=1}^{n - k} \sum_{s=1}^{n - k} X_t X_{t + k} X_s X_{s + k}
$$

### Paso 4: Cálculo de \( E[r(k)^2] \)

Calculamos la esperanza:

$$
E[r(k)^2] = \frac{1}{S^2} \sum_{t=1}^{n - k} \sum_{s=1}^{n - k} E\left[ X_t X_{t + k} X_s X_{s + k} \right]
$$

Analizamos dos casos:

#### Caso 1: \( t = s \)

$$
E\left[ X_t X_{t + k} X_t X_{t + k} \right] = E\left[ X_t^2 X_{t + k}^2 \right]
$$

Dado que \( X_t \) y \( X_{t + k} \) son independientes para \( k > q \):

$$
E\left[ X_t^2 X_{t + k}^2 \right] = E\left[ X_t^2 \right] E\left[ X_{t + k}^2 \right] = \gamma_0^2
$$

#### Caso 2: \( t \neq s \)

Para \( t \neq s \) y \( k > q \), las variables son independientes, por lo que:

$$
E\left[ X_t X_{t + k} X_s X_{s + k} \right] = E[X_t] E[X_{t + k}] E[X_s] E[X_{s + k}] = 0
$$

Porque \( E[X_t] = 0 \).

### Paso 5: Simplificación de la Suma

Solo los términos donde \( t = s \) contribuyen:

$$
E[r(k)^2] = \frac{1}{S^2} \sum_{t=1}^{n - k} E\left[ X_t^2 X_{t + k}^2 \right] = \frac{n - k}{S^2} \gamma_0^2
$$

### Paso 6: Aproximación de \( S \)

El valor esperado de \( S \) es:

$$
E[S] = \sum_{t=1}^{n} E[X_t^2] = n \gamma_0
$$

Aproximamos \( S \approx n \gamma_0 \).

### Paso 7: Cálculo Final de la Varianza

Sustituyendo:

$$
E[r(k)^2] = \frac{(n - k) \gamma_0^2}{(n \gamma_0)^2} = \frac{n - k}{n^2}
$$

Para \( n \) grande y \( k \ll n \):

$$
E[r(k)^2] \approx \frac{n}{n^2} = \frac{1}{n}
$$

Entonces:

$$
\text{Var}[r(k)] = E[r(k)^2] \approx \frac{1}{n}
$$

### Paso 8: Error Estándar

El error estándar es:

$$
\text{SE}[r(k)] = \sqrt{\text{Var}[r(k)]} = \sqrt{\frac{1}{n}} = \frac{1}{\sqrt{n}}
$$

### Paso 9: Fórmula de Bartlett

Bartlett (1946) derivó una expresión más general para la varianza de \( r(k) \):

$$
\text{Var}[r(k)] \approx \frac{1}{n} \left(1 + 2 \sum_{j=1}^{k-1} \rho(j)^2 \right)
$$

Bajo el supuesto de que \( \rho(j) = 0 \) para \( j > q \) y que \( k > q \), la suma se reduce a:

$$
\sum_{j=1}^{k-1} \rho(j)^2 = \sum_{j=1}^{q} \rho(j)^2
$$

Esta suma es una constante para \( k > q \), denotemos:

$$
C = 1 + 2 \sum_{j=1}^{q} \rho(j)^2
$$

Entonces:

$$
\text{Var}[r(k)] \approx \frac{C}{n}
$$

Si las autocorrelaciones \( \rho(j) \) son pequeñas, \( C \approx 1 \), y recuperamos el resultado anterior.

## Conclusión

Hemos demostrado que, para rezagos grandes \( k > q \):

1. La varianza del coeficiente de autocorrelación muestral es aproximadamente:

   $$
   \text{Var}[r(k)] \approx \frac{1}{n}
   $$

2. El error estándar es:

   $$
   \text{SE}[r(k)] \approx \frac{1}{\sqrt{n}}
   $$

Este resultado es consistente con la **fórmula reducida de Bartlett** y muestra que, para rezagos grandes, el error estándar de \( r(k) \) depende únicamente del tamaño de la muestra \( n \).



## Referencia

- **Bartlett, M. S. (1946)**. *On the Theoretical Specification and Sampling Properties of Autocorrelated Time-Series*. **Journal of the Royal Statistical Society**, 8(1), 27-41.

---

# Fin de la Derivación

# Bonus 4: Significancia Estadística del Coeficiente de Correlación Muestral

## Derivación del Límite de Significancia Estadística

En el análisis de series temporales, es importante determinar si los coeficientes de autocorrelación muestral \( r(k) \) son significativamente diferentes de cero. Un criterio práctico es considerar que un coeficiente de autocorrelación muestral es estadísticamente significativo si su valor absoluto excede el límite aproximado de \( \pm \dfrac{2}{\sqrt{n}} \), donde \( n \) es el tamaño de la muestra.

### Objetivo

Derivar matemáticamente el límite de significancia estadística \( \pm \dfrac{2}{\sqrt{n}} \) para el coeficiente de autocorrelación muestral \( r(k) \).

### Supuestos

- **Serie Temporal**: \( \{X_t\} \) es una serie temporal estacionaria con media cero y varianza constante.
- **Observaciones Independientes**: Para rezagos grandes (\( k > q \)), las observaciones \( X_t \) y \( X_{t+k} \) son aproximadamente independientes.
- **Distribución Normal**: Los \( X_t \) se distribuyen aproximadamente de forma normal.

### Paso 1: Varianza de \( r(k) \) para Rezagos Grandes

Como se ha demostrado previamente, para \( k > q \):

$$
\text{Var}[r(k)] \approx \frac{1}{n}
$$

Esto implica que el error estándar es:

$$
\text{SE}[r(k)] = \sqrt{\text{Var}[r(k)]} \approx \frac{1}{\sqrt{n}}
$$

### Paso 2: Distribución de \( r(k) \) Bajo la Hipótesis Nula

Bajo la hipótesis nula de que no hay autocorrelación (\( \rho(k) = 0 \)), y dado que \( X_t \) es normal, el coeficiente \( r(k) \) para \( k > q \) sigue aproximadamente una distribución normal:

$$
r(k) \sim N\left( 0, \frac{1}{n} \right)
$$

### Paso 3: Determinación del Límite de Significancia Estadística

Para un nivel de confianza del 95%, utilizamos el valor crítico de la distribución normal estándar:

$$
z_{\alpha/2} = z_{0.025} \approx 1.96
$$

El intervalo de confianza al 95% es:

$$
\text{IC}_{95\%} = \left[ -z_{\alpha/2} \cdot \text{SE}[r(k)],\ z_{\alpha/2} \cdot \text{SE}[r(k)] \right]
$$

Sustituyendo \( \text{SE}[r(k)] \approx \dfrac{1}{\sqrt{n}} \):

$$
\text{IC}_{95\%} = \left[ -\dfrac{1.96}{\sqrt{n}},\ \dfrac{1.96}{\sqrt{n}} \right]
$$

Para simplificar, se aproxima \( 1.96 \) a \( 2 \), obteniendo:

$$
\text{IC}_{95\%} \approx \left[ -\dfrac{2}{\sqrt{n}},\ \dfrac{2}{\sqrt{n}} \right]
$$

### Conclusión

- **Significancia Estadística**: Si \( |r(k)| > \dfrac{2}{\sqrt{n}} \), entonces el coeficiente de autocorrelación muestral es estadísticamente significativo al nivel del 5%.
- **No Significativo**: Si \( |r(k)| \leq \dfrac{2}{\sqrt{n}} \), no podemos rechazar la hipótesis nula de que \( \rho(k) = 0 \).


