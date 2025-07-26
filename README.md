# 🕒 Timezone & Timestamp API

Une API simple, rapide et **internationale** pour manipuler le temps.
Multi-fuseaux, multi-langues, et pensée pour s’intégrer **partout**.

---

## ✨ Fonctionnalités

* 🔁 Conversion de **timestamp en date lisible**
* 🌍 Liste des fuseaux horaires avec date/heure locale et offset UTC
* 🕐 Renvoi du timestamp Unix actuel (`Date.now()`)

---

## 🌐 Lien de l’API

> 88.151.197.191:2025

---

## 🚀 Exemples d’appel

### 🕐 Récupérer le timestamp actuel en secondes

```js
fetch('http://' + '88.151.197.191:2025' + '/time/now')=
  .then(res => res.json())
  .then(data => {
	console.log(data.time); // ex: 1700000000 (s)
  });
```

---

### 🔄 Convertir un timestamp en date lisible

```js
fetch('http://' + '88.151.197.191:2025' + '/time/convert', {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify({
	timestamp: 1700000000, // Attention à bien envoyer un timestamp en seconde et pas en millisecondes !
	locale: 'fr',
	timezone: 'Europe/Paris'
  })
})
.then(res => res.json())
.then(data => {
  console.log(data.time); // ex: "Mardi 14 novembre 2023 à 23h13"
});
```

---

### 🌐 Récupérer la liste des fuseaux horaires triés

```js
fetch('http://' + '88.151.197.191:2025' + '/time/timezone?search=europe&locale=fr-FR')
  .then(res => res.json())
  .then(data => {
	for (const tz in data) {
	  const { time, offset, localTimestamp } = data[tz];
	  console.log(`${time} (${offset}) - ${localTimestamp} - ${tz}`);
	}
  });
```

---

## 🔧 Paramètres acceptés

### `/time/convert` – POST JSON

| Champ       | Type   | Description                                             | Par défaut        |
| ----------- | ------ | ------------------------------------------------------- | ----------------- |
| `timestamp` | number | Timestamp Unix en seconde à convertir                   | — *(obligatoire)* |
| `locale`    | string | Langue (`fr`, `en`, `de`, etc.)                         | `fr`              |
| `timezone`  | string | Fuseau horaire (ex: `Europe/Paris`, `America/New_York`) | `Europe/Paris`    |

---

### `/time/timezone` – GET Query

| Paramètre | Type   | Description                                       | Par défaut        |
| --------- | ------ | ------------------------------------------------- | ----------------- |
| `search`  | string | Filtrer les fuseaux par nom (ex: `europe`, `paris`) | `""` (aucun)    |
| `locale`  | string | Langue de formatage (`fr-FR`, `en-US`, etc.)      | `fr-FR`           |

---

## 🌐 Exemple d’intégration HTML

Un exemple complet est disponible dans [`timeApi.html`](./timeApi.html), incluant :

* Récupération du timestamp actuel
* Conversion d’un timestamp personnalisé
* Recherche de fuseaux horaires avec heure locale

---

## 🧠 À propos

API développée pour être **sans dépendances** et **intégrable en 1 minute**.
Sans aucune base de données, ni aucun service tiers.

---

## 💬 Contact

Tu veux proposer une amélioration ? Discuter de l’intégration dans un projet plus vaste ?

* [@console.log(" \*x1 ")](https://discord.com/users/1066067393123733595)
* [@! ℳ𝓪𝔁𝟑𝟐](https://discord.com/users/1163887501895815168)

---

## Vu total de nos API
<img src='https://komarev.com/ghpvc/?username=console-log-Max32-API&style=for-the-badge'>

---

> 🛠️ Maintenu par des devs **passionnés & bénévoles**. Soyer compréhensif 🙏

> Chatgpt nous as permis d'économiser du temps en rédigeant à notre place le fichier d'exemple (html) et le readme. Je pense que je n'apprends rien à personne en précisant que cet outil magique a encore besoin d'une supervision humaine.
