# Guía de configuración EmailJS

## Paso 1 — Crear cuenta
Ve a https://emailjs.com y regístrate gratis (200 emails/mes).

## Paso 2 — Crear Email Service
1. Panel → **Email Services** → **Add New Service**
2. Selecciona **Gmail**
3. Conecta tu cuenta de Google
4. Copia el **Service ID** (ejemplo: `service_v3m9ok2`)

## Paso 3 — Crear Email Template

1. Panel → **Email Templates** → **Create New Template**
2. Configura EXACTAMENTE así:

```
To:        {{to_email}}
From Name: {{from_name}}
Reply To:  {{to_email}}
Subject:   {{subject}}
```

En el **body** del template pon:
```
{{{message}}}
```
⚠️ Son TRES llaves `{{{ }}}` — esto es crítico para que llegue HTML.

3. En **Settings** del template → **Content type** → `text/html`
4. Guarda y copia el **Template ID** (ejemplo: `template_abc123`)

## Paso 4 — Obtener Public Key
Panel → **Account** → **API Keys** → copia la **Public Key**

## Paso 5 — Configurar en el bot
Abre el MailBot → pestaña **Configuración** → pega los 3 valores:
- Public Key
- Service ID  
- Template ID

## Prueba
Haz clic en **"🧪 Email de prueba"** — deberías recibir el email en tu bandeja.

---

## ¿Por qué llega vacío?

| Problema | Causa | Solución |
|---|---|---|
| Cuerpo vacío | Template sin `{{{message}}}` | Agregar `{{{message}}}` al body |
| HTML visible como texto | Usando `{{message}}` con 2 llaves | Cambiar a `{{{message}}}` con 3 llaves |
| Asunto duplicado | Subject fijo + `{{subject}}` | Dejar solo `{{subject}}` en el campo Subject |
| "Sent via EmailJS" | Plan gratuito | Normal, aparece en el footer |
