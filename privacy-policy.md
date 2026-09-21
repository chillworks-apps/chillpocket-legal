# Política de Privacidad — ChillPocket

**Última actualización:** 21 de septiembre de 2026  
**Desarrollador:** ChillWorks-apps  
**Contacto:** development@chillworks-apps.com

---

## 1. Quién somos

ChillPocket es una aplicación de control financiero personal desarrollada por ChillWorks-apps. Esta política explica qué datos se recogen, cómo se usan, dónde se guardan y qué derechos tienes.

En resumen: **tus transacciones viven en tu móvil**. Solo salen de él si activas funciones concretas (categorías compartidas, inteligencia artificial, conexión bancaria), y en cada caso te explicamos qué se envía y a quién.

---

## 2. Datos que recopilamos y por qué

### 2.1 Datos que tú introduces (almacenados en tu dispositivo)

| Dato | Propósito |
|---|---|
| Transacciones (importe, fecha, nota, comercio, categoría) | Funcionalidad principal de la app |
| Categorías de gasto e ingreso | Organización de transacciones |
| Saldo inicial y preferencias (moneda, formato, idioma, tema) | Personalización de la app |
| Perfil laboral (tipo de empleo) | Módulo "Mi Trabajo" |
| Controles de gasto y objetivos de ahorro | Funcionalidad de presupuesto |

Todos estos datos se guardan en la base de datos local de tu dispositivo. **No se envían a servidores de ChillPocket ni se comparten con terceros**, salvo en las funciones opcionales descritas en las secciones 2.2 a 2.8.

ChillPocket está **excluida de la copia de seguridad automática de Android en la nube** (Google Drive): tus datos no se suben a tu cuenta de Google. Si cambias de móvil, usa la exportación e importación de datos (Ajustes → Descarga) para llevarlos contigo.

### 2.2 Identificador anónimo (Firebase)

Al abrir la app por primera vez se crea una **cuenta anónima** en Firebase Authentication (Google). Es un identificador aleatorio sin nombre, correo ni teléfono. Sirve para que las funciones que necesitan un servidor (categorías compartidas, conexión bancaria, borrado de cuenta) sepan qué datos son tuyos. Puedes eliminarlo en cualquier momento con "Borrar cuenta" (ver sección 6).

### 2.3 Lectura de notificaciones bancarias (opcional, desactivado por defecto)

Si activas *"Lectura de notificaciones"* en Ajustes → Detección bancaria, la app te explica primero qué va a hacer y, si aceptas, te lleva al ajuste de Android para concederle **acceso a las notificaciones**. Con ese acceso:

- Lee las notificaciones de las **apps bancarias que tú elijas** de la lista incluida en la app (bancos de España, Portugal, Reino Unido, Alemania, Francia, Italia, México y otros países).
- Si no eliges ningún banco, la app analiza las notificaciones que **parezcan un pago** (contienen un importe y una palabra como "compra", "cargo" o "transferencia", o el nombre de un sistema de pago como Bizum) y **descarta el resto sin guardarlo**.
- El texto se procesa **en tu móvil** para extraer importe, comercio y fecha.
- Si has configurado tu propia clave de IA (sección 2.5) y el análisis local no consigue interpretarlo, el texto puede enviarse a Gemini (Google).
- Los textos que sí corresponden a un pago se guardan temporalmente en la base de datos local para que puedas revisarlos y reprocesarlos. **Nunca se envían a servidores de ChillPocket.**
- Puedes desactivarlo cuando quieras desde ese mismo ajuste o retirando el permiso en los ajustes de Android.

### 2.4 Texto compartido desde otras apps (opcional, iniciado por ti)

Si desde otra app (por ejemplo, la de tu banco) usas "Compartir" y eliges ChillPocket, el texto compartido se analiza en tu móvil para crear una transacción. Igual que en 2.3, solo si tienes tu clave de IA configurada puede enviarse a Gemini cuando el análisis local no basta.

### 2.5 Inteligencia artificial — Gemini (opcional, desactivado por defecto)

