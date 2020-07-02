## Question
Wie kann ein Beleg storniert werden?

## Metadata tags
lang-at, lang-de, market-fr, middleware, PosCreator, PosDealer, PosOperator, Consultant

## Answer
An fiskaltrust.Middleware gesendete Daten können anschließend nicht mehr gelöscht werden. Hierzu müssen alle Änderungen durch Senden eines neuen Belegs vorgenommen werden. In diesem Beispiel wird ein Kassenbon (Ticket) zum Stornieren verwendet, dieses Beispiel kann jedoch für jede Art von Beleg adaptiert werden. Wenn Sie beispielsweise einem Kunden einen einfachen Kaffee in Rechnung stellen, müssen Sie einen Kassenbon an den fiskaltrust.Middleware senden:

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

Dies ist eine normale Anfrage mit einem ChargeItem für den Kaffee und einem PayItem für die Barzahlung. Bitte beachten Sie, dass alle sicherheitsrelevanten Daten mit allgemeinen Wörtern ersetzt wurden (z. B. ftCashBoxId, ftPosSystemId, …).
Jetzt verlässt der Kunde das Restaurant ohne Bezahlung. Sie müssen diesen Kassenbon stornieren, da Sie keine Zahlung erhalten haben. Dazu senden Sie das gleiche Ticket mit negativen Werten an den fiskaltrust.Middleware.

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

Zwei Dinge müssen auf der Quittung geändert werden. Der Inhalt des Felds ftReceiptCase bleibt der gleiche wie beim Originalbeleg, erhält jedoch das Flag für einen stornierten Beleg. (Der Wert 4 auf Position 12).
Und das Feld cbPreviousReceiptReference sollte hinzugefügt werden. Der Wert ist die Nummer der Original-Quittung.
