## Question
How to void a ticket?

## Metadata tags
lang-en, market-fr, middleware, PosCreator, PosDealer, PosOperator, Consultant

## Answer
Any data sent to the fiskaltrust.Middleware cannot be deleted afterwards. For this reason, all changes must done by sending a new receipt. In this example we use a ticket to “void”, but this can be used for any type of receipt. For example, if you bill a simple coffee for a client you must send a ticket to fiskaltrust.Middleware:

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

This is a normal request with one charge item for the coffee and one pay item for the cash payment. Please be aware that all security relevant data is masked with general words (e.g. ftCashBoxId, ftPosSystemId, …)

To continue our example, the client leaves the restaurant without paying. You now need to cancel this ticket, because you didn’t receive any payment. To accomplish this, you must send the same ticket with negative values to the fiskaltrust.Middleware.

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

Two things have to be changed on the receipt. The field ftReceiptCase stays the same than the original but gets the flag for voided ticket set. (The value 4 on position 12).

And the field cbPreviousReceiptReference should be added. The value has to be the number of the voided receipt.
