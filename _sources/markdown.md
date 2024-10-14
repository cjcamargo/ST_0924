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

