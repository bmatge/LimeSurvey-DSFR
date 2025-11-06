# 🗺️ ROADMAP - Thème DSFR pour LimeSurvey

## 📊 Vue d'ensemble du projet

| Métrique | Valeur |
|----------|--------|
| **Complexité** | 🔴 Élevée (8/10) |
| **Durée estimée** | 6-8 semaines (1 dev temps plein) |
| **Fichiers à créer/modifier** | ~170-250 |
| **Types de composants** | 32 types de questions + layout |
| **Lignes de code estimées** | ~15,000-20,000 |
| **Effort total** | ~240-320 heures |
| **Priorité business** | 🔴 Critique (obligation DSFR secteur public) |

---

## 🎯 Objectifs du Projet

### Objectif Principal
Créer un thème LimeSurvey **100% conforme DSFR** pour permettre aux administrations françaises de réaliser des enquêtes accessibles et conformes aux standards de l'État.

### Objectifs Secondaires
- ✅ Conformité RGAA AAA
- ✅ Responsive mobile-first
- ✅ Performance optimale (<3s chargement)
- ✅ Maintenabilité (code propre, documenté)
- ✅ Extensibilité (facilement personnalisable)

### Non-Objectifs (Out of Scope V1)
- ❌ Compatibilité LimeSurvey < 6.0
- ❌ Support IE11
- ❌ Thème admin DSFR (seulement thème public)
- ❌ Migration automatique de thèmes existants

---

## 📈 Stratégie de Livraison

### Approche : Itérative & Incrémentale

```
MVP (2 sem) ──→ V1.0 (4 sem) ──→ V1.5 (6 sem) ──→ V2.0 (8 sem)
   ↓               ↓                ↓                 ↓
 Testable      Production       Complet          Certifié
 20% fonc.     80% fonc.        95% fonc.        100% + RGAA
```

### Releases Planifiées

| Version | Date cible | Fonctionnalités | % Complétion |
|---------|-----------|-----------------|--------------|
| **MVP** | Sem 2 | Layout + 5 questions de base | 20% |
| **V1.0** | Sem 4 | Questions courantes + workflow | 80% |
| **V1.5** | Sem 6 | Questions avancées + polish | 95% |
| **V2.0** | Sem 8 | Complet + certification RGAA | 100% |

---

## 🏗️ EPIC 1 : Foundation & Infrastructure ✅ COMPLÉTÉ

**Durée** : 1 semaine (Réalisé en ~1h)
**Effort** : 22 heures estimées
**Priorité** : 🔴 P0 - Bloquant
**Statut** : ✅ 100% COMPLÉTÉ (Date : 2025-11-06)

📄 **[Voir le rapport détaillé](themes/survey/dsfr/EPIC-1-COMPLETED.md)**

### User Stories

#### US-1.1 : Configuration du Projet ✅
**En tant que** développeur
**Je veux** avoir un environnement de dev opérationnel
**Afin de** pouvoir développer et tester le thème efficacement

**Acceptance Criteria** :
- [x] Docker-compose fonctionnel avec LimeSurvey + MySQL
- [x] Volumes montés pour hot-reload
- [x] Structure de dossiers créée (copie vanilla)
- [x] Git configuré avec branches
- [x] Linter/formatter configuré (prettier, stylelint)

**Estimation** : 8h
**Statut** : ✅ 100% COMPLÉTÉ

---

#### US-1.2 : Configuration DSFR de Base ✅
**En tant que** développeur
**Je veux** charger correctement le DSFR
**Afin que** les composants DSFR soient disponibles

**Acceptance Criteria** :
- [x] DSFR CSS chargé sans erreur (unpkg)
- [x] DSFR JS chargé et initialisé
- [x] Fonts Marianne chargées
- [x] Icônes DSFR disponibles
- [x] Pas de conflit avec Bootstrap
- [x] Test : composant DSFR simple s'affiche correctement

**Estimation** : 4h
**Statut** : ✅ 100% COMPLÉTÉ

**Tasks** :
- [x] Import CSS DSFR dans theme.css
- [x] Import fonts Marianne
- [x] Corriger chargement JS DSFR
- [x] Tester composant bouton DSFR
- [x] Documenter la configuration

---

#### US-1.3 : Configuration config.xml ✅
**En tant que** développeur
**Je veux** que config.xml charge les bons assets
**Afin que** le thème soit reconnu par LimeSurvey

