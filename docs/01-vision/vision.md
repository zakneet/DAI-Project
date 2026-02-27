# L1 — Vision & Périmètre du Projet DAI (Dossier d’Anesthésie IA)

## 1. Contexte
Le projet DAI vise à moderniser et sécuriser le suivi anesthésique en milieu hospitalier en couvrant l’ensemble du parcours périopératoire (pré-opératoire, per-opératoire, post-opératoire).  
Le système cible une intégration en établissement de santé, avec des exigences élevées en matière de traçabilité, sécurité, disponibilité et interopérabilité.

## 2. Objectifs du projet
### 2.1 Objectif général
Mettre en place une plateforme DAI qui :
- centralise les informations du patient liées à l’anesthésie,
- automatise la collecte et la structuration des données (questionnaires, constantes),
- assiste les équipes médicales via des fonctionnalités d’IA (aide au tri, scores, alertes),
- permet la génération de documents et l’intégration aux systèmes hospitaliers.

### 2.2 Objectifs spécifiques
- Réduire les erreurs de saisie et améliorer la traçabilité.
- Accélérer la préparation pré-opératoire par questionnaire intelligent.
- Suivre les patients en temps réel en environnement périopératoire (bloc/SSPI).
- Détecter des anomalies (ex: hypotension prolongée) et produire des alertes.
- Standardiser les données cliniques (approche orientée ressources et interopérabilité).

## 3. Périmètre fonctionnel (Scope)
### 3.1 Inclus dans le périmètre (IN)
#### A) Pré-opératoire
- Collecte des informations patient via questionnaire numérique (symptômes, antécédents, allergies, traitements).
- Calcul et affichage de scores pertinents (ex: ASA, RCRI, Apfel, Mallampati).Ces quatre termes désignent des scores d'évaluation périopératoire utilisés en anesthésie pour stratifier les risques d'un patient avant une chirurgie. 
ASA (American Society of Anesthesiologists) : Évalue l'état physique général et les comorbidités du patient sur une échelle de 1 (patient sain) à 6 (mort cérébrale).
RCRI (Revised Cardiac Risk Index) : Aussi appelé score de Lee, il estime le risque de complications cardiaques (infarctus, arrêt cardiaque) pour une chirurgie non cardiaque.
Apfel : Prédit la probabilité de nausées et vomissements postopératoires (NVPO) en fonction de 4 critères : sexe féminin, non-fumeur, antécédents de NVPO/mal des transports et usage de morphiniques.
Mallampati : Évalue la visibilité des structures oropharyngées pour prédire la difficulté d'intubation (classes 1 à 4)
- Aide à la décision : recommandations et signaux d’alerte nécessitant validation clinique.

#### B) Per-opératoire (Bloc)
- Suivi du patient (état/étapes) dans le bloc.
- Collecte des constantes vitales (fréquence cardiaque, tension artérielle, SpO₂, EtCO₂, etc.) depuis dispositifs / passerelles.
- Enregistrement des événements, médicaments et actes liés à l’anesthésie.
- Alertes intelligentes (ex: hypotension prolongée) avec traçabilité.

#### C) Post-opératoire (SSPI)
- Suivi du patient en SSPI.
- Calcul/affichage de score de sortie (ex: Aldrete) et suivi douleur.
- Génération d’un rapport / document de synthèse anesthésique.

#### D) Données & traçabilité
- Stockage structuré des données patient et anesthésie.
- Journalisation des actions et traçabilité minimale (qui a fait quoi, quand).

### 3.2 Hors périmètre (OUT) — à confirmer avec le client
- Gestion complète du dossier médical global (hors anesthésie).
- Gestion administrative hospitalière complète (facturation, RH, etc.).
- Remplacement total du SIH existant.
- Dispositifs biomédicaux non compatibles / non autorisés par l’hôpital (à valider).

## 4. Parties prenantes (acteurs)
- Patient (répond au questionnaire pré-op)
- Anesthésiste (validation, décision, prescriptions)
- IADE / Infirmier anesthésiste (suivi per-op, saisie/validation)
- Équipe SSPI (post-op)
- Administrateur / IT hospitalier (sécurité, comptes, intégration)
- Systèmes hospitaliers (SIH) et équipements biomédicaux (sources de données)

## 5. Contraintes & exigences non-fonctionnelles (résumé)
- Sécurité : authentification, contrôle d’accès, journalisation, chiffrement des échanges.
- Disponibilité : service utilisable en environnement critique.
- Performance : écran per-op doit rester réactif (données quasi temps réel).
- Interopérabilité : échanges standardisés avec systèmes externes (à spécifier en L4).
- Traçabilité : conservation et audit des actions utilisateur.

## 6. Indicateurs de réussite (KPI) — proposés
- Diminution des erreurs de saisie manuelle (objectif à définir)
- Temps moyen de préparation pré-op réduit
- Complétude des dossiers anesthésie
- Disponibilité du système (objectif à définir)
- Acceptabilité utilisateur (retour terrain)

## 7. Hypothèses & points à valider avec le client
- Liste exacte des dispositifs biomédicaux connectés et formats disponibles.
- Modalités d’intégration aux systèmes hospitaliers (SIH / DPI / identité patient).
- Politique de sécurité (SSO, badges, MFA) et exigences réglementaires locales.
- Périmètre MVP : modules livrés en première version.

## 8. Résultat attendu du Livrable L1
Le présent document formalise la vision, le périmètre et les objectifs du projet DAI et servira de base à :
- L2 : exigences détaillées (fonctionnelles / non-fonctionnelles),
- L3 : conception UML,
- L4 : architecture technique,
- L5 : maquettes UI,
- L6 : prototype / MVP.