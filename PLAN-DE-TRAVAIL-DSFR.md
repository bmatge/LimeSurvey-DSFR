# Plan de Travail Complet - Thème DSFR pour LimeSurvey

## 📋 Résumé Exécutif

### Bonne nouvelle : On contrôle le HTML !
LimeSurvey utilise **Twig** partout, ce qui signifie qu'on peut **réécrire complètement le HTML** pour être 100% conforme DSFR.

### Scope du projet
- **~170 fichiers** à créer/adapter (minimum viable)
- **~250 fichiers** pour un projet complet
- **32 types de questions** différents
- **Durée estimée** : 6-8 semaines (1 développeur temps plein)

---

## 🎯 Stratégie Recommandée

### Option A : Approche Progressive (RECOMMANDÉ)
Créer un thème DSFR fonctionnel par itérations :
1. **MVP** : Layout + 5 types de questions les plus utilisés (2 semaines)
2. **V1** : Tous les types de questions courants (4 semaines)
3. **V2** : Types de questions avancés + print (2 semaines)

### Option B : Approche Hybride (PRAGMATIQUE)
- Créer de **nouveaux templates Twig** pour les composants critiques (header, footer, navigation)
- **Garder les templates vanilla** pour les types de questions moins utilisés
- **Override CSS** pour uniformiser le style

### Option C : Approche Complète (IDÉAL)
Tout réécrire from scratch avec DSFR natif (8 semaines)

---

## 📊 Analyse de l'Ampleur

### Structure LimeSurvey

```
LimeSurvey Theme System
│
├── Survey Themes (themes/survey/*)
│   ├── Layout files (8 fichiers)
│   ├── CSS (3-5 fichiers)
│   ├── JavaScript (2 fichiers)
│   └── Subviews (70+ fichiers Twig)
│       ├── Header/Navigation (25 fichiers)
│       ├── Content pages (17 fichiers)
│       ├── Messages (10 fichiers)
│       └── Question wrappers (20 fichiers)
│
└── Question Themes (application/views/survey/questions/answer/*)
    ├── 32 types de questions
    ├── ~3-5 fichiers par type
    └── ~100-150 fichiers Twig total
```

### 32 Types de Questions Identifiés

#### Catégorie 1 : Questions Texte (5 types) ⭐ PRIORITÉ
1. **ShortFreeText** - Champ texte court
2. **LongFreeText** - Zone de texte (textarea)
3. **HugeFreeText** - Grande zone de texte
4. **MultipleShortText** - Plusieurs champs texte
5. **Numerical** - Nombre

#### Catégorie 2 : Choix Simple (7 types) ⭐ PRIORITÉ
6. **ListRadio** - Liste de boutons radio
7. **ListDropdown** - Liste déroulante
8. **ListWithComment** - Liste avec commentaire
9. **YesNoRadio** - Oui/Non
10. **GenderDropdown** - Homme/Femme/Autre
11. **5PointChoice** - Échelle 1-5

#### Catégorie 3 : Choix Multiple (2 types) ⭐ PRIORITÉ
12. **MultipleChoice** - Cases à cocher
13. **MultipleChoiceWithComments** - Cases à cocher avec commentaires

#### Catégorie 4 : Questions Array (10 types) ⭐⭐ MOYEN
14. **ArrayFlexibleRow** - Tableau flexible (le plus utilisé)
15. **Array5ChoiceQuestions** - Tableau 5 points
16. **Array10ChoiceQuestions** - Tableau 10 points
17. **ArrayYesUncertainNo** - Tableau Oui/Incertain/Non
18. **ArrayOfIncSameDecQuestions** - Augmente/Identique/Diminue
19. **ArrayFlexibleColumn** - Tableau par colonne
20. **ArrayMultiFlexText** - Tableau textes multiples
21. **ArrayMultiFlexNumbers** - Tableau nombres multiples
22. **ArrayMultiscale** - Tableau double échelle

