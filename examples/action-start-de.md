## Action start examples germany

Examples of action starttimes determination

### Standard action - explicit flow

1. Start- Transaction 

Request:

```json
{
    "ftCashBoxID":"cashboxid-guid",
    "ftPosSystemId":"possystemid-guid",
    "cbTerminalID":"T1",
    "cbReceiptReference":"233348",
    "cbReceiptMoment":"2020-05-22T10:47:40.960Z",
    "cbChargeItems":[
        {
            "Quantity":1.0,
            "Description":"0,5 Soda Zitrone",
            "Amount":3.50,
            "VATRate":19.0000,
            "ftChargeItemCase":4919338167972134913,
            "Moment":"2020-05-22T10:47:40.960Z"
        }
    ],
    "cbPayItems":[],
    // 0x4445 0000 0000 0009 (start-transa-receipt)  
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

2. Update Transaction 

Request:

```json
{
    "ftCashBoxID":"cashboxid-guid",
    "ftPosSystemId":"possystemid-guid",
    "cbTerminalID":"T1",
    "cbReceiptReference":"233348",
    "cbReceiptMoment":"2020-05-22T10:58:03.960Z",
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
    "cbPayItems":[],
    // 0x4445 0000 0000 0009 (update-transaction-receipt)  
    "ftReceiptCase":4919338167972134921,
    "cbArea":"Tisch 56"
}
```

Response:

```json
{
    "ftCashBoxID": "cashboxid-guid",
    "ftQueueID": "b6c9f13b-b987-43cd-ab08-3f5cb2a850d6",
    "ftQueueItemID": "378e1671-0387-487e-9644-4913baf4653d",
    "ftQueueRow": 12,
    "cbTerminalID": "T1",
    "cbReceiptReference": "233348",
    "ftCashBoxIdentification": "220130d5-9060-4e26-b75c-35968f49aae3",
    "ftReceiptIdentification": "ftB#UT10",
    "ftReceiptMoment": "2020-05-22T10:58:03.9048491Z",
    "ftSignatures": [],
    "ftState": 4919338167972134912
}

```

nothing to print here

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
            "ftSignatureType": 4919338167972134937,
            "Caption": "<start-zeit>",
            "Data": "2020-05-22T10:47:42.000Z"
        },
        {
            "ftSignatureFormat": 1,
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
        }
    ],
    "ftState": 4919338167972134912
}
```

**Datetimes to be printed**:

- time of receipt creation:  `2020-05-22T11:11:00.260Z"` from `cbReceiptMoment` of the pos-receipt request
- start time of the action (`ftSignatureType`: `0x444500000000001F`) :  `todo currently missing` minimum of ( `cbReceiptMoment` , `cbChargeItems[0].Moment`,   `cbChargeItems[1].Moment`,  `cbPayItems[0].Moment`) = `cbChargeItems[0].Moment`
- start time of start transaction (`ftSignatureType`: `0x4445000000000019`.):   `2020-05-22T10:47:42.000Z` 


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
            "ftSignatureType": 4919338167972134937,
            "Caption": "<start-zeit>",
            "Data": "2020-05-22T11:33:01.000Z"
        },
        {
            "ftSignatureFormat": 1,
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
        }
    ],
    "ftState": 4919338167972134912
}
```

**Datetimes to be printed**:

- time of receipt creation:  `2020-05-22T11:33:00.260Z"` from `cbReceiptMoment` of the pos-receipt request
- start time of the action (`ftSignatureType`: `0x444500000000001F`) :  `will be available soon` minimum of ( `cbReceiptMoment` , `cbChargeItems[0].Moment`,   `cbChargeItems[1].Moment`,  `cbPayItems[0].Moment`) = `cbChargeItems[0].Moment`
- start time of start transaction (`ftSignatureType`: `0x4445000000000019`.):   `2020-05-22T11:33:01.000Z` 


### Long lasting action - implicit flow
