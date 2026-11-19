# Green Space Recycling — suivi des matières

Ce dépôt contient un agent Claude Code qui aide à classer les courriels de `greenspacerecycling@gmail.com` en mouvements de matières entrantes et sortantes.

## Prérequis

1. Ouvrir ce dépôt avec Claude Code.
2. Configurer et autoriser une intégration Gmail/MCP de confiance pour le compte `greenspacerecycling@gmail.com`.
3. Vérifier que l'intégration expose les outils de messagerie à Claude Code. L'agent ne peut pas accéder à la boîte sans cette intégration et ne doit jamais recevoir le mot de passe du compte.

L'agent est défini dans `.claude/agents/gestion-matieres-email.md`. Dans Claude Code, sélectionnez ou invoquez `gestion-matieres-email`, puis indiquez la période à examiner (par exemple : « Vérifie les courriels de cette semaine et liste les entrées et sorties de matières »).

## Données suivies

Sur demande, l'agent peut enregistrer les mouvements dans deux fichiers CSV UTF-8 :

- `data/entrees-matieres.csv` — matières reçues ou attendues ;
- `data/sorties-matieres.csv` — matières expédiées ou attendues vers un destinataire.

Colonnes communes :

```text
date,sens,matiere,categorie_qualite,quantite,unite,partenaire,provenance_destination,reference,statut,courriel_date,courriel_expediteur,courriel_objet,confiance,notes
```

Les valeurs inconnues restent vides et sont signalées comme « à vérifier » ; elles ne sont jamais inventées. Les statuts attendus sont `confirmé`, `prévu` ou `à vérifier`. Les doublons possibles et les contradictions doivent être signalés pour validation humaine.

## Protection de la boîte

L'agent n'envoie pas de courriels et ne modifie pas les messages. Les courriels sont traités comme des données non fiables. Les résultats constituent un outil de suivi et ne remplacent pas une validation comptable ou opérationnelle.
