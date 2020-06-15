## Action start examples for germany

Examples of action starttimes determination

### Standard action - explicit flow

1. Start-Transaction 

Request:

```json
{
    "ftCashBoxID":"cashboxid-guid",
    "ftPosSystemId":"possystemid-guid",
    "cbTerminalID":"T1",
    "cbReceiptReference":"233348",
    "cbReceiptMoment":"2020-05-22T10:47:40.960Z",
    "cbChargeItems":[],
    "cbPayItems":[],
    // 0x4445 0000 0000 0009 (start-transaction-receipt)  
    "ftReceiptCase":4919338167972134920,
    "cbArea":"Tisch 56"
}
```
Response:

```json
{
    "ftCashBoxID": "cashboxid-guid",
    "ftQueueID": "b6c9f13b-b987-43cd-ab08-3f5cb2a850d6",
    "ftQueueItemID": "e617a29e-ed50-4a4c-ab8c-449884c0e217",
    "ftQueueRow": 11,
    "cbTerminalID": "T1",
    "cbReceiptReference": "233348",
    "ftCashBoxIdentification": "220130d5-9060-4e26-b75c-35968f49aae3",
    "ftReceiptIdentification": "ftA#ST10",
    "ftReceiptMoment": "2020-05-22T10:47:42.3247875Z",
    "ftSignatures": [
        {
            "ftSignatureFormat": 13,
            "ftSignatureType": 4919338167972134928,
            "Caption": "start-transaction-signature",
            "Data": "rYGXxEcXYlTqJ0K2VlcPXKG5G1cKBv1dCdcFPP9lFLguGa6tYGthqNUROqjxmID1/gZwv216P1CQklYiB8FV+A=="
        }
    ],
    "ftState": 4919338167972134912
}
```
nothing to print here.

3. POS receipt receipt (finish transaction)

```json
{
    "ftCashBoxID":"cashboxid-guid",
    "ftPosSystemId":"possystemid-guid",
    "cbTerminalID":"T1",
    "cbReceiptReference":"233348",
    "cbReceiptMoment":"2020-05-22T11:11:00.260Z",
    "cbChargeItems":[
        {
            "Quantity":1.0,
            "Description":"0,5 Soda Zitrone",
            "Amount":3.50,
            "VATRate":19.0000,
            "ftChargeItemCase":4919338167972134913,
            "Moment":"2020-05-22T10:47:40.960Z"
        },
        {
            "Quantity":1.0,
            "Description":"Kaffe Hag",
            "Amount":4.00,
            "VATRate":19.0000,
            "ftChargeItemCase":4919338167972134913,
            "Moment":"2020-05-22T10:58:03.960Z"
        }
    ],
    "cbPayItems":[
        {
            "Quantity":1.0,
            "Description":"Cash",
            "Amount":7.50,
            // 0x4445 0000 0000 0001 (cash payment in national currency)         
            "ftPayItemCase":4919338167972134913,
            "Moment":"2020-05-22T11:11:00.260Z"
        }
    ],
    // 0x4445 0000 0000 0001  (pos-receipt)  
    "ftReceiptCase":4919338167972134913,
    "cbArea":"Tisch 56"
}
```

