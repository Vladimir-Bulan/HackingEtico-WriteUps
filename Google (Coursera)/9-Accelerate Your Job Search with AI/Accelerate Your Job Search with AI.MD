# 📘 Writeups: Acelere su Búsqueda de Empleo con IA

## Accelerate Your Job Search with AI - Google Career Certificates

[![Google](https://img.shields.io/badge/Google-Career_Certificate-4285F4.svg)](https://www.coursera.org/)
[![Coursera](https://img.shields.io/badge/Coursera-Online_Course-0056D2.svg)](https://www.coursera.org/)
[![AI](https://img.shields.io/badge/AI-Powered-success.svg)](https://www.coursera.org/)

---

## 📚 Índice de Módulos

- [Semana 1: Descubra sus Habilidades con IA](#semana-1-descubra-sus-habilidades-con-ia)
- [Semana 2: Optimice su Búsqueda con IA](#semana-2-optimice-su-búsqueda-con-ia)
- [Semana 3: Gestione Aplicaciones con IA](#semana-3-gestione-aplicaciones-con-ia)
- [Semana 4: Prepare Entrevistas con IA](#semana-4-prepare-entrevistas-con-ia)

---

# Semana 1: Descubra sus Habilidades con IA

## 🎯 Objetivos
- Usar IA para identificar habilidades transferibles
- Crear declaración de identidad profesional
- Explorar nuevas posibilidades de carrera
- Construir fundamentos para búsqueda de empleo

## 🤖 Herramientas Principales

### Google Gemini
**Para qué sirve:**
- Análisis de experiencia laboral
- Identificación de habilidades
- Generación de ideas de carrera
- Brainstorming profesional

### Google NotebookLM
**Para qué sirve:**
- Organizar información de carrera
- Analizar ofertas de trabajo
- Crear resúmenes personalizados
- Investigación de empresas

## 💡 Descubrir Habilidades Transferibles

### Prompt para Gemini

```
"Analiza mi experiencia laboral y educativa para identificar 
habilidades transferibles:

EXPERIENCIA:
- [Puesto anterior 1]: [Responsabilidades]
- [Puesto anterior 2]: [Responsabilidades]
- [Proyectos personales]: [Descripción]

EDUCACIÓN:
- [Título/Certificación]
- [Cursos relevantes]

Por favor identifica:
1. Habilidades técnicas (hard skills)
2. Habilidades blandas (soft skills)
3. Competencias transferibles a [industria objetivo]
4. Fortalezas únicas
5. Áreas de desarrollo recomendadas"
```

### Ejemplo de Output

```markdown
HABILIDADES TÉCNICAS:
✅ Python (intermedio)
✅ Análisis de datos con Excel
✅ SQL básico
✅ Herramientas SIEM (Splunk)
✅ Linux command line

HABILIDADES BLANDAS:
✅ Resolución de problemas
✅ Comunicación técnica
✅ Trabajo en equipo
✅ Atención al detalle
✅ Adaptabilidad

TRANSFERIBLES A CIBERSEGURIDAD:
→ Análisis de logs → Security Analyst
→ Troubleshooting → SOC Analyst
→ Documentación → Security Documentation
→ Python scripting → Security Automation
```

## 🎭 Crear Career Identity Statement

### Qué es
Una declaración concisa (2-3 líneas) que resume:
- Quién eres profesionalmente
- Qué haces mejor
- Qué valor aportas
- Hacia dónde vas

### Template con IA

**Prompt:**
```
"Ayúdame a crear mi Career Identity Statement.

Información:
- Experiencia: [Años y roles]
- Certificaciones: [Lista]
- Fortalezas: [Top 3]
- Objetivo: [Rol deseado]
- Industria: [Sector objetivo]

Formato: 2-3 oraciones poderosas y memorables"
```

**Ejemplos:**

```
❌ DÉBIL:
"Busco trabajo en ciberseguridad porque me gusta la tecnología."

✅ FUERTE:
"Security Analyst certificado con pasión por proteger datos 
críticos. Especializado en análisis de amenazas y respuesta 
a incidentes con Python. Busco aplicar habilidades técnicas 
y analíticas en SOC de empresa innovadora."
```

### Componentes Clave

```
[IDENTIDAD PROFESIONAL] + [ESPECIALIZACIÓN] + [VALOR ÚNICO] + [OBJETIVO]

Ejemplo:
"Analista de seguridad certificado" + 
"especializado en threat hunting" + 
"con habilidad para automatizar detección" + 
"buscando rol en equipo blue team enterprise"
```

## 🔍 Explorar Nuevas Carreras

### Prompt de Exploración

```
"Basándome en mi perfil:
- Habilidades: [Lista]
- Intereses: [Lista]
- Valores: [Lo que es importante para ti]

¿Qué roles en ciberseguridad serían adecuados?
Para cada rol sugiere:
1. Título del puesto
2. Responsabilidades principales
3. Habilidades requeridas (tengo vs. necesito)
4. Rango salarial promedio
5. Demanda laboral
6. Pasos para calificar"
```

### Matriz de Roles Sugeridos

```
ROL: Security Analyst
├─ Match: 85%
├─ Tienes: Python, Análisis, SIEM
├─ Necesitas: Más experiencia con IDS/IPS
├─ Salario: $60K-$85K
└─ Demanda: Alta (↑ 20% anual)

ROL: SOC Analyst (Tier 1)
├─ Match: 90%
├─ Tienes: Troubleshooting, Logs, Alertas
├─ Necesitas: Certificación básica
├─ Salario: $55K-$75K
└─ Demanda: Muy Alta (Entry-friendly)

ROL: Cybersecurity Specialist
├─ Match: 70%
├─ Tienes: Fundamentos técnicos
├─ Necesitas: 1-2 años experiencia
├─ Salario: $70K-$95K
└─ Demanda: Alta (requiere más skills)
```

## 📊 Autoevaluación Asistida por IA

### Skills Gap Analysis

**Prompt:**
```
"Compara mi perfil con los requisitos de [rol objetivo]:

MI PERFIL:
[Habilidades actuales]

REQUISITOS DEL ROL:
[Copia de descripción de trabajo]

Genera:
1. Skills que ya tengo ✅
2. Skills que puedo desarrollar rápido (1-3 meses) 🟡
3. Skills que requieren tiempo (3-6 meses) 🟠
4. Plan de acción priorizado
5. Recursos de aprendizaje recomendados"
```

### Output Esperado

```
✅ TENGO (LISTO):
- Networking fundamentals
- Python scripting
- Log analysis
- Problem-solving
- Google Cybersecurity Certificate

🟡 DESARROLLAR RÁPIDO (1-3 MESES):
- Wireshark avanzado
- → Recurso: Wireshark 101 (Udemy)
- SIEM específico (Splunk)
- → Recurso: Splunk Fundamentals (gratis)
- Linux hardening
- → Recurso: OverTheWire wargames

🟠 REQUIERE TIEMPO (3-6 MESES):
- CompTIA Security+
- → Plan: Estudiar 10h/semana
- Experiencia práctica
- → Plan: HackTheBox, TryHackMe
- Incident response
- → Plan: Labs + Documentación

PLAN PRIORIZADO:
Mes 1: Wireshark + Splunk
Mes 2: Linux + Práctica CTF
Mes 3: Security+ prep
Mes 4-5: Security+ exam + HTB
Mes 6: Aplicaciones a trabajos
```

## 🛠️ Ejercicios Prácticos

### Ejercicio 1: Inventario de Habilidades
```
Usa Gemini para:
1. Listar TODAS tus habilidades (10 min)
2. Categorizar: Técnicas vs. Blandas
3. Identificar top 5 más valiosas
4. Encontrar 3 habilidades sorpresa que no sabías que tenías
```

### Ejercicio 2: Career Identity Draft
```
Escribe 5 versiones diferentes de tu Career Identity Statement
con ayuda de IA. Pide a amigos/mentores que voten cuál es mejor.
```

### Ejercicio 3: Role Exploration
```
Investiga 3 roles diferentes usando IA:
- Rol aspiracional (dream job)
- Rol alcanzable (1 año)
- Rol alternativo (plan B)

Para cada uno documenta: requisitos, salario, empresas
```

## 📋 Checklist Semana 1

- [ ] Creé inventario completo de habilidades con Gemini
- [ ] Identifiqué al menos 8 habilidades transferibles
- [ ] Escribí mi Career Identity Statement (versión 1)
- [ ] Exploré 3+ roles de carrera potenciales
- [ ] Completé skills gap analysis
- [ ] Creé plan de desarrollo de 6 meses
- [ ] Configuré Gemini y NotebookLM
- [ ] Guardé todos los outputs en carpeta organizada

---

# Semana 2: Optimice su Búsqueda con IA

## 🎯 Objetivos
- Crear plan de búsqueda personalizado
- Optimizar CV con IA
- Construir presencia online profesional
- Usar IA para destacar con empleadores

## 📝 Plan de Búsqueda con IA

### Crear Job Search Plan

**Prompt para Gemini:**
```
"Ayúdame a crear un plan de búsqueda de empleo estructurado:

OBJETIVO:
- Rol deseado: [Security Analyst]
- Timeline: [3 meses]
- Ubicación: [Ciudad/Remoto]
- Tipo: [Full-time/Contract]

SITUACIÓN ACTUAL:
- Disponibilidad: [X horas/semana]
- Recursos: [Certificaciones, portafolio, network]
- Restricciones: [Salario mínimo, etc.]

Genera plan semanal con:
1. Metas específicas y medibles
2. Actividades diarias
3. Métricas de progreso
4. Recursos necesarios
5. Contingencias"
```

### Template de Plan Generado

```markdown
## PLAN DE BÚSQUEDA - 12 SEMANAS

### FASE 1: PREPARACIÓN (Semanas 1-3)
Semana 1: Fundamentos
├─ Lunes-Miércoles: Optimizar CV y LinkedIn
├─ Jueves: Crear portafolio en GitHub
├─ Viernes: Investigar 10 empresas objetivo
└─ Meta: Materiales de aplicación listos

Semana 2: Investigación
├─ Investigar 20 ofertas relevantes
├─ Identificar palabras clave comunes
├─ Mapear requisitos vs. habilidades
└─ Meta: Lista de 50 empresas objetivo

Semana 3: Red de Contactos
├─ Conectar con 10 profesionales en LinkedIn
├─ Unirse a 3 grupos de ciberseguridad
├─ Asistir a 1 meetup/webinar
└─ Meta: 15 conexiones nuevas relevantes

### FASE 2: APLICACIONES (Semanas 4-8)
Objetivo: 5-7 aplicaciones de calidad/semana
├─ Lunes: Buscar ofertas (2h)
├─ Martes-Jueves: Aplicar (3-4 apps)
├─ Viernes: Seguimiento y networking
└─ Meta: 25-35 aplicaciones total

### FASE 3: ENTREVISTAS (Semanas 9-12)
├─ Preparación diaria con IA
├─ Mock interviews 2x/semana
├─ Seguimiento post-entrevista
└─ Meta: 3-5 entrevistas, 1+ oferta

MÉTRICAS SEMANALES:
□ Aplicaciones enviadas: __/5
□ Conexiones LinkedIn: __/10
□ Entrevistas agendadas: __
□ Respuestas recibidas: __
□ Actualizaciones de skills: __
```

## 📄 Optimizar CV con IA

### Análisis de CV con Gemini

**Prompt:**
```
"Analiza mi CV para posición de Security Analyst.

[PEGA TU CV AQUÍ]

Por favor:
1. Identifica debilidades
2. Sugiere mejoras de formato
3. Optimiza palabras clave para ATS
4. Reescribe bullets más impactantes
5. Recomienda qué agregar/quitar
6. Verifica consistencia y errores"
```

### Optimización de Bullets

**ANTES (débil):**
```
• Trabajé con logs de seguridad
• Ayudé al equipo con incidentes
• Usé varias herramientas
```

**Prompt de mejora:**
```
"Transforma estos bullets en formato STAR 
(Situation-Task-Action-Result) con métricas cuando sea posible:
[Pegar bullets actuales]"
```

**DESPUÉS (fuerte):**
```
• Analicé 500+ eventos de seguridad diarios usando Splunk,
  reduciendo falsos positivos en 30% mediante reglas optimizadas
  
• Respondí a 15 incidentes críticos de ransomware, conteniendo
  amenazas en promedio 25% más rápido que baseline del equipo
  
• Automaticé análisis de logs con Python, ahorrando 10 horas
  semanales al equipo y mejorando tiempo de detección en 40%
```

### Palabras Clave ATS

**Prompt:**
```
"Extrae palabras clave de esta descripción de trabajo
y compárala con mi CV:

JOB DESCRIPTION:
[Pegar descripción completa]

MI CV:
[Pegar CV]

Muéstrame:
1. Keywords que estoy usando ✅
2. Keywords que me faltan ❌
3. Cómo incorporarlas naturalmente
4. Score estimado de ATS (0-100)"
```

### Personalización Rápida

**Template con Variables:**
```
"Adapta mi CV para esta posición específica:

POSICIÓN: [Título]
EMPRESA: [Nombre]
REQUISITOS CLAVE: [Top 3-5]

Mantén estructura base pero:
- Reordena secciones por relevancia
- Enfatiza experiencia más relevante
- Ajusta Career Summary
- Incorpora keywords específicos
- Mantén 1 página
```

## 💼 Presencia Online con IA

### Optimizar LinkedIn

**Headline Generator:**
```
"Crea 5 opciones de LinkedIn headline para:
- Rol: Security Analyst
- Especialización: Threat Detection
- Diferenciador: Python Automation
- Certificación: Google Cybersecurity

Formato: Máximo 120 caracteres, keywords estratégicos"
```

**Ejemplos:**
```
1. "Security Analyst | Threat Detection & Response | 
    Python Automation | Google Certified"

2. "SOC Analyst Specialist | SIEM & Threat Hunting | 
    Cybersecurity Automation Expert"

3. "Security Analyst | Blue Team | Python | Splunk | 
    Protecting Digital Assets"
```

### About Section con IA

**Prompt:**
```
"Escribe mi LinkedIn About section:

INCLUIR:
- Career Identity Statement
- Habilidades técnicas clave
- Pasión por ciberseguridad
- Logro destacado
- Call to action

Tono: Profesional pero auténtico
Longitud: 3-4 párrafos
Keywords: [lista]"
```

**Estructura:**
```
PÁRRAFO 1: Quién soy (Career Identity)
"Security Analyst apasionado por defender infraestructuras 
críticas contra amenazas emergentes..."

PÁRRAFO 2: Qué hago bien (Habilidades + Valor)
"Especializado en threat detection usando SIEM, automatización 
con Python, y respuesta rápida a incidentes..."

PÁRRAFO 3: Logro + Impacto
"Recientemente desarrollé sistema automatizado que redujo 
tiempo de triaje de alertas en 50%..."

PÁRRAFO 4: Qué busco + CTA
"Busco conectar con profesionales de ciberseguridad y 
oportunidades en SOC/security teams. ¡Conectemos!"
```

### Featured Section

**Qué incluir:**
- Certificaciones (imagen + link)
- Proyectos en GitHub
- Artículos/blogs técnicos
- Presentaciones
- Endorsements destacados

**Prompt para descriptions:**
```
"Escribe descripción de 150 caracteres para mi proyecto:
[Nombre y breve explicación del proyecto]

Que resalte: impacto, tecnologías, resultados"
```

## 🎨 Portfolio con IA

### GitHub Profile README

**Prompt:**
```
"Crea mi GitHub profile README.md:

SECCIONES:
- Intro breve + emoji
- Stack tecnológico con badges
- Proyectos destacados (3)
- Certificaciones
- Estadísticas de GitHub
- Contacto

Estilo: Profesional, visual, fácil de escanear"
```

**Template generado:**
```markdown
# 👋 Hola, soy [Tu Nombre]

🔐 Security Analyst | 🐍 Python Automation | 🎯 Threat Hunter

## 🛠️ Tech Stack
![Python](https://img.shields.io/badge/-Python-3776AB?logo=python&logoColor=white)
![Linux](https://img.shields.io/badge/-Linux-FCC624?logo=linux&logoColor=black)
![Splunk](https://img.shields.io/badge/-Splunk-000000?logo=splunk)

## 🚀 Featured Projects
### [Log Analyzer Pro](link)
Sistema automatizado de análisis de logs con detección de anomalías
`Python` `Pandas` `ML`

## 📜 Certifications
- ✅ Google Cybersecurity Professional
- ✅ CompTIA Security+ (in progress)

## 📫 Connect
[![LinkedIn](link)] [![Email](link)]
```

## 🛠️ Ejercicios Prácticos

### Ejercicio 1: CV A/B Testing
```
1. Genera 2 versiones de CV con IA
2. Usa herramienta ATS simulator
3. Compara scores
4. Optimiza basándote en resultados
```

### Ejercicio 2: LinkedIn Makeover
```
- Reescribe todos los elementos clave
- Actualiza foto profesional
- Agrega featured content
- Solicita 10 recommendations
```

### Ejercicio 3: Brand Consistency Check
```
Usa IA para verificar que CV, LinkedIn, GitHub,
y Portfolio cuenten historia consistente.
```

## 📋 Checklist Semana 2

- [ ] Plan de búsqueda de 12 semanas creado
- [ ] CV optimizado para ATS (score >80)
- [ ] LinkedIn profile al 100% completado
- [ ] GitHub profile README publicado
- [ ] 3 proyectos destacados documentados
- [ ] Portafolio online live
- [ ] Career materials en carpeta organizada
- [ ] Recibí feedback de 2+ personas

---

# Semana 3: Gestione Aplicaciones con IA

## 🎯 Objetivos
- Usar plataformas de búsqueda efectivamente
- Crear sistema de tracking de aplicaciones
- Maximizar networking con IA
- Organizar proceso de búsqueda

## 🔍 Plataformas de Búsqueda

### Estrategia Multi-Plataforma

```
TIER 1 (Diario):
├─ LinkedIn Jobs
├─ Indeed
└─ Glassdoor

TIER 2 (3x semana):
├─ CyberSecJobs
├─ InfoSec-Jobs
└─ Dice (tech)

TIER 3 (Semanal):
├─ Company career pages
├─ Startup boards (AngelList)
└─ Government jobs (USAJobs)
```

### Búsqueda Optimizada con IA

**Prompt para Job Search:**
```
"Ayúdame a crear búsquedas efectivas:

ROL OBJETIVO: Security Analyst
NIVEL: Entry/Junior
UBICACIÓN: [Ciudad] o Remoto
PREFERENCIAS: [Industria, tamaño empresa]

Genera:
1. 10 variaciones de términos de búsqueda
2. Filtros a aplicar
3. Palabras clave para incluir/excluir
4. Booleanos para búsqueda avanzada
5. Alertas a configurar"
```

**Output:**
```
BÚSQUEDAS PRINCIPALES:
✓ "Security Analyst" AND (Junior OR Entry OR Associate)
✓ "SOC Analyst" AND (Tier 1 OR Level 1)
✓ "Cybersecurity Analyst" -Senior -Lead
✓ "Information Security" AND (Analyst OR Specialist)

FILTROS:
□ Fecha: Últimos 7 días
□ Experiencia: 0-2 años
□ Tipo: Full-time
□ Remoto: Sí/Híbrido

EXCLUIR:
✗ "Senior", "Lead", "Manager", "Director"
✗ "5+ years", "extensive experience"

ALERTAS:
→ Configurar email diario
→ Notificaciones móvil
→ RSS feed si disponible
```

### Análisis de Ofertas con IA

**Prompt:**
```
"Analiza esta oferta de trabajo:

[PEGAR DESCRIPCIÓN COMPLETA]

Evalúa:
1. Match con mi perfil (%)
2. Requisitos críticos vs. deseables
3. Red flags potenciales
4. Preguntas para hacer en entrevista
5. Debería aplicar? (Sí/No y por qué)
6. Cómo personalizar mi aplicación"
```

## 📊 Sistema de Tracking

### Application Tracker con Google Sheets + IA

**Estructura de Spreadsheet:**
```
| Fecha | Empresa | Posición | Link | Estado | Contacto | Seguimiento | Notas |
|-------|---------|----------|------|--------|----------|-------------|-------|
```

**Columnas Avanzadas:**
```
| ATS-Friendly | Keywords Match | Referral | Salary Range | Priority | Next Action |
```

### Automatización con Gemini

**Prompt para generar entries:**
```
"Crea entrada de tracking para esta aplicación:

URL: [link]
Empresa: [nombre]
Posición: [título]

Extrae y organiza:
- Fecha de aplicación (hoy)
- Requisitos clave
- Salario si mencionado
- Persona de contacto si hay
- Follow-up date (sugerir)
- Template de follow-up email"
```

### Estados del Proceso

```
📝 APLICADO
├─ Follow-up en 1 semana
└─ Preparar para posible screening

📞 SCREENING
├─ Preparar preguntas
├─ Investigar empresa
└─ Follow-up en 3 días

💼 ENTREVISTA 1
├─ Estudiar role-specific questions
├─ Preparar ejemplos STAR
└─ Thank you note (24h)

🎯 ENTREVISTA 2+
├─ Preparar preguntas avanzadas
├─ Investigación profunda
└─ Negociación prep

✅ OFERTA
├─ Evaluar términos
├─ Negociar si apropiado
└─ Decisión (plazo típico: 1 semana)

❌ RECHAZADO
├─ Pedir feedback
├─ Aprender y mejorar
└─ Keep connection (LinkedIn)
```

## 🤝 Networking Potenciado con IA

### LinkedIn Outreach

**Template de Mensaje Generado por IA:**
```
"Crea mensaje de LinkedIn para:

DESTINATARIO: [Nombre, título, empresa]
CONTEXTO: [Cómo lo encontré]
OBJETIVO: [Informational interview / referral / advice]

Características:
- Personalizado (mencionar algo específico)
- Breve (3-4 líneas)
- Clear ask
- Profesional pero friendly"
```

**Ejemplo Output:**
```
"Hola [Nombre],

Vi tu trayectoria como Security Analyst en [Empresa] 
y me impresionó tu trabajo en [proyecto específico 
mencionado en su perfil].

Soy recién certificado en Google Cybersecurity y 
estoy explorando roles en SOC. ¿Tendrías 15 minutos 
para compartir tu experiencia en la industria?

Agradecería mucho tus insights.

Saludos,
[Tu nombre]"
```

### Follow-up Inteligente

**Prompt:**
```
"Genera follow-up message para:

SITUACIÓN: Aplicé hace [X días]
EMPRESA: [Nombre]
POSICIÓN: [Título]
CONTACTO: [Si tengo]
CONTEXTO ADICIONAL: [Conexión, evento, etc.]

Tono: Profesional, interesado, no desesperado"
```

**Email Generado:**
```
Subject: Following up: Security Analyst Application

Dear [Hiring Manager],

I applied for the Security Analyst position (Job ID: XXX) 
on [date] and wanted to express my continued interest.

With my recent Google Cybersecurity certification and hands-on 
experience in [relevant skill], I'm confident I could contribute 
to [specific company initiative you researched].

Would it be possible to schedule a brief call to discuss how 
my skills align with your team's needs?

Thank you for your consideration.

Best regards,
[Your Name]
[LinkedIn] | [Portfolio]
```

### Informational Interviews

**Preparación con IA:**
```
"Voy a tener informational interview con:

PERSONA: [Security Engineer en Big Tech]
BACKGROUND: [Su experiencia]
DURACIÓN: 30 minutos

Genera:
1. 10 preguntas inteligentes
2. Orden estratégico
3. Cómo hacer ask (referral/advice)
4. Thank you note template
5. Cómo mantener conexión"
```

## 📧 Email Templates con IA

### Application Email

**Prompt:**
```
"Escribe email de aplicación para:

POSICIÓN: [Título exacto]
EMPRESA: [Nombre y lo que hacen]
POR QUÉ ENCAJO: [3 puntos clave]
CALL TO ACTION: [Entrevista]

Estructura:
- Subject line atractivo
- Opening fuerte
- 2-3 párrafos
- Cierre con CTA
- Máximo 200 palabras"
```

### Thank You Note

**Post-Interview Template:**
```
Subject: Thank you - [Position] Interview

Dear [Interviewer Name],

Thank you for taking the time to discuss the [Position] 
role today. I enjoyed learning about [specific topic 
discussed] and [team/project mentioned].

Our conversation reinforced my interest in joining 
[Company]. My experience with [relevant skill/project] 
aligns well with [specific need they mentioned].

I'm excited about the possibility of contributing to 
[specific initiative discussed] and would welcome the 
opportunity to join your team.

Please let me know if you need any additional information.

Best regards,
[Your Name]
```

## 🛠️ Ejercicios Prácticos

### Ejercicio 1: Tracker Setup
```
1. Crea Google Sheet con todas las columnas
2. Agrega 10 aplicaciones pasadas/futuras
3. Configura recordatorios automáticos
4. Crea dashboard con stats
```

### Ejercicio 2: Networking Sprint
```
SEMANA DE NETWORKING:
- Lunes: Identifica 20 personas objetivo
- Martes: Envía 5 connection requests
- Miércoles: Envía 5 más
- Jueves: Follow-up previous week
- Viernes: 1 informational interview agendado
```

### Ejercicio 3: Application Quality Test
```
Aplica a 2 trabajos con máximo esfuerzo:
- Personaliza CV 100%
- Cover letter customizado
- Networking previo si posible
- Follow-up estratégico
Vs.
Quick apply a 5 trabajos

Compara tasa de respuesta
```

## 📋 Checklist Semana 3

- [ ] Application tracker configurado y activo
- [ ] Alertas de trabajo configuradas en 3+ plataformas
- [ ] 10+ aplicaciones de calidad enviadas
- [ ] 15+ conexiones LinkedIn nuevas
- [ ] 5+ mensajes de networking enviados
- [ ] 1 informational interview realizado o agendado
- [ ] Templates de email guardados
- [ ] Sistema de follow-up funcionando

---

# Semana 4: Prepare Entrevistas con IA

## 🎯 Objetivos
- Preparar preguntas para entrevistadores
- Crear professional pitch efectivo
- Dominar método STAR con IA
- Practicar entrevistas con IA

## 🎤 Professional Pitch (Elevator Pitch)

### Estructura del Pitch

```
[QUIÉN ERES] → [QUÉ HACES] → [POR QUÉ IMPORTA] → [QUÉ BUSCAS]

30 segundos: Versión concisa
60 segundos: Versión completa
2 minutos: Versión con ejemplos
```

### Generar