Si configuras una clave de API propia de Google AI Studio (*Bring Your Own Key*):

- Las **imágenes de tickets o recibos**, el **audio** de voz y, cuando el análisis local falla, el **texto de notificaciones o compartido** se envían a la API de Gemini de Google para su análisis. Las imágenes y audios se eliminan de tu móvil inmediatamente después.
- Tu clave se almacena **cifrada en el almacenamiento seguro del dispositivo** y nunca se transmite a servidores de ChillPocket.
- Los datos enviados a Gemini están sujetos a la [Política de Privacidad de Google](https://policies.google.com/privacy) y a las [condiciones de la API de Gemini](https://ai.google.dev/gemini-api/terms). Eres responsable del uso y coste de tu propia clave.
- Si no configuras ninguna clave, esta funcionalidad está completamente desactivada y ningún dato se envía a Gemini.

### 2.6 Categorías y objetivos compartidos (opcional)

Si creas o te unes a una **categoría compartida** o a un **objetivo de ahorro compartido**, esa información se guarda en un servidor gestionado por ChillPocket (**Firebase / Google Cloud, región europe-west1**) para sincronizarla entre los miembros del grupo:

- De la categoría u objetivo: nombre, icono, tipo, meta y la lista de miembros (identificador anónimo + el **nombre visible** que tú elijas).
- De cada movimiento que publiques en ella: importe, fecha, nota, tu identificador anónimo y tu nombre visible.
- Solo pueden verlo los miembros del grupo, es decir, quienes tengan el **código de invitación**. Compártelo únicamente con personas de confianza.
- Tus transacciones **no compartidas** nunca se suben.
- Puedes salir de una categoría u objetivo cuando quieras. Los movimientos que ya compartiste con el grupo pueden seguir siendo visibles para sus miembros mientras el grupo exista. Con "Borrar cuenta" (sección 6) se eliminan tus vínculos con todos los grupos.

### 2.7 Avisos de la app

La app descarga ocasionalmente **avisos y novedades** publicados por ChillWorks-apps desde nuestro servidor (Firebase). Es una descarga de solo lectura: no se envía ningún dato tuyo.

### 2.8 Conexión bancaria — Open Banking (Enable Banking)

*Esta función se está desplegando de forma progresiva y puede no estar disponible en tu versión de la app.* Cuando la uses para vincular una cuenta bancaria real:

- La conexión se realiza mediante **Enable Banking**, un proveedor de servicios de información de cuentas (AISP) regulado bajo PSD2, con un flujo OAuth2 en el que autorizas el acceso directamente en la web de tu banco o de Enable Banking. **ChillPocket nunca ve ni almacena tus credenciales bancarias.**
- Tras autorizar la conexión, se guardan en nuestro servidor (Firebase / Google Cloud, región europe-west1) estos metadatos: IBAN, nombre del titular, nombre y país del banco, tipo de cuenta y fecha de validez del consentimiento. Se conservan mientras la conexión esté activa.
- Los movimientos (importe, fecha, concepto, comercio) se obtienen a través de Enable Banking y se transfieren a tu dispositivo para guardarse en tu base de datos local. **No conservamos un histórico de tus movimientos en el servidor.**
- Puedes desconectar un banco cuando quieras desde Ajustes → Detección bancaria. Al hacerlo se elimina permanentemente el registro de esa conexión (IBAN incluido) de nuestro servidor y se revoca el acceso en Enable Banking.
- El consentimiento tiene validez limitada (normalmente entre 90 y 180 días según el banco); después deberás renovarlo.
- Consulta la [Política de Privacidad de Enable Banking](https://enablebanking.com/privacy).

### 2.9 Publicidad — Google AdMob (solo usuarios gratuitos)

Si no tienes una suscripción activa de ChillPocket Pro, la app muestra un banner publicitario mediante Google AdMob.

- AdMob puede recopilar el **identificador publicitario del dispositivo** y datos técnicos para mostrar anuncios, personalizados o no según la configuración de tu dispositivo y la normativa de tu región.
- Esta recopilación está sujeta a la [Política de Privacidad de Google](https://policies.google.com/privacy). Puedes restablecer o desactivar la personalización del identificador publicitario en los ajustes de Android.
- Los usuarios Pro no ven publicidad.

### 2.10 Suscripciones — RevenueCat

La gestión de la suscripción ChillPocket Pro se realiza a través de Google Play y RevenueCat.

- RevenueCat recibe un identificador anónimo de la app y datos de compra (identificador de transacción, estado de la suscripción) para verificar tu plan.
- No tiene acceso a tus transacciones ni datos financieros.
- Consulta la [Política de Privacidad de RevenueCat](https://www.revenuecat.com/privacy).

### 2.11 Reportar un problema / Compartir experiencia (opcional, iniciado por ti)

Estas opciones de Ajustes abren un formulario externo de Google Forms. Enviarlo es voluntario y está sujeto a la política de privacidad de Google.

---

## 3. Datos que NO recopilamos

- ❌ No usamos analytics ni herramientas de telemetría (sin Firebase Analytics, Crashlytics ni similares).
- ❌ No recopilamos datos de localización.
- ❌ No accedemos a tus contactos.
- ❌ No pedimos tu nombre real, correo ni teléfono para usar la app.
- ❌ No vendemos ni cedemos datos a terceros.
- ❌ La app no está dirigida a menores de 13 años.

---

## 4. Dónde se almacenan tus datos

| Dato | Dónde |
|---|---|
| Transacciones, categorías, presupuestos, objetivos, preferencias | Tu dispositivo (base de datos local) |
| Clave de IA (si la configuras) | Tu dispositivo (almacenamiento cifrado) |
| Categorías y objetivos compartidos, metadatos de conexión bancaria, identificador anónimo | Firebase / Google Cloud, región europe-west1 (UE) |
| Datos enviados a Gemini, AdMob, RevenueCat, Enable Banking | Servidores de cada proveedor, según sus políticas |

No existe ningún servidor de copia de seguridad de tus transacciones gestionado por ChillPocket, y la app no participa en la copia automática de Android en la nube. Cuando desinstalas la app, los datos locales se eliminan.

---

## 5. Seguridad

- La clave de IA se almacena cifrada mediante el almacenamiento seguro del sistema operativo.
- Las comunicaciones con Firebase, Gemini, RevenueCat y Enable Banking van cifradas (HTTPS).
- El acceso a los datos compartidos en Firebase está limitado por reglas de seguridad a los miembros de cada grupo.
- Las suscripciones se verifican a través de los canales seguros de Google Play y RevenueCat.

---

## 6. Tus derechos

- **Acceso y portabilidad:** exporta todos tus datos en XLSX, CSV o PDF desde Ajustes → Descarga.
- **Rectificación:** edita o elimina cualquier transacción, categoría u objetivo desde la propia app.
- **Supresión:** en Ajustes → Zona de peligro → **Borrar cuenta** se eliminan de forma irreversible tu base de datos local, tus preferencias, tus claves de IA, tus conexiones bancarias, tu participación en categorías y objetivos compartidos y tu cuenta anónima en nuestro servidor.
- **Retirar permisos:** puedes desactivar la lectura de notificaciones, el micrófono o la cámara en cualquier momento desde los ajustes de Android.

Para cualquier consulta relacionada con la privacidad, escribe a **development@chillworks-apps.com**. Si consideras que no hemos atendido tus derechos, puedes reclamar ante la Agencia Española de Protección de Datos (www.aepd.es).

---

## 7. Cambios en esta política

Si realizamos cambios materiales, actualizaremos la fecha al inicio del documento y, cuando sea relevante, lo indicaremos en la app. Te recomendamos revisarla periódicamente.

---

## 8. Legislación aplicable

Esta política se rige por la normativa española y europea de protección de datos (RGPD — Reglamento (UE) 2016/679 y LOPDGDD).
