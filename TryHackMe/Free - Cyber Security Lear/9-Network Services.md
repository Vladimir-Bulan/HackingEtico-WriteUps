# 🌐 TryHackMe – Network Services

> Sala del camino *Cyber Defense* en [TryHackMe](https://tryhackme.com/room/networkservices)

---

##  Descripción

Esta sala enseña a explorar y explotar servicios de red comunes utilizando técnicas de enumeración y herramientas forenses. Los servicios incluyen **SMB**, **Telnet** y **FTP**, profundizando en su comprensión, escaneo, autenticación y explotación. :contentReference[oaicite:1]{index=1}

---

##  Contenido y preguntas con respuestas

###  Tarea 2 – Understanding SMB

1. **¿Qué significa SMB?**  
   `Server Message Block`

2. **¿Qué tipo de protocolo es?**  
   `response-request`

3. **¿Qué usan los clientes para conectarse a servidores?**  
   `TCP/IP`

4. **¿En qué sistemas funciona Samba?**  
   `Unix` :contentReference[oaicite:2]{index=2}

---

###  Tarea 3 – Enumerating SMB

1. **¿Cuántos puertos están abiertos?**  
   `3` (22, 139, 445)

2. **¿En qué puertos funciona SMB?**  
   `139/445`

3. **¿Cuál es el nombre del workgroup?**  
   `WORKGROUP`

4. **¿Cuál es el nombre del host detectado?**  
   `POLOSMB`

5. **¿Qué versión del sistema operativo corre?**  
   `6.1`

6. **¿Qué recurso compartido llama la atención?**  
   `profiles` :contentReference[oaicite:3]{index=3}

---

###  Tarea 4 – Exploiting SMB

1. **¿Cuál es la sintaxis para acceder a `secret` como usuario `suit` por el puerto 445?**  
smbclient //10.10.10.2/secret -U suit -p 445

2. **¿Permite acceso anónimo?**  
`Y` (sí)

3. **¿A quién pertenece la carpeta `profiles`?**  
`John Cactus`

4. **¿Qué servicio le permite trabajar desde casa?**  
`ssh`

5. **¿En qué directorio buscar llaves SSH?**  
`.ssh`

6. **¿Cuál es la llave SSH más útil?**  
`id_rsa`

7. **¿Cuál es la bandera smb.txt?**  
`THM{smb_is_fun_eh?}` :contentReference[oaicite:4]{index=4}

---

###  Tarea 5 – Understanding Telnet

1. **¿Qué es Telnet?**  
`application protocol`

2. **¿Qué lo reemplaza lentamente?**  
`ssh`

3. **¿Cómo conectarse a un servidor Telnet (IP 10.10.10.3)?**  
```bash
telnet 10.10.10.3 23


![image](https://github.com/user-attachments/assets/04dbb7ef-15e5-4364-8c3b-7effadeb1e7b)

