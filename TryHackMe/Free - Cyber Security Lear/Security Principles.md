# 🔐 TryHackMe - Principios de Seguridad (Security Principles)

>  Sala del camino de aprendizaje **Pre Security** en [TryHackMe](https://tryhackme.com/room/securityprinciples)

---

##  Descripción de la sala

La sala **Security Principles** introduce los fundamentos de la seguridad de la información, incluyendo:

- La tríada **CIA** (Confidencialidad, Integridad y Disponibilidad)
- El modelo **DAD** (Divulgación, Alteración y Destrucción)
- Modelos de seguridad como **Bell-LaPadula** y **Biba**
- Conceptos de gestión de privilegios: **PIM** y **PAM**
- Modelos de amenazas como **STRIDE**
- Principios de diseño de seguridad según la norma **ISO/IEC 19249**

---

## 🧪 Preguntas y Respuestas

###  Tarea 2: La Tríada CIA

1. **¿Qué elemento de la tríada CIA asegura que los datos no puedan ser alterados por personas no autorizadas?**  
   `integrity`

2. **¿Qué elemento de la tríada CIA asegura que los datos estén disponibles?**  
   `availability`

3. **¿Qué elemento de la tríada CIA asegura que los datos solo sean accedidos por personas autorizadas?**  
   `confidentiality`

4. **¿Cuál es la bandera que obtuviste al final?**  
   `THM{CIA_TRIAD}`

---

###  Tarea 3: DAD

1. **El atacante logró acceder a los registros de clientes y los publicó en línea. ¿Qué tipo de ataque es este?**  
   `Disclosure`

2. **Un grupo de atacantes localizó tanto el sistema de alimentación principal como el de respaldo y los apagó. Como resultado, toda la red se cayó. ¿Qué tipo de ataque es este?**  
   `Destruction/Denial`

---

###  Tarea 4: Conceptos Fundamentales de los Modelos de Seguridad

1. **¿Qué modelo dicta "no leer hacia abajo"?**  
   `Biba`

2. **¿Qué modelo establece "no leer hacia arriba"?**  
   `Bell-LaPadula Model`

3. **¿Qué modelo enseña "no escribir hacia abajo"?**  
   `Bell-LaPadula Model`

4. **¿Qué modelo impone "no escribir hacia arriba"?**  
   `Biba`

5. **¿Cuál es la bandera que obtuviste al final?**  
   `THM{SECURITY_MODELS}`

---

###  Tarea 5: Modelado de Amenazas e Incidentes

1. **¿Qué modelo describe "Suplantación"?**  
   `STRIDE`

2. **¿Qué significa la sigla "IR"?**  
   `Incident Response`

3. **Se te asignó la tarea de agregar algunas medidas a una aplicación para mejorar la integridad de los datos. ¿Qué principio de STRIDE es este?**  
   `Tampering`

4. **Un atacante ha penetrado la seguridad de tu organización y robado datos. Tu tarea es devolver a la organización a su estado normal. ¿Qué etapa de respuesta a incidentes es esta?**  
   `Recovery`

---

###  Tarea 6: ISO/IEC 19249

1. **¿Qué principio estás aplicando cuando apagas un servidor inseguro que no es crítico para el negocio?**  
   `2`

2. **Tu empresa contrató a un nuevo representante de ventas. ¿Qué principio están aplicando cuando te dicen que le des acceso solo a los productos y precios de la empresa?**  
   `1`

3. **Mientras lees el código de un cajero automático, notas una gran cantidad de código para manejar situaciones inesperadas como desconexión de red y fallos de energía. ¿Qué principio están aplicando?**  
   `5`

---


