# Popt Datenschutzrichtlinie

*Dieses Dokument ist eine Übersetzung der englischen Fassung. Rechtlich verbindlich ist allein die englische Fassung: [privacy-policy_EN.md](privacy-policy_EN.md).*

Zuletzt aktualisiert: 2. November 2026

## Zusammenfassung

Popt ist eine App, bei der der Datenschutz an erster Stelle steht. Inhalte, die du in Popt ablegst, werden auf deinem Gerät verschlüsselt, bevor sie irgendwohin gesendet werden, mit Schlüsseln, die wir nicht haben (echte Ende-zu-Ende-Verschlüsselung). Wir können deine Aufgaben, Notizen, dein Tagebuch, deine Fotos, deine Bibliothek, deine Beiträge und Nachrichten nicht lesen, und auch niemand, der in unsere Server einbricht. Was unsere Server sehen, ist die Technik dahinter: welche Accounts Inhalte miteinander teilen, wann Inhalte erstellt und geändert wurden, und deinen Popt-Namen und Avatar, damit du sehen kannst, wer mit dir in einer Gruppe ist, auch wenn ihr nicht befreundet seid.

Wir nutzen deine Daten nicht, um KI zu trainieren. Wir verkaufen sie nicht an Dritte. Wir erstellen kein Profil von dir und zeigen dir keinerlei Werbung. Die App verbindet sich mit unseren eigenen Servern, um deine Inhalte auf allen deinen Geräten zu synchronisieren und zu sichern, und für das Teilen, die Nachrichten und unseren Mediensuchdienst, mit dem du deiner Popt-Bibliothek etwas hinzufügst. Die App kommuniziert außerdem mit Diensten Dritter, die für uns wesentliche Leistungen erbringen:

* **Apple:** Karten, Orte und Musiksuche, alle unter Apples strengen Datenschutzrichtlinien.
* **Google:** Account-Verwaltung und Anmeldung mit Firebase. Server- und Datenbank-Hosting mit Google Cloud.
* **PowerSync:** Deine Daten laufen über PowerSync-Server, um deine Geräte zu erreichen.
* **Cloudflare:** Deine verschlüsselten Fotos und Dateien werden in Cloudflare R2 gespeichert. Die App lädt direkt zu R2 hoch und von R2 herunter.

Diese Dritten haben keinen Zugriff auf deine Inhalte, die ohnehin vollständig verschlüsselt sind.

Du kannst alles exportieren, alles löschen und unsere Aussagen mit den offenen Werkzeugen überprüfen, die wir veröffentlichen.

## Wer wir sind

Popt wird von Skile SA entwickelt, einem Unternehmen mit Sitz in der Schweiz. Skile SA ist der Verantwortliche für Popt: Wir entscheiden, was die App erhebt und warum, und wir stehen dafür gerade. Unser Gerichtsstand ist die Schweiz. Popt wird in Europa, den USA und anderswo genutzt, und wir bemühen uns, die strengsten Datenschutzgesetze einzuhalten. Heute ist das die Datenschutz-Grundverordnung der EU (DSGVO, GDPR). Egal, in welchem Land du bist: Du bekommst den Schutz der DSGVO.

Zu allem in dieser Richtlinie erreichst du uns unter support@popt.com. Unsere Adresse ist Skile SA, Rue de Riant-Coteau 7, 1196 Gland, Schweiz.

