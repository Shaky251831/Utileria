# Proyecto: Librería de Utilería JS

**Alumna:** Marquez Agustin Briseida  
**Curso:** 2026 Verano 7 a 10 - Programación Web

---

## Descripción del Proyecto. 

**Objetivo:** Crear una librería JS funcional (sin frameworks, sin componentes visuales) que se usará en un formulario, modal y login.html.

El proyecto incluye 6 funciones principales:

1. `validarCorreo(correo)` → boolean — valida formato de correo electrónico
2. `soloLetras(texto)` → boolean — solo letras mayúsculas/minúsculas, acepta vocales acentuadas
3. `validarLongitud(numero, maxLongitud)` → boolean — valida longitud de un número
4. `calcularEdad(fechaNacimiento)` → número entero — calcula edad a partir de fecha de nacimiento
5. `esMayorDeEdad(fechaNacimiento)` → boolean — valida si es mayor de edad
6. `validarPassword(password)` → boolean — requiere mayúscula, minúscula, número, carácter especial y mínimo 8 caracteres

Las 2 funciones adicionales:

- **`capitalizarTexto(texto)`**: corrige lo que el usuario escribe (Si lo escribió todo en minúsculas o todo en mayúsculas desordenadas), dejando cada palabra con la primera letra en mayúscula.
- **`limpiarEspacios(texto)`**: quita los espacios vacíos que quedan antes de la letra o al escribir doble espacio en medio del texto.

---

## Instalación.

Para utilizar esta librería, se agrega esta línea de código dentro de la página HTML:

```html
<script src="js/utileria.js"></script>
```

---

## Código de la librería.

```javascript
// 1. Validar formato de correo electrónico
function validarCorreo(correo) {
    const regex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
    return regex.test(correo);
}

// 2. Solo letras (mayúsculas/minúsculas, acepta espacios y vocales acentuadas).
function soloLetras(texto) {
    const regex = /^[a-zA-ZáéíóúÁÉÍÓÚñÑ\s]+$/;
    return regex.test(texto);
}

// 3. Valida la longitud máxima de dígitos de un número.
function validarLongitud(numero, maxLongitud) {
    return String(numero).length <= maxLongitud;
}

// 4. Calcula edad exacta a partir de una fecha de nacimiento (YYYY-MM-DD).
function calcularEdad(fechaNacimiento) {
    if (!fechaNacimiento) return 0;
    const hoy = new Date();
    const cumpleanos = new Date(fechaNacimiento);
    let edad = hoy.getFullYear() - cumpleanos.getFullYear();
    const mes = hoy.getMonth() - cumpleanos.getMonth();

    if (mes < 0 || (mes === 0 && hoy.getDate() < cumpleanos.getDate())) {
        edad--;
    }
    return edad;
}

// 5. Valida si es mayor de edad (18 años o más).
function esMayorDeEdad(fechaNacimiento) {
    return calcularEdad(fechaNacimiento) >= 18;
}

// 6. Requiere mayúscula, minúscula, número, carácter especial y mínimo 8 caracteres.
function validarPassword(password) {
    const tieneMayuscula = /[A-Z]/.test(password);
    const tieneMinuscula = /[a-z]/.test(password);
    const tieneNumero = /[0-9]/.test(password);
    const tieneEspecial = /[\W_]/.test(password);
    const largoCorrecto = password.length >= 8;

    return tieneMayuscula && tieneMinuscula && tieneNumero && tieneEspecial && largoCorrecto;
}

// --- Las 2 funciones que agregué ---

// 1. Limpiar espacios al inicio, final y duplicados en medio.
function limpiarEspacios(texto) {
    return texto.trim().replace(/\s+/g, ' ');
}

// 2. Capitalizar la primera letra de cada palabra (formato de nombre propio).
function capitalizarTexto(texto) {
    return texto.toLowerCase().replace(/\b\w/g, l => l.toUpperCase());
}
```

---

## Evidencias.

### Capturas de pantalla (consola mostrando resultados).

![Evidencia del Formulario 1](img/Imagen1.png)
![Evidencia del Formulario 2](img/Imagen2.png)

### Video demostrativo.

https://github.com/user-attachments/assets/6aafbf17-1c98-4b26-8c53-e56a16869e8c 
