# Política de privacidad de Popt

*Este documento es una traducción de la versión en inglés. Solo la versión en inglés es legalmente vinculante: [privacy-policy_EN.md](privacy-policy_EN.md).*

Última actualización: 2 de noviembre de 2026

## Resumen

Popt es una app que pone la privacidad por delante. El contenido que guardas en Popt se cifra en tu dispositivo antes de enviarse a ningún sitio, con claves que no tenemos (cifrado de extremo a extremo real). No podemos leer tus tareas, notas, diario, fotos, biblioteca, publicaciones ni mensajes, y tampoco puede hacerlo nadie que entre en nuestros servidores. Lo que sí ven nuestros servidores es la parte técnica: qué cuentas tienen contenido compartido, las fechas de creación y modificación del contenido, y tu nombre y tu avatar de Popt, para que puedas ver quién está en un grupo contigo aunque no sean tus amigos.

No usamos tus datos para entrenar IA. No los vendemos a terceros. No creamos perfiles sobre ti ni te mostramos anuncios de ningún tipo. La app se conecta a nuestros propios servidores para sincronizar y respaldar tu contenido en todos tus dispositivos, y para que funcionen el uso compartido, los mensajes y nuestro servicio de búsqueda de contenidos para añadir a tu biblioteca de Popt. La app también se comunica con servicios de terceros que nos prestan servicios esenciales:

* **Apple:** búsqueda en Mapas, Lugares y Música, todo cubierto por las estrictas políticas de privacidad de Apple.
* **Google:** gestión de cuentas y autenticación con Firebase. Alojamiento de servidores y bases de datos con Google Cloud.
* **PowerSync:** tus datos pasan por los servidores de PowerSync para llegar a tus dispositivos.
* **Cloudflare:** tus fotos y archivos cifrados se guardan en Cloudflare R2. La app sube y descarga directamente de R2.

Estos terceros no tienen acceso a tu contenido, que en cualquier caso está completamente cifrado.

Puedes exportarlo todo, eliminarlo todo y comprobar lo que afirmamos con las herramientas abiertas que publicamos.

## Quiénes somos

Popt es un producto de Skile SA, una empresa con sede en Suiza. Skile SA es el responsable del tratamiento de los datos de Popt: decidimos qué recopila la app y por qué, y respondemos por ello. Nuestra jurisdicción es Suiza. Popt se usa en Europa, Estados Unidos y otros lugares, y nos esforzamos por cumplir las leyes de protección de datos más estrictas. Hoy es el Reglamento General de Protección de Datos de la UE (RGPD, GDPR en inglés), así que, estés en el país que estés, tienes las protecciones del RGPD.

Puedes escribirnos sobre cualquier punto de esta política a support@popt.com. Nuestra dirección es Skile SA, Rue de Riant-Coteau 7, 1196 Gland, Suiza.

