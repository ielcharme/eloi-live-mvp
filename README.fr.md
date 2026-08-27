# Zerendo Live MVP

[English](README.md) | **Français**

Un Skill Codex open source pour construire une expérience de présentatrice IA réactive : saisie web ou microphone, réponses Zerendo en anglais ou en français, synthèse vocale bilingue, quatre états visuels et sortie transparente pour OBS.

Zerendo reste la couche de raisonnement IA. **Eloi** est la présentatrice visuelle par défaut et peut être remplacée par un autre pack de personnage autorisé.

## Important : la licence d'Eloi est payante

Le code et les instructions de ce dépôt sont sous licence MIT. **L'identité, l'apparence et les images d'Eloi ne sont pas couvertes par la licence MIT.**

Pour utiliser Eloi dans une vidéo, un direct, un site, une application, une publicité, un produit ou une chaîne sociale, vous devez obtenir avant utilisation :

- une autorisation écrite du détenteur des droits ; ou
- une licence Projet Unique de **9,99 USD**.

Contact : [zerencontact@sina.com](mailto:zerencontact@sina.com)

Objet recommandé : `Eloi License - [Nom du projet]`

Indiquez le projet, le produit, le site, l'application ou la chaîne qui utilisera Eloi. Le détenteur des droits vous enverra le lien de paiement officiel via l'intégration PayPal ZEREN. La licence devient valide uniquement après confirmation du paiement par PayPal.

Le clonage, le fork ou l'installation de ce dépôt ne constitue pas une autorisation d'utiliser Eloi. Consultez [LICENSE-ELOI-ASSETS.md](LICENSE-ELOI-ASSETS.md) pour les conditions complètes.

## Fonctionnement

```text
Texte web / microphone
-> réponse de Zerendo
-> voix féminine anglais/français
-> Eloi idle/thinking/tip/error
-> Browser Source OBS transparent
```

## Fonctionnalités du MVP

- saisie texte en anglais et en français ;
- entrée microphone après une action explicite de l'utilisateur ;
- adaptation à un endpoint Zerendo existant ;
- voix féminine adulte, chaleureuse et bilingue ;
- états visuels `idle`, `thinking`, `tip` et `error` ;
- fond alpha transparent pour OBS ;
- architecture par adaptateurs pour remplacer le STT, le TTS, le modèle ou la présentatrice.

## Installation

Copiez le dossier `zerendo-live-mvp` dans votre répertoire de Skills Codex, puis utilisez :

```text
$zerendo-live-mvp Build a transparent OBS-ready Zerendo experience with Eloi as the presenter.
```

Sans licence Eloi valide, utilisez des images neutres dont vous possédez les droits ou un autre pack de présentateur correctement licencié.

## Fichiers principaux

- `SKILL.md` : instructions principales du Skill ;
- `references/architecture.md` : architecture, événements et machine à états ;
- `references/character-contract.md` : identité, voix et comportement visuel d'Eloi ;
- `assets/zerendo-live.config.example.json` : configuration de départ ;
- `assets/eloi-*.png` : images propriétaires d'Eloi.

## Licences

- Code, instructions et configuration : [MIT](LICENSE)
- Identité et images d'Eloi : [licence propriétaire Eloi](LICENSE-ELOI-ASSETS.md)

Ce modèle de licence ne constitue pas un avis juridique.
