# Clase 10 — Manejo de Errores y Depuración
**Coding Bootcamps ESPOL · Prof. Javier Gutiérrez · Vie 8 may 2026**

---

## Tipos de error
- **SyntaxError** — código mal escrito, JS no puede leerlo
- **ReferenceError** — variable que no existe
- **TypeError** — operación inválida para ese tipo
- **RangeError** — valor fuera del rango permitido

## try / catch / finally
```javascript
function dividir(a, b) {
  try {
    if (b === 0) throw new Error("No se divide por 0");
    return a / b;
  } catch (error) {
    console.error("Error:", error.message);
    return null;
  } finally {
    console.log("Operación completada"); // siempre se ejecuta
  }
}
```

## throw — errores personalizados
```javascript
function validarEdad(edad) {
  if (typeof edad !== "number") throw new TypeError("Debe ser número");
  if (edad < 0 || edad > 150)  throw new RangeError("Fuera de rango");
  return true;
}
```

## DevTools
- **Console:** `console.log`, `console.error`, `console.table`
- **Sources:** breakpoints, step over/into, call stack
- **Network:** ver peticiones y respuestas de APIs

## Debugging sistemático
1. Lee el error completo — nombre, mensaje, línea
2. Reproduce el error
3. Aísla el problema — reduce a caso mínimo
4. `console.log` estratégico
5. Busca el error exacto en Google
6. Verifica tus suposiciones

## Tarea
- Creá `validarEmail(email)` que lance errores descriptivos.
- Creá una función que parsee JSON y maneje errores con try/catch.
- Subí a clase-10 en GitHub.
