## Question
Comment annuler un ticket ?

## Metadata tags
lang-fr, market-fr, middleware, PosCreator, PosDealer, PosOperator, Consultant

## Answer
Aucune donnée envoyée au fiskaltrust.Middleware ne peut être supprimée à postériori. Pour garantir cela, un nouveau reçu est créé pour toutes les modifications effectuées. Dans l’exemple ci-dessous, nous utilisons un ticket pour annuler, mais cela peut être utilisé pour tout type de reçu.

Exemple:<br>En facturant un simple café à un client, vous devez envoyer un ticket à fiskaltrust.Middleware.

```JSON
{
  "ftCashboxId": "cashbox-identification",
  "ftPosSystemId": "pos-system-identification",
  "cbTerminalId": "terminal-identification",
  "cbReceiptReference": "pos-action-identification",
  "cbReceiptMoment": "receipt-moment",
  "ftReceiptCase": "0x4652000000000001",
  "cbChargeItems": [
    {
      "Quantity": 1.0,
      "Description": "Café",
      "Amount": 2.2,
      "VATRate": 10.0,
      "VATAmount": 0.2,
      "ftChargeItemCase": "0x4652000000000002",
      "Moment": "moment-chargeitem",
      "ftChargeItemCaseData": "{\"NetAmount\": 2}"
    }
  ],
  "cbPayItems": [
    {
      "Quantity": 1.0,
      "Description": "Cash",
      "Amount": 2.2,
      "ftPayItemCase": "0x4652000000000001",
      "Moment": "moment-payitem"
    }
  ]
}
```

Il s’agit d’une demande correcte avec un élément de facturation pour le café et un élément de paiement pour le règlement en espèces. Veuillez noter que toutes les données relatives à la sécurité sont masquées par des mots généraux (par exemple ftCashBoxId, ftPosSystemId, …)

Maintenant, les clients quittent le restaurant sans payer. Vous devez annuler ce ticket, car vous ne recevez aucun paiement. Pour cela, vous envoyez le même ticket avec des valeurs négatives au fiskaltrust.Middleware.

```JSON
{
  "ftCashboxId": "cashbox-identification",
  "ftPosSystemId": "pos-system-identification",
  "cbTerminalId": "terminal-identification",
  "cbReceiptReference": "pos-action-identification",
  "cbReceiptMoment": "receipt-moment",
  "ftReceiptCase": "0x4652000000040001",
  "cbPreviousReceiptReference": "number of voided ticket",
  "cbChargeItems": [
    {
      "Quantity": -1.0,
      "Description": "Café",
      "Amount": -2.2,
      "VATRate": 10.0,
      "VATAmount": -0.2,
      "ftChargeItemCase": "0x4652000000000002",
      "Moment": "moment-chargeitem",
      "ftChargeItemCaseData": "{\"NetAmount\": -2}"
    }
  ],
  "cbPayItems": [
   {
      "Quantity": -1.0,
      "Description": "Cash",
      "Amount": -2.2,
      "ftPayItemCase": "0x4652000000000001",
      "Moment": "moment-payitem"
    }
  ]
}
```

Deux choses doivent être modifiées sur le reçu. Le champ ftReceiptCase reste identique à l’original mais obtient un indicateur pour l’ensemble du tickets annulé. (La valeur 4 en position 12).

Et le champ cbPreviousReceiptReference doit être ajouté. La valeur doit être le numéro du reçu annulé.
