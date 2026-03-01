# L2 — Exigences du Projet DAI (Requirements)

## 1. Objectif
Ce document formalise les exigences du projet DAI (Dossier d’Anesthésie Intelligent) :
- Exigences Fonctionnelles (EF)
- Exigences Non Fonctionnelles (NFR)

Chaque exigence est numérotée et associée à une priorité afin de définir le MVP et le plan de livraison.

### Priorités
- P0 : obligatoire pour MVP
- P1 : important (V1/V1.1)
- P2 : amélioration (V2)

---

## 2. Exigences Fonctionnelles (EF)

### 2.1 Patient & parcours périopératoire
- EF-01 (P0) : Le système doit permettre la création, consultation et mise à jour d’un dossier anesthésique patient.
- EF-02 (P0) : Le système doit couvrir le parcours : Pré-op / Per-op / Post-op (SSPI).
- EF-03 (P0) : Le système doit gérer le suivi d’état du patient (statuts et transitions) durant le parcours.
- EF-04 (P1) : Le système doit permettre la consultation de l’historique anesthésique du patient (dans le périmètre anesthésie).

### 2.2 Pré-opératoire
- EF-05 (P0) : Le système doit permettre au patient de compléter un questionnaire pré-opératoire numérique.
- EF-06 (P0) : Le questionnaire doit couvrir au minimum : antécédents, allergies, traitements, symptômes, facteurs de risque.
- EF-07 (P0) : Le système doit calculer automatiquement des scores (ASA, RCRI, Apfel, Mallampati).
- EF-08 (P1) : Le système doit permettre à l’anesthésiste de valider/corriger les informations collectées.
- EF-09 (P1) : Le système doit afficher des alertes d’attention clinique (ex : allergies, comorbidités) nécessitant validation.

### 2.3 Per-opératoire (Bloc)
- EF-10 (P0) : Le système doit afficher une interface per-opératoire pour le suivi patient en temps quasi réel.
- EF-11 (P0) : Le système doit collecter et enregistrer les constantes vitales (FC, TA, SpO₂, EtCO₂, etc.) via dispositifs/passerelles.
- EF-12 (P0) : Le système doit permettre l’enregistrement des événements per-op (actes, médicaments, incidents).
- EF-13 (P0) : Le système doit conserver un historique horodaté des constantes et événements.
- EF-14 (P1) : Le système doit produire des alertes intelligentes (ex : hypotension prolongée) avec traçabilité (apparition, acquittement).

### 2.4 Post-opératoire (SSPI)
- EF-15 (P0) : Le système doit permettre le suivi du patient en SSPI (constantes, douleur, observations).
- EF-16 (P0) : Le système doit calculer et afficher un score de sortie SSPI (ex : Aldrete).
- EF-17 (P1) : Le système doit fournir un support postopératoire (protocoles/recommandations) avec validation clinique.

### 2.5 Documents
- EF-18 (P0) : Le système doit générer un document de synthèse anesthésique (feuille/rapport).
- EF-19 (P1) : Le document doit être exportable (PDF ou format imposé par l’établissement).
- EF-20 (P1) : Le système doit archiver et permettre la consultation des documents générés.

### 2.6 Utilisateurs & administration
- EF-21 (P0) : Le système doit gérer des rôles utilisateurs (anesthésiste, IADE, SSPI, admin).
- EF-22 (P0) : Le système doit appliquer un contrôle d’accès basé sur les rôles (RBAC).
- EF-23 (P1) : Le système doit permettre la configuration de paramètres (protocoles, seuils d’alertes, modèles de documents).

---

## 3. Exigences Non Fonctionnelles (NFR)

### 3.1 Sécurité & confidentialité
- NFR-01 (P0) : Authentification obligatoire pour tout utilisateur.
- NFR-02 (P0) : Contrôle d’accès RBAC.
- NFR-03 (P0) : Chiffrement des échanges réseau (TLS).
- NFR-04 (P0) : Journalisation des actions critiques (audit : qui/quoi/quand).
- NFR-05 (P1) : Support SSO / badges / MFA selon exigences du client.

### 3.2 Performance & temps réel
- NFR-06 (P0) : L’interface per-op doit rester réactive en continu.
- NFR-07 (P0) : Les constantes doivent être mises à jour proche du temps réel (valeur cible à valider).
- NFR-08 (P1) : Le système doit supporter plusieurs salles/patients simultanés.

### 3.3 Disponibilité & continuité
- NFR-09 (P0) : Le système doit être adapté à un environnement critique (bloc/SSPI).
- NFR-10 (P1) : Sauvegarde/restauration selon politique IT de l’hôpital.

### 3.4 Interopérabilité
- NFR-11 (P0) : Intégration avec SIH/DPI selon les modalités de l’établissement.
- NFR-12 (P1) : Données structurées et standardisées pour échange et traçabilité.

### 3.5 Exploitation & qualité
- NFR-13 (P0) : Documentation (installation, exploitation, utilisation).
- NFR-14 (P0) : Versioning Git + PR + traçabilité des changements.
- NFR-15 (P1) : Logs exploitables + supervision/monitoring.

---

## 4. Hypothèses à verrouiller avec le client
- H-01 : Liste des dispositifs biomédicaux + protocoles/formats.
- H-02 : Interfaces SIH/DPI (identité patient, admissions, documents).
- H-03 : Politique de sécurité (SSO/MFA), audit, conservation.
- H-04 : Seuils d’alertes et protocoles.
- H-05 : Liste finale des exigences P0 (MVP).

---

## 5. BMAD mapping (preuve de méthode)
- Business (B) : EF/NFR définissent le périmètre et le MVP.
- Modeling (M) : L3 UML sera dérivé des exigences P0 en priorité.
- Architecture (A) : L4 traduira EF/NFR en composants/flux techniques.
- Delivery (D) : Backlog + tests + livraisons seront liés aux EF/NFR.