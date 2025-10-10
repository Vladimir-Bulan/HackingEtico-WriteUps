
# 📘 Writeup: Automatizar Tareas de Seguridad Cibernética con Python

## Módulo 4: Python en la Práctica

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![Coursera](https://img.shields.io/badge/Coursera-Google%20Cybersecurity-0056D2.svg)](https://www.coursera.org/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

---

## 📋 Tabla de Contenidos

- [Descripción General](#descripción-general)
- [Objetivos de Aprendizaje](#objetivos-de-aprendizaje)
- [Trabajar con Archivos](#trabajar-con-archivos)
- [Manejo de Excepciones](#manejo-de-excepciones)
- [Depuración de Código](#depuración-de-código)
- [Módulos y Librerías](#módulos-y-librerías)
- [Proyectos Prácticos](#proyectos-prácticos)
- [Mejores Prácticas](#mejores-prácticas)
- [Recursos Adicionales](#recursos-adicionales)

---

## 🎯 Descripción General

Este módulo final integra todos los conceptos aprendidos y se enfoca en aplicaciones prácticas de Python en ciberseguridad. Aprenderás a trabajar con archivos, manejar errores, depurar código y utilizar módulos especializados para automatizar tareas de seguridad reales.

**Duración estimada:** 6-8 horas  
**Nivel:** Intermedio-Avanzado  
**Prerrequisitos:** Módulos 1, 2 y 3 completados

---

## 🎓 Objetivos de Aprendizaje

Al completar este módulo, serás capaz de:

- ✅ Leer y escribir archivos de forma segura
- ✅ Procesar archivos CSV, JSON y TXT
- ✅ Implementar manejo robusto de excepciones
- ✅ Depurar y solucionar errores en código Python
- ✅ Utilizar módulos estándar de Python
- ✅ Importar y usar librerías externas
- ✅ Desarrollar scripts de automatización completos
- ✅ Aplicar mejores prácticas de programación
- ✅ Crear herramientas de seguridad funcionales

---

## 📁 Trabajar con Archivos

### 1. Fundamentos de Archivos

Python proporciona funciones integradas para trabajar con archivos del sistema.

```python
# Abrir y cerrar archivos - Método tradicional
archivo = open("logs.txt", "r")
contenido = archivo.read()
archivo.close()

# Método recomendado: Context Manager (with)
with open("logs.txt", "r") as archivo:
    contenido = archivo.read()
# El archivo se cierra automáticamente
```

### 2. Modos de Apertura de Archivos

```python
# Modos principales:
# "r"  - Lectura (read) - archivo debe existir
# "w"  - Escritura (write) - sobrescribe archivo
# "a"  - Anexar (append) - agrega al final
# "x"  - Crear (exclusive) - error si existe
# "r+" - Lectura y escritura
# "b"  - Modo binario (rb, wb, etc.)

# Ejemplos prácticos

# Lectura
with open("security_log.txt", "r") as archivo:
    contenido = archivo.read()
    print(contenido)

# Escritura (sobrescribe)
with open("reporte.txt", "w") as archivo:
    archivo.write("Reporte de Seguridad\n")
    archivo.write("=" * 50 + "\n")

# Anexar (no sobrescribe)
with open("alertas.txt", "a") as archivo:
    archivo.write("Nueva alerta detectada\n")

# Crear nuevo archivo
try:
    with open("nuevo_log.txt", "x") as archivo:
        archivo.write("Archivo de log inicializado\n")
except FileExistsError:
    print("El archivo ya existe")
```

### 3. Leer Archivos

```python
# Leer archivo completo
with open("usuarios.txt", "r") as archivo:
    contenido_completo = archivo.read()
    print(contenido_completo)

# Leer línea por línea
with open("usuarios.txt", "r") as archivo:
    for linea in archivo:
        print(linea.strip())  # strip() elimina saltos de línea

# Leer todas las líneas como lista
with open("usuarios.txt", "r") as archivo:
    lineas = archivo.readlines()
    print(f"Total de líneas: {len(lineas)}")

# Leer línea específica
with open("usuarios.txt", "r") as archivo:
    primera_linea = archivo.readline()
    segunda_linea = archivo.readline()
    print(f"Primera línea: {primera_linea.strip()}")
```

### 4. Escribir en Archivos

```python
# Escribir string único
with open("output.txt", "w") as archivo:
    archivo.write("Línea de texto\n")

# Escribir múltiples líneas
lineas = [
    "Usuario: admin\n",
    "Estado: activo\n",
    "Permisos: todos\n"
]

with open("usuario_info.txt", "w") as archivo:
    archivo.writelines(lineas)

# Escribir con formato
usuarios = ["admin", "user1", "user2"]

with open("lista_usuarios.txt", "w") as archivo:
    for i, usuario in enumerate(usuarios, 1):
        archivo.write(f"{i}. {usuario}\n")
```

### 5. Procesar Archivos de Log

```python
def analizar_archivo_log(nombre_archivo):
    """
    Analiza un archivo de log y extrae estadísticas.
    """
    estadisticas = {
        "total_lineas": 0,
        "errores": 0,
        "advertencias": 0,
        "info": 0,
        "ips_unicas": set()
    }
    
    try:
        with open(nombre_archivo, "r") as archivo:
            for linea in archivo:
                estadisticas["total_lineas"] += 1
                
                # Contar por nivel
                if "ERROR" in linea:
                    estadisticas["errores"] += 1
                elif "WARNING" in linea:
                    estadisticas["advertencias"] += 1
                elif "INFO" in linea:
                    estadisticas["info"] += 1
                
                # Extraer IPs (patrón simple)
                palabras = linea.split()
                for palabra in palabras:
                    if palabra.count(".") == 3:
                        partes = palabra.split(".")
                        if all(parte.isdigit() for parte in partes):
                            estadisticas["ips_unicas"].add(palabra)
        
        # Convertir set a lista para el resultado
        estadisticas["ips_unicas"] = list(estadisticas["ips_unicas"])
        return estadisticas
    
    except FileNotFoundError:
        print(f"Error: El archivo {nombre_archivo} no existe")
        return None
    except PermissionError:
        print(f"Error: Sin permisos para leer {nombre_archivo}")
        return None

# Uso
resultado = analizar_archivo_log("security.log")
if resultado:
    print(f"Total de líneas: {resultado['total_lineas']}")
    print(f"Errores: {resultado['errores']}")
    print(f"Advertencias: {resultado['advertencias']}")
    print(f"IPs únicas: {len(resultado['ips_unicas'])}")
```

### 6. Trabajar con CSV

```python
import csv

# Leer archivo CSV
def leer_usuarios_csv(nombre_archivo):
    """Lee usuarios desde un archivo CSV."""
    usuarios = []
    
    with open(nombre_archivo, "r") as archivo:
        lector = csv.reader(archivo)
        encabezados = next(lector)  # Primera línea (headers)
        
        for fila in lector:
            usuario = {
                "username": fila[0],
                "email": fila[1],
                "rol": fila[2],
                "activo": fila[3] == "True"
            }
            usuarios.append(usuario)
    
    return usuarios

# Escribir archivo CSV
def escribir_reporte_csv(nombre_archivo, datos):
    """Escribe reporte de seguridad en CSV."""
    with open(nombre_archivo, "w", newline="") as archivo:
        escritor = csv.writer(archivo)
        
        # Escribir encabezados
        escritor.writerow(["Timestamp", "Evento", "Usuario", "IP", "Severidad"])
        
        # Escribir datos
        for evento in datos:
            escritor.writerow([
                evento["timestamp"],
                evento["evento"],
                evento["usuario"],
                evento["ip"],
                evento["severidad"]
            ])

# Usar DictReader y DictWriter (más conveniente)
def procesar_csv_avanzado(archivo_entrada, archivo_salida):
    """Procesa CSV y filtra eventos críticos."""
    with open(archivo_entrada, "r") as entrada:
        lector = csv.DictReader(entrada)
        
        eventos_criticos = []
        for fila in lector:
            if fila["severidad"] == "CRITICO":
                eventos_criticos.append(fila)
    
    # Escribir eventos críticos
    if eventos_criticos:
        with open(archivo_salida, "w", newline="") as salida:
            campos = eventos_criticos[0].keys()
            escritor = csv.DictWriter(salida, fieldnames=campos)
            
            escritor.writeheader()
            escritor.writerows(eventos_criticos)

# Ejemplo de uso
datos_ejemplo = [
    {
        "timestamp": "2024-10-09 10:30:00",
        "evento": "Login fallido",
        "usuario": "admin",
        "ip": "192.168.1.100",
        "severidad": "MEDIO"
    },
    {
        "timestamp": "2024-10-09 10:35:00",
        "evento": "Acceso no autorizado",
        "usuario": "hacker",
        "ip": "10.0.0.5",
        "severidad": "CRITICO"
    }
]

escribir_reporte_csv("reporte_eventos.csv", datos_ejemplo)
```

### 7. Trabajar con JSON

```python
import json

# Leer archivo JSON
def leer_configuracion_json(nombre_archivo):
    """Lee configuración desde archivo JSON."""
    with open(nombre_archivo, "r") as archivo:
        configuracion = json.load(archivo)
    return configuracion

# Escribir archivo JSON
def guardar_reporte_json(nombre_archivo, datos):
    """Guarda reporte en formato JSON."""
    with open(nombre_archivo, "w") as archivo:
        json.dump(datos, archivo, indent=4)

# Ejemplo completo
def procesar_eventos_seguridad():
    """Procesa y guarda eventos de seguridad."""
    eventos = {
        "fecha_reporte": "2024-10-09",
        "total_eventos": 3,
        "eventos": [
            {
                "id": 1,
                "tipo": "intrusion",
                "severidad": "alta",
                "detalles": {
                    "ip_origen": "192.168.1.100",
                    "puerto": 22,
                    "intentos": 5
                }
            },
            {
                "id": 2,
                "tipo": "malware",
                "severidad": "critica",
                "detalles": {
                    "archivo": "virus.exe",
                    "ubicacion": "/tmp/",
                    "hash": "abc123def456"
                }
            }
        ]
    }
    
    # Guardar como JSON
    guardar_reporte_json("reporte_seguridad.json", eventos)
    
    # Leer y procesar
    datos = leer_configuracion_json("reporte_seguridad.json")
    print(f"Total de eventos: {datos['total_eventos']}")
    
    for evento in datos["eventos"]:
        print(f"Evento {evento['id']}: {evento['tipo']} - Severidad: {evento['severidad']}")

# Convertir entre formatos
def csv_a_json(archivo_csv, archivo_json):
    """Convierte archivo CSV a JSON."""
    import csv
    
    datos = []
    with open(archivo_csv, "r") as archivo:
        lector = csv.DictReader(archivo)
        for fila in lector:
            datos.append(fila)
    
    with open(archivo_json, "w") as archivo:
        json.dump(datos, archivo, indent=4)
```

### 8. Gestión de Rutas de Archivos

```python
import os

# Verificar existencia de archivo
def verificar_archivo(nombre_archivo):
    """Verifica si un archivo existe."""
    if os.path.exists(nombre_archivo):
        print(f"✅ El archivo {nombre_archivo} existe")
        
        # Obtener información
        tamano = os.path.getsize(nombre_archivo)
        print(f"Tamaño: {tamano} bytes")
        
        if os.path.isfile(nombre_archivo):
            print("Es un archivo")
        elif os.path.isdir(nombre_archivo):
            print("Es un directorio")
    else:
        print(f"❌ El archivo {nombre_archivo} no existe")

# Listar archivos en directorio
def listar_logs(directorio):
    """Lista todos los archivos .log en un directorio."""
    if not os.path.exists(directorio):
        print(f"El directorio {directorio} no existe")
        return []
    
    archivos_log = []
    for archivo in os.listdir(directorio):
        if archivo.endswith(".log"):
            ruta_completa = os.path.join(directorio, archivo)
            archivos_log.append(ruta_completa)
    
    return archivos_log

# Crear directorios
def crear_estructura_logs():
    """Crea estructura de directorios para logs."""
    directorios = [
        "logs",
        "logs/security",
        "logs/access",
        "logs/error"
    ]
    
    for directorio in directorios:
        if not os.path.exists(directorio):
            os.makedirs(directorio)
            print(f"Directorio creado: {directorio}")
        else:
            print(f"Directorio ya existe: {directorio}")

# Ejemplo de uso
verificar_archivo("security.log")
logs = listar_logs("logs/security")
print(f"Archivos de log encontrados: {len(logs)}")
```

---

## ⚠️ Manejo de Excepciones

### 1. Fundamentos de Excepciones

```python
# Estructura básica try-except
try:
    # Código que puede generar error
    numero = int(input("Ingrese un número: "))
    resultado = 10 / numero
    print(f"Resultado: {resultado}")
except ValueError:
    print("Error: Debe ingresar un número válido")
except ZeroDivisionError:
    print("Error: No se puede dividir por cero")

# Con bloque else y finally
try:
    archivo = open("datos.txt", "r")
    contenido = archivo.read()
except FileNotFoundError:
    print("Archivo no encontrado")
else:
    print("Archivo leído exitosamente")
    print(contenido)
finally:
    print("Operación completada")
    # Se ejecuta siempre, ideal para limpieza
```

### 2. Excepciones Comunes en Seguridad

```python
def leer_archivo_seguro(nombre_archivo):
    """Lee archivo con manejo robusto de errores."""
    try:
        with open(nombre_archivo, "r") as archivo:
            return archivo.read()
    
    except FileNotFoundError:
        print(f"❌ Error: El archivo '{nombre_archivo}' no existe")
        return None
    
    except PermissionError:
        print(f"❌ Error: Sin permisos para leer '{nombre_archivo}'")
        return None
    
    except IsADirectoryError:
        print(f"❌ Error: '{nombre_archivo}' es un directorio, no un archivo")
        return None
    
    except Exception as e:
        print(f"❌ Error inesperado: {e}")
        return None

def validar_ip_segura(ip):
    """Valida formato de IP con manejo de errores."""
    try:
        partes = ip.split(".")
        
        if len(partes) != 4:
            raise ValueError("La IP debe tener 4 octetos")
        
        for parte in partes:
            numero = int(parte)
            if numero < 0 or numero > 255:
                raise ValueError(f"Octeto {numero} fuera de rango (0-255)")
        
        return True
    
    except ValueError as e:
        print(f"IP inválida: {e}")
        return False
    except AttributeError:
        print("Error: El valor proporcionado no es una cadena")
        return False

# Uso
contenido = leer_archivo_seguro("usuarios.txt")
if contenido:
    print("Contenido procesado exitosamente")

validar_ip_segura("192.168.1.1")  # True
validar_ip_segura("256.1.1.1")    # False
```

### 3. Crear Excepciones Personalizadas

```python
# Definir excepciones personalizadas
class ErrorDeSeguridad(Exception):
    """Excepción base para errores de seguridad."""
    pass

class AccesoNoAutorizadoError(ErrorDeSeguridad):
    """Se lanza cuando se detecta acceso no autorizado."""
    pass

class CredencialesInvalidasError(ErrorDeSeguridad):
    """Se lanza cuando las credenciales son inválidas."""
    pass

class LimiteIntentosExcedidoError(ErrorDeSeguridad):
    """Se lanza cuando se excede el límite de intentos."""
    pass

# Usar excepciones personalizadas
class SistemaAutenticacion:
    def __init__(self):
        self.usuarios_validos = {
            "admin": "admin123",
            "user1": "pass123"
        }
        self.intentos_fallidos = {}
        self.max_intentos = 3
    
    def autenticar(self, usuario, password):
        """Autentica usuario con manejo de errores personalizado."""
        # Verificar intentos fallidos
        if usuario in self.intentos_fallidos:
            if self.intentos_fallidos[usuario] >= self.max_intentos:
                raise LimiteIntentosExcedidoError(
                    f"Usuario '{usuario}' bloqueado por exceder intentos permitidos"
                )
        
        # Verificar usuario existe
        if usuario not in self.usuarios_validos:
            raise AccesoNoAutorizadoError(
                f"Usuario '{usuario}' no existe en el sistema"
            )
        
        # Verificar password
        if self.usuarios_validos[usuario] != password:
            # Incrementar intentos fallidos
            if usuario not in self.intentos_fallidos:
                self.intentos_fallidos[usuario] = 0
            self.intentos_fallidos[usuario] += 1
            
            raise CredencialesInvalidasError(
                f"Contraseña incorrecta. Intento {self.intentos_fallidos[usuario]}/{self.max_intentos}"
            )
        
        # Autenticación exitosa
        if usuario in self.intentos_fallidos:
            del self.intentos_fallidos[usuario]
        
        return True

# Ejemplo de uso
sistema = SistemaAutenticacion()

try:
    sistema.autenticar("admin", "wrong_pass")
except CredencialesInvalidasError as e:
    print(f"⚠️ {e}")

try:
    sistema.autenticar("hacker", "password")
except AccesoNoAutorizadoError as e:
    print(f"🚨 {e}")

try:
    # Múltiples intentos fallidos
    for i in range(4):
        sistema.autenticar("admin", "wrong")
except LimiteIntentosExcedidoError as e:
    print(f"🔒 {e}")
except CredencialesInvalidasError as e:
    print(f"⚠️ {e}")
```

### 4. Logging de Errores

```python
import logging
from datetime import datetime

# Configurar logging
logging.basicConfig(
    filename='security_errors.log',
    level=logging.DEBUG,
    format='%(asctime)s - %(levelname)s - %(message)s'
)

def procesar_archivo_con_logging(nombre_archivo):
    """Procesa archivo y registra errores."""
    try:
        logging.info(f"Iniciando procesamiento de {nombre_archivo}")
        
        with open(nombre_archivo, "r") as archivo:
            lineas = archivo.readlines()
            logging.info(f"Archivo leído: {len(lineas)} líneas")
            
            for i, linea in enumerate(lineas, 1):
                try:
                    # Procesar línea
                    if "ERROR" in linea:
                        logging.warning(f"Error encontrado en línea {i}: {linea.strip()}")
                except Exception as e:
                    logging.error(f"Error procesando línea {i}: {e}")
        
        logging.info("Procesamiento completado exitosamente")
        return True
    
    except FileNotFoundError:
        logging.error(f"Archivo no encontrado: {nombre_archivo}")
        return False
    except Exception as e:
        logging.critical(f"Error crítico: {e}")
        return False

# Función de logging personalizada
def log_evento_seguridad(nivel, mensaje, detalles=None):
    """Registra eventos de seguridad en archivo específico."""
    timestamp = datetime.now().strftime("%Y-%m-%d %H:%M:%S")
    
    with open("security_events.log", "a") as archivo:
        linea = f"[{timestamp}] {nivel}: {mensaje}"
        if detalles:
            linea += f" - Detalles: {detalles}"
        archivo.write(linea + "\n")

# Uso
log_evento_seguridad("ALERTA", "Intento de acceso no autorizado", 
                     {"ip": "192.168.1.100", "usuario": "admin"})
```

---

## 🐛 Depuración de Código

### 1. Técnicas de Depuración

```python
# 1. Print debugging (básico pero efectivo)
def calcular_promedio_intentos(intentos):
    print(f"DEBUG: Procesando {len(intentos)} intentos")
    
    total = sum(intentos)
    print(f"DEBUG: Total = {total}")
    
    promedio = total / len(intentos)
    print(f"DEBUG: Promedio = {promedio}")
    
    return promedio

# 2. Usar assert para validaciones
def validar_puerto(puerto):
    assert isinstance(puerto, int), "Puerto debe ser un entero"
    assert 1 <= puerto <= 65535, f"Puerto {puerto} fuera de rango válido"
    return True

# 3. Depuración con try-except detallado
def procesar_datos_debug(datos):
    try:
        resultado = []
        for i, item in enumerate(datos):
            try:
                procesado = item.strip().upper()
                resultado.append(procesado)
            except AttributeError:
                print(f"DEBUG: Item {i} no es string: {type(item)} - {item}")
            except Exception as e:
                print(f"DEBUG: Error en item {i}: {e}")
        return resultado
    except Exception as e:
        print(f"DEBUG: Error general: {e}")
        import traceback
        traceback.print_exc()
        return None
```

### 2. Herramientas de Depuración

```python
# Usar pdb (Python Debugger)
import pdb

def funcion_compleja(datos):
    resultado = []
    
    for item in datos:
        # pdb.set_trace()  # Pausa ejecución aquí
        procesado = item * 2
        resultado.append(procesado)
    
    return resultado

# Breakpoint (Python 3.7+)
def analizar_log(linea):
    if "CRITICAL" in linea:
        breakpoint()  # Pausa para inspección
        # Aquí puedes examinar variables
    return linea.split()

# Función de debugging personalizada
def debug_print(variable, nombre="Variable"):
    """Imprime variable con formato detallado."""
    print(f"\n{'='*50}")
    print(f"DEBUG - {nombre}")
    print(f"Tipo: {type(variable)}")
    print(f"Valor: {variable}")
    if hasattr(variable, '__len__'):
        print(f"Longitud: {len(variable)}")
    print('='*50 + '\n')

# Uso
datos = [1, 2, 3, 4, 5]
debug_print(datos, "Lista de datos")
```

### 3. Validación y Testing

```python
def validar_entrada(valor, tipo_esperado, rango=None):
    """Valida entrada con debugging detallado."""
    errores = []
    
    # Validar tipo
    if not isinstance(valor, tipo_esperado):
        errores.append(f"Tipo incorrecto: esperado {tipo_esperado}, recibido {type(valor)}")
    
    # Validar rango si es numérico
    if rango and isinstance(valor, (int, float)):
        min_val, max_val = rango
        if valor < min_val or valor > max_val:
            errores.append(f"Fuera de rango: {valor} no está entre {min_val} y {max_val}")
    
    if errores:
        print("❌ Errores de validación:")
        for error in errores:
            print(f"  - {error}")
        return False
    
    print("✅ Validación exitosa")
    return True

# Tests unitarios simples
def test_validar_ip():
    """Pruebas para función de validación de IP."""
    casos_prueba = [
        ("192.168.1.1", True),
        ("256.1.1.1", False),
        ("192.168.1", False),
        ("abc.def.ghi.jkl", False)
    ]
    
    print("Ejecutando tests...")
    for ip, esperado in casos_prueba:
        resultado = validar_formato_ip(ip)
        if resultado == esperado:
            print(f"✅ PASS: {ip}")
        else:
            print(f"❌ FAIL: {ip} - Esperado: {esperado}, Obtenido: {resultado}")

def validar_formato_ip(ip):
    """Valida formato de IP."""
    try:
        partes = ip.split(".")
        if len(partes) != 4:
            return False
        return all(parte.isdigit() and 0 <= int(parte) <= 255 for parte in partes)
    except:
        return False

# Ejecutar tests
test_validar_ip()
```

---

## 📦 Módulos y Librerías

### 1. Módulos Estándar Útiles

```python
# datetime - Manejo de fechas y tiempo
from datetime import datetime, timedelta

def registrar_evento_con_timestamp():
    """Registra evento con timestamp actual."""
    ahora = datetime.now()
    timestamp = ahora.strftime("%Y-%m-%d %H:%M:%S")
    print(f"[{timestamp}] Evento registrado")
    
    # Calcular tiempo hace 24 horas
    hace_24h = ahora - timedelta(hours=24)
    print(f"Eventos desde: {hace_24h}")

# os y os.path - Operaciones del sistema
import os

def analizar_sistema_archivos():
    """Analiza archivos del sistema."""
    directorio_actual = os.getcwd()
    print(f"Directorio actual: {directorio_actual}")
    
    # Listar archivos
    archivos = os.listdir(".")
    print(f"Total de archivos: {len(archivos)}")
    
    # Información de archivos
    for archivo in archivos:
        if os.path.isfile(archivo):
            tamano = os.path.getsize(archivo)
            print(f"{archivo}: {tamano} bytes")

# re - Expresiones regulares
import re

def extraer_ips_con_regex(texto):
    """Extrae IPs usando expresiones regulares."""
    patron = r'\b\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}\b'
    ips = re.findall(patron, texto)
    return ips

def validar_email(email):
    """Valida formato de email."""
    patron = r'^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$'
    return re.match(patron, email) is not None

# hashlib - Funciones hash
import hashlib

def calcular_hash_archivo(nombre_archivo):
    """Calcula hash SHA-256 de un archivo."""
    sha256 = hashlib.sha256()
    
    try:
        with open(nombre_archivo, "rb") as archivo:
            # Leer en bloques para archivos grandes
            for bloque in iter(lambda: archivo.read(4096), b""):
                sha256.update(bloque)
        
        return sha256.hexdigest()
    except FileNotFoundError:
        return None

def hash_password(password):
    """Genera hash de contraseña."""
    return hashlib.sha256(password.encode()).hexdigest()

# Ejemplo de uso
texto_log = "Conexión desde 192.168.1.100 y 10.0.0.5"
ips_encontradas = extraer_ips_con_regex(texto_log)
print(f"IPs encontradas: {ips_encontradas}")

print(f"Email válido: {validar_email('usuario@ejemplo.com')}")
print(f"Email inválido: {validar_email('usuario@')}")
```

### 2. Crear y Usar Módulos Propios

```python
# Archivo: seguridad_utils.py
"""
Módulo de utilidades para seguridad cibernética.
Contiene funciones comunes para análisis y validación.
"""

def validar_ip(ip):
    """Valida formato de dirección IP."""
    try:
        partes = ip.split(".")
        if len(partes) != 4:
            return False
        return all(p.isdigit() and 0 <= int(p) <= 255 for p in partes)
    except:
        return False

def sanitizar_entrada(entrada):
    """Sanitiza entrada de usuario para prevenir inyecciones."""
    caracteres_peligrosos = ["<", ">", "&", "'", '"', ";", "--"]
    entrada_limpia = entrada
    for char in caracteres_peligrosos:
        entrada_limpia = entrada_limpia.replace(char, "")
    return entrada_limpia

def generar_reporte(titulo, datos):
    """Genera reporte formateado."""
    reporte = []
    reporte.append("=" * 60)
    reporte.append(f" {titulo.center(58)} ")
    reporte.append("=" * 60)
    
    for clave, valor in datos.items():
        reporte.append(f"{clave}: {valor}")
    
    reporte.append("=" * 60)
    return "\n".join(reporte)

# Archivo: main.py
# Importar módulo propio
import seguridad_utils

# Usar funciones del módulo
ip_valida = seguridad_utils.validar_ip("192.168.1.1")
print(f"IP válida: {ip_valida}")

entrada_usuario = "<script>alert('XSS')</script>"
entrada_segura = seguridad_utils.sanitizar_entrada(entrada_usuario)
print(f"Entrada sanitizada: {entrada_segura}")

datos = {
    "Eventos totales": 150,
    "Alertas críticas": 5,
    "IPs bloqueadas": 12
}
print(seguridad_utils.generar_reporte("Reporte de Seguridad", datos))

# Importar funciones específicas
from seguridad_utils import validar_ip, sanitizar_entrada

# Usar directamente sin prefijo
if validar_ip("10.0.0.1"):
    print("IP válida")

# Importar con alias
import seguridad_utils as sec_utils

resultado = sec_utils.validar_ip("172.16.0.1")
```

### 3. Librerías Externas Comunes

```python
# requests - Para peticiones HTTP
# pip install requests
import requests

def verificar_url(url):
    """Verifica si una URL está accesible."""
    try:
        respuesta = requests.get(url, timeout=5)
        return {
            "accesible": True,
            "codigo_estado": respuesta.status_code,
            "tiempo_respuesta": respuesta.elapsed.total_seconds()
        }
    except requests.exceptions.RequestException as e:
        return {
            "accesible": False,
            "error": str(e)
        }

# tabulate - Para formatear tablas
# pip install tabulate
from tabulate import tabulate

def mostrar_tabla_eventos(eventos):
    """Muestra eventos en formato tabla."""
    headers = ["ID", "Tipo", "Usuario", "IP", "Severidad"]
    datos = []
    
    for evento in eventos:
        datos.append([
            evento["id"],
            evento["tipo"],
            evento["usuario"],
            evento["ip"],
            evento["severidad"]
        ])
    
    print(tabulate(datos, headers=headers, tablefmt="grid"))

# Ejemplo de uso
eventos = [
    {"id": 1, "tipo": "Login", "usuario": "admin", "ip": "192.168.1.10", "severidad": "INFO"},
    {"id": 2, "tipo": "Intrusión", "usuario": "unknown", "ip": "10.0.0.5", "severidad": "CRITICO"}
]
mostrar_tabla_eventos(eventos)
```

---

## 🚀 Proyectos Prácticos

### Proyecto 1: Sistema de Análisis de Logs

```python
"""
Sistema completo de análisis de logs de seguridad.
Procesa archivos de log, detecta patrones y genera reportes.
"""

import re
import json
from datetime import datetime
from collections import Counter

class AnalizadorLogs:
    def __init__(self):
        self.eventos = []
        self.estadisticas = {
            "total_eventos": 0,
            "por_nivel": Counter(),
            "por_tipo": Counter(),
            "ips_unicas": set(),
            "usuarios_unicos": set()
        }
    
    def cargar_archivo(self, nombre_archivo):
        """Carga y procesa archivo de log."""
        try:
            with open(nombre_archivo, "r") as archivo:
                for linea in archivo:
                    evento = self._parsear_linea(linea)
                    if evento:
                        self.eventos.append(evento)
                        self._actualizar_estadisticas(evento)
            
            print(f"✅ Archivo cargado: {len(self.eventos)} eventos procesados")
            return True
        
        except FileNotFoundError:
            print(f"❌ Error: Archivo {nombre_archivo} no encontrado")
            return False
        except Exception as e:
            print(f"❌ Error al procesar archivo: {e}")
            return False
    
    def _parsear_linea(self, linea):
        """Parsea una línea de log y extrae información."""
        # Formato: [TIMESTAMP] NIVEL - TIPO - USUARIO - IP - MENSAJE
        patron = r'\[(.*?)\] (\w+) - (\w+) - (\w+) - ([\d.]+) - (.*)'
        match = re.match(patron, linea)
        
        if match:
            return {
                "timestamp": match.group(1),
                "nivel": match.group(2),
                "tipo": match.group(3),
                "usuario": match.group(4),
                "ip": match.group(5),
                "mensaje": match.group(6).strip()
            }
        return None
    
    def _actualizar_estadisticas(self, evento):
        """Actualiza estadísticas con nuevo evento."""
        self.estadisticas["total_eventos"] += 1
        self.estadisticas["por_nivel"][evento["nivel"]] += 1
        self.estadisticas["por_tipo"][evento["tipo"]] += 1
        self.estadisticas["ips_unicas"].add(evento["ip"])
        self.estadisticas["usuarios_unicos"].add(evento["usuario"])
    
    def filtrar_por_nivel(self, nivel):
        """Filtra eventos por nivel de severidad."""
        return [e for e in self.eventos if e["nivel"] == nivel]
    
    def filtrar_por_ip(self, ip):
        """Filtra eventos de una IP específica."""
        return [e for e in self.eventos if e["ip"] == ip]
    
    def detectar_anomalias(self):
        """Detecta patrones anómalos en los logs."""
        anomalias = []
        
        # Detectar IPs con múltiples intentos fallidos
        intentos_por_ip = Counter()
        for evento in self.eventos:
            if evento["tipo"] == "LOGIN_FAILED":
                intentos_por_ip[evento["ip"]] += 1
        
        for ip, intentos in intentos_por_ip.items():
            if intentos >= 5:
                anomalias.append({
                    "tipo": "Múltiples intentos fallidos",
                    "ip": ip,
                    "cantidad": intentos,
                    "severidad": "ALTA"
                })
        
        # Detectar accesos fuera de horario
        for evento in self.eventos:
            hora = int(evento["timestamp"].split()[1].split(":")[0])
            if hora < 6 or hora > 22:
                anomalias.append({
                    "tipo": "Acceso fuera de horario",
                    "usuario": evento["usuario"],
                    "timestamp": evento["timestamp"],
                    "severidad": "MEDIA"
                })
        
        return anomalias
    
    def generar_reporte(self, archivo_salida="reporte_seguridad.txt"):
        """Genera reporte completo de análisis."""
        try:
            with open(archivo_salida, "w") as archivo:
                archivo.write("=" * 70 + "\n")
                archivo.write("REPORTE DE ANÁLISIS DE SEGURIDAD\n".center(70))
                archivo.write("=" * 70 + "\n\n")
                
                # Estadísticas generales
                archivo.write("ESTADÍSTICAS GENERALES\n")
                archivo.write("-" * 70 + "\n")
                archivo.write(f"Total de eventos: {self.estadisticas['total_eventos']}\n")
                archivo.write(f"IPs únicas: {len(self.estadisticas['ips_unicas'])}\n")
                archivo.write(f"Usuarios únicos: {len(self.estadisticas['usuarios_unicos'])}\n\n")
                
                # Eventos por nivel
                archivo.write("EVENTOS POR NIVEL\n")
                archivo.write("-" * 70 + "\n")
                for nivel, cantidad in self.estadisticas["por_nivel"].most_common():
                    archivo.write(f"{nivel}: {cantidad}\n")
                archivo.write("\n")
                
                # Eventos por tipo
                archivo.write("EVENTOS POR TIPO\n")
                archivo.write("-" * 70 + "\n")
                for tipo, cantidad in self.estadisticas["por_tipo"].most_common():
                    archivo.write(f"{tipo}: {cantidad}\n")
                archivo.write("\n")
                
                # Anomalías detectadas
                anomalias = self.detectar_anomalias()
                archivo.write("ANOMALÍAS DETECTADAS\n")
                archivo.write("-" * 70 + "\n")
                if anomalias:
                    for i, anomalia in enumerate(anomalias, 1):
                        archivo.write(f"{i}. {anomalia['tipo']}\n")
                        for clave, valor in anomalia.items():
                            if clave != 'tipo':
                                archivo.write(f"   {clave}: {valor}\n")
                        archivo.write("\n")
                else:
                    archivo.write("No se detectaron anomalías\n")
                
                archivo.write("=" * 70 + "\n")
            
            print(f"✅ Reporte generado: {archivo_salida}")
            return True
        
        except Exception as e:
            print(f"❌ Error al generar reporte: {e}")
            return False
    
    def exportar_json(self, archivo_salida="analisis.json"):
        """Exporta análisis completo a JSON."""
        datos = {
            "fecha_analisis": datetime.now().strftime("%Y-%m-%d %H:%M:%S"),
            "estadisticas": {
                "total_eventos": self.estadisticas["total_eventos"],
                "por_nivel": dict(self.estadisticas["por_nivel"]),
                "por_tipo": dict(self.estadisticas["por_tipo"]),
                "ips_unicas": list(self.estadisticas["ips_unicas"]),
                "usuarios_unicos": list(self.estadisticas["usuarios_unicos"])
            },
            "anomalias": self.detectar_anomalias(),
            "eventos_criticos": self.filtrar_por_nivel("CRITICAL")
        }
        
        try:
            with open(archivo_salida, "w") as archivo:
                json.dump(datos, archivo, indent=4)
            print(f"✅ Datos exportados a: {archivo_salida}")
            return True
        except Exception as e:
            print(f"❌ Error al exportar: {e}")
            return False

# Ejemplo de uso del sistema
def main():
    print("🛡️ Sistema de Análisis de Logs de Seguridad\n")
    
    # Crear analizador
    analizador = AnalizadorLogs()
    
    # Cargar archivo de log
    if analizador.cargar_archivo("security.log"):
        
        # Mostrar estadísticas
        print(f"\n📊 Estadísticas:")
        print(f"Total de eventos: {analizador.estadisticas['total_eventos']}")
        print(f"IPs únicas: {len(analizador.estadisticas['ips_unicas'])}")
        
        # Detectar anomalías
        anomalias = analizador.detectar_anomalias()
        print(f"\n⚠️ Anomalías detectadas: {len(anomalias)}")
        
        # Generar reportes
        analizador.generar_reporte()
        analizador.exportar_json()

if __name__ == "__main__":
    main()
```

### Proyecto 2: Gestor de Listas de Control de Acceso

```python
"""
Sistema de gestión de listas de control de acceso (ACL).
Administra permitidos, bloqueados y genera reportes.
"""

import json
import csv
from datetime import datetime

class GestorACL:
    def __init__(self, archivo_config="acl_config.json"):
        self.archivo_config = archivo_config
        self.lista_permitidos = []
        self.lista_bloqueados = []
        self.historial = []
        self.cargar_configuracion()
    
    def cargar_configuracion(self):
        """Carga configuración desde archivo JSON."""
        try:
            with open(self.archivo_config, "r") as archivo:
                datos = json.load(archivo)
                self.lista_permitidos = datos.get("permitidos", [])
                self.lista_bloqueados = datos.get("bloqueados", [])
                self.historial = datos.get("historial", [])
            print("✅ Configuración cargada")
        except FileNotFoundError:
            print("⚠️ Archivo de configuración no encontrado, creando nuevo")
            self.guardar_configuracion()
        except json.JSONDecodeError:
            print("❌ Error al leer configuración")
    
    def guardar_configuracion(self):
        """Guarda configuración en archivo JSON."""
        datos = {
            "permitidos": self.lista_permitidos,
            "bloqueados": self.lista_bloqueados,
            "historial": self.historial,
            "ultima_actualizacion": datetime.now().strftime("%Y-%m-%d %H:%M:%S")
        }
        
        try:
            with open(self.archivo_config, "w") as archivo:
                json.dump(datos, archivo, indent=4)
            return True
        except Exception as e:
            print(f"❌ Error al guardar: {e}")
            return False
    
    def agregar_permitido(self, elemento, razon=""):
        """Agrega elemento a lista de permitidos."""
        if elemento in self.lista_bloqueados:
            self.lista_bloqueados.remove(elemento)
            self._registrar_historial("DESBLOQUEAR", elemento, razon)
        
        if elemento not in self.lista_permitidos:
            self.lista_permitidos.append(elemento)
            self._registrar_historial("PERMITIR", elemento, razon)
            self.guardar_configuracion()
            print(f"✅ {elemento} agregado a permitidos")
            return True
        else:
            print(f"⚠️ {elemento} ya está en permitidos")
            return False
    
    def agregar_bloqueado(self, elemento, razon=""):
        """Agrega elemento a lista de bloqueados."""
        if elemento in self.lista_permitidos:
            self.lista_permitidos.remove(elemento)
            self._registrar_historial("REMOVER_PERMITIDO", elemento, razon)
        
        if elemento not in self.lista_bloqueados:
            self.lista_bloqueados.append(elemento)
            self._registrar_historial("BLOQUEAR", elemento, razon)
            self.guardar_configuracion()
            print(f"🚫 {elemento} agregado a bloqueados")
            return True
        else:
            print(f"⚠️ {elemento} ya está en bloqueados")
            return False
    
    def verificar_acceso(self, elemento):
        """Verifica si un elemento tiene acceso permitido."""
        if elemento in self.lista_bloqueados:
            return {
                "permitido": False,
                "motivo": "Elemento en lista de bloqueados",
                "accion": "DENEGAR"
            }
        elif elemento in self.lista_permitidos:
            return {
                "permitido": True,
                "motivo": "Elemento en lista de permitidos",
                "accion": "PERMITIR"
            }
        else:
            return {
                "permitido": None,
                "motivo": "Elemento no está en ninguna lista",
                "accion": "VERIFICAR_MANUALMENTE"
            }
    
    def _registrar_historial(self, accion, elemento, razon=""):
        """Registra acción en historial."""
        registro = {
            "timestamp": datetime.now().strftime("%Y-%m-%d %H:%M:%S"),
            "accion": accion,
            "elemento": elemento,
            "razon": razon
        }
        self.historial.append(registro)
    
    def importar_desde_csv(self, archivo_csv, tipo="permitidos"):
        """Importa lista desde archivo CSV."""
        try:
            with open(archivo_csv, "r") as archivo:
                lector = csv.reader(archivo)
                next(lector)  # Saltar encabezado
                
                contador = 0
                for fila in lector:
                    if len(fila) >= 1:
                        elemento = fila[0].strip()
                        razon = fila[1] if len(fila) > 1 else "Importado desde CSV"
                        
                        if tipo == "permitidos":
                            self.agregar_permitido(elemento, razon)
                        else:
                            self.agregar_bloqueado(elemento, razon)
                        contador += 1
                
                print(f"✅ Importados {contador} elementos")
                return True
        except FileNotFoundError:
            print(f"❌ Archivo {archivo_csv} no encontrado")
            return False
        except Exception as e:
            print(f"❌ Error al importar: {e}")
            return False
    
    def exportar_a_csv(self, archivo_csv="acl_export.csv"):
        """Exporta listas a archivo CSV."""
        try:
            with open(archivo_csv, "w", newline="") as archivo:
                escritor = csv.writer(archivo)
                escritor.writerow(["Tipo", "Elemento", "Fecha"])
                
                for elemento in self.lista_permitidos:
                    escritor.writerow(["PERMITIDO", elemento, datetime.now().date()])
                
                for elemento in self.lista_bloqueados:
                    escritor.writerow(["BLOQUEADO", elemento, datetime.now().date()])
            
            print(f"✅ Datos exportados a {archivo_csv}")
            return True
        except Exception as e:
            print(f"❌ Error al exportar: {e}")
            return False
    
    def generar_reporte(self):
        """Genera reporte completo de ACL."""
        reporte = []
        reporte.append("=" * 70)
        reporte.append("REPORTE DE CONTROL DE ACCESO".center(70))
        reporte.append("=" * 70)
        reporte.append(f"\nFecha: {datetime.now().strftime('%Y-%m-%d %H:%M:%S')}\n")
        
        # Estadísticas
        reporte.append("ESTADÍSTICAS")
        reporte.append("-" * 70)
        reporte.append(f"Total permitidos: {len(self.lista_permitidos)}")
        reporte.append(f"Total bloqueados: {len(self.lista_bloqueados)}")
        reporte.append(f"Total en historial: {len(self.historial)}\n")
        
        # Lista de permitidos
        reporte.append("ELEMENTOS PERMITIDOS")
        reporte.append("-" * 70)
        if self.lista_permitidos:
            for i, elem in enumerate(self.lista_permitidos, 1):
                reporte.append(f"{i}. {elem}")
        else:
            reporte.append("(vacío)")
        reporte.append("")
        
        # Lista de bloqueados
        reporte.append("ELEMENTOS BLOQUEADOS")
        reporte.append("-" * 70)
        if self.lista_bloqueados:
            for i, elem in enumerate(self.lista_bloqueados, 1):
                reporte.append(f"{i}. {elem}")
        else:
            reporte.append("(vacío)")
        reporte.append("")
        
        # Historial reciente
        reporte.append("HISTORIAL RECIENTE (últimas 10 acciones)")
        reporte.append("-" * 70)
        for registro in self.historial[-10:]:
            reporte.append(f"[{registro['timestamp']}] {registro['accion']}: {registro['elemento']}")
            if registro['razon']:
                reporte.append(f"  Razón: {registro['razon']}")
        
        reporte.append("=" * 70)
        
        return "\n".join(reporte)
    
    def mostrar_estadisticas(self):
        """Muestra estadísticas en consola."""
        print("\n📊 Estadísticas de ACL:")
        print(f"  • Permitidos: {len(self.lista_permitidos)}")
        print(f"  • Bloqueados: {len(self.lista_bloqueados)}")
        print(f"  • Acciones en historial: {len(self.historial)}")

# Interfaz de línea de comandos
def menu_principal():
    gestor = GestorACL()
    
    while True:
        print("\n" + "=" * 50)
        print("GESTOR DE CONTROL DE ACCESO")
        print("=" * 50)
        print("1. Agregar a permitidos")
        print("2. Agregar a bloqueados")
        print("3. Verificar acceso")
        print("4. Mostrar estadísticas")
        print("5. Generar reporte")
        print("6. Exportar a CSV")
        print("7. Importar desde CSV")
        print("8. Salir")
        print("=" * 50)
        
        opcion = input("\nSeleccione opción: ").strip()
        
        if opcion == "1":
            elemento = input("Elemento a permitir: ").strip()
            razon = input("Razón (opcional): ").strip()
            gestor.agregar_permitido(elemento, razon)
        
        elif opcion == "2":
            elemento = input("Elemento a bloquear: ").strip()
            razon = input("Razón (opcional): ").strip()
            gestor.agregar_bloqueado(elemento, razon)
        
        elif opcion == "3":
            elemento = input("Elemento a verificar: ").strip()
            resultado = gestor.verificar_acceso(elemento)
            print(f"\nResultado: {resultado['accion']}")
            print(f"Motivo: {resultado['motivo']}")
        
        elif opcion == "4":
            gestor.mostrar_estadisticas()
        
        elif opcion == "5":
            print("\n" + gestor.generar_reporte())
            guardar = input("\n¿Guardar en archivo? (s/n): ").strip().lower()
            if guardar == 's':
                with open("reporte_acl.txt", "w") as f:
                    f.write(gestor.generar_reporte())
                print("✅ Reporte guardado")
        
        elif opcion == "6":
            gestor.exportar_a_csv()
        
        elif opcion == "7":
            archivo = input("Nombre del archivo CSV: ").strip()
            tipo = input("Tipo (permitidos/bloqueados): ").strip()
            gestor.importar_desde_csv(archivo, tipo)
        
        elif opcion == "8":
            print("\n👋 ¡Hasta luego!")
            break
        
        else:
            print("❌ Opción inválida")

if __name__ == "__main__":
    menu_principal()
```

### Proyecto 3: Monitor de Integridad de Archivos

```python
"""
Sistema de monitoreo de integridad de archivos.
Detecta cambios en archivos críticos del sistema.
"""

import os
import hashlib
import json
from datetime import datetime

class MonitorIntegridad:
    def __init__(self, archivo_baseline="baseline.json"):
        self.archivo_baseline = archivo_baseline
        self.baseline = {}
        self.cambios_detectados = []
    
    def calcular_hash(self, ruta_archivo):
        """Calcula hash SHA-256 de un archivo."""
        try:
            sha256 = hashlib.sha256()
            with open(ruta_archivo, "rb") as archivo:
                for bloque in iter(lambda: archivo.read(4096), b""):
                    sha256.update(bloque)
            return sha256.hexdigest()
        except Exception as e:
            print(f"Error calculando hash de {ruta_archivo}: {e}")
            return None
    
    def obtener_metadata(self, ruta_archivo):
        """Obtiene metadata del archivo."""
        try:
            stats = os.stat(ruta_archivo)
            return {
                "tamano": stats.st_size,
                "modificado": datetime.fromtimestamp(stats.st_mtime).strftime("%Y-%m-%d %H:%M:%S"),
                "permisos": oct(stats.st_mode)[-3:]
            }
        except Exception as e:
            print(f"Error obteniendo metadata de {ruta_archivo}: {e}")
            return None
    
    def crear_baseline(self, directorios):
        """Crea baseline de archivos a monitorear."""
        print("🔍 Creando baseline...")
        
        for directorio in directorios:
            if not os.path.exists(directorio):
                print(f"⚠️ Directorio no encontrado: {directorio}")
                continue
            
            for raiz, dirs, archivos in os.walk(directorio):
                for archivo in archivos:
                    ruta_completa = os.path.join(raiz, archivo)
                    
                    hash_archivo = self.calcular_hash(ruta_completa)
                    metadata = self.obtener_metadata(ruta_completa)
                    
                    if hash_archivo and metadata:
                        self.baseline[ruta_completa] = {
                            "hash": hash_archivo,
                            "metadata": metadata,
                            "timestamp": datetime.now().strftime("%Y-%m-%d %H:%M:%S")
                        }
        
        self.guardar_baseline()
        print(f"✅ Baseline creado: {len(self.baseline)} archivos monitoreados")
    
    def cargar_baseline(self):
        """Carga baseline desde archivo."""
        try:
            with open(self.archivo_baseline, "r") as archivo:
                self.baseline = json.load(archivo)
            print(f"✅ Baseline cargado: {len(self.baseline)} archivos")
            return True
        except FileNotFoundError:
            print("⚠️ Baseline no encontrado")
            return False
        except json.JSONDecodeError:
            print("❌ Error al leer baseline")
            return False
    
    def guardar_baseline(self):
        """Guarda baseline en archivo."""
        try:
            with open(self.archivo_baseline, "w") as archivo:
                json.dump(self.baseline, archivo, indent=4)
            return True
        except Exception as e:
            print(f"❌ Error al guardar baseline: {e}")
            return False
    
    def verificar_integridad(self):
        """Verifica integridad de archivos contra baseline."""
        print("🔍 Verificando integridad...")
        self.cambios_detectados = []
        
        for ruta_archivo, datos_baseline in self.baseline.items():
            # Verificar si archivo existe
            if not os.path.exists(ruta_archivo):
                self.cambios_detectados.append({
                    "archivo": ruta_archivo,
                    "tipo_cambio": "ELIMINADO",
                    "timestamp": datetime.now().strftime("%Y-%m-%d %H:%M:%S")
                })
                continue
            
            # Calcular hash actual
            hash_actual = self.calcular_hash(ruta_archivo)
            metadata_actual = self.obtener_metadata(ruta_archivo)
            
            if not hash_actual or not metadata_actual:
                continue
            
            # Comparar hash
            if hash_actual != datos_baseline["hash"]:
                self.cambios_detectados.append({
                    "archivo": ruta_archivo,
                    "tipo_cambio": "MODIFICADO",
                    "hash_anterior": datos_baseline["hash"],
                    "hash_actual": hash_actual,
                    "timestamp": datetime.now().strftime("%Y-%m-%d %H:%M:%S")
                })
            
            # Comparar metadata
            elif metadata_actual != datos_baseline["metadata"]:
                self.cambios_detectados.append({
                    "archivo": ruta_archivo,
                    "tipo_cambio": "METADATA_CAMBIADA",
                    "metadata_anterior": datos_baseline["metadata"],
                    "metadata_actual": metadata_actual,
                    "timestamp": datetime.now().strftime("%Y-%m-%d %H:%M:%S")
                })
        
        # Detectar archivos nuevos
        for ruta_archivo in self.baseline.keys():
            if os.path.exists(ruta_archivo):
                archivos_actuales = set()
                for raiz, dirs, archivos in os.walk(os.path.dirname(ruta_archivo)):
                    for archivo in archivos:
                        archivos_actuales.add(os.path.join(raiz, archivo))
                
                for archivo_actual in archivos_actuales:
                    if archivo_actual not in self.baseline:
                        self.cambios_detectados.append({
                            "archivo": archivo_actual,
                            "tipo_cambio": "NUEVO",
                            "timestamp": datetime.now().strftime("%Y-%m-%d %H:%M:%S")
                        })
        
        print(f"✅ Verificación completada: {len(self.cambios_detectados)} cambios detectados")
        return self.cambios_detectados
    
    def generar_alerta(self, cambio):
        """Genera alerta para un cambio detectado."""
        severidad = {
            "MODIFICADO": "CRITICO",
            "ELIMINADO": "ALTO",
            "NUEVO": "MEDIO",
            "METADATA_CAMBIADA": "BAJO"
        }
        
        return {
            "timestamp": datetime.now().strftime("%Y-%m-%d %H:%M:%S"),
            "severidad": severidad.get(cambio["tipo_cambio"], "MEDIO"),
            "tipo": cambio["tipo_cambio"],
            "archivo": cambio["archivo"],
            "detalles": cambio
        }
    
    def generar_reporte(self, archivo_salida="reporte_integridad.txt"):
        """Genera reporte de integridad."""
        try:
            with open(archivo_salida, "w") as archivo:
                archivo.write("=" * 70 + "\n")
                archivo.write("REPORTE DE INTEGRIDAD DE ARCHIVOS\n".center(70))
                archivo.write("=" * 70 + "\n\n")
                
                archivo.write(f"Fecha: {datetime.now().strftime('%Y-%m-%d %H:%M:%S')}\n")
                archivo.write(f"Archivos monitoreados: {len(self.baseline)}\n")
                archivo.write(f"Cambios detectados: {len(self.cambios_detectados)}\n\n")
                
                if self.cambios_detectados:
                    archivo.write("CAMBIOS DETECTADOS\n")
                    archivo.write("-" * 70 + "\n")
                    
                    for i, cambio in enumerate(self.cambios_detectados, 1):
                        alerta = self.generar_alerta(cambio)
                        archivo.write(f"\n{i}. [{alerta['severidad']}] {cambio['tipo_cambio']}\n")
                        archivo.write(f"   Archivo: {cambio['archivo']}\n")
                        archivo.write(f"   Timestamp: {cambio['timestamp']}\n")
                        
                        if "hash_anterior" in cambio:
                            archivo.write(f"   Hash anterior: {cambio['hash_anterior'][:16]}...\n")
                            archivo.write(f"   Hash actual: {cambio['hash_actual'][:16]}...\n")
                else:
                    archivo.write("✅ No se detectaron cambios\n")
                
                archivo.write("\n" + "=" * 70 + "\n")
            
            print(f"✅ Reporte generado: {archivo_salida}")
            return True
        except Exception as e:
            print(f"❌ Error al generar reporte: {e}")
            return False

# Ejemplo de uso
def main():
    print("🛡️ Monitor de Integridad de Archivos\n")
    
    monitor = MonitorIntegridad()
    
    # Opción 1: Crear nuevo baseline
    print("1. Crear nuevo baseline")
    print("2. Verificar integridad")
    opcion = input("\nSeleccione opción: ").strip()
    
    if opcion == "1":
        directorios = input("Directorios a monitorear (separados por coma): ").split(",")
        directorios = [d.strip() for d in directorios]
        monitor.crear_baseline(directorios)
    
    elif opcion == "2":
        if monitor.cargar_baseline():
            cambios = monitor.verificar_integridad()
            
            if cambios:
                print("\n⚠️ ALERTAS DE INTEGRIDAD:")
                for cambio in cambios:
                    alerta = monitor.generar_alerta(cambio)
                    print(f"[{alerta['severidad']}] {cambio['tipo_cambio']}: {cambio['archivo']}")
            else:
                print("\n✅ No se detectaron cambios en la integridad")
            
            monitor.generar_reporte()

if __name__ == "__main__":
    main()
```

---

## 📋 Mejores Prácticas

### 1. Escritura de Código Limpio

```python
# ❌ MAL - Código difícil de leer
def p(d):
    r=[]
    for i in d:
        if i['s']=='h':r.append(i)
    return r

# ✅ BIEN - Código claro y documentado
def filtrar_eventos_alta_severidad(eventos):
    """
    Filtra eventos con severidad alta.
    
    Args:
        eventos (list): Lista de eventos a filtrar
        
    Returns:
        list: Eventos con severidad alta
    """
    eventos_criticos = []
    for evento in eventos:
        if evento['severidad'] == 'alta':
            eventos_criticos.append(evento)
    return eventos_criticos

# Aún mejor - usando list comprehension
def filtrar_eventos_alta_severidad(eventos):
    """Filtra eventos con severidad alta."""
    return [e for e in eventos if e['severidad'] == 'alta']
```

### 2. Manejo de Recursos

```python
# ❌ MAL - No cierra recursos
def leer_archivo_mal(nombre):
    archivo = open(nombre, "r")
    datos = archivo.read()
    return datos  # archivo nunca se cierra

# ✅ BIEN - Usa context manager
def leer_archivo_bien(nombre):
    """Lee archivo usando context manager."""
    with open(nombre, "r") as archivo:
        return archivo.read()
    # archivo se cierra automáticamente

# Para múltiples archivos
def copiar_archivo_seguro(origen, destino):
    """Copia archivo de forma segura."""
    try:
        with open(origen, "r") as fuente:
            with open(destino, "w") as destino_archivo:
                destino_archivo.write(fuente.read())
        return True
    except Exception as e:
        print(f"Error: {e}")
        return False
```

### 3. Validación de Entrada

```python
def procesar_puerto_seguro(puerto_str):
    """
    Procesa y valida número de puerto.
    
    Args:
        puerto_str: String con número de puerto
        
    Returns:
        int: Puerto validado o None si es inválido
    """
    try:
        # Convertir a entero
        puerto = int(puerto_str)
        
        # Validar rango
        if 1 <= puerto <= 65535:
            return puerto
        else:
            print(f"Error: Puerto {puerto} fuera de rango válido (1-65535)")
            return None
    
    except ValueError:
        print(f"Error: '{puerto_str}' no es un número válido")
        return None
    except Exception as e:
        print(f"Error inesperado: {e}")
        return None

# Uso
puerto = procesar_puerto_seguro(input("Ingrese puerto: "))
if puerto:
    print(f"Puerto válido: {puerto}")
```

### 4. Documentación Efectiva

```python
def analizar_trafico_red(paquetes, filtro=None, incluir_metadata=True):
    """
    Analiza tráfico de red y genera estadísticas.
    
    Esta función procesa una lista de paquetes de red y genera
    estadísticas detalladas sobre el tráfico. Puede aplicar filtros
    opcionales para analizar solo ciertos tipos de paquetes.
    
    Args:
        paquetes (list): Lista de diccionarios con información de paquetes
        filtro (dict, optional): Criterios de filtrado. Ejemplo:
            {'protocolo': 'TCP', 'puerto': 80}
        incluir_metadata (bool, optional): Si incluir metadata adicional.
            Por defecto True.
    
    Returns:
        dict: Diccionario con estadísticas del análisis:
            {
                'total_paquetes': int,
                'protocolos': dict,
                'puertos_comunes': list,
                'metadata': dict (si incluir_metadata=True)
            }
    
    Raises:
        ValueError: Si paquetes está vacío o tiene formato inválido
        TypeError: Si paquetes no es una lista
    
    Example:
        >>> paquetes = [
        ...     {'protocolo': 'TCP', 'puerto': 80, 'tamano': 1500},
        ...     {'protocolo': 'UDP', 'puerto': 53, 'tamano': 512}
        ... ]
        >>> resultado = analizar_trafico_red(paquetes)
        >>> print(resultado['total_paquetes'])
        2
    
    Note:
        Esta función puede ser intensiva en recursos para grandes
        volúmenes de tráfico. Considere procesar en lotes.
    """
    # Implementación aquí
    pass
```


### 6. Manejo de Configuración

```python
import json

class ConfiguracionSeguridad:
    """Gestiona configuración de la aplicación."""
    
    def __init__(self, archivo_config="config.json"):
        self.archivo_config = archivo_config
        self.config = self.cargar_configuracion()
    
    def cargar_configuracion(self):
        """Carga configuración con valores por defecto."""
        config_default = {
            "max_intentos_login": 3,
            "timeout_sesion": 1800,
            "nivel_log": "INFO",
            "directorio_logs": "./logs",
            "puertos_monitoreados": [22, 80, 443],
            "alertas_email": True,
            "email_admin": "admin@empresa.com"
        }
        
        try:
            with open(self.archivo_config, "r") as archivo:
                config_usuario = json.load(archivo)
                # Combinar con defaults
                config_default.update(config_usuario)
                return config_default
        except FileNotFoundError:
            print("⚠️ Archivo de configuración no encontrado, usando valores por defecto")
            self.guardar_configuracion(config_default)
            return config_default
        except json.JSONDecodeError:
            print("❌ Error al leer configuración, usando valores por defecto")
            return config_default
    
    def guardar_configuracion(self, config=None):
        """Guarda configuración actual."""
        if config is None:
            config = self.config
        
        try:
            with open(self.archivo_config, "w") as archivo:
                json.dump(config, archivo, indent=4)
            return True
        except Exception as e:
            print(f"Error al guardar configuración: {e}")
            return False
    
    def get(self, clave, default=None):
        """Obtiene valor de configuración."""
        return self.config.get(clave, default)
    
    def set(self, clave, valor):
        """Establece valor de configuración."""
        self.config[clave] = valor
        self.guardar_configuracion()

# Uso
config = ConfiguracionSeguridad()
max_intentos = config.get("max_intentos_login")
print(f"Máximo de intentos: {max_intentos}")
```

---

## 🎯 Ejercicios Finales

### Ejercicio 1: Analizador de Headers HTTP

```python
"""
Crea un programa que lea un archivo con headers HTTP
y detecte problemas de seguridad.
"""

def analizar_headers_http(archivo_headers):
    """
    Analiza headers HTTP buscando problemas de seguridad.
    
    El archivo debe contener headers en formato:
    Header-Name: valor
    """
    headers_seguros_requeridos = [
        "Strict-Transport-Security",
        "X-Content-Type-Options",
        "X-Frame-Options",
        "Content-Security-Policy"
    ]
    
    headers_evitar = [
        "Server",  # Revela información del servidor
        "X-Powered-By"  # Revela tecnología
    ]
    
    try:
        with open(archivo_headers, "r") as archivo:
            headers_encontrados = {}
            
            for linea in archivo:
                if ":" in linea:
                    nombre, valor = linea.split(":", 1)
                    headers_encontrados[nombre.strip()] = valor.strip()
        
        # Análisis
        problemas = []
        recomendaciones = []
        
        # Verificar headers de seguridad
        for header in headers_seguros_requeridos:
            if header not in headers_encontrados:
                problemas.append(f"Falta header de seguridad: {header}")
        
        # Verificar headers problemáticos
        for header in headers_evitar:
            if header in headers_encontrados:
                problemas.append(f"Header revela información: {header}")
                recomendaciones.append(f"Eliminar o modificar: {header}")
        
        # Generar reporte
        print("=" * 60)
        print("ANÁLISIS DE HEADERS HTTP")
        print("=" * 60)
        print(f"\nHeaders encontrados: {len(headers_encontrados)}")
        print(f"Problemas detectados: {len(problemas)}\n")
        
        if problemas:
            print("🚨 PROBLEMAS:")
            for problema in problemas:
                print(f"  - {problema}")
        
        if recomendaciones:
            print("\n💡 RECOMENDACIONES:")
            for rec in recomendaciones:
                print(f"  - {rec}")
        
        if not problemas:
            print("✅ No se detectaron problemas de seguridad")
        
        return {
            "headers": headers_encontrados,
            "problemas": problemas,
            "recomendaciones": recomendaciones
        }
    
    except FileNotFoundError:
        print(f"Error: Archivo {archivo_headers} no encontrado")
        return None
    except Exception as e:
        print(f"Error: {e}")
        return None

# Prueba
# analizar_headers_http("headers.txt")
```

### Ejercicio 2: Sistema de Respaldo Automático

```python
"""
Crea un sistema que haga respaldo automático de archivos críticos.
"""

import os
import shutil
from datetime import datetime

class SistemaRespaldo:
    def __init__(self, directorio_respaldo="backups"):
        self.directorio_respaldo = directorio_respaldo
        self.crear_directorio_respaldo()
    
    def crear_directorio_respaldo(self):
        """Crea directorio para respaldos si no existe."""
        if not os.path.exists(self.directorio_respaldo):
            os.makedirs(self.directorio_respaldo)
            print(f"✅ Directorio de respaldo creado: {self.directorio_respaldo}")
    
    def respaldar_archivo(self, ruta_origen):
        """Crea respaldo de un archivo individual."""
        try:
            if not os.path.exists(ruta_origen):
                print(f"❌ Archivo no encontrado: {ruta_origen}")
                return False
            
            # Generar nombre de respaldo con timestamp
            nombre_base = os.path.basename(ruta_origen)
            timestamp = datetime.now().strftime("%Y%m%d_%H%M%S")
            nombre_respaldo = f"{timestamp}_{nombre_base}"
            ruta_respaldo = os.path.join(self.directorio_respaldo, nombre_respaldo)
            
            # Copiar archivo
            shutil.copy2(ruta_origen, ruta_respaldo)
            print(f"✅ Respaldo creado: {nombre_respaldo}")
            return True
        
        except Exception as e:
            print(f"❌ Error al respaldar {ruta_origen}: {e}")
            return False
    
    def respaldar_directorio(self, ruta_directorio, extensiones=None):
        """
        Respalda todos los archivos de un directorio.
        
        Args:
            ruta_directorio: Directorio a respaldar
            extensiones: Lista de extensiones a respaldar (ej: ['.txt', '.log'])
                        Si es None, respalda todos los archivos
        """
        if not os.path.exists(ruta_directorio):
            print(f"❌ Directorio no encontrado: {ruta_directorio}")
            return
        
        archivos_respaldados = 0
        
        for raiz, dirs, archivos in os.walk(ruta_directorio):
            for archivo in archivos:
                ruta_completa = os.path.join(raiz, archivo)
                
                # Filtrar por extensión si se especificó
                if extensiones:
                    if not any(archivo.endswith(ext) for ext in extensiones):
                        continue
                
                if self.respaldar_archivo(ruta_completa):
                    archivos_respaldados += 1
        
        print(f"\n📦 Total de archivos respaldados: {archivos_respaldados}")
    
    def listar_respaldos(self):
        """Lista todos los respaldos disponibles."""
        try:
            respaldos = os.listdir(self.directorio_respaldo)
            respaldos.sort(reverse=True)  # Más recientes primero
            
            print(f"\n📋 Respaldos disponibles ({len(respaldos)}):")
            for respaldo in respaldos:
                ruta = os.path.join(self.directorio_respaldo, respaldo)
                tamano = os.path.getsize(ruta)
                print(f"  • {respaldo} ({tamano} bytes)")
            
            return respaldos
        
        except Exception as e:
            print(f"Error al listar respaldos: {e}")
            return []
    
    def restaurar_respaldo(self, nombre_respaldo, ruta_destino):
        """Restaura un respaldo a la ubicación especificada."""
        try:
            ruta_respaldo = os.path.join(self.directorio_respaldo, nombre_respaldo)
            
            if not os.path.exists(ruta_respaldo):
                print(f"❌ Respaldo no encontrado: {nombre_respaldo}")
                return False
            
            shutil.copy2(ruta_respaldo, ruta_destino)
            print(f"✅ Respaldo restaurado a: {ruta_destino}")
            return True
        
        except Exception as e:
            print(f"❌ Error al restaurar: {e}")
            return False
    
    def limpiar_respaldos_antiguos(self, dias=30):
        """Elimina respaldos más antiguos que X días."""
        import time
        
        tiempo_limite = time.time() - (dias * 24 * 60 * 60)
        eliminados = 0
        
        try:
            for respaldo in os.listdir(self.directorio_respaldo):
                ruta = os.path.join(self.directorio_respaldo, respaldo)
                if os.path.getmtime(ruta) < tiempo_limite:
                    os.remove(ruta)
                    eliminados += 1
            
            print(f"🗑️ Respaldos eliminados: {eliminados}")
            return eliminados
        
        except Exception as e:
            print(f"Error al limpiar respaldos: {e}")
            return 0

# Ejemplo de uso
def main():
    sistema = SistemaRespaldo()
    
    print("🛡️ Sistema de Respaldo Automático\n")
    print("1. Respaldar archivo")
    print("2. Respaldar directorio")
    print("3. Listar respaldos")
    print("4. Restaurar respaldo")
    print("5. Limpiar respaldos antiguos")
    
    opcion = input("\nSeleccione opción: ").strip()
    
    if opcion == "1":
        archivo = input("Ruta del archivo: ").strip()
        sistema.respaldar_archivo(archivo)
    
    elif opcion == "2":
        directorio = input("Ruta del directorio: ").strip()
        extensiones = input("Extensiones (ej: .txt,.log) o Enter para todas: ").strip()
        
        if extensiones:
            ext_lista = [e.strip() for e in extensiones.split(",")]
            sistema.respaldar_directorio(directorio, ext_lista)
        else:
            sistema.respaldar_directorio(directorio)
    
    elif opcion == "3":
        sistema.listar_respaldos()
    
    elif opcion == "4":
        respaldos = sistema.listar_respaldos()
        if respaldos:
            nombre = input("\nNombre del respaldo a restaurar: ").strip()
            destino = input("Ruta de destino: ").strip()
            sistema.restaurar_respaldo(nombre, destino)
    
    elif opcion == "5":
        dias = input("Eliminar respaldos más antiguos que (días): ").strip()
        sistema.limpiar_respaldos_antiguos(int(dias))

if __name__ == "__main__":
    main()
```

---

## 📚 Recursos Adicionales

### Documentación Oficial

- [Python File I/O](https://docs.python.org/3/tutorial/inputoutput.html#reading-and-writing-files)
- [Python Exception Handling](https://docs.python.org/3/tutorial/errors.html)
- [Python Modules](https://docs.python.org/3/tutorial/modules.html)
- [Python Standard Library](https://docs.python.org/3/library/index.html)

### Librerías Útiles para Seguridad

- **hashlib**: Funciones hash criptográficas
- **secrets**: Generación segura de números aleatorios
- **ssl**: Soporte para TLS/SSL
- **cryptography**: Criptografía moderna
- **paramiko**: Protocolo SSH2
- **scapy**: Manipulación de paquetes de red
- **requests**: Cliente HTTP
- **beautifulsoup4**: Parsing de HTML/XML

### Herramientas de Desarrollo

- **pylint**: Análisis estático de código
- **black**: Formateador de código
- **pytest**: Framework de testing
- **ipython**: Shell interactivo mejorado
- **virtualenv**: Entornos virtuales

### Lecturas Recomendadas

- "Automate the Boring Stuff with Python" - Al Sweigart
- "Python for Cybersecurity" - Howard E. Poston III
- "Violent Python" - TJ O'Connor
- "Black Hat Python" - Justin Seitz

---

## ✅ Checklist de Competencias

Antes de finalizar el curso, asegúrate de poder:

- [ ] Leer y escribir archivos en diferentes formatos (TXT, CSV, JSON)
- [ ] Implementar manejo robusto de excepciones
- [ ] Usar context managers (with statement)
- [ ] Depurar código efectivamente
- [ ] Crear y usar módulos personalizados
- [ ] Importar y usar librerías externas
- [ ] Trabajar con rutas de archivos y directorios
- [ ] Calcular hashes de archivos
- [ ] Registrar eventos en logs
- [ ] Generar reportes automáticos
- [ ] Validar y sanitizar entradas
- [ ] Aplicar mejores prácticas de programación
- [ ] Crear scripts de automatización completos
- [ ] Documentar código adecuadamente

---

## 🎓 Proyecto Final Integrador

### Sistema Integral de Seguridad

Desarrolla un sistema que integre todos los conceptos aprendidos:

**Requisitos:**
1. Lectura y procesamiento de múltiples archivos de log
2. Detección de patrones maliciosos
3. Gestión de listas de control de acceso
4. Generación de reportes en múltiples formatos
5. Manejo robusto de errores
6. Logging de eventos
7. Interfaz de línea de comandos
8. Configuración mediante archivo JSON
9. Documentación completa

**Entregables:**
- Código fuente documentado
- Manual de usuario
- Ejemplos de archivos de entrada
- Reportes de ejemplo
- README con instrucciones de instalación

---
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/eaed8a4d-f91d-449e-be17-d6d653a80f2e" />

---

## 📄 Licencia

Este proyecto está bajo la Licencia MIT - ver el archivo [LICENSE](LICENSE) para más detalles.

---

## 🙏 Agradecimientos

- **Google Cybersecurity Professional Certificate**
- **Coursera Platform**
- Comunidad de Python
- Comunidad de Ciberseguridad

---

## 📝 Notas Finales

Este módulo completa el curso "Automatizar Tareas de Seguridad Cibernética con Python". Has aprendido a:

- Escribir código Python eficaz y eficiente
- Trabajar con estructuras de datos fundamentales
- Manipular archivos y procesar información
- Manejar errores de forma robusta
- Aplicar Python a problemas reales de ciberseguridad
- Desarrollar herramientas de automatización completas

**¡Felicitaciones por completar el curso!** 🎉

Ahora estás preparado para:
- Automatizar tareas de seguridad en tu organización
- Desarrollar herramientas personalizadas de análisis
- Procesar y analizar grandes volúmenes de datos de seguridad
- Contribuir a proyectos de código abierto relacionados con ciberseguridad

---

**Última actualización:** Octubre 2024

⭐ Si este writeup te fue útil, no olvides darle una estrella al repositorio!

**#Cybersecurity #Python #Automation #FileHandling #ExceptionHandling #InfoSec #PracticalPython**
