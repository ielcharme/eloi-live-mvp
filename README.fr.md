# Eloi Live MVP

[English](README.md) | **Français**

Un Skill Codex open source pour utiliser **Eloi comme présentatrice numérique IA en direct**. Le public ou l'opérateur peut interagir par texte ou microphone ; Eloi répond en français ou en anglais, parle avec une voix féminine chaleureuse, change automatiquement d'état visuel et apparaît sur un calque transparent dans OBS.

## Fonctionnement

```text
Texte web / microphone
-> réponse IA en français ou en anglais
-> voix féminine bilingue d'Eloi
-> idle / thinking / tip / error
-> Browser Source OBS transparent
```

## Important : l'utilisation d'Eloi est payante

Le logiciel et les instructions du Skill sont sous licence MIT. **L'identité, l'apparence, la conception du personnage et les images d'Eloi sont propriétaires et ne sont pas couvertes par la licence MIT.**

Avant d'utiliser Eloi dans un direct, une vidéo, un site, une application, une publicité, un produit ou une chaîne sociale, vous devez obtenir :

- une autorisation écrite du détenteur des droits ; ou
- une **licence Projet Unique de 9,99 USD**.

Contact : [zerencontact@sina.com](mailto:zerencontact@sina.com)

Objet conseillé : `Eloi License - [Nom du projet]`

Décrivez le projet ou la chaîne qui utilisera Eloi. Le détenteur des droits vous enverra le lien de paiement PayPal officiel. La licence devient valide uniquement après confirmation du paiement par PayPal.

Le clonage, le fork ou l'installation de ce dépôt ne donne pas le droit d'utiliser Eloi. Consultez [LICENSE-ELOI-ASSETS.md](LICENSE-ELOI-ASSETS.md) pour les conditions complètes.

## Fonctionnalités du MVP

- interaction texte en français et en anglais ;
- microphone activé après une action explicite de l'utilisateur ;
- connexion à un endpoint IA configurable ;
- voix féminine adulte, chaleureuse et bilingue ;
- états automatiques `idle`, `thinking`, `tip` et `error` ;
- calque OBS transparent pour les directs horizontaux ou verticaux ;
- adaptateurs STT, IA et TTS remplaçables.

## Installation

Copiez `eloi-live-mvp` dans votre répertoire de Skills Codex, puis utilisez :

```text
$eloi-live-mvp Build an English/French Eloi digital presenter for a transparent OBS livestream.
```

Sans licence Eloi valide, utilisez des images neutres dont vous possédez les droits pendant la construction de la partie technique.

## Fichiers principaux

- `SKILL.md` : instructions de réalisation du direct Eloi ;
- `references/architecture.md` : adaptateurs, événements, machine à états et contrat OBS ;
- `references/character-contract.md` : identité, voix et comportement visuel d'Eloi ;
- `assets/eloi-live.config.example.json` : configuration de départ ;
- `assets/eloi-*.png` : ressources visuelles propriétaires d'Eloi.

## Licences

- Logiciel, instructions et configuration : [MIT](LICENSE)
- Identité et ressources visuelles d'Eloi : [licence propriétaire Eloi](LICENSE-ELOI-ASSETS.md)

Ce modèle de licence ne constitue pas un avis juridique.
