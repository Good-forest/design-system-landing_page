# Goodforest · Landing Page Design System (v1)

Bienvenue dans le dépôt du Design System destiné aux landing pages et pages vitrines du projet **goodforest** (solution de surveillance satellite des forêts).

Ce projet a été conçu pour être **ultra-léger, robuste et complètement indépendant**. L'objectif est de pouvoir construire des pages rapidement, avec un rendu moderne (vibrations, couleurs, micro-animations) sans avoir recours à des bibliothèques externes lourdes.

## 🌟 Caractéristiques principales

- **Pur HTML / CSS** : Zéro dépendance (ni Tailwind, ni Bootstrap). Le code minimal requis est dans un seul et même endroit.
- **Multi-Thèmes** : Support statique de 3 thèmes intégrés (`Light`, `Dark`, `Forest`) modifiables via un attribut data sur le nœud parent.
- **Totalement Responsive** : La typographie utilise la fonction CSS `clamp()` pour fluidifier le texte sur toutes les résolutions. Les systèmes de grilles refluent automatiquement sur mobile.
- **Prêt pour l'IA (BMAD)** : Ce répertoire inclut une documentation formatée spécifiquement pour servir de contexte/prompt aux assistants IA (LLMs) afin de générer vos futures pages de manière cohérente.

## 📂 Contenu du répertoire

- `index.html` : **Le fichier central**. Il s'agit du "Viewer" complet du système de design. Il contient dans son `<head>` toutes les variables et classes CSS nécessaires, et dans son `<body>` la galerie complète et documentée de chaque composant (Boutons, Cards, KPI, CTA, Formulaires, Navbars...).
- `goodforest_ds_llm_instructions.md` : Guide d'instructions (Prompt System) prêt à être injecté dans vos LLMs préférés (ChatGPT, Claude, Gemini, etc.) pour qu'ils codent de nouveaux écrans respectant exactement ce design.

## 🚀 Comment l'utiliser ?

1. **Explorer les composants** : Ouvrez simplement `index.html` dans n'importe quel navigateur (Google Chrome, Firefox, Safari). Aucune installation, aucun serveur n'est requis.
2. **Récupérer le style global** : Copiez le bloc `<style>` contenu dans la balise `<head>` du `index.html` et intégrez-le (ou exportez-le dans un fichier `style.css`) dans votre projet web final.
3. **Construire la page** : Naviguez dans la page web locale, trouvez le composant visuel souhaité, et inspectez/copiez le bloc HTML correspondant. En l'encapsulant dans les classes utilitaires de grille (`.g2`, `.g3`, `.g4`), vous obtiendrez des sections complètes de votre landing page.

## 🎨 Les Thèmes

Pour appliquer ou forcer un thème, utilisez l'attribut `data-theme` le plus haut possible dans le DOM (idéalement sur la balise `<html>` ou `<body>`).

```html
<html data-theme="light"> <!-- Thème par défaut clair -->
<html data-theme="dark">  <!-- Thème sombre contrasté -->
<html data-theme="forest"> <!-- Thème sombre émeraude, spécialisé métier -->
```

## 🛠️ Stack Technique

- **Langages** : HTML5, CSS3.
- **Polices (Google Fonts)** : `Poppins` (Design principal), `JetBrains Mono` (Snippets de code). Il est vivement conseillé de précharger ces polices via une balise `<link>`.
- **Iconographie** : Tous les icônes présents dans les composants sont générés directement via des tracés SVG inlines (zéro appel CDN).

---
*Conçu pour **goodforest**.*
