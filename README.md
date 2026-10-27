# 🧪 demo-equals3

## ⚡whoami

🔐 **Security Demo** — Type juggling PHP, `==` vs `===` sur hashs MD5
🌐 **Web** — HTML, JavaScript, SVG inline, CSS custom
🐚 **Zero Build** — un seul `index.html`, aucune dépendance locale
🧪 **Interactive** — calculateur MD5 en direct, simulateur PHP 7.4 / 8.0+
🎯 **Education** — sensibilisation aux bonnes pratiques d'authentification
📦 **Deploy** — GitHub Pages, statique, 100 % client-side

## 🎯le projet

Démonstration **interactive et pédagogique** de la faille **type juggling** en PHP.

En **PHP < 8.0**, `==` convertit les chaînes numériques en nombres. Un hash MD5 commençant par `0e` suivi de chiffres (`0e462097…`) est interprété comme **0 × 10^n = 0**. Deux hashs « magiques » différents deviennent donc **égaux**, permettant de contourner une authentification mal codée.

**Ce que montre la démo :**
- 🧮 calculateur MD5 en direct avec détection de magic hash
- ⚖️ simulateur `==` / `===` sous PHP 7.4 et PHP 8.0+
- 🎬 animation pas à pas d'une attaque
- 🛡️ section défense (`hash_equals`, `password_verify`)
- 📊 table de magic hashes connus

> ⚠️ **Usage pédagogique uniquement.** Ne pas utiliser sur un système sans autorisation écrite. Voir [Éthique & légalité](#-éthique--légalité).

## 🛠️tech_stack

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat-square&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black)
![PHP](https://img.shields.io/badge/PHP-777BB4?style=flat-square&logo=php&logoColor=white)
![SparkMD5](https://img.shields.io/badge/SparkMD5-CDN-0055A4?style=flat-square)
![GitHub Pages](https://img.shields.io/badge/GitHub%20Pages-deployed-2f855a?style=flat-square&logo=github&logoColor=white)

## 🚀démo

👉 **[gunout.github.io/demo-equals3](https://gunout.github.io/demo-equals3/)**

Ou en local :

```bash
git clone https://github.com/gunout/demo-equals3.git
cd demo-equals3
xdg-open index.html    # Linux
open index.html        # macOS
start index.html       # Windows
```

## 🧪exemples à tester

| entrée | md5 | magic |
|---|---|---|
| `240610708` | `0e462097431906509019562988736854` | ✅ |
| `QNKCDZO` | `0e830400451993494058024219903391` | ✅ |
| `aabg7XSs` | `0e087386482136013740957780965295` | ✅ |
| `aabC9RqS` | `0e041022518165728065344349536299` | ✅ |
| `password` | `5f4dcc3b5aa765d61d8327deb882cf99` | ❌ |
| `admin` | `21232f297a57a5a743894a0e4a801fc3` | ❌ |

**Comparaisons à essayer dans le simulateur :**

- `0e462097431906509019562988736854` vs `0e830400451993494058024219903391`
  - `==` + PHP 7.4 → **true** ⚠️
  - `===` → **false** ✅
  - `==` + PHP 8.0+ → **false** ✅
- `"abc" == 0` PHP 7.4 → **true**
- `"1" == "01"` PHP 7.4 → **true**

## 🛡️défense

```php
// ❌ vulnérable
if (md5($input) == $stored) { /* … */ }

// ⚠️ mieux (strict, mais pas timing-safe)
if (md5($input) === $stored) { /* … */ }

// ✅ constant-time
if (hash_equals($stored, md5($input))) { /* … */ }

// ✅✅ pour des mots de passe : oublier MD5
if (password_verify($input, $stored)) { /* … */ }
```

## 📂structure

```
demo-equals3/
├── index.html      # démo complète (HTML + CSS + JS inline)
├── README.md       # ce fichier
└── LICENSE         # MIT
```

## 🧭références

- 📚 [PHP RFC — Saner string to number comparisons](https://wiki.php.net/rfc/string_to_number_comparison)
- 📖 [OWASP — PHP Type Juggling](https://owasp.org/www-community/vulnerabilities/PHP_Object_Injection)
- 🧪 [DVWA — Damn Vulnerable Web Application](https://github.com/digininja/DVWA)
- 🎯 [Root-Me — challenges PHP](https://www.root-me.org/)
- 🔐 [PHP `password_hash()`](https://www.php.net/manual/fr/function.password-hash.php) / [`password_verify()`](https://www.php.net/manual/fr/function.password-verify.php)

## ⚖️éthique & légalité

Ce projet est conçu **exclusivement** pour l'apprentissage et la sensibilisation à la sécurité, dans des environnements autorisés (labo, CTF, DVWA).

**Interdit** : l'utiliser pour tenter d'accéder à un système sans autorisation écrite. En France, l'accès ou le maintien frauduleux dans un système de traitement automatisé de données est réprimé par l'**article 323-1 du Code pénal** (jusqu'à 3 ans d'emprisonnement et 100 000 € d'amende).

L'auteur décline toute responsabilité en cas d'usage malveillant.

## 📄licence

MIT — voir [LICENSE](./LICENSE).

## 👤auteur

**[@gunout](https://github.com/gunout)**

🐍 Python & Automation · 🌐 Web · 🐚 Shell · 📊 Veille & Data · 🚀 Rapid Shipping

---

<div align="center">

**⭐ si ce projet t'a été utile, laisse une étoile**

[![GitHub stars](https://img.shields.io/github/stars/gunout/demo-equals3?style=social)](https://github.com/gunout/demo-equals3/stargazers)
[![GitHub forks](https://img.shields.io/github/forks/gunout/demo-equals3?style=social)](https://github.com/gunout/demo-equals3/network/members)

</div>
