# Aegis Bank - Landing Page Mobile-First

> **Note importante :** Ce projet a été réalisé dans le cadre d'un exercice pédagogique. Aegis Bank, Namcod et Remolut sont des entreprises fictives créées pour reproduire les conditions réelles du monde professionnel.

![HTML5](https://img.shields.io/badge/HTML5-E34C26?style=flat-square&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat-square&logo=css3&logoColor=white)
![BEM](https://img.shields.io/badge/Methodology-BEM-orange?style=flat-square)
![Lighthouse](https://img.shields.io/badge/Lighthouse-100%2F100-success?style=flat-square)

## Description

Landing page pour Aegis Bank, la néobanque éthique et transparente. Interface mobile-first avec contrainte **zero-scroll** : tout le contenu doit s'afficher dans une seule hauteur de viewport sans défilement.

**Technologies :** HTML5, CSS3 pur (zero JavaScript, zero framework)  
**Méthodologie :** BEM, SOLID principles, Mobile-First  
**Déploiement :** https://aegisbankproject.netlify.app/

## Le Challenge Zero-Scroll

Contrainte technique principale : créer une expérience mobile complète sans défilement vertical.

- Viewport fixe : `100dvh` sans overflow
- Optimisation chirurgicale du placement des éléments
- Typography et spacing adaptatifs avec `clamp()`
- Layout Flexbox pour distribution verticale intelligente

## Scores Lighthouse

| Métrique | Score |
|----------|-------|
| Performance | 100/100 |
| Accessibilité | 100/100 |
| Bonnes pratiques | 100/100 |
| SEO | 100/100 |

## Architecture du Projet

```
index.html (142 lignes)     → Structure HTML sémantique
style.css (271 lignes)      → CSS principal avec imports
│
└── styles/                 → Modules CSS organisés
    ├── all-variables.css   → Point d'entrée des variables
    ├── colors.css          → Palette de couleurs
    ├── typography.css      → Polices et tailles (@font-face Orbitron)
    ├── spacing.css         → Espacements et gaps responsifs
    ├── layout.css          → Helpers globaux
    ├── animations.css      → 3 keyframes CSS
    ├── button.css          → Composant Bouton (BEM)
    └── links.css           → Composant Links (BEM)
```

## Éléments Intégrés

### Header
- Logo Aegis Bank
- 2 boutons CTA : "Se connecter" / "S'inscrire"
- Menu burger SVG (visuel, non fonctionnel)

### Hero Section
- Titre H1 : "La néobanque éthique & transparente"
- Sous-titre motivant (< 140 caractères)
- Card promotionnelle : "20€ offerts - Mars 2026"
- CTA principal : "Télécharger l'app"
- 3 icônes réseaux sociaux SVG : Telegram, Mastodon, BlueSky

### Footer
- 3 liens légaux : Mentions • Confidentialité • CGU
- Copyright : "© 2025 Aegis Bank"
- Position fixe, hauteur optimisée

## Méthodologie BEM

Organisation stricte des classes CSS selon la convention Block Element Modifier :

```css
/* BLOCK - Composant principal */
.header { }
.card-promo { }
.social-links { }

/* ELEMENT - Partie d'un block */
.header__logo { }
.header__actions { }
.card-promo__title { }
.social-links__link { }

/* MODIFIER - Variante d'un block */
.btn--primary { }
.btn--ghost { }
```

**Avantages :**
- Zero conflit de styles
- Code auto-documenté
- Composants réutilisables et indépendants

## Animations CSS

3 animations fluides respectant la contrainte : **1 animation de contenu + 2 micro-interactions**

### 1. fade-in-up (Animation de contenu)
```css
@keyframes fade-in-up {
  from { opacity: 0; transform: translateY(1.2rem); }
  to { opacity: 1; transform: translateY(0); }
}
```
Appliquée sur `.main__container` au chargement (durée : 0.6s)

### 2. float-card (Micro-interaction)
```css
@keyframes float-card {
  0%, 100% { transform: translateY(0); }
  70% { transform: translateY(-0.6rem); }
}
```
Flottement continu de la card promo (durée : 4s infinite)

### 3. pulse-soft (Micro-interaction)
```css
@keyframes pulse-soft {
  0%, 100% { transform: scale(1); }
  50% { transform: scale(1.04); }
}
```
Pulsation douce sur les icônes sociales (durée : 3s infinite)

## Variables CSS

Système de design tokens centralisé pour cohérence et maintenabilité :

```css
:root {
  /* Typographie */
  --font-main: "OrbitronBold", sans-serif;
  --font-size-title: clamp(2.4rem, 3.6vw, 3.2rem);
  
  /* Couleurs */
  --color-primary: #4da3ff;
  --color-primary-hover: #1c7ed6;
  --second-primary: #ff6b6b;
  
  /* Spacing */
  --header-height: 5.5rem;
  --footer-height: 4.5rem;
  --gap-md: 1.2rem;
}
```

## Accessibilité WCAG AAA

- Attributs `aria-label` sur tous les éléments interactifs
- Focus states visibles (outline rouge 2px)
- Hiérarchie sémantique HTML5 stricte
- Contraste de couleurs validé WCAG AAA
- Balises sémantiques : `<header>`, `<main>`, `<footer>`

## Responsive Mobile-First

Approche mobile-first exclusive avec adaptation fluide :

- Viewport : `100dvh` (dynamic viewport height)
- Typography responsive : `clamp(min, preferred, max)`
- Spacing adaptatif avec variables CSS
- Zero media queries (adaptation via clamp)
- Overflow hidden pour zero-scroll

## Installation

### Prérequis
- VS Code avec extension Live Server
- Navigateur moderne (Chrome, Firefox, Edge)

### Lancement
```bash
# Cloner le repository
git clone git@github.com:CodeDoze/Aegis-Bank-Projet.git
cd Aegis-Bank-Projet

# Ouvrir dans VS Code
code .

# Clic droit sur index.html → Open with Live Server
# Le site s'ouvre sur http://localhost:5500
```

## Technologies

| Technologie | Usage |
|-------------|-------|
| HTML5 | Structure sémantique |
| CSS3 | Styles, animations, variables |
| Flexbox | Layout moderne |
| CSS Custom Properties | Design tokens |
| @font-face | Police Orbitron locale |
| SVG | Icônes vectorielles |

## Checklist Validation

### HTML
- [x] DOCTYPE, lang="fr", charset="UTF-8"
- [x] Meta viewport mobile
- [x] Meta description SEO
- [x] Balises sémantiques
- [x] Hiérarchie H1 correcte
- [x] Tous éléments requis présents

### CSS
- [x] Mobile-First uniquement (zero-scroll)
- [x] BEM methodology stricte
- [x] 3 animations CSS (1 contenu + 2 micro-interactions)
- [x] Variables CSS organisées (8 fichiers)
- [x] Commentaires détaillés
- [x] SOLID principles

### Qualité
- [x] Zero JavaScript
- [x] Zero framework
- [x] Accessibilité WCAG AAA
- [x] Lighthouse 100/100
- [x] Code propre et documenté

## Déploiement

- **Production :** https://aegisbankproject.netlify.app/
- **Repository :** https://github.com/CodeDoze/Aegis-Bank-Projet
- **Dernière mise à jour :** 11 décembre 2025

## Contributeur

Développé par [@CodeDoze](https://github.com/CodeDoze) dans le cadre de l'examen NAMCOD 2025.

---

**Projet pédagogique** - NAMCOD 2025 | Q1 + Q2


