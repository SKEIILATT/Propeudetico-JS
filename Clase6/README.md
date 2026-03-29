# Clase 6 — Funciones
**Coding Bootcamps ESPOL · Prof. Javier Gutiérrez · Vie 24 abr 2026**

---

## 1. ¿Qué es una función?

Una función es un bloque de código reutilizable con nombre:

```javascript
function saludar(nombre) {       // nombre = parámetro
  return "Hola, " + nombre + "!"; // return = resultado
}

const mensaje = saludar("Ana");  // "Ana" = argumento
console.log(mensaje); // → "Hola, Ana!"
```

**Terminología:**
- **Parámetro:** variable en la definición (`nombre`)
- **Argumento:** valor al llamar (`"Ana"`)
- **return:** devuelve el resultado

---

## 2. Tres variantes de función

```javascript
// Sin parámetros ni return
function horaActual() {
  console.log("Son las " + new Date().getHours() + "h");
}

// Con parámetros, sin return
function saludar(nombre, edad) {
  console.log("Hola " + nombre + ", tenés " + edad + " años");
}

// Con parámetros Y return
function calcularArea(base, altura) {
  return base * altura;
}
const area = calcularArea(5, 3);
console.log(area); // → 15
```

---

## 3. Parámetros por defecto

```javascript
// Sin defecto — puede dar undefined
function saludar(nombre) {
  return "Hola, " + nombre;
}
saludar(); // → "Hola, undefined" 😱

// Con defecto
function saludar(nombre = "amigo") {
  return "Hola, " + nombre;
}
saludar();        // → "Hola, amigo"  ✅
saludar("María"); // → "Hola, María" ✅
```

Los parámetros con defecto van **siempre al final**.

---

## 4. Funciones anónimas y expresiones

```javascript
// Función declarada — tiene hoisting
console.log(sumar(2, 3)); // → 5 ✅ funciona antes de definirla

function sumar(a, b) {
  return a + b;
}

// Expresión de función — SIN hoisting
const restar = function(a, b) {
  return a - b;
};
console.log(restar(5, 2)); // → 3 ✅

// Función anónima como argumento (callback)
const nums = [3, 1, 4, 1, 5];
nums.sort(function(a, b) {
  return a - b;
});
```

---

## Ejercicio — Calculadora

```javascript
function sumar(a, b)       { return a + b; }
function restar(a, b)      { return a - b; }
function multiplicar(a, b) { return a * b; }
function dividir(a, b) {
  if (b === 0) return "Error: no se puede dividir por 0";
  return a / b;
}

function calcularAreaTriangulo(base, altura) {
  return dividir(multiplicar(base, altura), 2);
}

console.log(sumar(10, 5));              // → 15
console.log(dividir(10, 0));            // → "Error..."
console.log(calcularAreaTriangulo(6, 4)); // → 12
```

---

## Tarea

1. Creá una función que convierta Celsius a Fahrenheit: `(C × 9/5) + 32`.
2. Creá `esMayorDeEdad(edad)` que devuelva `true` o `false`.
3. Creá una función que reciba un array y devuelva el promedio.
4. Subí a clase-06 en GitHub.
