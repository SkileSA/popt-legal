# Politique de confidentialité de Popt

*Ce document est une traduction de la version anglaise, [privacy-policy_EN.md](privacy-policy_EN.md). Seule la version anglaise fait foi et a valeur juridique.*

Dernière mise à jour : 2 novembre 2026

## Résumé

Popt est une app qui place la confidentialité en premier. Le contenu que vous mettez dans Popt est chiffré sur votre appareil avant d’être envoyé où que ce soit, avec des clés que nous ne possédons pas (un vrai chiffrement de bout en bout). Nous ne pouvons pas lire vos tâches, vos notes, votre journal, vos photos, votre bibliothèque, vos publications ni vos messages, et quelqu’un qui s’introduirait dans nos serveurs ne le pourrait pas non plus. Ce que nos serveurs voient, c’est la tuyauterie : quels comptes ont partagé du contenu, les dates de création et de modification du contenu, ainsi que votre nom affiché et votre avatar Popt, pour que vous puissiez voir qui est dans un groupe avec vous même si vous n’êtes pas amis.

Nous n’utilisons pas vos données pour entraîner une IA. Nous ne les vendons pas à des tiers. Nous n’établissons aucun profil à votre sujet et ne vous montrons aucune publicité, d’aucune sorte. L’app se connecte à nos propres serveurs pour synchroniser et sauvegarder votre contenu sur tous vos appareils, et pour faire fonctionner le partage, la messagerie et notre service de recherche de médias qui alimente votre bibliothèque Popt. L’app communique aussi avec des services tiers qui nous fournissent des services essentiels :

* **Apple :** Plans, Lieux et recherche musicale, tous couverts par les solides politiques de confidentialité d’Apple.
* **Google :** gestion des comptes et authentification avec Firebase. Hébergement des serveurs et de la base de données avec Google Cloud.
* **PowerSync :** vos données transitent par les serveurs de PowerSync pour atteindre vos appareils.
* **Cloudflare :** vos photos et fichiers chiffrés sont stockés dans Cloudflare R2. L’app envoie vers R2 et télécharge depuis R2 directement.

Ces tiers n’ont pas accès à votre contenu, qui est de toute façon entièrement chiffré.

Vous pouvez tout exporter, tout supprimer, et vérifier nos affirmations avec les outils open source que nous publions.

## Qui nous sommes

Popt est édité par Skile SA, une société établie en Suisse. Skile SA est le responsable du traitement pour Popt : nous décidons ce que l’app collecte et pourquoi, et nous en répondons. Notre juridiction est la Suisse. Popt est utilisé en Europe, aux États-Unis et ailleurs, et nous nous efforçons de respecter les lois sur la protection des données les plus strictes. Aujourd’hui, c’est le Règlement général sur la protection des données de l’UE, le RGPD (GDPR) : quel que soit le pays où vous vous trouvez, vous bénéficiez des protections du RGPD.

Vous pouvez nous contacter au sujet de tout point de cette politique à support@popt.com. Notre adresse est Skile SA, Rue de Riant-Coteau 7, 1196 Gland, Suisse.

