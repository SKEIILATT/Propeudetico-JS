# Clase 4 — Condicionales y Bucles for
**Coding Bootcamps ESPOL · Prof. Javier Gutiérrez · Vie 17 abr 2026**

---

## 1. if / else if / else

```javascript
let nota = 75;

if (nota >= 90) {
  console.log("Excelente 🏆");
} else if (nota >= 70) {
  console.log("Aprobado ✅");    // entra aquí
} else if (nota >= 50) {
  console.log("Recuperación ⚠️");
} else {
  console.log("Reprobado ❌");
}
```

Solo **uno** de los bloques se ejecuta — el primero cuya condición sea verdadera.

---

## 2. switch

Ideal cuando comparás **una** variable contra muchos valores:

```javascript
let dia = "lunes";

switch (dia) {
  case "lunes":
    console.log("Inicio de semana");
    break;            // ← obligatorio
  case "viernes":
    console.log("¡Por fin viernes!");
    break;
  case "sabado":
  case "domingo":     // dos casos juntos
    console.log("Fin de semana 🎉");
    break;
  default:            // como el else
    console.log("Día normal");
}
```

**Sin `break`** el código sigue ejecutando los casos siguientes (fall-through).

---

## 3. Bucle for clásico

```
for (inicio ; condición ; incremento) { }
```

```javascript
for (let i = 0; i < 5; i++) {
  console.log("Vuelta número " + i);
}
// Imprime: 0, 1, 2, 3, 4
```

| Parte | Qué hace | Cuándo se ejecuta |
|-------|----------|-------------------|
| `let i = 0` | Inicio | Una sola vez al comienzo |
| `i < 5` | Condición | Antes de cada vuelta |
| `i++` | Incremento | Al final de cada vuelta |

---

## 4. for...of — para arrays

```javascript
const frutas = ["🍎", "🍌", "🍊"];

for (const fruta of frutas) {
  console.log(fruta);
}
// 🍎
// 🍌
// 🍊
```

---

## 5. for...in — para objetos

```javascript
const auto = { marca: "Toyota", color: "rojo", año: 2022 };

for (const clave in auto) {
  console.log(clave + ": " + auto[clave]);
}
// marca: Toyota
// color: rojo
// año: 2022
```

---

## Tarea

1. Creá un `for` que imprima los números del 1 al 20.
2. Usá `if/else` para clasificar cada número: par o impar (pista: `%`).
3. Creá un array de 5 ciudades y recórrelo con `for...of`.
4. Creá un objeto `persona` y mostrá todas sus propiedades con `for...in`.
5. Subí a clase-04 en GitHub.
