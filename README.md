# 📊 Instagram Rétrospective - Analyse de vos données

Analysez vos conversations Instagram et créez de magnifiques graphiques pour votre rétrospective annuelle !

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)
![License](https://img.shields.io/badge/License-MIT-green.svg)

## ✨ Fonctionnalités

### 📈 Analyses disponibles
- **Messages** : Top conversations, répartition envoyés/reçus, activité horaire et par jour
- **Évolution temporelle** : Graphiques mensuels du top 5 de vos conversations
- **Réactions** : Emojis les plus utilisés, top reacteurs
- **Médias** : Audio, photos, vidéos, GIFs, reels (avec durées estimées)
- **Interactions** : Likes (posts, commentaires, stories), commentaires publiés
- **Contenus sauvegardés** : Posts, collections, lieux, musiques
- **Stories** : Stories publiées, évolution mensuelle
- **Période personnalisable** : Analysez n'importe quelle période (année, mois, custom)

### 🎨 Graphiques professionnels
- Design moderne style Instagram
- Support complet des emojis
- Export HD (150 DPI)
- Graphiques clairs et lisibles

## 🚀 Installation rapide

### Prérequis
- Python 3.8 ou supérieur
- Jupyter Notebook

### Installation des dépendances

```bash
pip install jupyter matplotlib seaborn numpy
```

Ou avec le fichier requirements.txt :

```bash
pip install -r requirements.txt
```

## 📋 Guide d'utilisation

### Étape 1 : Télécharger vos données Instagram

1. Ouvrez Instagram (web ou mobile)
2. Allez dans **Paramètres** → **Sécurité** → **Télécharger les données**
3. Sélectionnez **Format JSON** (important !)
4. Demandez le téléchargement
5. Attendez l'email de confirmation (peut prendre 24-48h)
6. Téléchargez et **extrayez le fichier ZIP**

### Étape 2 : Préparer les fichiers

```
📁 Votre dossier de travail/
├── instagram_analysis_clean.ipynb   ← Le notebook principal
├── requirements.txt                 ← Dépendances Python
├── connections/                     ← Données de connexions (extrait Instagram)
│   ├── contacts/
│   └── followers_and_following/
├── media/                           ← Médias publiés (extrait Instagram)
│   ├── archived_posts/              ← Posts archivés (organisés par date YYYYMM)
│   ├── posts/                       ← Vos posts (par mois: 202401, 202402, etc.)
│   ├── reels/                       ← Vos reels (par mois: 202401, 202402, etc.)
│   ├── stories/                     ← Vos stories (par mois: 202401, 202402, etc.)
│   ├── profile/                     ← Photos de profil
│   ├── recently_deleted/            ← Contenus supprimés récemment
│   └── other/                       ← Autres médias
└── your_instagram_activity/         ← Activités Instagram (extrait Instagram)
    ├── messages/
    │   ├── inbox/                   ← Vos conversations
    │   ├── broadcast/               ← Chaînes de diffusion
    │   └── message_requests/        ← Demandes de messages
    ├── likes/                       ← Vos likes
    │   ├── liked_posts.json
    │   └── liked_comments.json
    ├── comments/                    ← Vos commentaires
    │   ├── post_comments_1.json
    │   ├── reels_comments.json
    │   └── hype.json
    ├── saved/                       ← Contenus sauvegardés
    │   ├── saved_posts.json
    │   ├── saved_collections.json
    │   ├── saved_locations.json
    │   └── saved_music.json
    ├── media/
    │   └── stories.json             ← Métadonnées de vos stories
    └── story_interactions/
        └── story_likes.json         ← Likes sur stories
```

> **Note sur l'organisation des médias** : Les dossiers `posts/`, `reels/`, `stories/` dans `media/` contiennent des sous-dossiers organisés par date au format **YYYYMM** (ex: `202401` pour janvier 2024, `202512` pour décembre 2025). Instagram organise automatiquement vos médias par mois lors de l'export.

### Étape 3 : Configurer l'analyse

Ouvrez le notebook et **modifiez la première cellule** :

```python
# Votre prénom (tel qu'il apparaît dans les messages)
YOUR_NAME_PATTERN = "Maxim"  # ← CHANGEZ ICI

# Choisissez votre période d'analyse
YEAR_FILTER = 2025  # Analyser toute l'année 2025
```

### Étape 4 : Exécuter l'analyse

1. Lancez Jupyter Notebook :
```bash
jupyter notebook
```

2. Ouvrez `instagram_analysis_clean.ipynb`

3. Exécutez toutes les cellules dans l'ordre : **Cell** → **Run All**

4. Patientez (peut prendre 1-2 minutes selon le nombre de conversations)

5. Vos graphiques sont générés ! 🎉

## 📈 Statistiques détaillées disponibles

Le notebook génère des statistiques complètes sur :

### 💬 Messages
- Total messages envoyés/reçus
- Moyenne de caractères par message
- Distribution horaire (pic d'activité)
- Distribution par jour de la semaine
- Évolution mensuelle
- Top 10 conversations

### ❤️ Réactions
- Réactions données/reçues
- Top 10 emojis utilisés
- Top reacteurs (qui réagit le plus)

### 🎙️ Médias
- **Audio** : nombre, durée totale, durée moyenne
- **Photos** : nombre total, répartition envoyées/reçues
- **Vidéos** : nombre, durée totale, durée moyenne
- **GIFs** : nombre total
- **Partages** : posts/reels/stories partagés

### 👍 Interactions
- **Likes** : posts (X), commentaires (Y), stories (Z)
- **Commentaires** : stories, posts, reels
- Top 5 comptes les plus likés
- Top 5 comptes les plus commentés

### 💾 Contenus Sauvegardés
- Posts sauvegardés
- Collections créées
- Lieux enregistrés
- Musiques sauvegardées

### 📱 Stories
- Nombre de stories publiées
- Évolution mensuelle

## ⚙️ Configuration avancée

### Analyser une période spécifique

Dans la cellule de configuration, décommentez et modifiez :

```python
# Analyser du 1er janvier au 30 juin 2025
START_DATE = datetime(2025, 1, 1)
END_DATE = datetime(2025, 6, 30)
YEAR_FILTER = None  # Important : mettre à None
```

### Analyser les 6 derniers mois

```python
from datetime import timedelta
END_DATE = datetime.now()
START_DATE = END_DATE - timedelta(days=180)
YEAR_FILTER = None
```

## 📊 Graphiques générés

Après l'exécution du notebook, **tous les graphiques sont sauvegardés automatiquement** à la racine du projet en haute qualité (150 DPI).

| Fichier | Contenu | Section |
|---------|---------|---------|
| `top5_evolution_mensuelle.png` | Évolution mois par mois de vos 5 conversations principales | Messages |
| `messages_stats.png` | Top 10 conversations, répartition, activité horaire et par jour | Messages |
| `reactions_stats.png` | Répartition réactions et top emojis donnés/reçus | Réactions |
| `medias_overview.png` | Répartition médias (audio/photos/vidéos/GIFs) et distributions horaires | Médias |
| `medias_top_conversations.png` | Top 8 conversations pour chaque type de média | Médias |
| `medias_evolution_mensuelle.png` | Évolution mensuelle des médias (audio, photos, vidéos) | Médias |
| `interactions_overview.png` | Répartition des likes et commentaires avec distributions horaires | Interactions |
| `interactions_evolution.png` | Évolution mensuelle des interactions (likes, commentaires, sauvegardes) | Interactions |
| `saved_content.png` | Répartition des contenus sauvegardés (posts, collections, lieux, musiques) | Sauvegardés |
| `stories_posted.png` | Stories publiées par mois | Stories |

## 🎯 Exemples de visualisations

### 💬 Messages
- **Top 10 conversations** avec nombre de messages
- **Pie chart** envoyés vs reçus
- **Courbe d'activité** par heure (avec pic marqué)
- **Bar chart** par jour de la semaine
- **Évolution mensuelle** du top 5

### ❤️ Réactions
- **Top emojis** donnés et reçus (avec vrais emojis !)
- **Pie chart** répartition réactions
- **Top reacteurs** (qui réagit le plus à vos messages)

### 🎙️ Médias
- **Vue d'ensemble** : répartition audio/photos/vidéos/GIFs
- **Comparaison** envoyés vs reçus pour chaque type
- **Top 8 conversations** par type de média
- **Distributions horaires** : quand vous envoyez le plus d'audios, photos, etc.
- **Évolution mensuelle** : courbes comparatives des différents médias
- **Durées estimées** pour audio et vidéos

### 👍 Interactions
- **Likes** : posts, commentaires, stories
- **Commentaires** : stories, posts, reels
- **Top comptes** : les plus likés et commentés
- **Distributions horaires** : vos heures d'activité
- **Évolution mensuelle** : likes, commentaires, sauvegardes

### 💾 Contenus Sauvegardés
- **Répartition** : posts, collections, lieux, musiques
- **Évolution temporelle** de vos sauvegardes

### 📱 Stories
- **Stories publiées** par mois
- **Volume total** sur la période

## 🛠️ Dépannage

### "Aucun message trouvé"
✅ Vérifiez que le dossier `your_instagram_activity` est bien placé au même niveau que le notebook

✅ Vérifiez que `YOUR_NAME_PATTERN` correspond à votre nom dans les messages

✅ Vérifiez la période sélectionnée (peut-être qu'il n'y a pas de messages pour cette période)

### "Emojis ne s'affichent pas"
✅ Sur Windows, installez une police supportant les emojis (Segoe UI Emoji)

✅ Les emojis s'affichent correctement dans les fichiers PNG générés

### "Erreur d'encodage"
✅ Ne modifiez pas les fichiers JSON téléchargés d'Instagram

✅ Utilisez bien le format **JSON** lors du téléchargement (pas HTML)

### "Le notebook est trop lent"
✅ Normal si vous avez beaucoup de conversations (>100)

✅ L'analyse complète peut prendre 2-5 minutes

✅ Les fichiers audio/vidéo doivent être présents pour les estimations de durée

### "Certains graphiques sont vides"
✅ C'est normal si vous n'avez pas ce type de données (ex: pas de GIFs, pas de commentaires)

✅ Le notebook gère automatiquement les données manquantes

✅ Vérifiez que tous les dossiers (likes, comments, saved, etc.) sont bien présents

### "FileNotFoundError"
✅ Assurez-vous que tous les fichiers médias référencés dans les JSON sont présents

✅ Si vous avez déplacé/supprimé des fichiers médias, les durées ne pourront pas être calculées (mais l'analyse continue)

## 📁 Structure du projet

```
instagram-retrospective-analyse-personnalisee/
├── README.md                          ← Ce fichier
├── instagram_analysis_clean.ipynb     ← Notebook principal d'analyse
├── Requirements.txt                   ← Dépendances Python
├── .gitignore                         ← Fichiers à ignorer (données personnelles)
├── connections/                       ← Données de connexions Instagram (gitignored)
├── media/                             ← Vos médias publiés (gitignored)
└── your_instagram_activity/           ← Vos données d'activité (gitignored)
```

> **Note** : Les dossiers contenant vos données personnelles (`connections/`, `media/`, `your_instagram_activity/`) ne sont pas versionés dans Git pour protéger votre vie privée. Après avoir exécuté le notebook, les graphiques générés seront sauvegardés à la racine du projet.

## 🔒 Confidentialité et sécurité

- ✅ **100% local** : Toutes les analyses se font sur votre ordinateur
- ✅ **Aucun upload** : Vos données ne quittent jamais votre machine
- ✅ **Open source** : Code entièrement visible et modifiable
- ✅ **Pas de tracking** : Aucune télémétrie ou statistique collectée

⚠️ **Important** : Ne partagez jamais vos fichiers JSON Instagram en ligne, ils contiennent toutes vos conversations !

## 🤝 Contribution

Les contributions sont les bienvenues ! N'hésitez pas à :
- 🐛 Signaler des bugs
- 💡 Proposer de nouvelles fonctionnalités
- 📖 Améliorer la documentation
- 🎨 Ajouter de nouveaux graphiques

## 📝 TODO / Idées futures

- [x] Analyse des médias (audio, photos, vidéos, GIFs)
- [x] Analyse des interactions (likes, commentaires)
- [x] Contenus sauvegardés (posts, collections, lieux, musiques)
- [x] Stories publiées
- [x] Période personnalisable
- [ ] Export PDF multi-pages avec tous les graphiques
- [ ] Graphiques interactifs (Plotly)
- [ ] Analyse de sentiments des messages
- [ ] Wordcloud des mots les plus utilisés
- [ ] Heatmap jour/heure d'activité complète
- [ ] Temps de réponse moyen dans les conversations
- [ ] Interface web (Flask/Streamlit)
- [ ] Comparaison année N vs année N-1
- [ ] Analyse des hashtags utilisés
- [ ] Détection des conversations les plus actives par période
- [ ] Export des statistiques en JSON/CSV

## 📜 Licence

MIT License - Vous êtes libre d'utiliser, modifier et distribuer ce projet.

## 🙏 Remerciements

- Instagram pour l'export de données
- Matplotlib & Seaborn pour les graphiques
- La communauté Python

## 📞 Support

Des questions ? Des problèmes ?
- Ouvrez une issue sur GitHub
- Consultez le [Guide de dépannage](#-dépannage)

---

Made with ❤️ for Instagram analytics

**Note** : Ce projet n'est pas affilié à Meta/Instagram. Il s'agit d'un outil d'analyse personnel pour vos propres données.