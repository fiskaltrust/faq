## Question
Comment gérer request/reponse du fiskaltrust.Middleware ?

## Metadata tags
lang-fr, market-fr, middleware, PosCreator

## Answer
Lorsqu’un ticket est envoyé au fiskaltrust.Middleware, toutes les données sont sécurisées par le fiskaltrust.SecurityMechanism. Par conséquent, la demande est traitée et certaines données de sécurité ou données requises par la loi sont renvoyées en réponse.

Tout d’abord, le ticket doit être créé par le POS-System. Pour cela, certaines informations du POS-System lui-même ainsi que les informations d’en-tête du ticket doivent être rassemblées au format JSON. Par exemple, supposons qu’il soit vendu un café et une part de Cheesecake à un client dans un restaurant et que le paiement soit fait en espèces.

**1) L’en-tête d’un ticket :**<br>Il s’agit d’ informations générales pour le ticket lui-même. Les champs affichés ici regroupent l’ensemble des données minimum nécessaires. Tous les champs possibles sont décrits dans la documentation de l’interface.

```JSON
{
  "ftCashboxId": "487a5a77-fbc3-414f-8b3a-57930fb58f97",
  "ftPosSystemId": "058c4299-1657-4fd2-8ce3-fbbeb317a7b3",
  "cbTerminalId": "term01",
  "cbReceiptReference": "ticket 2020-4456",
  "cbReceiptMoment": "2020-04-05 10:49:20",
  "ftReceiptCase": "5067112530745229313",
```

**2) La liste des produits vendus :**<br>Il s’agit d’un tableau de lignes produits pour un ticket, dans le fiskaltrust.Univers cela s’appelle ChargeItems. L’ensemble des données présenté ci-après comprend l’ensemble des données absolument nécessaire afin d’être conforme aux lois françaises. Tous les champs et valeurs possibles sont décrits en détail dans la documentation de l’interface.

```JSON
"cbChargeItems": [
    {
      "Quantity": 1.0,
      "Description": "Café, espresso double",
      "Amount": 5.2,
      "VATRate": 20.0,
      "VATAmount": 0.87,
      "ftChargeItemCase": "5067112530745229315",
      "Moment": "2020-04-05 10:49:50",
"ftChargeItemCaseData": "{\"NetAmount\": 4.33}"
   },
    {
      "Quantity": 1.0,
      "Description": "Cheescake",
      "Amount": 7.9,
      "VATRate": 20.0,
      "VATAmount": 1.32,
      "ftChargeItemCase": "5067112530745229315",
      "Moment": "2020-04-05 10:49:50",
      "ftChargeItemCaseData": "{\"NetAmount\": 6.58}"
    }
  ],
```

**3) Comment le ticket est payé:**<br>Dans le fiskaltrust.Univers, ce tableau est appelé PayItems. Il s’agit d’une liste de tous les moyens de paiement pouvant être utilisés par un client. Dans l’exemple ci-dessous, seul les données obligatoires est affichées, plus d’informations peuvent être trouvées dans la documentation de l’interface.

```JSON
  "cbPayItems": [
    {
      "Quantity": 1.0,
      "Description": "Cash",
      "Amount": 13.1,
      "ftPayItemCase": "5067112530745229313",
      "Moment": "2020-04-05 10:50:20"
    }
  ]
}
```

En fonction du protocole utilisé, le ticket entier est envoyé dans le payload sous forme de JSON-String avec SOAP ou REST. Le type de protocole définit les informations d’identification que vous devez envoyer dans l’en-tête de la demande. Il s’agit généralement du CashBoxID et d’un AccessToken. Les deux peuvent être trouvés dans le [menu Configuration](https://portal.fiskaltrust.fr/CashBox) du fiskaltrust.Portail.

Le fiskaltrust.Middleware répondra à cette demande avec une réponse sous forme de JSON-String comme ceci:

```
{
  "ftCashBoxID": "487a5a77-fbc3-414f-8b3a-57930fb58f97",
  "ftQueueID": "0f68a617-c0cd-4249-9c48-c48da217ff77",
  "ftQueueItemID": "d4bfd2b0-973f-4e1a-90de-c63884cde8db",
  "ftQueueRow": 298886,
  "cbTerminalID": "term01",
  "cbReceiptReference": "posAction444",
  "ftCashBoxIdentification": "RueHelder_1(2)",
  "ftReceiptIdentification": "ft48F82#T293614",
  "ftReceiptMoment": "2020-04-05T11:03:58.4319402Z",
  "ftSignatures": [
    {
      "ftSignatureFormat": 3,
      "ftSignatureType": 5067112530745229313,
      "Caption": "www.fiskaltrust.fr",
      "Data": "eyJhbGciOiJFUzI1NiIsInR5cCI6IkpXVCJ9.::.MEQCIC7YDBVwEoBqGtlMfUznu4ExAYZ3t6qph5_nIJXuOelHAiBge_EPSeCirPma881ElrNvGf2sGYfCPo5nkYZujs1P4w"
    },
    {
      "ftSignatureFormat": 1,
      "ftSignatureType": 5067112530745229312,
      "Caption": "S A N D B O X",
      "Data": "0f68a617-c0cd-4249-9c48-c48da217ff77"
    }
],
  "ftState": 5067112530745229312
}
```
La plupart des informations doivent être imprimées sur le ticket, mais le mieux consiste néanmoins à tout imprimer. Chaque signature renvoyée par le fiskaltrust.Middleware doit être imprimée. Par conséquent, les champs Caption et Data doivent obligatoirement apparaître sur le ticket. Il peut y avoir plusieurs signatures. Si cela se produit, chaque signature doit être imprimée. La signature avec le type 3 contient un JWT sous la forme d’un QR-Code déjà encodé dans le champ de données; celui-ci doit être imprimé sur le ticket avant le pied de page.
