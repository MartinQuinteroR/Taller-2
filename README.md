# ⚡ Dashboard de Pronóstico de Demanda Energética — Austria

Dashboard interactivo para visualizar y pronosticar la demanda energética total en Austria, construido con **Plotly Dash**.

---

## 📋 Descripción

Esta herramienta visualiza la demanda energética total en Austria (en MW) hora a hora, según los datos publicados en el **ENTSO-E Data Portal**. Además, permite realizar **pronósticos de hasta 5 días (120 horas)** en el futuro con intervalos de confianza.

### Funcionalidades principales

- 📅 **Selector de fecha y hora inicial** — filtra el rango de visualización.
- 🎚️ **Slider de proyección** — ajusta cuántas horas hacia adelante se proyecta la demanda (0–119 horas).
- 📈 **Gráfica interactiva** — muestra la demanda real, la proyección y los límites superior e inferior del intervalo de confianza.

---

## 🗂️ Estructura del proyecto

```
Taller-2/
│
├── app.py                      # Aplicación principal Dash
├── datos_energia.csv           # Dataset de demanda energética (ENTSO-E)
├── assets/
│   ├── base.css                # Estilos base del dashboard
│   └── clinical-analytics.css # Estilos del panel de control
└── README.md
```

---

## 🚀 Instalación y ejecución

### Requisitos previos

- Python 3.8+
- pip

### 1. Crear y activar un entorno virtual (recomendado)

```bash
python -m venv venv
# Windows
venv\Scripts\activate
# macOS / Linux
source venv/bin/activate
```

### 2. Instalar dependencias

```bash
pip install dash plotly pandas numpy
```

### 3. Ejecutar la aplicación

```bash
python app.py
```

La aplicación estará disponible en `http://127.0.0.1:8050/` en tu navegador.

---

## 📊 Datos

| Campo | Descripción |
|---|---|
| `time` | Marca de tiempo horaria (índice) |
| `AT_load_actual_entsoe_transparency` | Demanda real en MW (Austria) |
| `forecast` | Valor proyectado por el modelo |
| `Upper bound` | Límite superior del intervalo de confianza |
| `Lower bound` | Límite inferior del intervalo de confianza |

**Fuente:** [ENTSO-E Transparency Platform](https://transparency.entsoe.eu/)

---

## 🛠️ Stack tecnológico

| Tecnología | Uso |
|---|---|
| [Plotly Dash](https://dash.plotly.com/) | Framework del dashboard web |
| [Plotly](https://plotly.com/python/) | Gráficas interactivas |
| [Pandas](https://pandas.pydata.org/) | Manipulación de datos |
| [NumPy](https://numpy.org/) | Operaciones numéricas |

---

## 📁 Descripción de `app.py`

| Función | Descripción |
|---|---|
| `load_data()` | Carga y pre-procesa el CSV; convierte `time` a índice datetime |
| `plot_series(data, initial_date, proy)` | Genera la figura Plotly con demanda real, proyección e intervalos |
| `description_card()` | Componente HTML con el título y descripción del dashboard |
| `generate_control_card()` | Panel de controles: DatePicker, Dropdown de hora y Slider |
| `update_output_div(date, hour, proy)` | Callback Dash que actualiza la gráfica al cambiar los controles |

---

## 📸 Interfaz

El dashboard está dividido en dos columnas:

- **Columna izquierda (4/12):** Descripción del proyecto y controles interactivos.
- **Columna derecha (8/12):** Gráfica de la serie de tiempo con demanda real y proyección.

---

## 👤 Autor

Proyecto desarrollado para el curso **202621** — Universidad de los Andes.

---

> **Nota:** Los datos de demanda provienen del portal de transparencia de ENTSO-E y corresponden al mercado eléctrico de Austria.