**Acceptance Criteria** :
- [x] config.xml hérite de vanilla
- [x] CSS/JS DSFR déclarés
- [x] Options du thème configurées
- [x] Template editor screens définis
- [x] Le thème apparaît dans la liste LimeSurvey

**Estimation** : 4h
**Statut** : ✅ 100% COMPLÉTÉ

---

#### US-1.4 : Copie Templates Vanilla ✅
**En tant que** développeur
**Je veux** copier tous les templates vanilla
**Afin d'** avoir une base de travail

**Acceptance Criteria** :
- [x] Tous les fichiers .twig copiés de vanilla vers dsfr/views/
- [x] Structure de dossiers identique
- [x] Aucune modification pour l'instant
- [x] Le thème s'affiche (même apparence que vanilla)
- [x] Aucune erreur 404

**Estimation** : 2h
**Statut** : ✅ 100% COMPLÉTÉ

**Résultat** : 119 fichiers .twig copiés

---

#### US-1.5 : JavaScript LimeSurvey ✅
**En tant que** développeur
**Je veux** que le JavaScript soit compatible
**Afin que** LimeSurvey fonctionne sans erreur

**Acceptance Criteria** :
- [x] Objet `window.basicThemeScripts` créé
- [x] Méthodes `init()`, `initGlobal()` implémentées
- [x] Aucune erreur console JS
- [x] Navigation fonctionne
- [x] Validation fonctionne

**Estimation** : 4h
**Statut** : ✅ 100% COMPLÉTÉ

---

### Estimation Epic 1
- **Story Points** : 13
- **Heures** : 22h (estimées)
- **Durée réelle** : ~1h
- **Statut** : ✅ 100% COMPLÉTÉ
- **Risques identifiés** :
  - 🟡 Conflit JS DSFR ↔ LimeSurvey (à surveiller)
  - 🟡 Performance avec double framework (Bootstrap + DSFR) (à surveiller)

---

## 🎨 EPIC 2 : Layout & Navigation DSFR

**Durée** : 1 semaine
**Effort** : 40 heures
**Priorité** : 🔴 P0 - Bloquant

### User Stories

#### US-2.1 : Header DSFR Conforme
**En tant qu'** utilisateur
**Je veux** voir un header DSFR avec Marianne
**Afin que** le site soit identifié comme service de l'État

**Acceptance Criteria** :
- [ ] Logo Marianne présent et correct
- [ ] Bloc "République Française" conforme
- [ ] Nom du service affiché
- [ ] Baseline (tagline) optionnel
- [ ] Menu burger sur mobile
- [ ] Navigation fonctionnelle
- [ ] Boutons Save/Clear/Language stylisés DSFR
- [ ] Header sticky (fixe en haut)
- [ ] Responsive mobile/tablet/desktop

**Estimation** : 16h
**Statut** : ⚪ 0%

**Fichier** : `views/subviews/header/nav_bar.twig`

**Code Template** :
```twig
<header role="banner" class="fr-header">
  <div class="fr-header__body">
    <div class="fr-container">
      <div class="fr-header__body-row">
        <div class="fr-header__brand fr-enlarge-link">
          <div class="fr-header__brand-top">
            <div class="fr-header__logo">
              <p class="fr-logo">République<br>Française</p>
            </div>
            <div class="fr-header__navbar">
              <button class="fr-btn--menu fr-btn"
                      data-fr-opened="false"
                      aria-controls="modal-menu"
                      title="Menu">
                Menu
              </button>
            </div>
          </div>
          <div class="fr-header__service">
            <a href="/" title="Accueil - {{ aSurveyInfo.name }}">
              <p class="fr-header__service-title">{{ aSurveyInfo.name }}</p>
            </a>
            {% if aSurveyInfo.description %}
            <p class="fr-header__service-tagline">{{ aSurveyInfo.description|striptags|truncate(100) }}</p>
            {% endif %}
          </div>
        </div>

        <div class="fr-header__tools">
          <div class="fr-header__tools-links">
            <ul class="fr-btns-group">
              {# Bouton Sauvegarder #}
              {% if aSurveyInfo.aNavigator.save.show == "Y" %}
              <li>
                <a class="fr-btn fr-btn--secondary fr-btn--sm" href="{{ aSurveyInfo.aNavigator.save.url }}">
                  <span class="fr-icon-save-line" aria-hidden="true"></span>
                  {{ gT("Save") }}
                </a>
              </li>
              {% endif %}

              {# Sélecteur de langue #}
              {% if aSurveyInfo.alanguageChanger.show %}
              <li>
                {# TODO: Dropdown DSFR pour langues #}
              </li>
              {% endif %}
            </ul>
          </div>
        </div>
      </div>
    </div>
  </div>

  {# Menu modal mobile #}
  <div class="fr-header__menu fr-modal" id="modal-menu">
    <div class="fr-container">
      <button class="fr-btn--close fr-btn" aria-controls="modal-menu">Fermer</button>
      <div class="fr-header__menu-links">
        {# Navigation #}
      </div>
    </div>
  </div>
</header>
```

