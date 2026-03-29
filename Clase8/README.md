# Clase 8 — Arreglos y sus Métodos Funcionales
**Coding Bootcamps ESPOL · Prof. Javier Gutiérrez · Vie 1 may 2026**

---

## forEach
Ejecuta una función por cada elemento. **No devuelve nada.**
```javascript
const frutas = ["manzana","banana","naranja"];
frutas.forEach((fruta, indice) => {
  console.log(indice + ": " + fruta);
});
```

## map
Crea un **nuevo array** transformando cada elemento. El original no cambia.
```javascript
const nums = [1,2,3,4,5];
const dobles = nums.map(n => n * 2);
// → [2,4,6,8,10]
// nums sigue siendo [1,2,3,4,5]
```

## filter
Crea un **nuevo array** con los elementos que pasan la condición.
```javascript
const edades = [12,25,8,30,19];
const mayores = edades.filter(n => n >= 18);
// → [25,30,19]
```

## reduce
Acumula el array en **un solo valor**.
```javascript
const precios = [120,45,89,200,15];
const total = precios.reduce((suma, precio) => suma + precio, 0);
// → 469

// Paso a paso: 0+120=120, 120+45=165, 165+89=254, 254+200=454, 454+15=469
```

## Encadenamiento
```javascript
const nums = [1,2,3,4,5,6,7,8,9,10];
const resultado = nums
  .filter(n => n % 2 === 0)  // → [2,4,6,8,10]
  .map(n => n * 2);           // → [4,8,12,16,20]
```

## Tarea
- Dado un array de precios, calculá el total, promedio y precio máximo.
- Filtrá los productos con stock > 0 y mostrá solo sus nombres.
- Subí a clase-08 en GitHub.
