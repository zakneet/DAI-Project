# L5a — Questionnaire & Scoring Domain Model

## 1. Objectif
Ce document transforme les fiches préanesthésiques du client et le document de scores en modèle métier exploitable pour le backend DAI.

Il servira à :
- définir les sections du questionnaire,
- structurer les données backend,
- identifier les règles de calcul des scores,
- préparer les modules Spring Boot.

---

## 2. Sources métier utilisées
- Fiche préanesthésique patient (français)
- Fiche préanesthésique patient (arabe)
- Document de scores cliniques
- Dossier d’architecture DAI

---

## 3. Sections métier du questionnaire préanesthésique

### 3.1 Identité & contexte opératoire
- Nom / prénom
- Âge
- Nature de l’acte
- Poids
- Taille

### 3.2 Antécédents médicaux
- HTA
- Asthme
- AVC
- Diabète
- Insuffisance rénale
- Épilepsie
- Dyslipidémie
- Anémie
- Troubles psychiatriques
- Cardiopathie
- Ulcère gastrique
- Endocrinopathie
- Autres maladies

### 3.3 Néphrologie / dialyse
- Dialyse
- Jours de dialyse
- Fistule artério-veineuse
- Localisation fistule

### 3.4 Traitements en cours
- Médicaments actuels
- Posologie
- Horaire de prise

### 3.5 Antécédents chirurgicaux / anesthésiques
- Opérations antérieures
- Date
- Type d’anesthésie
- Autres actes anesthésiques
- Complications d’anesthésie antérieures
- Hospitalisations antérieures

### 3.6 Allergies & habitudes
- Allergies médicamenteuses
- Tabac
- Nombre de cigarettes / jour
- Nombre d’années tabagisme
- Alcool

### 3.7 Risque hémorragique
- Saignements répétés
- Temps prolongé d’arrêt du saignement
- Ecchymoses spontanées
- Saignement anormal lors d’une chirurgie / extraction
- Transfusion antérieure

### 3.8 Antécédents familiaux
- Trouble de coagulation
- Maladie musculaire héréditaire
- Complication anesthésique familiale

### 3.9 Capacité fonctionnelle / effort
- Monter deux étages
- Monter un étage
- Dyspnée à l’effort
- Douleur thoracique à l’effort
- Questions de capacité fonctionnelle type Duke

### 3.10 Sommeil / SAOS
- Ronflement
- Apnées observées
- Somnolence diurne

### 3.11 Signes complémentaires
- Palpitations
- Vertiges
- Prothèse dentaire
- Problèmes du rachis
- Tension artérielle habituelle

### 3.12 Autonomie
- Se nourrit seul
- S’habille seul
- Se déplace à domicile
- Marche terrain plat
- Monte escalier
- Court courte distance

### 3.13 Questionnaires de satisfaction
- Satisfaction patient
- Satisfaction médecin anesthésiste

---

## 4. Entités métier à créer dans le backend

### 4.1 Entités principales
- Patient
- AnesthesiaCase
- PreAnesthesiaQuestionnaire
- QuestionnaireSection
- Question
- Answer
- Medication
- Allergy
- SurgicalHistory
- FamilyHistory
- FunctionalAssessment
- SleepAssessment
- BleedingRiskAssessment
- ClinicalScore
- ScoreResult

---

## 5. Mapping questionnaire → objets backend

### 5.1 Patient
Contient :
- identité de base
- âge / sexe
- poids / taille

### 5.2 AnesthesiaCase
Contient :
- acte prévu
- statut pré-op / per-op / post-op
- lien avec Patient

### 5.3 PreAnesthesiaQuestionnaire
Contient :
- toutes les sections du questionnaire
- date de soumission
- version langue
- statut validation

### 5.4 Answer
Contient :
- questionCode
- valeur
- type (bool, texte, nombre, choix)
- horodatage

### 5.5 ClinicalScore / ScoreResult
Contient :
- nom du score
- valeur calculée
- interprétation
- détail de calcul
- date de calcul

---

## 6. Scores à supporter dans le moteur de calcul
- Duke / METs
- Lee / RCRI
- STOP-BANG
- Apfel
- Child-Pugh
- NYHA
- CHA2DS2-VASc
- ARISCAT
- ASA (à définir par logique clinique validée)
- Mallampati (si saisie manuelle ou classification dédiée)

---

## 7. Règles backend à prévoir
- Une réponse du questionnaire peut alimenter plusieurs scores.
- Un score doit conserver son détail de calcul.
- Un score doit être recalculable après modification d’une réponse.
- La validation finale revient toujours au médecin.
- Les questionnaires arabe et français doivent partager le même modèle métier.

---

## 8. Décision de structuration backend
Les modules backend à créer ensuite seront :
- patient
- casefile
- questionnaire
- scoring
- preop
- shared
- config
- audit

---

## 9. Résultat attendu
Ce document sert de base immédiate pour :
- la vraie structure Spring Boot,
- la modélisation des entités JPA,
- la création du moteur de scores,
- l’intégration BMAD côté code.