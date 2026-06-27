# Diseño Dinámico y Aerodinámico de un Rotor de Autogiro

## Practica Profesional Supervisada (PPS)

Repositorio correspondiente al desarrollo de una herramienta numérica para el **análisis y diseño aerodinámico y dinámico de un rotor de autogiro**, capaz de predecir el comportamiento del rotor bajo condiciones de **autorrotación en descenso vertical y vuelo hacia adelante**.

El proyecto implementa un modelo basado en la **teoría de elementos de pala**, resolviendo las fuerzas aerodinámicas y la dinámica del rotor mediante un proceso iterativo.

---

# Objetivo del proyecto

El objetivo principal es desarrollar una herramienta computacional que permita:

* Analizar la generación de sustentación en un rotor de autogiro.
* Evaluar el comportamiento aerodinámico de cada segmento de pala.
* Calcular fuerzas, momentos y parámetros dinámicos del rotor.
* Determinar condiciones de autorrotación para diferentes condiciones de vuelo.

---

# Descripción general

El rotor se modela mediante una discretización de la pala en múltiples elementos. Para cada sección se calculan:

* Velocidad relativa del flujo.
* Ángulo de ataque.
* Número de Reynolds.
* Coeficientes aerodinámicos.
* Fuerzas de sustentación y resistencia.
* Momentos aerodinámicos.

Los coeficientes aerodinámicos se obtienen a partir del análisis del perfil seleccionado utilizando datos generados mediante herramientas como **XFoil**.

---

# Metodología

## Teoría de elementos de pala

Cada pala se divide en segmentos donde se evalúan las condiciones locales del flujo.

A partir de la velocidad relativa y los coeficientes aerodinámicos se calculan:

* Sustentación.
* Arrastre.
* Fuerzas tangenciales y normales.
* Momento generado sobre el rotor.

---

## Descenso vertical

Para esta condición se analiza el flujo perpendicular al rotor considerando:

* Velocidad de descenso.
* Velocidad inducida.
* Ángulo de flujo.
* Ángulo de ataque de pala.

El modelo permite obtener la distribución de fuerzas a lo largo del radio del rotor.

---

## Vuelo hacia adelante

En avance aparece una condición asimétrica entre ambas palas:

* Pala que avanza.
* Pala que retrocede.

Por esta razón se analiza el rotor durante un giro completo, considerando las diferencias de velocidad producidas por el viento relativo.

Además, se incorpora el fenómeno de **batimiento**, permitiendo modelar el movimiento de aleteo de las palas para compensar las diferencias aerodinámicas.

---

# Modelo dinámico

La dinámica del rotor se representa mediante una ecuación diferencial no lineal de segundo orden asociada al batimiento de pala.

La ecuación se resuelve utilizando herramientas numéricas de Python mediante integradores de ecuaciones diferenciales.

---

# Tecnologías utilizadas

* Python
* NumPy
* SciPy
* Matplotlib
* XFoil (obtención de coeficientes aerodinámicos)

---

# Estructura del repositorio

```
.
├── datos/
│   └── coeficientes_aerodinamicos/
│
├── docs/
│   └── PPS_DISEÑO_DINÁMICO_Y_AERODINÁMICO_DE_UN_ROTOR_DE_AUTOGIRO.pdf
│
├── resultados/
│   ├── graficos/
│   └── tablas/
│
├── software/
│   ├── calculo_beta.ipynb
│   ├── calculo_de_sustentación.ipynb
│
└── README.md
```


---

# Resultados obtenidos

El modelo permite observar:

* Variación de sustentación con la velocidad.
* Distribución de fuerzas sobre la pala.
* Diferencias entre pala de avance y retroceso.
* Evolución del ángulo de batimiento.

Los resultados muestran que el aumento de velocidad incrementa la sustentación debido a su dependencia cuadrática con la velocidad relativa del flujo.

---

# Conclusiones

Se logró desarrollar un modelo capaz de representar el comportamiento aerodinámico y dinámico de un rotor de autogiro mediante la teoría de elementos de pala.

La herramienta permite analizar la influencia de:

* Geometría del rotor.
* Condiciones de vuelo.
* Perfil aerodinámico.
* Número de Reynolds.
* Fenómeno de batimiento.

Este desarrollo permite continuar con futuras mejoras incorporando nuevos perfiles, materiales y configuraciones de rotor.

---

# Autor

<div align="center"> <h1> Alan Garrahan </h1> </div>
<div align="center"> <img width="562" height="183" alt="image" src="https://github.com/user-attachments/assets/183ca983-fc6c-4694-9581-a1344d4de029" /> </div>
