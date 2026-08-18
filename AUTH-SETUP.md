# 🔐 Configuración de Autenticación - VIBE CANA

## Métodos de Login Habilitados

Tu app ahora tiene **5 métodos de login**:

| Método | Estado | Proveedor Firebase |
|--------|--------|-------------------|
| ✅ Google | Activo | `GoogleAuthProvider` |
| ✅ Facebook | Activo | `FacebookAuthProvider` |
| ✅ Apple | Activo | `OAuthProvider('apple.com')` |
| ✅ Teléfono/SMS | Activo | `PhoneAuthProvider` |
| ✅ Email/Password | Activo | `signInWithEmailAndPassword` |

---

## 📋 Configuración en Firebase Console

### 1. Habilitar Proveedores

Ve a **Firebase Console** → **Authentication** → **Sign-in method**

#### Google
- Click en **Google** → **Habilitar**
- Selecciona email de soporte
- Aceptar términos → **Guardar**

#### Facebook
- Click en **Facebook** → **Habilitar**
- Necesitas **App ID** y **App Secret** de Facebook Developers
- Ve a [developers.facebook.com](https://developers.facebook.com)
- Crea una app → Agregar producto → Facebook Login
- Copia las credenciales en Firebase

#### Apple
- Click en **Apple** → **Habilitar**
- Necesitas un **Apple Developer Account** ($99/año)
- Ve a [developer.apple.com](https://developer.apple.com)
- Crea un App ID con "Sign in with Apple"
- Configura los certificados en Firebase

#### Teléfono
- Click en **Teléfono** → **Habilitar**
- Configura el **reCAPTCHA** para prevenir spam
- Agrega tu dominio en **Authorized domains**

---

### 2. Dominios Autorizados

En **Authentication** → **Settings** → **Authorized domains**, agrega:

```
localhost
tudominio.com
tudominio.web.app
```

---

### 3. Facebook - Paso a Paso

1. Ve a [developers.facebook.com](https://developers.facebook.com)
2. Crea una **App nueva** → Tipo: **Consumer**
3. En **Add products**, agrega **Facebook Login**
4. En **Settings**, copia:
   - **App ID** → Pegar en Firebase Console
   - **App Secret** → Pegar en Firebase Console
5. En **Valid OAuth Redirect URIs**, agrega:
   ```
   https://vibecana-e938d.firebaseapp.com/__/auth/handler
   ```

---

### 4. Apple - Paso a Paso

1. Ve a [developer.apple.com/account](https://developer.apple.com/account)
2. Crea un **App ID** → Habilita **Sign in with Apple**
3. En **Certificates, Identifiers & Profiles**:
   - Crea un **Service ID**
   - Crea una **Key** con "Sign in with Apple"
4. En **Firebase Console**:
   - Click **Apple** → **Habilitar**
   - Ingresa Service ID, Key ID, Team ID
   - Sube el archivo `.p8` de la Key

---

### 5. Teléfono - ReCAPTCHA

Para que funcione el login por teléfono:

1. Ve a **Authentication** → **Settings**
2. Habilita **reCAPTCHA verification**
3. Agrega tu dominio en **Authorized domains**

---

## 🔧 Configuración de Desarrollo

Para probar en **localhost**:

1. En Firebase Console → **Authentication** → **Settings** → **Authorized domains**
2. Agrega `localhost`
3. El reCAPTCHA funcionará automáticamente

---

## ⚠️ Errores Comunes

### "auth/operation-not-allowed"
- El proveedor no está habilitado en Firebase Console
- Ve a **Sign-in method** y habilita el método

### "auth/unauthorized-domain"
- Tu dominio no está en los autorizados
- Agrega el dominio en **Settings** → **Authorized domains**

### "auth/too-many-requests"
- Límite de intentos alcanzado
- Espera unos minutos o usa otro método

### "auth/popup-blocked"
- El navegador bloqueó la ventana emergente
- Permite popups para tu dominio

---

## 📱 Login por Teléfono - Flujo

1. Usuario ingresa número con código de país (+1 809 ...)
2. Se envía SMS con código de 6 dígitos
3. Usuario ingresa el código
4. Se verifica y se crea la sesión

**Nota:** En desarrollo, Firebase usa números de prueba configurados en Console.

---

## 🎯 Checklist de Configuración

- [ ] Google habilitado en Firebase
- [ ] Facebook habilitado (requiere App ID/Secret)
- [ ] Apple habilitado (requiere Developer Account)
- [ ] Teléfono habilitado
- [ ] Email/Password habilitado
- [ ] Dominios autorizados configurados
- [ ] reCAPTCHA habilitado (para teléfono)
- [ ] Facebook OAuth Redirect URI configurado
- [ ] Apple Service ID configurado

---

## 🆕 Agregar Más Métodos

Puedes agregar más proveedores editando `index.html`:

```javascript
// Ejemplo: GitHub
var githubProvider = new firebase.auth.GithubAuthProvider();
githubProvider.addScope('user:email');

function loginWithGitHub() {
    return fbAuth.signInWithPopup(githubProvider);
}
```

---

## 📞 Soporte

Si tienes problemas, revisa:
1. **Firebase Console** → **Authentication** → **Users** (verificar usuarios)
2. **Firebase Console** → **Authentication** → **Settings** (verificar configuración)
3. **Consola del navegador** (ver errores en rojo)
