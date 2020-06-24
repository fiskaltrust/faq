## Question
Comment gérer le mode dégradé ?

## Metadata tags
lang-fr, market-fr, middleware, PosCreator, PosDealer, PosOperator, Consultant

## Answer
Si le reçu ne peut pas être signé par le fiskaltrust.SecurityMechanism le POS-System doit imprimer mode dégradé sur le reçu.

Lorsque le fiskaltrust.Middleware peut à nouveau signer les reçus, tous ces reçus “dégradés” doivent être saisis (manuellement / automatiquement), envoyés au fiskaltrust.SecurityMechanism et imprimés à nouveau comme reçus normaux. Ensuite, les reçus dégradés et les nouveaux reçus doivent être archivés ensemble.

Une bonne pratique consiste à envoyer un message dans le journal technique avec le contenu suivant :

```JSON
{
  "code": 70,
  "description": "Start of degraded mode",
  "moment": "2020-03-22T06:10:52.6395741Z"
}
```

pour documenter le début du mode dégradé. Lorsque le fonctionnement normal est rétabli, le message suivant doit être envoyé au journal technique, afin de documenter également cette situation.

```JSON
{
  "code": 120,
  "description": "End of degraded mode",
  "moment": "2020-03-22T09:23:22.6015741Z"
}
```