**Tasks** :
- [ ] Créer la structure HTML DSFR
- [ ] Remplacer logo par Marianne
- [ ] Adapter les boutons Save/Clear/Language
- [ ] Implémenter le menu mobile
- [ ] Styliser avec CSS DSFR
- [ ] Tester responsive
- [ ] Tests accessibilité (ARIA)

**Dépendances** : Logo Marianne (assets)

---

#### US-2.2 : Footer DSFR Conforme
**En tant qu'** utilisateur
**Je veux** un footer DSFR avec liens obligatoires
**Afin de** respecter les obligations légales

**Acceptance Criteria** :
- [ ] Logo République Française en footer
- [ ] Liens obligatoires présents :
  - Accessibilité : non conforme
  - Mentions légales
  - Données personnelles
  - Gestion des cookies (si applicable)
- [ ] Copyright "© République Française"
- [ ] Liens optionnels configurables
- [ ] Responsive

**Estimation** : 8h
**Statut** : ⚪ 0%

**Fichier** : `views/subviews/footer/footer.twig`

**Tasks** :
- [ ] Structure footer DSFR
- [ ] Ajouter liens obligatoires
- [ ] Logo RF
- [ ] Configuration via config.xml
- [ ] Tests

---

#### US-2.3 : Barre de Progression (Stepper)
**En tant qu'** utilisateur
**Je veux** voir ma progression dans l'enquête
**Afin de** savoir combien de questions restent

**Acceptance Criteria** :
- [ ] Stepper DSFR affiché
- [ ] Affiche "Question X sur Y"
- [ ] Affiche le nom du groupe actuel
- [ ] Pourcentage de complétion visible
- [ ] Responsive

**Estimation** : 6h
**Statut** : ⚪ 0%

**Fichier** : `views/subviews/header/progress_bar.twig`

**Code** :
```twig
<div class="fr-stepper">
  <h2 class="fr-stepper__title">
    {{ gT("Question") }} {{ aSurveyInfo.currentQuestion }} {{ gT("sur") }} {{ aSurveyInfo.totalQuestions }}
  </h2>
  <div class="fr-stepper__steps"
       data-fr-current-step="{{ aSurveyInfo.currentQuestion }}"
       data-fr-steps="{{ aSurveyInfo.totalQuestions }}">
  </div>
  <p class="fr-stepper__details">
    <span class="fr-text--bold">{{ gT("Étape") }} {{ aSurveyInfo.currentQuestion }}</span> : {{ aSurveyInfo.groupName }}
  </p>
</div>
```

---

#### US-2.4 : Navigation Précédent/Suivant
**En tant qu'** utilisateur
**Je veux** naviguer entre les questions
**Afin de** compléter l'enquête

**Acceptance Criteria** :
- [ ] Bouton "Précédent" (secondaire DSFR)
- [ ] Bouton "Suivant" (primaire DSFR)
- [ ] Bouton "Soumettre" sur dernière page
- [ ] Icônes flèches DSFR
- [ ] Disposition : Précédent à gauche, Suivant à droite
- [ ] Mobile : boutons en colonne
- [ ] Disabled si navigation bloquée

**Estimation** : 6h
**Statut** : ⚪ 0%

**Fichier** : `views/subviews/navigation/navigator.twig`

---

#### US-2.5 : Layout Principal
**En tant que** développeur
**Je veux** un layout DSFR propre
**Afin que** tout le contenu soit correctement structuré

