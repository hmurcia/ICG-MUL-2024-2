## Algoritmo de Bresenham

El algoritmo de Bresenham es un método eficiente para dibujar líneas rectas en gráficos de píxeles, utilizando enteros en lugar de números de punto flotante.

### Conceptos Básicos

1. **Píxeles**: En un gráfico rasterizado, la pantalla se divide en una cuadrícula de píxeles.
2. **Coordenadas**: Se representan puntos en un plano 2D con coordenadas (x, y).

### Pasos del Algoritmo de Bresenham

1. **Inicialización**:
   - Comienza con dos puntos extremos: el punto inicial \((x_0, y_0)\) y el punto final \((x_1, y_1)\).
   - Calcula los cambios en las coordenadas:

     $$dx = x_1 - x_0$$
 
     $$dy = y_1 - y_0$$
   - Determina las direcciones:
     - \(sx = 1\) si \(dx > 0\) (mover a la derecha), \(sx = -1\) si \(dx < 0\) (mover a la izquierda).
     - \(sy = 1\) si \(dy > 0\) (mover hacia abajo), \(sy = -1\) si \(dy < 0\) (mover hacia arriba).

2. **Decidir la pendiente**:
   - El algoritmo utiliza la relación entre \(dx\) y \(dy\) para decidir cómo avanzar en la cuadrícula de píxeles.
   - Define la variable de error:
     - \(D = 2 \cdot dy - dx\) si la línea es más horizontal.
     - \(D = 2 \cdot dx - dy\) si la línea es más vertical.

3. **Dibujo de la línea**:
   - Comienza en \((x_0, y_0)\) y para cada valor de \(x\) o \(y\):
     - Si \(D > 0\), se incrementa la coordenada correspondiente (ya sea \(y\) o \(x\)), y se actualiza el error.
     - De lo contrario, solo se avanza en la otra dirección (el eje correspondiente).

### Ejemplo Gráfico

#### Supongamos que queremos dibujar una línea de \((2, 3)\) a \((7, 6)\):

1. **Inicialización**:
   - \(dx = 7 - 2 = 5\)
   - \(dy = 6 - 3 = 3\)
   - \(sx = 1\), \(sy = 1\)

2. **Determinar la pendiente**:
   - Como \(dx > dy\), comenzamos a incrementarnos en \(x\):
   - Inicialmente, \(D = 2 \cdot 3 - 5 = 1\).

3. **Dibujo**:
   - Comenzamos en \((2, 3)\).
   - A medida que avanzamos en \(x\):
     - Para \(x = 2\): (píxel en \((2, 3)\)), \(D = 1\).
     - Para \(x = 3\): \(D > 0\), incrementamos \(y\) a 4, nuevo \(D = -1\).
     - Para \(x = 4\): (píxel en \((4, 4)\)), \(D = 1\).
     - Para \(x = 5\): \(D > 0\), incrementamos \(y\) a 5, nuevo \(D = -1\).
     - Para \(x = 6\): (píxel en \((6, 5)\)), \(D = 1\).
     - Para \(x = 7\): \(D > 0\), incrementamos \(y\) a 6, nuevo \(D = -1\).

4. **Resultado**:
   - Los píxeles dibujados son \((2, 3)\), \((3, 4)\), \((4, 4)\), \((5, 5)\), \((6, 5)\), y \((7, 6)\).

### Resumen Visual

Puedes imaginar el algoritmo como un recorrido a lo largo de la cuadrícula de píxeles, decidiendo en cada paso qué píxel activar basándose en el valor de \(D\). Este método asegura que la línea dibujada se vea recta y continua, minimizando el error visual.

Si necesitas una representación visual más gráfica (como un diagrama), podría ser útil buscar ilustraciones específicas sobre el algoritmo de Bresenham en línea, ya que muchos recursos visuales explican estos pasos de manera clara. ¡Espero que esto te ayude a entender el algoritmo! Si tienes más preguntas, no dudes en preguntar.

![image](https://github.com/user-attachments/assets/16e28eed-7f3c-4516-bf98-08e947c61130)