#### Catégorie 5 : Questions Spéciales (8 types) ⭐⭐⭐ FAIBLE
23. **RankingStyle** - Classement/Ranking
24. **MultipleNumericalQuestion** - Plusieurs nombres
25. **Date** - Sélecteur de date
26. **FileUpload** - Upload de fichier
27. **Language** - Sélecteur de langue
28. **Equation** - Équation/calcul
29. **BoilerplateQuestion** - Texte d'information seulement
30. **DummyQuestion** - Question factice

---

## 🗓️ Plan de Travail Détaillé

### PHASE 0 : Préparation (3 jours)

#### Jour 1 : Setup & Documentation
- [x] ✅ Environnement Docker opérationnel
- [x] ✅ Structure du thème créée
- [ ] 📖 Lire la documentation DSFR complète
- [ ] 📖 Lire la documentation LimeSurvey sur les thèmes
- [ ] 🔍 Analyser les templates vanilla en détail

#### Jour 2 : Copie et Analyse
- [ ] 📁 Copier tous les templates vanilla vers dsfr/
- [ ] 🔍 Identifier les templates les plus critiques
- [ ] 📝 Créer un mapping Bootstrap → DSFR détaillé
- [ ] 🎨 Télécharger tous les assets DSFR nécessaires

#### Jour 3 : Configuration de Base
- [ ] ⚙️ Configurer config.xml pour DSFR
- [ ] 🎨 Créer la structure CSS de base
- [ ] 📜 Initialiser le JavaScript DSFR
- [ ] ✅ Tester que le thème se charge sans erreur

---

### PHASE 1 : Foundation - Layout & Navigation (1 semaine)

#### Composants à créer

##### 1.1 Header DSFR (2 jours)
**Fichier** : `views/subviews/header/nav_bar.twig`

**Structure DSFR à implémenter** :
```html
<header role="banner" class="fr-header">
  <div class="fr-header__body">
    <div class="fr-container">
      <div class="fr-header__body-row">
        <div class="fr-header__brand fr-enlarge-link">
          <div class="fr-header__brand-top">
            <div class="fr-header__logo">
              <p class="fr-logo">
                République<br>Française
              </p>
            </div>
            <div class="fr-header__navbar">
              <button class="fr-btn--menu fr-btn" data-fr-opened="false">
                Menu
              </button>
            </div>
          </div>
          <div class="fr-header__service">
            <a href="/" title="Accueil - {Nom du service}">
              <p class="fr-header__service-title">{Nom du service}</p>
            </a>
            <p class="fr-header__service-tagline">{Baseline}</p>
          </div>
        </div>
        <div class="fr-header__tools">
          <div class="fr-header__tools-links">
            <ul class="fr-btns-group">
              <!-- Sauvegarder, Index questions, Langue -->
            </ul>
          </div>
        </div>
      </div>
    </div>
  </div>
  <div class="fr-header__menu fr-modal">
    <div class="fr-container">
      <nav class="fr-nav" role="navigation">
        <!-- Navigation principale si nécessaire -->
      </nav>
    </div>
  </div>
</header>
```

**Tâches** :
- [ ] Remplacer navbar Bootstrap par header DSFR
- [ ] Ajouter le bloc République Française
- [ ] Intégrer le logo Marianne
- [ ] Adapter les boutons de navigation (Save, Clear, Question Index, Language)
- [ ] Rendre responsive
- [ ] Tester sur mobile

##### 1.2 Footer DSFR (1 jour)
**Fichier** : `views/subviews/footer/footer.twig`

**Structure DSFR** :
```html
<footer class="fr-footer" role="contentinfo">
  <div class="fr-container">
    <div class="fr-footer__body">
      <div class="fr-footer__brand fr-enlarge-link">
        <a href="/" title="Retour à l'accueil du site">
          <p class="fr-logo">
            République<br>Française
          </p>
        </a>
      </div>
      <div class="fr-footer__content">
        <p class="fr-footer__content-desc">
          {Description du service}
        </p>
        <ul class="fr-footer__content-list">
          <li class="fr-footer__content-item">
            <a class="fr-footer__content-link" href="#">Mentions légales</a>
          </li>
          <li class="fr-footer__content-item">
            <a class="fr-footer__content-link" href="#">Données personnelles</a>
          </li>
          <li class="fr-footer__content-item">
            <a class="fr-footer__content-link" href="#">Accessibilité</a>
          </li>
        </ul>
      </div>
    </div>
    <div class="fr-footer__bottom">
      <ul class="fr-footer__bottom-list">
        <li class="fr-footer__bottom-item">
          <a class="fr-footer__bottom-link" href="#">Plan du site</a>
        </li>
        <li class="fr-footer__bottom-item">
          <a class="fr-footer__bottom-link" href="#">Contact</a>
        </li>
      </ul>
      <div class="fr-footer__bottom-copy">
        <p>© République Française 2025</p>
      </div>
    </div>
  </div>
</footer>
```

