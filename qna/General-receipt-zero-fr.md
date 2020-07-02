## Question
Qu’est-ce qu’un “zero receipt” (reçu zéro) ?

## Metadata tags
lang-fr, market-all, middleware, PosCreator, PosDealer, PosOperator, Consultant

## Answer
Un zero receipt est un support et un stockage de données universels. La caisse enregistreuse envoie un reçu avec un bloc d’articles vide (_ftChargeItem_) et un bloc de paiement vide (_ftPayItem_) qui contiennent logiquement un montant total de “0”.

Le fiskaltrust.SecurityMechanism envoie les blocs nécessaires dans la réponse, tels que l’en-tête du reçu, le bloc d’articles et le bloc de signature. Cette réponse est imprimée ou publiée électroniquement et doit être archivée.

Par exemple, un reçu d’ouverture ou de clôture sont des cas particuliers de zero receipt.
