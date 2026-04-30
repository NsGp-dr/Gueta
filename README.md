```markdown
# ∑ GUETA · Observatorio Estocástico Geodésico

**Gueta** es una suite web de análisis y sonificación de sistemas estocásticos multivariados, que fusiona teoría de matrices aleatorias, cópulas, descomposición espectral, y geometría diferencial (atractor de Clifford, geodésicas del toro, curvas de Lissajous) para generar experiencias audiovisuales inmersivas. El proyecto consta de tres laboratorios interconectados:

- **GuetaRythm** – análisis multivariado interactivo (correlaciones, eigenvalores, riesgo, visualización geométrica).
- **Stochastic Lab** – laboratorio didáctico de majorización, cópulas, inferencia bayesiana y sonificación espectral.
- **Clifford Membrane** – exploración pura de variedades invariantes (Clifford, toro, agua, Chladni, Lissajous) moduladas en tiempo real.

---

## 🧠 Fundamentos Matemáticos

### 1. Descomposición Espectral y Criterio de Marchenko–Pastur
Para una matriz de datos `X` de dimensiones `p × n` (p variables, n observaciones), se construye la matriz de correlación muestral `R = (1/n) X Xᵀ`. Bajo la hipótesis nula de ruido blanco gaussiano, la distribución de los eigenvalores de `R` sigue la ley de Marchenko–Pastur con densidad:

\[
\rho(\lambda) = \frac{\sqrt{(\lambda_+ - \lambda)(\lambda - \lambda_-)}}{2\pi\sigma^2 \lambda}, \quad \lambda \in [\lambda_-, \lambda_+]
\]
donde \(\lambda_\pm = \sigma^2(1 \pm \sqrt{q})^2\), \(q = p/n\). Los eigenvalores observados que superan \(\lambda_+\) indican la presencia de **señal estructural** (correlaciones no espurias). En Gueta, este criterio se usa para estimar el riesgo y la entropía de la matriz.

### 2. Mayorización y Doble Estocasticidad (Sinkhorn)
La matriz de correlación absoluta `|R|` se normaliza mediante el algoritmo de Sinkhorn para obtener una matriz doblemente estocástica `DS`. Para cada fila `ds_i` de `DS`, se calcula su vector de mayorización `M(ds_i)`, que acumula los valores ordenados de forma descendente. La comparación de estas curvas de mayorización entre filas permite evaluar la dispersión de la correlación: una fila más uniforme (mayorización “menor”) indica que la variable correspondiente se correlaciona de manera homogénea con las demás.

### 3. Cópulas y Transformación Integral de Probabilidad (PIT)
Dada una serie `x_i`, se aplica la transformación a rangos uniformes \(u_i = \frac{\text{rango}(x_i)}{n+1}\). El par \((u_i, v_i)\) para dos variables define la cópula empírica, que captura la dependencia más allá de la correlación lineal. En Gueta se visualizan nubes de puntos de cópula y se calcula el coeficiente de correlación de Pearson en el espacio uniforme.

### 4. Geometría Invariante: Atractor de Clifford
El atractor de Clifford es un sistema dinámico discreto en \(\mathbb{R}^2\) definido por:

\[
\begin{cases}
x_{n+1} = \sin(a\, y_n) + c \cos(a\, x_n) \\
y_{n+1} = \sin(b\, x_n) + d \cos(b\, y_n)
\end{cases}
\]

Los parámetros \((a,b,c,d)\) se actualizan dinámicamente en función de los eigenvalores dominantes y la entropía del sistema:

\[
\begin{aligned}
a &= -1.5 - 0.6\,\lambda_1 - 0.2\,H, \\
b &= 1.5 + 0.6\,\lambda_2 + 0.3\,\text{flatness}, \\
c &= 0.7 + 0.8\,\lambda_3 + 0.4\,(1-\text{flatness}), \\
d &= -0.8 + 0.6\,\text{copula} - 0.3\,H,
\end{aligned}
\]

con límites ajustados para garantizar comportamiento caótico (no convergencia a punto fijo). La órbita generada se proyecta en el plano y se visualiza como una nube de puntos, cuya densidad refleja la frecuencia de visita de la trayectoria.

### 5. Geodésicas sobre el Toro
El toro paramétrico se define como:

\[
\mathbf{r}(\theta) = \big( (R + r \cos(q\theta)) \cos(p\theta),\; (R + r \cos(q\theta)) \sin(p\theta),\; r \sin(q\theta) \big)
\]

Los números enteros \(p,q\) se derivan de los eigenvalores: \(p = \lfloor 2 + 5\lambda_1\rfloor\), \(q = \lfloor 1 + 6\lambda_2\rfloor\). La curva traza una **geodésica** (no necesariamente cerrada) sobre la superficie del toro, y su torsión se modula por el riesgo estocástico, creando un patrón visual que revela la estructura de dependencia global de los datos.

### 6. Curvas de Lissajous y Relaciones Armónicas
Para frecuencias \(f_x = a \omega\), \(f_y = b \omega\), la curva de Lissajous viene dada por:

\[
x(t) = \sin(a \omega t + \phi), \quad y(t) = \sin(b \omega t)
\]

La relación \(a:b\) se calcula a partir de los eigenvalores y la entropía, simulando la interacción entre modos propios del sistema. La visualización de Lissajous en tiempo real refleja la consonancia armónica de la matriz de correlación.

---

## 🎛️ Síntesis de Audio: Osciladores Modulados Espectralmente

La sonificación en Gueta se basa en la **descomposición de Fourier** de la matriz de correlación a través de sus eigenvalores. El sintetizador implementa los siguientes componentes:

### Transformada de Fourier y Asignación de Frecuencias
Los eigenvalores normalizados \(\tilde{\lambda}_i = \lambda_i / \lambda_{\max}\) se mapean a frecuencias audibles mediante:

\[
f_i = f_{\text{base}} \cdot \frac{\lambda_i}{\lambda_{\max}} \cdot (i+1), \quad i=1,\dots,5
\]

donde \(f_{\text{base}}\) es ajustable por el usuario (típicamente 40–400 Hz). Este mapeo asegura que las componentes principales (mayor varianza explicada) se traduzcan en armónicos bajos y dominantes, mientras que los eigenvalores menores generan armónicos más agudos y de menor amplitud.

### Tipo de Onda y Mezcla
Cada canal armónico combina una onda sinusoidal pura con una onda diente de sierra mediante un parámetro de mezcla `wave ∈ [0,1]`:

\[
\text{señal}_i(t) = (1-\text{wave})\cdot \sin(2\pi f_i t) + \text{wave}\cdot \text{sawtooth}(2\pi f_i t)
\]

La onda diente de sierra aporta contenido armónico rico (múltiplos enteros de \(f_i\)), ideal para representar estructuras de alta entropía o riesgo.

### Envolvente y Modulación (LFO)
La ganancia de cada oscilador es modulada por un **LFO (oscilador de baja frecuencia)** cuya profundidad y velocidad dependen de la entropía espectral \(H\) y del score de Schur \(S\):

\[
g_i(t) = A_i \left(0.6 + 0.4 \sin(2\pi \nu t + \varphi_i)\right), \quad \nu = 0.03 + 0.08H
\]

donde \(A_i = \frac{0.6}{k} e^{-0.5 i S}\) es la amplitud base para el i-ésimo armónico. Esta modulación introduce **tremolo** y **vibrato** que varían con la complejidad del sistema: a mayor entropía, mayor fluctuación temporal.

### Reverberación Convolucional
Un impulso de ruido blanco decaído exponencialmente se utiliza como respuesta al impulso artificial para generar reverberación, simulando un espacio acústico. El nivel de reverb se controla mediante el parámetro `reverb ∈ [0,1]`.

### Efecto de “Snap” Armónico
El parámetro `snap ∈ [0,1]` fuerza a que las frecuencias generadas se alineen con una relación racional simple (por ejemplo, 2:1, 3:2, 4:3) respecto a la frecuencia base, induciendo **consonancia** perceptiva. Matemáticamente:

\[
f_i^{\text{snap}} = f_{\text{base}} \cdot \text{best\_ratio} \cdot \text{snap} + f_i \cdot (1-\text{snap})
\]

donde `best_ratio` es la relación armónica más cercana de la lista \([1, 2, 3/2, 4/3, 5/4, 5/3, 7/4, 2, 9/4, 3]\).

---

## 🖥️ Arquitectura Técnica

- **Canvas 2D y WebGL**: Visualización de trayectorias de Clifford, geodésicas del toro y curvas de Lissajous.
- **Web Audio API**: Síntesis de hasta 5 osciladores simultáneos, control de tipo de onda, LFO, reverb y envolvente.
- **Procesamiento de señales en tiempo real**: Detección de tono (ACF), centroide espectral, flujo espectral, flatness, entropía de Shannon.
- **Módulos interactivos**: Sliders para ventana temporal, parámetros bayesianos, knobs para sintetizador, pestañas de visualización.
- **Responsive design**: Grid CSS adaptable a escritorio y dispositivos móviles.

---

## 🧪 Experimentos y Casos de Uso

- **Análisis de series biológicas**: Carga de datos de diversidad, población o proxies climáticos; estudio de estacionariedad, estacionalidad y eventos leptocúrticos.
- **Exploración de la conjetura de Marchenko–Pastur**: Comparación de eigenvalores empíricos vs. teóricos, detección de desviaciones significativas.
- **Sonificación de matrices de correlación**: Cada celda de la matriz de correlación se convierte en un evento sonoro (tono y volumen según magnitud).
- **Estudio de la mayorización**: Visualización de curvas de Lorenz (mayorización) para filas de la matriz doblemente estocástica.

---

## 📦 Instalación y Ejecución

Clona el repositorio y abre `index.html` en un servidor local (por ejemplo, `npx http-server` o Live Server de VS Code).

```bash
git clone https://github.com/tuusuario/gueta-stochastic-lab.git
cd gueta-stochastic-lab
npx http-server -o
```

Asegúrate de permitir el acceso al micrófono si deseas usar la entrada de audio en vivo (Clifford Membrane).

---

## 🔮 Próximos Desarrollos

- Integración con API real de datos biológicos (GBIF, eBird, BioTIME).
- Despliegue de modelos de redes neuronales para predicción de regímenes.
- Exportación de sesiones en WebM con registro de métricas (CSV).
- Soporte para Midi output (control de sintetizador externo).

---

## 🤝 Contribuciones

Este proyecto es un laboratorio abierto a la comunidad de científicos de datos, músicos computacionales y entusiastas de los sistemas complejos. Las contribuciones en forma de nuevas visualizaciones, algoritmos de sonificación o datasets son bienvenidas.

---

## 📜 Licencia

MIT © 2026 — Observatorio Estocástico Geodésico.  
*“La geometría es la brújula del caos.”*
```
