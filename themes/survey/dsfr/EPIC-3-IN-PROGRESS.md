# 🚧 EPIC 3 : Questions Prioritaires (P0) - EN COURS

**Date de démarrage** : 6 novembre 2025
**Durée estimée** : 62 heures
**Statut** : 🟡 En cours (~10% complété)

---

## 📋 User Stories

### ✅ US-3.1 : Question Texte Court (ShortFreeText)
**Statut** : 100% ✅

**Fichiers créés** :
- `themes/survey/dsfr/survey/questions/answer/shortfreetext/text/item.twig`

**Composants DSFR utilisés** :
- `fr-input` - Input texte DSFR
- `fr-input-group` - Groupe d'input

**Résultat** :
- Input texte court avec style DSFR
- Support prefix/suffix
- Placeholder
- Maxlength
- Accessible

---

### ✅ US-3.2 : Question Texte Long (Textarea)
**Statut** : 100% ✅

**Fichiers créés** :
- `themes/survey/dsfr/survey/questions/answer/shortfreetext/textarea/item.twig`

**Composants DSFR utilisés** :
- `fr-input` - Textarea DSFR
- `fr-input-group` - Groupe d'input

**Résultat** :
- Textarea avec style DSFR
- Support prefix/suffix
- Rows configurables
- Maxlength
- Accessible

---

### ⚪ US-3.3 : Question Numérique
**Statut** : 0% - À faire

**Fichiers à créer** :
- `themes/survey/dsfr/survey/questions/answer/numerical/item.twig`

---

### ⚪ US-3.4 : Question Radio List
**Statut** : 0% - À faire

**Fichiers à créer** :
- `themes/survey/dsfr/survey/questions/answer/listradio/answer.twig`
- `themes/survey/dsfr/survey/questions/answer/listradio/rows/answer_row.twig`

**Composants DSFR à utiliser** :
- `fr-fieldset` - Groupe de radios
- `fr-radio-group` - Radio button DSFR
- `fr-label` - Label

---

### ⚪ US-3.5 : Question Checkbox List
**Statut** : 0% - À faire

**Fichiers à créer** :
- `themes/survey/dsfr/survey/questions/answer/multiplechoice/answer.twig`
- `themes/survey/dsfr/survey/questions/answer/multiplechoice/rows/answer_row.twig`

**Composants DSFR à utiliser** :
- `fr-fieldset` - Groupe de checkboxes
- `fr-checkbox-group` - Checkbox DSFR
- `fr-label` - Label

---

### ⚪ US-3.6 : Question Dropdown
**Statut** : 0% - À faire

---

### ⚪ US-3.7 : Question Yes/No
**Statut** : 0% - À faire

---

### ⚪ US-3.8 : Container de Question
**Statut** : 0% - À faire

---

## 📊 Progression EPIC 3

| User Story | Priorité | Statut | Heures |
|------------|----------|--------|--------|
| US-3.1 : Texte Court | P0 | ✅ 100% | 8h |
| US-3.2 : Texte Long (Textarea) | P0 | ✅ 100% | 6h |
| US-3.3 : Numérique | P0 | ⚪ 0% | 6h |
| US-3.4 : Radio List | P0 | ⚪ 0% | 12h |
| US-3.5 : Checkbox List | P0 | ⚪ 0% | 12h |
| US-3.6 : Dropdown | P0 | ⚪ 0% | 8h |
| US-3.7 : Yes/No | P0 | ⚪ 0% | 4h |
| US-3.8 : Container | P0 | ⚪ 0% | 6h |
| **TOTAL** | | **~23%** | **62h** |

---

## 📁 Structure des Templates

Les templates de questions dans LimeSurvey suivent cette structure :
```
application/views/survey/questions/answer/
├── shortfreetext/
│   ├── text/
│   │   └── item.twig
│   └── textarea/
│       └── item.twig
├── longfreetext/
│   └── item.twig
├── numerical/
│   └── item.twig
├── listradio/
│   ├── answer.twig
│   └── rows/
│       └── answer_row.twig
└── multiplechoice/
    ├── answer.twig
    └── rows/
        └── answer_row.twig
```

Pour le thème DSFR, nous créons des overrides dans :
```
themes/survey/dsfr/survey/questions/answer/
```

---

## 🎨 Composants DSFR Utilisés

### Pour les inputs
- `fr-input` - Input/textarea
- `fr-input-group` - Groupe d'input
- `fr-label` - Label
- `fr-hint-text` - Texte d'aide
- `fr-error-text` - Message d'erreur

### Pour les radios/checkboxes
- `fr-fieldset` - Fieldset
- `fr-fieldset__legend` - Légende
- `fr-radio-group` - Radio
- `fr-checkbox-group` - Checkbox

### Pour les selects
- `fr-select` - Select DSFR
- `fr-select-group` - Groupe select

---

## 📝 Notes Techniques

### Variables LimeSurvey disponibles
- `$name` - Nom du champ
- `$ia[1]` - ID de la question
- `$dispVal` - Valeur affichée
- `$placeholder` - Placeholder
- `$maxlength` - Longueur max
- `$prefix` - Préfixe
- `$suffix` - Suffixe
- `$kpclass` - Classes supplémentaires
- `$basename` - Nom de base pour aria-labelledby

### Bonnes pratiques
1. Toujours utiliser `aria-labelledby` pour l'accessibilité
2. Utiliser `fr-input` au lieu de `form-control`
3. Wrapper dans `fr-input-group`
4. Support prefix/suffix avec classes DSFR
5. Garder la compatibilité avec les variables LimeSurvey

---

## 🎯 Prochaines Étapes

1. ✅ Texte court (input) - FAIT
2. ✅ Textarea - FAIT
3. ⚪ Numérique
4. ⚪ Radio list
5. ⚪ Checkbox list
6. ⚪ Dropdown
7. ⚪ Yes/No
8. ⚪ Container

---

## ✅ Validation

### Tests à effectuer
- [ ] Input texte court s'affiche correctement
- [ ] Textarea fonctionne avec plusieurs lignes
- [ ] Prefix/suffix affichés correctement
- [ ] Maxlength respecté
- [ ] Placeholder visible
- [ ] Accessibilité (aria-labelledby)
- [ ] Responsive

---

**Dernière mise à jour** : 6 novembre 2025
**Prochaine action** : Continuer avec US-3.3 (Numérique)
