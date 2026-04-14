# Goodforest Landing Design System (v1) - LLM Prompting Guidelines

> **Rôle du LLM** : Ce document te sert de base de connaissances (System Prompt ou Contexte) pour générer du code HTML valide, esthétique et entièrement compatible avec le Design System (v1) du projet "goodforest".

---

## 1. Stack et Principes Fondamentaux
- **Technologie** : HTML/CSS pur. **AUCUN** framework CSS externe (ni Tailwind, ni Bootstrap). Zéro Javascript requis sauf pour les intéractions simples (accordéons).
- **Thèmes supportés** : Light, Dark, Forest. Gérés via l'attribut `data-theme` sur l'élément racine (`<html data-theme="dark">`).
- **Typographie** : `Poppins` (texte principal) et `JetBrains Mono` (code).
- **Règle d'or** : Utiliser **exclusivement** les classes utilitaires et sémantiques listées dans ce document pour conserver la cohérence visuelle. Ne pas écrire de styles inline (attribut `style="..."`) sauf si explicitement demandé.

---

## 2. Variables CSS Globales (Résumé)
Elles sont injectées au niveau du `:root`. N'utiliser ces variables que si tu dois écrire du CSS custom (à éviter si une classe utilitaire existe).
- **Couleurs de fond** : `--bg`, `--surface`, `--card`, `--ibg` (input background).
- **Couleurs de texte** : `--t1` (primary), `--t2` (secondary), `--t3` (muted).
- **Couleurs sémantiques** : `--primary`, `--accent` (avec ses variantes semi-transparentes `--acs`, `--acs-b`), `--alertes`, `--anomalie`, `--stress`, `--normal`.
- **Divers** : `--sh`, `--shm` (ombres), `--r`, `--r-sm` (border-radius), `--tr` (transition).

---

## 3. Structure de Page et Grilles

### Conteneurs de base
Chaque grande section de la landing page doit être englobée de cette manière :
```html
<section class="ds-sec">
  <div class="wrap">
    <!-- Contenu -->
  </div>
</section>
```
L'espacement de la section peut aussi être modifié en `.section` (padding 96px) ou `.section-sm` (padding 64px) via un wrapper `<div class="container">`.

### Grilles CSS (Responsive)
- `.g2` : Grille 2 colonnes (devient 1 colonne sur mobile < 600px).
- `.g3` : Grille 3 colonnes (2 col < 1000px, 1 col < 600px).
- `.g4` : Grille 4 colonnes (2 col < 1000px, 1 col < 600px).

---

## 4. Typographie
Toutes les tailles utilisent `clamp()` pour un responsive fluide automatique.
- `.lp-display` : Titre géant (Hero).
- `.lp-h1` : Titre de page principal.
- `.lp-h2` : Titre de section.
- `.lp-h3` : Titre de carte ou de composant.
- `.lp-overline` : Surtitre en majuscules (11px, très espacé, avec une barre colorée décorative en pseudo-élément).
- `.lp-lead` : Paragraphe introductif large et lisible.
- `.lp-body` : Texte courant de base (14.5px).
- `.lp-sm` : Texte secondaire (13px).
- `.lp-xs` : Mentions légales, texte tertiaire (11px).

**Utilitaires de texte** : 
- `.t-acc` (texte de couleur `--accent`)
- `.t-muted` (texte couleur `--t2`).

---

## 5. Composants UI (Copy-Paste Ready)

### 5.1. Boutons (`.btn`)
Les boutons doivent systématiquement avoir la classe `.btn`.
- **Tailles** : `.btn-sm`, `[défaut]`, `.btn-lg`, `.btn-xl`.
- **Variantes** :
  - `.btn-primary` (fond coloré)
  - `.btn-outline` (contour)
  - `.btn-ghost` (fond transparent)
  - `.btn-danger` (rouge).
- Les icônes SVG dans les boutons font 15x15px, `fill="none"`, `stroke="currentColor"`, `stroke-width="2.2"`.

### 5.2. Badges & Chips
- **Badges ronds (étiquettes sémantiques)** : `<span class="badge bg-green"><span class="bdot"></span>Normal</span>`.
  - Variantes de couleur : `.bg-green`, `.bg-red`, `.bg-orange`, `.bg-yellow`, `.bg-blue`, `.bg-gray`.
- **Chips (mot-clé simple)** : `<span class="chip">HTML/CSS</span>`.

### 5.3. Cards (`.card`)
Utilisé pour les blocs d'infos. Possibilité d'ajouter l'interaction au survol :
- `<div class="card card-lift"> ... </div>` (ajoute une ombre et remonte le bloc au hover).

### 5.4. Formulaires (`.form-group`)
Structure d'un champ :
```html
<div class="form-group">
  <label class="lp-label">Email professionnel</label>
  <input class="lp-input" placeholder="votre@email.com" />
  <!-- Pour Select : class="lp-select" -->
  <!-- Pour Textarea : class="lp-textarea" -->
</div>
```
- Champs en ligne : wrapper `<div class="inline-form">`.

### 5.5. Alertes & Bannières (`.lp-banner`)
Rendu visuel d'information (ex: Flash messages) :
```html
<div class="lp-banner b-green">
  <svg>...</svg> <!-- icône 17x17px -->
  <div>
    <div class="banner-title">Titre de l'alerte</div>
    Texte de l'alerte.
  </div>
</div>
```
Couleurs : `.b-green`, `.b-orange`, `.b-red`, `.b-blue`.

---

## 6. Animations (Classes utilitaires)
Animations fluides gérées en CSS (pas de JS d'intersection nécessaire pour ces comportements unitaires). Utiles pour animer l'apparition d'un Hero :
- `.anim-up` : Glisse de bas en haut et fade-in (0.5s).
- `.anim-in` : Fade-in pur (0.45s).
- **Delays (Stagger)** : `.d1` (0.1s) à `.d5` (0.5s).
  
> **Exemple** :
> `<h1 class="lp-display anim-up d1">Lancement</h1>`
> `<p class="lp-lead anim-up d2">Le sous-titre</p>`

- **Skeleton Loader** : `.skeleton` (sur une div avec largeur/hauteur pour un effet shimmer de chargement).

---

## Instructions pour l'Assistant IA (Prompt d'exécution)

Lorsque le client te demande de "créer une section" ou "créer une page" avec ce Design System :
1. **Identifie le composant** le plus adéquat parmi ceux listés ci-dessus (Faut-il une `.g3` ? des `.card` ? des `.badge` ?).
2. **Fournis uniquement le code HTML** (à moins qu'une règle CSS ou du JS ne soit formellement nécessaire ; tout a été prévu en principe).
3. Ne propose **jamais** de Tailwind ou de styles non-pertinents.
4. Tes classes CSS générées doivent strictement correspondre à ces règles (ex: `.lp-h2`, `.lp-lead`).
