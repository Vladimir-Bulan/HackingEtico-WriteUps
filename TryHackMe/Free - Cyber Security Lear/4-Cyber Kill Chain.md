# 🧠 TryHackMe: Cyber Kill Chain (ZMT)

> URL del room: [Cyber Kill Chain — TryHackMe](https://tryhackme.com/room/cyberkillchainzmt)

##  Descripción

Este laboratorio se enfoca en el modelo de la **Cyber Kill Chain** desarrollado por Lockheed Martin. Aprenderás cómo se estructura un ataque cibernético en diferentes fases, y cómo se puede detectar, prevenir o interrumpir un ataque en cada una de ellas.

---

##  Objetivos del Room

- Comprender las 7 fases de la Cyber Kill Chain.
- Identificar técnicas de ataque asociadas a cada fase.
- Aplicar el conocimiento a un caso real (el ataque a Target en 2013).

---

##  Preguntas y Respuestas por Actividad

###  Task 1: Introducción
_No contiene preguntas._

---

###  Task 2: **Reconocimiento (Reconnaissance)**  
> **P1:** ¿Cuál es el objetivo de esta fase?  
**R1:** Obtener información

---

###  Task 3: **Armar el arma (Weaponization)**  
> **P1:** ¿Qué se crea durante esta fase?  
**R1:** Carga útil (Payload)

---

###  Task 4: **Entrega (Delivery)**  
> **P1:** ¿Cuál es el método de entrega más común?  
**R1:** Correo electrónico

---

###  Task 5: **Explotación (Exploitation)**  
> **P1:** ¿Qué se explota en esta fase?  
**R1:** Vulnerabilidad

---

###  Task 6: **Instalación (Installation)**  
> **P1:** ¿Qué se instala durante esta fase?  
**R1:** Malware

---

###  Task 7: **Comando y Control (Command & Control)**  
> **P1:** ¿Cuál es el propósito de esta fase?  
**R1:** Controlar remotamente el sistema

---

###  Task 8: **Acciones sobre los Objetivos (Actions on Objectives)**  
> **P1:** ¿Qué es lo que normalmente buscan los atacantes?  
**R1:** Datos

---

###  Task 9: Aplicar lo aprendido – Caso real: Ataque a Target

####  Escenario:
Analizar el ataque cibernético a Target (2013), que comprometió la información de más de 40 millones de tarjetas.

####  Técnicas y fases de la Kill Chain:

| Fase                           | Técnica utilizada                   |
|--------------------------------|-------------------------------------|
| **Weaponization**              | `powershell`                        |
| **Delivery**                   | `spearphishing attachment`          |
| **Exploitation**               | `exploit public-facing application` |
| **Installation**               | `dynamic linker hijacking`          |
| **Command and Control (C2)**   | `fallback channels`                 |
| **Actions on Objectives**      | `data from local system`            |

> **Flag obtenido al finalizar la práctica:**  
 `THM{7HR347_1N73L_12_4w35om3}`

---

##  Conclusión

Este laboratorio ayuda a entender cómo se desarrollan los ataques dirigidos paso a paso. Aplicar el modelo de la **Cyber Kill Chain** permite a los analistas de ciberseguridad identificar y frenar amenazas en diferentes etapas del ciclo del ataque.

---

##  Recursos complementarios

- [MITRE ATT&CK - TA0011: Command and Control](https://attack.mitre.org/tactics/TA0011/)
- [Comunicado oficial de Target](https://corporate.target.com/news-features/article/2013/12/important-notice-unauthorized-access-to-payment-ca)
- [Acuerdo judicial del caso Target (Oficina del Fiscal General)](https://www.attorneygeneral.gov/taking-action/settlement-reached-with-target-following-major-consumer-data-breach/)

---
![image](https://github.com/user-attachments/assets/719c25e0-9026-41db-ac08-147e67ccbe15)

