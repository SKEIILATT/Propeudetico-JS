# Clase 2 — Tipos, Objetos, Arreglos y Operadores
**Coding Bootcamps ESPOL · Vie 10 abr 2026 · 19h30–21h30**

---

## 1. Repaso rápido — clase 1

Antes de arrancar lo nuevo, verificamos que tengamos claro esto:

```javascript
typeof "hola"   // → "string"
typeof 42       // → "number"
typeof true     // → "boolean"
let x;
typeof x        // → "undefined"
```

Y la regla de oro: **`const` por defecto, `let` si el valor cambia, nunca `var`**.

---

## 2. Los tres tipos que faltaron

### Null — vacío intencional

`null` significa "aquí no hay nada, y lo sé". Se usa cuando queremos representar la ausencia de un valor de forma explícita:

```javascript
let carrito = null;
// El carrito existe como variable, pero está vacío a propósito

let usuarioLogueado = null;
// Nadie ha iniciado sesión todavía
```

Algo importante: `typeof null` devuelve `"object"`. Es un bug histórico de JavaScript que existe desde 1995 y nunca se corrigió porque hacerlo rompería millones de páginas web. Solo memorízalo.

### Undefined — sin valor asignado

`undefined` es lo que tiene una variable cuando la declaramos pero no le damos un valor:

```javascript
let nombre;
console.log(nombre); // → undefined

// También aparece cuando buscamos algo que no existe:
const obj = { a: 1 };
console.log(obj.b); // → undefined (la propiedad 'b' no existe)
```

**Diferencia clave:**
- `null` → el programador dijo explícitamente "no hay nada aquí"
- `undefined` → JavaScript dice "esto no tiene valor todavía"

### Symbol — identificador único

Crea valores únicos e irrepetibles. Aunque dos Symbols tengan el mismo nombre, nunca son iguales:

```javascript
const idA = Symbol("id");
const idB = Symbol("id");

idA === idB; // → false — ¡son diferentes!
```

No lo vamos a usar en este curso, pero es bueno saber que existe.

---

## 3. Objects — colecciones de clave: valor

Un objeto es como una ficha con datos. Cada dato tiene un nombre (clave) y un valor:

```javascript
const estudiante = {
  nombre: "Ana García",
  edad: 22,
  ciudad: "Guayaquil",
  activo: true
};
```

### Acceder a propiedades

Hay dos formas, ambas funcionan igual:

```javascript
estudiante.nombre      // → "Ana García"    (notación de punto)
estudiante["edad"]     // → 22              (notación de corchetes)
```

Usa la notación de punto cuando conocés el nombre de la propiedad. Usa los corchetes cuando el nombre viene de una variable:

```javascript
const propiedad = "nombre";
estudiante[propiedad]; // → "Ana García"
```

### Modificar propiedades

```javascript
const user = { nombre: "Ana" };
user.nombre = "María";
console.log(user.nombre); // → "María"
```

Ojo: aunque `user` es `const`, podemos modificar sus propiedades. `const` protege la referencia al objeto, no su contenido.

### Agregar propiedades

```javascript
const auto = { marca: "Toyota" };
auto.color = "rojo";
auto.año = 2022;
// → { marca: "Toyota", color: "rojo", año: 2022 }
```

### Eliminar propiedades

```javascript
const p = { x: 1, y: 2, z: 3 };
delete p.z;
console.log(p); // → { x: 1, y: 2 }
```

### Verificar si una propiedad existe

```javascript
const obj = { a: 1 };
"a" in obj;             // → true
"b" in obj;             // → false
obj.hasOwnProperty("a"); // → true
```

---

## 4. Arrays — listas ordenadas

Un array es una lista donde cada elemento tiene una posición llamada **índice**, que siempre empieza en **0**, no en 1:

```javascript
const frutas = ["manzana", "banana", "naranja", "uva"];
//               índice 0    índice 1   índice 2   índice 3
```

### Acceder a elementos

```javascript
frutas[0]  // → "manzana"
frutas[3]  // → "uva"
frutas[10] // → undefined (no existe, pero no da error)
```

### Propiedad length

```javascript
frutas.length; // → 4 (número de elementos)

// Último elemento siempre:
frutas[frutas.length - 1]; // → "uva"
```

### Métodos principales

**Agregar elementos:**
```javascript
frutas.push("kiwi");     // agrega al FINAL   → 5 elementos
frutas.unshift("fresa"); // agrega al INICIO  → 6 elementos
```

