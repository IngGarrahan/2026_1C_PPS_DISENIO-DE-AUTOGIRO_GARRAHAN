# DISEÑO DINÁMICO Y AERODINÁMICO DE UN ROTOR DE AUTOGIRO

### <p align="center"> Práctica Profesional Supervisada - Ingeniería Mecatrónica
### <p align="center"> Universidad Nacional de Lomas de Zamora

<p align="center"> <img width="814" height="225" alt="image" src="https://github.com/user-attachments/assets/1b20a310-95c3-4436-a2dc-a868014db164" />

---

## Índice
* [1. Introducción / Objetivo general](#introducción--objetivo-general)
* [2. Objetivos específicos](#objetivos-específicos)
* [3. Descripción técnica](#Descripción-técnica)
* [4. Arquitectura del sistema](#Arquitectura-del-sistema)
* [5. Instrucciones de uso](#Instrucciones-de-uso)
* [6. Estructura del repositorio](#estructura-del-repositorio)
* [Autor](#autor)

---

# Introducción / Objetivo general

Este repositorio documenta el desarrollo de una Práctica Profesional Supervisada (PPS), realizada sobre el diseño dinámico y aerodinámico de un rotor de autogiro.
Se busca desarrollar un modelo numérico para simular el comportamiento aerodinámico y dinámico de un rotor de autogiro mediante la Teoría de Elementos de Pala, obteniendo la distribución de fuerzas, momentos y parámetros aerodinámicos del sistema.

# Objetivos específicos

- Implementar un modelo basado en Teoría de Elemento de Pala.
- Calcular velocidades relativas, ángulos de ataque y coeficientes aerodinámicos.
- Obtener fuerzas de sustentación y resistencia sobre cada elemento de pala.
- Analizar el comportamiento durante descenso vertical y vuelo hacia adelante.
- Modelar el fenómeno dinámico de batimiento del rotor.

# Descripción técnica
El script modela el comportamiento dinámico traduciendo las leyes de la aerodinámica bidimensional al espacio discreto de la pala. En vuelo de avance, calcula la velocidad tangencial ($V_{Bl} = \Omega R \cdot r \pm V$) y la velocidad perpendicular ($w_{Bl}$) considerando el aporte de la velocidad inducida ($w_{Ri}$) y la tasa de cambio del batimiento ($\beta'$). 

El núcleo del dinamismo radica en la resolución de la ecuación diferencial ordinaria no lineal de segundo orden:
$$\beta'' + P(\psi)\beta' + Q(\psi)\beta = R(\psi)$$
Donde $P(\psi)$ representa el amortiguamiento aerodinámico, $Q(\psi)$ la rigidez dinámica modificada por la fuerza centrífuga, y $R(\psi)$ las excitaciones armónicas aerodinámicas introducidas por la velocidad de traslación de la aeronave. Debido al carácter rígidamente acoplado (stiff) del sistema bajo ciertas velocidades, se seleccionó el método numérico adaptativo **LSODA**.


# Arquitectura del sistema

### Entradas (parámetros / señales):
* Parámetros operativos: Velocidad de descenso ($V_{sink}$), velocidad de avance ($V$), velocidad de giro ($n_R$ en RPM).
* Geometría del rotor: Radio ($R$), cuerda ($c$), masa de pala ($m_P$), ángulo de paso ($\epsilon_{Bl}$)].
* Aerodinámica: Archivos de polares generados por XFoil para el perfil seleccionado.

### Procesamiento / Control:
* Algoritmo iterativo en Python que recorre matricialmente los elementos de pala y las posiciones angulares del disco del rotor ($\psi$).

### Salidas (señales / resultados):
* Vectores de sustentación ($A_{Bl}$), arrastre ($W_{Bl}$) y momentos elementales ($M$).
* Distribución temporal de la oscilación de batimiento $\beta(\psi)$.

---

# Instrucciones de uso

### Requisitos previos
* **Software:** Python 3.8 o superior.
* **Librerías:** `numpy`, `scipy`, `matplotlib`.
* **Herramientas externas:** XFoil (opcional, solo para regenerar polares personalizadas).

### Puesta en marcha

Obtención de parametros físicos:

  Ejecutar el archivo CALCULO DE SUSTENTACIÓN para obtener los datos de vuelo vertical y/o de avance.

Notas: Asegurarse de que las tablas de XFoil estén correctamente ubicadas dentro del directorio de ejecución para evitar fallas de interpolación fuera de los límites de Reynolds tabulados.

Obtención de beta:

  Ejecutar el archivo CALCULO DE BETA para obtener el comportamiento del ángulo de batimiento a lo largo de la revolución.

---

# Estructura del repositorio

```
├── codigo/
│  ├── coeficientes_aerodinámicos/
│  ├── calculo_beta
│  └── calculo_de_sustentación
│
├── INFORMES/
│  └── PPS_DISEÑO_DINÁMICO_Y_AERODINÁMICO_DE_UN_ROTOR_DE_AUTOGIRO.pdf
│
├── multimedia/
│  ├── resultados_del_analisis_en_descenso_vertical
│  ├── resultados_obtenidos_para_la_pala_que_avanza
│  ├── resultados_obtenidos_para_la_pala_que_retrocede
│  └── variación_del_angulo_de_batimiento_durante_el giro_del_rotor_(beta)
│
└── README.md
```

---

# Autor

## <p align="center"> Alan Garrahan
