## Question
Qu’est-ce qu’un “stop receipt” (reçu de clôture) ?

## Metadata tags
lang-fr, market-all, middleware, PosCreator, PosDealer, PosOperator, Consultant

## Answer
Le _stop receipt_ est requis pour la mise hors fonction programmée des mécanismes de sécurité et / ou des caisses enregistreuses. Le stop receipt permet de désactiver: le chainage des tickets, la numérotation séquentielle et le stockage des totaux. Il clôture également le journal de collecte des données.

Ce reçu a une réponse significative du fiskaltrust.SecurityMechanism seulement la première fois afin d’arrêter les calculs opérationnels et le fonctionnement d’une queue. Après avoir reçu un accusé de réception, la queue sera fermée. Il n’y aura pas de réponse positive de la caisse enregistreuse lorsqu’un reçu est envoyé à une queue fermée.

Une queue fermée ne peut pas être rouverte avec un _start receipt_. Au lieu de cela, une nouvelle queue doit être générée et initialisée avec un _start receipt_.
