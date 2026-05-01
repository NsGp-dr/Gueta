# 🌌 ∑ GUETA · Observatorio Estocástico Geodésico

> *“¿Qué tan curiosa puede ser una pregunta?”*

¿Es la atención inducida por la coherencia? ¿Es la coherencia inducida por el ritmo? y así, ¿Es el estrés inducido por la atención? La motivación de este proyecto es la fascinación que encuentro en la capacidad humana de crear preguntas, de crear caminos, imágenes sobre una belleza que parece arbitraria. ¿Tendrá esta belleza la probabilidad de ser coherente?

---

**Gueta** es una plataforma de experimentación avanzada diseñada para transformar sistemas estocásticos multivariados en una experiencia sensorial tangible. Fusionamos la **Teoría de Matrices Aleatorias**, **Geometría Diferencial** y **Síntesis Espectral** para revelar *la naturaleza oculta de la coherencia*.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

---

## 🧪 Laboratorios de Inmersión

| Módulo | Enfoque Conceptual | Dimensión Sensorial |
|--------|--------------------|----------------------|
| **GuetaRythm** | Estabilidad espectral y correlaciones dinámicas | Ritmo y pulso de datos |
| **Stochastic Lab** | Cópulas, Inferencia Bayesiana y Ley de Marchenko–Pastur | Armonía Estocástica |
| **Clifford Membrane** | Atractores caóticos y geodésicas en variedades invariantes | Geometría del sonido |

---

## 🧠 Fundamentos Matemáticos

### 1. Detección de Señal: Marchenko–Pastur

Para una matriz de datos $X$ de dimensiones $p \times n$ ($p$ variables, $n$ observaciones), la matriz de correlación muestral es $R = \frac{1}{n} X X^{\mathsf{T}}$. Bajo la hipótesis nula de ruido blanco gaussiano, la distribución de los eigenvalores de $R$ sigue la ley de Marchenko–Pastur:

$$
\rho(\lambda)=\frac{\sqrt{(\lambda_+ - \lambda)(\lambda - \lambda_-)}}{2\pi\sigma^2\lambda}, \qquad \lambda \in [\lambda_-, \lambda_+]
$$

con límites:

$$
\lambda_\pm = \sigma^2(1 \pm \sqrt{q})^2, \qquad q = \frac{p}{n}.
$$

**Criterio de señal:** Todo eigenvalor observado que supere $\lambda_+$ corresponde a estructura real (correlación no espuria). Estos eigenvalores dominantes determinan las frecuencias fundamentales del sintetizador y la topología del atractor de Clifford.

---

### 2. Mayorización y Doble Estocasticidad (Sinkhorn)

A partir de la matriz de correlación absoluta $|R|$, aplicamos el algoritmo de **Sinkhorn** para obtener una matriz **doblemente estocástica** $DS$ (sumas fila y columna iguales a 1). Para cada fila $ds_i$ de $DS$, se calcula su vector de **mayorización**:

$$
M(ds_i) = \left( \sum_{j=1}^{k} ds_{i(j)}^{\downarrow} \right)_{k=1}^{p}
$$

donde $ds_{i(j)}^{\downarrow}$ es la fila ordenada de forma descendente. La comparación de las curvas de mayorización entre variables evalúa la dispersión de la correlación:

- **Uniformidad** → menor mayorización → sonido etéreo, difuso.
- **Concentración** → mayor mayorización → sonido punzante, definido.

---

### 3. Schur‑Convexidad y Riesgo

Una función $\Phi$ es **Schur‑convexa** si $x \succ y$ ($x$ mayoriza a $y$) implica $\Phi(x) \ge \Phi(y)$. En Gueta, el score de Schur se define como:

$$
S = \frac{\max(\lambda_i)}{\frac{1}{p}\sum \lambda_i}
$$

Este índice mide la concentración de la varianza: $S = 1$ indica uniformidad, $S = p$ indica dominancia completa. El riesgo estocástico se calcula como:

