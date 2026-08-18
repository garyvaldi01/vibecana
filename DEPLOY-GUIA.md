# 🚀 Guía para Publicar VIBE CANA - Gratis

## OPCIÓN 1: PWA GRATIS (Recomendada para empezar)

### Paso 1: Crear cuenta en Vercel (Gratis)
1. Ve a [vercel.com](https://vercel.com)
2. Click "Sign Up" → "Continue with GitHub"
3. Crea repositorio en GitHub con tu proyecto
4. Vercel lo despliega automáticamente

### Paso 2: Configurar Dominio (Gratis)
1. En Vercel, ve a "Settings" → "Domains"
2. Agrega tu dominio (ej: vibecana.com)
3. O usa el subdominio gratis: `vibecana.vercel.app`

### Paso 3: Los Usuarios Instalan la App
- **Android**: Chrome muestra "Instalar app"
- **iPhone**: Safari → Compartir → "Agregar a pantalla"

---

## OPCIÓN 2: GOOGLE PLAY STORE ($25 USD)

### Requisitos:
- $25 USD para cuenta de desarrollador (pago único)
- Cuenta de Google
- Tarjeta de crédito/débito

### Pasos:
1. Ve a [play.google.com/console](https://play.google.com/console)
2. Crea cuenta de desarrollador ($25)
3. Instala Bubblewrap:
   ```bash
   npm install -g @nickvision/bubblewrap
   ```
4. Inicializa tu proyecto:
   ```bash
   bubblewrap init --manifest=https://tudominio.com/manifest.json
   ```
5. Build:
   ```bash
   bubblewrap build
   ```
6. Sube el APK a Google Play Console

---

## OPCIÓN 3: APPLE APP STORE ($99/AÑO)

### Requisitos:
- $99 USD/año (se renueva cada año)
- Mac (necesario para compilar)
- Cuenta de Apple

### Alternativa Gratis para iOS:
- **PWA**: Los usuarios instalan desde Safari
- **No necesitas cuenta de desarrollador**
- **No necesitas Mac**

---

## 📱 Cómo los Usuarios Instalan tu PWA

### Android (Chrome):
1. Abre `tudominio.com`
2. Click en los 3 puntos → "Instalar app"
3. O aparece banner automático "Agregar a pantalla de inicio"

### iPhone (Safari):
1. Abre `tudominio.com` en Safari
2. Click en botón compartir (📤)
3. Selecciona "Agregar a pantalla de inicio"
4. Ponle nombre → "Agregar"

---

## ✅ Checklist Pre-Deploy

- [ ] manifest.json configurado con tu dominio
- [ ] Íconos de app (192x192 y 512x512)
- [ ] Service Worker registrado
- [ ] HTTPS habilitado (Vercel lo da gratis)
- [ ] Nombre de la app en meta tags

---

## 🆓 Recursos Gratis

| Recurso | URL |
|---------|-----|
| Vercel (hosting) | vercel.com |
| GitHub (código) | github.com |
| Favicon Generator | favicon.io |
| Íconos Gratis | icons8.com |
| Screenshots App | app_mockup.com |

---

## 💡 Mi Consejo

**Empieza gratis con PWA:**
1. Vende la idea a negocios locales en Punta Cana
2. Cuando tengas usuarios y ingresos, invierte en Google Play ($25)
3. Para iOS, la PWA funciona perfectamente gratis

**¿Por qué PWA es suficiente?**
- Se instala desde el navegador
- Funciona offline
- Se ve como app nativa
- No necesitas tienda de apps
- ¡Es 100% gratis!
