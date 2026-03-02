# L3 — UML Modeling (BMAD Phase M)

## 1. Objectif
Ce livrable traduit les exigences L2 (EF/NFR) en modèles UML structurés afin de :
- clarifier les scénarios métiers et interactions,
- sécuriser la compréhension commune (client ↔ équipe),
- préparer l’architecture (L4) et le développement (L6).

Diagrammes inclus :
1. Use Case Diagram
2. Sequence Diagram — Pré-op
3. Sequence Diagram — Per-op
4. Activity Diagram — Parcours patient
5. Class Diagram — Modèle métier

---

## 2. Lien avec BMAD
- **Business (B)** : basé sur EF/NFR validées en L2.
- **Modeling (M)** : modélisation UML (cas d’usage, scénarios, données).
- **Architecture (A)** : servira à définir composants, flux, intégration, sécurité (L4).
- **Delivery (D)** : servira à dériver le backlog, tests et livraisons (L6).

---

## 3. Organisation des fichiers
### Diagrammes exportés
Les versions SVG des diagrammes sont disponibles dans :
- `diagrams/exports/`

### Sources PlantUML
Les fichiers source PlantUML sont disponibles dans :
- `diagrams/uml/source/`

---

## 4. Use Case Diagram — Explication (vue métier)
### Objectif
Le Use Case Diagram présente **les acteurs** (utilisateurs et systèmes externes) et **les fonctionnalités principales** offertes par DAI.

### Acteurs
- **Patient** : remplit le questionnaire pré-op.
- **Anesthésiste** : consulte et valide le dossier pré-op, décide et génère le rapport.
- **IADE** : suit le patient au bloc (per-op), enregistre médicaments/actes/événements.
- **Équipe SSPI** : assure le suivi post-op et la sortie (score).
- **Admin IT** : gère utilisateurs/rôles et paramètres (seuils, protocoles).
- **Dispositifs biomédicaux** : source des constantes vitales.
- **SIH/DPI** : identité patient, intégration et export documentaire.

### Couverture fonctionnelle
- Pré-opératoire : questionnaire, scores, validation
- Per-opératoire : suivi temps réel, constantes, alertes, traçabilité
- Post-opératoire : SSPI, score de sortie, synthèse
- Administration & intégration SIH

---

## 5. Sequence Diagram — Pré-opératoire (Questionnaire + IA + Validation)
### Flux (pas à pas)
1. Le patient accède au questionnaire pré-op.
2. Le backend fournit le questionnaire (modèle et structure).
3. Le patient soumet ses réponses.
4. Le backend déclenche le calcul automatique des scores via module IA / moteur de règles.
5. Le système sauvegarde réponses, scores et alertes potentielles.
6. L’anesthésiste consulte le dossier et **valide/corrige** les informations (validation clinique obligatoire).

### Exigences couvertes
- EF-05 à EF-09
- NFR-01 (authentification)
- NFR-04 (audit/traçabilité)

---

## 6. Sequence Diagram — Per-opératoire (Bloc / temps réel)
### Flux (pas à pas)
1. L’IADE ouvre une session per-op pour le patient.
2. Les dispositifs biomédicaux envoient les constantes via une passerelle.
3. Le backend enregistre chaque mesure horodatée.
4. Le moteur d’alertes évalue les seuils en continu.
5. Si anomalie : alerte créée (ACTIVE) et affichée en temps réel.
6. L’IADE saisit les événements (médicaments/incidents/actes).
7. L’IADE acquitte l’alerte (ACK) avec traçabilité (qui/quand/commentaire).
8. Résilience : gestion d’une perte de flux dispositif (warning + événement technique).
9. Clôture de la session per-op.

### Exigences couvertes
- EF-10 à EF-14
- NFR-06 / NFR-07 (performance & temps quasi réel)
- NFR-04 (audit/traçabilité)

---

## 7. Activity Diagram — Parcours patient global (processus)
### Objectif
Représenter le **workflow clinique global** du patient sur les 3 phases : pré-op, per-op, post-op.

### Flux (résumé)
1. Sélection/création patient et dossier anesthésie.
2. Pré-op : questionnaire → scores → alertes → validation anesthésiste.
3. Per-op : démarrage session → monitoring temps réel → événements/médicaments → alertes + acquittement → fin bloc.
4. Post-op (SSPI) : suivi → douleur → score Aldrete → décision de sortie.
5. Génération du rapport anesthésique et archivage.

### Exigences couvertes (vue globale)
- EF-01 à EF-20 (selon périmètre MVP) + NFR-04 (traçabilité)

---

## 8. Class Diagram — Modèle métier (domain model)
### Objectif
Définir les entités principales et leurs relations afin de guider :
- la conception BD,
- l’API backend,
- l’architecture (L4),
- l’audit et la traçabilité.

### Entités principales (résumé)
- Patient, AnesthesiaCase (dossier anesthésie)
- PreOpQuestionnaire, QuestionnaireResponse
- ClinicalScore (ASA/RCRI/Apfel/Mallampati/Aldrete)
- PerOpSession, VitalSignMeasurement, Device
- Event, MedicationAdministration
- Alert (ACTIVE/ACK/RESOLVED)
- PostOpStay, AnesthesiaReport
- User, AuditLog

### Exigences couvertes
- EF (structure des données) + NFR-04 (audit/traçabilité)

---

## 9. Traçabilité L2 → L3 (BMAD)
- Use Case : vue globale des EF (modules et acteurs).
- Séquence Pré-op : EF-05..EF-09.
- Séquence Per-op : EF-10..EF-14.
- Activity : enchaînement des phases et transitions (parcours complet).
- Class Diagram : modèle de données supportant EF/NFR (traçabilité, audit).

Ce livrable L3 constitue l’entrée directe du livrable L4 (Architecture) : composants, flux et intégrations seront déduits de ces modèles.