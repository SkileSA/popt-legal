# Popt Privacy Policy

Last updated: 2 November 2026

## Summary

Popt is a privacy-first app. Content you put in Popt is encrypted on your device before it is sent anywhere, with keys we do not have (true end-to-end encryption). We cannot read your tasks, notes, journal, photos, library, posts or messages, and neither can anyone who breaks into our servers. What our servers do see is the plumbing: which accounts have shared content, content creation and modification dates, and your Popt screen name and avatar so that you can see who's in a group with you even if you're not friends with them.

We do not use your data to train AI. We do not sell it to third parties. We do not profile you or serve you ads of any kind. The app connects to our own servers in order to synchronize and back up your content on all your devices, and to power sharing, messaging, and our media search service for adding to your Popt library. The app also communicates with third party services that provide essential services for us:

* **Apple:** Maps, Places and Music search, all covered by Apple's strong privacy policies.
* **Google:** Account management and authentication with Firebase. Server and database hosting with Google Cloud.
* **PowerSync:** Your data flows through PowerSync servers to reach your devices.
* **Cloudflare:** Your encrypted photos and files are stored in Cloudflare R2. The app uploads to and downloads from R2 directly.

These third parties do not have access to your content, which is in any case fully encrypted.

You can export everything, delete everything, and check our claims with the open tools we publish.

## Who we are

Popt is made by Skile SA, a company based in Switzerland. Skile SA is the data controller for Popt: we decide what the app collects and why, and we answer for it. Our jurisdiction is Switzerland. Popt is used in Europe, the United States and elsewhere, and we strive to comply with the most restrictive data protection laws. Today that is the EU's General Data Protection Regulation (GDPR), so whatever country you are in, you get GDPR's protections.

You can reach us about anything in this policy at support@popt.com. Our address is Skile SA, Rue de Riant-Coteau 7, 1196 Gland, Switzerland.

