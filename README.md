# 🫧 Bubble — Jeu de bulles interactif

> Jeu web minimaliste où des bulles colorées apparaissent aléatoirement et disparaissent au clic avec un compteur de score.

🌐 **Voir le projet** → [github.com/elangebbakambo-prog/bubble](https://github.com/elangebbakambo-prog/bubble)

---

## 📋 Description

Des bulles surgissent en continu à des positions et tailles aléatoires, flottent vers le haut en changeant de couleur, et disparaissent au bout de 8 secondes. Le joueur doit cliquer dessus avant qu'elles s'échappent pour incrémenter son compteur. Projet centré sur les **animations CSS avancées**, les **propriétés CSS custom** et la **génération dynamique du DOM**.

---

## ⚙️ Fonctionnalités

- 🫧 **Génération automatique** — une nouvelle bulle apparaît toutes les secondes via `setInterval`
- 📐 **Taille aléatoire** — chaque bulle a une taille différente (entre 100px et 300px)
- 🎯 **Position aléatoire** — apparition à des positions `top` et `left` aléatoires
- 🌈 **Animation de couleur** — `hue-rotate` de 0° à 720° pendant le vol, les bulles changent de couleur en flottant
- 🛤️ **Trajectoire aléatoire** — propriété CSS custom `--left` injectée en JS pour une trajectoire unique à chaque bulle
- 💥 **Éclatement au clic** — la bulle disparaît instantanément au clic
- 🔢 **Compteur de score** — incrémente à chaque bulle cliquée, affiché en grand au centre
- ⏳ **Disparition automatique** — `setTimeout` de 8s supprime les bulles non cliquées
- 🎯 **Curseur crosshair** — ambiance jeu de tir

---

## 🏗️ Architecture du code

Le projet tient en **moins de 25 lignes de JavaScript** — c'est sa force :

### Fonction `bubbleMaker()`
Crée et configure chaque bulle :
- `document.createElement("span")` — crée l'élément bulle
- Injection de `size`, `top`, `left` aléatoires via `Math.random()`
- `setProperty("--left", ...)` — injecte une **CSS custom property** directement depuis JS pour personnaliser la trajectoire CSS de chaque bulle individuellement
- `addEventListener("click")` — incrémente le compteur et supprime la bulle
- `setTimeout(() => bubble.remove(), 8000)` — supprime automatiquement après 8 secondes

### `setInterval(bubbleMaker, 1000)`
Lance une nouvelle bulle toutes les secondes.

---

## 🎨 CSS notable

```css
@keyframes anim {
  to {
    top: -250px;
    left: var(--left);      /* trajectoire unique par bulle */
    opacity: 1;
    filter: hue-rotate(720deg); /* changement de couleur en vol */
  }
}
```

L'utilisation de `var(--left)` dans le keyframe permet à chaque bulle d'avoir sa propre trajectoire — une technique avancée combinant CSS custom properties et JavaScript.

---

## 🛠️ Stack technique

| Technologie | Usage |
|---|---|
| JavaScript | Génération DOM, `setInterval`, `setTimeout`, `Math.random()` |
| CSS3 | `@keyframes`, `hue-rotate`, CSS custom properties (`--left`) |
| HTML5 | Structure minimale |

---

## 👨‍💻 Développeur

**Elange Bakambo** — Développeur Web Junior  
🌐 [github.com/elangebbakambo-prog](https://github.com/elangebbakambo-prog)
