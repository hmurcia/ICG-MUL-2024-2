# Primitivas de Graficación

![image](https://github.com/user-attachments/assets/68d80039-f585-42ae-b2d7-124de8267f42)


## Ejemplo en JavaScript/HTML

A continuación, se presentan ejemplos de cómo implementar estas primitivas en un lienzo HTML utilizando el elemento `<canvas>`.

### 1. Lienzo HTML

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Primitivas de Graficación</title>
    <style>
        canvas {
            border: 1px solid black;
        }
    </style>
</head>
<body>
    <canvas id="canvas" width="500" height="500"></canvas>
    <script src="script.js"></script>
</body>
</html>
```

### 2. Script JavaScript (`script.js`)

```javascript
const canvas = document.getElementById('canvas');
const ctx = canvas.getContext('2d');

// Dibujar una línea usando el algoritmo de Bresenham
function dibujarLinea(x1, y1, x2, y2) {
    const dx = Math.abs(x2 - x1);
    const dy = Math.abs(y2 - y1);
    const sx = (x1 < x2) ? 1 : -1;
    const sy = (y1 < y2) ? 1 : -1;
    let err = dx - dy;

    while (true) {
        ctx.fillRect(x1, y1, 1, 1); // Dibuja un píxel
        if (x1 === x2 && y1 === y2) break;
        const err2 = err * 2;
        if (err2 > -dy) {
            err -= dy;
            x1 += sx;
        }
        if (err2 < dx) {
            err += dx;
            y1 += sy;
        }
    }
}

// Dibujar una circunferencia usando el algoritmo de Bresenham
function dibujarCircunferencia(cx, cy, r) {
    let x = r;
    let y = 0;
    let err = 0;

    while (x >= y) {
        ctx.fillRect(cx + x, cy + y, 1, 1);
        ctx.fillRect(cx + y, cy + x, 1, 1);
        ctx.fillRect(cx - y, cy + x, 1, 1);
        ctx.fillRect(cx - x, cy + y, 1, 1);
        ctx.fillRect(cx - x, cy - y, 1, 1);
        ctx.fillRect(cx - y, cy - x, 1, 1);
        ctx.fillRect(cx + y, cy - x, 1, 1);
        ctx.fillRect(cx + x, cy - y, 1, 1);
        y++;
        if (err <= 0) {
            err += 2 * y + 1;
        }
        if (err > 0) {
            x--;
            err -= 2 * x + 1;
        }
    }
}

// Dibujar una elipse
function dibujarElipse(cx, cy, a, b) {
    let x = 0;
    let y = b;
    let a2 = a * a;
    let b2 = b * b;
    let err = b2 - (a2 * b) + (0.25 * a2);

    while (x <= a) {
        ctx.fillRect(cx + x, cy - (b * Math.sqrt(1 - (x * x) / a2)), 1, 1);
        ctx.fillRect(cx - x, cy - (b * Math.sqrt(1 - (x * x) / a2)), 1, 1);
        ctx.fillRect(cx + x, cy + (b * Math.sqrt(1 - (x * x) / a2)), 1, 1);
        ctx.fillRect(cx - x, cy + (b * Math.sqrt(1 - (x * x) / a2)), 1, 1);
        x++;
        err += b2 * (2 * x + 1);
        if (err >= 0) {
            y--;
            err -= a2 * (2 * y + 1);
        }
    }
}

// Dibujar las primitivas
ctx.fillStyle = 'black';
dibujarLinea(50, 50, 200, 200);
dibujarCircunferencia(300, 100, 50);
dibujarElipse(400, 300, 80, 50);
```

## Resultados

- **Vectorizado**: El uso de `<canvas>` permite un enfoque rasterizado, donde cada forma se dibuja píxel a píxel. Si se requiere un formato vectorizado (como SVG), se pueden usar elementos SVG en lugar de `<canvas>`.

- **Rasterizado**: La representación visual resultante de los ejemplos es rasterizada, ya que se dibujan píxeles en un lienzo, lo que puede llevar a pérdida de calidad al escalar.

## Conclusión

Las primitivas de graficación son esenciales en computación gráfica y se pueden implementar de manera efectiva en JavaScript utilizando el elemento `<canvas>`. Esto te permite crear visualizaciones básicas, y a partir de ahí, puedes construir aplicaciones más complejas y avanzadas. Para trabajar con gráficos vectoriales, considerar el uso de SVG, que permitirá escalar sin pérdida de calidad.
