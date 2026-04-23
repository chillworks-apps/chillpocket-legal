# Política de Privacidad — ChillPocket

**Última actualización:** 23 de abril de 2026  
**Desarrollador:** ChillWorks-apps
**Contacto:** development@chillworks-apps.com

---

## 1. Quién somos

ChillPocket es una aplicación de control financiero personal desarrollada por ChillWorks-apps. Esta política explica qué datos se recogen, cómo se usan y qué derechos tienes.

---

## 2. Datos que recopilamos y por qué

### 2.1 Datos que tú introduces (almacenados únicamente en tu dispositivo)

| Dato | Propósito |
|---|---|
| Transacciones (importe, fecha, nota, comercio) | Funcionalidad principal de la app |
| Categorías de gasto e ingreso | Organización de transacciones |
| Saldo inicial y preferencias (moneda, separadores) | Personalización de la app |
| Perfil laboral (tipo de empleo) | Módulo "Mi Trabajo" |
| Controles de gasto y objetivos de ahorro | Funcionalidad de presupuesto |

**Todos estos datos se guardan exclusivamente en la base de datos SQLite local de tu dispositivo. No se envían a ningún servidor ni se comparten con terceros.**

### 2.2 Notificaciones bancarias (opcional, desactivado por defecto)

Si activas la función *"Registrar compras automáticamente"* en Ajustes, la app solicita el permiso de Acceso a Notificaciones de Android para leer las notificaciones push de tus apps bancarias.

- Solo se leen notificaciones de entidades bancarias conocidas (BBVA, CaixaBank, Santander, Sabadell, Bankinter, ING, Openbank, EVO Banco).
- El texto leído se procesa localmente para extraer importe, comercio y fecha.
- Si el procesamiento local falla, el texto puede enviarse a la API de Gemini (Google) para su análisis (ver sección 2.3).
- Los textos de notificaciones se almacenan temporalmente en la base de datos local para auditoría y reprocesamiento. No se envían a servidores propios.
- Puedes desactivar esta función en cualquier momento desde Ajustes → Conexión Bancaria.

### 2.3 Inteligencia Artificial — Gemini (opcional, desactivado por defecto)

Si configuras una clave de API propia de Google AI Studio (función BYOK — *Bring Your Own Key*):

- Las imágenes de tickets/recibos, el audio de voz y, en caso de fallo del parser local, el texto de notificaciones bancarias se envían a la API de Gemini Flash de Google para su análisis.
- **Tu clave de API se almacena cifrada en el Keystore seguro del dispositivo** (`flutter_secure_storage`) y nunca se transmite a servidores de ChillPocket.
- Los datos enviados a Gemini están sujetos a la [Política de Privacidad de Google](https://policies.google.com/privacy) y a las [condiciones de uso de la API de Gemini](https://ai.google.dev/gemini-api/terms).
- Si no configuras ninguna clave de API, esta funcionalidad está completamente desactivada.

### 2.4 Publicidad — Google AdMob (solo usuarios gratuitos)

Si no tienes una suscripción activa de ChillPocket Pro, la app muestra un banner publicitario mediante Google AdMob.

- AdMob puede recopilar el **identificador publicitario del dispositivo (GAID)** para mostrar anuncios relevantes.
- Esta recopilación está sujeta a la [Política de Privacidad de Google](https://policies.google.com/privacy).
- Los usuarios con suscripción Pro no ven publicidad y AdMob no recopila datos en su caso.

### 2.5 Suscripciones — RevenueCat

La gestión de compras y suscripciones In-App se realiza a través de RevenueCat.

- RevenueCat puede recopilar datos de compra (ID de transacción, estado de suscripción) para verificar el estado de tu suscripción.
- No tiene acceso a tus datos financieros ni de transacciones.
- Consulta la [Política de Privacidad de RevenueCat](https://www.revenuecat.com/privacy).

### 2.6 Categorías compartidas — MQTT P2P (opcional)

Si usas la función de categorías compartidas:

- Las transacciones de esa categoría se publican cifradas (AES-256-CBC) en un broker MQTT público (HiveMQ).
- Solo los dispositivos con la clave de cifrado correcta (generada localmente en tu dispositivo) pueden descifrar los mensajes.
- Los mensajes son efímeros (TTL de 7 días) y no contienen datos de identificación personal más allá del nombre de display que tú elijas.

### 2.7 Reportar problemas / Compartir experiencia (opcional, iniciado por ti)

Si usas las opciones de "Reportar un problema" o "Comparte tu experiencia" en Ajustes, se abre un formulario externo de Google Forms. El envío de ese formulario es completamente voluntario y está sujeto a la política de privacidad de Google.

---

## 3. Datos que NO recopilamos

- ❌ No tenemos servidores propios que almacenen tus datos.
- ❌ No usamos analytics ni herramientas de telemetría (sin Firebase Analytics, sin Crashlytics, sin Sentry).
- ❌ No recopilamos datos de localización (GPS).
- ❌ No accedemos a tus contactos.
- ❌ No vendemos ni cedemos datos a terceros.
- ❌ La app no está dirigida a menores de 13 años.

---

## 4. Dónde se almacenan tus datos

Todos tus datos financieros residen en la base de datos SQLite del almacenamiento interno de tu dispositivo. Cuando desinstalas la app, estos datos se eliminan permanentemente.

No existe ningún servidor de backup gestionado por ChillPocket.

---

## 5. Seguridad

- La clave de API de Gemini se almacena cifrada en el Keystore del sistema operativo.
- Las comunicaciones MQTT usan cifrado AES-256-CBC extremo a extremo.
- Las suscripciones se verifican a través de canales seguros de Google Play y RevenueCat.

---

## 6. Tus derechos

Dado que todos tus datos se almacenan localmente en tu dispositivo, tienes control total sobre ellos:

- **Acceso:** puedes exportar tus datos en formato CSV o PDF desde Ajustes → Descarga.
- **Eliminación:** puedes eliminar transacciones individualmente o desinstalar la app para borrar todos los datos.
- **Portabilidad:** la exportación CSV incluye todas tus transacciones.

Para cualquier consulta relacionada con la privacidad, contacta con: **development@chillworks-apps.com**

---

## 7. Cambios en esta política

Si realizamos cambios materiales en esta política, actualizaremos la fecha al inicio del documento. Te recomendamos revisarla periódicamente.

---

## 8. Legislación aplicable

Esta política se rige por la normativa española y europea de protección de datos (RGPD — Reglamento (UE) 2016/679).
