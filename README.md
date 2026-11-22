<div align="center">

# 🧠 Perceptron Learning Visualization

### Implementación desde cero de un perceptrón para clasificación binaria

*Sin librerías de machine learning: solo Python, lógica y matemáticas.*

<br>

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/JosueVele77/perceptron-learning-visualization/blob/main/Practica_03_Perceptron.ipynb)

![Python](https://img.shields.io/badge/Python-3.x-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=for-the-badge&logo=jupyter&logoColor=white)
![Google Colab](https://img.shields.io/badge/Google-Colab-F9AB00?style=for-the-badge&logo=googlecolab&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualización-11557C?style=for-the-badge)

</div>

---

## 📌 Descripción

Este proyecto implementa **manualmente** el perceptrón de Rosenblatt, el modelo más básico de neurona artificial, para separar dos clases de puntos en un plano bidimensional (`-1` y `+1`).

Además de entrenar el modelo, el proyecto **visualiza cómo aprende**: muestra cómo se mueve la frontera de decisión época tras época, cómo evoluciona el error y cómo influye la tasa de aprendizaje en la convergencia.

> 🎓 Desarrollado como práctica de la asignatura **Inteligencia Artificial** — Carrera de Computación.

---

## 🛠️ Herramientas utilizadas

<div align="center">

| Herramienta | Uso en el proyecto |
|:---:|:---|
| <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/python/python-original.svg" width="40"/><br>**Python** | Lenguaje principal. Toda la lógica del perceptrón está escrita a mano con listas, ciclos y funciones. |
| <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/jupyter/jupyter-original.svg" width="40"/><br>**Jupyter Notebook** | Formato del proyecto: combina código, gráficas y explicaciones en un solo documento. |
| <img src="https://www.vectorlogo.zone/logos/google_colab/google_colab-icon.svg" width="40"/><br>**Google Colab** | Entorno de ejecución en la nube, sin necesidad de instalar nada. |
| <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/matplotlib/matplotlib-original.svg" width="40"/><br>**Matplotlib** | Gráficas del dataset, fronteras de decisión y curvas de error. |
| 🎲<br>**random** | Módulo estándar de Python para inicializar los pesos aleatorios. |

</div>

> ⚠️ **No se usan** NumPy, scikit-learn, TensorFlow ni PyTorch. El objetivo es entender el algoritmo desde su base.

---

## ⚙️ ¿Cómo funciona?

El perceptrón calcula una suma ponderada de las entradas y aplica una función escalón:

```
z = w0 + w1·x1 + w2·x2

ŷ =  1   si z ≥ 0
    -1   si z < 0
```

Cuando se equivoca, corrige sus pesos con la regla de aprendizaje:

```
wi ← wi + η · (y − ŷ) · xi
w0 ← w0 + η · (y − ŷ)
```

La **frontera de decisión** es la recta donde `z = 0`:

```
x2 = −(w1 / w2) · x1 − (w0 / w2)
```

---

## 🚀 Funcionalidades

- ✅ **Exploración del dataset** — conteo de instancias y clases con ciclos y contadores.
- ✅ **Funciones propias** — `initialize_weights()`, `activation()`, `perceptron_compute()`.
- ✅ **Entrenamiento** — `perceptron_learning()` con registro de pesos y error por época.
- ✅ **Visualización de la frontera** — incluye el caso especial `w2 = 0` (recta vertical).
- ✅ **Evolución del aprendizaje** — seis estados de la frontera (0%, 20%, 40%, 60%, 80% y 100%).
- ✅ **Curva de error** — tasa de error por época.
- ✅ **Predicción** — clasificación de nuevas instancias no vistas en el entrenamiento.
- ✅ **Comparación de tasas de aprendizaje** — `η = 0.3`, `0.5` y `0.8` con los mismos pesos iniciales.

---

## 📊 Resultados

Resultados con semilla fija (`SEED = 42`) para que sean reproducibles:

<div align="center">

| Tasa de aprendizaje | Épocas | Actualizaciones | Error final |
|:---:|:---:|:---:|:---:|
| `0.3` | 271 | 949 | **0.0** ✅ |
| `0.5` | 115 | 427 | **0.0** ✅ |
| `0.8` | 241 | 827 | **0.0** ✅ |

</div>

**Predicción de nuevas instancias:**

<div align="center">

| Instancia | Clase predicha |
|:---:|:---:|
| `[5, 5]` | 🔵 `-1` |
| `[10, 6]` | 🔴 `+1` |
| `[6, 10]` | 🔴 `+1` |

</div>

---

## 💡 Conclusiones principales

- 🔹 El perceptrón **converge** porque el dataset es linealmente separable.
- 🔹 El error **no disminuye de forma continua**: oscila antes de llegar a cero.
- 🔹 Una mayor tasa de aprendizaje **no siempre** implica una convergencia más rápida.
- 🔹 Pesos finales distintos pueden generar **rectas casi idénticas**: lo que importa es la proporción entre ellos.
- 🔹 Error cero en entrenamiento **no garantiza** un modelo perfecto para datos nuevos.

---

## ▶️ Cómo ejecutarlo

**Opción 1 — Google Colab (recomendado)**

Haz clic en el botón **Open in Colab** al inicio de este README y luego en `Entorno de ejecución → Ejecutar todas`.

**Opción 2 — Local**

```bash
git clone https://github.com/JosueVele77/perceptron-learning-visualization.git
cd perceptron-learning-visualization
pip install matplotlib notebook
jupyter notebook Practica_03_Perceptron.ipynb
```

---

## 📁 Estructura del proyecto

```
perceptron-learning-visualization/
├── Practica_03_Perceptron.ipynb   # Notebook con código, gráficas y análisis
└── README.md                      # Documentación del proyecto
```

---

## 📚 Referencias

1. F. Rosenblatt, *"The Perceptron: A Probabilistic Model for Information Storage and Organization in the Brain"*, Psychological Review, 1958.
2. W. S. McCulloch y W. Pitts, *"A Logical Calculus of the Ideas Immanent in Nervous Activity"*, Bulletin of Mathematical Biophysics, 1943.

---

<div align="center">

### 👨‍💻 Autor

**Josué** — [@JosueVele77](https://github.com/JosueVele77)

⭐ Si este proyecto te fue útil, ¡dale una estrella!

</div>
