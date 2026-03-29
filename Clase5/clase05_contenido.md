# Clase 5 — while, do...while y Control de Flujo
**Coding Bootcamps ESPOL · Prof. Javier Gutiérrez · Mié 22 abr 2026**

---

## 1. Bucle while

```javascript
let vidas = 3;

while (vidas > 0) {
  console.log("Vidas: " + vidas);
  vidas--;    // ← actualizar siempre, o bucle infinito
}
// Imprime: 3, 2, 1
```

**Cuándo usar:** cuando no sabés cuántas veces repetir. Si sabés, usá `for`.

---

## 2. do...while — al menos una vez

```javascript
// while — puede no ejecutar nunca:
let x = 10;
while (x < 5) {
  console.log(x); // no imprime nada
}

// do...while — ejecuta siempre al menos una vez:
let y = 10;
do {
  console.log(y); // → imprime 10
} while (y < 5);
```

---

## 3. break — salir del bucle

```javascript
const nums = [1, 2, 3, 4, 5, 6, 7, 8];

for (const n of nums) {
  if (n === 5) {
    break;      // sale del bucle aquí
  }
  console.log(n);
}
// Imprime: 1 2 3 4
```

---

## 4. continue — saltar una iteración

```javascript
for (let i = 1; i <= 8; i++) {
  if (i % 2 === 0) {
    continue;   // salta los pares
  }
  console.log(i);
}
// Imprime: 1 3 5 7
```

---

## 5. Etiquetas (labels)

Permiten controlar bucles externos desde uno interno:

```javascript
externo:
for (let i = 0; i < 3; i++) {
  for (let j = 0; j < 3; j++) {
    if (j === 1) break externo;  // rompe el bucle externo
    console.log(i, j);
  }
}
// Solo imprime: 0 0
```

---

## Ejercicio integrador Módulo 2

```javascript
const notas = [4, 8, 6, 9, 3, 7, 5, 10, 2, 8];
let aprobados = 0;
let reprobados = 0;

for (const nota of notas) {
  if (nota < 0 || nota > 10) continue; // nota inválida

  if (nota >= 7) {
    aprobados++;
  } else {
    reprobados++;
  }
}

console.log("Aprobados:", aprobados);   // 6
console.log("Reprobados:", reprobados); // 4
```

**Desafíos:** nota más alta, nota más baja, promedio de aprobados, clasificar con switch.

---

## Tarea

1. Usá `while` para simular un dado: genera números random hasta sacar un 6.
2. Usá `for` + `continue` para imprimir solo los múltiplos de 3 del 1 al 30.
3. Usá `for` + `break` para encontrar el primer número negativo en un array.
4. Subí a clase-05 en GitHub.
