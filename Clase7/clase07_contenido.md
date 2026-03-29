# Clase 7 — Scope, Hoisting, Arrow Functions y Closures
**Coding Bootcamps ESPOL · Prof. Javier Gutiérrez · Mié 29 abr 2026**

---

## 1. Scope — alcance de variables

El scope define desde dónde podés acceder a una variable:

```javascript
let ciudad = "Guayaquil"; // scope global

function saludar() {
  let nombre = "Ana";     // scope de función
  
  if (true) {
    let temp = "temporal"; // scope de bloque
    // Aquí podés ver: ciudad ✅  nombre ✅  temp ✅
  }
  // Aquí podés ver: ciudad ✅  nombre ✅  temp ❌
}
// Aquí podés ver: ciudad ✅  nombre ❌  temp ❌
```

**Regla:** podés acceder a variables de scopes externos, pero no internos.

---

## 2. Hoisting

JavaScript mueve las declaraciones al inicio del scope antes de ejecutar:

```javascript
// function declarada — sube COMPLETA
console.log(sumar(2, 3)); // → 5 ✅
function sumar(a, b) { return a + b; }

// var — sube la declaración, NO el valor
console.log(x); // → undefined (no da error)
var x = 10;

// let/const — NO suben (Temporal Dead Zone)
console.log(nombre); // → ❌ ReferenceError
let nombre = "Ana";
```

---

## 3. Arrow Functions

```javascript
// Función declarada
function sumar(a, b) { return a + b; }

// Expresión de función
const sumar = function(a, b) { return a + b; };

// Arrow function completa
const sumar = (a, b) => { return a + b; };

// Arrow — return implícito (sin llaves)
const sumar = (a, b) => a + b;
```

**Casos especiales:**

```javascript
// Un parámetro — sin paréntesis
const doble = n => n * 2;

// Sin parámetros — paréntesis vacíos obligatorios
const saludar = () => "Hola!";

// Retornar objeto — entre paréntesis
const crearUser = n => ({ nombre: n });

// Cuerpo multilínea — llaves y return explícito
const calcular = (precio, imp) => {
  const total = precio + precio * imp;
  return total.toFixed(2);
};
```

---

## 4. Closures

Un closure es una función que recuerda las variables del scope donde fue creada:

```javascript
function crearContador() {
  let cuenta = 0; // variable privada

  return function() {
    cuenta++;       // recuerda 'cuenta'
    return cuenta;
  };
}

const contador = crearContador();
contador(); // → 1
contador(); // → 2
contador(); // → 3

// 'cuenta' no es accesible desde afuera — está encapsulada
```

**Caso práctico — cuenta bancaria:**

```javascript
function crearCuenta(saldoInicial) {
  let saldo = saldoInicial;
  return {
    depositar: cantidad => { saldo += cantidad; return saldo; },
    retirar:   cantidad => { saldo -= cantidad; return saldo; },
    consultar: ()       => saldo
  };
}

const cuenta = crearCuenta(1000);
cuenta.depositar(500);  // → 1500
cuenta.retirar(200);    // → 1300
```

---

## Tarea

1. Creá `crearSaludador(idioma)` que devuelva una arrow function que salude en ese idioma.
2. Creá un closure `crearCarrito()` con funciones `agregar()`, `quitar()` y `total()`.
3. Reescribí 3 funciones de la clase 6 como arrow functions.
4. Subí a clase-07 en GitHub.