**Tâches** :
- [ ] Créer le footer DSFR complet
- [ ] Ajouter les liens obligatoires (Accessibilité, Mentions légales, etc.)
- [ ] Responsive design

##### 1.3 Barre de Progression (1 jour)
**Fichier** : `views/subviews/header/progress_bar.twig`

**Structure DSFR Stepper** :
```html
<div class="fr-stepper">
  <h2 class="fr-stepper__title">
    Question {currentStep} sur {totalSteps}
  </h2>
  <div class="fr-stepper__steps"
       data-fr-current-step="{currentStep}"
       data-fr-steps="{totalSteps}">
  </div>
  <p class="fr-stepper__details">
    <span class="fr-text--bold">Étape {currentStep}</span> : {currentGroup}
  </p>
</div>
```

**Tâches** :
- [ ] Remplacer progress bar Bootstrap par stepper DSFR
- [ ] Calculer le pourcentage de progression
- [ ] Afficher le numéro de question actuelle
- [ ] Responsive

##### 1.4 Layout Principal (1 jour)
**Fichier** : `views/layout_global.twig`

**Tâches** :
- [ ] Remplacer `<div class="container-fluid">` par `<div class="fr-container">`
- [ ] Retirer les classes Bootstrap du body
- [ ] Ajouter l'attribut `data-fr-theme` pour le thème clair/sombre
- [ ] Structurer avec les grids DSFR (`fr-grid-row`, `fr-col-*`)
- [ ] Tester le layout de base

##### 1.5 Navigation Précédent/Suivant (1 jour)
**Fichier** : `views/subviews/navigation/navigator.twig`

**Structure DSFR** :
```html
<div class="fr-btns-group fr-btns-group--inline fr-btns-group--between">
  <button class="fr-btn fr-btn--secondary" type="submit" name="move" value="moveprev">
    <span class="fr-icon-arrow-left-line fr-icon--sm" aria-hidden="true"></span>
    Précédent
  </button>
  <button class="fr-btn" type="submit" name="move" value="movenext">
    Suivant
    <span class="fr-icon-arrow-right-line fr-icon--sm" aria-hidden="true"></span>
  </button>
</div>
```

**Tâches** :
- [ ] Bouton Précédent (secondaire)
- [ ] Bouton Suivant (primaire)
- [ ] Icônes DSFR
- [ ] Responsive (colonne sur mobile)

##### 1.6 Messages & Alertes (1 jour)
**Fichiers** : `views/subviews/messages/*.twig`

**Structure DSFR Alert** :
```html
<div class="fr-alert fr-alert--{type}">
  <p class="fr-alert__title">{title}</p>
  <p>{message}</p>
</div>
```

**Types** : `success`, `error`, `info`, `warning`

**Tâches** :
- [ ] Convertir welcome.twig
- [ ] Convertir warnings.twig
- [ ] Convertir assessments.twig
- [ ] Convertir justsaved.twig
- [ ] Convertir no_js_alert.twig

---

### PHASE 2 : Questions Prioritaires (2 semaines)

#### 2.1 Question Text Input (2 jours)
**Type** : ShortFreeText, LongFreeText, Numerical

**Fichiers** :
- `application/views/survey/questions/answer/shortfreetext/answer.twig`
- `application/views/survey/questions/answer/longfreetext/answer.twig`
- `application/views/survey/questions/answer/numerical/answer.twig`

