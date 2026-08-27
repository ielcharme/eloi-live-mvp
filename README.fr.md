# Eloi Live MVP

> [!CAUTION]
> **LICENCE D'IMAGE ELOI PAYANTE OBLIGATOIRE.** Sans autorisation écrite du détenteur des droits, l'utilisation de l'identité, de l'apparence ou des images d'Eloi exige une **licence Projet Unique de 9,99 USD**. Toute copie, publication, exploitation commerciale, utilisation pour entraîner un modèle, revente ou autre usage non autorisé peut entraîner des demandes de retrait, des demandes de dommages-intérêts et des poursuites judiciaires. Contactez [zerencontact@sina.com](mailto:zerencontact@sina.com) pour recevoir le lien de paiement PayPal officiel.

<p align="center">
  <img src="assets/eloi-live-overview.png" alt="Présentation d'Eloi Live, présentatrice numérique IA bilingue" width="960">
</p>

<p align="center">
  <strong>Une présentatrice numérique IA bilingue pour le live commerce, les vidéos de vente, les fictions IA et bien plus.</strong>
</p>

<p align="center">
  <a href="assets/eloi-live-overview.pptx"><strong>Télécharger la présentation PowerPoint modifiable d'une page</strong></a>
  ·
  <a href="README.md">English</a>
  ·
  <strong>Français</strong>
</p>

> [!NOTE]
> Ce dépôt est un kit d'implémentation, et non une application de direct hébergée. Il fournit l'architecture, les règles du personnage, les ressources d'état, une configuration d'exemple et la liste de vérifications nécessaires pour intégrer Eloi dans un workflow web, vidéo ou OBS.

## Fonctionnement d'Eloi Live

L'opérateur ou le public écrit ou parle, une IA prépare une réponse en français ou en anglais, Eloi la prononce avec une voix féminine chaleureuse, son état visuel change automatiquement et OBS reçoit un calque transparent de la présentatrice.

```text
Texte ou microphone
        │
        ▼
Reconnaissance vocale, si nécessaire
        │
        ▼
Endpoint IA configuré
Réponse en français ou en anglais
        │
   ┌────┴────┐
   ▼         ▼
État visuel  Voix bilingue
   └────┬────┘
        ▼
Browser Source OBS transparent
```

## Cas d'usage

| Scénario | Utilisation possible d'Eloi |
| --- | --- |
| **Plateaux de direct** | Présentatrice virtuelle, co-animatrice, réponse au chat, guide produit ou présentation multilingue. |
| **Vidéos de vente** | Démonstrations produit, explication des fonctionnalités, offres, appels à l'action et clips commerciaux réutilisables. |
| **Fictions IA et contenus en série** | Personnage récurrent, fiction interactive, scènes scénarisées, récits éducatifs ou séries courtes. |
| **Vidéos sociales multilingues** | Versions françaises et anglaises de Reels, Shorts, TikTok et actualités communautaires. |
| **Présentation de marque et de produit** | Introduction produit, démonstration des fonctions, annonce de lancement et contenu de campagne. |
| **Tutoriels et onboarding** | Guides pas à pas, cours, prise en main d'un logiciel et vidéos FAQ. |
| **Événements virtuels et webinaires** | Animation, introduction des sessions, présentation de l'agenda, transitions et récapitulatifs. |
| **Contenus client et communauté** | Vidéos d'aide, messages de bienvenue, consignes de modération et actualités de service. |

## Les quatre états d'Eloi

<table>
  <tr>
    <th width="25%">Idle</th>
    <th width="25%">Thinking</th>
    <th width="25%">Tip</th>
    <th width="25%">Error</th>
  </tr>
  <tr>
    <td><img src="assets/eloi-idle.png" alt="État idle d'Eloi" width="210"></td>
    <td><img src="assets/eloi-thinking.png" alt="État thinking d'Eloi" width="210"></td>
    <td><img src="assets/eloi-tip.png" alt="État tip d'Eloi" width="210"></td>
    <td><img src="assets/eloi-error.png" alt="État error d'Eloi" width="210"></td>
  </tr>
  <tr>
    <td>Eloi écoute, attend ou vient de terminer sa réponse.</td>
    <td>L'IA prépare une réponse.</td>
    <td>Eloi donne un conseil ou une conclusion utile.</td>
    <td>Un problème récupérable est survenu.</td>
  </tr>
</table>

Les quatre fichiers PNG utilisent une transparence alpha et sont conçus pour un calque OBS ancré en bas de l'écran.

## Périmètre d'implémentation inclus