Wir haben keine Werbepartner, keine Datenhändler und kein Analyseunternehmen hinter der App. Die einzigen anderen Beteiligten sind die Dienstleister, die unter [Dienste, mit denen die App verbunden ist](#dienste-mit-denen-die-app-verbunden-ist) aufgeführt sind, und wir nennen jeden einzelnen von ihnen.

## Wie deine Inhalte geschützt werden

Alles, was du in Popt schreibst, fotografierst oder sicherst, wird auf deinem Gerät verschlüsselt, bevor es das Gerät verlässt, mit Schlüsseln, die nur du und die Personen haben, mit denen du teilst. Unsere Server speichern und übermitteln diese verschlüsselten Inhalte. Wir verwenden Standardkryptografie und nichts Selbsterfundenes: AES-256 für deine Inhalte und Dateien und Elliptische-Kurven-Schlüssel, um sie zu teilen. Das vollständige Design ist veröffentlicht und kann unabhängig überprüft werden (siehe [Selbst überprüfen](#selbst-überprüfen)).

**Deine Schlüssel verlassen dein Gerät nie in lesbarer Form.** Eine gesperrte Kopie liegt auf unseren Servern, damit ein neues Gerät eingerichtet werden kann, und das Einzige, was sie entsperren kann, ist dein **Wiederherstellungscode**, der auf deinem Gerät erzeugt wird und den wir nie sehen. Der Wiederherstellungscode ist das eine Geheimnis, das du aufbewahren musst. Wenn du ihn verlierst und auch jedes angemeldete Gerät verlierst, können wir deine Inhalte nicht für dich wiederherstellen.

**Geteilte Inhalte** werden genau für die Personen in der Freigabe verschlüsselt, und jede von ihnen hält ihren eigenen Schlüssel dazu. Wird jemand entfernt, wird alles, was ab dann geteilt wird, mit einem neuen Schlüssel verschlüsselt, den diese Person nicht hat.

**Fotos und Dateien** werden vor dem Hochladen auf deinem Gerät verschlüsselt, ebenso ihre Namen, Typen und Abmessungen. Jede Datei hat ihren eigenen Schlüssel, der im verschlüsselten Element steckt, zu dem sie gehört. Ein Foto kann also nur lesen, wer die Notiz, die Liste oder den Beitrag lesen kann, in dem es sitzt. Im Speicher ist eine Datei nur ein zufälliger Name und ein verschlüsselter Datenblock.

**Push-Mitteilungen** sind ebenfalls verschlüsselt. Die Vorschau in einer Mitteilung (der Name eines Elements, die ersten Worte eines Kommentars) ist so versiegelt, dass nur die vorgesehenen Geräte sie öffnen können. Mitteilungen laufen über Googles Firebase Cloud Messaging und dann über Apples Push-Dienst. Beide sehen, wie unser eigener Mitteilungsserver, die Account-Kennungen von Absender und Empfänger und welche Art von Ereignis es war (Nachricht, Beitrag, neue Freigabe …), nie den Inhalt.

### Was nicht verschlüsselt ist

Ein Server, der verschlüsselte Inhalte speichert und ausliefert, muss trotzdem wissen, zu welchem Account sie gehören, mit welchen Accounts sie geteilt sind, welches Gerät sie zuletzt aktualisiert hat und wann sie erstellt oder aktualisiert wurden. Das sind die Teile, die unsere Server lesen können, und der Grund, warum es jeden davon gibt:

- **Account-Kennungen.** Damit der Server jedes Element an die richtigen Geräte ausliefern kann und an keine anderen.
- **Wann jedes Element erstellt, geändert oder gelöscht wurde, und welche Geräte es zuletzt aktualisiert haben.** So werden zwei Geräte abgeglichen, die dasselbe offline bearbeitet haben: Ohne diese Angaben könnte der Server nicht erkennen, welche Änderung die neueste ist, und Änderungen gingen verloren. Die Gerätekennung ist Apples „identifier for vendor“ (IDFV): Sie gilt nur für Popt auf diesem Gerät, sie ist nicht die Werbekennung und kann nicht verwendet werden, um dich in anderen Apps wiederzuerkennen. Sie wird zurückgesetzt, wenn Popt vom Gerät entfernt wird.
- **Wie Inhalte gruppiert sind.** Zu welchem übergeordneten Element (einer Liste, einer Notiz, einem Beitrag, einem Projekt) jeder Teil gehört. Der Server speichert, liefert und schützt Inhalte als ganze Elemente, also muss er wissen, wo eines endet und das nächste beginnt. Die Struktur innerhalb eines Elements, welche Zeile unter welcher steht, ist verschlüsselt.
- **Dein Popt-Name, dein Status und dein Avatar.** Sie bleiben lesbar, damit alle in einem geteilten Beitrag oder einer geteilten Liste sehen können, wer sonst noch dabei ist, auch Personen, mit denen du nicht befreundet bist, und damit jemand, den du einlädst, sehen kann, wer einlädt. Die App sagt das dort, wo du dein Profil bearbeitest.
- **Welche Unterhaltungen du stummgeschaltet hast und wann du jede zuletzt geöffnet hast.** Unser Mitteilungsserver liest diese Angaben, um dich nicht mehr über eine stummgeschaltete Unterhaltung zu benachrichtigen und dich nicht auf etwas hinzuweisen, das du schon gesehen hast. Er verfolgt Unterhaltungs-IDs, keine Inhalte.
- **Wie viel Speicherplatz du nutzt.** Cloudflare, wo die verschlüsselten Dateien liegen, sieht die Größe jeder Datei, wie jeder Dateispeicher. Wir rechnen sie pro Account zusammen, um das Speicherlimit deines Tarifs anzuwenden, und wir entfernen eine Datei, sobald nichts mehr auf sie verweist.

## Welche Daten wir erheben und warum

Wir erheben so wenig, wie die App zum Funktionieren braucht, und nichts, um etwas über dich zu erfahren.

- **Deine E-Mail-Adresse.** Um dich anzumelden und dich wiederzuerkennen, wenn du uns schreibst. Sie kommt von dir bei der Anmeldung oder von Apple oder Google, wenn du dich über sie anmeldest („Mit Apple anmelden“ kann sie hinter Apples Weiterleitungsdienst verbergen). Sie wird von Firebase Authentication gehalten; unsere eigene Datenbank speichert nur einen Hash davon.
- **Dein Popt-Name, dein Status und dein Avatar.** Damit Freunde dich erkennen. Nur der Name ist Pflicht. Im Klartext gespeichert, wie oben erklärt.
- **Deine verschlüsselten Inhalte und ihre Metadaten.** Für die Synchronisierung zwischen deinen Geräten und mit den Personen, mit denen du teilst.
- **Anonyme Gerätekennungen.** Um deine Geräte zu benachrichtigen und sie auseinanderzuhalten. Verwendet Apples datenschutzfreundlichen `identifierForVendor`.
- **Deine Abo-Belege.** Um Popt Pro auf allen deinen Geräten freizuschalten. Sie kommen von Apple, wenn du abonnierst; Zahlungsdaten sehen wir nie.
- **Anfrageprotokolle** (IP-Adresse, Zeit, Pfad). Um den Dienst am Laufen zu halten und Missbrauch zu untersuchen, wie jeder Webserver.
- **Missbrauchsmeldungen.** Um gegen schädliches Verhalten vorzugehen. Sie kommen von den Personen, die sie senden.

**Was wir nicht erheben:** dein Geburtsdatum, deine Kontakte, deine Fotomediathek, deinen Standort, Analysen darüber, wie du die App nutzt, oder eine Werbekennung.

**Rechtsgrundlagen.** Wir verarbeiten deine Daten, um den Dienst zu erbringen, den du angefordert hast (der Vertrag mit dir), weil du dich entschieden hast, etwas zu teilen oder eine Berechtigung zu erteilen (Einwilligung, die du widerrufen kannst), um den Dienst sicher zu halten und Missbrauchsmeldungen zu beantworten (unser berechtigtes Interesse und zum Teil eine gesetzliche Pflicht) und um Buchhaltungs- und Steuerpflichten zu erfüllen (gesetzliche Pflicht).

**Wir verkaufen nie Daten, geben sie nie für Werbung weiter und nutzen deine Inhalte nie, um irgendetwas zu trainieren.**

## Dienste, mit denen die App verbunden ist

Das ist die vollständige Liste. Wenn die App mit einem Dienst spricht, steht er hier.

### Popt-Server

Sie laufen auf Google Cloud in den USA, und die verschlüsselten Fotos und Dateien werden bei Cloudflare gespeichert, ebenfalls in den USA. Wir sagen das so deutlich, weil der Standort wichtig ist, und weil er hier so wenig ausmacht: Auf diesen Servern liegen Inhalte, die wir nicht lesen können, plus die oben aufgeführten Metadaten. Deine Inhalte sind in einem US-Rechenzentrum genauso unlesbar wie in einem Schweizer, und die Metadaten sind überall durch dieselben Regeln geschützt.

Alle laufen unter `*.popt.com`. Das sendet jede Funktion der App:

- **Synchronisierung zwischen deinen Geräten.** Deine verschlüsselten Inhalte, die oben aufgeführten Metadaten und den Nachweis, dass du angemeldet bist.
- **Freunde und Teilen.** Die Account-Kennungen, die als Freunde verbunden sind, die Account-Kennungen, die zu jeder geteilten Liste, jedem geteilten Projekt oder Beitrag gehören, und gesperrte Kopien der geteilten Schlüssel.
- **Nachrichten.** Deine verschlüsselten Nachrichten und die Account-Kennungen der beiden Seiten einer Unterhaltung.
- **Mitteilungen.** Die Adresse, die Apple uns gibt, um dein Gerät zu erreichen, die Account-Kennungen von Absender und Empfängern und die verschlüsselte Vorschau.
- **Popt Pro.** Apples Beleg für dein Abo, damit Pro auf allen deinen Geräten freigeschaltet werden kann.
- **Anmeldung per E-Mail.** Deine E-Mail-Adresse, damit wir dir den Einmalcode senden können.
- **Zur Bibliothek hinzufügen.** Deine Suche nach einem Buch, Film, einer Serie, einem Spiel oder Podcast, mit deiner Sprache und Altersgruppe. Suchanfragen werden nicht protokolliert.
- **Ein Bibliothekselement als Link veröffentlichen.** Das Element, das du veröffentlichen willst. Das veröffentlichte Element selbst ist nicht mit deinem Account verknüpft.
- **Missbrauch melden.** Deine Meldung, verschlüsselt und nur für unser Prüfteam lesbar.
- **Avatare.** Den Stil, den du gewählt hast, und eine Zufallszahl, aus der der Avatar gezeichnet wird. Nichts über dich.

Unsere Server behalten Standard-Anfrageprotokolle 30 Tage lang: welche Adresse welche Funktion aufgerufen hat und wann.

### Google-Dienste

Die [Datenschutzerklärung von Google](https://policies.google.com/privacy) gilt für alle diese Dienste. Firebase und Google Cloud veröffentlichen jeweils eine eigene Seite, unten verlinkt.

- **Anmeldung ([Firebase Authentication](https://firebase.google.com/support/privacy)).** Hält deine E-Mail-Adresse und wie du dich anmeldest. Bei „Über Google anmelden“ auch den Namen und das Foto deines Google-Accounts.
- **Nachweis, dass die App echt ist ([Firebase App Check](https://firebase.google.com/support/privacy)).** Bevor unsere Server antworten, weist die App nach, dass sie eine echte Kopie von Popt auf einem echten Gerät ist. Google sieht diesen Nachweis, nicht, wofür die Anfrage ist.
- **Push-Zustellung ([Firebase Cloud Messaging](https://firebase.google.com/support/privacy)).** Leitet unsere Mitteilungen an Apples Push-Dienst weiter. Hält die Adresse, die Apple uns gibt, um dein Gerät zu erreichen. Die weitergeleitete Mitteilung ist verschlüsselt.
- **Hosting ([Google Cloud](https://cloud.google.com/terms/cloud-privacy-notice)).** Betreibt unsere Server und Datenbank in den USA und hält damit alles, was unsere Server halten.
- **YouTube.** Wenn du einen YouTube-Link sicherst, fragt dein Gerät YouTube nach Titel und Vorschaubild. Wenn du einen Trailer in der App abspielst (ab 16), lädt die App den YouTube-Player, und YouTube sieht dich so, wie es einen Besucher seiner Website sieht, Cookies eingeschlossen. YouTube hat keine eigene Richtlinie: Die von Google deckt es ab.

### Apple-Dienste

Die [Apple Datenschutzrichtlinie](https://www.apple.com/legal/privacy/) gilt für alle diese Dienste. Wo Apple für einen Dienst eine eigene Seite veröffentlicht, ist sie unten verlinkt.

- **[Mit Apple anmelden](https://www.apple.com/legal/privacy/data/en/sign-in-with-apple/).** Apple teilt uns deine E-Mail-Adresse mit oder die private Weiterleitungsadresse, hinter der du sie verbergen wolltest.
- **Mitteilungen (der Apple Push Notification Service).** Stellt unsere Mitteilungen auf deinem Gerät zu. Apple transportiert den verschlüsselten Umschlag und kann ihn nicht lesen.
- **Popt Pro (der [App Store](https://www.apple.com/legal/privacy/data/en/app-store/)).** Dein Abo kaufst du bei Apple, und Apple rechnet es ab. Ein Kauf wird über ein zufälliges Token mit deinem Popt-Account verknüpft, und Apples Beleg ist das, was unsere Server prüfen.
- **Orte ([Apple Karten](https://www.apple.com/legal/privacy/data/en/apple-maps/)).** Die Suche nach einem Ort, die Kartenanzeige und das Umwandeln von Koordinaten in eine Adresse gehen alle von deinem Gerät an Apple. Suchen sind an eine wechselnde Kennung gebunden, nicht an deine Apple-ID oder deinen Popt-Account.
- **Musik ([Apple Music](https://www.apple.com/legal/privacy/data/en/apple-music/) und [Shazam](https://www.apple.com/legal/privacy/data/en/music-recognition/)).** Die Suche nach einem Album oder Künstler geht an Apple Music. Beim Erkennen eines Songs wird ein kurzer Audio-Fingerabdruck an Shazam gesendet, nicht die Aufnahme.
- **Altersgruppe.** Wird auf dem Gerät bei iOS abgefragt, wie unter [Kinder und Alter](#kinder-und-alter) beschrieben. Sie kommt vom Alter in deinem [Apple Account](https://www.apple.com/legal/privacy/data/en/apple-account/).


### PowerSync

Die [Datenschutzrichtlinie von PowerSync](https://www.powersync.com/legal/privacy-policy) gilt.

PowerSync (JourneyApps) ist der Dienst, der die Synchronisierung aus der Popt-Datenbank auf deine Geräte übernimmt. Deine Geräte verbinden sich direkt damit, mit einem Token von unseren Servern, in den USA.

### Cloudflare R2

Die [Datenschutzrichtlinie von Cloudflare](https://www.cloudflare.com/privacypolicy/) gilt.

Deine verschlüsselten Fotos und Dateien werden bei Cloudflare gespeichert, in den USA. Die App lädt sie direkt hoch und herunter, über eine kurzlebige Adresse, die unsere Server ihr geben. Cloudflare sieht also deine IP-Adresse, die verschlüsselten Bytes und ihre Größe sowie einen Speicherschlüssel, der mit deiner Account-Kennung beginnt. Nie einen Dateinamen, nie den Inhalt.

### Wikipedia und Wikidata

Die [Datenschutzrichtlinie der Wikimedia Foundation](https://foundation.wikimedia.org/wiki/Policy:Privacy_policy) gilt.

Wenn du einen Künstler zu deiner Bibliothek hinzufügst, fragt dein Gerät Wikidata, welcher Wikipedia-Artikel zu diesem Künstler gehört, und dann Wikipedia nach dessen erstem Absatz. Sie sehen deine IP-Adresse und den Künstler, nichts über deinen Account.

### Andere

Manche Anfragen gehen direkt von deinem Gerät an die Website, auf die ein Link zeigt. Diese Website sieht deine IP-Adresse, so wie beim Besuch in jedem Browser. Wir können diese Websites nicht auflisten, weil sie von den Links abhängen, die du sicherst.

- **Linkvorschauen.** Wenn du einen Link sicherst oder einfügst, ruft dein Gerät diese Seite ab, um einen Titel und ein Bild anzuzeigen. TikTok-Links verwenden den Vorschau-Endpunkt von TikTok. Bilder in Suchergebnissen und Linkvorschauen werden von ihren ursprünglichen Hosts geladen. Wenn du im Popt-Browser auf einer Website angemeldet bist, tragen diese Vorschauanfragen die Cookies dieser Website.
- **Bilder in Mitteilungen.** Wenn der Beitrag eines Freundes einen Link enthält, ruft dein Gerät das Bild des Links ab, um es in der Mitteilung zu zeigen.
- **Der Popt-Browser** ist ein normaler Webbrowser: Die Websites, die du besuchst, sehen dich wie in jedem Browser. Verlauf und Cookies bleiben auf deinem Gerät, und ein Browser, der in einem geheimen Tresor geöffnet wird, behält nichts.

## Dienste, die wir im Hintergrund nutzen

Dein Gerät verbindet sich nie mit diesen Diensten. Unsere Server tun das, von unserer Adresse aus, und geben keine Identität, keinen Account und keine IP-Adresse weiter.

### Twilio SendGrid

Die [Datenschutzrichtlinie von Twilio](https://www.twilio.com/en-us/legal/privacy) gilt.

Versendet die E-Mail mit dem Anmeldecode und erhält dafür bei jeder Anmeldung einmal deine E-Mail-Adresse.

### TMDB

Die [Datenschutzrichtlinie von TMDB](https://www.themoviedb.org/privacy-policy) gilt.

Wenn du nach einem Film, einer Serie, einem Schauspieler oder Regisseur suchst, leitet unser Server die eingegebenen Wörter und deine Sprache weiter.

### Movie of the Night

Die [Datenschutzrichtlinie von Movie of the Night](https://www.movieofthenight.com/privacy) gilt.

Sagt der App, wo ein Film oder eine Serie gestreamt werden kann. Unser Server sendet die Katalognummer des Films und dein Land.

## Nur auf deinem Gerät

Mehrere der klügeren Funktionen von Popt laufen vollständig auf deinem Telefon. Nichts davon wird an uns gesendet.

- **Sortieren, was du schreibst.** Wenn du etwas schreibst, entscheidet ein kleines Machine-Learning-Modell, das mit der App ausgeliefert wird, ob es wie eine Aufgabe, ein Einkaufsartikel, ein Tagebucheintrag oder eine Notiz aussieht, und sortiert Einkaufsartikel in Gänge. Die Modelle laufen auf dem Gerät. Dein Text wird dafür nirgendwohin gesendet. Für eine Sprache, für die wir kein Modell ausliefern, fragt die App [Apple Intelligence](https://www.apple.com/legal/privacy/data/en/intelligence-engine/) auf dem Gerät, wenn es verfügbar ist, und tut sonst nichts.
- **Suche.** Der Suchindex von Popt wird auf deinem Gerät aus deinen entschlüsselten Inhalten aufgebaut und verlässt es nie. Wenn du Siri & Spotlight für Popt einschaltest, erhält Apples eigener Index auf dem Gerät die Aufgaben, Listen und Notizen, die du auswählst. Dieser Index bleibt auf dem Gerät und unterliegt [Apples Siri-Richtlinie](https://www.apple.com/legal/privacy/data/en/ask-siri-dictation/).
- **Fotoprüfung.** Auf Geräten, auf denen Apples „Warnung vor sensiblen Inhalten“ oder „Kommunikationssicherheit“ eingeschaltet ist, bittet Popt iOS, jedes angezeigte Foto auf dem Gerät auf Nacktheit zu prüfen. Markierte Fotos werden unscharf dargestellt. Die Fotos werden für diese Prüfung nirgendwohin gesendet, und wir erfahren das Ergebnis nie.
- **Altersgruppe.** Wenn du eine Funktion mit Altersbeschränkung nutzt, fragt Popt iOS, in welche Altersgruppe du fällst (unter 13, 13 bis 15, 16 bis 17 oder ab 18). Popt sieht nie ein Geburtsdatum. Die Antwort wird mit deinen verschlüsselten Einstellungen gespeichert, wir können sie in unserer Datenbank also nicht lesen. Die einzige Stelle, an der sie im Klartext unterwegs ist, ist die Suche unter „Zur Bibliothek hinzufügen“: Die grobe Gruppe (unter 13, 13 bis 15, 16 bis 17, ab 18) geht mit der Anfrage mit, damit die Ergebnisse zum Alter passen, ohne Verbindung zu deinem Account.
- **Standort.** Einen Ort an einen Eintrag anzuhängen nutzt den Standort deines Geräts nur, wenn du es willst, und nur, wenn du es in iOS erlaubt hast. Die Koordinaten werden wie alle anderen Inhalte verschlüsselt. Das Umwandeln der Koordinaten in eine Adresse ist eine Anfrage von deinem Gerät an Apple Karten, unter Apples Richtlinien zu den [Ortungsdiensten](https://www.apple.com/legal/privacy/data/en/location-services/) und zu [Apple Karten](https://www.apple.com/legal/privacy/data/en/apple-maps/). Sie geht nie über unsere Server.
- **Erinnerungen.** Erinnerungshinweise für Aufgaben mit Datum werden lokal von der App geplant, nicht von einem Server.

## Soziale Funktionen

Popt hat kein öffentliches Profilverzeichnis: Niemand kann dich finden oder etwas von dir sehen ohne eine direkte Einladung. Alles, was du teilst, bleibt Ende-zu-Ende-verschlüsselt, und die Personen, mit denen du teilst, können nur lesen, was du geteilt hast. Unsere Server sehen die beteiligten Account-Kennungen, nie den Inhalt.

### Einladungen

Eine Einladung ist ein Link. Die optionale Nachricht und das Bibliothekselement darin werden auf deinem Gerät mit einem Schlüssel verschlüsselt, der im Link selbst mitreist. So werden die Inhalte der Einladung nicht im Klartext auf unserem Server gespeichert, und trotzdem kann jeder, der den vollständigen Link hat, eine Vorschau der Einladung sehen. Das Annehmen einer Einladung verbindet die beiden Account-Kennungen als Freunde und tauscht die Schlüssel aus, auf denen späteres Teilen aufbaut.

### Beiträge

Ein Beitrag wird für die Freunde verschlüsselt, die du beim Posten ausgewählt hast, und jeder Kommentar wird für die Personen verschlüsselt, die in diesem Moment am Beitrag beteiligt sind.
- Nur wer den Beitrag gepostet hat, kann Teilnehmer hinzufügen oder entfernen
- Neue Teilnehmer sehen frühere Kommentare nicht
- Entfernte Teilnehmer können neuere Kommentare nicht sehen, behalten aber den Zugang zum Beitrag und zu allen Kommentaren, die sie zum Zeitpunkt ihrer Entfernung sehen konnten

### Direktnachrichten

Jede Seite einer Unterhaltung besitzt ihre Hälfte: Deine Nachrichten werden mit einem Schlüssel verschlüsselt, den nur ihr beide habt, und die andere Person kann sie weder bearbeiten noch löschen. Löschst du eine deiner eigenen Nachrichten, verschwindet sie für euch beide. Unsere Server sehen, dass zwei Account-Kennungen verschlüsselte Nachrichten austauschen, und wann.

### Geteilte Listen, Projekte und Notizen

Gemeinsame Inhalte werden mit einem Schlüssel verschlüsselt, den alle Beteiligten teilen, und jedes Mitglied kann je nach der Rolle, die du ihm gegeben hast, lesen oder bearbeiten. Wenn du jemanden entfernst, werden die Inhalte mit einem neuen Schlüssel neu verschlüsselt und bei der nächsten Synchronisierung von den Geräten dieser Person entfernt. Was sie als Mitglied geschrieben hat, bleibt in der Liste, in deinem Besitz.

### Missbrauch melden

Das Melden ist der einzige Fall, in dem Inhalte uns in lesbarer Form erreichen. Wenn du ein Profil, einen Beitrag oder eine Nachricht meldest, enthält die Meldung den gemeldeten Inhalt, seine Fotos und bei einer Nachricht die wenigen Nachrichten davor und danach als Kontext, plus eine optionale Anmerkung. Der gemeldete Inhalt wird dir angezeigt, bevor du die Meldung sendest, damit du genau weißt, was du sendest. Die Meldung wird dann auf deinem Gerät verschlüsselt, bevor sie an uns geht, sodass nur unser Prüfteam sie öffnen kann. Der gemeldete Account wird nicht über deine Meldung informiert, kann aber gesperrt oder ganz von der Nutzung unserer Dienste ausgeschlossen werden.

## Daten löschen und aufbewahren

**Inhalte löschen.** Alles, was du löschst, landet für 30 Tage unter „Zuletzt gelöscht“, wo du es wiederherstellen oder sofort endgültig löschen kannst. Nach 30 Tagen löschen unsere Server es endgültig. Ein Foto oder eine Datei wird aus dem Speicher entfernt, sobald das letzte Element, das darauf verweist, weg ist. Inhalte, die du mit anderen geteilt hast, liegen auch auf deren Geräten: Das Löschen deiner Kopie löscht ihre nicht.

**Deinen Account löschen.** Öffne „Mein Account“, wähle „Account löschen“ und gib die Bestätigungsphrase ein. Innerhalb von 7 Tagen löschen wir deine Anmeldung, dein Profil, deine Schlüssel, deine verschlüsselten Inhalte und Dateien, deine Push-Tokens und deine Mitteilungseinstellungen. Geteilte Listen, Notizen und Projekte, die dir gehören, werden für alle gelöscht, ebenso deine Beiträge samt allen Kommentaren, deine Kommentare zu Beiträgen anderer und deine Nachrichten. Was du zu Listen, Notizen und Projekten deiner Freunde hinzugefügt hast, bleibt dort. Freunde sehen dann „Gelöschter Account“ statt deines Namens. Alles, was du zwischen der Anfrage und der Löschung hinzufügst, wird ebenfalls gelöscht, und danach lässt sich nichts mehr wiederherstellen. Wenn du deinen Account löschst, wird ein Abo für Popt Pro nicht gekündigt: Kündige es in den Abo-Einstellungen deines Apple Accounts. Wenn du kein angemeldetes Gerät mehr hast, schreib an support@popt.com von der Adresse, mit der du dich registriert hast, und wir löschen den Account für dich.

Manche Daten müssen länger aufbewahrt werden, damit wir unsere gesetzlichen Pflichten erfüllen können:
- Abo-Unterlagen, die wir laut Apple für die Buchhaltung aufbewahren müssen, bleiben so lange, wie es gesetzlich vorgeschrieben ist.
- Missbrauchsmeldungen bleiben so lange, wie wir sie brauchen, um auf die Meldung zu reagieren und unsere Entscheidung zu begründen, auch nachdem der gemeldete Account weg ist.

**Abmelden** löscht deine Inhalte vom Gerät: die Datenbank, die Foto- und Datei-Caches, die Cookies und Anmeldungen des Browsers, den Spotlight-Index und deine Einstellungen. Wenn du auf dem Gerät, auf dem du dich bei Popt angemeldet hast, den iCloud-Schlüsselbund aktiviert hast, bleibt der Wiederherstellungscode in deinem Schlüsselbund, damit du dich auf jedem Gerät, auf dem du mit derselben Apple-ID angemeldet bist, leicht wieder bei Popt anmelden kannst.

**Alles andere ist kurzlebig.** Zustellungsdatensätze für Mitteilungen werden nach 31 Tagen gelöscht; Anmeldecodes, Einladungslinks und Zähler für Anfragelimits werden gelöscht, wenn sie ablaufen.

## Deine Rechte

Wo immer du lebst, hast du Rechte an deinen Daten, und wir geben allen den vollen Umfang der DSGVO. Die meisten davon kannst du selbst in der App ausüben, und so ist es uns am liebsten, weil wir deine Inhalte nicht lesen können und es auch nicht müssen sollten.

- **Auskunft und Übertragbarkeit.** Exportiere alles unter „Mein Account“. Der Export ist ein Ordner mit einfachen Markdown-Dateien und deinen Fotos, lesbar mit jedem Texteditor und mit Obsidian. Er umfasst deine eigenen Inhalte und das, was andere mit dir geteilt haben. Inhalte in einem geheimen Tresor exportierst du, indem du sie zuerst aus dem Tresor heraus nach Start verschiebst.
- **Berichtigung.** Bearbeite alles in der App. Deinen Profilnamen, Status und Avatar kannst du jederzeit ändern.
- **Löschung.** Lösche Inhalte oder deinen ganzen Account, wie oben beschrieben.
- **Widerspruch und Einschränkung.** Wir erstellen keine Profile, zeigen keine Werbung und treffen keine automatisierten Entscheidungen über dich, es gibt in diesem Sinne also nichts, dem du widersprechen könntest. Wenn du glaubst, dass wir etwas haben, das wir nicht haben sollten, schreib uns.
- **Einwilligung widerrufen.** Standort, Mitteilungen, Fotozugriff und die Altersgruppe sind iOS-Berechtigungen, die du jederzeit in den Einstellungen widerrufen kannst. Die App funktioniert auch ohne sie weiter.
- **Beschwerde.** Du kannst dich beim Eidgenössischen Datenschutz- und Öffentlichkeitsbeauftragten (EDÖB, edoeb.admin.ch) oder bei der Datenschutzbehörde deines eigenen Landes beschweren. Uns wäre lieber, du schreibst zuerst uns, aber du musst das nicht.

Für alles, was du in der App nicht tun kannst, schreib uns an **support@popt.com**. Weil wir deine Inhalte nicht sehen können, bitten wir dich vielleicht um einen Nachweis, dass du den Account kontrollierst, zum Beispiel indem du von der E-Mail-Adresse schreibst, mit der du dich registriert hast.

**Wo deine Daten sind.** Unsere Server und unser Speicher stehen in den USA, wie unter [Dienste, mit denen die App verbunden ist](#dienste-mit-denen-die-app-verbunden-ist) beschrieben. Übermittlungen aus der Schweiz und der EU sind durch die EU-Standardvertragsklauseln mit jedem Anbieter abgedeckt, und durch die Verschlüsselung selbst: Was das Land verlässt, sind Inhalte, die wir nicht lesen können.

## Kinder und Alter

Popt ist im App Store ab 13 eingestuft, und Eltern können es über die Bildschirmzeit für ein jüngeres Kind genehmigen. Das einzige personenbezogene Datum dabei ist die **Altersgruppe**, und so gehen wir damit um.

Wir fragen nie nach einem Geburtsdatum. Wenn jemand zum ersten Mal eine Funktion mit Altersbeschränkung nutzt, fragt Popt iOS über Apples Declared Age Range API, die Eltern in den Familieneinstellungen einrichten, in welche Altersgruppe die Person fällt (unter 13, 13 bis 15, 16 bis 17 oder ab 18). Die Antwort wird mit deinen verschlüsselten Einstellungen gespeichert, wo wir sie nicht lesen können. Die einzige Stelle, an der die Gruppe im Klartext unterwegs ist, ist die Suche unter „Zur Bibliothek hinzufügen“, damit die Ergebnisse zum Alter passen, und dort ist sie nicht mit deinem Account verknüpft.

Was jede Altersgruppe freischaltet, wie die Zustimmung der Eltern zu neuen Freunden funktioniert und wie markierte Fotos behandelt werden, erklären wir auf unserer Seite zur Inhaltssicherheit: [popt.com/content-safety](https://popt.com/content-safety). Über Minderjährige erheben wir nichts weiter.

## Selbst überprüfen

Du solltest uns nichts davon einfach glauben müssen. Wir veröffentlichen **veri-popt**, eine Sammlung von Werkzeugen und Dokumentation, um die Kryptografie von Popt zu prüfen: [github.com/SkileSA/veri-popt](https://github.com/SkileSA/veri-popt).

## Änderungen an dieser Richtlinie

Wenn wir ändern, was die App erhebt oder mit wem sie spricht, aktualisieren wir zuerst diese Richtlinie und dann die App. Das Datum oben ist das Datum der letzten Änderung, und die vollständige Versionsgeschichte ist öffentlich in unserem Repository für Rechtsdokumente auf GitHub, zusammen mit unseren Nutzungsbedingungen: [github.com/SkileSA/popt-legal](https://github.com/SkileSA/popt-legal). Bei einer Änderung, die deinen Datenschutz verringert, informieren wir dich per E-Mail, bevor sie wirksam wird.
