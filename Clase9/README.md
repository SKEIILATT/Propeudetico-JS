# Clase 9 — Objetos Avanzados, JSON, Set y Map
**Coding Bootcamps ESPOL · Prof. Javier Gutiérrez · Mié 6 may 2026**

---

## Desestructuración
```javascript
const { nombre, edad, pais = "Ecuador" } = usuario;
const { nombre: nombreCompleto } = usuario; // renombrar
function saludar({ nombre, edad }) { ... }  // en parámetros
```

## Spread operator
```javascript
const completo = { ...base, ...extra };          // combinar
const actualizado = { ...base, edad: 23 };       // modificar sin mutar
```

## Object methods
```javascript
Object.keys(obj)     // → array de claves
Object.values(obj)   // → array de valores
Object.entries(obj)  // → array de [clave, valor]
```

## JSON
```javascript
// Objeto → string (para enviar a servidor)
const json = JSON.stringify(usuario);
const bonito = JSON.stringify(usuario, null, 2);

// String → objeto (para procesar respuesta)
const obj = JSON.parse('{"nombre":"Ana","edad":22}');
```

## Set — valores únicos
```javascript
const set = new Set(["a","b","a","c"]); // → Set {"a","b","c"}
set.add("d"); set.delete("a"); set.has("b"); set.size;

// Eliminar duplicados de array:
const unico = [...new Set(array)];
```

## Map — claves de cualquier tipo
```javascript
const m = new Map();
m.set("Ana", 95); m.get("Ana"); m.has("Carlos"); m.size;
for (const [nombre, puntos] of m) { ... }
```

## Tarea
- Parsea un JSON string con array de objetos y extrae los nombres.
- Dado un array con palabras repetidas, usá Set para eliminar duplicados.
- Creá un Map que cuente cuántas veces aparece cada letra en una frase.
- Subí a clase-09 en GitHub.
