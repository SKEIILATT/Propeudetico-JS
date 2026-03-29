# Clase 11 — Buenas Prácticas, Patrones y Cierre
**Coding Bootcamps ESPOL · Prof. Javier Gutiérrez · Mié 13 may 2026**

---

## ESLint — detectar problemas
```bash
npm install -D eslint
npx eslint --init
```
Detecta: `==` en lugar de `===`, variables no usadas, funciones sin return, etc.

## Prettier — formatear automáticamente
```bash
npm install -D prettier
npx prettier --write .
```
Aplica indentación, comillas, punto y coma de forma consistente.

## Convenciones de nomenclatura
| Tipo | Estilo | Ejemplo |
|------|--------|---------|
| Variables/funciones | camelCase | `let miNombre`, `function calcularArea()` |
| Constantes globales | UPPER_SNAKE_CASE | `const MAX_INTENTOS = 3` |
| Clases | PascalCase | `class Usuario` |
| Archivos | kebab-case | `calcular-impuesto.js` |

## Patrones de diseño
**Module Pattern** — estado privado:
```javascript
const contador = (() => {
  let _cuenta = 0;
  return { incrementar: () => ++_cuenta, valor: () => _cuenta };
})();
```

**Factory Pattern** — crear objetos:
```javascript
function crearUsuario(nombre, rol) {
  return { nombre, rol, saludar() { return `Hola, soy ${this.nombre}`; } };
}
```

## JSDoc
```javascript
/**
 * Calcula el descuento de un precio.
 * @param {number} precio - Precio original
 * @param {number} porcentaje - Descuento 0-100
 * @returns {number} Precio con descuento
 * @throws {RangeError} Si porcentaje está fuera de rango
 * @example calcularDescuento(200, 20); // → 160
 */
function calcularDescuento(precio, porcentaje) { ... }
```

## Próximos pasos
- **Corto plazo:** DOM, fetch/APIs, async/await
- **Mediano plazo:** React, Vue o Angular
- **Largo plazo:** Node.js backend, proyecto real completo