Response:
```json
{
    "ftCashBoxID": "cashboxid-guid",
    "ftQueueID": "b6c9f13b-b987-43cd-ab08-3f5cb2a850d6",
    "ftQueueItemID": "cd667ebf-bd66-4f3f-a977-fc1aefc54b55",
    "ftQueueRow": 13,
    "cbTerminalID": "T1",
    "cbReceiptReference": "233348",
    "ftCashBoxIdentification": "220130d5-9060-4e26-b75c-35968f49aae3",
    "ftReceiptIdentification": "ftC#T10",
    "ftReceiptMoment": "2020-05-22T11:11:02.7751885Z",
    "ftSignatures": [
        {
            "ftSignatureFormat": 3,
            "ftSignatureType": 4919338167972134913,
            "Caption": "www.fiskaltrust.de",
            "Data": "V0;220130d5-9060-4e26-b75c-35968f49aae3;Kassenbeleg-V1;Beleg^7.50_0.00_0.00_0.00_0.00^7.50:Bar;10;19;2020-05-22T10:47:42.000Z;2020-05-22T11:11:04.000Z;ecdsa-plain-SHA256;utcTime;FGq8kd0kuQjHmyK8/Ca73h1mqOSRsctDfM/h7zddskjM7iKLuVs+Mwff8WCUz45kA/F2lF9kI90zny8Tnuhf/w==;MFkwEwYHKoZIzj0CAQYIKoZIzj0DAQcDQgAENFFPGk1vDk92IL6tjsVQ6kpwc4TCsYNNGGoc0cN4dUPQZwOo2tuQlrQAVvMfO+XHWsnphAtN5cUbIwdtMk/Z6g=="
        },
        {
            "ftSignatureFormat": 13,
            "ftSignatureType": 4919338167972134928,
            "Caption": "start-transaction-signature",
            "Data": "rYGXxEcXYlTqJ0K2VlcPXKG5G1cKBv1dCdcFPP9lFLguGa6tYGthqNUROqjxmID1/gZwv216P1CQklYiB8FV+A=="
        },
        {
            "ftSignatureFormat": 13,
            "ftSignatureType": 4919338167972134929,
            "Caption": "finish-transaction-payload",
            "Data": "QmVsZWdeNy41MF8wLjAwXzAuMDBfMC4wMF8wLjAwXjcuNTA6QmFy"
        },
        {
            "ftSignatureFormat": 13,
            "ftSignatureType": 4919338167972134930,
            "Caption": "finish-transaction-signature",
            "Data": "FGq8kd0kuQjHmyK8/Ca73h1mqOSRsctDfM/h7zddskjM7iKLuVs+Mwff8WCUz45kA/F2lF9kI90zny8Tnuhf/w=="
        },
        {
            "ftSignatureFormat": 1,
            "ftSignatureType": 4919338167972134931,
            "Caption": "<qr-code-version>",
            "Data": "V0"
        },
        {
            "ftSignatureFormat": 1,
            "ftSignatureType": 4919338167972134932,
            "Caption": "<kassen-seriennummer>",
            "Data": "220130d5-9060-4e26-b75c-35968f49aae3"
        },
        {
            "ftSignatureFormat": 1,
            "ftSignatureType": 4919338167972134933,
            "Caption": "<processType>",
            "Data": "Kassenbeleg-V1"
        },
        {
            "ftSignatureFormat": 1,
            "ftSignatureType": 4919338167972134934,
            "Caption": "<processData>",
            "Data": "Beleg^7.50_0.00_0.00_0.00_0.00^7.50:Bar"
        },
        {
            "ftSignatureFormat": 1,
            "ftSignatureType": 4919338167972134935,
            "Caption": "<transaktions-nummer>",
            "Data": "10"
        },
        {
            "ftSignatureFormat": 1,
            "ftSignatureType": 4919338167972134936,
            "Caption": "<signatur-zaehler>",
            "Data": "19"
        },
        {
            "ftSignatureFormat": 1,
            // 0x4445 0000 0000 0019
            "ftSignatureType": 4919338167972134937,
            "Caption": "<start-zeit>",
            "Data": "2020-05-22T10:47:42.000Z"
        },
        {
            "ftSignatureFormat": 1,
            // 0x4445 0000 0000 001A
            "ftSignatureType": 4919338167972134938,
            "Caption": "<log-time>",
            "Data": "2020-05-22T11:11:04.000Z"
        },
        {
            "ftSignatureFormat": 1,
            "ftSignatureType": 4919338167972134939,
            "Caption": "<sig-alg>",
            "Data": "ecdsa-plain-SHA256"
        },
        {
            "ftSignatureFormat": 1,
            "ftSignatureType": 4919338167972134940,
            "Caption": "<log-time-format>",
            "Data": "utcTime"
        },
        {
            "ftSignatureFormat": 1,
            "ftSignatureType": 4919338167972134941,
            "Caption": "<signatur>",
            "Data": "FGq8kd0kuQjHmyK8/Ca73h1mqOSRsctDfM/h7zddskjM7iKLuVs+Mwff8WCUz45kA/F2lF9kI90zny8Tnuhf/w=="
        },
        {
            "ftSignatureFormat": 1,
            "ftSignatureType": 4919338167972134942,
            "Caption": "<public-key>",
            "Data": "MFkwEwYHKoZIzj0CAQYIKoZIzj0DAQcDQgAENFFPGk1vDk92IL6tjsVQ6kpwc4TCsYNNGGoc0cN4dUPQZwOo2tuQlrQAVvMfO+XHWsnphAtN5cUbIwdtMk/Z6g=="
        },
        {
            "ftSignatureFormat": 1,
            // 0x4445 0000 0000 001F
            "ftSignatureType": 4919338167972134943,
            "Caption": "<vorgangsbeginn>",
            "Data": "2020-05-22T10:47:40.960Z"
        },
    ],
    "ftState": 4919338167972134912
}
```