**Structure DSFR Input** :
```html
<div class="fr-input-group">
  <label class="fr-label" for="text-input-{qid}">
    {questionText}
    {% if mandatory %}<span class="fr-error-text">*</span>{% endif %}
  </label>
  <input class="fr-input"
         type="text"
         id="text-input-{qid}"
         name="{sgqa}"
         {% if error %}aria-describedby="text-input-{qid}-error"{% endif %} />

  {% if error %}
  <p id="text-input-{qid}-error" class="fr-error-text">
    <span class="fr-error-text__icon" aria-hidden="true"></span>
    {errorMessage}
  </p>
  {% endif %}

  {% if help %}
  <p class="fr-hint-text">{help}</p>
  {% endif %}
</div>
```

**Tâches** :
- [ ] Input court avec `fr-input`
- [ ] Textarea avec `fr-input`
- [ ] Input numérique
- [ ] Gestion des erreurs
- [ ] Texte d'aide
- [ ] Champs obligatoires
- [ ] Validation côté client

#### 2.2 Question Radio (3 jours)
**Type** : ListRadio, YesNoRadio, 5PointChoice

**Fichiers** :
- `application/views/survey/questions/answer/listradio/answer.twig`
- `application/views/survey/questions/answer/listradio/rows/answer_row.twig`
- `application/views/survey/questions/answer/yesno/answer.twig`
- `application/views/survey/questions/answer/5pointchoice/answer.twig`

**Structure DSFR Radio** :
```html
<fieldset class="fr-fieldset"
          {% if error %}aria-describedby="radio-{qid}-messages"{% endif %}>
  <legend class="fr-fieldset__legend fr-text--regular">
    {questionText}
    {% if mandatory %}<span class="fr-error-text">*</span>{% endif %}
  </legend>

  {% if help %}
  <p class="fr-hint-text">{help}</p>
  {% endif %}

  <div class="fr-fieldset__content">
    {% for answer in answers %}
    <div class="fr-radio-group">
      <input type="radio"
             id="radio-{qid}-{answer.code}"
             name="{sgqa}"
             value="{answer.code}">
      <label class="fr-label" for="radio-{qid}-{answer.code}">
        {answer.text}
      </label>
    </div>
    {% endfor %}
  </div>

  {% if error %}
  <div class="fr-messages-group" id="radio-{qid}-messages" aria-live="assertive">
    <p class="fr-message fr-message--error">
      {errorMessage}
    </p>
  </div>
  {% endif %}
</fieldset>
```

**Tâches** :
- [ ] Structure fieldset + legend
- [ ] Radio buttons DSFR
- [ ] Labels associés
- [ ] Options "Autre" avec champ texte
- [ ] Options "Aucune réponse"
- [ ] Validation
- [ ] Radio horizontaux (option)

#### 2.3 Question Checkbox (2 jours)
**Type** : MultipleChoice

**Fichiers** :
- `application/views/survey/questions/answer/multiplechoice/answer.twig`
- `application/views/survey/questions/answer/multiplechoice/rows/answer_row.twig`

**Structure DSFR Checkbox** :
```html
<fieldset class="fr-fieldset">
  <legend class="fr-fieldset__legend fr-text--regular">
    {questionText}
    {% if mandatory %}<span class="fr-error-text">*</span>{% endif %}
  </legend>

  <div class="fr-fieldset__content">
    {% for answer in answers %}
    <div class="fr-checkbox-group">
      <input type="checkbox"
             id="checkbox-{qid}-{answer.code}"
             name="{sgqa}"
             value="{answer.code}">
      <label class="fr-label" for="checkbox-{qid}-{answer.code}">
        {answer.text}
      </label>
    </div>
    {% endfor %}
  </div>
</fieldset>
```

**Tâches** :
- [ ] Checkboxes DSFR
- [ ] Labels
- [ ] Option "Autre"
- [ ] Min/max sélections
- [ ] Validation

#### 2.4 Question Dropdown (2 jours)
**Type** : ListDropdown

**Fichiers** :
- `application/views/survey/questions/answer/list_dropdown/answer.twig`