$$
\text{riesgo} = \frac{\#\{\lambda_i > \lambda_+\}}{p} + 0.3 \cdot \frac{\lambda_1}{3\lambda_+}
$$

y se utiliza para modular la amplitud del LFO y la deformación de las geodésicas del toro.

---

### 4. Geometría Invariante: Atractor de Clifford

El sistema dinámico discreto en $\mathbb{R}^2$:

$$
\begin{cases}
x_{n+1} = \sin(a\, y_n) + c \cos(a\, x_n) \\[4pt]
y_{n+1} = \sin(b\, x_n) + d \cos(b\, y_n)
\end{cases}
$$

Los parámetros $(a,b,c,d)$ se actualizan en tiempo real a partir de los eigenvalores $\lambda_1, \lambda_2, \lambda_3$, la entropía de Shannon $H$ y la planoitud espectral $F$:

$$
\begin{aligned}
a &= -1.5 - 0.6\lambda_1 - 0.2H \\
b &= 1.5 + 0.6\lambda_2 + 0.3F \\
c &= 0.7 + 0.8\lambda_3 + 0.4(1-F) \\
d &= -0.8 + 0.6\,\text{copula} - 0.3H
\end{aligned}
$$

con límites que garantizan comportamiento caótico (sin colapso a punto fijo). La órbita se visualiza como una nube de puntos cuya densidad refleja la frecuencia de visita de la trayectoria.

---

### 5. Geodésicas sobre el Toro

Un toro paramétrico se define como:

$$
\mathbf{r}(\theta) = \big( (R + r \cos(q\theta)) \cos(p\theta),\; (R + r \cos(q\theta)) \sin(p\theta),\; r \sin(q\theta) \big)
$$

Los enteros $p, q$ se derivan de los eigenvalores:  
$p = \lfloor 2 + 5\lambda_1\rfloor$, $q = \lfloor 1 + 6\lambda_2\rfloor$.

La curva traza una **geodésica** (no necesariamente cerrada) sobre la superficie del toro. Su torsión es modulada por el riesgo estocástico, generando patrones visuales que revelan la estructura de dependencia global.

---

### 6. Curvas de Lissajous y Relaciones Armónicas

Para frecuencias $f_x = a\omega$, $f_y = b\omega$, la curva de Lissajous responde a:

$$
x(t) = \sin(a\omega t + \phi), \quad y(t) = \sin(b\omega t)
$$

La relación $a:b$ se extrae directamente de los eigenvalores y de la entropía, simulando la interacción entre modos propios del sistema. La animación en tiempo real refleja la **consonancia armónica** de la matriz de correlación.

---

## 🎛️ Arquitectura de Síntesis de Audio

El sintetizador de Gueta funciona como un **observatorio auditivo**. Cada componente del sistema estocástico se traduce en un parámetro sonoro.

### Mapeo Espectral

Los eigenvalores normalizados $\tilde{\lambda}_i = \lambda_i / \lambda_{\max}$ se convierten en frecuencias audibles:

$$
f_i = f_{\text{base}} \cdot \frac{\lambda_i}{\lambda_{\max}} \cdot (i+1), \qquad i = 1,\dots,5
$$

donde $f_{\text{base}}$ (ajustable por el usuario, típicamente 40–400 Hz) establece la tónica. Las componentes principales generan armónicos bajos y dominantes; los eigenvalores menores producen armónicos agudos de menor amplitud.

---

### Tipo de Onda y Mezcla

Cada canal combina una onda sinusoidal pura con una onda diente de sierra mediante el parámetro $\text{wave} \in [0,1]$:

$$
\text{señal}_i(t) = (1-\text{wave})\sin(2\pi f_i t) + \text{wave}\cdot\text{sawtooth}(2\pi f_i t)
$$

La diente de sierra aporta contenido armónico rico (múltiplos enteros de $f_i$), ideal para representar estructuras de alta entropía o riesgo.

---

### Envolvente y LFO Entrópico

La ganancia de cada oscilador se modula por un **LFO** cuya profundidad y velocidad dependen de la entropía espectral $H$ y del score de Schur $S$:

$$
g_i(t) = A_i \left(0.6 + 0.4 \sin(2\pi \nu t + \varphi_i)\right), \quad \nu = 0.03 + 0.08H
$$

con amplitud base:

$$
A_i = \frac{0.6}{k} e^{-0.5 i S}
$$

Este *tremolo* varía con la complejidad del sistema: a mayor entropía, mayor fluctuación temporal.

---

### Snap Armónico

El parámetro $\text{snap} \in [0,1]$ fuerza a que las frecuencias generadas se alineen con una relación racional simple respecto a la frecuencia base (2:1, 3:2, 4:3, etc.), induciendo **consonancia** perceptiva:

$$
f_i^{\text{snap}} = f_{\text{base}} \cdot \text{best\_ratio} \cdot \text{snap} + f_i (1 - \text{snap})
$$

donde `best_ratio` es la relación armónica más cercana de la lista:

$$
[1,\; 2,\; 3/2,\; 4/3,\; 5/4,\; 5/3,\; 7/4,\; 2,\; 9/4,\; 3]
$$

---

### Reverberación Convolucional

Una respuesta al impulso artificial (ruido blanco decaído exponencialmente) se utiliza para generar reverberación, simulando un espacio acústico. El nivel de reverb se controla mediante un parámetro $\text{reverb} \in [0,1]$.

---

## 🛠️ Stack Técnico

- **Core**: JavaScript (ES6+) / Vite  
- **Graphics**: Canvas 2D & WebGL (renderizado de alta densidad de partículas)  
- **Audio**: Web Audio API (osciladores polifónicos, filtros biquad, convolución)  
- **Formalismo matemático**: LaTeX en documentación y comentarios  
- **Responsive**: Grid CSS adaptable a escritorio y móviles  

---
