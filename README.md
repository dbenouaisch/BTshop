# Biker Tov MC — thème Shopify

Thème Shopify (Online Store 2.0) basé sur **Dawn**, le thème open-source officiel de Shopify,
entièrement reskinné avec l'identité graphique du mockup Biker Tov MC : fond noir, typographie
gothique **Pirata One** pour les titres, **Inter** pour le texte, bordures fines, badge circulaire
et panneaux encadrés.

Comme il repose sur Dawn, tout le moteur Shopify fonctionne nativement : fiches produits, variantes,
panier (tiroir latéral), checkout, recherche, filtres de collection, comptes clients, etc.

## Installation sur Shopify

1. Compresser le contenu de **ce dossier** (pas le dossier lui-même, son contenu : `assets/`,
   `config/`, `layout/`, `locales/`, `sections/`, `snippets/`, `templates/`) en `.zip`.
2. Dans l'admin Shopify : **Boutique en ligne → Thèmes → Ajouter un thème → Importer un fichier zip**.
3. Publier le thème (ou le tester en aperçu avant de publier).

Alternative recommandée pour un vrai suivi de version : utiliser le
[Shopify CLI](https://shopify.dev/docs/themes/tools/cli) (`shopify theme dev` / `shopify theme push`)
depuis ce dossier.

## À configurer dans l'admin Shopify après installation

Le thème est prêt à l'emploi, mais certains contenus vivent dans Shopify (pages, menus, produits) et
doivent être créés une fois par le marchand — c'est le fonctionnement normal d'un thème Shopify :

- **Pages** (Boutique en ligne → Pages) — créer ces 3 pages et leur assigner le modèle indiqué
  (menu déroulant "Modèle de page" dans l'éditeur de page) :
  - **Le Club** — handle `le-club`, modèle `page.club` → contient déjà tout le texte de l'histoire du club.
  - **Notre Mission** — handle `notre-mission`, modèle `page.mission` → contient déjà le texte de la mission.
  - **Contact** — handle `contact`, modèle `page.contact` → formulaire de contact Dawn déjà stylé.
- **Produits & collection** — ajouter les produits (t-shirts, casquettes, patchs). La page d'accueil et
  la page Boutique utilisent par défaut la collection automatique **"Toutes"** (`all`) ; vous pouvez
  créer une collection dédiée et la sélectionner dans l'éditeur de thème si besoin. Pour les filtres
  "T-shirts / Casquettes / Patchs" évoqués dans le mockup, utiliser le type de produit ou des tags, et
  activer les filtres de collection (déjà activés par défaut dans le modèle `collection.json`).
  - Le titre et la description de la collection "Toutes" (modifiables dans Admin → Collections) alimentent
    automatiquement le titre "Nos goodies officiels" et le chapô au-dessus de la grille produits.
- **Menus** (Boutique en ligne → Navigation) — créer :
  - `main-menu` (menu principal du header) avec les liens Le Club / Boutique / Notre Mission / Contact.
  - Un menu **"Le club"** et un menu **"Boutique"** pour les colonnes du pied de page (déjà référencés
    dans le pied de page ; si le nom exact ne correspond pas, il suffit de les re-sélectionner dans
    Personnaliser le thème → Pied de page).
- **Mentions légales** (Paramètres → Règlements) — renseigner CGV, mentions légales, politique de
  confidentialité et droit de rétractation : ils s'affichent automatiquement en bas du pied de page.
- **Logo** — un logo par défaut est intégré (`assets/logo-biker-tov.png`) pour le badge de la page
  d'accueil. Vous pouvez le remplacer par votre propre fichier dans la section "Bannière avec badge"
  de l'éditeur de thème (Personnaliser → Accueil).
- **Favicon** — à ajouter dans Personnaliser le thème → Paramètres du thème → Favicon.

## Personnalisations apportées par rapport à Dawn

- `layout/theme.liquid` — polices Google Fonts (Pirata One / Inter), chargement de `biker-tov-theme.css`.
- `assets/biker-tov-theme.css` — couche de style additionnelle (badge circulaire, panneau mission, etc.).
- `assets/logo-biker-tov.png` — logo par défaut.
- `config/settings_data.json` — palette de couleurs sombre (noir/os), coins carrés, bordures fines,
  panier en tiroir, police par défaut.
- `sections/hero-badge.liquid` — nouvelle section : bannière d'accueil avec logo en médaillon.
- `sections/mission-panel.liquid` — nouvelle section : panneau encadré "Chaque achat a un sens".
- `sections/header-group.json`, `sections/footer-group.json` — nav épurée, pied de page à 3 blocs.
- `templates/index.json` — page d'accueil recomposée avec les nouvelles sections.
- `templates/page.club.json`, `templates/page.mission.json` — modèles de page pré-remplis avec les
  textes fournis (`Le Club`, `Notre Mission`).
- `templates/collection.json` — grille boutique en 3 colonnes, images carrées.
- `locales/fr.default.json` — le français est la langue par défaut de la boutique (au lieu de l'anglais).

## Limite connue de cette livraison

Le rendu Liquid n'a pas pu être testé sur une vraie boutique Shopify depuis cet environnement
(ni Shopify CLI, ni Node.js disponibles ici). La structure et la syntaxe (JSON, balises Liquid) ont
été vérifiées, et le rendu visuel des nouvelles sections a été contrôlé séparément en HTML/CSS. Un
premier import + aperçu dans l'admin Shopify reste recommandé avant publication pour repérer
d'éventuels ajustements mineurs.