No tenemos socios publicitarios, ni intermediarios de datos, ni ninguna empresa de analítica detrás de la app. Los únicos terceros implicados son los proveedores de servicios enumerados en [Servicios a los que se conecta la app](#servicios-a-los-que-se-conecta-la-app), y nombramos a cada uno de ellos.

## Cómo se protege tu contenido

Todo lo que escribes, fotografías o guardas en Popt se cifra en tu dispositivo antes de salir de él, con claves que solo tienen tú y las personas con las que compartes. Nuestros servidores almacenan y transmiten ese contenido cifrado. Usamos criptografía estándar del sector y nada de invención propia: AES-256 para tu contenido y tus archivos, y claves de curva elíptica para compartirlos. El diseño completo está publicado y se puede comprobar de forma independiente (consulta [Compruébalo por tu cuenta](#compruébalo-por-tu-cuenta)).

**Tus claves nunca salen de tu dispositivo en forma legible.** Guardamos una copia bloqueada en nuestros servidores para poder configurar un dispositivo nuevo, y lo único que puede desbloquearla es tu **código de recuperación**, que se genera en tu dispositivo y que nosotros nunca vemos. El código de recuperación es el único secreto que debes guardar. Si lo pierdes y pierdes todos los dispositivos con sesión iniciada, no podemos recuperar tu contenido por ti.

**El contenido compartido** se cifra exactamente para las personas que participan en él, y cada una tiene su propia clave para acceder a él. Cuando se quita a alguien, lo que se comparte a partir de ese momento se cifra con una clave nueva que esa persona no tiene.

**Las fotos y los archivos** se cifran en tu dispositivo antes de subirse, y también sus nombres, tipos y dimensiones. Cada archivo tiene su propia clave, que viaja dentro del elemento cifrado al que pertenece, así que una foto solo puede leerla quien pueda leer la nota, la lista o la publicación en la que está. En el almacenamiento, un archivo es solo un nombre aleatorio y un bloque de datos cifrado.

**Las notificaciones push** también están cifradas. La vista previa de una notificación (el nombre de un elemento, las primeras palabras de un comentario) va sellada para que solo los dispositivos de destino puedan abrirla. Las notificaciones pasan por Firebase Cloud Messaging de Google y después por el servicio push de Apple; ambos, como nuestro propio servidor de notificaciones, ven los identificadores de la cuenta de origen y de la cuenta de destino y el tipo de evento (mensaje, publicación, nuevo contenido compartido...), nunca lo que dice.

### Lo que no está cifrado

Un servidor que almacena y entrega contenido cifrado tiene que saber a qué cuenta pertenece, con qué cuentas está compartido, qué dispositivo lo actualizó por última vez y cuándo se creó o se actualizó. Estos son los datos que nuestros servidores pueden leer, y la razón por la que existe cada uno:

- **Identificadores de cuenta.** Para que el servidor pueda entregar cada elemento a los dispositivos correctos y a nadie más.
- **Cuándo se creó, cambió o eliminó cada elemento, y qué dispositivos lo actualizaron por última vez.** Así se reconcilian dos dispositivos que editaron lo mismo sin conexión: sin esto, el servidor no sabría qué cambio es el más reciente y se perderían ediciones. El identificador de dispositivo es el identificador de proveedor de Apple (IDFV): es específico de Popt en ese dispositivo, no es el identificador de publicidad y no sirve para reconocerte en otras apps. Se restablece cuando se elimina Popt del dispositivo.
- **Cómo se agrupa el contenido.** A qué elemento de nivel superior (una lista, una nota, una publicación, un proyecto) pertenece cada pieza. El servidor almacena, entrega y protege el contenido como elementos completos, así que tiene que saber dónde termina uno y empieza el siguiente. La estructura dentro de un elemento, qué línea va debajo de cuál, está cifrada.
- **Tu nombre, tu línea de estado y tu avatar de Popt.** Se mantienen legibles para que todos los participantes de una publicación o una lista compartida puedan ver quién más está ahí, incluidas personas que no son tus amigos, y para que alguien a quien invitas pueda ver quién lo invita. La app lo indica donde editas tu perfil.
- **Qué conversaciones has silenciado y la fecha en que abriste cada una por última vez.** Nuestro servidor de notificaciones lee estos datos para dejar de avisarte de una conversación que silenciaste y para no alertarte de algo que ya has visto. Registra identificadores de conversación, no contenidos.
- **Cuánto almacenamiento usas.** Cloudflare, donde se guardan los archivos cifrados, ve el tamaño de cada uno, como cualquier almacén de archivos. Lo sumamos por cuenta para aplicar el límite de almacenamiento de tu plan, y liberamos un archivo cuando ya nada apunta a él.

## Los datos que recopilamos y por qué

Recopilamos lo mínimo que la app necesita para funcionar, y nada para saber cosas sobre ti.

- **Tu dirección de correo electrónico.** Para iniciar tu sesión y reconocerte cuando nos escribes. Nos la das tú al iniciar sesión, o nos la dan Apple o Google cuando inicias sesión con ellos (Iniciar sesión con Apple puede ocultarla tras el relay de Apple). La guarda Firebase Authentication; nuestra propia base de datos conserva solo un hash de ella.
- **Tu nombre, tu línea de estado y tu avatar de Popt.** Para que tus amigos te reconozcan. Solo el nombre es obligatorio. Se guardan sin cifrar, como se explica arriba.
- **Tu contenido cifrado y sus metadatos.** Para sincronizarlo entre tus dispositivos y con las personas con las que compartes.
- **Identificadores anónimos de dispositivo.** Para notificar a tus dispositivos y distinguirlos entre sí. Usa el `identifierForVendor` de Apple, que protege la privacidad.
- **Tus recibos de suscripción.** Para desbloquear Popt Pro en todos tus dispositivos. Vienen de Apple cuando te suscribes; nunca vemos datos de pago.
- **Registros de solicitudes** (dirección IP, hora, ruta). Para mantener el servicio en marcha e investigar abusos, como cualquier servidor web.
- **Denuncias de abuso.** Para actuar contra comportamientos dañinos. Vienen de las personas que las envían.

**Lo que no recopilamos:** tu fecha de nacimiento, tus contactos, tu fototeca, tu ubicación, analíticas sobre cómo usas la app ni un identificador de publicidad.

**Bases legales.** Tratamos tus datos para prestarte el servicio que pediste (el contrato contigo), porque decidiste compartir algo o conceder un permiso (consentimiento, que puedes retirar), para mantener la seguridad del servicio y atender las denuncias de abuso (nuestro interés legítimo y, en parte, una obligación legal), y para cumplir obligaciones contables y fiscales (obligación legal).

**Nunca vendemos datos, nunca los compartimos con fines publicitarios y nunca usamos tu contenido para entrenar nada.**

## Servicios a los que se conecta la app

Esta es la lista completa. Si la app se comunica con algo, está aquí.

### Servidores de Popt

Funcionan en Google Cloud, en Estados Unidos, y las fotos y los archivos cifrados se guardan en Cloudflare, también en Estados Unidos. Lo decimos claramente porque la ubicación importa, y por lo poco que importa aquí: lo que hay en esos servidores es contenido que no podemos leer, más los metadatos enumerados arriba. Tu contenido es tan ilegible en un centro de datos de Estados Unidos como lo sería en uno suizo, y los metadatos están protegidos por las mismas reglas estén donde estén.

Todos están bajo `*.popt.com`. Esto es lo que envía cada función de la app:

- **Sincronización entre tus dispositivos.** Tu contenido cifrado, los metadatos enumerados arriba y la prueba de que has iniciado sesión.
- **Amigos y uso compartido.** Los identificadores de las cuentas conectadas como amigos, los identificadores de las cuentas que pertenecen a cada lista, proyecto o publicación compartidos, y copias bloqueadas de las claves compartidas.
- **Mensajes.** Tus mensajes cifrados y los identificadores de cuenta de las dos partes de una conversación.
- **Notificaciones.** La dirección que Apple nos da para llegar a tu dispositivo, los identificadores de cuenta del remitente y de los destinatarios, y la vista previa cifrada.
- **Popt Pro.** El recibo de Apple de tu suscripción, para que Pro pueda desbloquearse en todos tus dispositivos.
- **Inicio de sesión por correo.** Tu dirección de correo electrónico, para poder enviarte el código de un solo uso.
- **Añadir a tu biblioteca.** Tu búsqueda de un libro, una película, una serie, un juego o un pódcast, con tu idioma y tu franja de edad. Las búsquedas no se registran.
- **Publicar un elemento de biblioteca como enlace.** El elemento que decidiste publicar. El elemento publicado no está vinculado a tu cuenta.
- **Denunciar abusos.** Tu denuncia, cifrada y legible solo por nuestro equipo de revisión.
- **Avatares.** El estilo que elegiste y un número aleatorio a partir del cual se dibuja el avatar. Nada sobre ti.

Nuestros servidores conservan registros de solicitudes estándar durante 30 días: qué dirección llamó a qué función, y cuándo.

### Servicios de Google

[La política de privacidad de Google](https://policies.google.com/privacy) se aplica a todos ellos. Firebase y Google Cloud publican cada uno su propia página, enlazadas abajo.

- **Inicio de sesión ([Firebase Authentication](https://firebase.google.com/support/privacy)).** Guarda tu dirección de correo electrónico y cómo inicias sesión. Con Iniciar sesión con Google, también el nombre y la foto de tu cuenta de Google.
- **Prueba de que la app es auténtica ([Firebase App Check](https://firebase.google.com/support/privacy)).** Antes de que nuestros servidores respondan, la app demuestra que es una copia real de Popt que se ejecuta en un dispositivo real. Google ve esa prueba, no para qué es la solicitud.
- **Entrega de notificaciones push ([Firebase Cloud Messaging](https://firebase.google.com/support/privacy)).** Retransmite nuestras notificaciones al servicio push de Apple. Guarda la dirección que Apple nos da para llegar a tu dispositivo. La notificación que retransmite está cifrada.
- **Alojamiento ([Google Cloud](https://cloud.google.com/terms/cloud-privacy-notice)).** Ejecuta nuestros servidores y nuestra base de datos en Estados Unidos, y por tanto guarda todo lo que guardan nuestros servidores.
- **YouTube.** Cuando guardas un enlace de YouTube, tu dispositivo pide a YouTube su título y su miniatura. Cuando reproduces un tráiler dentro de la app (a partir de 16 años), la app carga el reproductor de YouTube, y YouTube te ve como vería a un visitante de su sitio, cookies incluidas. YouTube no tiene una política aparte: la de Google la cubre.

### Servicios de Apple

[La política de privacidad de Apple](https://www.apple.com/legal/privacy/) se aplica a todos ellos. Cuando Apple publica una página para un servicio concreto, está enlazada abajo.

- **[Iniciar sesión con Apple](https://www.apple.com/legal/privacy/data/en/sign-in-with-apple/).** Apple nos comunica tu dirección de correo electrónico, o la dirección de relay privado que elegiste para ocultarla.
- **Notificaciones (el servicio de notificaciones push de Apple).** Entrega nuestras notificaciones a tu dispositivo. Apple transporta el sobre cifrado y no puede leerlo.
- **Popt Pro (el [App Store](https://www.apple.com/legal/privacy/data/en/app-store/)).** Tu suscripción se compra a Apple y la factura Apple. Una compra se vincula a tu cuenta de Popt mediante un token aleatorio, y el recibo de Apple es lo que comprueban nuestros servidores.
- **Lugares ([Mapas de Apple](https://www.apple.com/legal/privacy/data/en/apple-maps/)).** Buscar un lugar, mostrar el mapa y convertir coordenadas en una dirección son solicitudes que van de tu dispositivo a Apple. Las búsquedas se vinculan a un identificador rotatorio, no a tu ID de Apple ni a tu cuenta de Popt.
- **Música ([Apple Music](https://www.apple.com/legal/privacy/data/en/apple-music/) y [Shazam](https://www.apple.com/legal/privacy/data/en/music-recognition/)).** Buscar un álbum o un artista es una solicitud a Apple Music. Reconocer una canción envía a Shazam una huella de audio corta, no la grabación.
- **Rango de edad.** Se pide a iOS en el dispositivo, como se describe en [Menores y edad](#menores-y-edad). Procede de la edad de tu [cuenta de Apple](https://www.apple.com/legal/privacy/data/en/apple-account/).


### PowerSync

[La política de privacidad de PowerSync](https://www.powersync.com/legal/privacy-policy) se aplica.

PowerSync (JourneyApps) es el servicio que gestiona la sincronización descendente desde la base de datos de Popt hasta tus dispositivos. Tus dispositivos se conectan a él directamente, con un token de nuestros servidores, en Estados Unidos.

### Cloudflare R2

[La política de privacidad de Cloudflare](https://www.cloudflare.com/privacypolicy/) se aplica.

Tus fotos y archivos cifrados se guardan en Cloudflare, en Estados Unidos. La app los sube y los descarga directamente, en una dirección de corta duración que le entregan nuestros servidores, así que Cloudflare ve tu dirección IP, los bytes cifrados y su tamaño, y una clave de almacenamiento que empieza por tu identificador de cuenta. Nunca un nombre de archivo, nunca el contenido.

### Wikipedia y Wikidata

[La política de privacidad de Wikimedia](https://foundation.wikimedia.org/wiki/Policy:Privacy_policy) se aplica.

Cuando añades un artista a tu biblioteca, tu dispositivo pregunta a Wikidata qué artículo de Wikipedia corresponde a ese artista y después pide a Wikipedia su primer párrafo. Ven tu dirección IP y el artista, nada sobre tu cuenta.

### Otros

Algunas solicitudes van directamente de tu dispositivo al sitio al que apunta un enlace. Ese sitio ve tu dirección IP, como cuando lo visitas en cualquier navegador. No podemos enumerar esos sitios, porque dependen de los enlaces que guardes.

- **Vistas previas de enlaces.** Cuando guardas o pegas un enlace, tu dispositivo descarga esa página para mostrar un título y una imagen. Los enlaces de TikTok usan el punto de acceso de vista previa de TikTok. Las imágenes de los resultados de búsqueda y de las vistas previas de enlaces se cargan desde sus servidores originales. Si has iniciado sesión en un sitio en el navegador de Popt, esas solicitudes de vista previa llevan las cookies de ese sitio.
- **Imágenes de notificaciones.** Cuando la publicación de un amigo incluye un enlace, tu dispositivo descarga la imagen del enlace para mostrarla en la notificación.
- **El navegador de Popt** es un navegador web normal: los sitios que visitas te ven como lo haría cualquier navegador. Su historial y sus cookies se quedan en tu dispositivo, y un navegador abierto dentro de una bóveda secreta no conserva nada.

## Servicios que usamos en segundo plano

Tu dispositivo nunca se conecta a estos. Lo hacen nuestros servidores, desde nuestra dirección, y no transmiten ninguna identidad, cuenta ni dirección IP.

### Twilio SendGrid

[La política de privacidad de Twilio](https://www.twilio.com/en-us/legal/privacy) se aplica.

Envía el correo con el código de inicio de sesión, y por tanto recibe tu dirección de correo electrónico una vez por cada inicio de sesión.

### TMDB

[La política de privacidad de TMDB](https://www.themoviedb.org/privacy-policy) se aplica.

Cuando buscas una película, una serie, un actor o un director, nuestro servidor reenvía las palabras que escribiste y tu idioma.

### Movie of the Night

[La política de privacidad de Movie of the Night](https://www.movieofthenight.com/privacy) se aplica.

Indica a la app dónde se puede ver en streaming una película o una serie. Nuestro servidor le envía el número de catálogo de la película y tu país.

## Solo en tu dispositivo

Varias de las funciones más inteligentes de Popt se ejecutan por completo en tu teléfono. No nos envían nada.

- **Clasificar lo que escribes.** Cuando escribes algo, un pequeño modelo de aprendizaje automático incluido en la app decide si parece una tarea, un artículo de compra, una entrada de diario o una nota, y ordena los artículos de compra por pasillos del supermercado. Los modelos se ejecutan en el dispositivo. Tu texto no se envía a ningún sitio para esto. Para un idioma para el que no incluimos modelo, la app consulta [Apple Intelligence](https://www.apple.com/legal/privacy/data/en/intelligence-engine/) en el dispositivo cuando está disponible, y si no, no hace nada.
- **Búsqueda.** El índice de búsqueda de Popt se construye en tu dispositivo a partir de tu contenido descifrado y nunca sale de él. Si activas Siri y Spotlight para Popt, el índice de Apple en el dispositivo recibe las tareas, listas y notas que elijas. Ese índice se queda en el dispositivo y se rige por [la política de Siri de Apple](https://www.apple.com/legal/privacy/data/en/ask-siri-dictation/).
- **Revisión de fotos.** En los dispositivos donde está activada la Advertencia de contenido sensible o la Seguridad en la comunicación de Apple, Popt pide a iOS que compruebe en el dispositivo si cada foto que muestra contiene desnudos. Las fotos marcadas se muestran difuminadas. Las fotos no se envían a ningún sitio para esta comprobación, y nosotros nunca conocemos el resultado.
- **Rango de edad.** Si usas una función con restricción de edad, Popt pide a iOS en qué rango de edad estás (menos de 13, de 13 a 15, de 16 a 17, o 18 o más). Popt nunca ve una fecha de nacimiento. La respuesta se guarda con tus ajustes cifrados, así que no podemos leerla en nuestra base de datos. El único lugar al que viaja sin cifrar es la búsqueda de Añadir a la biblioteca: la franja aproximada (menos de 13, de 13 a 15, de 16 a 17, 18 o más) acompaña a la consulta para que los resultados se ajusten a la edad, sin que tu cuenta vaya asociada.
- **Ubicación.** Adjuntar un lugar a una entrada usa la ubicación de tu dispositivo solo cuando tú lo decides, y solo si lo has permitido en iOS. Las coordenadas se cifran como cualquier otro contenido. Convertir las coordenadas en una dirección es una solicitud de tu dispositivo a Mapas de Apple, bajo las políticas de [Localización](https://www.apple.com/legal/privacy/data/en/location-services/) y [Mapas de Apple](https://www.apple.com/legal/privacy/data/en/apple-maps/) de Apple. Nunca pasa por nuestros servidores.
- **Recordatorios.** Los avisos de las tareas con fecha los programa la app en el dispositivo, no un servidor.

## Funciones sociales

Popt no tiene un directorio público de perfiles: nadie puede encontrarte ni ver nada tuyo sin una invitación directa. Todo lo que compartes se mantiene cifrado de extremo a extremo, y las personas con las que compartes solo pueden leer lo que compartiste. Nuestros servidores ven los identificadores de cuenta implicados, nunca el contenido.

### Invitaciones

Una invitación es un enlace. El mensaje opcional y el elemento de biblioteca que contiene se cifran en tu dispositivo con una clave que viaja en el propio enlace, de modo que el contenido de la invitación no se guarda sin cifrar en nuestro servidor, pero cualquiera que tenga el enlace completo puede ver su vista previa. Aceptar una invitación conecta los dos identificadores de cuenta como amigos e intercambia las claves sobre las que se construye el uso compartido posterior.

### Publicaciones

Una publicación se cifra para los amigos que elegiste al publicarla, y cada comentario se cifra para las personas que están en la publicación en ese momento.
- Solo el usuario que publicó puede añadir o quitar participantes
- Los participantes nuevos no ven los comentarios anteriores
- Los participantes que han sido quitados no pueden ver los comentarios posteriores, pero conservan el acceso a la publicación y a todos los comentarios que podían ver cuando se les quitó

### Mensajes directos

Cada parte de una conversación es dueña de su mitad: tus mensajes se cifran con una clave que solo tienen tú y la otra persona, y la otra persona no puede editarlos ni eliminarlos. Eliminar uno de tus mensajes lo elimina para ambos. Nuestros servidores ven que dos identificadores de cuenta intercambian mensajes cifrados, y cuándo.

### Listas, proyectos y notas compartidos

El contenido colaborativo se cifra con una clave compartida por todos sus participantes, y cada miembro puede leerlo o editarlo según el rol que le hayas dado. Cuando quitas a alguien, el contenido se vuelve a cifrar con una clave nueva y se retira de sus dispositivos en la siguiente sincronización. Lo que escribió mientras era miembro se queda en la lista, bajo tu propiedad.

### Denunciar abusos

Denunciar es el único caso en que el contenido nos llega en forma legible. Cuando denuncias un perfil, una publicación o un mensaje, la denuncia lleva el contenido que denuncias, sus fotos y, en el caso de un mensaje, los pocos mensajes de alrededor para dar contexto, más unos detalles opcionales. El contenido denunciado se muestra antes de enviar la denuncia, para que sepas exactamente qué estás enviando. Después, la denuncia se cifra en tu dispositivo antes de enviárnosla, de modo que solo nuestro equipo de revisión puede abrirla. La cuenta denunciada no es informada de tu denuncia, pero puede ser suspendida o expulsada por completo de nuestros servicios.

## Eliminar y conservar datos

**Eliminar contenido.** Todo lo que eliminas pasa a Eliminados recientemente durante 30 días, donde puedes restaurarlo o eliminarlo definitivamente al momento. Pasados 30 días, nuestros servidores lo eliminan de forma definitiva. Una foto o un archivo se borra del almacenamiento en cuanto desaparece el último elemento que apunta a él. El contenido compartido con otras personas vive también en sus dispositivos: eliminar tu copia no elimina la suya.

**Eliminar tu cuenta.** Abre Mi cuenta, elige Eliminar cuenta y escribe la frase de confirmación. En un plazo de 7 días eliminamos tu inicio de sesión, tu perfil, tus claves, tu contenido y tus archivos cifrados, tus tokens push y tus ajustes de notificaciones. Las listas, notas y proyectos compartidos que te pertenecen se eliminan para todos sus participantes, y también tus publicaciones con todos sus comentarios, tus comentarios en las publicaciones de otras personas y tus mensajes. Lo que añadiste a listas, notas y proyectos de tus amigos se queda ahí. Tus amigos verán entonces "Cuenta eliminada" en lugar de tu nombre. Todo lo que añadas entre la solicitud y la eliminación también se elimina, y después no se puede recuperar nada. Eliminar tu cuenta no cancela una suscripción a Popt Pro: cancélala en los ajustes de suscripciones de tu cuenta de Apple. Si ya no tienes ningún dispositivo con sesión iniciada, escribe a support@popt.com desde la dirección con la que te registraste y eliminaremos la cuenta por ti.

Algunos datos deben conservarse más tiempo para cumplir nuestras obligaciones legales:
- Los registros de suscripción que Apple nos exige conservar a efectos contables se guardan mientras la ley lo exija.
- Las denuncias de abuso se guardan mientras las necesitemos para actuar sobre la denuncia y responder de nuestra decisión, incluso después de que la cuenta denunciada haya desaparecido.

**Cerrar sesión** elimina tu contenido del dispositivo: la base de datos, las cachés de fotos y archivos, las cookies y los inicios de sesión del navegador, el índice de Spotlight y tus ajustes. Si has activado el Llavero de iCloud en el dispositivo en el que iniciaste sesión en Popt, el código de recuperación se queda en tu llavero para que puedas volver a iniciar sesión en Popt fácilmente, en cualquier dispositivo en el que hayas iniciado sesión con el mismo ID de Apple.

**Todo lo demás dura poco.** Los registros de entrega de notificaciones se eliminan a los 31 días; los códigos de inicio de sesión, los enlaces de invitación y los contadores de límite de solicitudes se eliminan cuando caducan.

## Tus derechos

Vivas donde vivas, tienes derechos sobre tus datos, y damos a todo el mundo el conjunto completo de derechos del RGPD. La mayoría puedes ejercerlos tú directamente dentro de la app, que es como preferimos que sea, porque no podemos leer tu contenido y no deberíamos tener que hacerlo.

- **Acceso y portabilidad.** Exporta todo desde Mi cuenta. La exportación es una carpeta de archivos Markdown sin formato y tus fotos, legible con cualquier editor de texto y con Obsidian. Incluye tu propio contenido y lo que otras personas compartieron contigo. El contenido de una bóveda secreta se exporta moviéndolo primero a Inicio desde dentro de la bóveda.
- **Corrección.** Edita lo que quieras en la app. Tu nombre de perfil, tu estado y tu avatar son tuyos y puedes cambiarlos en cualquier momento.
- **Eliminación.** Elimina contenido, o tu cuenta entera, como se describe arriba.
- **Oposición y limitación.** No hacemos perfiles, ni publicidad, ni decisiones automatizadas sobre ti, así que no hay nada a lo que oponerse en ese sentido. Si crees que guardamos algo que no deberíamos, escríbenos.
- **Retirar el consentimiento.** La ubicación, las notificaciones, el acceso a las fotos y el rango de edad son permisos de iOS que puedes retirar en Ajustes en cualquier momento. La app sigue funcionando sin ellos.
- **Reclamación.** Puedes reclamar ante el Comisionado Federal de Protección de Datos e Información de Suiza (FDPIC, edoeb.admin.ch) o ante la autoridad de protección de datos de tu país. Preferimos que nos escribas primero, pero no tienes por qué hacerlo.

Para cualquier cosa que no puedas hacer en la app, escríbenos a **support@popt.com**. Como no podemos ver tu contenido, puede que te pidamos que demuestres que controlas la cuenta, por ejemplo escribiendo desde la dirección de correo con la que te registraste.

**Dónde están tus datos.** Nuestros servidores y nuestro almacenamiento están en Estados Unidos, como se describe en [Servicios a los que se conecta la app](#servicios-a-los-que-se-conecta-la-app). Las transferencias fuera de Suiza y de la UE están cubiertas por las cláusulas contractuales tipo de la UE con cada proveedor, y por el propio cifrado: lo que sale es contenido que no podemos leer.

## Menores y edad

Popt tiene una clasificación de 13+ en el App Store, y los padres pueden aprobar su uso para un menor de esa edad a través de Tiempo de uso. El único dato personal que esto implica es el **rango de edad**, y así es como lo tratamos.

Nunca pedimos una fecha de nacimiento. Cuando alguien usa por primera vez una función con restricción de edad, Popt pide a iOS en qué rango de edad está (menos de 13, de 13 a 15, de 16 a 17, o 18 o más) a través de la API Declared Age Range de Apple, que los padres configuran en los ajustes de Familia. La respuesta se guarda con tus ajustes cifrados, donde no podemos leerla. El único lugar al que viaja la franja sin cifrar es la búsqueda de Añadir a la biblioteca, para que los resultados se ajusten a la edad, y no está vinculada a tu cuenta.

Lo que desbloquea cada rango de edad, cómo funciona la aprobación parental de nuevos amigos y cómo se tratan las fotos marcadas se explica en nuestra página de seguridad del contenido: [popt.com/content-safety](https://popt.com/content-safety). No recopilamos nada más sobre los menores.

## Compruébalo por tu cuenta

No deberías tener que fiarte de nuestra palabra en nada de esto. Publicamos **veri-popt**, un conjunto de herramientas y documentación para comprobar la criptografía de Popt: [github.com/SkileSA/veri-popt](https://github.com/SkileSA/veri-popt).

## Cambios en esta política

Cuando cambiamos lo que la app recopila o con quién se comunica, actualizamos primero esta política y después la app. La fecha de arriba es la del último cambio, y el historial completo de versiones es público en nuestro repositorio de documentos legales en GitHub, junto con nuestras Condiciones del servicio: [github.com/SkileSA/popt-legal](https://github.com/SkileSA/popt-legal). Si un cambio reduce tu privacidad, te lo comunicaremos por correo antes de que entre en vigor.
