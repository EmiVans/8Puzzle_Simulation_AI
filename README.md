# 8Puzzle_Simulation_AI
# Práctica 1: Simulación del Juego del 8-Puzzle

**Autores:**
Brandon Imanol Regalado Urbina,  
Vazquez Amador Daniel Emiliano,  
Arroyo Lozano Santiago,  
Valencia Cruz Jonathan Josué,  
Luis Gerardo Estrada García

**Fecha:** \today

## Introducción
En esta práctica, se desarrolló una simulación del famoso juego de **8-Puzzle**. El objetivo del juego es organizar los números del 1 al 8 en una cuadrícula de 3x3, moviendo las fichas alrededor de una casilla vacía (representada como 'e'). El estado final deseado es:

|   |   |   |
|---|---|---|
| 1 | 2 | 3 |
| 4 | 5 | 6 |
| 7 | 8 | e |


La práctica incluye la programación de los movimientos posibles (arriba, abajo, izquierda, derecha) y la simulación de cómo estos afectan la configuración del tablero.

## Desarrollo
Para la implementación del juego, se desarrolló la clase `Puzzle8`, que contiene los métodos necesarios para representar y manipular el estado del tablero.

### Estructura de la Clase `Puzzle8`
La clase `Puzzle8` tiene las siguientes funciones principales:
- `__init__`: Inicializa el tablero con un estado dado, un nodo padre, y la acción que llevó a ese estado.
- `__str__`: Permite imprimir el tablero en una forma legible.
- `find_empty`: Encuentra la posición de la casilla vacía ('e').
- `move`: Aplica un movimiento de acuerdo a la dirección indicada (arriba, abajo, izquierda, derecha), intercambiando la posición de 'e' con otra casilla.

### Código Implementado
A continuación se presenta una parte del código implementado en Python para la simulación del juego:

```python
class Puzzle8:
    def __init__(self, state, parent=None, action=None):
        self.state = state
        self.parent = parent
        self.action = action

    def __str__(self):
        return "\n".join(["|".join(map(str, row)) for row in self.state])

    def find_empty(self):
        for i in range(3):
            for j in range(3):
                if self.state[i][j] == 'e':
                    return i, j

    def move(self, direction):
        i, j = self.find_empty()

        if direction == 'up' and i > 0:
            new_state = [row[:] for row in self.state]
            new_state[i][j], new_state[i - 1][j] = new_state[i - 1][j], new_state[i][j]
            return Puzzle8(new_state, self, 'up')

        elif direction == 'down' and i < 2:
            new_state = [row[:] for row in self.state]
            new_state[i][j], new_state[i + 1][j] = new_state[i + 1][j], new_state[i][j]
            return Puzzle8(new_state, self, 'down')

        elif direction == 'left' and j > 0:
            new_state = [row[:] for row in self.state]
            new_state[i][j], new_state[i][j - 1] = new_state[i][j - 1], new_state[i][j]
            return Puzzle8(new_state, self, 'left')

        elif direction == 'right' and j < 2:
            new_state = [row[:] for row in self.state]
            new_state[i][j], new_state[i][j + 1] = new_state[i][j + 1], new_state[i][j]
            return Puzzle8(new_state, self, 'right')

        else:
            return None
```
Resultados
Se realizaron múltiples pruebas para verificar el correcto funcionamiento de los movimientos dentro del tablero. A continuación se muestran algunos ejemplos de las configuraciones obtenidas tras aplicar diversos movimientos.

Conclusión
La simulación del juego del 8-Puzzle fue implementada exitosamente en Python. La estructura de la clase Puzzle8 permite la fácil modificación del estado del tablero y su visualización en formato de texto. Esta práctica ayuda a entender mejor la manipulación de estructuras de datos en un entorno dinámico y la resolución de problemas de búsqueda y optimización.
