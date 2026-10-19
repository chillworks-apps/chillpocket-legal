# Política de Privacidad — ChillPocket

**Última actualización:** 19 de octubre de 2026  
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
| Transacciones (importe, moneda, fecha, nota, comercio, categoría) | Funcionalidad principal de la app |
| Movimientos recurrentes y programados | Generación automática de transacciones |
| Categorías de gasto e ingreso | Organización de transacciones |
| Saldo inicial, ajustes de saldo y preferencias (moneda, formato de fecha y número, idioma, tema) | Personalización de la app |
| Controles de gasto, objetivos de ahorro y reglas de ahorro automático | Funcionalidad de presupuesto |
| Resúmenes semanales y mensuales generados por la app | Función "Pendientes → Resumen" |

Todos estos datos se guardan en la base de datos local de tu dispositivo. **No se envían a servidores de ChillPocket ni se comparten con terceros**, salvo en las funciones opcionales descritas en las secciones 2.2 a 2.12. Los resúmenes y las alertas se calculan en tu móvil, también cuando la app está cerrada (una tarea periódica del sistema), sin enviar nada fuera.

ChillPocket está **excluida de la copia de seguridad automática de Android en la nube** (Google Drive): tus datos no se suben a tu cuenta de Google. Si cambias de móvil, usa la exportación e importación de datos (Ajustes → Descarga) para llevarlos contigo.

### 2.2 Identificador anónimo (Firebase)

Al abrir la app por primera vez se crea una **cuenta anónima** en Firebase Authentication (Google). Es un identificador aleatorio sin nombre, correo ni teléfono. Sirve para que las funciones que necesitan un servidor (categorías compartidas, conexión bancaria, borrado de cuenta) sepan qué datos son tuyos. Puedes eliminarlo en cualquier momento con "Borrar cuenta" (ver sección 6).

Si reinstalas la app o borras sus datos, se crea un identificador nuevo y el anterior queda huérfano. Para no conservar datos que nadie puede reclamar, **las cuentas anónimas sin actividad durante 180 días se eliminan automáticamente** de nuestro servidor, junto con sus datos: se cierran sus conexiones bancarias, se retira a esa cuenta de sus categorías y objetivos compartidos y se borra su registro (sección 4).

### 2.3 Lectura de notificaciones bancarias (opcional, desactivado por defecto; solo Android)

Si activas *"Habilitar lectura"* en Ajustes → Detección bancaria, la app te explica primero qué va a hacer y, si aceptas, te lleva al ajuste de Android para concederle **acceso a las notificaciones**. Con ese acceso:

- Lee las notificaciones de las **apps bancarias que tú elijas** en "Mis bancos", de un catálogo que cubre bancos y neobancos de 41 países de Europa y América.
- Si no eliges ningún banco, la app analiza las notificaciones que **parezcan un pago** (contienen un importe y una palabra como "compra", "cargo" o "transferencia" en alguno de los idiomas que reconoce, o el nombre de un sistema de pago como Bizum) y **descarta el resto sin guardarlo**.
- El texto se procesa **en tu móvil** para extraer importe, moneda, comercio y fecha. La app aprende el formato de los avisos de tu banco y lo guarda en tu móvil para no necesitar la IA la próxima vez.
- Si has configurado tu propia clave de IA (sección 2.5) y el análisis local no consigue interpretarlo, el título y el texto del aviso pueden enviarse a Gemini (Google). Sin clave, el aviso se queda en Pendientes para que lo revises a mano.
- El procesamiento también funciona **con la app cerrada** o tras reiniciar el móvil: una tarea del sistema procesa los avisos que llegaron mientras tanto, siempre en tu dispositivo.
- Los textos que sí corresponden a un pago se guardan temporalmente en la base de datos local para que puedas revisarlos y reprocesarlos, y **se purgan a los 90 días**. **Nunca se envían a servidores de ChillPocket.**
- Un aviso en una moneda distinta de la tuya se queda en espera hasta que escribas el importe convertido; no se calcula ningún tipo de cambio ni se consulta ningún servicio externo.
- Puedes desactivarlo cuando quieras desde ese mismo ajuste o retirando el permiso en los ajustes de Android. Si Android retira el acceso, la app lo refleja al volver a abrirla.

Esta función no existe en iOS, porque el sistema no permite a las apps leer notificaciones de otras apps.

### 2.4 Texto e imágenes compartidos desde otras apps (opcional, iniciado por ti)

Si desde otra app usas "Compartir" y eliges ChillPocket:

