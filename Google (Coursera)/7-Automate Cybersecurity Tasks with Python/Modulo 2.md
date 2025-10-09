
# 📘 Writeup: Automatizar Tareas de Seguridad Cibernética con Python

## Módulo 2: Escribir Código Python Eficaz

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![Coursera](https://img.shields.io/badge/Coursera-Google%20Cybersecurity-0056D2.svg)](https://www.coursera.org/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

---

## 📋 Tabla de Contenidos

- [Descripción General](#descripción-general)
- [Objetivos de Aprendizaje](#objetivos-de-aprendizaje)
- [Conceptos Clave](#conceptos-clave)
- [Ejercicios Prácticos](#ejercicios-prácticos)
- [Recursos Adicionales](#recursos-adicionales)
- [Contacto](#contacto)

---

## 🎯 Descripción General

Este módulo se enfoca en desarrollar habilidades fundamentales para escribir código Python eficiente y efectivo en el contexto de la seguridad cibernética. Se cubren estructuras de control, funciones, y mejores prácticas para automatizar tareas de seguridad.

**Duración estimada:** 4-6 horas  
**Nivel:** Principiante-Intermedio

---

## 🎓 Objetivos de Aprendizaje

Al completar este módulo, serás capaz de:

- ✅ Implementar estructuras condicionales para la toma de decisiones
- ✅ Utilizar bucles para automatizar tareas repetitivas
- ✅ Crear y utilizar funciones personalizadas
- ✅ Manejar diferentes tipos de datos y estructuras
- ✅ Aplicar mejores prácticas en la escritura de código Python
- ✅ Desarrollar scripts básicos para análisis de seguridad

---

## 🔑 Conceptos Clave

### 1. Estructuras Condicionales

Las declaraciones condicionales permiten que el código tome decisiones basadas en condiciones específicas.

```python
# Ejemplo: Verificación de intentos de inicio de sesión
intentos_fallidos = 5

if intentos_fallidos >= 5:
    print("Cuenta bloqueada por múltiples intentos fallidos")
elif intentos_fallidos >= 3:
    print("Advertencia: Múltiples intentos fallidos detectados")
else:
    print("Acceso permitido")
```

**Aplicación en Seguridad:**
- Validación de credenciales
- Detección de anomalías
- Control de acceso basado en políticas

### 2. Bucles (Loops)

Los bucles permiten ejecutar código repetidamente, esencial para procesar grandes volúmenes de datos de seguridad.

#### Bucle `for`

```python
# Ejemplo: Análisis de múltiples direcciones IP
direcciones_ip = ["192.168.1.1", "10.0.0.5", "172.16.0.10"]

for ip in direcciones_ip:
    print(f"Analizando dirección: {ip}")
    # Lógica de análisis aquí
```

#### Bucle `while`

```python
# Ejemplo: Monitoreo continuo
intentos = 0
max_intentos = 3

while intentos < max_intentos:
    intentos += 1
    print(f"Intento de conexión {intentos}")
    # Lógica de verificación
```

**Aplicación en Seguridad:**
- Análisis de logs
- Escaneo de puertos
- Procesamiento de listas de amenazas

### 3. Funciones

Las funciones permiten encapsular código reutilizable y mantener programas organizados.

```python
def validar_contrasena(contrasena):
    """
    Valida la fortaleza de una contraseña.
    
    Args:
        contrasena (str): Contraseña a validar
        
    Returns:
        bool: True si cumple requisitos, False en caso contrario
    """
    if len(contrasena) < 8:
        return False
    
    tiene_mayuscula = any(c.isupper() for c in contrasena)
    tiene_minuscula = any(c.islower() for c in contrasena)
    tiene_numero = any(c.isdigit() for c in contrasena)
    
    return tiene_mayuscula and tiene_minuscula and tiene_numero

# Uso de la función
password = "Segur1dad123"
if validar_contrasena(password):
    print("Contraseña válida")
else:
    print("Contraseña débil")
```

**Ventajas:**
- Reutilización de código
- Facilita el mantenimiento
- Mejora la legibilidad

### 4. Manipulación de Strings

El trabajo con cadenas de texto es fundamental para analizar logs y datos de seguridad.

```python
# Ejemplo: Extracción de información de logs
log_entry = "2024-10-09 14:30:45 - ERROR - Failed login attempt from 192.168.1.100"

# Dividir el string
partes = log_entry.split(" - ")
timestamp = partes[0]
nivel = partes[1]
mensaje = partes[2]

# Buscar patrones
if "Failed login" in log_entry:
    ip = log_entry.split("from ")[-1]
    print(f"Intento fallido desde: {ip}")
```

### 5. Listas y Diccionarios

Estructuras de datos esenciales para organizar información de seguridad.

```python
# Lista de usuarios sospechosos
usuarios_sospechosos = ["user123", "admin_fake", "root_clone"]

# Diccionario de eventos de seguridad
eventos = {
    "timestamp": "2024-10-09 14:30:45",
    "tipo": "login_fallido",
    "usuario": "admin",
    "ip_origen": "192.168.1.100",
    "severidad": "alta"
}

# Acceso a datos
print(f"Usuario: {eventos['usuario']}")
print(f"Severidad: {eventos['severidad']}")
```

---

## 💻 Ejercicios Prácticos

### Ejercicio 1: Analizador de Intentos de Login

```python
def analizar_intentos_login(intentos):
    """
    Analiza una lista de intentos de login y clasifica por resultado.
    """
    exitosos = 0
    fallidos = 0
    
    for intento in intentos:
        if intento["resultado"] == "exitoso":
            exitosos += 1
        else:
            fallidos += 1
    
    return {
        "exitosos": exitosos,
        "fallidos": fallidos,
        "total": len(intentos)
    }

# Datos de prueba
intentos = [
    {"usuario": "admin", "resultado": "exitoso"},
    {"usuario": "user1", "resultado": "fallido"},
    {"usuario": "admin", "resultado": "fallido"},
    {"usuario": "user2", "resultado": "exitoso"}
]

resultado = analizar_intentos_login(intentos)
print(f"Análisis completo: {resultado}")
```

### Ejercicio 2: Filtro de IPs Sospechosas

```python
def filtrar_ips_sospechosas(ips, ips_bloqueadas):
    """
    Filtra direcciones IP contra una lista de IPs bloqueadas.
    """
    ips_peligrosas = []
    
    for ip in ips:
        if ip in ips_bloqueadas:
            ips_peligrosas.append(ip)
            print(f"⚠️ IP bloqueada detectada: {ip}")
    
    return ips_peligrosas

# Uso
ips_detectadas = ["192.168.1.1", "10.0.0.5", "172.16.0.10", "192.168.1.1"]
lista_negra = ["10.0.0.5", "192.168.1.1"]

ips_encontradas = filtrar_ips_sospechosas(ips_detectadas, lista_negra)
print(f"\nTotal de IPs sospechosas: {len(ips_encontradas)}")
```

### Ejercicio 3: Validador de Políticas de Seguridad

```python
def verificar_politica_seguridad(configuracion):
    """
    Verifica que la configuración cumpla con políticas de seguridad.
    """
    problemas = []
    
    # Verificar timeout de sesión
    if configuracion.get("timeout_sesion", 0) > 30:
        problemas.append("Timeout de sesión demasiado largo")
    
    # Verificar cifrado
    if not configuracion.get("cifrado_habilitado", False):
        problemas.append("Cifrado no habilitado")
    
    # Verificar autenticación de dos factores
    if not configuracion.get("2fa_habilitado", False):
        problemas.append("Autenticación de dos factores deshabilitada")
    
    return problemas

# Prueba
config = {
    "timeout_sesion": 60,
    "cifrado_habilitado": True,
    "2fa_habilitado": False
}

problemas = verificar_politica_seguridad(config)
if problemas:
    print("❌ Problemas de seguridad detectados:")
    for problema in problemas:
        print(f"  - {problema}")
else:
    print("✅ Configuración cumple con políticas de seguridad")
```

---

## 📚 Mejores Prácticas

### 1. Nomenclatura Clara

```python
# ❌ Evitar
x = 5
def f(a):
    return a * 2

# ✅ Preferir
intentos_maximos = 5
def calcular_intentos_restantes(intentos_actuales):
    return intentos_maximos - intentos_actuales
```

### 2. Comentarios y Documentación

```python
def procesar_log(ruta_archivo):
    """
    Procesa un archivo de log y extrae eventos de seguridad.
    
    Args:
        ruta_archivo (str): Ruta al archivo de log
        
    Returns:
        list: Lista de eventos de seguridad encontrados
        
    Raises:
        FileNotFoundError: Si el archivo no existe
    """
    # Implementación aquí
    pass
```

### 3. Manejo de Errores

```python
def leer_archivo_config(ruta):
    try:
        with open(ruta, 'r') as archivo:
            return archivo.read()
    except FileNotFoundError:
        print(f"Error: Archivo {ruta} no encontrado")
        return None
    except PermissionError:
        print(f"Error: Sin permisos para leer {ruta}")
        return None
```

---

## 🛠️ Herramientas y Librerías

- **Python 3.8+**: Lenguaje de programación principal
- **VS Code / PyCharm**: IDEs recomendados
- **Jupyter Notebooks**: Para experimentación interactiva

---

## 📖 Recursos Adicionales

### Documentación Oficial
- [Python Official Documentation](https://docs.python.org/3/)
- [Python Style Guide (PEP 8)](https://pep8.org/)

### Tutoriales Recomendados
- Real Python - Python Security
- OWASP Python Security Project
- Cybersecurity with Python - Coursera

### Lecturas Complementarias
- "Black Hat Python" por Justin Seitz
- "Violent Python" por TJ O'Connor
- "Python for Cybersecurity" por Howard Poston

---

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/8aca2cbd-db5c-40a9-9f61-421b7d1bb784" />

---

## 📝 Notas Finales

Este writeup documenta el aprendizaje del Módulo 2 del curso "Automatizar Tareas de Seguridad Cibernética con Python" de Google en Coursera. Los ejemplos y ejercicios están diseñados para reforzar los conceptos aprendidos y pueden ser adaptados para casos de uso específicos.

**Última actualización:** Octubre 2024

---

⭐ Si este contenido te resultó útil, no olvides darle una estrella al repositorio!

**#Cybersecurity #Python #Automation #InfoSec #Programming**