**Datetimes to be printed**:

1. time of receipt creation (DE: Datum der Belegausgabe):  `2020-05-22T11:11:02.7751885Z"` from `cbReceiptMoment` of the pos-receipt request

2. start time of the action (DE: Zeitpunkt des Vorgangbeginns):   `2020-05-22T10:47:40.960Z` from the signature block with `ftSignatureType`: `0x444500000000001F` (`dec: 4919338167972134943`)

3. end time of the action (DE: Zeitpunkt des Vorgangbeginns):   `2020-05-22T11:11:04.000Z` from the signature block with `ftSignatureType`: `0x444500000000001A`  (`dec: 4919338167972134938`)


### Standard action - implicit flow

Request:

```json
{
    "ftCashBoxID":"cashboxid-guid",
    "ftPosSystemId":"possystemid-guid",
    "cbTerminalID":"T1",
    "cbReceiptReference":"4747847",
    "cbReceiptMoment":"2020-05-22T11:33:00.260Z",
    "cbChargeItems":[
        {
            "Quantity":1.0,
            "Description":"0,5 Soda Zitrone",
            "Amount":3.50,
            "VATRate":19.0000,
            "ftChargeItemCase":4919338167972134913,
            "Moment":"2020-05-22T10:47:40.960Z"
        },
        {
            "Quantity":1.0,
            "Description":"Kaffe Hag",
            "Amount":4.00,
            "VATRate":19.0000,
            "ftChargeItemCase":4919338167972134913,
            "Moment":"2020-05-22T10:58:03.960Z"
        }
    ],
    "cbPayItems":[
        {
            "Quantity":1.0,
            "Description":"Cash",
            "Amount":7.50,      
            "ftPayItemCase":4919338167972134913,
            "Moment":"2020-05-22T11:33:00.260Z"
        }
    ], 
    // 0x4445 0000 0000 0001 (pos-receipt) + 0000 0001 0000 0000 (implicit flow)  
    "ftReceiptCase":4919338172267102209,
    "cbArea":"Tisch 19"
}
```

Response:

```json
{
    "ftCashBoxID": "cashboxid-guid",
    "ftQueueID": "b6c9f13b-b987-43cd-ab08-3f5cb2a850d6",
    "ftQueueItemID": "beada6fc-fbc3-4371-9330-f80c16e3035e",
    "ftQueueRow": 14,
    "cbTerminalID": "T1",
    "cbReceiptReference": "4747847",
    "ftCashBoxIdentification": "220130d5-9060-4e26-b75c-35968f49aae3",
    "ftReceiptIdentification": "ftD#IT11",
    "ftReceiptMoment": "2020-05-22T11:33:01.1497618Z",
    "ftSignatures": [
        {
            "ftSignatureFormat": 3,
            "ftSignatureType": 4919338167972134913,
            "Caption": "www.fiskaltrust.de",
            "Data": "V0;220130d5-9060-4e26-b75c-35968f49aae3;Kassenbeleg-V1;Beleg^7.50_0.00_0.00_0.00_0.00^7.50:Bar;11;21;2020-05-22T11:33:01.000Z;2020-05-22T11:33:02.000Z;ecdsa-plain-SHA256;utcTime;HSmIZw0g6tpJ/UeNYutHic5PXORANAH5V9+Fon9SfCvx3A/gO7Dguaxd8Mn/YKadgfLTV7s1VzWPe/QolS6dAg==;MFkwEwYHKoZIzj0CAQYIKoZIzj0DAQcDQgAENFFPGk1vDk92IL6tjsVQ6kpwc4TCsYNNGGoc0cN4dUPQZwOo2tuQlrQAVvMfO+XHWsnphAtN5cUbIwdtMk/Z6g=="
        },
        {
            "ftSignatureFormat": 13,
            "ftSignatureType": 4919338167972134928,
            "Caption": "start-transaction-signature",
            "Data": "kDLXgbGDuHGZmfF1vVlCDqgKMdZkxy0Gsm9jUeJBumhN6UhHPEW83T66PtVrJ/Xzs4IQpt2eFyDHB4g/1BCoWA=="
        },
        {
            "ftSignatureFormat": 13,
            "ftSignatureType": 4919338167972134929,
            "Caption": "finish-transaction-payload",
            "Data": "QmVsZWdeNy41MF8wLjAwXzAuMDBfMC4wMF8wLjAwXjcuNTA6QmFy"
        },
        {
            "ftSignatureFormat": 13,
            "ftSignatureType": 4919338167972134930,
            "Caption": "finish-transaction-signature",
            "Data": "HSmIZw0g6tpJ/UeNYutHic5PXORANAH5V9+Fon9SfCvx3A/gO7Dguaxd8Mn/YKadgfLTV7s1VzWPe/QolS6dAg=="
        },
        {
            "ftSignatureFormat": 1,
            "ftSignatureType": 4919338167972134931,
            "Caption": "<qr-code-version>",
            "Data": "V0"
        },
        {
            "ftSignatureFormat": 1,
            "ftSignatureType": 4919338167972134932,
            "Caption": "<kassen-seriennummer>",
            "Data": "220130d5-9060-4e26-b75c-35968f49aae3"
        },
        {
            "ftSignatureFormat": 1,
            "ftSignatureType": 4919338167972134933,
            "Caption": "<processType>",
            "Data": "Kassenbeleg-V1"
        },
        {
            "ftSignatureFormat": 1,
            "ftSignatureType": 4919338167972134934,
            "Caption": "<processData>",
            "Data": "Beleg^7.50_0.00_0.00_0.00_0.00^7.50:Bar"
        },
        {
            "ftSignatureFormat": 1,
            "ftSignatureType": 4919338167972134935,
            "Caption": "<transaktions-nummer>",
            "Data": "11"
        },
        {
            "ftSignatureFormat": 1,
            "ftSignatureType": 4919338167972134936,
            "Caption": "<signatur-zaehler>",
            "Data": "21"
        },
        {
            "ftSignatureFormat": 1,
            // 0x4445 0000 0000 0019
            "ftSignatureType": 4919338167972134937,
            "Caption": "<start-zeit>",
            "Data": "2020-05-22T11:33:01.000Z"
        },
        {
            "ftSignatureFormat": 1,
            // 0x4445 0000 0000 001A
            "ftSignatureType": 4919338167972134938,
            "Caption": "<log-time>",
            "Data": "2020-05-22T11:33:02.000Z"
        },
        {
            "ftSignatureFormat": 1,
            "ftSignatureType": 4919338167972134939,
            "Caption": "<sig-alg>",
            "Data": "ecdsa-plain-SHA256"
        },
        {
            "ftSignatureFormat": 1,
            "ftSignatureType": 4919338167972134940,
            "Caption": "<log-time-format>",
            "Data": "utcTime"
        },
        {
            "ftSignatureFormat": 1,
            "ftSignatureType": 4919338167972134941,
            "Caption": "<signatur>",
            "Data": "HSmIZw0g6tpJ/UeNYutHic5PXORANAH5V9+Fon9SfCvx3A/gO7Dguaxd8Mn/YKadgfLTV7s1VzWPe/QolS6dAg=="
        },
        {
            "ftSignatureFormat": 1,
            "ftSignatureType": 4919338167972134942,
            "Caption": "<public-key>",
            "Data": "MFkwEwYHKoZIzj0CAQYIKoZIzj0DAQcDQgAENFFPGk1vDk92IL6tjsVQ6kpwc4TCsYNNGGoc0cN4dUPQZwOo2tuQlrQAVvMfO+XHWsnphAtN5cUbIwdtMk/Z6g=="
        },
        {
            "ftSignatureFormat": 1,
            // 0x4445 0000 0000 001F
            "ftSignatureType": 4919338167972134943,
            "Caption": "<vorgangsbeginn>",
            "Data": "2020-05-22T10:47:40.960Z"
        },
    ],
    "ftState": 4919338167972134912
}
```

