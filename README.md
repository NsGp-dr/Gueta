∑ GUETA · Observatorio Estocástico Geodésico

Gueta es una plataforma de experimentación avanzada que trasciende la visualización de datos convencional para convertirse en un órgano de percepción sensorial. Fusiona la teoría de matrices aleatorias, geometría diferencial y síntesis espectral para transformar sistemas estocásticos multivariados en variedades visuales y estructuras armónicas.

Basado en la premisa de que "la cognición es una experiencia intuitiva", Gueta permite escuchar la señal estructural y observar la topología del riesgo a través de tres laboratorios de inmersión:

    GuetaRythm: Análisis de estabilidad espectral y correlaciones dinámicas.

    Stochastic Lab: Inferencia bayesiana, cópulas y el límite de Marchenko–Pastur.

    Clifford Membrane: Exploración de atractores caóticos y geodésicas sobre toros, modulados por la entropía del sistema.

🧠 Marco Teórico y Rigor Matemático
1. El Límite de la Señal: Marchenko–Pastur

En el análisis de grandes matrices de datos X∈Rp×n, la distinción entre ruido y estructura es fundamental. Gueta evalúa la matriz de correlación R=n1​XXT. Bajo la hipótesis nula, la densidad de los eigenvalores sigue la ley de Marchenko–Pastur:
ρ(λ)=2πσ2λq(λ+​−λ)(λ−λ−​)​​,λ∈[λ−​,λ+​]

Donde q=p/n. Los eigenvalores que escapan de este soporte (λ>λ+​) son tratados como los modos propios de la señal, los cuales dictan la frecuencia fundamental de la sonificación y los parámetros del atractor.
2. Mayorización y Doble Estocasticidad

Implementamos el Algoritmo de Sinkhorn para transformar la matriz de correlación en una matriz doblemente estocástica DS. A través de la Mayorización, comparamos la dispersión de información entre variables:

    Si una variable dsi​ mayoriza a dsj​, su "huella" de correlación es más concentrada y menos entrópica.

    Este ordenamiento parcial se traduce en la envolvente de amplitud de los osciladores.

3. Dinámica del Caos: Atractor de Clifford

La "Membrana" utiliza un sistema dinámico discreto cuyas órbitas están gobernadas por:
xn+1​=sin(ayn​)+ccos(axn​)
yn+1​=sin(bxn​)+dcos(byn​)

En Gueta, los coeficientes (a,b,c,d) no son estáticos; son funciones de estado de la matriz de datos:

    a,b dependen de los eigenvalores dominantes (estructura).

    c,d dependen de la entropía de Shannon y la correlación de cópulas (complejidad).

4. Topología del Sonido: Geodésicas sobre Toros

Visualizamos la coherencia mediante curvas geodésicas en un toro paramétrico. La relación de enrollamiento (p,q) es una proyección directa de la relación entre los dos componentes principales del sistema, permitiendo identificar visualmente estados de resonancia o disonancia estocástica.
🎛️ Arquitectura de Sonidificación Espectral

El motor de audio de Gueta no es decorativo; es un procedimiento analítico.

    Mapeo de Eigenvalores: Los autovalores λi​ se normalizan y escalan a la serie armónica fi​=fbase​⋅(λi​/λmax​).

    Modulación por Entropía: La entropía espectral H controla un LFO que afecta la fase de los osciladores, creando texturas de "vibrato" en sistemas de alta incertidumbre.

    Snap Armónico: Para facilitar la interpretación intuitiva, el sistema permite forzar las frecuencias hacia ratios racionales (3:2, 4:3, etc.), transformando la correlación estadística en consonancia musical.

🛠️ Tecnologías y Stack

    Engine: JavaScript (ES6+) con procesamiento de señales en tiempo real.

    Visuals: Canvas 2D / WebGL para la renderización de nubes de puntos de alta densidad.

    Audio: Web Audio API (Osciladores polifónicos, filtros biquad, reverb convolucional).

    Matemáticas: Implementaciones nativas de descomposición espectral, algoritmos de Sinkhorn y transformadas de probabilidad integral (PIT).

🚀 Instalación y Despliegue

Este proyecto está optimizado para ejecutarse en entornos modernos de navegador.
Bash

# Clonar el observatorio
git clone https://github.com/NsGp-dr/gueta.git

# Entrar al directorio
cd gueta

# Ejecutar con cualquier servidor local (ej. Live Server o http-server)
npx http-server .

🔮 Visión: "La Naturaleza Oculta de la Coherencia"

Gueta se concibe como una herramienta de docencia e investigación. Buscamos que el estudiante de posgrado o el investigador pueda:

    Sentir la transición de fase entre ruido y señal.

    Explorar la geometría de las variedades invariantes sin la barrera de la abstracción pura.

    Validar visualmente la independencia de variables mediante el análisis de cópulas.

🤝 Contribuciones y Desarrollo

Desarrollado por NsGp-dr. Como proyecto nacido en un semillero de investigación matemática, las contribuciones enfocadas en topología, teoría de números aplicada a la música y análisis multivariado son más que bienvenidas.

Licencia: MIT

"Hacia una cognición de los datos a través de la armonía de las formas."
