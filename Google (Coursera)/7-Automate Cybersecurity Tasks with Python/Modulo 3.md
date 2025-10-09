# 📘 Writeup: Automatizar Tareas de Seguridad Cibernética con Python

## Módulo 3: Trabajar con Cadenas y Listas

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![Coursera](https://img.shields.io/badge/Coursera-Google%20Cybersecurity-0056D2.svg)](https://www.coursera.org/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

---

## 📋 Tabla de Contenidos

- [Descripción General](#descripción-general)
- [Objetivos de Aprendizaje](#objetivos-de-aprendizaje)
- [Trabajar con Strings](#trabajar-con-strings)
- [Manipulación de Listas](#manipulación-de-listas)
- [Métodos y Operaciones](#métodos-y-operaciones)
- [Casos de Uso en Seguridad](#casos-de-uso-en-seguridad)
- [Ejercicios Prácticos](#ejercicios-prácticos)
- [Laboratorios](#laboratorios)
- [Recursos Adicionales](#recursos-adicionales)

---

## 🎯 Descripción General

Este módulo profundiza en el manejo de dos estructuras de datos fundamentales en Python: strings (cadenas de texto) y listas. Estas estructuras son esenciales para procesar logs, analizar datos de seguridad y automatizar tareas de ciberseguridad.

**Duración estimada:** 5-7 horas  
**Nivel:** Intermedio  
**Prerrequisitos:** Módulo 1 y 2 completados

---

## 🎓 Objetivos de Aprendizaje

Al completar este módulo, serás capaz de:

- ✅ Manipular y formatear strings para análisis de seguridad
- ✅ Aplicar métodos de strings para extraer información crítica
- ✅ Crear, modificar y recorrer listas de datos
- ✅ Utilizar slicing para acceder a segmentos de datos
- ✅ Implementar operaciones comunes en listas
- ✅ Combinar strings y listas para automatizar tareas
- ✅ Procesar logs y archivos de configuración
- ✅ Desarrollar scripts para análisis de amenazas

---

## 🔤 Trabajar con Strings

### 1. Fundamentos de Strings

Los strings son secuencias inmutables de caracteres, fundamentales para trabajar con logs y datos textuales.

```python
# Creación de strings
mensaje_alerta = "Intento de acceso no autorizado detectado"
ip_address = '192.168.1.100'
log_entry = """2024-10-09 15:30:45 - WARNING
Usuario: admin
Acción: Login fallido"""

# Concatenación
usuario = "admin"
mensaje = "Acceso denegado para usuario: " + usuario
print(mensaje)  # Acceso denegado para usuario: admin

# Formateo moderno (f-strings)
intentos = 5
alerta = f"Se detectaron {intentos} intentos fallidos de login"
print(alerta)
```

### 2. Métodos Principales de Strings

#### Búsqueda y Validación

```python
log = "ERROR: Failed authentication from 10.0.0.5"

# Buscar substring
if "ERROR" in log:
    print("Error detectado en el log")

# Verificar inicio/final
if log.startswith("ERROR"):
    print("Log de error encontrado")

if log.endswith("10.0.0.5"):
    print("Actividad desde IP sospechosa")

# Encontrar posición
posicion = log.find("authentication")
print(f"'authentication' encontrado en posición: {posicion}")

# Contar ocurrencias
cantidad = log.count("0")
print(f"El carácter '0' aparece {cantidad} veces")
```

#### Transformación de Texto

```python
usuario_input = "  ADMIN  "

# Cambiar mayúsculas/minúsculas
print(usuario_input.lower())    # "  admin  "
print(usuario_input.upper())    # "  ADMIN  "
print(usuario_input.title())    # "  Admin  "

# Eliminar espacios
print(usuario_input.strip())    # "ADMIN"
print(usuario_input.lstrip())   # "ADMIN  "
print(usuario_input.rstrip())   # "  ADMIN"

# Reemplazar texto
log = "User admin failed to login"
log_anonimizado = log.replace("admin", "***")
print(log_anonimizado)  # User *** failed to login
```

#### División y Unión

```python
# Dividir strings (split)
log_entry = "2024-10-09,15:30:45,ERROR,Login failed,192.168.1.100"
campos = log_entry.split(",")
print(campos)
# ['2024-10-09', '15:30:45', 'ERROR', 'Login failed', '192.168.1.100']

fecha = campos[0]
hora = campos[1]
nivel = campos[2]
mensaje = campos[3]
ip = campos[4]

# Dividir por líneas
logs_multiples = """ERROR: Login failed
WARNING: Suspicious activity
INFO: Session started"""

lineas = logs_multiples.split("\n")
for linea in lineas:
    print(f"Procesando: {linea}")

# Unir strings (join)
palabras = ["Intento", "de", "acceso", "no", "autorizado"]
mensaje_completo = " ".join(palabras)
print(mensaje_completo)  # Intento de acceso no autorizado

# Unir con separador
ips = ["192.168.1.1", "192.168.1.2", "192.168.1.3"]
lista_ips = ", ".join(ips)
print(f"IPs detectadas: {lista_ips}")
```

### 3. Indexación y Slicing de Strings

```python
dominio = "ejemplo.com"

# Acceso por índice
primer_caracter = dominio[0]      # 'e'
ultimo_caracter = dominio[-1]     # 'm'

# Slicing (rebanado)
extension = dominio[-3:]          # 'com'
nombre = dominio[:-4]             # 'ejemplo'
subdominio = dominio[0:7]         # 'ejemplo'

# Aplicación práctica: Extraer información de email
email = "usuario@empresa.com"
indice_arroba = email.index("@")
nombre_usuario = email[:indice_arroba]
dominio_email = email[indice_arroba+1:]

print(f"Usuario: {nombre_usuario}")    # Usuario: usuario
print(f"Dominio: {dominio_email}")     # Dominio: empresa.com
```

### 4. Validación de Strings

```python
def validar_formato_ip(ip):
    """Valida formato básico de una dirección IP"""
    partes = ip.split(".")
    
    if len(partes) != 4:
        return False
    
    for parte in partes:
        if not parte.isdigit():
            return False
        numero = int(parte)
        if numero < 0 or numero > 255:
            return False
    
    return True

# Pruebas
print(validar_formato_ip("192.168.1.1"))    # True
print(validar_formato_ip("256.1.1.1"))      # False
print(validar_formato_ip("192.168.1"))      # False
```

---

## 📝 Manipulación de Listas

### 1. Fundamentos de Listas

Las listas son colecciones ordenadas y mutables, ideales para almacenar múltiples elementos.

```python
# Crear listas
usuarios_bloqueados = ["user123", "admin_fake", "hacker01"]
puertos_abiertos = [22, 80, 443, 8080]
datos_mixtos = ["192.168.1.1", 5, True, "admin"]

# Lista vacía
alertas = []

# Lista de listas (matriz)
eventos = [
    ["2024-10-09", "ERROR", "Login failed"],
    ["2024-10-09", "WARNING", "Suspicious IP"],
    ["2024-10-09", "INFO", "Session started"]
]
```

### 2. Acceso y Modificación

```python
ips_sospechosas = ["10.0.0.5", "192.168.1.100", "172.16.0.50"]

# Acceso por índice
primera_ip = ips_sospechosas[0]      # "10.0.0.5"
ultima_ip = ips_sospechosas[-1]      # "172.16.0.50"

# Modificar elementos
ips_sospechosas[1] = "192.168.1.200"
print(ips_sospechosas)
# ['10.0.0.5', '192.168.1.200', '172.16.0.50']

# Slicing en listas
numeros_puerto = [20, 21, 22, 23, 80, 443, 8080]
puertos_ftp = numeros_puerto[0:3]    # [20, 21, 22]
puertos_web = numeros_puerto[4:6]    # [80, 443]
ultimos_tres = numeros_puerto[-3:]   # [443, 8080]
```

### 3. Métodos de Listas

#### Agregar Elementos

```python
amenazas = ["malware", "phishing"]

# Agregar al final
amenazas.append("ransomware")
print(amenazas)  # ['malware', 'phishing', 'ransomware']

# Agregar en posición específica
amenazas.insert(1, "virus")
print(amenazas)  # ['malware', 'virus', 'phishing', 'ransomware']

# Extender lista con otra lista
nuevas_amenazas = ["spyware", "trojan"]
amenazas.extend(nuevas_amenazas)
print(amenazas)
# ['malware', 'virus', 'phishing', 'ransomware', 'spyware', 'trojan']
```

#### Eliminar Elementos

```python
usuarios = ["admin", "user1", "guest", "user2", "guest"]

# Eliminar por valor (primera ocurrencia)
usuarios.remove("guest")
print(usuarios)  # ['admin', 'user1', 'user2', 'guest']

# Eliminar por índice y obtener valor
usuario_eliminado = usuarios.pop(2)
print(f"Usuario eliminado: {usuario_eliminado}")  # user2
print(usuarios)  # ['admin', 'user1', 'guest']

# Eliminar último elemento
ultimo = usuarios.pop()
print(usuarios)  # ['admin', 'user1']

# Vaciar lista
usuarios.clear()
print(usuarios)  # []
```

#### Buscar y Ordenar

```python
puertos = [80, 22, 443, 8080, 22, 3306]

# Buscar índice
indice = puertos.index(443)
print(f"Puerto 443 está en índice: {indice}")  # 2

# Contar ocurrencias
cantidad = puertos.count(22)
print(f"Puerto 22 aparece {cantidad} veces")  # 2

# Verificar existencia
if 3306 in puertos:
    print("Puerto MySQL detectado")

# Ordenar lista (modifica original)
puertos.sort()
print(puertos)  # [22, 22, 80, 443, 3306, 8080]

# Ordenar en reversa
puertos.sort(reverse=True)
print(puertos)  # [8080, 3306, 443, 80, 22, 22]

# Invertir orden
puertos.reverse()
print(puertos)  # [22, 22, 80, 443, 3306, 8080]

# Crear copia ordenada (no modifica original)
severidades = ["high", "low", "medium", "critical"]
severidades_ordenadas = sorted(severidades)
print(severidades)            # ['high', 'low', 'medium', 'critical']
print(severidades_ordenadas)  # ['critical', 'high', 'low', 'medium']
```

### 4. Operaciones Comunes

```python
# Longitud de lista
usuarios = ["admin", "user1", "user2"]
cantidad_usuarios = len(usuarios)
print(f"Total de usuarios: {cantidad_usuarios}")  # 3

# Concatenar listas
lista1 = [1, 2, 3]
lista2 = [4, 5, 6]
lista_completa = lista1 + lista2
print(lista_completa)  # [1, 2, 3, 4, 5, 6]

# Repetir lista
patron = ["red", "yellow"]
secuencia = patron * 3
print(secuencia)  # ['red', 'yellow', 'red', 'yellow', 'red', 'yellow']

# Mínimo y máximo
intentos = [3, 7, 2, 9, 1, 5]
print(f"Mínimo: {min(intentos)}")  # 1
print(f"Máximo: {max(intentos)}")  # 9
print(f"Suma: {sum(intentos)}")    # 27
```

### 5. Iterar sobre Listas

```python
ips_bloqueadas = ["10.0.0.5", "192.168.1.100", "172.16.0.50"]

# Iteración básica
for ip in ips_bloqueadas:
    print(f"IP bloqueada: {ip}")

# Iteración con índice
for i in range(len(ips_bloqueadas)):
    print(f"Posición {i}: {ips_bloqueadas[i]}")

# Iteración con enumerate
for indice, ip in enumerate(ips_bloqueadas):
    print(f"#{indice + 1}: {ip}")

# Iteración con múltiples listas
usuarios = ["admin", "user1", "user2"]
estados = ["activo", "inactivo", "activo"]

for usuario, estado in zip(usuarios, estados):
    print(f"Usuario {usuario} está {estado}")
```

---

## 🔧 Métodos y Operaciones Avanzadas

### 1. List Comprehensions

Forma concisa de crear listas basadas en listas existentes.

```python
# Sintaxis básica: [expresión for elemento in iterable if condición]

# Ejemplo: Filtrar puertos comunes
todos_los_puertos = [20, 21, 22, 23, 80, 443, 3389, 8080, 9000]
puertos_seguros = [puerto for puerto in todos_los_puertos if puerto > 1000]
print(puertos_seguros)  # [3389, 8080, 9000]

# Transformar datos
usuarios = ["admin", "user1", "guest"]
usuarios_upper = [usuario.upper() for usuario in usuarios]
print(usuarios_upper)  # ['ADMIN', 'USER1', 'GUEST']

# Extraer información de logs
logs = [
    "ERROR: Login failed from 10.0.0.5",
    "INFO: Session started",
    "ERROR: Connection timeout",
    "WARNING: Suspicious activity"
]

errores = [log for log in logs if "ERROR" in log]
print(f"Errores encontrados: {len(errores)}")
```

### 2. Trabajar con Strings y Listas Juntos

```python
# Analizar archivo de configuración
config_texto = """firewall=enabled
ssh_port=22
timeout=300
max_connections=100"""

# Convertir a lista de líneas
lineas = config_texto.split("\n")

# Crear diccionario de configuración
configuracion = {}
for linea in lineas:
    clave, valor = linea.split("=")
    configuracion[clave] = valor

print(configuracion)
# {'firewall': 'enabled', 'ssh_port': '22', 'timeout': '300', 'max_connections': '100'}

# Procesar lista de emails
emails = ["admin@empresa.com", "user@ejemplo.com", "soporte@empresa.com"]
dominios = [email.split("@")[1] for email in emails]
print(dominios)  # ['empresa.com', 'ejemplo.com', 'empresa.com']

# Contar dominios únicos
dominios_unicos = list(set(dominios))
print(f"Dominios únicos: {dominios_unicos}")
```

---

## 🛡️ Casos de Uso en Seguridad

### 1. Análisis de Logs de Firewall

```python
def analizar_log_firewall(log_texto):
    """
    Analiza logs de firewall y extrae información relevante.
    """
    lineas = log_texto.strip().split("\n")
    estadisticas = {
        "permitidos": 0,
        "bloqueados": 0,
        "ips_bloqueadas": []
    }
    
    for linea in lineas:
        if "ACCEPT" in linea:
            estadisticas["permitidos"] += 1
        elif "DROP" in linea or "REJECT" in linea:
            estadisticas["bloqueados"] += 1
            # Extraer IP
            partes = linea.split()
            for parte in partes:
                if "SRC=" in parte:
                    ip = parte.split("=")[1]
                    estadisticas["ips_bloqueadas"].append(ip)
    
    return estadisticas

# Ejemplo de uso
log_firewall = """
Oct 09 10:15:32 firewall kernel: DROP SRC=192.168.1.100 DST=10.0.0.1
Oct 09 10:15:45 firewall kernel: ACCEPT SRC=192.168.1.50 DST=10.0.0.1
Oct 09 10:16:12 firewall kernel: DROP SRC=172.16.0.20 DST=10.0.0.1
"""

resultado = analizar_log_firewall(log_firewall)
print(f"Conexiones permitidas: {resultado['permitidos']}")
print(f"Conexiones bloqueadas: {resultado['bloqueados']}")
print(f"IPs bloqueadas: {resultado['ips_bloqueadas']}")
```

### 2. Validación de Lista de Usuarios

```python
def validar_usuarios(usuarios_archivo, usuarios_autorizados):
    """
    Valida que los usuarios en el sistema estén autorizados.
    """
    usuarios_sistema = usuarios_archivo.strip().split("\n")
    usuarios_no_autorizados = []
    
    for usuario in usuarios_sistema:
        usuario_limpio = usuario.strip()
        if usuario_limpio not in usuarios_autorizados:
            usuarios_no_autorizados.append(usuario_limpio)
    
    return usuarios_no_autorizados

# Uso
usuarios_en_sistema = """
admin
user1
guest
root
user2
"""

usuarios_validos = ["admin", "user1", "user2"]

no_autorizados = validar_usuarios(usuarios_en_sistema, usuarios_validos)

if no_autorizados:
    print("⚠️ ALERTA: Usuarios no autorizados detectados:")
    for usuario in no_autorizados:
        print(f"  - {usuario}")
else:
    print("✅ Todos los usuarios están autorizados")
```

### 3. Extractor de Direcciones IP

```python
def extraer_ips(texto):
    """
    Extrae todas las direcciones IP de un texto.
    """
    ips_encontradas = []
    palabras = texto.split()
    
    for palabra in palabras:
        # Limpiar caracteres extra
        palabra_limpia = palabra.strip(",:;()")
        
        # Verificar formato IP básico
        if palabra_limpia.count(".") == 3:
            partes = palabra_limpia.split(".")
            es_ip = True
            
            for parte in partes:
                if not parte.isdigit():
                    es_ip = False
                    break
                if int(parte) < 0 or int(parte) > 255:
                    es_ip = False
                    break
            
            if es_ip and palabra_limpia not in ips_encontradas:
                ips_encontradas.append(palabra_limpia)
    
    return ips_encontradas

# Ejemplo
log_texto = """
Se detectaron conexiones desde 192.168.1.100 y 10.0.0.5
El servidor 172.16.0.10 respondió correctamente
Conexión fallida desde 192.168.1.100 (duplicado)
"""

ips = extraer_ips(log_texto)
print(f"IPs únicas: {len(resultado['ips_unicas'])}")
print(f"Rutas más accedidas: {resultado['rutas_mas_accedidas']}")
```

### Ejercicio 4: Gestor de Lista de Permitidos/Bloqueados

```python
def gestionar_listas_acceso(comando, elemento, lista_permitidos, lista_bloqueados):
    """
    Gestiona listas de control de acceso.
    
    Comandos: 'permitir', 'bloquear', 'eliminar', 'verificar'
    """
    resultado = {
        "exito": False,
        "mensaje": "",
        "lista_permitidos": lista_permitidos.copy(),
        "lista_bloqueados": lista_bloqueados.copy()
    }
    
    elemento = elemento.strip().lower()
    
    if comando == "permitir":
        if elemento in resultado["lista_bloqueados"]:
            resultado["lista_bloqueados"].remove(elemento)
            resultado["mensaje"] = f"Elemento {elemento} removido de bloqueados"
        
        if elemento not in resultado["lista_permitidos"]:
            resultado["lista_permitidos"].append(elemento)
            resultado["mensaje"] += f" y agregado a permitidos"
            resultado["exito"] = True
        else:
            resultado["mensaje"] = f"Elemento {elemento} ya está en permitidos"
    
    elif comando == "bloquear":
        if elemento in resultado["lista_permitidos"]:
            resultado["lista_permitidos"].remove(elemento)
            resultado["mensaje"] = f"Elemento {elemento} removido de permitidos"
        
        if elemento not in resultado["lista_bloqueados"]:
            resultado["lista_bloqueados"].append(elemento)
            resultado["mensaje"] += f" y agregado a bloqueados"
            resultado["exito"] = True
        else:
            resultado["mensaje"] = f"Elemento {elemento} ya está en bloqueados"
    
    elif comando == "eliminar":
        eliminado = False
        if elemento in resultado["lista_permitidos"]:
            resultado["lista_permitidos"].remove(elemento)
            eliminado = True
        if elemento in resultado["lista_bloqueados"]:
            resultado["lista_bloqueados"].remove(elemento)
            eliminado = True
        
        if eliminado:
            resultado["exito"] = True
            resultado["mensaje"] = f"Elemento {elemento} eliminado de todas las listas"
        else:
            resultado["mensaje"] = f"Elemento {elemento} no encontrado en ninguna lista"
    
    elif comando == "verificar":
        if elemento in resultado["lista_permitidos"]:
            resultado["mensaje"] = f"✅ {elemento} está PERMITIDO"
            resultado["exito"] = True
        elif elemento in resultado["lista_bloqueados"]:
            resultado["mensaje"] = f"❌ {elemento} está BLOQUEADO"
            resultado["exito"] = False
        else:
            resultado["mensaje"] = f"⚠️ {elemento} no está en ninguna lista"
    
    return resultado

# Simulación de uso
permitidos = ["192.168.1.10", "192.168.1.20"]
bloqueados = ["10.0.0.5", "172.16.0.100"]

print("=== Sistema de Control de Acceso ===\n")

# Verificar IP
resultado = gestionar_listas_acceso("verificar", "192.168.1.10", permitidos, bloqueados)
print(resultado["mensaje"])

# Bloquear IP permitida
resultado = gestionar_listas_acceso("bloquear", "192.168.1.10", permitidos, bloqueados)
print(resultado["mensaje"])
permitidos = resultado["lista_permitidos"]
bloqueados = resultado["lista_bloqueados"]

# Verificar nuevamente
resultado = gestionar_listas_acceso("verificar", "192.168.1.10", permitidos, bloqueados)
print(resultado["mensaje"])
```

---

## 🧪 Laboratorios

### Laboratorio 1: Procesador de Archivos de Configuración

**Objetivo:** Leer y procesar un archivo de configuración de seguridad.

```python
def procesar_configuracion_seguridad(config_texto):
    """
    Procesa archivo de configuración y valida parámetros de seguridad.
    """
    lineas = config_texto.strip().split("\n")
    configuracion = {}
    advertencias = []
    
    for numero_linea, linea in enumerate(lineas, 1):
        # Ignorar comentarios y líneas vacías
        linea = linea.strip()
        if not linea or linea.startswith("#"):
            continue
        
        # Procesar línea de configuración
        if "=" in linea:
            clave, valor = linea.split("=", 1)
            clave = clave.strip()
            valor = valor.strip()
            configuracion[clave] = valor
        else:
            advertencias.append(f"Línea {numero_linea}: Formato inválido")
    
    # Validar configuraciones críticas
    validaciones = {
        "ssh_port": lambda v: v != "22",
        "password_min_length": lambda v: int(v) >= 12,
        "session_timeout": lambda v: int(v) <= 1800,
        "encryption_enabled": lambda v: v.lower() == "true",
        "firewall_enabled": lambda v: v.lower() == "true"
    }
    
    problemas_seguridad = []
    
    for parametro, validacion in validaciones.items():
        if parametro not in configuracion:
            problemas_seguridad.append(f"Parámetro '{parametro}' no configurado")
        else:
            try:
                if not validacion(configuracion[parametro]):
                    problemas_seguridad.append(
                        f"Parámetro '{parametro}' no cumple con política de seguridad"
                    )
            except (ValueError, AttributeError):
                problemas_seguridad.append(
                    f"Valor inválido para '{parametro}': {configuracion[parametro]}"
                )
    
    return {
        "configuracion": configuracion,
        "advertencias": advertencias,
        "problemas_seguridad": problemas_seguridad,
        "es_seguro": len(problemas_seguridad) == 0
    }

# Archivo de configuración de ejemplo
config_ejemplo = """
# Configuración de Seguridad del Sistema
ssh_port=2222
password_min_length=14
session_timeout=1200
encryption_enabled=true
firewall_enabled=true
max_login_attempts=3
backup_enabled=true
# Fin de configuración
"""

resultado = procesar_configuracion_seguridad(config_ejemplo)

print("📋 Configuración procesada:")
for clave, valor in resultado["configuracion"].items():
    print(f"  {clave}: {valor}")

if resultado["advertencias"]:
    print("\n⚠️ Advertencias:")
    for adv in resultado["advertencias"]:
        print(f"  - {adv}")

if resultado["problemas_seguridad"]:
    print("\n🚨 Problemas de seguridad:")
    for prob in resultado["problemas_seguridad"]:
        print(f"  - {prob}")
else:
    print("\n✅ Configuración cumple con políticas de seguridad")
```

### Laboratorio 2: Detector de Patrones Maliciosos

**Objetivo:** Identificar patrones de ataque en cadenas de texto.

```python
def detectar_patrones_ataque(entrada):
    """
    Detecta patrones comunes de ataques de seguridad.
    """
    patrones_maliciosos = {
        "sql_injection": ["'", "OR 1=1", "DROP TABLE", "UNION SELECT", "--", "/*"],
        "xss": ["<script>", "javascript:", "onerror=", "onload=", "<iframe>"],
        "command_injection": [";", "&&", "||", "|", "`", "$("],
        "path_traversal": ["../", "..\\", "%2e%2e", "....//"],
        "ldap_injection": ["*", "(", ")", "&", "|"]
    }
    
    entrada_lower = entrada.lower()
    amenazas_detectadas = []
    
    for tipo_ataque, patrones in patrones_maliciosos.items():
        for patron in patrones:
            if patron.lower() in entrada_lower:
                amenazas_detectadas.append({
                    "tipo": tipo_ataque,
                    "patron": patron,
                    "posicion": entrada_lower.find(patron.lower())
                })
    
    return {
        "entrada": entrada,
        "es_malicioso": len(amenazas_detectadas) > 0,
        "amenazas": amenazas_detectadas,
        "nivel_riesgo": "ALTO" if len(amenazas_detectadas) > 2 else 
                        "MEDIO" if len(amenazas_detectadas) > 0 else "BAJO"
    }

# Casos de prueba
casos_prueba = [
    "admin",
    "' OR '1'='1",
    "<script>alert('XSS')</script>",
    "../../../etc/passwd",
    "normal_input_123",
    "user@email.com",
    "SELECT * FROM users WHERE id=1; DROP TABLE users--"
]

print("🔍 Detector de Patrones Maliciosos\n")

for caso in casos_prueba:
    resultado = detectar_patrones_ataque(caso)
    print(f"Entrada: {caso[:50]}...")
    print(f"Riesgo: {resultado['nivel_riesgo']}")
    
    if resultado["amenazas"]:
        print("Amenazas detectadas:")
        for amenaza in resultado["amenazas"]:
            print(f"  - {amenaza['tipo']}: '{amenaza['patron']}' en posición {amenaza['posicion']}")
    else:
        print("✅ No se detectaron amenazas")
    print()
```

### Laboratorio 3: Analizador de Headers HTTP

**Objetivo:** Analizar headers HTTP para detectar problemas de seguridad.

```python
def analizar_headers_seguridad(headers_texto):
    """
    Analiza headers HTTP y verifica presencia de headers de seguridad.
    """
    # Convertir texto a diccionario
    headers = {}
    lineas = headers_texto.strip().split("\n")
    
    for linea in lineas:
        if ":" in linea:
            nombre, valor = linea.split(":", 1)
            headers[nombre.strip().lower()] = valor.strip()
    
    # Headers de seguridad recomendados
    headers_seguridad = {
        "strict-transport-security": "Fuerza conexiones HTTPS",
        "x-frame-options": "Previene clickjacking",
        "x-content-type-options": "Previene MIME sniffing",
        "content-security-policy": "Controla recursos permitidos",
        "x-xss-protection": "Protección contra XSS",
        "referrer-policy": "Controla información de referencia"
    }
    
    resultados = {
        "headers_presentes": [],
        "headers_faltantes": [],
        "headers_inseguros": [],
        "puntuacion_seguridad": 0
    }
    
    # Verificar headers de seguridad
    for header, descripcion in headers_seguridad.items():
        if header in headers:
            resultados["headers_presentes"].append({
                "nombre": header,
                "valor": headers[header],
                "descripcion": descripcion
            })
            resultados["puntuacion_seguridad"] += 1
        else:
            resultados["headers_faltantes"].append({
                "nombre": header,
                "descripcion": descripcion
            })
    
    # Detectar headers potencialmente inseguros
    headers_problematicos = {
        "server": "Revela información del servidor",
        "x-powered-by": "Revela tecnología utilizada"
    }
    
    for header, razon in headers_problematicos.items():
        if header in headers:
            resultados["headers_inseguros"].append({
                "nombre": header,
                "valor": headers[header],
                "razon": razon
            })
            resultados["puntuacion_seguridad"] -= 0.5
    
    # Calcular porcentaje
    total_headers = len(headers_seguridad)
    porcentaje = (resultados["puntuacion_seguridad"] / total_headers) * 100
    resultados["porcentaje_seguridad"] = max(0, porcentaje)
    
    return resultados

# Ejemplo de headers HTTP
headers_ejemplo = """
Content-Type: text/html; charset=UTF-8
Server: Apache/2.4.41
X-Powered-By: PHP/7.4.3
Strict-Transport-Security: max-age=31536000
X-Frame-Options: DENY
X-Content-Type-Options: nosniff
"""

analisis = analizar_headers_seguridad(headers_ejemplo)

print("🔒 Análisis de Headers de Seguridad HTTP\n")
print(f"Puntuación de seguridad: {analisis['porcentaje_seguridad']:.1f}%\n")

if analisis["headers_presentes"]:
    print("✅ Headers de seguridad presentes:")
    for header in analisis["headers_presentes"]:
        print(f"  • {header['nombre']}: {header['descripcion']}")
        print(f"    Valor: {header['valor']}")

if analisis["headers_faltantes"]:
    print("\n⚠️ Headers de seguridad faltantes:")
    for header in analisis["headers_faltantes"]:
        print(f"  • {header['nombre']}: {header['descripcion']}")

if analisis["headers_inseguros"]:
    print("\n🚨 Headers que revelan información sensible:")
    for header in analisis["headers_inseguros"]:
        print(f"  • {header['nombre']}: {header['razon']}")
        print(f"    Valor: {header['valor']}")
```

---

## 📊 Proyecto Final: Sistema de Monitoreo de Seguridad

Integra todos los conceptos aprendidos en un sistema completo.

```python
class MonitorSeguridad:
    """
    Sistema integral de monitoreo de seguridad.
    """
    
    def __init__(self):
        self.ips_bloqueadas = []
        self.usuarios_bloqueados = []
        self.intentos_fallidos = {}
        self.max_intentos = 5
        self.alertas = []
    
    def registrar_intento_login(self, usuario, ip, exitoso):
        """Registra un intento de login."""
        clave = f"{usuario}@{ip}"
        
        if exitoso:
            # Resetear intentos fallidos si login exitoso
            if clave in self.intentos_fallidos:
                del self.intentos_fallidos[clave]
            return {"bloqueado": False, "mensaje": "Login exitoso"}
        
        # Incrementar intentos fallidos
        if clave not in self.intentos_fallidos:
            self.intentos_fallidos[clave] = 0
        
        self.intentos_fallidos[clave] += 1
        intentos = self.intentos_fallidos[clave]
        
        # Verificar si se debe bloquear
        if intentos >= self.max_intentos:
            self.bloquear_usuario(usuario)
            self.bloquear_ip(ip)
            self.crear_alerta(
                "CRITICO",
                f"Usuario {usuario} bloqueado tras {intentos} intentos desde {ip}"
            )
            return {
                "bloqueado": True,
                "mensaje": f"Usuario y IP bloqueados tras {intentos} intentos"
            }
        
        return {
            "bloqueado": False,
            "mensaje": f"Intento fallido {intentos}/{self.max_intentos}"
        }
    
    def bloquear_ip(self, ip):
        """Agrega IP a lista de bloqueados."""
        if ip not in self.ips_bloqueadas:
            self.ips_bloqueadas.append(ip)
    
    def bloquear_usuario(self, usuario):
        """Agrega usuario a lista de bloqueados."""
        if usuario not in self.usuarios_bloqueados:
            self.usuarios_bloqueados.append(usuario)
    
    def verificar_acceso(self, usuario, ip):
        """Verifica si usuario/IP tienen acceso permitido."""
        if usuario in self.usuarios_bloqueados:
            return {"permitido": False, "razon": "Usuario bloqueado"}
        
        if ip in self.ips_bloqueadas:
            return {"permitido": False, "razon": "IP bloqueada"}
        
        return {"permitido": True, "razon": "Acceso autorizado"}
    
    def crear_alerta(self, nivel, mensaje):
        """Crea una alerta de seguridad."""
        from datetime import datetime
        alerta = {
            "timestamp": datetime.now().strftime("%Y-%m-%d %H:%M:%S"),
            "nivel": nivel,
            "mensaje": mensaje
        }
        self.alertas.append(alerta)
    
    def generar_reporte(self):
        """Genera reporte de seguridad."""
        reporte = []
        reporte.append("=" * 50)
        reporte.append("REPORTE DE SEGURIDAD")
        reporte.append("=" * 50)
        reporte.append(f"\nIPs Bloqueadas ({len(self.ips_bloqueadas)}):")
        for ip in self.ips_bloqueadas:
            reporte.append(f"  • {ip}")
        
        reporte.append(f"\nUsuarios Bloqueados ({len(self.usuarios_bloqueados)}):")
        for usuario in self.usuarios_bloqueados:
            reporte.append(f"  • {usuario}")
        
        reporte.append(f"\nIntentos Fallidos Activos ({len(self.intentos_fallidos)}):")
        for clave, intentos in self.intentos_fallidos.items():
            reporte.append(f"  • {clave}: {intentos} intentos")
        
        reporte.append(f"\nAlertas Recientes ({len(self.alertas)}):")
        for alerta in self.alertas[-5:]:  # Últimas 5 alertas
            reporte.append(f"  [{alerta['timestamp']}] {alerta['nivel']}: {alerta['mensaje']}")
        
        return "\n".join(reporte)

# Simulación del sistema
print("🛡️ Sistema de Monitoreo de Seguridad\n")

monitor = MonitorSeguridad()

# Simular eventos
eventos = [
    ("usuario1", "192.168.1.10", True),
    ("admin", "10.0.0.5", False),
    ("admin", "10.0.0.5", False),
    ("admin", "10.0.0.5", False),
    ("admin", "10.0.0.5", False),
    ("admin", "10.0.0.5", False),  # Este será bloqueado
    ("usuario2", "192.168.1.20", True),
]

for usuario, ip, exitoso in eventos:
    resultado = monitor.registrar_intento_login(usuario, ip, exitoso)
    estado = "✅ EXITOSO" if exitoso else "❌ FALLIDO"
    print(f"{estado} - {usuario} desde {ip}: {resultado['mensaje']}")

print("\n" + monitor.generar_reporte())
```

---

## 🎯 Resumen de Conceptos Clave

### Strings
- Inmutables y secuenciales
- Métodos: `split()`, `join()`, `replace()`, `strip()`, `find()`, `startswith()`, `endswith()`
- Formateo: f-strings, `format()`, concatenación
- Slicing y indexación

### Listas
- Mutables y ordenadas
- Métodos: `append()`, `insert()`, `remove()`, `pop()`, `sort()`, `reverse()`
- Operaciones: concatenación, repetición, `len()`, `min()`, `max()`, `sum()`
- List comprehensions para creación eficiente

### Aplicaciones en Seguridad
- Análisis de logs
- Procesamiento de listas de control de acceso
- Validación de datos de entrada
- Extracción de patrones
- Automatización de tareas repetitivas

---

## 📚 Recursos Adicionales

### Documentación Oficial
- [Python String Methods](https://docs.python.org/3/library/stdtypes.html#string-methods)
- [Python List Methods](https://docs.python.org/3/tutorial/datastructures.html)
- [Python Regular Expressions](https://docs.python.org/3/library/re.html)

### Tutoriales Recomendados
- Real Python - Working with Strings
- Python for Beginners - Lists and Strings
- Automate the Boring Stuff with Python

### Herramientas Útiles
- **RegEx101**: Para probar expresiones regulares
- **Python Tutor**: Visualizar ejecución de código
- **IPython**: Shell interactivo mejorado

### Lecturas Complementarias
- "Python Crash Course" por Eric Matthes
- "Effective Python" por Brett Slatkin
- "Fluent Python" por Luciano Ramalho

---

## ✅ Checklist de Competencias

Antes de avanzar al siguiente módulo, asegúrate de poder:

- [ ] Manipular strings usando métodos comunes
- [ ] Dividir y unir cadenas de texto
- [ ] Usar slicing en strings y listas
- [ ] Crear y modificar listas
- [ ] Iterar sobre listas con diferentes métodos
- [ ] Aplicar list comprehensions
- [ ] Combinar strings y listas en soluciones prácticas
- [ ] Procesar archivos de logs básicos
- [ ] Validar y sanitizar datos de entrada
- [ ] Crear funciones que manipulen strings y listas

---

## 🤝 Contacto y Contribuciones

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/6b99b440-500a-4863-92bf-0ae93d726ec2" />


---

## 📄 Licencia

Este proyecto está bajo la Licencia MIT. Ver el archivo `LICENSE` para más detalles.

---

## 🙏 Agradecimientos

- Google Cybersecurity Professional Certificate
- Coursera Platform
- Comunidad de Python en Ciberseguridad

---

**Última actualización:** Octubre 2024

⭐ Si este writeup te fue útil, considera darle una estrella al repositorio!

**#Cybersecurity #Python #Strings #Lists #Automation #InfoSec** encontradas: {ips}")
```

### 4. Procesador de Reglas de Firewall

```python
def procesar_reglas_firewall(reglas_texto):
    """
    Procesa y organiza reglas de firewall.
    """
    lineas = reglas_texto.strip().split("\n")
    reglas = {
        "permitir": [],
        "denegar": [],
        "total": 0
    }
    
    for linea in lineas:
        if not linea.strip() or linea.startswith("#"):
            continue
            
        reglas["total"] += 1
        partes = linea.split()
        
        if len(partes) >= 3:
            accion = partes[0].lower()
            protocolo = partes[1]
            puerto = partes[2]
            
            regla_info = f"{protocolo}:{puerto}"
            
            if accion == "allow":
                reglas["permitir"].append(regla_info)
            elif accion == "deny":
                reglas["denegar"].append(regla_info)
    
    return reglas

# Uso
reglas_config = """
# Reglas de firewall
allow tcp 80
allow tcp 443
deny tcp 23
allow udp 53
deny tcp 3389
"""

reglas_procesadas = procesar_reglas_firewall(reglas_config)
print(f"Total de reglas: {reglas_procesadas['total']}")
print(f"Permitir: {reglas_procesadas['permitir']}")
print(f"Denegar: {reglas_procesadas['denegar']}")
```

---

## 💻 Ejercicios Prácticos

### Ejercicio 1: Analizador de Passwords

```python
def analizar_fortaleza_password(password):
    """
    Analiza la fortaleza de una contraseña.
    
    Retorna diccionario con análisis completo.
    """
    analisis = {
        "longitud": len(password),
        "tiene_mayuscula": False,
        "tiene_minuscula": False,
        "tiene_numero": False,
        "tiene_especial": False,
        "puntuacion": 0
    }
    
    caracteres_especiales = "!@#$%^&*()_+-=[]{}|;:,.<>?"
    
    for caracter in password:
        if caracter.isupper():
            analisis["tiene_mayuscula"] = True
        elif caracter.islower():
            analisis["tiene_minuscula"] = True
        elif caracter.isdigit():
            analisis["tiene_numero"] = True
        elif caracter in caracteres_especiales:
            analisis["tiene_especial"] = True
    
    # Calcular puntuación
    if analisis["longitud"] >= 8:
        analisis["puntuacion"] += 2
    if analisis["longitud"] >= 12:
        analisis["puntuacion"] += 1
    if analisis["tiene_mayuscula"]:
        analisis["puntuacion"] += 1
    if analisis["tiene_minuscula"]:
        analisis["puntuacion"] += 1
    if analisis["tiene_numero"]:
        analisis["puntuacion"] += 1
    if analisis["tiene_especial"]:
        analisis["puntuacion"] += 2
    
    # Determinar nivel
    if analisis["puntuacion"] >= 7:
        analisis["nivel"] = "Fuerte"
    elif analisis["puntuacion"] >= 5:
        analisis["nivel"] = "Media"
    else:
        analisis["nivel"] = "Débil"
    
    return analisis

# Pruebas
passwords = ["admin123", "P@ssw0rd!", "Contrasena_Segura_2024!"]

for pwd in passwords:
    resultado = analizar_fortaleza_password(pwd)
    print(f"\nPassword: {pwd}")
    print(f"Nivel: {resultado['nivel']}")
    print(f"Puntuación: {resultado['puntuacion']}/8")
```

### Ejercicio 2: Filtro de Emails Sospechosos

```python
def detectar_emails_sospechosos(lista_emails):
    """
    Detecta emails potencialmente maliciosos.
    """
    dominios_sospechosos = ["spam.com", "fake-bank.com", "malware.net"]
    palabras_sospechosas = ["urgent", "verify", "suspended", "click", "winner"]
    
    resultados = {
        "seguros": [],
        "sospechosos": [],
        "razones": {}
    }
    
    for email in lista_emails:
        email_lower = email.lower()
        es_sospechoso = False
        razones = []
        
        # Verificar dominio
        if "@" in email:
            dominio = email.split("@")[1]
            if dominio in dominios_sospechosos:
                es_sospechoso = True
                razones.append(f"Dominio sospechoso: {dominio}")
        
        # Verificar palabras sospechosas
        for palabra in palabras_sospechosas:
            if palabra in email_lower:
                es_sospechoso = True
                razones.append(f"Palabra sospechosa: {palabra}")
        
        # Verificar caracteres extraños
        if email.count("@") != 1:
            es_sospechoso = True
            razones.append("Formato de email inválido")
        
        if es_sospechoso:
            resultados["sospechosos"].append(email)
            resultados["razones"][email] = razones
        else:
            resultados["seguros"].append(email)
    
    return resultados

# Prueba
emails = [
    "usuario@empresa.com",
    "urgent@spam.com",
    "verify@fake-bank.com",
    "info@ejemplo.com",
    "winner@malware.net"
]

analisis = detectar_emails_sospechosos(emails)

print("📧 Emails seguros:")
for email in analisis["seguros"]:
    print(f"  ✅ {email}")

print("\n⚠️ Emails sospechosos:")
for email in analisis["sospechosos"]:
    print(f"  ❌ {email}")
    print(f"     Razones: {', '.join(analisis['razones'][email])}")
```

### Ejercicio 3: Parser de Access Logs

```python
def parsear_access_log(log_linea):
    """
    Extrae información de una línea de access log.
    """
    # Formato típico: IP - - [timestamp] "METHOD /path HTTP/1.1" status size
    
    partes = log_linea.split()
    
    if len(partes) < 7:
        return None
    
    info = {
        "ip": partes[0],
        "timestamp": partes[3].strip("[") + " " + partes[4].strip("]"),
        "metodo": partes[5].strip('"'),
        "ruta": partes[6],
        "codigo_estado": partes[8],
        "tamano": partes[9] if len(partes) > 9 else "-"
    }
    
    return info

def analizar_access_logs(logs_texto):
    """
    Analiza múltiples líneas de access logs.
    """
    lineas = logs_texto.strip().split("\n")
    estadisticas = {
        "total_requests": 0,
        "errores_4xx": 0,
        "errores_5xx": 0,
        "exitosos": 0,
        "ips_unicas": [],
        "rutas_mas_accedidas": {}
    }
    
    for linea in lineas:
        info = parsear_access_log(linea)
        if not info:
            continue
        
        estadisticas["total_requests"] += 1
        
        # Analizar código de estado
        codigo = int(info["codigo_estado"])
        if 200 <= codigo < 300:
            estadisticas["exitosos"] += 1
        elif 400 <= codigo < 500:
            estadisticas["errores_4xx"] += 1
        elif 500 <= codigo < 600:
            estadisticas["errores_5xx"] += 1
        
        # Registrar IP única
        if info["ip"] not in estadisticas["ips_unicas"]:
            estadisticas["ips_unicas"].append(info["ip"])
        
        # Contar accesos por ruta
        ruta = info["ruta"]
        if ruta in estadisticas["rutas_mas_accedidas"]:
            estadisticas["rutas_mas_accedidas"][ruta] += 1
        else:
            estadisticas["rutas_mas_accedidas"][ruta] = 1
    
    return estadisticas

# Ejemplo de uso
logs = """
192.168.1.10 - - [09/Oct/2024:10:15:23 +0000] "GET /index.html HTTP/1.1" 200 1234
10.0.0.5 - - [09/Oct/2024:10:16:45 +0000] "GET /admin HTTP/1.1" 403 567
192.168.1.10 - - [09/Oct/2024:10:17:12 +0000] "POST /login HTTP/1.1" 200 890
172.16.0.20 - - [09/Oct/2024:10:18:33 +0000] "GET /api/data HTTP/1.1" 500 234
"""

resultado = analizar_access_logs(logs)
print(f"📊 Estadísticas de Access Logs:")
print(f"Total de requests: {resultado['total_requests']}")
print(f"Requests exitosos: {resultado['exitosos']}")
print(f"Errores 4xx: {resultado['errores_4xx']}")
print(f"Errores 5xx: {resultado['errores_5xx']}")
print(f"IPs únicas
