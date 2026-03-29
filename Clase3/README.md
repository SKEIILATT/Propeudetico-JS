# Clase 3 — Operadores de Comparación y Lógicos
**Coding Bootcamps ESPOL · Prof. Javier Gutiérrez · Mié 15 abr 2026**

---

## 1. Repaso rápido

```javascript
const a = { x: 1 };
a.y                        // → undefined (propiedad que no existe)

const f = ["a","b","c"];
f[f.length - 1]            // → "c" (último elemento)

let n = 10; n += 5; n *= 2; n  // → 30
5 > 3 ? "mayor" : "menor"      // → "mayor"
```

---

## 2. Operadores de comparación

Comparan dos valores y siempre devuelven `true` o `false`.

| Operador | Nombre | Ejemplo | Resultado |
|----------|--------|---------|-----------|
| `==` | Igual (con coerción) | `5 == '5'` | `true` ⚠️ |
| `===` | Igual estricto | `5 === '5'` | `false` ✅ |
| `!=` | Diferente (con coerción) | `5 != '6'` | `true` |
| `!==` | Diferente estricto | `5 !== '5'` | `true` ✅ |
| `>` | Mayor que | `8 > 5` | `true` |
| `<` | Menor que | `3 < 1` | `false` |
| `>=` | Mayor o igual | `5 >= 5` | `true` |
| `<=` | Menor o igual | `4 <= 3` | `false` |

---

## 3. == vs === — la diferencia más importante del curso

`==` hace **coerción de tipos** — convierte los valores antes de comparar:

```javascript
5 == '5'        // → true  😱  (convirtió string a número)
0 == false      // → true  😱  (false se convierte a 0)
'' == false     // → true  😱
null == undefined // → true 😱
```

`===` compara valor Y tipo — no convierte nada:

```javascript
5 === '5'       // → false ✅
0 === false     // → false ✅
5 === 5         // → true  ✅
```

**Regla de oro: usa siempre `===`. Nunca `==`.**

---

## 4. Operadores lógicos

### `&&` — AND (Y)
Devuelve `true` solo si **ambas** condiciones son verdaderas:

```javascript
true  && true   // → true
true  && false  // → false
false && true   // → false
false && false  // → false

let edad = 20;
let tienePermiso = true;
if (edad >= 18 && tienePermiso) {
  console.log("Puede votar"); // entra aquí ✅
}
```

### `||` — OR (O)
Devuelve `true` si **al menos una** condición es verdadera:

```javascript
true  || true   // → true
true  || false  // → true ✅
false || true   // → true ✅
false || false  // → false

let dia = "sabado";
if (dia === "sabado" || dia === "domingo") {
  console.log("Es fin de semana");
}
```

### `!` — NOT (NO)
Invierte el valor booleano:

```javascript
!true   // → false
!false  // → true
!0      // → true  (0 es falsy)
!""     // → true  (string vacío es falsy)

let logueado = false;
if (!logueado) {
  console.log("Inicia sesión");
}
```

---

## 5. Truthy y Falsy

JavaScript puede usar cualquier valor como condición. Los **falsy** se comportan como `false`:

```
false, 0, '', null, undefined, NaN
```

Todo lo demás es **truthy**:

```javascript
// Falsy — NO entra al if
if (0) { }
if ("") { }
if (null) { }

// Truthy — SÍ entra al if
if (1) { }
if ("hola") { }
if ([]) { }   // array vacío es truthy!
if ({}) { }   // objeto vacío es truthy!
```

---

## 6. Ejercicio integrador — Módulo 1 completo

```javascript
const alumno = {
  nombre: "TuNombre",
  edad: 0,
  notas: [7, 8, 9, 6, 10],
  aprobado: null
};

// Calculá el promedio
const suma = alumno.notas[0] + alumno.notas[1] + alumno.notas[2]
           + alumno.notas[3] + alumno.notas[4];
const promedio = suma / alumno.notas.length;

// ¿Aprobó?
alumno.aprobado = promedio >= 7;

// ¿Es mayor de edad Y aprobó?
const feliz = alumno.edad >= 18 && alumno.aprobado;

console.log("Promedio:", promedio);
console.log("Aprobado:", alumno.aprobado);
console.log("Feliz:", feliz);
```

**Desafíos:** agregá una nota con `push()`, recalculá el promedio, usá ternario para el mensaje.

---

## Tarea

1. Probá 5 comparaciones con `==` y con `===` — ¿los resultados difieren?
2. Creá una condición con `&&`, otra con `||` y otra con `!`.
3. Completá el ejercicio del alumno con tus propios datos.
4. Subí a clase-03 en GitHub.

### Estrategias de práctica

- **Para `===`:** abrí la consola y probá estas comparaciones: `0 == false`, `0 === false`, `"" == false`, `"" === false`. Observá la diferencia.
- **Para operadores lógicos:** antes de escribirlo en código, escríbelo en español: "si la edad es mayor a 18 Y tiene permiso...". Luego traducilo.
