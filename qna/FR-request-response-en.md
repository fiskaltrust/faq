## Question
How to handle the request/response of the fiskaltrust.Middleware?

## Metadata tags
lang-en, market-fr, middleware, PosCreator

## Answer
When a ticket is sent to the fiskaltrust.Middleware, all of the data is secured by the fiskaltrust.SecurityMechanism. Therefore the request is processed and some security data or data required by national laws is sent back as response.

To begin the process, a receipt needs to be created by the POS-System. To accomplish this, some information from the POS-System itself and some information from the header of the receipt has to be gathered in a JSON-format.

See the below example assuming a coffee and a cheesecake is sold to a client in a restaurant and the bill is paid with cash.

**1) The header of a receipt:**<br>This is general information for the receipt itself. The fields shown here are the minimal data set necessary. All possible fields are described in the middleware documentation.

```JSON
{
  "ftCashboxId": "487b7a77-fbc3-414f-8b3a-57930fb58f97",
  "ftPosSystemId": "058c4299-1657-5ad2-8ce3-fbbeb317a7b3",
  "cbTerminalId": "term01",
  "cbReceiptReference": "ticket 2020-4456",
  "cbReceiptMoment": "2020-04-05 10:49:20",
  "ftReceiptCase": "5067112530745229313",
```

**2) The list of products sold:**<br>This is an array of products or lines items for a ticket. In the fiskaltrust.Universe, these are called ChargeItems. The data set shown below, is the absolute necessary set to be compliant with the French law. All the fields and possible values are described in depth in the middleware documentation.

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

**3) How the ticket is payed:**<br>In the fiskaltrust.Universe, this block is called PayItems. This a list of all the means of payment, used by the client. The example shown below is only the obligatory dataset, more information can be found in the middleware documentation.

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

Depending on the protocol used, the whole receipt is sent in the payload as JSON-string with SOAP or REST. The type of protocol defines which credentials you have to send in the header of the request. Usually, it is the CashBoxID and an AccessToken. Both can be found in the Configuration menu in the fiskaltrust.Portal.

The fiskaltrust.Middleware will answer this request with a response as JSON-string like this:

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

Most of this information must be printed on the receipt, but best practice is to print everything. Each signature sent back by the fiskaltrust.Middleware must be printed. Therefore, the fields Caption and Data are obligatory and must be shown on the receipt. There can be more than one signature. If this occurs each signature must be printed. Signatures with a type 3, contain a JWT, displayed as an encoded QR-Code in the Data-field, which must be printed before the footer, on the receipt.