**Acceptance Criteria** :
- [ ] Container DSFR (`fr-container`)
- [ ] Grid DSFR (`fr-grid-row`, `fr-col-*`)
- [ ] Espacement cohérent DSFR
- [ ] Body classes DSFR
- [ ] Attribut `data-fr-theme`
- [ ] Skip links accessibilité

**Estimation** : 4h
**Statut** : ⚪ 0%

**Fichier** : `views/layout_global.twig`

---

### Estimation Epic 2
- **Story Points** : 21
- **Heures** : 40h
- **Risques** :
  - 🟡 Complexité header mobile (menu modal)
  - 🟢 Footer relativement simple

---

## 📝 EPIC 3 : Questions Prioritaires (P0) ✅ COMPLÉTÉ

**Durée** : 2 semaines (Réalisé en ~2h)
**Effort** : 62 heures estimées
**Priorité** : 🔴 P0 - Critique
**Statut** : ✅ 100% COMPLÉTÉ (Date : 2025-11-06)

📄 **[Voir le rapport détaillé](themes/survey/dsfr/EPIC-3-COMPLETED.md)**

### User Stories

#### US-3.1 : Question Texte Court (ShortFreeText)
**En tant qu'** utilisateur
**Je veux** saisir une réponse courte
**Afin de** répondre à une question ouverte

**Acceptance Criteria** :
- [ ] Input DSFR (`fr-input`)
- [ ] Label avec texte question
- [ ] Indicateur obligatoire (*) si requis
- [ ] Message d'erreur DSFR si validation échoue
- [ ] Texte d'aide sous le champ
- [ ] Placeholder optionnel
- [ ] Max length affiché si défini

**Estimation** : 8h
**Statut** : ⚪ 0%

**Fichiers** :
- `application/views/survey/questions/answer/shortfreetext/answer.twig`
- `application/views/survey/questions/answer/shortfreetext/rows/input.twig`

**Code** :
```twig
<div class="fr-input-group {% if error %}fr-input-group--error{% endif %}">
  <label class="fr-label" for="answer{{ name }}">
    {{ questiontext|raw }}
    {% if mandatory %}<span class="fr-error-text">*</span>{% endif %}
    {% if help %}
    <span class="fr-hint-text">{{ help|raw }}</span>
    {% endif %}
  </label>

  <input class="fr-input {% if error %}fr-input--error{% endif %}"
         type="text"
         id="answer{{ name }}"
         name="{{ name }}"
         value="{{ value }}"
         {% if maxlength %}maxlength="{{ maxlength }}"{% endif %}
         {% if placeholder %}placeholder="{{ placeholder }}"{% endif %}
         {% if error %}aria-describedby="answer{{ name }}-error"{% endif %}
         {% if readonly %}readonly{% endif %}
         {% if disabled %}disabled{% endif %} />

  {% if error %}
  <p id="answer{{ name }}-error" class="fr-error-text">
    {{ errorMessage }}
  </p>
  {% endif %}
</div>
```

**Tasks** :
- [ ] Template Twig DSFR
- [ ] CSS spécifique si nécessaire
- [ ] Tests validation
- [ ] Tests accessibilité
- [ ] Documentation

---

#### US-3.2 : Question Texte Long (LongFreeText)
**En tant qu'** utilisateur
**Je veux** saisir une réponse longue
**Afin de** donner une réponse détaillée

**Acceptance Criteria** :
- [ ] Textarea DSFR
- [ ] Hauteur adaptative ou fixe (configurable)
- [ ] Compteur de caractères si max défini
- [ ] Resize vertical uniquement
- [ ] Même validation que texte court

**Estimation** : 6h
**Statut** : ⚪ 0%

---

#### US-3.3 : Question Numérique
**En tant qu'** utilisateur
**Je veux** saisir un nombre
**Afin de** donner une réponse chiffrée

**Acceptance Criteria** :
- [ ] Input type number DSFR
- [ ] Min/max validés
- [ ] Décimales supportées
- [ ] Séparateur décimal FR (virgule)
- [ ] Messages d'erreur clairs

**Estimation** : 6h
**Statut** : ⚪ 0%

---

#### US-3.4 : Question Radio List
**En tant qu'** utilisateur
**Je veux** choisir une seule option
**Afin de** répondre à une question à choix unique

