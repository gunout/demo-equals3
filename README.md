<div align="center">

<svg width="720" height="180" viewBox="0 0 720 180" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="demo-equals3 — type juggling animation">
  <defs>
    <linearGradient id="grad" x1="0" y1="0" x2="1" y2="1">
      <stop offset="0%" stop-color="#0055A4"/>
      <stop offset="100%" stop-color="#EF4135"/>
    </linearGradient>
    <filter id="glow">
      <feGaussianBlur stdDeviation="2" result="blur"/>
      <feMerge><feMergeNode in="blur"/><feMergeNode in="SourceGraphic"/></feMerge>
    </filter>
  </defs>

  <!-- Fond -->
  <rect width="720" height="180" fill="#0d1117" rx="12"/>
  <rect x="1" y="1" width="718" height="178" fill="none" stroke="url(#grad)" stroke-width="2" rx="12"/>

  <!-- Titre -->
  <text x="360" y="45" text-anchor="middle" fill="#ffffff" font-family="monospace" font-size="20" font-weight="700" filter="url(#glow)">
    demo-equals3
  </text>
  <text x="360" y="68" text-anchor="middle" fill="#8b949e" font-family="monospace" font-size="12">
    PHP type juggling — == vs === on MD5 magic hashes
  </text>

  <!-- Boîte gauche : hash magique 1 -->
  <g>
    <rect x="40" y="95" width="220" height="50" rx="8" fill="#161b22" stroke="#0055A4" stroke-width="1.5"/>
    <text x="150" y="118" text-anchor="middle" fill="#58a6ff" font-family="monospace" font-size="11">0e462097431…</text>
    <text x="150" y="135" text-anchor="middle" fill="#8b949e" font-family="monospace" font-size="9">= 0 × 10^n = 0</text>
    <animate attributeName="opacity" values="0.6;1;0.6" dur="2s" repeatCount="indefinite"/>
  </g>

  <!-- Opérateur == -->
  <text x="290" y="128" text-anchor="middle" fill="#EF4135" font-family="monospace" font-size="18" font-weight="700">
    ==
    <animate attributeName="opacity" values="1;0.2;1" dur="1.2s" repeatCount="indefinite"/>
  </text>

  <!-- Boîte droite : hash magique 2 -->
  <g>
    <rect x="320" y="95" width="220" height="50" rx="8" fill="#161b22" stroke="#EF4135" stroke-width="1.5"/>
    <text x="430" y="118" text-anchor="middle" fill="#ff7b72" font-family="monospace" font-size="11">0e830400451…</text>
    <text x="430" y="135" text-anchor="middle" fill="#8b949e" font-family="monospace" font-size="9">= 0 × 10^n = 0</text>
    <animate attributeName="opacity" values="0.6;1;0.6" dur="2s" begin="0.3s" repeatCount="indefinite"/>
  </g>

  <!-- Flèche -->
  <text x="565" y="128" text-anchor="middle" fill="#8b949e" font-family="monospace" font-size="16">→</text>

  <!-- Résultat TRUE -->
  <g>
    <rect x="585" y="105" width="100" height="35" rx="6" fill="#EF4135">
      <animate attributeName="fill" values="#EF4135;#ff6b5e;#EF4135" dur="2s" repeatCount="indefinite"/>
    </rect>
    <text x="635" y="128" text-anchor="middle" fill="#ffffff" font-family="monospace" font-size="14" font-weight="700">TRUE</text>
  </g>

  <!-- Ligne de scan -->
  <line x1="40" y1="160" x2="680" y2="160" stroke="#30363d" stroke-width="1"/>
  <circle r="3" fill="#0055A4">
    <animate attributeName="cx" values="40;680;40" dur="4s" repeatCount="indefinite"/>
    <animate attributeName="cy" values="160;160;160" dur="4s" repeatCount="indefinite"/>
    <animate attributeName="fill" values="#0055A4;#EF4135;#0055A4" dur="4s" repeatCount="indefinite"/>
  </circle>
</svg>

<br/>

# 🧪 demo-equals3

**Démonstration interactive du type juggling PHP (`==` vs `===`) sur les hashs MD5**

[![Live Demo](https://img.shields.io/badge/demo-live-0055A4?style=for-the-badge&logo=githubpages&logoColor=white)](https://gunout.github.io/demo-equals3/)
[![License](https://img.shields.io/badge/license-MIT-EF4135?style=for-the-badge)](./LICENSE)
[![Made with ❤️](https://img.shields.io/badge/made%20with-%E2%9D%A4%EF%B8%8F-EF4135?style=for-the-badge)](#)

</div>

---

## ⚡whoami

🔐 **Security Demo** — type juggling PHP, `==` vs `===` sur hashs MD5
🌐 **Web** — HTML, JavaScript, SVG inline, CSS custom
🐚 **Zero Build** — un seul `index.html`, aucune dépendance locale
🧪 **Interactive** — calculateur MD5 en direct, simulateur PHP 7.4 / 8.0+
🎯 **Education** — sensibilisation aux bonnes pratiques d'authentification

## 🎯le projet

Démonstration **interactive et pédagogique** de la faille **type juggling** en PHP.

En **PHP < 8.0**, `==` convertit les chaînes numériques en nombres. Un hash MD5 commençant par `0e` suivi de chiffres (`0e462097…`) est interprété comme **0 × 10^n = 0**. Deux hashs « magiques » différents deviennent donc **égaux**, permettant de contourner une authentification mal codée.

> ⚠️ **Usage pédagogique uniquement.** Ne pas utiliser sur un système sans autorisation écrite.

## 🛠️tech_stack

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat-square&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black)
![PHP](https://img.shields.io/badge/PHP-777BB4?style=flat-square&logo=php&logoColor=white)
![GitHub Pages](https://img.shields.io/badge/GitHub%20Pages-deployed-2f855a?style=flat-square&logo=github&logoColor=white)

## 🚀démo

👉 **[gunout.github.io/demo-equals3](https://gunout.github.io/demo-equals3/)**

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

## 🛡️défense

```php
// ❌ vulnérable
if (md5($input) == $stored) { /* … */ }

// ⚠️ strict
if (md5($input) === $stored) { /* … */ }

// ✅ constant-time
if (hash_equals($stored, md5($input))) { /* … */ }

// ✅✅ mots de passe
if (password_verify($input, $stored)) { /* … */ }
```

## 📂structure

```
demo-equals3/
├── index.html      # démo complète
├── README.md       # ce fichier
└── LICENSE         # MIT
```

## 🧭références

- 📚 [PHP RFC — Saner string to number comparisons](https://wiki.php.net/rfc/string_to_number_comparison)
- 📖 [OWASP — PHP Type Juggling](https://owasp.org/www-community/vulnerabilities/PHP_Object_Injection)
- 🧪 [DVWA](https://github.com/digininja/DVWA)
- 🔐 [PHP `password_hash()`](https://www.php.net/manual/fr/function.password-hash.php)

## ⚖️éthique & légalité

Usage **pédagogique uniquement**. En France, l'accès non autorisé à un système est réprimé par l'**article 323-1 du Code pénal**.

## 📄licence

MIT — voir [LICENSE](./LICENSE).

## 👤auteur

**[@gunout](https://github.com/gunout)**

---

<div align="center">

[![GitHub stars](https://img.shields.io/github/stars/gunout/demo-equals3?style=social)](https://github.com/gunout/demo-equals3/stargazers)
[![GitHub forks](https://img.shields.io/github/forks/gunout/demo-equals3?style=social)](https://github.com/gunout/demo-equals3/network/members)

</svg>
</div>
