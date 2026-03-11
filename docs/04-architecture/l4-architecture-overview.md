# L4 — Architecture Technique (BMAD Phase A)

## 1. Objectif
Ce livrable définit l’architecture technique du projet DAI à partir des exigences L2 et de la modélisation L3.

Il précise :
- la stack technologique,
- les composants principaux,
- les flux d’échange,
- les principes de sécurité,
- la base de l’implémentation.

---

## 2. Lien avec BMAD
- Business (B) : exigences fonctionnelles et non fonctionnelles définies en L2.
- Modeling (M) : scénarios et modèle métier définis en L3.
- Architecture (A) : traduction en composants techniques, flux et décisions.
- Delivery (D) : base de l’implémentation logicielle et des incréments futurs.

---

## 3. Stack retenue
### Frontend
- Angular

### Backend
- Spring Boot

### Base de données
- PostgreSQL

### API
- REST API

### Sécurité
- Spring Security
- JWT (phase initiale)

### Communication temps réel
- WebSocket (phase ultérieure)

### Gestion de versions
- Git + Pull Requests

---

## 4. Vue logique de l’architecture
Le système DAI est organisé en plusieurs couches :

1. Frontend Angular
   - interface utilisateur
   - formulaires pré-op
   - vue de suivi per-op
   - consultation post-op

2. Backend Spring Boot
   - logique métier
   - API REST
   - sécurité
   - gestion des alertes
   - gestion de l’audit

3. Base PostgreSQL
   - persistance des dossiers
   - questionnaires
   - scores
   - constantes
   - événements
   - alertes
   - audit

4. Systèmes externes
   - dispositifs biomédicaux
   - SIH / DPI
   - services IA (phase avancée)

---

## 5. Principes d’architecture
- séparation frontend / backend,
- architecture modulaire,
- API centralisée,
- traçabilité des actions,
- extensibilité pour IA et interopérabilité.

---

## 6. Phasage technique
### Phase 1 — Socle
- Angular initialisé
- Spring Boot initialisé
- API REST simple
- connexion frontend/backend

### Phase 2 — MVP
- gestion patient
- dossier anesthésie
- questionnaire pré-op
- scores simulés
- affichage interface

### Phase 3 — Avancé
- monitoring per-op simulé
- alertes
- audit
- sécurité renforcée
- intégration IA
- intégration SIH simulée

---

## 7. Résultat attendu
Ce livrable servira de base :
- au cadrage technique,
- à la mise en place du code,
- au découpage du backlog,
- aux décisions d’architecture détaillées (ADR).