**Structure DSFR Select** :
```html
<div class="fr-select-group">
  <label class="fr-label" for="select-{qid}">
    {questionText}
    {% if mandatory %}<span class="fr-error-text">*</span>{% endif %}
  </label>

  <select class="fr-select" id="select-{qid}" name="{sgqa}">
    <option value="">Sélectionnez une option</option>
    {% for answer in answers %}
    <option value="{answer.code}">{answer.text}</option>
    {% endfor %}
  </select>
</div>
```

**Tâches** :
- [ ] Select DSFR
- [ ] Options
- [ ] Option par défaut
- [ ] Validation

#### 2.5 Container de Question (1 jour)
**Fichiers** :
- `views/subviews/survey/question_container.twig`
- `views/subviews/survey/question.twig`

**Structure DSFR** :
```html
<div class="fr-my-4w" id="question{qid}">
  <div class="fr-container--fluid">
    {# Numéro de question #}
    <div class="fr-mb-1w">
      <span class="fr-badge fr-badge--sm">Question {seq}</span>
    </div>

    {# Contenu de la question #}
    {include questionTemplate}

    {# Messages de validation #}
    {% if validationMessages %}
    <div class="fr-messages-group">
      {validationMessages}
    </div>
    {% endif %}
  </div>
</div>
```

**Tâches** :
- [ ] Wrapper de question
- [ ] Numérotation
- [ ] Code question
- [ ] Conteneur des réponses
- [ ] Zone de validation

---

### PHASE 3 : Questions Avancées (1,5 semaines)

#### 3.1 Questions Array (5 jours)
**Types** : ArrayFlexibleRow, Array5Point, Array10Point

**Structure DSFR Table** :
```html
<div class="fr-table fr-table--bordered">
  <table>
    <caption>{questionText}</caption>
    <thead>
      <tr>
        <th scope="col"></th>
        {% for col in columns %}
        <th scope="col">{col}</th>
        {% endfor %}
      </tr>
    </thead>
    <tbody>
      {% for row in rows %}
      <tr>
        <th scope="row">{row.text}</th>
        {% for col in columns %}
        <td>
          <div class="fr-radio-group">
            <input type="radio" ...>
            <label class="fr-label">...</label>
          </div>
        </td>
        {% endfor %}
      </tr>
      {% endfor %}
    </tbody>
  </table>
</div>
```

**Tâches** :
- [ ] 10 types de tableaux array
- [ ] Tables DSFR responsive
- [ ] Radio dans cellules
- [ ] Checkbox dans cellules
- [ ] Input texte dans cellules
- [ ] Validation par ligne

#### 3.2 Questions Spéciales (3 jours)
**Types** : Ranking, Date, FileUpload

**Tâches** :
- [ ] Ranking avec drag & drop DSFR
- [ ] Date picker DSFR
- [ ] Upload de fichier DSFR

---

### PHASE 4 : Pages & Workflow (1 semaine)

#### 4.1 Page d'Accueil (1 jour)
**Fichier** : `views/subviews/content/firstpage.twig`

**Tâches** :
- [ ] Titre enquête avec typo DSFR
- [ ] Description
- [ ] Message de bienvenue
- [ ] Politique de confidentialité (modal DSFR)
- [ ] Bouton "Commencer"

#### 4.2 Page de Soumission (1 jour)
**Fichier** : `views/subviews/content/submit.twig`

**Tâches** :
- [ ] Message de confirmation
- [ ] Récapitulatif (si activé)
- [ ] Export PDF avec styles DSFR

#### 4.3 Save/Load (1 jour)
**Fichiers** : `views/subviews/content/save.twig`, `load.twig`

**Tâches** :
- [ ] Formulaire de sauvegarde DSFR
- [ ] Champ email/password
- [ ] Boutons DSFR

#### 4.4 Modales (2 jours)
**Fichiers** : `views/subviews/messages/bootstrap_alert_modal.twig`, `privacy_modal.twig`

