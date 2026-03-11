# ADR-001 — Choix de la stack technique

## Statut
Accepté

## Contexte
Le projet DAI nécessite une architecture professionnelle, modulaire et extensible pour un contexte hospitalier.

L’équipe souhaite utiliser une stack adaptée à une application web structurée avec backend robuste.

## Décision
La stack retenue est :
- Angular pour le frontend
- Spring Boot pour le backend
- PostgreSQL pour la base de données

## Justification
- Angular offre une structure adaptée aux applications complexes.
- Spring Boot fournit un socle robuste pour des API REST sécurisées.
- PostgreSQL est stable et adapté à la persistance métier.

## Conséquences
- montée en compétence nécessaire sur Angular et Spring Boot,
- besoin de démarrer par un socle technique simple,
- nécessité d’un découpage progressif du MVP.