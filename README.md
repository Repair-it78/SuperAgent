# ⚡ SuperAgent — Multi-LLM Orchestrator

Orquestador de múltiples LLMs con backend seguro en Netlify.

## Estructura del proyecto

```
superagent/
├── public/
│   └── index.html          ← Frontend
├── netlify/
│   └── functions/
│       └── claude.js       ← Backend serverless (protege tu API key)
├── netlify.toml            ← Configuración de Netlify
└── README.md
```

---

## 🚀 Deploy en 5 pasos

### 1. Sube el proyecto a GitHub

```bash
git init
git add .
git commit -m "SuperAgent inicial"
git branch -M main
git remote add origin https://github.com/TU_USUARIO/superagent.git
git push -u origin main
```

### 2. Conecta con Netlify

1. Ve a [netlify.com](https://netlify.com) e inicia sesión
2. Clic en **"Add new site"** → **"Import an existing project"**
3. Selecciona **GitHub** y elige el repo `superagent`
4. Netlify detecta automáticamente la config del `netlify.toml`
5. Clic en **"Deploy site"**

### 3. Añade tu API Key de Anthropic (IMPORTANTE)

En Netlify, ve a:
**Site settings → Environment variables → Add variable**

```
Key:   ANTHROPIC_API_KEY
Value: sk-ant-api03-XXXXXXXXXXXXXXXX
```

### 4. Redeploy

Después de añadir la variable, ve a **Deploys → Trigger deploy → Deploy site**

### 5. ¡Listo!

Tu SuperAgent estará en `https://tu-sitio.netlify.app` 🎉

---

## 🔒 Seguridad

- La API key **nunca** se expone al navegador
- Todo pasa por la Netlify Function (`/api/claude`)
- Puedes añadir rate limiting en la función si lo necesitas

## 🤖 Modos disponibles

| Modo | Descripción |
|------|-------------|
| **Router** | Elige el mejor modelo para cada tarea |
| **Ensemble** | Todos los modelos responden, Claude sintetiza |
| **Debate** | Los modelos se confrontan, Claude arbitra |
| **Pipeline** | Cada modelo enriquece al anterior en cadena |

## ➕ Añadir GPT-4 real

En `netlify/functions/claude.js`, añade una función similar
para `api.openai.com` con `OPENAI_API_KEY` en las env vars.

## ➕ Añadir Gemini real

Igual pero con `generativelanguage.googleapis.com`
y `GEMINI_API_KEY` en las env vars.