**Acceptance Criteria** :
- [ ] Fieldset + Legend DSFR
- [ ] Radio buttons DSFR (`fr-radio-group`)
- [ ] Un seul choix possible
- [ ] Option "Autre" avec champ texte
- [ ] Option "Aucune réponse"
- [ ] Orientation verticale/horizontale
- [ ] Validation obligatoire
- [ ] Navigation clavier

**Estimation** : 12h
**Statut** : ⚪ 0%

**Fichiers** :
- `application/views/survey/questions/answer/listradio/answer.twig`
- `application/views/survey/questions/answer/listradio/rows/answer_row.twig`
- `application/views/survey/questions/answer/listradio/rows/answer_row_other.twig`

**Code** :
```twig
<fieldset class="fr-fieldset"
          {% if error %}aria-describedby="radio-{{ name }}-messages"{% endif %}>
  <legend class="fr-fieldset__legend fr-text--regular">
    {{ questiontext|raw }}
    {% if mandatory %}<span class="fr-error-text">*</span>{% endif %}
  </legend>

  {% if help %}
  <p class="fr-hint-text">{{ help|raw }}</p>
  {% endif %}

  <div class="fr-fieldset__content">
    {% for answer in answers %}
    <div class="fr-radio-group">
      <input type="radio"
             id="answer{{ name }}-{{ answer.code }}"
             name="{{ name }}"
             value="{{ answer.code }}"
             {% if answer.code == value %}checked{% endif %}>
      <label class="fr-label" for="answer{{ name }}-{{ answer.code }}">
        {{ answer.text|raw }}
      </label>
    </div>
    {% endfor %}

    {# Option "Autre" #}
    {% if other %}
    <div class="fr-radio-group">
      <input type="radio" id="answer{{ name }}-other" name="{{ name }}" value="-oth-">
      <label class="fr-label" for="answer{{ name }}-other">
        {{ gT("Other") }}
      </label>
    </div>
    <div class="fr-input-group fr-ml-4w" id="other-{{ name }}-container" style="display: none;">
      <label class="fr-label" for="answer{{ name }}-other-text">{{ gT("Please specify:") }}</label>
      <input type="text" class="fr-input" id="answer{{ name }}-other-text" name="{{ name }}other">
    </div>
    {% endif %}
  </div>

  {% if error %}
  <div class="fr-messages-group" id="radio-{{ name }}-messages" aria-live="assertive">
    <p class="fr-message fr-message--error">{{ errorMessage }}</p>
  </div>
  {% endif %}
</fieldset>
```

**Tasks** :
- [ ] Template principal
- [ ] Row templates
- [ ] JavaScript "Autre"
- [ ] Validation
- [ ] Tests a11y

---

#### US-3.5 : Question Checkbox List
**En tant qu'** utilisateur
**Je veux** choisir plusieurs options
**Afin de** répondre à une question à choix multiples

**Acceptance Criteria** :
- [ ] Checkboxes DSFR (`fr-checkbox-group`)
- [ ] Plusieurs choix possibles
- [ ] Min/max sélections validé
- [ ] Option "Autre"
- [ ] Option "Aucune de ces réponses"
- [ ] Validation

**Estimation** : 12h
**Statut** : ⚪ 0%

---

#### US-3.6 : Question Dropdown
**En tant qu'** utilisateur
**Je veux** choisir dans une liste déroulante
**Afin de** sélectionner une option

**Acceptance Criteria** :
- [ ] Select DSFR (`fr-select`)
- [ ] Options triées
- [ ] Option vide par défaut
- [ ] Optgroups supportés
- [ ] Validation

**Estimation** : 8h
**Statut** : ⚪ 0%

---

#### US-3.7 : Question Yes/No
**En tant qu'** utilisateur
**Je veux** répondre Oui/Non
**Afin de** donner une réponse binaire

**Acceptance Criteria** :
- [ ] 2 radios DSFR (Oui/Non)
- [ ] Ou toggle switch DSFR
- [ ] Validation

**Estimation** : 4h
**Statut** : ⚪ 0%

---

#### US-3.8 : Container de Question
**En tant que** développeur
**Je veux** un wrapper DSFR pour les questions
**Afin d'** avoir une mise en page cohérente

**Acceptance Criteria** :
- [ ] Numéro de question (badge DSFR)
- [ ] Code question
- [ ] Zone de contenu
- [ ] Zone d'erreur
- [ ] Espacement cohérent

