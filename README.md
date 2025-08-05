# 📚 Agent Personnel de Révision - Cahier des Charges

## 🎯 Objectif
Développer une application minimaliste et interactive servant d’assistant personnel pour organiser, suivre et améliorer les sessions de révision selon la méthode Pomodoro. L'agent vise à augmenter la productivité, à réduire les distractions et à générer des rapports statistiques détaillés.

---
## Visuels

Lien vers la dernier video de mise a jour: https://youtu.be/r4YPtQZm2AY
---

## 🖥️ Interface Générale

- **Démarrage automatique au lancement du système**
- **Interface initiale épurée, thème sombre**
  - Demande à l'utilisateur s'il souhaite réviser
    - Si **non** : l'agent se ferme
    - Si **oui** : l’interface complète s’ouvre

- **Interface compacte** (petit carré en haut à gauche de l’écran)
  - **Extension automatique** en quart d’écran lorsque le curseur passe dessus

---

## ⏱️ Fonctionnalités de Suivi

### Suivi du temps et de l'activité
- Traque du **temps total de révision**
- Suivi des **applications utilisées** :
  - Temps d’utilisation global
  - Temps en mode plein écran
- Export des données vers :
  - **Agenda personnel**
  - **Graphiques statistiques**
  - **Home Assistant** :
    - Envoi d'informations (état de session, début/fin de pause, chapitre terminé…)
    - Réception de commandes (changer de piste audio, valider une étape…)

### Méthode Pomodoro
- Possibilité de **configurer plusieurs modes Pomodoro** (ex: 25/5, 30/10, etc.)
- Prise en charge du **cycle Pomodoro complet** :
  - 3 sessions de travail + pause courte
  - 1 session de travail + pause longue
- Démarrage d’un Pomodoro lance une **piste audio** personnalisée
  - Gestion des pistes :
    - Ajouter / supprimer / modifier
    - Passer à la suivante facilement
  - Statistiques sur les pistes :
    - Durée moyenne d’écoute
    - Fréquences d’utilisation selon l’heure et le jour

---

## 📆 Planification et Organisation

### Agenda intégré
- Visualisation des **sessions de travail** et des **pauses**
- Possibilité d’**ajouter une activité planifiée** à chaque session de travail
- Construction d’un **planning personnalisé** selon les objectifs

---

## 🚫 Blocage de Distractions

- **Liste de programmes bannis** durant la révision
  - Édition via une interface intuitive
  - Empêche leur lancement durant la session

- **Liste de sites web interdits**
  - Blocage via une extension de navigateur personnalisée liée à l’agent
  - Liste éditable par l'utilisateur

---

## ✅ Marquage de Progression

- **Bouton “Leçon / Chapitre terminé”**
  - Permet d’enregistrer la progression
  - Intégration dans les graphiques et l’agenda pour analyses détaillées

---

## 📊 Statistiques et Visualisation

- **Page dédiée aux statistiques**
  - Graphiques dynamiques et interactifs
  - Nombreux filtres (période, durée, type de contenu, activité, etc.)
  - Corrélations entre activités (ex: temps de concentration vs. pistes audio vs. sites consultés)

- **Notifications intelligentes**
  - Affichage “Faire une pause” lorsque le timer de travail est écoulé
  - Timer de pause suivi d’un bouton “Remise au travail”

---

## 🔧 Fonctionnalités Secondaires

### Intégration avec Notion
- Connexion à un compte Notion personnel
  - Suivi en temps réel :
    - Pages ouvertes
    - Pages éditées
    - Pages supprimées
  - Affichage sous forme de graphiques

### Suivi du navigateur
- Historique des sites consultés
  - Classés par heure et durée
  - Visualisation graphique

### Chatbot intelligent (Ollama)
- Intégration d’un assistant conversationnel
  - Répond aux questions de l’utilisateur
  - Accès aux :
    - Statistiques de révision
    - Pages Notion connectées

---

## 🧩 Système de Plugins Communautaires

