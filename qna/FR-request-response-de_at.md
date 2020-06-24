## Question
Wie behandle ich den Request/Response des fiskaltrust.Middlewares?

## Metadata tags
lang-de, lang-at, market-fr, middleware, PosCreator

## Answer
Wenn ein Beleg an fiskaltrust.Middleware gesendet wird, werden alle Daten vom fiskaltrust.SecurityMechanism gesichert. Daher wird die Anfrage verarbeitet und einige Sicherheitsdaten oder Daten, die nach nationalem Recht erforderlich sind, als Antwort zurückgesendet.

Zunächst muss der Beleg vom POS-System erstellt werden. Dazu müssen einige Informationen aus dem POS-System selbst und einige Header-Informationen der Quittung und Verkaufsdaten in einem JSON-Format gesammelt und übertragen werden. Nehmen wir an, es wird ein Kaffee und ein Käsekuchen an einen Kunden in einem Restaurant verkauft und mit Bargeld bezahlt.

**1) Der Header einer Quittung:**<br>Dies ist eine allgemeine Information der Quittung. Die hier gezeigten Felder sind der minimal erforderliche Datensatz. Alle möglichen Felder sind in der Middleware Dokumentation beschrieben.

```JSON
{
  "ftCashboxId": "487b7a77-fbc3-414f-8b3a-57930fb58f97",
  "ftPosSystemId": "058c4299-1657-5ad2-8ce3-fbbeb317a7b3",
  "cbTerminalId": "term01",
  "cbReceiptReference": "ticket 2020-4456",
  "cbReceiptMoment": "2020-04-05 10:49:20",
  "ftReceiptCase": "5067112530745229313",
```

**2) Die Liste der verkauften Produkte:**<br>Dies ist eine Reihe von Produktzeilen auf einem Beleg, im fiskaltrust.Universum werden dies als ChargeItems bezeichnet. Der gezeigte Datensatz ist das absolut notwendige Minimum, um den französischen Gesetzen zu entsprechen. Alle Felder und möglichen Werte sind in der Middleware Dokumentation ausführlich beschrieben.

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

**3) Wie der Beleg bezahlt wird:**<br>Im fiskaltrust.Universum heißt dieses Array PayItems. Dies ist eine Liste aller vom Kunden verwendeten Zahlungsmittel. Auch hier wird nur der obligatorische Datensatz angezeigt, weitere Informationen finden Sie in der Middleware Dokumentation.

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

Je nach verwendetem Protokoll wird die gesamte Quittung als JSON-String mit SOAP oder REST im Payload gesendet. Der Protokolltyp definiert, welche Anmeldeinformationen Sie im Header der Anforderung senden müssen. Normalerweise ist es die CashBoxID und ein AccessToken. Beide finden Sie im Konfigurationsmenü im fiskaltrust.Portal.

Der fiskaltrust.Middleware beantwortet diese Anfrage mit einer Antwort als JSON-String wie folgt:

```JSON
{
  "ftCashBoxID": "487b7a77-fbc3-414f-8b3a-57930fb58f97",
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
      "Data": "eyJhbGciOiJFUzI1NiIsInR5cCI6IkpXVCJ9...MEQCIC7YDBVwEoBqGtlMfUznu4ExAYZ3t6qph5_nIJXuOelHAiBge_EPSeCirPma881ElrNvGf2sGYfCPo5nkYZujs1P4w"
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

Die meisten dieser Informationen (fett gedruckt) müssen auf dem Beleg gedruckt werden. Es wird jedoch empfohlen, alle Informationen auszugeben. Jede vom fiskaltrust.Middleware zurückgesendete Signatur muss gedruckt werden. Daher müssen die Felder Caption und Data auf der Quittung angegeben werden. Es kann mehr als eine Signatur übermittelt werden, in diesem Fall muss jede gedruckt werden. Die Signatur mit Typ 3 enthält einen JWT als bereits codierten QR-Code im Datenfeld Data, der vor der Fußzeile des Belegs gedruckt werden muss.