- saisie de texte en français et en anglais ;
- microphone activé uniquement après une action explicite ;
- reconnaissance vocale facultative ;
- adaptateur vers l'endpoint IA choisi ;
- voix féminine adulte bilingue français/anglais ;
- transitions déterministes entre `idle`, `thinking`, `tip` et `error` ;
- route transparente séparée pour OBS Browser Source ;
- récupération propre après les erreurs de microphone, de réseau, d'IA ou de synthèse vocale.

Le kit ne fournit pas de service IA hébergé, de crédits API, de compte de plateforme de streaming, de rig Live2D ni de modèle 3D terminé.

## Démarrage rapide

### 1. Obtenir l'autorisation d'image

Avant toute publication d'Eloi, demandez une autorisation écrite ou achetez la **licence Projet Unique de 9,99 USD** via le lien PayPal officiel fourni par le détenteur des droits.

### 2. Suivre le guide d'implémentation

Utilisez [SKILL.md](SKILL.md) comme spécification de construction. Copiez les ressources d'état et [la configuration d'exemple](assets/eloi-live.config.example.json) dans le projet cible.

### 3. Connecter les services IA et vocaux

```json
{
  "assistant": {
    "endpoint": "/api/assistant/reply",
    "replyLanguages": ["en", "fr"]
  },
  "speech": {
    "preferredVoiceGender": "female",
    "preferredVoiceMode": "single-multilingual-voice"
  },
  "overlay": {
    "transparent": true
  }
}
```

Conservez les identifiants des fournisseurs sur le serveur. N'exposez aucune clé API dans le code du navigateur.

### 4. Ajouter le calque dans OBS

Utilisez l'URL générée comme **OBS Browser Source**.

- Format horizontal conseillé : `1920 × 1080`
- Format vertical conseillé : `1080 × 1920`
- Arrière-plan : transparent
- Position d'Eloi : centrée en bas

## Licence des images d'Eloi

Le dépôt utilise deux licences distinctes :

| Contenu | Licence |
| --- | --- |
| Instructions d'implémentation, configuration d'exemple et code logiciel original | [Licence MIT](LICENSE) |
| Identité, apparence, conception d'Eloi et fichiers `assets/eloi-*.png` | [Licence propriétaire Eloi](LICENSE-ELOI-ASSETS.md) |

Avant d'utiliser Eloi dans un direct, une vidéo, un site, une application, une publicité, un produit, une chaîne sociale, un jeu de données ou un entraînement de modèle, obtenez :

1. une autorisation écrite du détenteur des droits ; ou
2. une **licence Projet Unique de 9,99 USD**.

**Contact licence :** [zerencontact@sina.com](mailto:zerencontact@sina.com)<br>
**Objet conseillé :** `Eloi License - [Nom du projet]`

Décrivez le projet, le produit, le site, l'application ou la chaîne qui utilisera Eloi. Le détenteur des droits vous enverra le lien de paiement PayPal officiel. La licence devient active uniquement après confirmation du paiement par PayPal.

Le clonage, le téléchargement, le fork ou l'installation de ce dépôt ne donne **aucun droit** de publier, commercialiser, utiliser pour l'entraînement, revendre, sous-licencier ou créer des ressources dérivées à partir d'Eloi. Le détenteur des droits se réserve tous les recours disponibles contre toute utilisation non autorisée.

## Organisation du dépôt

```text
eloi-live-mvp/
├── SKILL.md                              Workflow d'implémentation et garde-fous
├── README.md                            Documentation anglaise
├── README.fr.md                         Documentation française
├── LICENSE                              Licence logicielle MIT
├── LICENSE-ELOI-ASSETS.md               Licence des images d'Eloi
├── agents/openai.yaml                   Métadonnées d'affichage du kit
├── assets/
│   ├── eloi-live-overview.pptx          Présentation modifiable d'une page
│   ├── eloi-live-overview.png           Aperçu rendu pour ce README
│   ├── eloi-idle.png                    État d'écoute normal
│   ├── eloi-thinking.png                État de traitement IA
│   ├── eloi-tip.png                     État de conseil
│   ├── eloi-error.png                   État d'erreur récupérable
│   └── eloi-live.config.example.json    Configuration de départ
└── references/
    ├── architecture.md                  Architecture du direct et d'OBS
    └── character-contract.md            Règles d'identité et de voix d'Eloi
```

## Références

- [Contrat d'identité et de voix d'Eloi](references/character-contract.md)
- [Architecture du direct et machine à états](references/architecture.md)
- [Licence complète des ressources Eloi](LICENSE-ELOI-ASSETS.md)

Ce modèle de licence ne constitue pas un avis juridique.