**Structure DSFR Modal** :
```html
<dialog class="fr-modal" id="modal-{id}">
  <div class="fr-container fr-container--fluid fr-container-md">
    <div class="fr-grid-row fr-grid-row--center">
      <div class="fr-col-12 fr-col-md-8">
        <div class="fr-modal__body">
          <div class="fr-modal__header">
            <button class="fr-btn--close fr-btn"
                    aria-controls="modal-{id}">
              Fermer
            </button>
          </div>
          <div class="fr-modal__content">
            <h1 class="fr-modal__title">{title}</h1>
            <p>{content}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</dialog>
```

**Tâches** :
- [ ] Modal DSFR pour alertes
- [ ] Modal pour confidentialité
- [ ] Modal pour index questions

---

### PHASE 5 : CSS & JavaScript (1 semaine)

#### 5.1 CSS Principal (3 jours)
**Fichier** : `css/theme.css`

**Contenu** :
```css
/* Import DSFR */
@import url('https://unpkg.com/@gouvfr/dsfr@1.11/dist/dsfr.min.css');

/* Variables personnalisées si besoin */
:root {
  --custom-var: value;
}

/* Overrides spécifiques LimeSurvey */
.ls-answers { ... }
.question-container { ... }

/* Utilitaires */
.space-col { ... }
```

**Tâches** :
- [ ] Importer DSFR
- [ ] Ajouter les overrides nécessaires
- [ ] Responsive design
- [ ] Print styles

#### 5.2 JavaScript (2 jours)
**Fichier** : `scripts/theme.js`

**Tâches** :
- [ ] Charger DSFR JS
- [ ] Initialiser les composants DSFR
- [ ] Créer les objets attendus par LimeSurvey
- [ ] Validation formulaires
- [ ] Interactions custom

#### 5.3 Configuration (1 jour)
**Fichier** : `config.xml`

**Tâches** :
- [ ] Déclarer tous les fichiers CSS/JS
- [ ] Configurer les options du thème
- [ ] Définir les écrans pour l'éditeur
- [ ] Tester le chargement

#### 5.4 Assets (1 jour)
**Dossier** : `files/`

**Tâches** :
- [ ] Logo Marianne
- [ ] Favicon RF
- [ ] Images par défaut
- [ ] Icônes supplémentaires si besoin

---

### PHASE 6 : Tests & Finitions (1 semaine)

#### 6.1 Tests Fonctionnels (3 jours)
- [ ] Tester TOUS les types de questions
- [ ] Tester le workflow complet (welcome → questions → submit)
- [ ] Tester save/load
- [ ] Tester les validations
- [ ] Tester les messages d'erreur

#### 6.2 Tests Responsive (1 jour)
- [ ] Mobile (< 576px)
- [ ] Tablet (576-992px)
- [ ] Desktop (> 992px)
- [ ] Vérifier tous les composants

#### 6.3 Tests Accessibilité (2 jours)
- [ ] Navigation clavier
- [ ] Lecteur d'écran (NVDA/JAWS/VoiceOver)
- [ ] Contrastes de couleurs
- [ ] Focus visible
- [ ] Attributs ARIA
- [ ] Tests avec des utilisateurs

#### 6.4 Documentation (1 jour)
- [ ] README complet
- [ ] Guide d'installation
- [ ] Guide de personnalisation
- [ ] Changelog
- [ ] Exemples

---

## 📦 Livrables

### Livrable 1 : MVP (Fin Semaine 2)
- ✅ Layout DSFR (header, footer, navigation)
- ✅ 5 types de questions de base fonctionnels
- ✅ Page welcome/submit
- ✅ CSS de base
- 🎯 **Utilisable pour 80% des enquêtes simples**

### Livrable 2 : V1 (Fin Semaine 4)
- ✅ Tous les types de questions courants
- ✅ Questions array
- ✅ Save/load
- ✅ Modales
- ✅ Validation complète
- 🎯 **Production-ready pour la majorité des cas**

### Livrable 3 : V2 (Fin Semaine 6)
- ✅ Questions spéciales (ranking, upload, etc.)
- ✅ Print styles
- ✅ Tests d'accessibilité complets
- ✅ Documentation complète
- 🎯 **Version complète et certifiée RGAA**

