# L1 — Vision & Périmètre du Projet DAI (Dossier d’Anesthésie Intelligent)

## 1. Contexte

Le projet DAI vise à moderniser, sécuriser et structurer le suivi anesthésique en milieu hospitalier en couvrant l’ensemble du parcours périopératoire (pré-opératoire, per-opératoire et post-opératoire).  
Le système est destiné à une intégration en établissement de santé, avec des exigences élevées en matière de traçabilité, de sécurité, de disponibilité et d’interopérabilité.

---

## 2. Objectifs du projet

### 2.1 Objectif général

Mettre en place une plateforme DAI capable de :

- Centraliser les informations du patient liées à l’anesthésie.
- Automatiser la collecte et la structuration des données (questionnaires, constantes vitales).
- Assister les équipes médicales via des fonctionnalités d’intelligence artificielle (aide à la décision, calcul de scores, détection d’anomalies).
- Générer des documents anesthésiques standardisés.
- Permettre l’intégration avec les systèmes hospitaliers existants.

### 2.2 Objectifs spécifiques

- Réduire les erreurs de saisie et améliorer la traçabilité.
- Accélérer la préparation pré-opératoire via un questionnaire numérique intelligent.
- Assurer un suivi patient en temps réel en environnement périopératoire (bloc opératoire / SSPI).
- Détecter des anomalies cliniques (ex : hypotension prolongée) et produire des alertes.
- Standardiser les données cliniques selon une approche interopérable.

---

## 3. Périmètre fonctionnel (Scope)

### 3.1 Inclus dans le périmètre (IN)

#### A) Pré-opératoire

- Collecte des informations patient via questionnaire numérique (symptômes, antécédents, allergies, traitements).
- Calcul automatique de scores d’évaluation périopératoire (ASA, RCRI, Apfel, Mallampati).
- Assistance à la décision avec recommandations nécessitant validation médicale.

#### B) Per-opératoire (Bloc)

- Suivi des étapes et de l’état du patient au bloc opératoire.
- Collecte des constantes vitales (fréquence cardiaque, tension artérielle, SpO₂, EtCO₂, etc.) depuis dispositifs biomédicaux ou passerelles.
- Enregistrement des événements, médicaments et actes liés à l’anesthésie.
- Génération d’alertes intelligentes avec traçabilité.

#### C) Post-opératoire (SSPI)

- Suivi du patient en salle de surveillance post-interventionnelle.
- Calcul et affichage du score de sortie (ex : score d’Aldrete).
- Génération d’un rapport de synthèse anesthésique.

#### D) Données et traçabilité

- Stockage structuré des données patient liées à l’anesthésie.
- Journalisation des actions utilisateurs (traçabilité : qui a fait quoi et quand).

---

### 3.2 Hors périmètre (OUT) — à confirmer avec le client

- Gestion complète du dossier médical global (hors anesthésie).
- Gestion administrative hospitalière (facturation, ressources humaines, etc.).
- Remplacement total du système d’information hospitalier (SIH) existant.
- Intégration de dispositifs biomédicaux non validés par l’établissement.

---

## 4. Parties prenantes (Acteurs)

- Patient (questionnaire pré-opératoire).
- Anesthésiste (validation, décision, prescriptions).
- IADE / Infirmier anesthésiste (suivi per-opératoire).
- Équipe SSPI (suivi post-opératoire).
- Administrateur / IT hospitalier (sécurité, intégration).
- Systèmes hospitaliers (SIH) et équipements biomédicaux.

---

## 5. Contraintes & exigences non-fonctionnelles (Résumé)

- Sécurité : authentification forte, contrôle d’accès, chiffrement des échanges, journalisation.
- Disponibilité : système utilisable en environnement critique.
- Performance : affichage quasi temps réel des données per-opératoires.
- Interopérabilité : échanges standardisés avec systèmes externes.
- Traçabilité : conservation et audit des actions utilisateurs.

---

## 6. Indicateurs de réussite (KPI)

- Réduction des erreurs de saisie manuelle.
- Réduction du temps moyen de préparation pré-opératoire.
- Amélioration de la complétude des dossiers anesthésiques.
- Taux de disponibilité du système.
- Niveau de satisfaction des utilisateurs.

---

## 7. Hypothèses & points à valider avec le client

- Liste précise des dispositifs biomédicaux connectés.
- Modalités d’intégration avec le SIH / DPI.
- Politique de sécurité (SSO, badges, MFA).
- Définition du périmètre MVP (modules livrés en première version).

---

## 8. Résultat attendu du Livrable L1

Le présent document formalise la vision, le périmètre et les objectifs du projet DAI.  
Il constitue la base des livrables suivants :

- L2 : Exigences détaillées.
- L3 : Conception UML.
- L4 : Architecture technique.
- L5 : Maquettes UI/UX.
- L6 : Prototype fonctionnel (MVP).
