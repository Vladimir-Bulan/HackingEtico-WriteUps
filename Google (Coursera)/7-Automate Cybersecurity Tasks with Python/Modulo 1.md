# Módulo 1 – Automate Cybersecurity Tasks with Python

## 1. Introducción

El **Módulo 1** establece las bases para el curso: introduce los conceptos fundamentales de programación con Python que luego se aplicarán en automatización de tareas de ciberseguridad. Este módulo busca asegurarse de que todos los estudiantes tengan la comprensión básica necesaria para avanzar con scripts simples y manejo de datos.

---

## 2. Objetivos del módulo

Al finalizar este módulo, el estudiante habrá logrado:

- Repasar los fundamentos de Python (variables, tipos de datos, estructuras básicas).  
- Comprender cómo leer y escribir en archivos desde Python.  
- Familiarizarse con el uso de librerías estándar útiles para automatización.  
- Crear scripts sencillos que manipulen datos básicos (cadenas, listas, diccionarios).  
- Sentar bases para los módulos posteriores, donde se aplicará Python a tareas de ciberseguridad más avanzadas.

---

## 3. Contenidos típicos / temas principales

Aunque no tengo acceso al contenido exacto interno de Coursera para ese módulo, estos temas son los habituales en un primer módulo de “Python para ciberseguridad”:

### 3.1 Fundamentos de Python

- Tipos de datos básicos: cadenas (strings), enteros, flotantes, booleanos.  
- Estructuras: listas, tuplas, diccionarios, sets.  
- Operaciones comunes con cadenas y listas (acceso, slicing, métodos).  

### 3.2 Control de flujo

- Condicionales `if / elif / else`.  
- Bucles `for` y `while`.  
- Uso de `break`, `continue`.  
- Comprensiones de listas/diccionarios.

### 3.3 Funciones

- Definición y llamada de funciones (`def`).  
- Parámetros posicionales y por palabra clave (kwargs).  
- Retorno de valores.  
- Modularización básica del código.

### 3.4 Manejo de archivos

- Apertura / cierre de archivos (`open`, `with`).  
- Lectura (`read`, `readline`, `readlines`) y escritura (`write`, `writelines`).  
- Manipulación de formatos de archivo simples (texto, CSV, JSON si aplica).

### 3.5 Librerías estándar útiles

- Módulos como `os`, `sys`, `time`, `datetime`.  
- Librerías para manipulación de rutas de archivos (`os.path`, `pathlib`).  
- Posible introducción a `re` (expresiones regulares) si hay espacio.

---

## 4. Ejemplos prácticos posibles

- Un script que lea un archivo de texto, cuente cuántas veces aparece una palabra clave específica y muestre el resultado.  
- Un programa que reciba una lista de direcciones IP en un archivo y genere una salida filtrada según un criterio (por ejemplo, eliminar duplicados).  
- Funciones auxiliares que validen formato de cadenas (por ejemplo, ver si una cadena representa una dirección IP válida).  
- Automatizar la lectura de múltiples archivos en un directorio y procesarlos uno por uno.

---

## 5. Buenas prácticas y reflexiones

- Siempre usar `with open(...) as f:` para asegurar que los archivos se cierren adecuadamente.  
- Validar los datos leídos (no asumir que el contenido será siempre correcto).  
- Escribir funciones pequeñas que hagan tareas claras (modularidad).  
- Manejar excepciones con `try/except` cuando haya operaciones de I/O.  
- Documentar el propósito del script o función mediante comentarios o docstrings.

---

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/6fb3d8b6-60a1-46ac-beea-7b4595325033" />