---

## 🎯 Priorisation des Tâches

### Must Have (Critique)
1. Header DSFR
2. Footer DSFR
3. Navigation (prev/next)
4. Questions : text, radio, checkbox, dropdown
5. Layout de base
6. CSS principal
7. JavaScript de base

### Should Have (Important)
8. Barre de progression
9. Messages & alertes
10. Questions array
11. Page welcome/submit
12. Modales
13. Save/load
14. Validation

### Nice to Have (Optionnel)
15. Questions spéciales (ranking, upload)
16. Print styles
17. Question themes variants
18. Animations
19. Dark mode

---

## 🚧 Risques & Défis

### Risques Techniques
1. **Compatibilité DSFR ↔ LimeSurvey** - Possible conflit JS/CSS
   - *Mitigation* : Namespace, tests incrémentaux

2. **Complexité des questions array** - Nombreuses variantes
   - *Mitigation* : Template commun, composition

3. **Responsive des tableaux** - Difficile sur mobile
   - *Mitigation* : Scroll horizontal, collapse sur mobile

4. **Performance** - DSFR + LimeSurvey JS = lourd
   - *Mitigation* : Lazy loading, minification

### Défis Organisationnels
1. **Maintenance** - LimeSurvey évolue
   - *Solution* : Versioning, tests automatisés

2. **Documentation** - Complexe à maintenir
   - *Solution* : Documentation as code, exemples

---

## 💡 Recommandations

### Pour démarrer MAINTENANT
1. **Commencez par le header** - C'est le plus visible
2. **Puis le layout** - Foundation du reste
3. **Ensuite 3 types de questions** - text, radio, checkbox
4. **Testez à chaque étape** - Ne pas accumuler les bugs

### Pour aller vite
- **Utiliser des snippets** - Créer des templates réutilisables
- **Tester en parallèle** - Un fichier = un test
- **Automatiser** - Scripts de génération si possible
- **Documenter au fur et à mesure** - Pas après

### Pour la qualité
- **Respecter DSFR à 100%** - Pas de compromis
- **Accessibilité dès le début** - Pas en afterthought
- **Code reviews** - Peer review des templates
- **Tests utilisateurs** - Feedback réel

---

## 📊 Métriques de Succès

- [ ] **100% des composants DSFR** utilisés correctement
- [ ] **0 classe Bootstrap** restante
- [ ] **Accessibilité RGAA AAA** sur tous les composants
- [ ] **< 3s temps de chargement** sur 4G
- [ ] **100% responsive** mobile/tablet/desktop
- [ ] **Score Lighthouse > 90** sur tous les critères
- [ ] **Validation W3C** HTML/CSS sans erreur

---

## 🎓 Ressources

### Documentation
- [DSFR Documentation](https://www.systeme-de-design.gouv.fr/)
- [DSFR Composants](https://www.systeme-de-design.gouv.fr/composants)
- [LimeSurvey Theme Manual](https://manual.limesurvey.org/Themes)
- [Twig Documentation](https://twig.symfony.com/)

### Outils
- [DSFR sur GitHub](https://github.com/GouvernementFR/dsfr)
- [RGAA Checker](https://ara.numerique.gouv.fr/)
- [Contrast Checker](https://webaim.org/resources/contrastchecker/)
- [Lighthouse](https://developers.google.com/web/tools/lighthouse)

---

## ✅ Checklist de Démarrage

Avant de commencer le développement :

- [ ] Lire ce plan en entier
- [ ] Lire la documentation DSFR
- [ ] Analyser 3-4 templates vanilla en détail
- [ ] Installer les outils de dev (linters, formatters)
- [ ] Créer un système de versioning
- [ ] Mettre en place les tests
- [ ] Créer une branche Git dédiée
- [ ] Préparer un environnement de démo

---

**Prêt à démarrer ? Par quoi voulez-vous commencer ?**

Options :
1. 🎨 Créer le header DSFR conforme
2. 📝 Adapter la première question (text input)
3. 🏗️ Copier tous les templates vanilla vers dsfr
4. 📚 Analyser plus en détail un composant spécifique