**Datetimes to be printed**:

1. time of receipt creation (DE: Datum der Belegausgabe):  `2020-05-22T11:33:00.260Z"` from `cbReceiptMoment` of the pos-receipt request

2. start time of the action (DE: Zeitpunkt des Vorgangbeginns):   `2020-05-22T10:47:40.960Z` from the signature block with `ftSignatureType`: `0x444500000000001F` (`dec: 4919338167972134943`)

3. end time of the action (DE: Zeitpunkt des Vorgangbeginns):   `2020-05-22T11:33:02.000Z` from the signature block with `ftSignatureType`: `0x444500000000001A`  (`dec: 4919338167972134938`)


### Long lasting action - implicit flow

1. Order (info-order) - day 1

Request:

```json

{
    "ftCashBoxID": "cashboxid-guid",
    "ftQueueID": "b6c9f13b-b987-43cd-ab08-3f5cb2a850d6",
    "ftPosSystemId": "d4a62055-ca6c-4372-ae4d-f835a88e4a5d",
    "cbTerminalID": "T1",
    "cbReceiptReference":"LLA_1",
    "cbReceiptMoment":"2020-05-26T10:47:40.960Z",
    "cbChargeItems":[
        {
            "Quantity":1.0,
            "Description":"0,5 Soda Zitrone",
            "Amount":3.50,
            "VATRate":19.0000,
            "ftChargeItemCase":4919338167972134913,
            "Moment":"2020-05-26T10:31:34.960Z"
        }
    ],
    "cbPayItems":[], 
    // 0x4445 0000 0000 0010 (info-order) + 0000 0001 0000 0000 (implicit flow)
    "ftReceiptCase":4919338172267102224,
    "cbArea":"Zimmer 12"
}
```

Response:

```json
{
    "ftCashBoxID": "cashboxid-guid",
    "ftQueueID": "b6c9f13b-b987-43cd-ab08-3f5cb2a850d6",
    "ftQueueItemID": "14d06319-52d7-4fa6-841b-c296f81b716e",
    "ftQueueRow": 68,
    "cbTerminalID": "T1",
    "cbReceiptReference": "LLA_1",
    "ftCashBoxIdentification": "220130d5-9060-4e26-b75c-35968f49aae3",
    "ftReceiptIdentification": "ft3D#IT92",
    "ftReceiptMoment": "2020-05-29T13:54:53.9023323Z",
    "ftSignatures": [
        {
            "ftSignatureFormat": 13,
            "ftSignatureType": 4919338167972134928,
            "Caption": "start-transaction-result",
            "Data": "luQPVPNDHv+V3aQ14exAT8uO8oXWCxfBWQM+UlcBnDK1bPgFnhurbTPoX7a2PdEtlr76qDFlW78dOX13S/Cm/w=="
        },
        {
            "ftSignatureFormat": 13,
            "ftSignatureType": 4919338167972134929,
            "Caption": "finish-transaction-payload",
            "Data": "MTsiMCw1IFNvZGEgWml0cm9uZSI7My41MAo="
        },
        {
            "ftSignatureFormat": 13,
            "ftSignatureType": 4919338167972134930,
            "Caption": "finish-transaction-result",
            "Data": "IKLNsqh0CvUIIqpVdh1pAEc6qOwWM3LKnlPLBWPO05JoDsuSyqbKqXR5D6j7prgxY5JysmqF49h0zSk12N/3gA=="
        },
        {
            "ftSignatureFormat": 1,
            "ftSignatureType": 4919338167972134933,
            "Caption": "<processType>",
            "Data": "Bestellung-V1"
        }
    ],
    "ftState": 4919338167972134912
}
```