**Eliminar elementos:**
```javascript
frutas.pop();   // elimina el ÚLTIMO  → devuelve el elemento eliminado
frutas.shift(); // elimina el PRIMERO → devuelve el elemento eliminado
```

**Buscar elementos:**
```javascript
frutas.includes("banana");  // → true  (¿existe?)
frutas.indexOf("naranja");  // → 2     (¿en qué posición?)
frutas.indexOf("papaya");   // → -1    (no existe)
```

---

## 5. Operadores aritméticos

```javascript
5 + 3   // → 8   (suma)
10 - 4  // → 6   (resta)
3 * 4   // → 12  (multiplicación)
15 / 4  // → 3.75 (división — siempre da decimal si aplica)
10 % 3  // → 1   (módulo: el resto de la división entera)
2 ** 8  // → 256 (potencia: 2 elevado a la 8)
```

**El + con strings concatena:**
```javascript
"Ho" + "la"         // → "Hola"
"Edad: " + 20       // → "Edad: 20"
"Edad: " + 20 + 1   // → "Edad: 201"  ⚠️ ojo con esto
"Edad: " + (20 + 1) // → "Edad: 21"   ✅ con paréntesis
```

---

## 6. Operadores de asignación

Son atajos para modificar una variable:

```javascript
let x = 10;

x += 3;  // equivale a: x = x + 3  → x = 13
x -= 2;  // equivale a: x = x - 2  → x = 11
x *= 4;  // equivale a: x = x * 4  → x = 44
x /= 2;  // equivale a: x = x / 2  → x = 22

x++;     // equivale a: x = x + 1  → x = 23
x--;     // equivale a: x = x - 1  → x = 22
```

---

## 7. Operador ternario

Es un `if-else` comprimido en una sola línea:

```
condicion ? valorSiTrue : valorSiFalse
```

**Ejemplo:**
```javascript
let edad = 20;
let acceso = edad >= 18 ? "Mayor de edad" : "Menor de edad";
console.log(acceso); // → "Mayor de edad"
```

**Equivalente con if-else:**
```javascript
let acceso;
if (edad >= 18) {
  acceso = "Mayor de edad";
} else {
  acceso = "Menor de edad";
}
```

Ambas formas hacen exactamente lo mismo. El ternario es más corto cuando la lógica es simple.

---

## Ejercicio de clase — Ficha de un estudiante

```javascript
// 1. Creá tu ficha
const estudiante = {
  nombre: "TuNombre",
  edad: 0,
  ciudad: "TuCiudad",
  materias: ["JS", "HTML", "CSS"],
  activo: true
};

// 2. Mostrá tu nombre
console.log(estudiante.nombre);

// 3. ¿Tenés acceso completo?
let acceso = estudiante.edad >= 18
  ? "Acceso total"
  : "Acceso limitado";
console.log(acceso);

// 4. Ahora probá estos pasos:
// - Agregá tu apellido: estudiante.apellido = "TuApellido"
// - Mostrá la segunda materia: estudiante.materias[1]
// - Agregá una materia nueva: estudiante.materias.push("Node.js")
// - Calculá en qué año naciste: 2026 - estudiante.edad
```

---

## Tarea para casa

1. Creá un objeto `mascota` con: nombre, especie, edad (en años) y vacunada (boolean).
2. Creá un array con 5 películas favoritas.
3. Agregá una película con `push()` y eliminá la primera con `shift()`.
4. Usá el ternario para saber si la mascota es mayor o menor a 5 años.
5. Calculá la edad de la mascota en "años humanos" multiplicando por 7 con `*=`.
6. Subí todo a tu carpeta `clase-02` en GitHub.

### Estrategias de práctica adicionales

- **Para entender índices:** anotá en papel una lista con 5 elementos y escribí el índice debajo de cada uno empezando desde 0. Luego preguntate: ¿cuál es el índice del último? Siempre es `length - 1`.
- **Para el ternario:** antes de escribirlo, formulá la pregunta como si/sino en español: "si la edad es mayor a 18, entonces 'adulto', sino 'menor'". Después traducilo al código.
- **Para operadores de asignación:** tomá cualquier variable numérica y hacé que cambie 5 veces usando `+=`, `-=`, `*=`, `/=` y `++`. Imprimí el valor después de cada cambio.
