# 📘 Módulo 4 – Detection & Response (Curso: Detection and Response, Coursera)

## 1. Introducción

El Módulo 4 del curso “Detection and Response” explora los mecanismos, técnicas y herramientas clave utilizadas para **detectar amenazas** y **responder ante incidentes de seguridad en sistemas informáticos**. Se profundiza en cómo se estructura un sistema de detección, cómo se manejan alertas, y cuáles son los mejores procedimientos de respuesta.

---

## 2. Objetivos del módulo

Al finalizar este módulo, el estudiante podrá:

- Comprender los principios y componentes de un sistema de detección (IDS/IPS, monitorización, alertas).  
- Analizar métodos para correlacionar eventos y reducir falsos positivos.  
- Planificar una estrategia de respuesta a incidentes, con roles, procesos y pasos.  
- Familiarizarse con herramientas y tecnologías utilizadas en detección y respuesta.

---

## 3. Contenidos principales

### 3.1 Arquitectura de detección

- Componentes de un sistema de detección (sensores, colectores, correladores, console).  
- Ubicación de sensores: en red, host-based, híbridos.  
- En qué punto del flujo de datos se sitúan los mecanismos de detección.

### 3.2 Generación y gestión de alertas

- Qué es una alerta y cómo se produce una señal relevante.  
- Procesamiento y priorización de alertas.  
- Técnicas de correlación entre eventos para reducir ruido (filtros, reglas, agregación).  
- Clasificación y escalamiento de alertas.

### 3.3 Respuesta a incidentes

- Proceso típico de respuesta (identificación, contención, erradicación, recuperación).  
- Roles y responsabilidades (analistas, equipo forense, gestión).  
- Herramientas de apoyo (SIEM, SOAR, playbooks).  
- Comunicación interna y externa durante incidentes.

### 3.4 Retorno de la experiencia

- Registro y documentación del incidente.  
- Lecciones aprendidas y ajustes al sistema de detección.  
- Mejora continua del ciclo de detección-respuesta.

---

## 4. Casos de uso y ejemplos

- Ejemplo de correlación: múltiples alertas de acceso fallido + tráfico inusual → posible ataque de fuerza bruta.  
- Uso de playbooks automatizados para responder ante detección de malware: aislamiento de máquina, eliminación de artefactos, análisis post mortem.  
- Integración de un SIEM con fuentes de datos como logs de red, endpoint, sistema operativo.

---

## 5. Reflexiones y buenas prácticas

- La clave está en balancear **sensibilidad vs ruido**: un sistema demasiado generoso dispara muchas falsas alarmas, demasiado estricto puede perder ataques reales.  
- Tener un plan de respuesta bien definido **antes** de que ocurra un incidente.  
- Automatizar los pasos repetitivos cuando sea seguro hacerlo, pero dejando margen para intervención humana.  
- La documentación y el feedback posterior al incidente son esenciales para mejorar el sistema continuamente.

---

## 6. Recursos adicionales sugeridos

- Lecturas sobre sistemas de detección y respuesta (IDS/IPS, SIEM, SOAR).  
- Herramientas populares como **Splunk**, **ELK Stack**, **TheHive / Cortex**, **Security Onion**.  
- Normas y marcos de trabajo para respuesta a incidentes (por ejemplo, el estándar **NIST SP 800-61**).  
- Estudios de caso de incidentes reales (brechas, ataques APTs, ransomware).

---

