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
- **Médias** : Audio, photos, vidéos (avec durées estimées)
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
├── instagram_analysis_period.ipynb  ← Le notebook
├── requirements.txt
└── your_instagram_activity/         ← Dossier extrait d'Instagram
    └── messages/
        └── inbox/                   ← Vos conversations
            ├── conversation1/
            │   └── message_1.json
            ├── conversation2/
            │   └── message_1.json
            └── ...
```

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

2. Ouvrez `instagram_analysis_period.ipynb`

3. Exécutez toutes les cellules dans l'ordre : **Cell** → **Run All**

4. Patientez (peut prendre 1-2 minutes selon le nombre de conversations)

5. Vos graphiques sont générés ! 🎉

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

| Fichier | Contenu |
|---------|---------|
| `top5_evolution_mensuelle.png` | Évolution mois par mois de vos 5 conversations principales |
| `messages_stats.png` | Top 10, répartition, activité horaire et par jour |
| `reactions_stats.png` | Répartition réactions et top emojis |

## 🎯 Exemples de visualisations

### Messages
- **Top 10 conversations** avec nombre de messages
- **Pie chart** envoyés vs reçus
- **Courbe d'activité** par heure (avec pic marqué)
- **Bar chart** par jour de la semaine

### Évolution
- **Graphique multi-lignes** montrant l'évolution de vos 5 principales conversations
- **Annotations automatiques** sur les pics d'activité

### Réactions
- **Top emojis** donnés et reçus (avec vrais emojis !)
- **Pie chart** répartition réactions

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

## 📁 Structure du projet

```
instagram-retrospective/
├── README.md                          ← Ce fichier
├── instagram_analysis_period.ipynb    ← Notebook principal
├── requirements.txt                   ← Dépendances Python
├── .gitignore                         ← Fichiers à ignorer
└── examples/                          ← Exemples de graphiques
    ├── top5_evolution_mensuelle.png
    ├── messages_stats.png
    └── reactions_stats.png
```

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

- [ ] Export PDF multi-pages avec tous les graphiques
- [ ] Graphiques interactifs (Plotly)
- [ ] Analyse de sentiments des messages
- [ ] Wordcloud des mots les plus utilisés
- [ ] Heatmap jour/heure d'activité
- [ ] Temps de réponse moyen
- [ ] Interface web (Flask/Streamlit)
- [ ] Support des stories Instagram
- [ ] Comparaison année N vs année N-1

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
