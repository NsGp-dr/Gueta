# 🌌 ∑ GUETA · Observatorio Estocástico Geodésico

<p align="center">
  <img src="https://img.shields.io/badge/Status-Research_Phase-blueviolet?style=for-the-badge">
  <img src="https://img.shields.io/badge/Mathematics-TDA%20%7C%20Spectral-gold?style=for-the-badge">
  <img src="https://img.shields.io/badge/Sound-Synthesis_Vite-00e2ff?style=for-the-badge">
</p>

> *"𝙻𝚊 𝚐𝚎𝚘𝚖𝚎𝚝𝚛í𝚊 𝚎𝚜 𝚕𝚊 𝚋𝚛ú𝚓𝚞𝚕𝚊 𝚍𝚎𝚕 𝚌𝚊𝚘𝚜."*

**Gueta** es una plataforma de experimentación avanzada diseñada para transformar sistemas estocásticos multivariados en una experiencia sensorial tangible. Fusionamos la **Teoría de Matrices Aleatorias**, **Geometría Diferencial** y **Síntesis Espectral** para revelar *la naturaleza oculta de la coherencia*.

---

## 🧪 𝙻𝚊𝚋𝚘𝚛𝚊𝚝𝚘𝚛𝚒𝚘𝚜 𝚍𝚎 𝙸𝚗𝚖𝚎𝚛𝚜𝚒ó𝚗

| Módulo | Enfoque Conceptual | Dimensión Sensorial |
| :--- | :--- | :--- |
| **GuetaRythm** | Estabilidad espectral y correlaciones dinámicas. | Ritmo y Pulso de Datos |
| **Stochastic Lab** | Cópulas, Inferencia Bayesiana y Ley de Marchenko–Pastur. | Armonía Estocástica |
| **Clifford Membrane** | Atractores caóticos y geodésicas en variedades invariantes. | Geometría del Sonido |

---

## 🧠 𝙵𝚞𝚗𝚍𝚊𝚖𝚎𝚗𝚝𝚘𝚜 𝙼𝚊𝚝𝚎𝚖á𝚝𝚒𝚌𝚘𝚜

### 1. 𝙳𝚎𝚝𝚎𝚌𝚌𝚒ó𝚗 𝚍𝚎 𝚂𝚎ñ𝚊𝚕: 𝙼𝚊𝚛𝚌𝚑𝚎𝚗𝚔𝚘–𝙿𝚊𝚜𝚝𝚞𝚛
Para distinguir la estructura real del ruido blanco, analizamos la densidad de los eigenvalores $\lambda$ de la matriz de correlación $R$. Bajo la hipótesis nula, estos deben habitar en el soporte:
$$ \lambda_\pm = \sigma^2(1 \pm \sqrt{q})^2 $$
Cualquier autovalor fuera de este límite es tratado como **información estructural dominante**, dictando las frecuencias fundamentales de nuestro motor de síntesis.

### 2. 𝙼𝚊𝚢𝚘𝚛𝚒𝚣𝚊𝚌𝚒ó𝚗 𝚢 𝙴𝚗𝚝𝚛𝚘𝚙í𝚊 𝚍𝚎 𝚂𝚒𝚗𝚔𝚑𝚘𝚛𝚗
Utilizamos el algoritmo de Sinkhorn para normalizar la matriz de correlación en una matriz **doble mente estocástica**. Aplicamos el concepto de mayorización para evaluar la dispersión:
*   **Uniformidad:** Menor mayorización $\rightarrow$ Sonido etéreo.
*   **Concentración:** Mayor mayorización $\rightarrow$ Sonido punzante y definido.

### 3. 𝙶𝚎𝚘𝚖𝚎𝚝𝚛í𝚊 𝙸𝚗𝚟𝚊𝚛𝚒𝚊𝚗𝚝𝚎 (𝙰𝚝𝚛𝚊𝚌𝚝𝚘𝚛 𝚍𝚎 𝙲𝚕𝚒𝚏𝚏𝚘𝚛𝚍)
La visualización dinámica se rige por:
$$ x_{n+1} = \sin(a y_n) + c \cos(a x_n) $$
$$ y_{n+1} = \sin(b x_n) + d \cos(b y_n) $$
Donde los coeficientes $(a, b, c, d)$ son **funciones de estado** derivadas directamente de los eigenvalores dominantes y la entropía de Shannon del sistema.

---

## 🎛️ 𝙰𝚛𝚚𝚞𝚒𝚝𝚎𝚌𝚝𝚞𝚛𝚊 𝚍𝚎 𝚂í𝚗𝚝𝚎𝚜𝚒𝚜 𝚍𝚎 𝙰𝚞𝚍𝚒𝚘

El sintetizador de Gueta opera como un **observatorio auditivo**:

*   **Mapeo Espectral:** Los autovalores $\lambda_i$ se mapean a la serie armónica $f_i = f_{base} \cdot (\lambda_i / \lambda_{max})$.
*   **LFO Entrópico:** La inestabilidad del sistema modula la fase y el tremolo, permitiendo "escuchar" el riesgo.
*   **Snap Armónico:** Una función de cuantización que atrae las frecuencias hacia ratios racionales, transformando datos en consonancia musical.

---

## 🛠️ 𝚂𝚝𝚊𝚌𝚔 𝚃é𝚌𝚗𝚒𝚌𝚘

*   **Core:** JavaScript (ES6+) / Vite.
*   **Graphics:** Canvas 2D & WebGL para renderizado de alta densidad de partículas.
*   **Audio:** Web Audio API con osciladores polifónicos y filtros biquad.
*   **Formalismo:** Documentación técnica en **LaTeX** para la preservación del rigor científico.

---

## 🚀 𝙸𝚗𝚜𝚝𝚊𝚕𝚊𝚌𝚒ó𝚗
```bash
# Clonar el observatorio
git clone [https://github.com/NsGp-dr/zzsynth.git](https://github.com/NsGp-dr/zzsynth.git)

# Acceder al directorio
cd zzsynth

# Lanzar el servidor local
npx http-server .