We have no advertising partners, no data brokers and no analytics company behind the app. The only other parties involved are the service providers listed under [Services the app connects to](#services-the-app-connects-to), and we name every one of them.

## How your content is protected

Everything you write, photograph or save in Popt is encrypted on your device before it leaves it, with keys that only you and the people you share with hold. Our servers store and relay that encrypted content. We use industry-standard cryptography and nothing of our own invention: AES-256 for your content and files, and elliptic-curve keys for sharing them. The full design is published and can be checked independently (see [Verify it yourself](#verify-it-yourself)).

**Your keys never leave your device in readable form.** A locked copy is kept on our servers so that a new device can be set up, and the only thing that can unlock it is your **recovery code**, generated on your device and never seen by us. The recovery code is the one secret you must keep. If you lose it and lose every signed-in device, we cannot recover your content for you.

**Shared content** is encrypted for exactly the people in the share, and each of them holds their own key to it. When someone is removed, what is shared from then on is encrypted with a new key they do not have.

**Photos and files** are encrypted on your device before upload, and so are their names, types and dimensions. Each file has its own key, carried inside the encrypted item it belongs to, so a photo is readable only by whoever can read the note, list or post it sits in. In storage a file is just a random name and an encrypted blob.

**Push notifications** are encrypted too. The preview in a notification (an item's name, the first words of a comment) is sealed so that only intended devices can open it. Notifications travel through Google's Firebase Cloud Messaging and then Apple's push service; both, like our own notification server, see the source and target account identifiers and what kind of event it was (message, post, new share...), never what it says.

### What is not encrypted

A server that stores and delivers encrypted content still has to know which account it belongs to, which accounts it is shared with, which device last updated it, and when it was created or updated. These are the pieces our servers can read, and the reason each one exists:

- **Account identifiers.** So the server can deliver each item to the right devices and nobody else's.
- **When each item was created, changed or deleted, and which devices last updated it.** This is how two devices that edited the same thing while offline are reconciled: without it the server could not tell which change is the newest, and edits would be lost. The device identifier is Apple's identifier for vendor (IDFV): it is specific to Popt on that device, it is not the advertising identifier, and it cannot be used to recognise you in other apps. It resets when Popt is removed from the device.
- **How content is grouped.** Which top-level item (a list, a note, a post, a project) each piece belongs to. The server stores, delivers and protects content as whole items, so it has to know where one ends and the next begins. The structure inside an item, which line sits under which, is encrypted.
- **Your Popt name, status line and avatar.** They stay readable so that everyone in a shared post or list can see who else is there, including people you are not friends with, and so that someone you invite can see who is inviting them. The app says so where you edit your profile.
- **Which conversations you muted, and the date you last opened each one.** Our notification server reads these to stop notifying you about a conversation you muted, and to avoid alerting you about something you have already seen. It tracks conversation ids, no contents.
- **How much storage you use.** Cloudflare, where encrypted files are stored, sees the size of each one, as any file store does. We total it per account to apply your plan's storage limit, and we free a file once nothing points to it any more.

## The data we collect and why

We collect as little as the app needs to work, and nothing to learn about you.

- **Your email address.** To sign you in and to recognise you when you write to us. It comes from you at sign-in, or from Apple or Google when you sign in with them (Sign in with Apple can hide it behind Apple's relay). It is held by Firebase Authentication; our own database keeps only a hash of it.
- **Your Popt name, status line and avatar.** So friends recognise you. Only the name is required. Stored in the clear, as explained above.
- **Your encrypted content and its metadata.** To sync between your devices and to the people you share with.
- **Anonymous device identifiers.** To notify your devices and to tell them apart. Uses Apple's privacy preserving `identifierForVendor`.
- **Your subscription receipts.** To unlock Popt Pro on all your devices. They come from Apple when you subscribe; we never see payment details.
- **Request logs** (IP address, time, path). To keep the service running and to investigate abuse, like any web server.
- **Abuse reports.** To act on harmful behaviour. They come from the people who send them.

**What we do not collect:** your birth date, your contacts, your photo library, your location, analytics about how you use the app, or an advertising identifier.

**Legal bases.** We process your data to provide the service you asked for (the contract with you), because you chose to share something or allow a permission (consent, which you can withdraw), to keep the service secure and to answer abuse reports (our legitimate interest, and in part a legal duty), and to meet accounting and tax obligations (legal duty).

**We never sell data, never share it for advertising, and never use your content to train anything.**

## Services the app connects to

This is the complete list. If the app talks to it, it is here.

### Popt servers 

They run on Google Cloud in the United States, and the encrypted photos and files are stored with Cloudflare, also in the United States. We say so plainly because location matters, and because of how little it matters here: what sits on those servers is content we cannot read, plus the metadata listed above. Your content is as unreadable in a US data centre as it would be in a Swiss one, and the metadata is protected by the same rules wherever it is.

All of them live under `*.popt.com`. Here is what each feature of the app sends:

- **Syncing between your devices.** Your encrypted content, the metadata listed above, and proof that you are signed in.
- **Friends and sharing.** The account identifiers that are connected as friends, the account identifiers that belong to each shared list, project or post, and locked copies of shared keys.
- **Messaging.** Your encrypted messages, and the account identifiers of the two sides of a conversation.
- **Notifications.** The address Apple gives us to reach your device, the account identifiers of sender and recipients, and the encrypted preview.
- **Popt Pro.** Apple's receipt for your subscription, so Pro can be unlocked on all your devices.
- **Signing in by email.** Your email address, so we can send you the one-time code.
- **Adding to your library.** Your search for a book, film, show, game or podcast, with your language and age band. Search queries are not logged.
- **Publishing a library item as a link.** The item you chose to publish. The published item itself is not linked to your account.
- **Reporting abuse.** Your report, encrypted and only readable by our review team.
- **Avatars.** The style you picked, and a random number the avatar is drawn from. Nothing about you.

Our servers keep standard request logs for 30 days: which address called which feature, and when.

### Google services

[Google's privacy policy](https://policies.google.com/privacy) applies to all of these. Firebase and Google Cloud each publish a page of their own, linked below.

- **Sign-in ([Firebase Authentication](https://firebase.google.com/support/privacy)).** Holds your email address and how you sign in. With Sign in with Google, also the name and photo on your Google account.
- **Proof the app is genuine ([Firebase App Check](https://firebase.google.com/support/privacy)).** Before our servers answer, the app proves it is a real copy of Popt running on a real device. Google sees that proof, not what the request is for.
- **Push delivery ([Firebase Cloud Messaging](https://firebase.google.com/support/privacy)).** Relays our notifications to Apple's push service. Holds the address Apple gives us to reach your device. The notification it relays is encrypted.
- **Hosting ([Google Cloud](https://cloud.google.com/terms/cloud-privacy-notice)).** Runs our servers and database in the United States, and so holds everything our servers hold.
- **YouTube.** When you save a YouTube link, your device asks YouTube for its title and thumbnail. When you play a trailer inside the app (16 and over), the app loads YouTube's player, and YouTube sees you as a visitor to its site would, cookies included. YouTube has no separate policy: Google's covers it.

### Apple services

[Apple's privacy policy](https://www.apple.com/legal/privacy/) applies to all of these. Where Apple publishes a page for one service, it is linked below.

- **[Sign in with Apple](https://www.apple.com/legal/privacy/data/en/sign-in-with-apple/).** Apple tells us your email address, or the private relay address you chose to hide it behind.
- **Notifications (the Apple Push Notification service).** Delivers our notifications to your device. Apple carries the encrypted envelope and cannot read it.
- **Popt Pro (the [App Store](https://www.apple.com/legal/privacy/data/en/app-store/)).** Your subscription is bought from and billed by Apple. A purchase is tied to your Popt account by a random token, and Apple's receipt is what our servers check.
- **Places ([Apple Maps](https://www.apple.com/legal/privacy/data/en/apple-maps/)).** Searching for a place, showing the map and turning coordinates into an address all go to Apple from your device. Searches are tied to a rotating identifier, not to your Apple ID or Popt account.
- **Music ([Apple Music](https://www.apple.com/legal/privacy/data/en/apple-music/) and [Shazam](https://www.apple.com/legal/privacy/data/en/music-recognition/)).** Searching for an album or artist goes to Apple Music. Recognising a song sends a short audio fingerprint to Shazam, not the recording.
- **Age range.** Asked of iOS on the device, as described under [Children and age](#children-and-age). It comes from the age on your [Apple Account](https://www.apple.com/legal/privacy/data/en/apple-account/).


### PowerSync

[PowerSync's privacy policy](https://www.powersync.com/legal/privacy-policy) applies.

PowerSync (JourneyApps) is the service handling down-sync from the Popt database to your devices. Your devices connect to it directly, with a token from our servers, in the United States.

### Cloudflare R2

[Cloudflare's privacy policy](https://www.cloudflare.com/privacypolicy/) applies.

Your encrypted photos and files are stored with Cloudflare, in the United States. The app uploads and downloads them directly, at a short-lived address our servers hand it, so Cloudflare sees your IP address, the encrypted bytes and their size, and a storage key that starts with your account identifier. Never a filename, never the content.

### Wikipedia and Wikidata

[The Wikimedia privacy policy](https://foundation.wikimedia.org/wiki/Policy:Privacy_policy) applies.

When you add an artist to your library, your device asks Wikidata which Wikipedia article belongs to that artist, then asks Wikipedia for its first paragraph. They see your IP address and the artist, nothing about your account.

### Others

Some requests go straight from your device to whatever site a link points at. That site sees your IP address, as it does when you visit it in any browser. We cannot list those sites, because they depend on the links you save.

- **Link previews.** When you save or paste a link, your device fetches that page to show a title and image. TikTok links use TikTok's preview endpoint. Images in search results and link previews load from their original hosts. If you are signed in to a site in the Popt browser, those preview requests carry that site's cookies.
- **Notification images.** When a friend's post includes a link, your device fetches the link's image to show it in the notification.
- **The Popt browser** is a normal web browser: the sites you visit see you as any browser would. Its history and cookies stay on your device, and a browser opened inside a secret vault keeps nothing.

## Services we use behind the scenes

Your device never connects to these. Our servers do, from our address, and pass on no identity, account or IP address.

### Twilio SendGrid

[Twilio's privacy policy](https://www.twilio.com/en-us/legal/privacy) applies.

Sends the sign-in code email, and so receives your email address once per sign-in.

### TMDB

[TMDB's privacy policy](https://www.themoviedb.org/privacy-policy) applies.

When you search for a film, TV show, actor or director, our server forwards the words you typed and your language.

### Movie of the Night

[Movie of the Night's privacy policy](https://www.movieofthenight.com/privacy) applies.

Tells the app where a film or show can be streamed. Our server sends it the film's catalogue number and your country.

## On your device only

Several of Popt's smarter features run entirely on your phone. Nothing about them is sent to us.

- **Sorting what you type.** When you jot something, a small machine-learning model bundled with the app decides whether it looks like a task, a shopping item, a journal entry or a note, and sorts shopping items into aisles. The models run on the device. Your text is not sent anywhere for this. For a language we ship no model for, the app asks [Apple Intelligence](https://www.apple.com/legal/privacy/data/en/intelligence-engine/) on the device when it is available, and otherwise does nothing.
- **Search.** Popt's search index is built on your device from your decrypted content and never leaves it. If you turn on Siri and Spotlight for Popt, Apple's own on-device index receives the tasks, lists and notes you choose. That index stays on the device and is covered by [Apple's Siri policy](https://www.apple.com/legal/privacy/data/en/ask-siri-dictation/).
- **Photo screening.** On devices where Apple's Sensitive Content Warning or Communication Safety is turned on, Popt asks iOS to check every photo it shows for nudity, on the device. Flagged photos are blurred. The photos are not sent anywhere for this check, and we never learn the result.
- **Age range.** If you use a feature that is age-restricted, Popt asks iOS which age range you fall in (under 13, 13 to 15, 16 to 17, or 18 and over). Popt never sees a birth date. The answer is stored with your encrypted settings, so we cannot read it in our database. The one place it travels in the clear is the Add to Library search: the coarse band (under 13, 13 to 15, 16 to 17, 18 and over) goes with the query so results fit the age, without your account attached.
- **Location.** Attaching a place to an entry uses your device's location only when you choose to, and only if you have allowed it in iOS. The coordinates are encrypted like any other content. Turning the coordinates into an address is a request from your device to Apple Maps, under Apple's [Location Services](https://www.apple.com/legal/privacy/data/en/location-services/) and [Apple Maps](https://www.apple.com/legal/privacy/data/en/apple-maps/) policies. It never goes through our servers.
- **Reminders.** Reminder alerts for dated tasks are scheduled locally by the app, not by a server.

## Social features

Popt has no public directory of profiles: nobody can find you or see anything of yours without a direct invite. Everything you share stays end-to-end encrypted, and the people you share with can only read what you shared. Our servers see the account identifiers involved, never the content.

### Invites

An invite is a link. The optional message and library item inside it are encrypted on your device with a key that travels in the link itself, so that the invite contents are not stored in clear on our server but invites remain previewable by anyone who holds the full link. Accepting an invite connects the two account identifiers as friends and exchanges the keys that later sharing is built on.

### Posts

A post is encrypted for the friends you chose when you posted it, and every comment is encrypted for the people in the post at that moment. 
- Only the user who posted can add or remove participants
- New participants do not see previous comments
- Removed participants cannot see newer comments but keep access to the post and all comments they could see when they were removed

### Direct messages

Each side of a conversation owns its half: your messages are encrypted under a key only the two of you hold, and the other person can neither edit nor delete them. Deleting one of your own messages removes it for both of you. Our servers see that two account identifiers exchange encrypted messages, and when.

### Shared lists, projects and notes

Collaborative content is encrypted under a key shared by everyone in it, and each member can read or edit according to the role you gave them. When you remove someone, the content is re-encrypted under a new key and taken off their devices at the next sync. What they wrote while they were a member stays in the list, under your ownership.

### Reporting abuse

Reporting is the one case where content reaches us in readable form. When you report a profile, a post or a message, the report carries the content you are reporting, its photos and, for a message, the few messages around it for context, plus an optional note. Reported content is displayed before you send the report so that you know exactly what you're sending. The report is then encrypted on your device before being sent to us, so that only our review team can open it. The reported account is not informed of your report, but may be suspended or entirely banned from using our services.

## Deleting and keeping data

**Deleting content.** Anything you delete goes to Recently Deleted for 30 days, where you can restore it or purge it at once. After 30 days our servers hard-delete it. A photo or file is erased from storage as soon as the last item pointing to it is gone. Content shared with others lives on their devices too: deleting your copy does not delete theirs.

**Deleting your account.** Open My Account, choose Delete Account and type the confirmation phrase. Within 7 days we delete your sign-in, your profile, your keys, your encrypted content and files, your push tokens and your notification settings. Shared lists, notes and projects that you own are deleted for everyone in them, and so are your posts with all their comments, your comments on other people's posts and your messages. What you added to friends' lists, notes and projects stays there. Friends then see "Deleted account" in place of your name. Anything you add between the request and the deletion is deleted too, and nothing can be recovered afterwards. Deleting your account does not cancel a Popt Pro subscription: cancel it in your Apple Account's subscription settings. If you no longer have a signed-in device, email support@popt.com from the address you signed up with and we will delete the account for you.

Some data needs to be retained longer in order to fulfill our legal obligations:
- Subscription records that Apple requires us to keep for accounting are kept as long as legally required. 
- Abuse reports are kept as long as we need them to act on the report and to answer for our decision, even after the reported account is gone. 

**Signing out** deletes your content from the device: the database, the photo and file caches, the browser's cookies and logins, the Spotlight index and your settings. If you have enabled iCloud Keychain on the device you signed in to Popt, the recovery code remains in your keychain so that you can easily sign in back to Popt, on any device where you're logged in with the same Apple ID.

**Everything else is short-lived.** Notification delivery records are deleted after 31 days; sign-in codes, invite links and rate-limit counters are deleted when they expire.

## Your rights

Wherever you live, you have rights over your data, and we give everyone the GDPR's full set. Most of them you can exercise yourself inside the app, which is how we prefer it, because we cannot read your content and should not have to.

- **Access and portability.** Export everything from My Account. The export is a folder of plain Markdown files and your photos, readable by any text editor and by Obsidian. It covers your own content and what others shared with you. Content in a secret vault is exported by first moving it to Home from inside the vault.
- **Correction.** Edit anything in the app. Your profile name, status and avatar are yours to change at any time.
- **Deletion.** Delete content, or your whole account, as described above.
- **Objection and restriction.** We do no profiling, no advertising and no automated decisions about you, so there is nothing to object to in that sense. If you believe we hold something we should not, write to us.
- **Withdrawing consent.** Location, notifications, photo access and the age range are iOS permissions you can withdraw in Settings at any time. The app keeps working without them.
- **Complaint.** You can complain to the Swiss Federal Data Protection and Information Commissioner (FDPIC, edoeb.admin.ch) or to your own country's data protection authority. We would rather you write to us first, but you do not have to.

For anything you cannot do in the app, email us at **support@popt.com**. Because we cannot see your content, we may ask you to prove you control the account, for instance by sending from the email address you signed up with.

**Where your data is.** Our servers and storage are in the United States, as described under [Services the app connects to](#services-the-app-connects-to). Transfers out of Switzerland and the EU are covered by the EU standard contractual clauses with each provider, and by the encryption itself: what leaves is content we cannot read.

## Children and age

Popt is rated 13+ on the App Store, and parents can approve it for a younger child through Screen Time. The one piece of personal data this involves is the **age range**, and here is how we handle it.

We never ask for a birth date. When someone first uses an age-restricted feature, Popt asks iOS which age range they fall in (under 13, 13 to 15, 16 to 17, or 18 and over) through Apple's Declared Age Range API, which parents set up in Family settings. The answer is stored with your encrypted settings, where we cannot read it. The only place the band travels in the clear is the Add to Library search, so that results fit the age, and it isn't linked to your account.

What each age range unlocks, how parental approval of new friends works and how flagged photos are handled is explained on our content safety page: [popt.com/content-safety](https://popt.com/content-safety). We collect nothing else about minors.

## Verify it yourself

You should not have to take our word for any of this. We publish **veri-popt**, a set of tools and documentation for checking Popt's cryptography: [github.com/SkileSA/veri-popt](https://github.com/SkileSA/veri-popt).

## Changes to this policy

When we change what the app collects or whom it talks to, we update this policy first and the app second. The date at the top is the date of the last change, and the full version history is public in our legal documents repository on GitHub, alongside our Terms of Service: [github.com/SkileSA/popt-legal](https://github.com/SkileSA/popt-legal). For a change that reduces your privacy, we will tell you by email before it takes effect.