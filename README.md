<div align="center">

# 🧪 demo-equals3

**Démonstration interactive du type juggling PHP (`==` vs `===`) sur les hashs MD5**

[![Live Demo](https://img.shields.io/badge/demo-live-0055A4?style=for-the-badge&logo=githubpages&logoColor=white)](https://gunout.github.io/demo-equals3/)
[![GitHub Pages](https://img.shields.io/badge/GitHub%20Pages-deployed-2f855a?style=for-the-badge&logo=github&logoColor=white)](https://gunout.github.io/demo-equals3/)
[![License](https://img.shields.io/badge/license-MIT-EF4135?style=for-the-badge)](./LICENSE)

[![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white)](https://developer.mozilla.org/fr/docs/Web/HTML)
[![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black)](https://developer.mozilla.org/fr/docs/Web/JavaScript)
[![PHP](https://img.shields.io/badge/PHP-777BB4?style=flat-square&logo=php&logoColor=white)](https://www.php.net/)
[![Security](https://img.shields.io/badge/security-type%20juggling-EF4135?style=flat-square&logo=shield&logoColor=white)](#)

[![Made with ❤️](https://img.shields.io/badge/made%20with-%E2%9D%A4%EF%B8%8F-EF4135?style=flat-square)](#)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-2f855a?style=flat-square)](./CONTRIBUTING.md)
[![Maintained](https://img.shields.io/badge/maintained-yes-0055A4?style=flat-square)](#)

</div>

---

## 📖 À propos

`demo-equals3` est une **démonstration pédagogique interactive** qui illustre la faille dite de **type juggling** en PHP : l'utilisation de l'opérateur de comparaison lâche `==` au lieu de `===` sur des hashs MD5 peut permettre de contourner une authentification.

Le projet est **100 % local**, sans backend, sans envoi de données. Tout le calcul MD5 se fait dans le navigateur via [SparkMD5](https://github.com/satazor/js-spark-md5).

> ⚠️ **Avertissement** : ce projet est destiné à l'**apprentissage** et à la **sensibilisation** à la sécurité. Il ne doit en aucun cas être utilisé pour attaquer un système sans autorisation écrite. Voir [Éthique & légalité](#-éthique--légalité).

---

## ✨ Fonctionnalités

- 🔐 **Calculateur MD5 en direct** — tapez une chaîne, le hash s'affiche instantanément, avec détection automatique des « magic hashes » (`0e…`)
- 🧮 **Simulateur de comparaison PHP** — reproduit le comportement de `==` et `===` sous **PHP 7.4** (vulnérable) et **PHP 8.0+** (corrigé)
- 🎬 **Animation pas à pas** — visualisation d'une attaque type juggling en 5 étapes
- 📊 **Table de magic hashes connus** — `240610708`, `QNKCDZO`, `aabg7XSs`, `aabC9RqS`
- 🛡️ **Section défense** — comparaison stricte, `hash_equals()`, `password_hash()` / `password_verify()`
- ⚖️ **Vue côte à côte** — code vulnérable vs code sûr
- 🎨 **Design responsive** — thème clair, bandeau tricolore, animations SVG, accessible mobile
- 📦 **Zéro dépendance locale** — un seul fichier HTML, aucun build, aucun serveur

---

## 🚀 Démo en ligne

👉 **[https://gunout.github.io/demo-equals3/](https://gunout.github.io/demo-equals3/)**

Ou ouvrez simplement `index.html` dans votre navigateur après clonage.

---

## 🧠 Le concept en 30 secondes

En **PHP < 8.0**, l'opérateur `==` convertit les chaînes numériques en nombres avant de comparer :

```php
var_dump("0e462097431906509019562988736854" == "0e830400451993494058024219903391");
// bool(true)   ← ⚠️ deux hashs DIFFÉRENTS considérés égaux
```

Pourquoi ? Parce que `"0e4620…"` est interprété comme **0 × 10^4620… = 0**, et idem pour l'autre. Donc `0 == 0` → `true`.

Si une application compare `md5($password_saisi) == $hash_stocké` et que le hash stocké est lui-même « magique », un attaquant peut se connecter **sans connaître le vrai mot de passe**.

### Correction

| PHP | `"0e4620…" == "0e8304…"` |
|---|---|
| 7.4 | `true` ❌ |
| 8.0+ | `false` ✅ |

Et la **bonne pratique** reste :

```php
if (hash_equals($stored, md5($input))) { /* … */ }
// ou mieux, pour des mots de passe :
if (password_verify($input, $stored)) { /* … */ }
```

---

## 🛠️ Stack technique

| Composant | Rôle |
|---|---|
| **HTML5** | Structure sémantique |
| **CSS3** | Thème tricolore, animations, SVG inline, responsive |
| **JavaScript (vanilla)** | Simulateur PHP, animation, reveal au scroll |
| **SparkMD5** (CDN) | Calcul MD5 côté client |
| **GitHub Pages** | Hébergement statique |

Aucune étape de build. Aucun `npm install`. Aucun framework.

---

## 📂 Structure du projet

```
demo-equals3/
├── index.html      # Application complète (HTML + CSS + JS inline)
├── README.md       # Ce fichier
└── LICENSE         # MIT
```

---

## 🏁 Démarrage rapide

### Option 1 — Cloner et ouvrir

```bash
git clone https://github.com/gunout/demo-equals3.git
cd demo-equals3
# Ouvrir index.html dans le navigateur
xdg-open index.html      # Linux
open index.html          # macOS
start index.html         # Windows
```

### Option 2 — Serveur local (optionnel)

```bash
# Python 3
python3 -m http.server 8000

# ou avec Node
npx serve .
```

Puis ouvrir [http://localhost:8000](http://localhost:8000).

---

## 🧪 Exemples à tester

| Entrée | MD5 | Magique ? |
|---|---|---|
| `240610708` | `0e462097431906509019562988736854` | ✅ |
| `QNKCDZO` | `0e830400451993494058024219903391` | ✅ |
| `aabg7XSs` | `0e087386482136013740957780965295` | ✅ |
| `aabC9RqS` | `0e041022518165728065344349536299` | ✅ |
| `password` | `5f4dcc3b5aa765d61d8327deb882cf99` | ❌ |
| `admin` | `21232f297a57a5a743894a0e4a801fc3` | ❌ |

### Comparaisons à essayer dans le simulateur

- `0e462097431906509019562988736854` vs `0e830400451993494058024219903391`
  - `==` + PHP 7.4 → **true** ⚠️
  - `===` → **false** ✅
  - `==` + PHP 8.0+ → **false** ✅
- `"abc" == 0` en PHP 7.4 → **true** (chaîne non numérique convertie en 0)
- `"1" == "01"` en PHP 7.4 → **true** (entiers égaux)

---

## 🛡️ Éthique & légalité

Ce projet est conçu **exclusivement** pour :

- 🎓 l'apprentissage des failles de type juggling
- 🧑‍🏫 la sensibilisation des développeurs aux bonnes pratiques
- 🧪 des tests dans des **environnements autorisés** (labo, CTF, DVWA, etc.)

**Interdit** : l'utiliser pour tenter d'accéder à un système sans autorisation écrite. En France, l'accès ou le maintien frauduleux dans un système de traitement automatisé de données est réprimé par l'**article 323-1 du Code pénal** (jusqu'à 3 ans d'emprisonnement et 100 000 € d'amende).

L'auteur décline toute responsabilité en cas d'usage malveillant.

---

## 🧭 Pour aller plus loin

- 📚 [PHP RFC — Saner string to number comparisons](https://wiki.php.net/rfc/string_to_number_comparison)
- 📖 [OWASP — Type Juggling](https://owasp.org/www-community/vulnerabilities/PHP_Object_Injection)
- 🧪 [DVWA — Damn Vulnerable Web Application](https://github.com/digininja/DVWA)
- 🎯 [Root-Me — challenges PHP](https://www.root-me.org/)
- 🔐 [PHP `password_hash()`](https://www.php.net/manual/fr/function.password-hash.php) / [`password_verify()`](https://www.php.net/manual/fr/function.password-verify.php)

---

## 🤝 Contribution

Les contributions sont les bienvenues ! Voir [CONTRIBUTING.md](./CONTRIBUTING.md) (à créer) pour les guidelines.

```bash
# Fork → clone → branche → commit → PR
git checkout -b feat/ma-fonctionnalite
git commit -m "feat: ajout de …"
git push origin feat/ma-fonctionnalite
```

---

## 📄 Licence

Distribué sous licence **MIT**. Voir [LICENSE](./LICENSE) pour plus d'informations.

---

## 👤 Auteur

**gunout**

[![GitHub](https://img.shields.io/badge/GitHub-gunout-181717?style=flat-square&logo=github)](https://github.com/gunout)
[![Repos](https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fapi.github.com%2Fusers%2Fgunout&query=%24.public_repos&label=repos&color=0055A4&style=flat-square)](https://github.com/gunout?tab=repositories)

> 🐍 Python & Automation · 🌐 Web Development · 🐚 Shell & Scripting · 📊 Veille & Data · 🚀 Rapid Shipping

---

<div align="center">

**⭐ Si ce projet vous a été utile, n'hésitez pas à lui donner une étoile !**

[⬆ Retour en haut](#-demo-equals3)

</div>
