# Eloi Live MVP

<p align="center">
  <img src="assets/eloi-turnaround.png" alt="Planche de référence de la présentatrice numérique Eloi" width="920">
</p>

<p align="center"><strong>Créez Eloi comme présentatrice numérique IA bilingue pour vos directs OBS.</strong></p>

<p align="center"><a href="README.md">English</a> · <strong>Français</strong></p>

> [!IMPORTANT]
> Ce dépôt contient un **Skill Codex**, et non une application de direct déjà terminée. Il fournit à Codex l'architecture, les règles du personnage, les ressources visuelles, la logique d'états et la liste de vérifications nécessaires pour construire ou adapter une expérience de direct avec Eloi.

> [!WARNING]
> Le logiciel est sous licence MIT, mais **l'identité et les images d'Eloi sont propriétaires**. Toute utilisation externe exige une autorisation écrite ou une **licence Projet Unique de 9,99 USD**. Consultez [la licence des images d'Eloi](#licence-des-images-deloi).

## En une phrase

L'opérateur ou le public écrit ou parle, une IA prépare une réponse en français ou en anglais, Eloi la prononce avec une voix féminine chaleureuse, son état visuel change automatiquement et OBS reçoit un calque transparent du personnage.

## Déroulement d'une interaction en direct

```text
Public ou opérateur
      │
      ├── écrit dans la page de contrôle
      └── parle dans le microphone
                    │
                    ▼
      Reconnaissance vocale, si nécessaire
                    │
                    ▼
              Endpoint IA configuré
         Réponse en français ou en anglais
                    │
          ┌─────────┴─────────┐
          ▼                   ▼
   État visuel d'Eloi     Voix féminine bilingue
 idle/thinking/tip/error          │
          └─────────┬────────────┘
                    ▼
          Browser Source OBS transparent
```

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

Les quatre fichiers PNG disposent d'une véritable transparence alpha et sont conçus pour un calque OBS ancré en bas de l'écran.

## Ce que le Skill aide Codex à construire

- une page web de contrôle pour les textes en français et en anglais ;
- un microphone activé uniquement après une action explicite ;
- une reconnaissance vocale facultative ;
- un adaptateur vers l'endpoint IA choisi ;
- une voix féminine adulte bilingue français/anglais ;
- des transitions déterministes entre `idle`, `thinking`, `tip` et `error` ;
- une route transparente séparée pour OBS Browser Source ;
- une récupération propre après les erreurs de microphone, de réseau, d'IA ou de synthèse vocale.

Le dépôt ne fournit pas de service IA hébergé, de crédits API, de compte de plateforme de streaming, de rig Live2D ni de modèle 3D terminé.

## Démarrage rapide

### 1. Installer le Skill

Copiez ce dossier dans votre répertoire de Skills Codex :

```text
~/.codex/skills/eloi-live-mvp
```

### 2. Demander à Codex de construire l'expérience

```text
$eloi-live-mvp Build an English/French Eloi digital presenter with text input,
microphone input, female bilingual TTS, automatic visual states, and a
transparent OBS overlay.
```

### 3. Connecter les services IA et vocaux

Partez de [la configuration d'exemple](assets/eloi-live.config.example.json) :

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

Codex doit adapter l'endpoint et les fournisseurs au projet cible sans exposer de clé API dans le navigateur.

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
| Instructions du Skill, configuration d'exemple et code logiciel original | [Licence MIT](LICENSE) |
| Identité, apparence, conception d'Eloi et fichiers `assets/eloi-*.png` | [Licence propriétaire Eloi](LICENSE-ELOI-ASSETS.md) |

Avant d'utiliser Eloi dans un direct, une vidéo, un site, une application, une publicité, un produit ou une chaîne sociale, obtenez :

1. une autorisation écrite du détenteur des droits ; ou
2. une **licence Projet Unique de 9,99 USD**.

**Contact licence :** [zerencontact@sina.com](mailto:zerencontact@sina.com)<br>
**Objet conseillé :** `Eloi License - [Nom du projet]`

Décrivez le projet, le produit, le site, l'application ou la chaîne qui utilisera Eloi. Le détenteur des droits vous enverra le lien de paiement PayPal officiel. La licence devient active uniquement après confirmation du paiement par PayPal.

Le clonage, le téléchargement, le fork ou l'installation de ce dépôt ne donne **aucun droit** de publier ou d'exploiter commercialement Eloi.

## Organisation du dépôt

```text
eloi-live-mvp/
├── SKILL.md                              Workflow Codex et règles de sécurité
├── README.md                            Documentation anglaise
├── README.fr.md                         Documentation française
├── LICENSE                              Licence logicielle MIT
├── LICENSE-ELOI-ASSETS.md               Licence des images d'Eloi
├── agents/openai.yaml                   Métadonnées du Skill
├── assets/
│   ├── eloi-turnaround.png              Référence visuelle principale
│   ├── eloi-idle.png                    État d'écoute normal
│   ├── eloi-thinking.png                État de traitement IA
│   ├── eloi-tip.png                     État de conseil
│   ├── eloi-error.png                   État d'erreur récupérable
│   └── eloi-live.config.example.json    Configuration de départ
└── references/
    ├── architecture.md                  Architecture du direct et d'OBS
    └── character-contract.md            Règles d'identité et de voix d'Eloi
```

## Références du personnage et de l'implémentation

- [Contrat d'identité et de voix d'Eloi](references/character-contract.md)
- [Architecture du direct et machine à états](references/architecture.md)
- [Licence complète des ressources Eloi](LICENSE-ELOI-ASSETS.md)

Ce modèle de licence ne constitue pas un avis juridique.
