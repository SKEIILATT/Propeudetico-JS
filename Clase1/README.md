# Clase 1 — Fundamentos de JavaScript
**Coding Bootcamps ESPOL · Mié 8 abr 2026 · 19h30–21h30**

---

## 1. Entorno de trabajo

Para escribir JavaScript necesitás tres cosas:

**VS Code** — es el editor de código donde vas a escribir tus archivos. Es gratuito y lo usan profesionales en todo el mundo. Descargalo en code.visualstudio.com.

**El navegador (Chrome o Firefox)** — ya lo tenés instalado. Tiene una herramienta integrada llamada consola que nos permite ejecutar JavaScript directamente, sin necesidad de crear archivos. Se abre con F12 → pestaña Console.

**Node.js (opcional por ahora)** — permite correr JavaScript fuera del navegador, directamente en tu computadora. Lo vamos a necesitar más adelante.

---

## 2. ¿Qué es JavaScript?

JavaScript es el lenguaje de programación de la web. Es el único lenguaje que los navegadores entienden de forma nativa (junto con HTML y CSS).

- **HTML** define la estructura de la página (los títulos, párrafos, botones).
- **CSS** define el estilo (colores, tamaños, fuentes).
- **JavaScript** le da vida a la página: reacciona cuando hacés click, valida formularios, muestra datos sin recargar la página.

JavaScript también puede correr fuera del navegador gracias a Node.js, lo que lo convierte en uno de los lenguajes más versátiles del mercado.

### ¿Cómo agrego JavaScript a una página?

**Forma A — inline (dentro del HTML):**
```html
<html>
  <script>
    alert("Hi there!");
  </script>
</html>
```
Útil para aprender y probar cosas rápido.

**Forma B — archivo separado (mejor práctica):**
```html
<!-- index.html -->
<html>
  <script src="app.js"></script>
</html>
```
```javascript
// app.js
alert("Saying hi from a different file!");
```
Así separamos la estructura del comportamiento. Es como hacen los proyectos reales.

---

## 3. Sintaxis básica

### Case sensitive
JavaScript distingue entre mayúsculas y minúsculas. Estas son tres variables completamente diferentes:
```javascript
let nombre = "Ana";
let Nombre = "Pedro";
let NOMBRE = "Carlos";
```

### Espacios y saltos de línea
JavaScript ignora los espacios extra y los saltos de línea. Úsalos para hacer el código más legible:
```javascript
// Esto funciona pero es ilegible:
let a=1;let b=2;let c=a+b;

// Esto es lo mismo pero legible:
let a = 1;
let b = 2;
let c = a + b;
```

### Punto y coma
Separa instrucciones. Es opcional (JS lo agrega automáticamente en muchos casos) pero es buena práctica ponerlo siempre:
```javascript
let x = 5;
let y = 10;
console.log(x + y);
```

### Comentarios
El navegador ignora los comentarios. Sirven para explicar qué hace tu código:
```javascript
// Esto es un comentario de una línea

let edad = 20; // También puedo comentar al final de una línea

/*
  Esto es un comentario
  de múltiples líneas
*/
```

---

## 4. Variables

Una variable es una caja con nombre donde guardamos información. En JavaScript tenemos tres formas de declararlas:

### `let` — la más usada
```javascript
let edad = 20;
edad = 21; // Correcto: Se puede cambiar el valor
```
Usala por defecto para cualquier valor que pueda cambiar.

### `const` — para valores fijos
```javascript
const PI = 3.14159;
PI = 3; //  Error: no se puede reasignar una constante
```
Usala cuando el valor no debe cambiar nunca (una URL base, una configuración, etc.).

### `var` — la forma antigua
```javascript
var nombre = "Ana";
```
Funciona, pero tiene comportamientos extraños con el scope (lo veremos en el módulo de funciones). Evitala en código nuevo.

**Regla práctica:** usá `const` por defecto. Si necesitás que el valor cambie, usá `let`. Nunca usés `var`.

---

## 5. Tipos de datos primitivos

JavaScript tiene seis tipos de datos primitivos:

### String — texto
Siempre va entre comillas (simples, dobles o backticks):
```javascript
let nombre = "Ana";
let saludo = 'Hola mundo';
let mensaje = `Hola, mi nombre es ${nombre}`; // template literal
```

### Number — números
Enteros y decimales, positivos y negativos:
```javascript
let edad = 20;
let precio = 3.99;
let temperatura = -5;
let bigNumber = 1_000_000; // el _ es solo visual, no afecta el valor
```

### Boolean — verdadero o falso
Solo tiene dos valores posibles:
```javascript
let esMayorDeEdad = true;
let estaLogueado = false;
```
Se usan mucho en condiciones: "si el usuario está logueado, muestra el perfil".

### Null — ausencia intencional de valor
```javascript
let resultado = null; // "aquí no hay nada, intencionalmente"
```

### Undefined — sin valor asignado
```javascript
let x; // declarada pero sin valor → undefined
console.log(x); // undefined
```

### Symbol — identificador único (avanzado)
```javascript
const id = Symbol("id");
```
No lo vamos a usar en este curso, pero es bueno saber que existe.

### Cómo saber el tipo de una variable
```javascript
typeof "Hola"      // → "string"
typeof 42          // → "number"
typeof true        // → "boolean"
typeof null        // → "object" (¡bug histórico de JS!)
typeof undefined   // → "undefined"
```

---

## 6. Tipos compuestos

### Object — objeto
Colección de propiedades con nombre (clave: valor):
```javascript
const persona = {
  nombre: "Ana",
  edad: 22,
  ciudad: "Guayaquil"
};

persona.nombre        // → "Ana"
persona["edad"]       // → 22
```

### Array — arreglo
Lista ordenada de valores, accesibles por índice (empezando en 0):
```javascript
const frutas = ["manzana", "banana", "naranja"];

frutas[0]  // → "manzana"
frutas[2]  // → "naranja"
frutas.length // → 3
```

---

## 7. Errores comunes

Aprender a leer errores es parte fundamental de programar. Estos son los más frecuentes en esta clase:

**ReferenceError** — usaste una variable que no existe:
```javascript
console.log(precio); // Error: ReferenceError: precio is not defined
let precio = 10;
console.log(precio); // Correcto
```

**SyntaxError** — escribiste algo que JS no puede interpretar:
```javascript
Let nombre = "Ana"; // Incorrecto: SyntaxError — "Let" con mayúscula no existe
let nombre = "Ana"; // Correcto
```

**TypeError: Assignment to constant variable** — intentaste cambiar una constante:
```javascript
const PI = 3.14;
PI = 3; // Error: TypeError
```

---

## Ejercicio de clase

Abrí la consola del navegador (F12 → Console) y escribí esto línea por línea:

```javascript
// 1. Tu primera variable
let miNombre = "TuNombre"; // cambiá por tu nombre real
console.log(miNombre);

// 2. Operaciones con números
let edad = 20;
let anioActual = 2026;
console.log(anioActual - edad); // ¿en qué año naciste?

// 3. Descubrí el tipo de cada valor
typeof "Hola"
typeof 42
typeof true
typeof null
typeof undefined
```

---

## Tarea para casa

1. Creá un archivo `index.html` con JavaScript embebido (Forma A).
2. Declará al menos 5 variables con tipos diferentes (String, Number, Boolean, Null, Undefined).
3. Usá `console.log()` para mostrar cada variable y su tipo con `typeof`.
4. Provocá al menos 2 errores a propósito (ReferenceError y TypeError) y leé el mensaje en la consola.
5. Subí todo a tu carpeta `clase-01` en GitHub.

### Estrategias de práctica recomendadas

**Para reforzar variables y tipos:**
- Abrí la consola del navegador y jugá con `typeof`. ¿Qué devuelve `typeof null`? ¿Por qué?
- Intentá asignar un nuevo valor a una `const` y leé el error.

**Para desarrollar lógica de debugging:**
- Cada vez que veas un error en la consola, buscá el mensaje exacto en Google antes de preguntar. Esto es lo que hace cualquier programador profesional.

**Recurso sugerido:**
- Lee el capítulo 1 de [javascript.info](https://javascript.info/intro) (en inglés, pero muy claro con ejemplos).