- Un **texto** (por ejemplo, el aviso de tu banco) se analiza en tu móvil para crear una transacción, igual que en 2.3. Solo si tienes tu clave de IA configurada puede enviarse a Gemini cuando el análisis local no basta.
- Una **imagen** (por ejemplo, la foto de un ticket desde la galería; Android, hasta 10 MB en JPEG, PNG, WEBP o HEIC) sigue el mismo camino que una foto hecha desde la app: se copia temporalmente, se envía a Gemini con tu clave (sección 2.5) y la copia temporal se elimina siempre, también si cancelas. Sin clave de IA, la app no puede leer la imagen.

Cada texto o imagen compartido se consume una sola vez: no queda guardado en la app.

### 2.5 Inteligencia artificial — Gemini (opcional, desactivado por defecto)

Si configuras una clave de API propia de Google AI Studio (*Bring Your Own Key*):

- Lo que analiza la IA (**fotos de tickets o recibos**, lo que **dictas** y, cuando el análisis local falla, los **textos de los avisos y movimientos del banco**) va **de tu móvil a Google con tu clave, sin pasar por nuestros servidores**. Las imágenes y audios se eliminan de tu móvil inmediatamente después, y las fotos de recibos que queden en la caché se limpian de forma periódica.
- **Entrada por voz:** el dictado usa el servicio de reconocimiento de voz de tu móvil (en Android, el de Google) para convertir tu voz en texto, según la configuración de tu dispositivo; a Gemini se envía solo el **texto transcrito**. Únicamente si ese servicio no está disponible, la app graba el audio y lo envía a Gemini para transcribirlo.
- La app puede pedir a Gemini que le enseñe el formato de un aviso bancario y **guarda ese patrón en tu móvil**, para que los avisos siguientes del mismo tipo se interpreten localmente sin volver a enviarlos.
- Tu clave se almacena **cifrada en el almacenamiento seguro del dispositivo**, viaja a Google en una cabecera de la petición (nunca en la dirección) y nunca se transmite a servidores de ChillPocket.
- Los datos enviados a Gemini están sujetos a la [Política de Privacidad de Google](https://policies.google.com/privacy) y a las [condiciones de la API de Gemini](https://ai.google.dev/gemini-api/terms). Ten en cuenta que, con una clave del nivel gratuito y fuera del Espacio Económico Europeo, Suiza y el Reino Unido, Google puede usar lo enviado para mejorar sus productos. Eres responsable del uso y coste de tu propia clave.
- Si no configuras ninguna clave, esta funcionalidad está completamente desactivada y ningún dato se envía a Gemini.

### 2.6 Categorías y objetivos compartidos (opcional; sincronización con Pro)

Si creas o te unes a una **categoría compartida** o a un **objetivo de ahorro compartido**, esa información se guarda en un servidor gestionado por ChillPocket (**Firebase / Google Cloud, región europe-west1**) para sincronizarla entre los miembros del grupo:

- De la categoría u objetivo: nombre, icono, tipo, meta, reparto entre miembros y la lista de miembros (identificador anónimo + el **nombre visible** que tú elijas).
- De cada movimiento que publiques en ella: importe, fecha, nota, quién lo pagó, tu identificador anónimo y tu nombre visible. Las compras detectadas desde el banco se publican con su nota tal cual, que puede incluir los últimos dígitos de la tarjeta si el aviso del banco los lleva; revísala antes de publicar si no quieres compartirla.
- Un **historial del grupo** con líneas como "Ana entró en el grupo", "Bea cambió el reparto" o "Carlos saldó 10 €", visible para los miembros.
- Solo pueden verlo los miembros del grupo, es decir, quienes tengan el **código de invitación**. Compártelo únicamente con personas de confianza.
- Tus transacciones **no compartidas** nunca se suben. La importación de archivos CSV/XLSX nunca publica en un grupo.
- Los datos del grupo se guardan también **en tu móvil** (caché de Firestore) para que puedas verlos sin conexión; se eliminan con "Borrar cuenta".
- Sin suscripción Pro, tu app **deja de sincronizar** los grupos y muestra la última foto de sus datos; solo puedes salir del grupo y borrar tus propios movimientos.
- Cualquier miembro con Pro puede **pausar o quitar** a otra persona del grupo. Si te quitan, tu app te avisa y la categoría pasa a ser normal en tu móvil.
- Puedes salir de una categoría u objetivo cuando quieras (borrarla desde Ajustes equivale a salir). Los movimientos que ya compartiste y las líneas del historial con tu nombre visible pueden seguir siendo visibles para los miembros mientras el grupo exista, y lo que tuvieras pendiente de saldar sigue atribuido a ti. Si eras la última persona, el grupo se cierra. Con "Borrar cuenta" (sección 6) se te retira de todos los grupos de la misma forma.

### 2.7 Avisos y configuración de la app

La app descarga ocasionalmente **avisos y novedades** publicados por ChillWorks-apps y **datos de configuración de la app** (por ejemplo, si la prueba gratuita está activa y cuánto dura) desde nuestro servidor (Firebase). Es una descarga de solo lectura: no se envía ningún dato tuyo.

### 2.8 Conexión bancaria — Open Banking (Enable Banking)

*Esta función no está disponible todavía: la app la muestra como "Muy pronto" y el servidor la mantiene desactivada.* Cuando se active y la uses para vincular una cuenta bancaria real:

- La conexión se realizará mediante **Enable Banking**, un proveedor de servicios de información de cuentas (AISP) regulado bajo PSD2, con un flujo OAuth2 en el que autorizas el acceso directamente en la web de tu banco o de Enable Banking. **ChillPocket nunca verá ni almacenará tus credenciales bancarias.**
- Tras autorizar la conexión, se guardarán en nuestro servidor (Firebase / Google Cloud, región europe-west1) estos metadatos: IBAN, nombre del titular, nombre y país del banco, tipo de cuenta y fecha de validez del consentimiento. Se conservarán mientras la conexión esté activa.
- Los movimientos (importe, fecha, concepto, comercio) se obtendrán a través de Enable Banking y se transferirán a tu dispositivo para guardarse en tu base de datos local. **No conservaremos un histórico de tus movimientos en el servidor.** El concepto de un movimiento puede incluir nombres o IBAN de terceros; si tienes clave de IA, el concepto puede enviarse a Gemini para identificar el comercio.
- Podrás desconectar un banco cuando quieras desde Ajustes → Detección bancaria. Al hacerlo se eliminará permanentemente el registro de esa conexión (IBAN incluido) de nuestro servidor y se revocará el acceso en Enable Banking.
- El consentimiento tendrá validez limitada (normalmente entre 90 y 180 días según el banco); después deberás renovarlo.
- Consulta la [Política de Privacidad de Enable Banking](https://enablebanking.com/privacy).

### 2.9 Publicidad — Google AdMob (solo usuarios gratuitos)

Si no tienes una suscripción activa de ChillPocket Pro, la app muestra un banner publicitario mediante Google AdMob.

- **Primero tu consentimiento.** En el Espacio Económico Europeo, el Reino Unido y Suiza, antes de cargar ningún anuncio la app te muestra el formulario de consentimiento de Google para que decidas si aceptas anuncios personalizados. El servicio de anuncios no se inicia hasta que ese formulario termina, y la medición de AdMob no empieza antes. Si no das tu consentimiento, los anuncios que veas no serán personalizados.
- Puedes **revisar o cambiar tu decisión** cuando quieras en Ajustes → *Opciones de privacidad de anuncios* (al final de Ajustes; aparece cuando la normativa de tu región lo exige).
- AdMob puede recopilar el **identificador publicitario del dispositivo** y datos técnicos para mostrar anuncios, personalizados o no según tu decisión, la configuración de tu dispositivo y la normativa de tu región.
- Esta recopilación está sujeta a la [Política de Privacidad de Google](https://policies.google.com/privacy). Puedes restablecer o desactivar la personalización del identificador publicitario en los ajustes de Android.
- Los usuarios Pro, y quien está en la prueba gratuita, no ven publicidad ni reciben el formulario de consentimiento.

### 2.10 Suscripciones — RevenueCat

La gestión de la suscripción ChillPocket Pro se realiza a través de Google Play (y App Store cuando esté disponible) y RevenueCat.

- RevenueCat recibe un identificador anónimo generado para la app y datos de compra (identificador de transacción, estado de la suscripción) para verificar tu plan. Ese identificador no está ligado a tu nombre ni a tu cuenta anónima de Firebase.
- No tiene acceso a tus transacciones ni datos financieros.
- La pantalla de suscripción se muestra en el idioma de la app y el precio se consulta en la tienda en tu moneda local.
- Consulta la [Política de Privacidad de RevenueCat](https://www.revenuecat.com/privacy).

### 2.11 Reportar un problema / Compartir experiencia (opcional, iniciado por ti)

Estas opciones de Ajustes abren un formulario externo de Google Forms. Enviarlo es voluntario y está sujeto a la política de privacidad de Google.

### 2.12 Notificaciones que te envía la app

Con tu permiso para mostrar notificaciones, la app puede avisarte de: pagos detectados desde el banco, un control de gasto que se acerca a su límite, el recordatorio semanal, el resumen semanal o mensual listo, aportes de ahorro automático y el fin de la prueba gratuita. Todas se generan **en tu móvil** con tus propios datos; no hay servidor de notificaciones *push* ni se envía nada fuera. Puedes apagarlas en Ajustes ("Notificaciones de ChillPocket") o retirar el permiso en Android.

---

## 3. Datos que NO recopilamos

- ❌ No usamos analytics ni herramientas de telemetría (sin Firebase Analytics, Crashlytics ni similares).
- ❌ No recopilamos datos de localización.
- ❌ No accedemos a tus contactos.
- ❌ No pedimos tu nombre real, correo ni teléfono para usar la app.
- ❌ No vendemos ni cedemos datos a terceros.
- ❌ La app no descarga fuentes ni otros recursos de terceros al arrancar: todo va incluido en la instalación.
- ❌ La app no está dirigida a menores de 13 años.

---

## 4. Dónde se almacenan tus datos y cuánto tiempo

| Dato | Dónde | Cuánto tiempo |
|---|---|---|
| Transacciones, categorías, presupuestos, objetivos, resúmenes, preferencias | Tu dispositivo (base de datos local) | Hasta que los borres o desinstales la app |
| Textos de avisos bancarios guardados para revisar | Tu dispositivo | 90 días |
| Clave de IA (si la configuras) | Tu dispositivo (almacenamiento cifrado) | Hasta que la borres |
| Tu decisión sobre el consentimiento de anuncios | Tu dispositivo | Hasta que la cambies |
| Copia local de los grupos compartidos (caché) | Tu dispositivo | Hasta "Borrar cuenta" |
| Categorías y objetivos compartidos, metadatos de conexión bancaria, identificador anónimo | Firebase / Google Cloud, región europe-west1 (UE) | Mientras uses la app; las cuentas anónimas inactivas 180 días se eliminan automáticamente |
| Datos enviados a Gemini, AdMob, RevenueCat, Enable Banking | Servidores de cada proveedor, según sus políticas | Según cada proveedor |

No existe ningún servidor de copia de seguridad de tus transacciones gestionado por ChillPocket, y la app no participa en la copia automática de Android en la nube. Cuando desinstalas la app, los datos locales se eliminan.

---

## 5. Seguridad

- La clave de IA se almacena cifrada mediante el almacenamiento seguro del sistema operativo y nunca aparece en direcciones ni en los mensajes de error.
- Las comunicaciones con Firebase, Gemini, RevenueCat y Enable Banking van cifradas (HTTPS).
- Las peticiones a nuestro servidor (Firebase) se verifican con **Firebase App Check**, que usa la API Play Integrity de Google para comprobar que proceden de la app original. Esta verificación no incluye tus datos financieros.
- El acceso a los datos compartidos en Firebase está limitado por reglas de seguridad a los miembros de cada grupo, y las operaciones del grupo (entrar, salir, quitar, cambiar el reparto) las valida el servidor.
- Las suscripciones se verifican a través de los canales seguros de Google Play y RevenueCat.
- Los registros técnicos de la app no incluyen códigos de invitación, claves ni datos financieros.

---

## 6. Tus derechos

- **Acceso y portabilidad:** exporta todos tus datos en XLSX, CSV o PDF desde Ajustes → Descarga.
- **Rectificación:** edita o elimina cualquier transacción, categoría u objetivo desde la propia app.
- **Supresión:** en Ajustes → Zona de peligro → **Borrar cuenta** se eliminan de forma irreversible tu base de datos local, tus preferencias (idioma y tema incluidos), tu clave de IA, las notificaciones pendientes, la copia local de los grupos, tus conexiones bancarias, tu participación en categorías y objetivos compartidos y tu cuenta anónima en nuestro servidor. Quedan en el móvil únicamente dos cosas que no son de la cuenta sino del dispositivo: la marca de que la prueba gratuita ya se usó (es una por móvil) y el estado de tu suscripción en la tienda, que gestionan Google Play y RevenueCat.
- **Retirar permisos:** puedes desactivar la lectura de notificaciones, el permiso para mostrar notificaciones, el micrófono o la cámara en cualquier momento desde los ajustes de Android.
- **Publicidad:** puedes cambiar tu decisión sobre los anuncios personalizados en Ajustes → *Opciones de privacidad de anuncios* (sección 2.9).

Para cualquier consulta relacionada con la privacidad, escribe a **development@chillworks-apps.com**. Si consideras que no hemos atendido tus derechos, puedes reclamar ante la Agencia Española de Protección de Datos ([www.aepd.es](https://www.aepd.es)).

---

## 7. Cambios en esta política

Si realizamos cambios materiales, actualizaremos la fecha al inicio del documento y, cuando sea relevante, lo indicaremos en la app. Te recomendamos revisarla periódicamente.

---

## 8. Legislación aplicable

Esta política se rige por la normativa española y europea de protección de datos (RGPD — Reglamento (UE) 2016/679 y LOPDGDD).
