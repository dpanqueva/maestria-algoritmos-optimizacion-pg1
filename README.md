# Análisis de Complejidad: Secuencia de Fibonacci

Este proyecto presenta un estudio comparativo entre dos enfoques fundamentales para resolver la secuencia de Fibonacci mediante recursión en Python: la **Recursión Ingenua** y la **Recursión con Memorización (Top-Down)**. El objetivo es demostrar cómo la optimización de algoritmos mediante Programación Dinámica puede transformar un código inviable en una solución de alto rendimiento.

---

## 📊 Tabla Comparativa de Complejidad

| Algoritmo | Complejidad Temporal | Complejidad Espacial (Auxiliar) | Viabilidad Práctica |
| :--- | :--- | :--- | :--- |
| **Opción 1: Con Memorización** | $O(N)$ - Lineal | $O(N)$ - Pila + Diccionario | **Excelente** (Eficiente) |
| **Opción 2: Recursión Ingenua** | $O(\phi^N) \approx O(2^N)$ - Exponencial | $O(N)$ - Solo Pila de llamadas | **Inviable** (Colapsa con $N > 40$) |

---

## 🛠️ Análisis de las Implementaciones

### 1. Recursión con Memorización (Top-Down)
Este enfoque introduce un diccionario intermedio (`memo`) que actúa como memoria a corto plazo del algoritmo, previniendo la redundancia mediante una técnica de Programación Dinámica.

```python
def fibonacci_opt(N: int, memo: dict[int, int] = None) -> int:

    if memo is None:
        memo = {}

    if N in memo:
        return memo[N]

    if N < 2:
        resultado = 1
    else:
        resultado = fibonacci_opt(N - 1, memo) + fibonacci_opt(N - 2, memo)

    memo[N] = resultado
    return resultado

fibonacci_opt(5)