Nous n’avons aucun partenaire publicitaire, aucun courtier en données et aucune société d’analyse derrière l’app. Les seuls autres acteurs impliqués sont les prestataires listés sous [Services auxquels l’app se connecte](#services-auxquels-lapp-se-connecte), et nous les nommons tous.

## Comment votre contenu est protégé

Tout ce que vous écrivez, photographiez ou enregistrez dans Popt est chiffré sur votre appareil avant de le quitter, avec des clés que seuls vous et les personnes avec qui vous partagez détenez. Nos serveurs stockent et relaient ce contenu chiffré. Nous utilisons une cryptographie standard de l’industrie et rien de notre invention : AES-256 pour votre contenu et vos fichiers, et des clés à courbes elliptiques pour les partager. La conception complète est publiée et peut être vérifiée de façon indépendante (voir [Vérifiez par vous-même](#vérifiez-par-vous-même)).

**Vos clés ne quittent jamais votre appareil sous une forme lisible.** Une copie verrouillée est conservée sur nos serveurs pour qu’un nouvel appareil puisse être configuré, et la seule chose qui peut la déverrouiller est votre **code de récupération**, généré sur votre appareil et que nous ne voyons jamais. Le code de récupération est le seul secret que vous devez garder. Si vous le perdez et perdez aussi tous vos appareils connectés, nous ne pouvons pas récupérer votre contenu pour vous.

**Le contenu partagé** est chiffré pour exactement les personnes du partage, et chacune d’elles détient sa propre clé. Quand quelqu’un est retiré, ce qui est partagé à partir de là est chiffré avec une nouvelle clé qu’il ne possède pas.

**Les photos et fichiers** sont chiffrés sur votre appareil avant l’envoi, et leurs noms, types et dimensions le sont aussi. Chaque fichier a sa propre clé, transportée dans l’élément chiffré auquel il appartient, de sorte qu’une photo n’est lisible que par qui peut lire la note, la liste ou la publication où elle se trouve. Dans le stockage, un fichier n’est qu’un nom aléatoire et un bloc de données chiffré.

**Les notifications push** sont chiffrées elles aussi. L’aperçu d’une notification (le nom d’un élément, les premiers mots d’un commentaire) est scellé pour que seuls les appareils destinataires puissent l’ouvrir. Les notifications passent par Firebase Cloud Messaging de Google, puis par le service push d’Apple ; tous deux, comme notre propre serveur de notifications, voient les identifiants des comptes source et destinataire et le type d’événement (message, publication, nouveau partage…), jamais le contenu.

### Ce qui n’est pas chiffré

Un serveur qui stocke et distribue du contenu chiffré doit tout de même savoir à quel compte il appartient, avec quels comptes il est partagé, quel appareil l’a mis à jour en dernier, et quand il a été créé ou modifié. Voici les éléments que nos serveurs peuvent lire, et la raison d’être de chacun :

- **Les identifiants de compte.** Pour que le serveur distribue chaque élément aux bons appareils et à personne d’autre.
- **Quand chaque élément a été créé, modifié ou supprimé, et quels appareils l’ont mis à jour en dernier.** C’est ainsi que deux appareils qui ont modifié la même chose hors ligne sont réconciliés : sans cela, le serveur ne pourrait pas dire quelle modification est la plus récente, et des modifications seraient perdues. L’identifiant d’appareil est l’identifiant pour fournisseur d’Apple (IDFV) : il est propre à Popt sur cet appareil, ce n’est pas l’identifiant publicitaire, et il ne peut pas servir à vous reconnaître dans d’autres apps. Il est réinitialisé quand Popt est retiré de l’appareil.
- **La façon dont le contenu est regroupé.** À quel élément de premier niveau (une liste, une note, une publication, un projet) chaque morceau appartient. Le serveur stocke, distribue et protège le contenu par éléments entiers, il doit donc savoir où l’un finit et où le suivant commence. La structure à l’intérieur d’un élément, quelle ligne se trouve sous quelle autre, est chiffrée.
- **Votre nom, votre statut et votre avatar Popt.** Ils restent lisibles pour que toutes les personnes d’une publication ou d’une liste partagée puissent voir qui d’autre est là, y compris des personnes dont vous n’êtes pas ami, et pour que quelqu’un que vous invitez puisse voir qui l’invite. L’app le dit à l’endroit où vous modifiez votre profil.
- **Les conversations que vous avez mises en sourdine, et la date à laquelle vous avez ouvert chacune pour la dernière fois.** Notre serveur de notifications les lit pour cesser de vous notifier au sujet d’une conversation en sourdine, et pour éviter de vous alerter sur quelque chose que vous avez déjà vu. Il suit des identifiants de conversation, pas de contenu.
- **L’espace de stockage que vous utilisez.** Cloudflare, où les fichiers chiffrés sont stockés, voit la taille de chacun, comme tout service de stockage. Nous en faisons le total par compte pour appliquer la limite de stockage de votre forfait, et nous libérons un fichier dès que plus rien ne pointe vers lui.

## Les données que nous collectons et pourquoi

Nous collectons aussi peu que l’app en a besoin pour fonctionner, et rien pour en apprendre sur vous.

- **Votre adresse e-mail.** Pour vous connecter et vous reconnaître quand vous nous écrivez. Elle vient de vous à la connexion, ou d’Apple ou de Google quand vous vous connectez avec eux (Sign in with Apple peut la masquer derrière le relais d’Apple). Elle est détenue par Firebase Authentication ; notre propre base de données n’en conserve qu’un hachage.
- **Votre nom, votre statut et votre avatar Popt.** Pour que vos amis vous reconnaissent. Seul le nom est obligatoire. Stockés en clair, comme expliqué ci-dessus.
- **Votre contenu chiffré et ses métadonnées.** Pour synchroniser entre vos appareils et avec les personnes avec qui vous partagez.
- **Des identifiants d’appareil anonymes.** Pour notifier vos appareils et les distinguer. Utilise l’`identifierForVendor` d’Apple, conçu pour préserver la confidentialité.
- **Vos reçus d’abonnement.** Pour débloquer Popt Pro sur tous vos appareils. Ils viennent d’Apple quand vous vous abonnez ; nous ne voyons jamais vos informations de paiement.
- **Les journaux de requêtes** (adresse IP, heure, chemin). Pour maintenir le service en marche et enquêter sur les abus, comme tout serveur web.
- **Les signalements d’abus.** Pour agir contre les comportements nuisibles. Ils viennent des personnes qui les envoient.

**Ce que nous ne collectons pas :** votre date de naissance, vos contacts, votre photothèque, votre position, des données d’analyse sur votre usage de l’app, ou un identifiant publicitaire.

**Bases légales.** Nous traitons vos données pour fournir le service que vous avez demandé (le contrat avec vous), parce que vous avez choisi de partager quelque chose ou d’accorder une autorisation (le consentement, que vous pouvez retirer), pour garder le service sûr et répondre aux signalements d’abus (notre intérêt légitime, et en partie une obligation légale), et pour respecter nos obligations comptables et fiscales (obligation légale).

**Nous ne vendons jamais de données, ne les partageons jamais à des fins publicitaires, et n’utilisons jamais votre contenu pour entraîner quoi que ce soit.**

## Services auxquels l’app se connecte

Voici la liste complète. Si l’app lui parle, il est ici.

### Serveurs Popt

Ils tournent sur Google Cloud aux États-Unis, et les photos et fichiers chiffrés sont stockés chez Cloudflare, également aux États-Unis. Nous le disons clairement parce que l’emplacement compte, et parce qu’il compte si peu ici : ce qui se trouve sur ces serveurs est du contenu que nous ne pouvons pas lire, plus les métadonnées listées ci-dessus. Votre contenu est aussi illisible dans un centre de données américain qu’il le serait dans un centre suisse, et les métadonnées sont protégées par les mêmes règles où qu’elles soient.

Ils sont tous sous `*.popt.com`. Voici ce que chaque fonction de l’app envoie :

- **Synchronisation entre vos appareils.** Votre contenu chiffré, les métadonnées listées ci-dessus, et la preuve que vous êtes connecté.
- **Amis et partage.** Les identifiants des comptes reliés comme amis, les identifiants des comptes qui font partie de chaque liste, projet ou publication partagés, et des copies verrouillées des clés partagées.
- **Messagerie.** Vos messages chiffrés, et les identifiants de compte des deux côtés d’une conversation.
- **Notifications.** L’adresse qu’Apple nous donne pour joindre votre appareil, les identifiants de compte de l’expéditeur et des destinataires, et l’aperçu chiffré.
- **Popt Pro.** Le reçu d’Apple pour votre abonnement, pour que Pro puisse être débloqué sur tous vos appareils.
- **Connexion par e-mail.** Votre adresse e-mail, pour que nous puissions vous envoyer le code à usage unique.
- **Ajout à votre bibliothèque.** Votre recherche d’un livre, d’un film, d’une série, d’un jeu ou d’un podcast, avec votre langue et votre tranche d’âge. Les recherches ne sont pas journalisées.
- **Publication d’un élément de bibliothèque sous forme de lien.** L’élément que vous avez choisi de publier. L’élément publié lui-même n’est pas lié à votre compte.
- **Signalement d’abus.** Votre signalement, chiffré et lisible uniquement par notre équipe de modération.
- **Avatars.** Le style que vous avez choisi, et un nombre aléatoire à partir duquel l’avatar est dessiné. Rien sur vous.

Nos serveurs conservent des journaux de requêtes standard pendant 30 jours : quelle adresse a appelé quelle fonction, et quand.

### Services Google

La [politique de confidentialité de Google](https://policies.google.com/privacy) s’applique à tous ces services. Firebase et Google Cloud publient chacun une page qui leur est propre, en lien ci-dessous.

- **Connexion ([Firebase Authentication](https://firebase.google.com/support/privacy)).** Détient votre adresse e-mail et votre méthode de connexion. Avec Sign in with Google, également le nom et la photo de votre compte Google.
- **Preuve que l’app est authentique ([Firebase App Check](https://firebase.google.com/support/privacy)).** Avant que nos serveurs répondent, l’app prouve qu’elle est une vraie copie de Popt tournant sur un vrai appareil. Google voit cette preuve, pas l’objet de la requête.
- **Distribution des push ([Firebase Cloud Messaging](https://firebase.google.com/support/privacy)).** Relaie nos notifications vers le service push d’Apple. Détient l’adresse qu’Apple nous donne pour joindre votre appareil. La notification relayée est chiffrée.
- **Hébergement ([Google Cloud](https://cloud.google.com/terms/cloud-privacy-notice)).** Fait tourner nos serveurs et notre base de données aux États-Unis, et détient donc tout ce que nos serveurs détiennent.
- **YouTube.** Quand vous enregistrez un lien YouTube, votre appareil demande à YouTube son titre et sa vignette. Quand vous lisez une bande-annonce dans l’app (16 ans et plus), l’app charge le lecteur de YouTube, et YouTube vous voit comme il verrait un visiteur de son site, cookies compris. YouTube n’a pas de politique séparée : celle de Google le couvre.

### Services Apple

L’[Engagement de confidentialité d’Apple](https://www.apple.com/legal/privacy/) s’applique à tous ces services. Quand Apple publie une page pour un service, elle est en lien ci-dessous.

- **[Sign in with Apple](https://www.apple.com/legal/privacy/data/en/sign-in-with-apple/).** Apple nous communique votre adresse e-mail, ou l’adresse de relais privé derrière laquelle vous avez choisi de la masquer.
- **Notifications (le service Apple Push Notification).** Distribue nos notifications à votre appareil. Apple transporte l’enveloppe chiffrée et ne peut pas la lire.
- **Popt Pro (l’[App Store](https://www.apple.com/legal/privacy/data/en/app-store/)).** Votre abonnement est acheté auprès d’Apple et facturé par Apple. Un achat est rattaché à votre compte Popt par un jeton aléatoire, et c’est le reçu d’Apple que nos serveurs vérifient.
- **Lieux ([Apple Plans](https://www.apple.com/legal/privacy/data/en/apple-maps/)).** Rechercher un lieu, afficher le plan et convertir des coordonnées en adresse : tout cela part de votre appareil vers Apple. Les recherches sont rattachées à un identifiant tournant, pas à votre identifiant Apple ni à votre compte Popt.
- **Musique ([Apple Music](https://www.apple.com/legal/privacy/data/en/apple-music/) et [Shazam](https://www.apple.com/legal/privacy/data/en/music-recognition/)).** Rechercher un album ou un artiste passe par Apple Music. Reconnaître une chanson envoie une courte empreinte audio à Shazam, pas l’enregistrement.
- **Tranche d’âge.** Demandée à iOS sur l’appareil, comme décrit sous [Enfants et âge](#enfants-et-âge). Elle provient de l’âge de votre [compte Apple](https://www.apple.com/legal/privacy/data/en/apple-account/).


### PowerSync

La [politique de confidentialité de PowerSync](https://www.powersync.com/legal/privacy-policy) s’applique.

PowerSync (JourneyApps) est le service qui gère la synchronisation descendante de la base de données Popt vers vos appareils. Vos appareils s’y connectent directement, avec un jeton délivré par nos serveurs, aux États-Unis.

### Cloudflare R2

La [politique de confidentialité de Cloudflare](https://www.cloudflare.com/privacypolicy/) s’applique.

Vos photos et fichiers chiffrés sont stockés chez Cloudflare, aux États-Unis. L’app les envoie et les télécharge directement, à une adresse temporaire que nos serveurs lui fournissent, de sorte que Cloudflare voit votre adresse IP, les octets chiffrés et leur taille, et une clé de stockage qui commence par votre identifiant de compte. Jamais un nom de fichier, jamais le contenu.

### Wikipedia et Wikidata

La [politique de confidentialité de Wikimedia](https://foundation.wikimedia.org/wiki/Policy:Privacy_policy) s’applique.

Quand vous ajoutez un artiste à votre bibliothèque, votre appareil demande à Wikidata quel article Wikipedia correspond à cet artiste, puis demande à Wikipedia son premier paragraphe. Ils voient votre adresse IP et l’artiste, rien sur votre compte.

### Autres

Certaines requêtes partent directement de votre appareil vers le site qu’un lien désigne. Ce site voit votre adresse IP, comme quand vous le visitez dans n’importe quel navigateur. Nous ne pouvons pas lister ces sites, parce qu’ils dépendent des liens que vous enregistrez.

- **Aperçus de liens.** Quand vous enregistrez ou collez un lien, votre appareil charge cette page pour afficher un titre et une image. Les liens TikTok utilisent le point de terminaison d’aperçu de TikTok. Les images des résultats de recherche et des aperçus de liens se chargent depuis leurs hôtes d’origine. Si vous êtes connecté à un site dans le navigateur Popt, ces requêtes d’aperçu transportent les cookies de ce site.
- **Images de notification.** Quand la publication d’un ami contient un lien, votre appareil charge l’image du lien pour l’afficher dans la notification.
- **Le navigateur Popt** est un navigateur web normal : les sites que vous visitez vous voient comme n’importe quel navigateur le ferait. Son historique et ses cookies restent sur votre appareil, et un navigateur ouvert dans un coffre secret ne conserve rien.

## Services que nous utilisons en coulisses

Votre appareil ne se connecte jamais à ces services. Nos serveurs le font, depuis notre adresse, et ne transmettent aucune identité, aucun compte ni aucune adresse IP.

### Twilio SendGrid

La [politique de confidentialité de Twilio](https://www.twilio.com/en-us/legal/privacy) s’applique.

Envoie l’e-mail contenant le code de connexion, et reçoit donc votre adresse e-mail une fois par connexion.

### TMDB

La [politique de confidentialité de TMDB](https://www.themoviedb.org/privacy-policy) s’applique.

Quand vous recherchez un film, une série, un acteur ou un réalisateur, notre serveur transmet les mots que vous avez tapés et votre langue.

### Movie of the Night

La [politique de confidentialité de Movie of the Night](https://www.movieofthenight.com/privacy) s’applique.

Indique à l’app où un film ou une série peut être vu en streaming. Notre serveur lui envoie le numéro de catalogue du film et votre pays.

## Sur votre appareil uniquement

Plusieurs des fonctions les plus intelligentes de Popt s’exécutent entièrement sur votre téléphone. Rien à leur sujet ne nous est envoyé.

- **Trier ce que vous tapez.** Quand vous notez quelque chose, un petit modèle d’apprentissage automatique intégré à l’app décide si cela ressemble à une tâche, à un article de courses, à une entrée de journal ou à une note, et range les articles de courses par rayon. Les modèles s’exécutent sur l’appareil. Votre texte n’est envoyé nulle part pour cela. Pour une langue pour laquelle nous ne fournissons pas de modèle, l’app interroge [Apple Intelligence](https://www.apple.com/legal/privacy/data/en/intelligence-engine/) sur l’appareil quand cette fonctionnalité est disponible, et ne fait rien sinon.
- **Recherche.** L’index de recherche de Popt est construit sur votre appareil à partir de votre contenu déchiffré et ne le quitte jamais. Si vous activez Siri et Spotlight pour Popt, l’index d’Apple sur l’appareil reçoit les tâches, les listes et les notes que vous choisissez. Cet index reste sur l’appareil et est couvert par la [politique d’Apple concernant Siri](https://www.apple.com/legal/privacy/data/en/ask-siri-dictation/).
- **Filtrage des photos.** Sur les appareils où l’Avertissement de contenu sensible ou la Sécurité des communications d’Apple sont activés, Popt demande à iOS de vérifier, sur l’appareil, chaque photo qu’il affiche pour y détecter de la nudité. Les photos signalées sont floutées. Les photos ne sont envoyées nulle part pour cette vérification, et nous ne connaissons jamais le résultat.
- **Tranche d’âge.** Si vous utilisez une fonction soumise à une restriction d’âge, Popt demande à iOS dans quelle tranche d’âge vous vous situez (moins de 13 ans, 13 à 15 ans, 16 à 17 ans, ou 18 ans et plus). Popt ne voit jamais de date de naissance. La réponse est stockée avec vos réglages chiffrés, nous ne pouvons donc pas la lire dans notre base de données. Le seul endroit où elle circule en clair est la recherche d’Ajout à la bibliothèque : la tranche approximative (moins de 13 ans, 13 à 15 ans, 16 à 17 ans, 18 ans et plus) accompagne la requête pour que les résultats soient adaptés à l’âge, sans que votre compte y soit rattaché.
- **Position.** Attacher un lieu à une entrée utilise la position de votre appareil uniquement quand vous le choisissez, et seulement si vous l’avez autorisé dans iOS. Les coordonnées sont chiffrées comme tout autre contenu. Convertir les coordonnées en adresse est une requête de votre appareil vers Apple Plans, couverte par les politiques d’Apple concernant le [service de localisation](https://www.apple.com/legal/privacy/data/en/location-services/) et [Apple Plans](https://www.apple.com/legal/privacy/data/en/apple-maps/). Elle ne passe jamais par nos serveurs.
- **Rappels.** Les alertes de rappel des tâches datées sont programmées localement par l’app, pas par un serveur.

## Fonctions sociales

Popt n’a pas d’annuaire public de profils : personne ne peut vous trouver ni voir quoi que ce soit de vous sans une invitation directe. Tout ce que vous partagez reste chiffré de bout en bout, et les personnes avec qui vous partagez ne peuvent lire que ce que vous avez partagé. Nos serveurs voient les identifiants de compte impliqués, jamais le contenu.

### Invitations

Une invitation est un lien. Le message et l’élément de bibliothèque facultatifs qu’elle contient sont chiffrés sur votre appareil avec une clé qui voyage dans le lien lui-même, de sorte que le contenu de l’invitation n’est pas stocké en clair sur notre serveur, tout en restant prévisualisable par quiconque détient le lien complet. Accepter une invitation relie les deux identifiants de compte comme amis et échange les clés sur lesquelles le partage ultérieur repose.

### Publications

Une publication est chiffrée pour les amis que vous avez choisis au moment de publier, et chaque commentaire est chiffré pour les personnes présentes dans la publication à ce moment-là.
- Seule la personne qui a publié peut ajouter ou retirer des participants
- Les nouveaux participants ne voient pas les commentaires précédents
- Les participants retirés ne peuvent pas voir les commentaires plus récents, mais gardent l’accès à la publication et à tous les commentaires qu’ils pouvaient voir au moment de leur retrait

### Messages

Chaque côté d’une conversation possède sa moitié : vos messages sont chiffrés sous une clé que seuls vous deux détenez, et l’autre personne ne peut ni les modifier ni les supprimer. Supprimer un de vos propres messages le retire pour vous deux. Nos serveurs voient que deux identifiants de compte échangent des messages chiffrés, et quand.

### Listes, projets et notes partagés

Le contenu collaboratif est chiffré sous une clé partagée par toutes les personnes qui y participent, et chaque membre peut lire ou modifier selon le rôle que vous lui avez donné. Quand vous retirez quelqu’un, le contenu est rechiffré sous une nouvelle clé et retiré de ses appareils à la synchronisation suivante. Ce qu’il a écrit pendant qu’il était membre reste dans la liste, sous votre propriété.

### Signaler un abus

Le signalement est le seul cas où du contenu nous parvient sous une forme lisible. Quand vous signalez un profil, une publication ou un message, le signalement contient le contenu que vous signalez, ses photos et, pour un message, les quelques messages qui l’entourent pour le contexte, plus une remarque facultative. Le contenu signalé est affiché avant l’envoi du signalement, pour que vous sachiez exactement ce que vous envoyez. Le signalement est ensuite chiffré sur votre appareil avant de nous être envoyé, de sorte que seule notre équipe de modération peut l’ouvrir. Le compte signalé n’est pas informé de votre signalement, mais il peut être suspendu ou définitivement banni de nos services.

## Suppression et conservation des données

**Supprimer du contenu.** Tout ce que vous supprimez va dans Supprimés récemment pendant 30 jours, où vous pouvez le restaurer ou le purger immédiatement. Après 30 jours, nos serveurs le suppriment définitivement. Une photo ou un fichier est effacé du stockage dès que le dernier élément qui pointe vers lui a disparu. Le contenu partagé avec d’autres vit aussi sur leurs appareils : supprimer votre copie ne supprime pas la leur.

**Supprimer votre compte.** Ouvrez Mon compte, choisissez Supprimer le compte et saisissez la phrase de confirmation. Sous 7 jours, nous supprimons votre connexion, votre profil, vos clés, votre contenu et vos fichiers chiffrés, vos jetons push et vos réglages de notifications. Les listes, notes et projets partagés qui vous appartiennent sont supprimés pour tout le monde, de même que vos publications avec tous leurs commentaires, vos commentaires sur les publications d’autres personnes et vos messages. Ce que vous avez ajouté aux listes, notes et projets de vos amis y reste. Vos amis voient ensuite « Compte supprimé » à la place de votre nom. Tout ce que vous ajoutez entre la demande et la suppression est supprimé aussi, et rien ne peut être récupéré ensuite. Supprimer votre compte ne résilie pas un abonnement Popt Pro : résiliez-le dans les réglages d’abonnement de votre compte Apple. Si vous n’avez plus aucun appareil connecté, écrivez à support@popt.com depuis l’adresse avec laquelle vous vous êtes inscrit et nous supprimerons le compte pour vous.

Certaines données doivent être conservées plus longtemps pour respecter nos obligations légales :
- Les enregistrements d’abonnement qu’Apple nous demande de conserver à des fins comptables sont gardés aussi longtemps que la loi l’exige.
- Les signalements d’abus sont conservés aussi longtemps que nous en avons besoin pour agir sur le signalement et répondre de notre décision, même après la disparition du compte signalé.

**Se déconnecter** supprime votre contenu de l’appareil : la base de données, les caches de photos et de fichiers, les cookies et les identifiants de connexion du navigateur, l’index Spotlight et vos réglages. Si vous avez activé le trousseau iCloud sur l’appareil où vous vous êtes connecté à Popt, le code de récupération reste dans votre trousseau pour que vous puissiez facilement vous reconnecter à Popt, sur tout appareil où vous êtes connecté avec le même identifiant Apple.

**Tout le reste est de courte durée.** Les enregistrements de distribution des notifications sont supprimés après 31 jours ; les codes de connexion, les liens d’invitation et les compteurs de limitation de débit sont supprimés à leur expiration.

## Vos droits

Où que vous viviez, vous avez des droits sur vos données, et nous donnons à tout le monde l’ensemble complet des droits du RGPD. La plupart, vous pouvez les exercer vous-même dans l’app, ce que nous préférons, parce que nous ne pouvons pas lire votre contenu et ne devrions pas avoir à le faire.

- **Accès et portabilité.** Exportez tout depuis Mon compte. L’export est un dossier de fichiers Markdown bruts et de vos photos, lisible par tout éditeur de texte et par Obsidian. Il couvre votre propre contenu et ce que d’autres ont partagé avec vous. Le contenu d’un coffre secret s’exporte en le déplaçant d’abord vers l’Accueil depuis l’intérieur du coffre.
- **Rectification.** Modifiez ce que vous voulez dans l’app. Votre nom de profil, votre statut et votre avatar sont à vous et modifiables à tout moment.
- **Suppression.** Supprimez du contenu, ou votre compte entier, comme décrit ci-dessus.
- **Opposition et limitation.** Nous ne faisons aucun profilage, aucune publicité et aucune décision automatisée vous concernant, il n’y a donc rien à quoi s’opposer en ce sens. Si vous pensez que nous détenons quelque chose que nous ne devrions pas, écrivez-nous.
- **Retrait du consentement.** La position, les notifications, l’accès aux photos et la tranche d’âge sont des autorisations iOS que vous pouvez retirer à tout moment dans Réglages. L’app continue de fonctionner sans elles.
- **Réclamation.** Vous pouvez vous plaindre auprès du Préposé fédéral à la protection des données et à la transparence (PFPDT, edoeb.admin.ch) ou auprès de l’autorité de protection des données de votre pays. Nous préférerions que vous nous écriviez d’abord, mais vous n’y êtes pas obligé.

Pour tout ce que vous ne pouvez pas faire dans l’app, écrivez-nous à **support@popt.com**. Comme nous ne pouvons pas voir votre contenu, nous pourrons vous demander de prouver que vous contrôlez le compte, par exemple en écrivant depuis l’adresse e-mail avec laquelle vous vous êtes inscrit.

**Où sont vos données.** Nos serveurs et notre stockage sont aux États-Unis, comme décrit sous [Services auxquels l’app se connecte](#services-auxquels-lapp-se-connecte). Les transferts hors de Suisse et de l’UE sont couverts par les clauses contractuelles types de l’UE avec chaque prestataire, et par le chiffrement lui-même : ce qui part est du contenu que nous ne pouvons pas lire.

## Enfants et âge

Popt est classé 13+ sur l’App Store, et les parents peuvent l’approuver pour un enfant plus jeune via Temps d’écran. La seule donnée personnelle que cela implique est la **tranche d’âge**, et voici comment nous la traitons.

Nous ne demandons jamais de date de naissance. Quand quelqu’un utilise pour la première fois une fonction soumise à une restriction d’âge, Popt demande à iOS dans quelle tranche d’âge il se situe (moins de 13 ans, 13 à 15 ans, 16 à 17 ans, ou 18 ans et plus) via l’API Declared Age Range d’Apple, que les parents configurent dans les réglages Famille. La réponse est stockée avec vos réglages chiffrés, où nous ne pouvons pas la lire. Le seul endroit où la tranche circule en clair est la recherche d’Ajout à la bibliothèque, pour que les résultats soient adaptés à l’âge, et elle n’est pas liée à votre compte.

Ce que chaque tranche d’âge débloque, comment fonctionne l’approbation parentale des nouveaux amis et comment les photos signalées sont traitées est expliqué sur notre page Sécurité des contenus : [popt.com/content-safety](https://popt.com/content-safety). Nous ne collectons rien d’autre sur les mineurs.

## Vérifiez par vous-même

Vous ne devriez pas avoir à nous croire sur parole pour tout cela. Nous publions **veri-popt**, un ensemble d’outils et de documentation pour vérifier la cryptographie de Popt : [github.com/SkileSA/veri-popt](https://github.com/SkileSA/veri-popt).

## Modifications de cette politique

Quand nous changeons ce que l’app collecte ou à qui elle parle, nous mettons d’abord à jour cette politique, puis l’app. La date en haut est celle de la dernière modification, et l’historique complet des versions est public dans notre dépôt de documents juridiques sur GitHub, à côté de nos Conditions d’utilisation : [github.com/SkileSA/popt-legal](https://github.com/SkileSA/popt-legal). Pour une modification qui réduit votre confidentialité, nous vous préviendrons par e-mail avant qu’elle prenne effet.