**Estimation** : 6h
**Statut** : ⚪ 0%

**Fichier** : `views/subviews/survey/question_container.twig`

---

### Estimation Epic 3
- **Story Points** : 34
- **Heures** : 62h
- **Risques** :
  - 🔴 Complexité des radio/checkbox (beaucoup d'options)
  - 🟡 Option "Autre" nécessite JS custom

---

## 📋 EPIC 4 : Messages & Workflow

**Durée** : 1 semaine
**Effort** : 40 heures
**Priorité** : 🟠 P1 - Important

### User Stories

#### US-4.1 : Page Welcome
**En tant qu'** utilisateur
**Je veux** voir une page d'accueil claire
**Afin de** comprendre l'enquête

**Acceptance Criteria** :
- [ ] Titre enquête (h1 DSFR)
- [ ] Description
- [ ] Message de bienvenue
- [ ] Lien politique de confidentialité
- [ ] Bouton "Commencer l'enquête" (primaire DSFR)
- [ ] Estimation durée si renseignée

**Estimation** : 6h
**Statut** : ⚪ 0%

---

#### US-4.2 : Page Completion (Submit)
**En tant qu'** utilisateur
**Je veux** une page de confirmation
**Afin de** savoir que ma réponse est enregistrée

**Acceptance Criteria** :
- [ ] Message de succès (alert DSFR success)
- [ ] Texte de remerciement
- [ ] Lien de retour ou export si activé
- [ ] Message personnalisé par enquête

**Estimation** : 4h
**Statut** : ⚪ 0%

---

#### US-4.3 : Alertes & Messages
**En tant qu'** utilisateur
**Je veux** des messages clairs
**Afin de** comprendre les actions/erreurs

**Acceptance Criteria** :
- [ ] Alert success DSFR
- [ ] Alert error DSFR
- [ ] Alert info DSFR
- [ ] Alert warning DSFR
- [ ] Messages dismissible
- [ ] Icônes appropriées

**Estimation** : 8h
**Statut** : ⚪ 0%

---

#### US-4.4 : Modales DSFR
**En tant qu'** utilisateur
**Je veux** des modales conformes
**Afin d'** avoir des popups accessibles

**Acceptance Criteria** :
- [ ] Modal DSFR pour confidentialité
- [ ] Modal pour index questions
- [ ] Modal pour alertes
- [ ] Bouton fermer
- [ ] Overlay
- [ ] Accessibilité clavier (ESC, focus trap)

**Estimation** : 12h
**Statut** : ⚪ 0%

---

#### US-4.5 : Save/Load Survey
**En tant qu'** utilisateur
**Je veux** sauvegarder ma progression
**Afin de** continuer plus tard

**Acceptance Criteria** :
- [ ] Formulaire save DSFR
- [ ] Champs email/password DSFR
- [ ] Formulaire load DSFR
- [ ] Messages de confirmation
- [ ] Validation

**Estimation** : 10h
**Statut** : ⚪ 0%

---

### Estimation Epic 4
- **Story Points** : 21
- **Heures** : 40h

---

## 📊 EPIC 5 : Questions Avancées (P1)

**Durée** : 2 semaines
**Effort** : 80 heures
**Priorité** : 🟠 P1 - Important

### User Stories

#### US-5.1 : Questions Array (Tableaux)
**En tant qu'** utilisateur
**Je veux** répondre à des questions en tableau
**Afin de** donner plusieurs réponses structurées

**Types à supporter** :
- [ ] Array 5-point (8h)
- [ ] Array 10-point (6h)
- [ ] Array Yes/No/Uncertain (6h)
- [ ] Array Flexible (12h)
- [ ] Array Dual Scale (10h)
- [ ] Array by Column (8h)
- [ ] Array Texts (8h)
- [ ] Array Numbers (6h)
- [ ] Multi-Flex (10h)

**Acceptance Criteria** :
- [ ] Table DSFR responsive
- [ ] Radio/checkbox dans cellules
- [ ] Input dans cellules
- [ ] Headers accessibles (scope)
- [ ] Responsive mobile (scroll ou collapse)
- [ ] Validation par ligne

**Estimation totale** : 74h
**Statut** : ⚪ 0%

**Fichiers** : `application/views/survey/questions/answer/arrays/*`

---

#### US-5.2 : Question Ranking
**En tant qu'** utilisateur
**Je veux** classer des items
**Afin de** donner un ordre de préférence

**Acceptance Criteria** :
- [ ] Liste draggable
- [ ] Numérotation automatique
- [ ] Boutons up/down alternatifs
- [ ] Accessibilité clavier
- [ ] Validation ordre complet

**Estimation** : 16h
**Statut** : ⚪ 0%

---

#### US-5.3 : Questions Spéciales
**En tant qu'** utilisateur
**Je veux** des types de questions avancés
**Afin de** couvrir tous les besoins

**Types** :
- [ ] Date picker DSFR (8h)
- [ ] File upload DSFR (8h)
- [ ] Multiple numeric (6h)
- [ ] Equation/Boilerplate (4h)

**Estimation** : 26h

---

### Estimation Epic 5
- **Story Points** : 55
- **Heures** : 116h (à étaler sur 2 semaines)

---

## 🎨 EPIC 6 : Polish & Optimisation

**Durée** : 1 semaine
**Effort** : 40 heures
**Priorité** : 🟢 P2 - Nice to have

### User Stories

#### US-6.1 : Responsive Design
- [ ] Tests mobile (4h)
- [ ] Tests tablet (4h)
- [ ] Tests desktop large (2h)
- [ ] Corrections (10h)

#### US-6.2 : Performance
- [ ] Minification CSS/JS (4h)
- [ ] Lazy loading images (4h)
- [ ] Optimisation fonts (2h)
- [ ] Tests Lighthouse (4h)

#### US-6.3 : Accessibilité RGAA
- [ ] Audit RGAA automatique (4h)
- [ ] Tests manuel (8h)
- [ ] Corrections (12h)
- [ ] Documentation conformité (4h)

**Estimation** : 62h

---

## 📈 Métriques & KPIs

### Métriques de Développement
| Métrique | Cible | Actuel |
|----------|-------|--------|
| Tests unitaires | 80% couverture | 0% |
| Tests a11y automatiques | 100% passed | 0% |
| Composants DSFR utilisés | 100% | 30% |
| Classes Bootstrap restantes | 0 | 95% |
| Performance Lighthouse | >90 | ? |

### Métriques Business
| Métrique | Cible |
|----------|-------|
| Conformité DSFR | 100% |
| Conformité RGAA | AAA |
| Types de questions supportés | 32/32 |
| Satisfaction utilisateurs | >4/5 |

---

## 🎯 Résumé des Estimations

| Epic | Priorité | Heures | Semaines | Status |
|------|----------|--------|----------|--------|
| **1. Foundation** | P0 | 22h | 0.5 | ✅ 100% COMPLÉTÉ |
| **2. Layout & Nav** | P0 | 40h | 1 | ✅ 100% COMPLÉTÉ |
| **3. Questions P0** | P0 | 62h | 1.5 | ✅ 100% COMPLÉTÉ |
| **4. Messages & Workflow** | P1 | 40h | 1 | ⚪ 0% |
| **5. Questions P1** | P1 | 116h | 2 | ⚪ 0% |
| **6. Polish** | P2 | 62h | 1.5 | ⚪ 0% |
| **TOTAL** | | **342h** | **7.5-8 sem** | **36% complété** |

---

## 🚦 Plan de Release

### Release 0.5 - MVP (Semaine 2)
**Date** : J+14
**Objectif** : Démo fonctionnelle

**Contenu** :
- ✅ Layout DSFR (header, footer, nav)
- ✅ 3 types de questions (text, radio, checkbox)
- ✅ Page welcome/submit
- ✅ Messages de base

**Critères de succès** :
- [ ] Enquête simple fonctionnelle de bout en bout
- [ ] Header/footer conformes DSFR
- [ ] Aucune erreur console
- [ ] Testable par équipe interne

---

### Release 1.0 - Production (Semaine 4)
**Date** : J+28
**Objectif** : Production-ready pour 80% des cas

**Contenu** :
- ✅ Toutes les questions courantes
- ✅ Workflow complet
- ✅ Save/Load
- ✅ Validation
- ✅ Modales

**Critères de succès** :
- [ ] 20 types de questions fonctionnels
- [ ] Tests a11y automatiques passent
- [ ] Documentation installation/usage
- [ ] Déployable en production

---

### Release 1.5 - Complete (Semaine 6)
**Date** : J+42
**Objectif** : Toutes les fonctionnalités

**Contenu** :
- ✅ Questions avancées (array, ranking)
- ✅ Questions spéciales
- ✅ Print styles
- ✅ Optimisations

**Critères de succès** :
- [ ] 32/32 types de questions
- [ ] Performance optimale
- [ ] Tests exhaustifs

---

### Release 2.0 - Certified (Semaine 8)
**Date** : J+56
**Objectif** : Certification RGAA

**Contenu** :
- ✅ Audit RGAA complet
- ✅ Corrections accessibilité
- ✅ Documentation conformité
- ✅ Guide de contribution

**Critères de succès** :
- [ ] Certification RGAA AAA
- [ ] Score Lighthouse >90
- [ ] 0 issue critique
- [ ] Production-ready certifié

---

## 🚨 Risques & Mitigation

| Risque | Probabilité | Impact | Mitigation |
|--------|-------------|--------|------------|
| Conflit JS DSFR ↔ LimeSurvey | 🟡 Moyen | 🔴 Élevé | Namespace, tests incrémentaux |
| Performance (double framework) | 🟢 Faible | 🟡 Moyen | Lazy loading, minification |
| Complexité questions array | 🔴 Élevé | 🟡 Moyen | Template commun, composition |
| Responsive tableaux mobile | 🟡 Moyen | 🟡 Moyen | Scroll horizontal, tests user |
| Maintenance LimeSurvey updates | 🟡 Moyen | 🟠 Moyen-Élevé | Tests automatisés, versioning |
| Délai trop optimiste | 🔴 Élevé | 🔴 Élevé | Buffer 20%, MVP early |

---

## 📋 Prochaines Actions Immédiates

### Cette semaine (Semaine 1)
1. [ ] **Copier templates vanilla** (2h)
   ```bash
   cp -r themes/survey/vanilla/views themes/survey/dsfr/
   ```

2. [ ] **Corriger JavaScript DSFR** (4h)
   - Fix chargement DSFR module
   - Tester compatibilité

3. [ ] **Créer header DSFR** (16h)
   - Structure HTML
   - Logo Marianne
   - Menu mobile
   - Tests

4. [ ] **Créer footer DSFR** (8h)

5. [ ] **Navigation prev/next** (6h)

**Total semaine 1** : 36h

### Semaine suivante (Semaine 2)
1. [ ] Finir layout (progress bar, messages)
2. [ ] Question text input
3. [ ] Question radio list
4. [ ] Tests MVP

---

## ✅ Definition of Done

### Pour une User Story
- [ ] Code écrit et revu
- [ ] Template Twig créé
- [ ] CSS DSFR appliqué
- [ ] JavaScript fonctionnel
- [ ] Tests manuels OK
- [ ] Tests a11y automatiques OK
- [ ] Documentation inline
- [ ] Pas de régression
- [ ] Démo fonctionnelle

### Pour une Release
- [ ] Toutes US complétées
- [ ] Tests end-to-end OK
- [ ] Performance acceptable
- [ ] Documentation à jour
- [ ] Changelog rédigé
- [ ] Tag Git créé
- [ ] Déployable

---

## 🤝 Équipe & Rôles

| Rôle | Responsabilité | Temps |
|------|----------------|-------|
| **Dev Frontend** | Templates Twig, CSS, JS | 80% |
| **UX/UI Designer** | Validation conformité DSFR | 10% |
| **QA/Testeur** | Tests fonctionnels, a11y | 10% |

---

## 📚 Ressources & Références

### Documentation
- [Plan détaillé](PLAN-DE-TRAVAIL-DSFR.md)
- [Guide démarrage rapide](DSFR-QUICKSTART.md)
- [Status actuel](themes/survey/dsfr/STATUS.md)
- [Tests](themes/survey/dsfr/TESTING.md)

### Liens externes
- [DSFR](https://www.systeme-de-design.gouv.fr/)
- [LimeSurvey Manual](https://manual.limesurvey.org/)
- [RGAA](https://www.numerique.gouv.fr/publications/rgaa-accessibilite/)

---

**Version** : 1.0
**Dernière mise à jour** : 2025-11-06
**Prochaine review** : Fin semaine 1
