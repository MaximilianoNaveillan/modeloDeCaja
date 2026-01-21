# 🧭 Guía Paso a Paso – Demo Modelo de Cajas con Tarjeta de Presentación

**HTML + CSS desde cero**

---

## 🎯 Objetivo de la Demo

Construir una **tarjeta de presentación de usuario (card)** inspirada en un diseño profesional, para observar y experimentar con:

- Modelo de cajas (box model)
- `display: block` vs `inline-block`
- `margin`, `padding` y `border`
- `box-sizing: border-box`
- `position: static`, `relative`, `absolute`
- Layout fluido (`%`) vs fijo (`px`)
- Uso de herramientas de inspección del navegador

La actividad se realiza **desde cero**, sin código previo, replicando un prototipo de referencia.

---

## 1️⃣ Preparar el entorno de trabajo

### 1.1 Crear estructura de archivos

En una carpeta nueva del proyecto:

```
/box-model-demo
  ├── index.html
  └── styles.css
```

### 1.2 Crear el HTML base

En `index.html` escribir:

```html
<!DOCTYPE html>
<html lang="es">
  <head>
    <meta charset="UTF-8" />
    <title>Demo Modelo de Cajas - Card</title>
    <link rel="stylesheet" href="styles.css" />
  </head>
  <body></body>
</html>
```

📌 Nota:

- `<!DOCTYPE html>` define HTML5
- `link` conecta el CSS

---

## 2️⃣ Analizar el componente antes de codificar

Antes de escribir código, identificar las cajas:

Elementos de la card:

- Contenedor principal (card)
- Imagen de usuario
- Nombre
- Cargo
- Contenedor de redes
- Enlaces individuales

📌 Pregunta al grupo:

> ¿Qué elementos serán cajas de bloque y cuáles podrían ser inline?

---

## 3️⃣ Crear la estructura HTML de la tarjeta

Dentro del `<body>` agregar:

```html
<div class="card">
  <img class="card__avatar" src="https://via.placeholder.com/150" alt="Usuario" />

  <h2 class="card__name">Juan Pérez</h2>
  <p class="card__role">Desarrollador Frontend</p>

  <div class="card__social">
    <a href="#" class="card__link">LinkedIn</a>
    <a href="#" class="card__link">GitHub</a>
    <a href="#" class="card__link">Twitter</a>
  </div>
</div>
```

📌 Explicar:

- `.card` es la caja contenedora
- Cada hijo es una caja independiente

---

## 4️⃣ Reset básico y estilos iniciales

En `styles.css` escribir:

```css
* {
  box-sizing: content-box;
}

body {
  font-family: Arial, sans-serif;
  background-color: #f2f2f2;
  padding: 40px;
}

.card {
  background-color: white;
  width: 300px;
  border: 2px solid #333;
}
```

📌 Mostrar:

- La card aparece sin centrado
- Todo usa `box-sizing: content-box` por defecto

---

## 5️⃣ Explorar `display: block` vs `inline-block`

### 5.1 Forzar display block

```css
.card__link {
  display: block;
  border: 1px dashed red;
}
```

📌 Observar:

- Cada enlace ocupa una línea completa

### 5.2 Cambiar a inline-block

```css
.card__link {
  display: inline-block;
}
```

📌 Comparar:

- Ahora se alinean horizontalmente

---

## 6️⃣ Trabajar con margin, padding y border

Agregar:

```css
.card {
  padding: 20px;
}

.card__avatar {
  display: block;
  margin: 0 auto 15px auto;
  border: 4px solid #ccc;
}

.card__name {
  margin: 10px 0 5px 0;
}

.card__role {
  margin: 0 0 15px 0;
}

.card__link {
  margin: 5px;
  padding: 5px 10px;
  border: 1px solid #333;
}
```

📌 Actividad:

- Ir quitando y agregando `margin` y `padding`
- Observar cómo cambia el tamaño total de la card

---

## 7️⃣ Analizar el modelo de cajas con DevTools

Instrucciones:

1. Abrir la página en el navegador
2. Clic derecho → Inspeccionar
3. Seleccionar `.card`
4. Observar:
   - Margin (naranja)
   - Border
   - Padding (verde)
   - Content

📌 Pregunta clave:

> ¿Qué suma exactamente al ancho total del elemento?

---

## 8️⃣ Cambiar a `box-sizing: border-box`

Modificar al inicio del CSS:

```css
* {
  box-sizing: border-box;
}
```

📌 Comparar:

- Antes: width + padding + border
- Ahora: todo cabe dentro del `width: 300px`

Actividad:

- Cambiar `padding` de `.card` a `40px`
- Ver si la card crece o no

---

## 9️⃣ Probar `position: static`, `relative` y `absolute`

### 9.1 Posición por defecto

```css
.card__avatar {
  position: static;
}
```

📌 Explicar:

- `static` es el comportamiento normal

### 9.2 Usar relative

```css
.card__avatar {
  position: relative;
  top: 10px;
  left: 10px;
}
```

📌 Observar:

- Se mueve respecto a su posición original

### 9.3 Usar absolute

```css
.card {
  position: relative;
}

.card__avatar {
  position: absolute;
  top: -20px;
  left: 50%;
  transform: translateX(-50%);
}
```

📌 Explicar:

- El absoluto se posiciona respecto al padre con `position: relative`

---

## 🔟 Comparar layout fijo vs fluido

### 10.1 Layout fijo

```css
.card {
  width: 300px;
}
```

Cambiar el tamaño de la ventana.

📌 Observar:

- La card no cambia de tamaño

### 10.2 Layout fluido

```css
.card {
  width: 80%;
  max-width: 400px;
}
```

📌 Observar:

- La card se adapta al ancho de la pantalla

---

## 1️⃣1️⃣ Centrar la tarjeta usando márgenes

```css
.card {
  margin: 0 auto;
}
```

📌 Explicar:

- `auto` centra horizontalmente bloques con ancho definido

---

## 1️⃣2️⃣ Inspección guiada en vivo

Ejercicio práctico:

1. Seleccionar `.card` en DevTools
2. Desactivar temporalmente:
   - padding
   - border
   - box-sizing

3. Observar en tiempo real:
   - Cambios de tamaño
   - Cambios de posición

---

## 1️⃣3️⃣ Comparación final y reflexión

Preguntas para el grupo:

- ¿Qué diferencia notaste entre `content-box` y `border-box`?
- ¿Cuándo usarías `absolute` en un proyecto real?
- ¿Qué layout es más flexible: `%` o `px`?

---

## 📦 Resultado esperado

Al finalizar, los estudiantes deben entender:

- Cómo funciona el modelo de cajas
- Cómo afectan `margin`, `padding` y `border`
- Cómo cambia el layout con `box-sizing`
- Cómo influyen los distintos tipos de `position`
- Cómo inspeccionar visualmente cada caja en el navegador

---

## 🧩 Extensión opcional

- Agregar `display: flex` en `.card__social`
- Agregar un `:hover` a los enlaces
- Convertir la card en responsive

## considerar:

# Tabla 1 – Propiedad display

| Display        | ¿Ocupa toda la línea?  | ¿Permite width/height? | ¿Se alinean en línea? | Uso típico                                  |
| -------------- | ---------------------- | ---------------------- | --------------------- | ------------------------------------------- |
| `block`        | Sí                     | Sí                     | No                    | Contenedores, secciones, div, p, h1-h6      |
| `inline`       | No                     | ❌ No                  | Sí                    | span, enlaces dentro de texto               |
| `inline-block` | No                     | Sí                     | Sí                    | Botones, tarjetas pequeñas, íconos          |
| `none`         | ❌ No (no se muestra)  | ❌ No                  | ❌ No                 | Ocultar elementos                           |
| `flex`         | Depende del contenedor | Sí                     | Depende del eje       | Layouts modernos, alineación de componentes |

# Tabla 1 – Propiedad position

| Position   | ¿Sale del flujo? | ¿Ocupa espacio? | ¿Respecto a qué se posiciona?                     | ¿top/left funcionan? | Uso típico                             |
| ---------- | ---------------- | --------------- | ------------------------------------------------- | -------------------- | -------------------------------------- |
| `static`   | No               | Sí              | Flujo normal del documento                        | ❌ No                | Layout por defecto                     |
| `relative` | No               | Sí              | Su posición original                              | ✅ Sí                | Ajustes finos, base para absolute      |
| `absolute` | Sí               | ❌ No           | Primer ancestro con `position` distinto de static | ✅ Sí                | Badges, overlays, tooltips             |
| `fixed`    | Sí               | ❌ No           | Viewport (pantalla)                               | ✅ Sí                | Menús fijos, botones flotantes         |
| `sticky`   | Parcial          | Sí              | Contenedor y luego viewport                       | ✅ Sí                | Headers que se “pegan” al hacer scroll |
