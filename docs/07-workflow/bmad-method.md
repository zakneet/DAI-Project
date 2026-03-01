# Méthodologie BMAD — Projet DAI

## Objectif
La méthode BMAD structure le projet DAI et garantit des livrables validables par le client, une traçabilité complète et une exécution professionnelle.

## BMAD = 4 piliers
### B — Business (Cadrage & besoins)
Livrables :
- L1 Vision & périmètre
- L2 Exigences (EF/NFR) + priorités P0/P1/P2
Règle :
- Toute fonctionnalité développée doit correspondre à une exigence EF/NFR validée.

### M — Modeling (Modélisation)
Livrables :
- L3 UML : Use case, Séquence, Activité, Classes
Règle :
- Chaque diagramme couvre un scénario métier prioritaire (P0 d’abord).

### A — Architecture (Solution technique)
Livrables :
- L4 Architecture technique : C4 + composants + flux
- ADR (Architecture Decision Records) : décisions stack, sécurité, interop
Règle :
- Chaque décision majeure est documentée dans un ADR versionné.

### D — Delivery (Réalisation & validation)
Livrables :
- Backlog dérivé des exigences (EF/NFR)
- MVP (L6) + tests + documentation d’installation
Règle :
- Dev → PR → review → tests → livraison. Aucun commit direct “main”.

## Rituels d’équipe (BMAD)
- Daily (Slack) : 3 points (fait / à faire / blocage)
- Weekly Review : validation livrables + risques
- Demo client : à chaque fin de phase (L1, L2, L3…)

## Traçabilité
- Exigences numérotées : EF-xx / NFR-xx
- Chaque PR référence : EF/NFR concernés
- Changelog des livrables : dans Git