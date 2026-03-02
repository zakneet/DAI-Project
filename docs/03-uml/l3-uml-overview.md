# L3 — UML Modeling (BMAD Phase M)

## Objectif
Ce livrable traduit les exigences L2 (EF/NFR) en modèles UML structurés.

Diagrammes inclus :
1. Use Case Diagram
2. Sequence Diagram — Pré-op
3. Sequence Diagram — Per-op
4. Activity Diagram — Parcours patient
5. Class Diagram — Modèle métier

## Lien avec BMAD
- Business (B) : basé sur EF/NFR validées en L2.
- Modeling (M) : représentation formelle des scénarios.
- Architecture (A) : servira à définir les composants techniques.
- Delivery (D) : base du backlog et du développement.

## Diagrammes exportés

Les versions SVG des diagrammes sont disponibles dans :

diagrams/uml/exports/

Les fichiers source PlantUML sont disponibles dans :

diagrams/uml/source/ 

## Use Case Diagram — Description

Ce diagramme présente les interactions principales entre les acteurs (patient, anesthésiste, IADE, SSPI, IT, dispositifs, SIH) et le système DAI.

Il couvre :
- Pré-opératoire (questionnaire, validation)
- Per-opératoire (suivi temps réel, constantes)
- Post-opératoire (SSPI, score sortie)
- Administration & intégration SIH

## Sequence Diagram — Pré-opératoire

Ce diagramme décrit le flux complet du questionnaire pré-opératoire :

1. Le patient complète le questionnaire.
2. Le backend transmet les données au module IA.
3. Les scores sont calculés automatiquement.
4. Les résultats sont sauvegardés.
5. L’anesthésiste valide ou corrige les informations.

Exigences couvertes :
- EF-05 à EF-09
- NFR-01 (authentification)
- NFR-04 (traçabilité)