# 🎰 TikTok Roulette

> Le jeu de soirée où chacun ajoute ses TikToks préférés en secret… puis tout le monde devine **qui a posté quoi** !

L'écran principal (TV ou ordi) diffuse les vidéos mélangées une par une, et chaque joueur vote depuis son téléphone pour deviner à qui appartient la vidéo. Pas d'appli à installer, pas de compte à créer : un QR code à scanner et c'est parti.

> ℹ️ Ce dépôt présente le projet. Le code source est hébergé dans un dépôt privé.

---

## ✨ En bref

- 📺 **Un écran partagé** (TV, ordi, vidéoprojecteur) qui diffuse les TikToks et affiche les résultats
- 📱 **Les téléphones comme manettes** : on rejoint en scannant un QR code, on ajoute ses vidéos, on vote
- ⚡ **Synchronisation en temps réel** entre tous les écrans
- 👥 **Jusqu'à 16 joueurs** par partie
- 🔒 **Aucun compte** : on recharge la page sans perdre sa partie
- 🔁 **Rejouer** en un clic avec les mêmes joueurs

---

## 🎮 Comment on joue ?

1. **L'hôte crée une partie** sur la TV et choisit ses réglages (mode de jeu, options, fin de partie).
2. **Les joueurs scannent le QR code**, choisissent un pseudo et collent leurs liens TikTok
   (*Partager → Copier le lien* dans l'appli TikTok).
3. **L'hôte lance la partie** : les vidéos sont mélangées et diffusées une par une.
4. **Tout le monde vote** sur son téléphone pour deviner à qui appartient la vidéo, y compris le propriétaire, qui vote pour **bluffer** 🎣.
5. **Révélations et podium** à la fin : on découvre enfin qui a posté quoi !

### Ajouter des vidéos

- 🔗 **Lien par lien** : liens classiques, liens courts `vm.tiktok.com` et carrousels photo
- 📁 **Dossier de favoris public** : le jeu compte les vidéos du dossier, puis pioche **au hasard** le nombre voulu, ou une **plage** (ex. de la n° 1 à la n° 25) pour se partager un même dossier à plusieurs sans doublons

---

## 🏆 Les modes de jeu

| | 🏆 Classique | 🍻 Picole |
|---|---|---|
| Au moins un joueur trouve | +1 point par bonne réponse | Le propriétaire de la vidéo boit **1 shot** |
| Personne ne trouve | +2 points pour le propriétaire | **Tous les autres** boivent 1 shot |
| Gagnant | Le plus de points | Le **moins** de shots |

*À consommer avec modération 😇*

---

## 🧩 Les options

| Option | Description |
|---|---|
| ❤️ **Qui a liké ?** | Au lieu de « qui a posté ? », on devine **qui a liké** chaque TikTok. Chaque joueur entre son @pseudo TikTok et le jeu pioche au hasard parmi ses derniers likes publics (3, 5 ou 10 par joueur). |
| 💀 **Mode hardcore** | Les téléphones ne disent plus « c'est ton TikTok » : quand c'est ta vidéo, **tu dois te reconnaître** et voter pour toi. Sinon : pénalité (+2 shots ou -2 points). |
| ⚡ **Réponse après chaque vidéo** | La TV dévoile pendant quelques secondes à qui appartenait le TikTok et qui a trouvé, sans révéler le classement. |
| 📊 **Checkpoints** | Toutes les 5 ou 10 vidéos, un classement intermédiaire s'affiche. On repart quand tout le monde a validé (« ✅ Shots pris ! »). |
| 🏁 **Fin de partie** | **Podium final** avec confettis 🎉, ou **récap vidéo par vidéo** sans classement. |

---

## 🗺️ Les écrans

| Écran | Appareil | Rôle |
|---|---|---|
| **Accueil** | TV / ordi | Créer une partie et choisir les réglages |
| **Écran hôte** | TV / ordi | Lobby avec QR code, lecture des vidéos, compteur de votes, révélations, podium |
| **Rejoindre** | Téléphone | Choisir un pseudo et ajouter ses TikToks |
| **Jouer** | Téléphone | Voter pendant la partie et voir ses résultats |

---

## 🛠️ Stack technique

- **[Next.js](https://nextjs.org)** (App Router) + **TypeScript**
- **[Tailwind CSS](https://tailwindcss.com)** pour l'interface
- **[Supabase](https://supabase.com)** : base Postgres + Realtime pour la synchro en direct
- **[Vercel](https://vercel.com)** pour l'hébergement

### Quelques choix techniques

- 🔐 **Anti-triche** : seul le serveur lit et écrit dans la base. Les navigateurs n'écoutent qu'un signal de mise à jour, sans aucune donnée secrète : impossible de voir les TikToks ou les votes des autres en fouillant la page.
- ⚡ **Temps réel** : à chaque action, tous les écrans sont prévenus via Supabase Realtime et se mettent à jour instantanément (avec un rafraîchissement de secours).
- ⏱️ **Pas de timer imposé** : dès que tout le monde a voté, la partie avance toute seule. L'hôte peut aussi passer à la suite sans attendre un retardataire.
- 🎬 **Lecteur TikTok officiel** : les vidéos privées ou supprimées sont détectées et sautées automatiquement.
- 🧮 **Scores toujours justes** : ils ne sont jamais stockés, mais recalculés à partir des votes.
- 🔊 **Son maîtrisé** : réactivation automatique du son et barre de volume à côté des vidéos.

---

## 📸 Aperçu

<!-- Ajoute tes captures d'écran ici, par exemple :
![Lobby](docs/lobby.png)
![Vote sur téléphone](docs/vote.png)
![Podium](docs/podium.png)
-->

*Captures d'écran à venir.*

---

## ⚠️ Avertissement

Projet personnel, non affilié à TikTok ni à ByteDance. L'ajout par dossier de favoris et le mode « Qui a liké ? » reposent sur l'API web non officielle de TikTok et peuvent cesser de fonctionner si TikTok la modifie.
