# MailBot EOS Community 🚀

Panel de envío masivo de emails para EOS Community. Importación XLSX, gestión activos/inactivos, diseñador visual HTML y campañas segmentadas — todo sin backend.

---

## ⚠️ FIX: El correo llega vacío / asunto duplicado

El problema está en el **template de EmailJS**. Configúralo así:

### En emailjs.com → Email Templates → edita tu template:

| Campo del template | Valor |
|---|---|
| **To Email** | `{{to_email}}` |
| **From Name** | `{{from_name}}` |
| **Reply To** | `{{to_email}}` |
| **Subject** | `{{subject}}` ← solo esto, sin texto fijo |
| **Content** | `{{{message}}}` ← tres llaves para HTML |

> ✅ **Tres llaves** `{{{message}}}` = renderiza HTML sin escapar  
> ❌ **Dos llaves** `{{message}}` = llega como texto plano / código visible  
> ❌ Subject con texto fijo + `{{subject}}` = asunto duplicado

### Activa HTML:
En el template → **Content type** → selecciona **text/html**

---

## 🚀 Inicio rápido

```bash
# Clona el repo
git clone https://github.com/tuusuario/mailbot-eos.git
cd mailbot-eos

# Abre en navegador (no necesita servidor)
open index.html
# o en Windows: start index.html
```

## 📁 Estructura

```
mailbot-eos/
├── index.html                      ← App completa
├── README.md
├── src/
│   └── email-templates/
│       ├── reactivacion-inactivos.html
│       ├── bienvenida-activos.html
│       └── newsletter.html
└── docs/
    └── emailjs-setup.md
```

## 🌐 Deploy gratis

**Netlify Drop** (más fácil):
1. [app.netlify.com/drop](https://app.netlify.com/drop)
2. Arrastra la carpeta → URL inmediata

**GitHub Pages**:
1. Settings → Pages → Branch: main
2. URL: `https://usuario.github.io/mailbot-eos`

## 📊 Columnas XLSX EOS Community detectadas automáticamente

`Correo` · `Nombre` · `Apellido` · `Estatus` (Activo/Inactivo) · `País` · `Ciudad` · `Patrocinador`

## ✉️ Variables en emails

`{{nombre}}` `{{empresa}}` `{{ciudad}}` `{{pais}}` `{{email}}`
