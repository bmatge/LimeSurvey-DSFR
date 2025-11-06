# Guide de démarrage rapide - Thème DSFR

Ce guide vous permet de démarrer rapidement le développement du thème DSFR pour LimeSurvey.

## 🚀 Démarrage en 3 étapes

### 1. Lancer Docker

```bash
docker-compose up -d
```

Cela démarre :
- MySQL (base de données)
- LimeSurvey (application web sur le port 8080)

### 2. Accéder à LimeSurvey

Ouvrez votre navigateur : http://localhost:8080

**Identifiants admin :**
- Utilisateur : `admin`
- Mot de passe : `admin`

### 3. Activer le thème DSFR

1. Connectez-vous à l'interface d'administration
2. Créez une nouvelle enquête (ou utilisez une existante)
3. Dans les paramètres de l'enquête, section **Présentation & navigation**
4. Sélectionnez le thème **DSFR**
5. Sauvegardez

## 🎨 Développement en temps réel

Les fichiers du thème sont **montés en volume** dans Docker. Cela signifie :

### ✅ Modifications instantanées

**Fichiers CSS/JS** → Rechargez simplement la page du navigateur
- `themes/survey/dsfr/css/theme.css`
- `themes/survey/dsfr/css/custom.css`
- `themes/survey/dsfr/scripts/theme.js`
- `themes/survey/dsfr/scripts/custom.js`

**Fichier config.xml** → Réinitialisez le thème dans l'admin
1. Configuration > Thèmes
2. Trouvez "DSFR"
3. Cliquez sur "Réinitialiser"

### 📂 Structure des fichiers

```
themes/survey/dsfr/
├── config.xml              ← Configuration du thème
├── css/
│   ├── theme.css          ← Styles DSFR principaux
│   └── custom.css         ← Vos styles perso
├── scripts/
│   ├── theme.js           ← JS DSFR
│   └── custom.js          ← Vos scripts perso
└── files/                  ← Ressources (logos, etc.)
```

## 🛠️ Commandes Docker

```bash
# Démarrer
docker-compose up -d

# Voir les logs en temps réel
docker-compose logs -f limesurvey

# Arrêter (garde les données)
docker-compose down

# Tout supprimer (⚠️ efface la base de données)
docker-compose down -v

# Redémarrer un service
docker-compose restart limesurvey
```

## 🔍 Tester le thème

### Créer une enquête de test

1. **Créer une enquête**
   - Allez dans "Créer une enquête"
   - Remplissez les informations de base
   - Sélectionnez le thème **DSFR**

2. **Ajouter des questions**
   - Créez un groupe de questions
   - Ajoutez différents types de questions :
     - Texte court
     - Texte long
     - Choix multiples
     - Liste déroulante
     - Etc.

3. **Activer l'enquête**
   - Activez l'enquête
   - Cliquez sur "Aperçu" pour voir le rendu avec le thème DSFR

### Tester différents types de questions

Le DSFR doit s'adapter à tous les types de questions LimeSurvey :
- Questions à choix unique/multiples
- Champs de texte
- Matrices
- Upload de fichiers
- Etc.

## 🎯 Workflow de développement recommandé

1. **Ouvrez deux fenêtres** :
   - Votre éditeur de code
   - Votre navigateur avec l'enquête de test

2. **Modifiez le CSS/JS** dans votre éditeur

3. **Rechargez la page** (Cmd+R / Ctrl+R)

4. **Inspectez avec les DevTools** (F12) pour ajuster

5. **Itérez** jusqu'à satisfaction !

## 🐛 Dépannage

### Le thème DSFR n'apparaît pas dans la liste

```bash
# Vérifier que Docker tourne
docker-compose ps

# Voir les logs
docker-compose logs limesurvey

# Redémarrer
docker-compose restart limesurvey
```

### Les modifications CSS ne s'appliquent pas

1. **Vider le cache du navigateur** : Cmd+Shift+R (Mac) ou Ctrl+Shift+R (Windows/Linux)
2. **Vérifier la console** : F12 → onglet "Console" pour voir les erreurs
3. **Vérifier le fichier** : Assurez-vous que votre fichier est bien sauvegardé

### Le conteneur ne démarre pas

```bash
# Voir les logs détaillés
docker-compose logs

# Vérifier que le port 8080 n'est pas utilisé
lsof -i :8080  # Mac/Linux
netstat -ano | findstr :8080  # Windows

# Supprimer tout et recommencer
docker-compose down -v
docker-compose up -d
```

## 📚 Ressources utiles

- [Documentation DSFR](https://www.systeme-de-design.gouv.fr/)
- [Composants DSFR](https://www.systeme-de-design.gouv.fr/composants)
- [Documentation LimeSurvey](https://manual.limesurvey.org/)
- [README du thème](themes/survey/dsfr/README.md)

## ✨ Prochaines étapes

1. **Personnaliser les couleurs** dans `css/custom.css`
2. **Ajouter le logo Marianne** dans `files/`
3. **Tester l'accessibilité** avec les outils RGAA
4. **Adapter les templates Twig** si nécessaire (dans `views/`)

---

**Bon développement ! 🚀**
