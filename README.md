# MediDocs Pro

> Sistema profesional de generación de documentos médicos para consultorios. Funciona como app instalable en computadora, tablet y celular — sin internet, sin servidores, 100% privado.

[![Demo](https://img.shields.io/badge/Demo-live-2BA39A?style=flat-square)](https://medi-docs-pro-adulam.vercel.app/)
[![PWA](https://img.shields.io/badge/PWA-instalable-1F4E79?style=flat-square)]()
[![Offline](https://img.shields.io/badge/Offline-first-555?style=flat-square)]()
[![Made by codegurex.com](https://img.shields.io/badge/by-codegurex.com-2E86AB?style=flat-square)](https://codegurex.com)

---

## ¿Qué es MediDocs Pro?

**MediDocs Pro** es una aplicación web instalable (PWA) diseñada para que cualquier médico con consultorio propio pueda generar documentación clínica profesional —informes, certificados, recetas e historias clínicas— en cuestión de segundos, desde su computadora o celular, sin depender de internet ni de servicios externos.

El sistema nació de una necesidad real: la mayoría de consultorios pequeños todavía redactan estos documentos a mano o copiando plantillas de Word, lo que consume tiempo de consulta y proyecta una imagen poco profesional. MediDocs Pro lo resuelve con una herramienta lista para usar, personalizable y privada.

🔗 **Demo en vivo:** [medi-docs-pro-adulam.vercel.app](https://medi-docs-pro-adulam.vercel.app/)

---

## Características principales

- 🩺 **6 tipos de documentos médicos** listos para usar
- 📱 **Instalable como app nativa** en Android (Chrome) e iOS (Safari)
- 🔌 **Funciona 100% offline** una vez instalada
- 🔒 **Privacidad total** — los datos nunca salen del dispositivo
- ⚙️ **Personalizable** — cada médico configura su nombre, especialidad, logo y firma
- 👥 **Gestión de pacientes** con autocompletado y respaldo exportable
- 📄 **PDFs profesionales** con ajuste automático a una página
- 🎨 **Diseño elegante y sobrio** pensado para uso clínico

---

## Documentos que genera

| # | Documento | Descripción |
|---|-----------|-------------|
| 1 | **Informe médico** | Reporte clínico completo: motivo, antecedentes, evaluación, hallazgos, diagnóstico y recomendaciones |
| 2 | **Certificado médico** | Certificado de estado de salud o aptitud, con texto autogenerado y editable |
| 3 | **Certificado médico completo** | Combina evaluación clínica, diagnóstico, recomendaciones y reposo en un solo certificado |
| 4 | **Certificado de reposo** | Justificación de reposo con cálculo automático de fecha final |
| 5 | **Receta médica** | Prescripción de medicamentos con indicaciones y próximo control |
| 6 | **Historia clínica** | Historia clínica completa con anamnesis, antecedentes, signos vitales y cálculo automático de IMC |

---

## Stack técnico

El sistema está construido como un único archivo HTML autocontenido para máxima portabilidad:

- **Frontend:** JavaScript vanilla, HTML5, CSS3
- **Generación de PDF:** [jsPDF](https://github.com/parallax/jsPDF) (embebida, sin CDN)
- **PWA:** Service Worker + Web App Manifest para instalación nativa
- **Persistencia:** `localStorage` del navegador (datos locales, sin servidor)
- **Hosting:** [Vercel](https://vercel.com) (PWA estática)

> Decisión de diseño: cero dependencias en runtime y cero backend. Toda la aplicación —incluyendo la librería de PDF— se entrega en un solo archivo HTML, lo que permite que funcione completamente offline y se pueda distribuir como un archivo único.

---

## Arquitectura

```
┌──────────────────────────────────────────────────┐
│            MediDocs_Pro.html (un solo archivo)   │
│  ┌────────────────────────────────────────────┐  │
│  │  UI: Vista enrutada + formularios          │  │
│  │  ↓                                         │  │
│  │  Motor de PDF (jsPDF + render sobrio)      │  │
│  │  ↓                                         │  │
│  │  Auto-ajuste a una página (compresión      │  │
│  │  iterativa hasta encontrar escala óptima)  │  │
│  └────────────────────────────────────────────┘  │
│                                                  │
│  Persistencia local (localStorage)               │
│  ├── medidocs_config_v1 → datos del médico       │
│  └── medidocs_pacientes_v1 → registros           │
│                                                  │
│  PWA layer                                       │
│  ├── manifest.json → instalación                 │
│  └── sw.js → cacheo offline                      │
└──────────────────────────────────────────────────┘
```

---

## Funciones destacadas

### 🎯 Ajuste automático a una página
El generador de PDF mide el contenido renderizado y, si excede una página, reduce automáticamente el espaciado vertical en pasos (1.0 → 0.85 → 0.7 → … → 0.05) hasta que entra. Los documentos cortos respiran con espacio amplio; los densos se compactan sin perder legibilidad.

### 🧮 Cálculo automático de IMC
En la historia clínica, al ingresar peso y talla, el IMC se calcula y muestra en tiempo real.

### 👤 Autocompletado de pacientes
Al escribir el nombre de un paciente ya registrado en cualquier formulario, sus datos (cédula, fecha de nacimiento, edad) se cargan automáticamente.

### 💾 Respaldo entre dispositivos
La sección de pacientes permite exportar todos los registros a un archivo JSON e importarlos en otro dispositivo — útil para sincronizar computadora y celular, y como copia de seguridad.

### 🏥 Configuración por médico
La primera vez que se abre, la app pide los datos del consultorio (nombre, especialidad, teléfono, firma y logo). Quedan guardados permanentemente y aparecen en el encabezado y la firma de todos los documentos.

---

## Instalación como app

### En Android (Chrome)
1. Abre el enlace de la aplicación en Chrome
2. Toca el botón **"Instalar app"** que aparece arriba, o usa el menú ⋮ → **"Instalar aplicación"**
3. Confirma — el ícono aparecerá en la pantalla de inicio

### En iPhone / iPad (Safari)
1. Abre el enlace en **Safari** (importante: no funciona en Chrome iOS)
2. Toca el botón **Compartir** (cuadrado con flecha hacia arriba)
3. Selecciona **"Agregar a pantalla de inicio"**
4. Confirma

### En computadora (Chrome / Edge)
Aparece un ícono de instalación en la barra de direcciones. Un clic y queda como aplicación de escritorio.

---

## Uso rápido

```
1. Abrir la app  →  2. Configurar consultorio (solo la primera vez)
                 →  3. Elegir tipo de documento
                 →  4. Llenar formulario
                 →  5. "Generar PDF"  →  Documento listo
```

> Solo el nombre del paciente es obligatorio. El resto de campos es opcional y la app se adapta al contenido que ingreses.

---

## Privacidad

MediDocs Pro está diseñado con **privacidad por defecto**:

- 🚫 No hay servidor — la app es 100% estática
- 🚫 No hay analytics, tracking ni cookies de terceros
- 🚫 Los datos de pacientes nunca se transmiten por red
- ✅ Todo se guarda en `localStorage` del navegador del médico
- ✅ El respaldo es un archivo JSON que el médico controla

Esto es especialmente relevante para cumplir con normativas de protección de datos de salud, donde almacenar información clínica en servidores externos suele requerir contratos y certificaciones específicas.

---

## Estado del proyecto

✅ **En producción** — actualmente en uso real en consultorio médico (Consultorio Médico Familiar ADULAM, Ecuador).

🚀 **Disponible para comercializar** a otros médicos en versión personalizable.

---

## Roadmap

- [ ] Plantillas personalizables por especialidad médica
- [ ] Búsqueda avanzada en historial de pacientes
- [ ] Estadísticas básicas del consultorio (diagnósticos frecuentes, etc.)
- [ ] Multiidioma (inglés, portugués)
- [ ] Integración opcional con impresión térmica de recetas

---

## Contacto

Desarrollado por **[codegurex.com](https://codegurex.com)**

¿Interesado en una versión personalizada para tu consultorio?
Solicita una demostración o configuración a medida.

---

## Licencia

Software propietario · © codegurex.com · Todos los derechos reservados.

Para licenciamiento, distribución comercial o personalización, contactar con codegurex.com.
