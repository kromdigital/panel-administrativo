# Panel de Clientes · Sendero del Bosque

Página web para celular (funciona también en computadora) para llevar clientes, calendario, recordatorios y notas.

## Archivos
- `index.html` — toda la aplicación
- `firestore.rules` — reglas de seguridad de la base de datos
- `logo.png` — tu logo horizontal (pantalla de inicio de sesión)
- `escudo.png` — tu escudo (barra superior)

Guarda tus dos imágenes en esta misma carpeta con esos nombres. Si faltan, la página muestra el texto "SENDERO DEL BOSQUE" y una "S" en su lugar.

## Configurar Firebase (una sola vez, ~10 minutos)
1. Entra a https://console.firebase.google.com y crea un proyecto (por ejemplo "sendero-panel").
2. **Authentication** → Comenzar → pestaña *Método de acceso* → activa **Correo electrónico/contraseña**.
3. **Firestore Database** → Crear base de datos → modo producción → elige la región más cercana.
4. En Firestore, pestaña **Reglas**: pega el contenido de `firestore.rules` y publica.
5. Configuración del proyecto (⚙️) → *Tus apps* → agrega una app **Web** (`</>`) → copia el objeto `firebaseConfig`.
6. Abre `index.html`, busca `PEGA AQUÍ TU CONFIGURACIÓN DE FIREBASE` y reemplaza los valores `PEGA_AQUI` por los tuyos.

## Publicarla en internet (gratis)
Con **Firebase Hosting**: en tu computadora instala Node.js, luego en esta carpeta:
```
npm install -g firebase-tools
firebase login
firebase init hosting     (carpeta pública: el punto "."  ·  una sola página: No)
firebase deploy
```
Te dará una dirección tipo `https://tu-proyecto.web.app`. Ábrela en el celular y usa "Agregar a pantalla de inicio" para tenerla como app.

## Primer uso
1. Abre la página → **Crear cuenta** → elige usuario y contraseña (esa será tu cuenta).
2. Si otra persona la va a usar, que cree su propia cuenta: cada quien ve solo sus datos.
   (Si prefieres que todos vean los mismos clientes, avísame y lo cambiamos.)
3. Para evitar que cualquiera cree cuentas, cuando ya tengan las suyas ve a Authentication → Configuración → Acciones del usuario y desactiva "Habilitar la creación de usuarios".

## Cómo funcionan los recordatorios
- **Campana 🔔:** muestra un número rojo con los recordatorios que ya llegaron a su hora y siguen pendientes, y los de las próximas 24 horas. Se actualiza sola mientras la página está abierta.
- **WhatsApp:** el botón **💬 Avisarme** abre WhatsApp con el recordatorio listo para enviártelo (guarda tu número en ⚙️). También hay botón para escribirle directo al cliente.
- **Importante:** que WhatsApp te escriba **solo, con la página cerrada**, requiere la API oficial de WhatsApp Business (con costo mensual) y una función en el servidor. Se puede agregar como segunda etapa.