- Architecture prévue pour **étendre l’application** avec des modules externes
- Les plugins sont classés en **trois catégories distinctes** :

### 1. 🎨 Plugins de **Style**
- Modifient **l'apparence de l'application**
- Un **style par défaut** est fourni par le développeur
- Possibilité pour la communauté de créer des **thèmes visuels complets**
- Gestion intuitive via une interface dédiée

### 2. 🛠️ Plugins **Modifier**
- Permettent de **modifier des comportements natifs** de l’application
- Exemples : 
  - Personnalisation des appels à Home Assistant
  - Redéfinition des connexions avec Notion
  - Ajustements de règles Pomodoro ou de format de statistiques

### 3. ✨ Plugins **Features**
- Ajoutent des **fonctionnalités entièrement nouvelles**
- Peuvent inclure :
  - Un ou plusieurs modules fonctionnels
  - Nouveaux onglets ou ajout dans des onglets existants
- Chaque Feature utilise obligatoirement le **système de style natif** pour rester compatible avec les plugins de style

### 📦 Packs personnalisés
- Système de **packs partagés** :
  - Peuvent contenir un ensemble de plugins : Styles, Modifiers, Features
  - Inclus les **fichiers de configuration utilisateur**
  - Import/export simple pour **partager un setup complet**

---

## 🔒 Confidentialité
- Toutes les données personnelles sont stockées localement
- Aucun envoi externe sans autorisation explicite de l'utilisateur

---

## Technologies envisagées