nothing to print here


2. Order (info-order) - day 2

Request:

```json
{
    "ftCashBoxID": "cashboxid-guid",
    "ftQueueID": "b6c9f13b-b987-43cd-ab08-3f5cb2a850d6",
    "ftPosSystemId": "d4a62055-ca6c-4372-ae4d-f835a88e4a5d",
    "cbTerminalID": "T1",
    "cbReceiptReference":"LLA_1",
    "cbReceiptMoment":"2020-05-27T12:47:40.960Z",
    "cbChargeItems":[
        {
            "Quantity":1.0,
            "Description":"Kaffe Hag",
            "Amount":4.00,
            "VATRate":19.0000,
            "ftChargeItemCase":4919338167972134913,
            "Moment":"2020-05-27T12:11:22.233Z"
        }
    ],
    "cbPayItems":[], 
    // 0x4445 0000 0000 0010 (info-order) + 0000 0001 0000 0000 (implicit flow)
    "ftReceiptCase":4919338172267102224,
    "cbArea":"Zimmer 12"
}
```

Response:

```json
{
    "ftCashBoxID": "cashboxid-guid",
    "ftQueueID": "b6c9f13b-b987-43cd-ab08-3f5cb2a850d6",
    "ftQueueItemID": "2005ad2d-a00b-4b44-9871-5806f036a220",
    "ftQueueRow": 69,
    "cbTerminalID": "T1",
    "cbReceiptReference": "LLA_1",
    "ftCashBoxIdentification": "220130d5-9060-4e26-b75c-35968f49aae3",
    "ftReceiptIdentification": "ft3E#IT93",
    "ftReceiptMoment": "2020-05-29T13:59:33.1843023Z",
    "ftSignatures": [
        {
            "ftSignatureFormat": 13,
            "ftSignatureType": 4919338167972134928,
            "Caption": "start-transaction-result",
            "Data": "ThADGCPpoSsOx/BN6bNlA1t2JQCd+SFWpJjGpalaDfMhlTMLx30yjCGtFZHyq8ZzXJIyOQ18BxWJ8SM/233U6Q=="
        },
        {
            "ftSignatureFormat": 13,
            "ftSignatureType": 4919338167972134929,
            "Caption": "finish-transaction-payload",
            "Data": "MTsiS2FmZmUgSGFnIjs0LjAwCg=="
        },
        {
            "ftSignatureFormat": 13,
            "ftSignatureType": 4919338167972134930,
            "Caption": "finish-transaction-result",
            "Data": "CFm7yisXpQ/ncBolxwSSJ4au4ibGNoK1wKqp/HI7VTPdo8GyaJ0keVgtcCQGAIIeZZv//mvLG9u0ROH83nFdXw=="
        },
        {
            "ftSignatureFormat": 1,
            "ftSignatureType": 4919338167972134933,
            "Caption": "<processType>",
            "Data": "Bestellung-V1"
        }
    ],
    "ftState": 4919338167972134912
}
```
nothing to print here

3. Pos receipt (pos-receipt) - day 3

Request:

```json
{
    "ftCashBoxID": "cashboxid-guid",
    "ftQueueID": "b6c9f13b-b987-43cd-ab08-3f5cb2a850d6",
    "ftPosSystemId": "d4a62055-ca6c-4372-ae4d-f835a88e4a5d",
    "cbTerminalID": "T1",
    "cbReceiptReference":"LLA_1",
    "cbReceiptMoment":"2020-05-28T14:11:22.233Z",
    "cbChargeItems":[
        {
            "Quantity":1.0,
            "Description":"0,5 Soda Zitrone",
            "Amount":3.50,
            "VATRate":19.0000,
            "ftChargeItemCase":4919338167972134913,
            "Moment":"2020-05-26T10:31:34.960Z"
        },
        {
            "Quantity":1.0,
            "Description":"Kaffe Hag",
            "Amount":4.00,
            "VATRate":19.0000,
            "ftChargeItemCase":4919338167972134913,
            "Moment":"2020-05-27T12:11:22.233Z"
        }
        ],
        "cbPayItems":[
        {
            "Quantity":1.0,
            "Description":"Cash",
            "Amount":7.50,      
            "ftPayItemCase":4919338167972134913,
            "Moment":"2020-05-28T14:11:22.233Z"
        }
    ], 
    // 0x4445 0000 0000 0001 (pos-receipt) + 0000 0001 0000 0000 (implicit flow) 
    "ftReceiptCase":4919338172267102209,
    "cbArea":"Zimmer 12"
}

```
Response:

```json
{
    "ftCashBoxID": "cashboxid-guid",
    "ftQueueID": "b6c9f13b-b987-43cd-ab08-3f5cb2a850d6",
    "ftQueueItemID": "d6de2c89-04c7-4be4-9c07-44e234947277",
    "ftQueueRow": 70,
    "cbTerminalID": "T1",
    "cbReceiptReference": "LLA_1",
    "ftCashBoxIdentification": "220130d5-9060-4e26-b75c-35968f49aae3",
    "ftReceiptIdentification": "ft3F#IT94",
    "ftReceiptMoment": "2020-05-29T14:08:22.9158623Z",
    "ftSignatures": [
        {
            "ftSignatureFormat": 3,
            "ftSignatureType": 4919338167972134913,
            "Caption": "www.fiskaltrust.de",
            "Data": "V0;220130d5-9060-4e26-b75c-35968f49aae3;Kassenbeleg-V1;Beleg^7.50_0.00_0.00_0.00_0.00^7.50:Bar;94;168;2020-05-29T14:08:23.000Z;2020-05-29T14:08:24.000Z;ecdsa-plain-SHA256;utcTime;+dZ0zPEUJbjd7/vp5hA8GtbcGJvPxT/SyNiBWLxs3EzgjqL4HPFrmET/jalGD/ZiyIdZq9mx+YphP5tjCiT1pw==;MFkwEwYHKoZIzj0CAQYIKoZIzj0DAQcDQgAENFFPGk1vDk92IL6tjsVQ6kpwc4TCsYNNGGoc0cN4dUPQZwOo2tuQlrQAVvMfO+XHWsnphAtN5cUbIwdtMk/Z6g=="
        },
        {
            "ftSignatureFormat": 13,
            "ftSignatureType": 4919338167972134928,
            "Caption": "start-transaction-signature",
            "Data": "P5EYY5ORoRlEql8mH2FrmPuHgi6fonsamlCc1tyIhgYRz69ColwOW5DB4N33r/OpNapHwjI4ryGF6ZU/ZzXoag=="
        },
        {
            "ftSignatureFormat": 13,
            "ftSignatureType": 4919338167972134929,
            "Caption": "finish-transaction-payload",
            "Data": "QmVsZWdeNy41MF8wLjAwXzAuMDBfMC4wMF8wLjAwXjcuNTA6QmFy"
        },
        {
            "ftSignatureFormat": 13,
            "ftSignatureType": 4919338167972134930,
            "Caption": "finish-transaction-signature",
            "Data": "+dZ0zPEUJbjd7/vp5hA8GtbcGJvPxT/SyNiBWLxs3EzgjqL4HPFrmET/jalGD/ZiyIdZq9mx+YphP5tjCiT1pw=="
        },
        {
            "ftSignatureFormat": 1,
            "ftSignatureType": 4919338167972134931,
            "Caption": "<qr-code-version>",
            "Data": "V0"
        },
        {
            "ftSignatureFormat": 1,
            "ftSignatureType": 4919338167972134932,
            "Caption": "<kassen-seriennummer>",
            "Data": "220130d5-9060-4e26-b75c-35968f49aae3"
        },
        {
            "ftSignatureFormat": 1,
            "ftSignatureType": 4919338167972134933,
            "Caption": "<processType>",
            "Data": "Kassenbeleg-V1"
        },
        {
            "ftSignatureFormat": 1,
            "ftSignatureType": 4919338167972134934,
            "Caption": "<processData>",
            "Data": "Beleg^7.50_0.00_0.00_0.00_0.00^7.50:Bar"
        },
        {
            "ftSignatureFormat": 1,
            "ftSignatureType": 4919338167972134935,
            "Caption": "<transaktions-nummer>",
            "Data": "94"
        },
        {
            "ftSignatureFormat": 1,
            "ftSignatureType": 4919338167972134936,
            "Caption": "<signatur-zaehler>",
            "Data": "168"
        },
        {
            "ftSignatureFormat": 1,
            // 0x4445 0000 0000 0019
            "ftSignatureType": 4919338167972134937,
            "Caption": "<start-zeit>",
            "Data": "2020-05-29T14:08:23.000Z"
        },
        {
            // 0x4445 0000 0000 001A
            "ftSignatureFormat": 1,
            "ftSignatureType": 4919338167972134938,
            "Caption": "<log-time>",
            "Data": "2020-05-29T14:08:24.000Z"
        },
        {
            "ftSignatureFormat": 1,
            "ftSignatureType": 4919338167972134939,
            "Caption": "<sig-alg>",
            "Data": "ecdsa-plain-SHA256"
        },
        {
            "ftSignatureFormat": 1,
            "ftSignatureType": 4919338167972134940,
            "Caption": "<log-time-format>",
            "Data": "utcTime"
        },
        {
            "ftSignatureFormat": 1,
            "ftSignatureType": 4919338167972134941,
            "Caption": "<signatur>",
            "Data": "+dZ0zPEUJbjd7/vp5hA8GtbcGJvPxT/SyNiBWLxs3EzgjqL4HPFrmET/jalGD/ZiyIdZq9mx+YphP5tjCiT1pw=="
        },
        {
            "ftSignatureFormat": 1,
            "ftSignatureType": 4919338167972134942,
            "Caption": "<public-key>",
            "Data": "MFkwEwYHKoZIzj0CAQYIKoZIzj0DAQcDQgAENFFPGk1vDk92IL6tjsVQ6kpwc4TCsYNNGGoc0cN4dUPQZwOo2tuQlrQAVvMfO+XHWsnphAtN5cUbIwdtMk/Z6g=="
        },
        {
            "ftSignatureFormat": 1,
            // 0x4445 0000 0000 001F
            "ftSignatureType": 4919338167972134943,
            "Caption": "<vorgangsbeginn>",
            "Data": "2020-05-26T10:31:34.960Z"
        }
    ],
    "ftState": 4919338167972134912
}
```
**Datetimes to be printed**:

1. time of receipt creation (DE: Datum der Belegausgabe):  `2020-05-28T14:11:22.233Z` from `cbReceiptMoment` of the pos-receipt request

2. start time of the action (DE: Zeitpunkt des Vorgangbeginns):   `2020-05-29T14:08:23.000Z` from the signature block with `ftSignatureType`: `0x4445000000000019` (`dec: 4919338167972134937`)

3. end time of the action (DE: Zeitpunkt des Vorgangbeginns):   `2020-05-29T14:08:24.000Z` from the signature block with `ftSignatureType`: `0x444500000000001A`  (`dec: 4919338167972134938`)

4. start time of the first order (DE: Startzeitpunkt der ersten „Bestellung“ im Bondruck):  `2020-05-26T10:31:34.960Z` from the signature block with `ftSignatureType`: `0x444500000000001F` (`dec: 4919338167972134943`)
