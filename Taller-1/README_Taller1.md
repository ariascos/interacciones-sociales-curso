# Taller 1 — Fundamentos de Python y primeros pasos en redes

**ECON 64597 · Modelos de Interacciones Sociales · 2026-2**
Semana de entrega: **33** · Peso: **10%** de la nota final · Grupos de **2 a 3** personas

---

## 1. Qué se entrega

Un único archivo `Taller1_ApellidoA_ApellidoB_ApellidoC.zip` que contenga:

| Archivo | Descripción |
|---|---|
| `Taller1_ESTUDIANTES.ipynb` | El cuaderno completo, **ya ejecutado** (con outputs visibles) |
| `requirements.txt` | Paquetes y versiones exactas con las que corre su cuaderno |
| `red_aristas.csv`, `red_nodos.csv` | Los datos generados por el cuaderno |
| `figuras/` *(opcional)* | Gráficas exportadas, si las guardan aparte |

Para generar el archivo de dependencias desde su entorno:

```bash
pip freeze > requirements.txt
```

**Criterio de reproducibilidad:** el monitor debe poder descomprimir el `.zip`, instalar
`requirements.txt` y correr *Kernel > Restart & Run All* sin errores y **sin conexión a
internet**. Un cuaderno que no corre completo pierde automáticamente el 20% de la nota del
taller.

---

## 2. Protocolo de evaluación (sección 5b del programa)

1. **Entrega:** el `.zip` autocontenido descrito arriba.
2. **Auditoría automática:** el monitor pasa el código por un *AI code reviewer workflow* que
   critica el código y genera preguntas de comprensión específicas sobre lo que ustedes
   entregaron.
3. **Microreunión:** cada grupo es citado a una reunión corta (~15 min) para defender, explicar y modificar en vivo su trabajo. Se pregunta a integrantes al azar.

> Todos los integrantes deben poder explicar **cualquier** celda.

---

## 3. Uso de IA

Permitido en todo el taller. Dos condiciones:

- **Divulgación:** diligenciar la *Declaración de Uso de IA* al inicio del cuaderno
  (herramientas que uso, en qué puntos, qué verificaron ustedes, qué corrigieron del output).
- **Capacidad de explicación:** ver protocolo arriba.

Sugerencia práctica: use la IA para depurar y para explicarse conceptos, pero **verifique
siempre contra un caso pequeño que pueda calcular a mano**. Por eso el taller empieza con una
red juguete de 8 nodos antes de pasar a los datos reales: si su función falla ahí, ninguna
librería lo va a salvar después.

---

## 4. Rúbrica (sobre 5.0)

| Componente | Peso | Qué se evalúa |
|---|---|---|
| **S1 · Fundamentos de Python** (E1.1–E1.5) | 20% | Uso correcto de listas, conjuntos, diccionarios, comprensiones y BFS. Funciones limpias y generales, no soluciones ad hoc para el ejemplo. |
| **S2 · NumPy y matriz de adyacencia** (E2.1–E2.4) | 15% | Vectorización (sin ciclos innecesarios), interpretación correcta de $A^k$. |
| **S3 · Pandas** (E3.1–E3.4) | 20% | Manipulación correcta de DataFrames, `merge`, `groupby`. Inspección de los datos antes de operar. |
| **S4 · NetworkX y descriptivos** (E4.1–E4.7) | 30% | Estadísticos correctos, contraste explícito contra el código propio (E4.4), gráficas legibles con ejes y títulos rotulados. |
| **S5 · Homofilia y modelo nulo** (E5.1–E5.3) | 15% | Simulación correcta, p-valor bien construido, lectura del resultado. |
| **S6 · Interpretación** (P1–P4) | 15% | Razonamiento económico y estadístico. Se penaliza la respuesta genérica sin referencia a los números obtenidos. |
| **Bonus** (B1/B2/B3) | +0.5 | Uno solo, bien hecho. |

*(Los pesos suman 115%; el excedente compensa parcialmente errores menores. La nota se topa
en 5.0 antes del bonus.)*

**Descuentos transversales:**

- Cuaderno que no corre de principio a fin: −20%
- Declaración de Uso de IA ausente o vacía: −10%
- Gráficas sin rótulos de ejes o sin título: −5% cada una
- Entrega no autocontenida (rutas absolutas, archivos faltantes, dependencias no declaradas): −10%

---

## 5. Errores frecuentes que cuestan nota

- Usar `list` en vez de `set` para vecinos y luego contar duplicados en el grado.
- Olvidar que el grafo es **no dirigido** al construir la lista de adyacencia o la matriz.
- Confundir *recorrido* (walk, puede repetir nodos) con *camino* (path) al interpretar $A^k$.
- Calcular distancia promedio o diámetro sobre un grafo no conexo (hay que restringirse a la componente gigante, y ser explicito sobre la existencia de varias componentes).
- Concluir que hay homofilia solo porque hay pocas aristas cruzadas, sin comparar contra un  modelo nulo.
- Reportar el p-valor sin decir de qué hipótesis nula se trata.

---

## 6. Instalación

```bash
python -m venv .venv
source .venv/bin/activate      # Windows: .venv\Scripts\activate
pip install -r requirements.txt
jupyter lab
```

Todos los datos se generan localmente desde `networkx`; no se requiere descargar nada.