| Technologie                            | Badge                                                                                                              | Utilité principale                                     |
| -------------------------------------- | ------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------ |
| **.NET 8 (C#)**                        | ![.NET](https://img.shields.io/badge/.NET-8.0-blueviolet?logo=dotnet)                                              | Base de l’application – logique, structure, timers     |
| **WPF**                                | ![WPF](https://img.shields.io/badge/WPF-Windows%20Desktop-lightblue?logo=windows)                                  | Interface utilisateur compacte, moderne, responsive    |
| **SQLite**                             | ![SQLite](https://img.shields.io/badge/SQLite-Local%20Database-003B57?logo=sqlite)                                 | Stockage local des stats, historiques, paramètres      |
| **Dapper**                             | ![Dapper](https://img.shields.io/badge/Dapper-Lightweight%20ORM-orange)                                            | Accès à la base SQLite simple et rapide                |
| **LiveCharts2**                        | ![LiveCharts](https://img.shields.io/badge/LiveCharts2-Graphiques%20dynamiques-ff69b4)                             | Affichage des statistiques interactives                |
| **NAudio**                             | ![NAudio](https://img.shields.io/badge/NAudio-Gestion%20audio-darkgreen)                                           | Lecture de pistes audio au début/fin de sessions       |
| **MQTTnet**                            | ![MQTTnet](https://img.shields.io/badge/MQTTnet-Home%20Assistant%20Bridge-brightgreen?logo=homeassistant)          | Communication bidirectionnelle avec Home Assistant     |
| **Newtonsoft.Json**                    | ![JSON.NET](https://img.shields.io/badge/JSON.NET-Parsing%20JSON-ffdd00?logo=json)                                 | Gestion des données JSON (API externes, plugins)       |
| **Flurl.Http**                         | ![Flurl](https://img.shields.io/badge/Flurl-HTTP%20Client-lightgray?logo=rest)                                     | Appels aux API (Notion, Ollama, plugins)               |
| **WebView2**                           | ![WebView2](https://img.shields.io/badge/WebView2-Affichage%20de%20contenu%20web-0078d7?logo=microsoftedge)        | Affichage intégré de contenus HTML (Notion, stats web) |
| **PowerShell**                         | ![PowerShell](https://img.shields.io/badge/PowerShell-Automation-blue?logo=powershell)                             | Scripts système (blocage app, démarrage auto)          |
| **CefSharp (optionnel)**               | ![CefSharp](https://img.shields.io/badge/CefSharp-Extension%20navigateur-red)                                      | Blocage ou suivi web si WebView2 insuffisant           |
| **MVVM Toolkit**                       | ![MVVM Toolkit](https://img.shields.io/badge/MVVM%20Toolkit-Pattern%20d'architecture-informational)                | Structure claire pour l’interface WPF                  |
| **SharpHook**                          | ![SharpHook](https://img.shields.io/badge/SharpHook-Hotkeys%20globales-blueviolet)                                 | Gestion des raccourcis clavier système                 |
| **MSIX / Inno Setup**                  | ![Installer](https://img.shields.io/badge/Setup-MSIX%20ou%20Inno%20Setup-blue?logo=windows)                        | Génération d’un installateur pour Windows              |
| **Ollama API**                         | ![Ollama](https://img.shields.io/badge/Ollama-Assistant%20IA%20local-black?logo=openai)                            | Assistant conversationnel local, sans cloud            |
| **Extension navigateur (Manifest V3)** | ![Chrome Extension](https://img.shields.io/badge/Chrome%20Extension-Blocage%20de%20sites-yellow?logo=googlechrome) | Blocage de sites distrayants pendant les sessions      |
| **Plugin Loader (Reflection)**         | ![Plugin System](https://img.shields.io/badge/Plugins-System%20modulaire-purple)                                   | Chargement dynamique de modules externes via DLL       |
---

## 🤝 Contributions

### 🔔 Appel à contributions
Vous souhaitez améliorer cet agent personnel de révision ? Vous êtes les bienvenus ! Toute contribution sérieuse et respectueuse des lignes directrices ci-dessous sera étudiée avec attention.

### 📌 Limites des contributions

- Les contributions **doivent s’appuyer sur le système natif** de l’application.
- Elles peuvent :
  - Améliorer une **fonctionnalité existante**.
  - Ajouter une **fonctionnalité explicitement listée dans le présent README**.
- **Les contributions ne doivent pas introduire de plugins** :  
  - Les plugins seront développés dans un **projet séparé** avec une structure propre (non encore mise en place à ce jour).
  - Toute fonctionnalité additionnelle non prévue ici devrait plutôt être proposée comme **plugin futur**.

### 📝 Requis pour toute contribution

- Fournir une **description claire et détaillée** :
  - Liste des ajouts et des modifications.
  - Description du **fonctionnement du code ajouté ou modifié**.
- Respecter la structure de l'application et le système de style natif.
- Garder une logique minimaliste et modulaire.

### 👥 Liste des contributeurs

La liste des contributeurs est générée automatiquement à partir des commits du dépôt principal. Merci à toutes les personnes qui participent à rendre ce projet plus utile, solide et inspirant.

[![Contributeurs](https://contrib.rocks/image?repo=TisaTHor08/Agent-Pomodoro)](https://github.com/TisaTHor08/Agent-Pomodoro/graphs/contributors)



---


## 🗂️ Résumé des Modules Clés

| Module                | Fonctionnalité principale                                 |
|----------------------|------------------------------------------------------------|
| Interface graphique   | Affichage compact et ergonomique, thème sombre             |
| Suivi de session      | Temps, applications, sites, pistes audio                   |
| Méthode Pomodoro      | Minuterie, rythme complet, musique, pauses intelligentes   |
| Blocage de distractions | Programmes et sites bannis pendant la session            |
| Planification         | Agenda des tâches, activités par session, planning         |
| Statistiques          | Graphiques détaillés, corrélations, filtres avancés        |
| Intégration Home Assistant | Échange bidirectionnel d’infos domotiques            |
| Intégration Notion    | Suivi des pages éditées en temps réel                      |
| Assistant (chatbot)   | Réponses personnalisées selon les données                  |
| Plugins               | Styles, Modificateurs, Nouvelles fonctionnalités, Packs    |

---

**Projet pensé pour booster la concentration, analyser les habitudes de travail et optimiser chaque session de révision.**
