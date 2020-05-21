## Action start examples germany

Examples of action starttimes determination

### Standard action - explicit flow

1. Start- Transaction 

Request:

```json
{
    "ftCashBoxID":"cashboxid-guid",
    "ftPosSystemId":"possystemid-guid",
    "cbTerminalID":"terminalid",
    "cbReceiptReference":"233348",
    "cbReceiptMoment":"2020-05-20T12:52:34.9609375Z",
    "cbChargeItems":[
        {
            "Quantity":1.0,
            "Description":"0,5 Soda Zitrone",
            "Amount":3.50,
            "VATRate":19.0000,
            "ftChargeItemCase":4919338167972134913
            "Moment":"2020-05-20T12:52:34.9609375Z"
        }
    ],
    "cbPayItems":[],
    // 0x4445 0000 0000 0009 (start-transa-receipt)  
    "ftReceiptCase":4919338167972134920,
    "cbArea":"Tisch 56"
}
```
Response:
TODO

2. Update Transaction 

Request:

```json
{
    "ftCashBoxID":"cashboxid-guid",
    "ftPosSystemId":"possystemid-guid",
    "cbTerminalID":"terminalid",
    "cbReceiptReference":"233348",
    "cbReceiptMoment":"2020-05-20T12:53:01.1231331Z",
    "cbChargeItems":[
        {
            "Quantity":1.0,
            "Description":"0,5 Soda Zitrone",
            "Amount":3.50,
            "VATRate":19.0000,
            "ftChargeItemCase":4919338167972134913
            "Moment":"2020-05-20T12:52:34.9609375Z"
        },
        {
            "Quantity":1.0,
            "Description":"Kaffe Hag",
            "Amount"4.00,
            "VATRate":19.0000,
            "ftChargeItemCase":4919338167972134913
            "Moment":"2020-05-20T12:53:01.1231331Z"
        }
    ],
    "cbPayItems":[],
    // 0x4445 0000 0000 0009 (update-transaction-receipt)  
    "ftReceiptCase":4919338167972134921,
    "cbArea":"Tisch 56"
}
```

Response:
TODO

3. POS receipt receipt (finish transaction)

```json
{
    "ftCashBoxID":"cashboxid-guid",
    "ftPosSystemId":"possystemid-guid",
    "cbTerminalID":"terminalid",
    "cbReceiptReference":"233348",
    "cbReceiptMoment":"2020-05-20T13:06:12.0181273Z",
    "cbChargeItems":[
        {
            "Quantity":1.0,
            "Description":"0,5 Soda Zitrone",
            "Amount":3.50,
            "VATRate":19.0000,
            "ftChargeItemCase":4919338167972134913
            "Moment":"2020-05-20T12:52:34.9609375Z"
        },
        {
            "Quantity":1.0,
            "Description":"Kaffe Hag",
            "Amount"4.00,
            "VATRate":19.0000,
            "ftChargeItemCase":4919338167972134913
            "Moment":"2020-05-20T12:53:01.1231331Z"
        }
    ],
    "cbPayItems":[
        {
            "Quantity":1.0,
            "Description":"Cash",
            "Amount":7.50,
            // 0x4445 0000 0000 0001 (cash payment in national currency)         
            "ftPayItemCase":4919338167972134913
            "Moment":"2020-05-20T13:06:12.0181273Z"
        }
    ],
    // 0x4445 0000 0000 0001  (pos-receipt)  
    "ftReceiptCase":4919338167972134913,
    "cbArea":"Tisch 56"
}
```

Response:
TODO

**Datetimes to be printed**:

- time of receipt creation:  `2020-05-20T13:06:12.0181273Z"` from `cbReceiptMoment` of the pos-receipt request
- start time of the action (`ftSignatureType`: `0x444500000000001F`) :  `"2020-05-20T12:52:34.9609375Z"` minimum of ( `cbReceiptMoment` , `cbChargeItems[0].Moment`,   `cbChargeItems[1].Moment`,  `cbPayItems[0].Moment`) = `cbChargeItems[0].Moment`
- start time of start transaction (`ftSignatureType`: `0x4445000000000019`.):   `2020-05-20T12:52:34.9609375Z` 


### Standard action - implicit flow

Request:

```json
{
    "ftCashBoxID":"cashboxid-guid",
    "ftPosSystemId":"possystemid-guid",
    "cbTerminalID":"terminalid",
    "cbReceiptReference":"233348",
    "cbReceiptMoment":"2020-05-20T13:06:12.0181273Z",
    "cbChargeItems":[
        {
            "Quantity":1.0,
            "Description":"0,5 Soda Zitrone",
            "Amount":3.50,
            "VATRate":19.0000,
            "ftChargeItemCase":4919338167972134913
            "Moment":"2020-05-20T12:52:34.9609375Z"
        },
        {
            "Quantity":1.0,
            "Description":"Kaffe Hag",
            "Amount"4.00,
            "VATRate":19.0000,
            "ftChargeItemCase":4919338167972134913
            "Moment":"2020-05-20T12:53:01.1231331Z"
        }
    ],
    "cbPayItems":[
        {
            "Quantity":1.0,
            "Description":"Cash",
            "Amount":7.50,
            // 0x4445 0000 0000 0001 (cash payment in national currency)         
            "ftPayItemCase":4919338167972134913
            "Moment":"2020-05-20T13:06:12.0181273Z"
        }
    ],
    // 0x4445 0000 0000 0001 (pos-receipt) + 0000 0001 0000 0000 (implicit flow)  
    "ftReceiptCase":4919338172267102209,
    "cbArea":"Tisch 56"
    }
```

Response:
TODO

**Datetimes to be printed**:

- time of receipt creation:  `2020-05-20T13:06:12.0181273Z"` from `cbReceiptMoment` of the pos-receipt request
- start time of the action (`ftSignatureType`: `0x444500000000001F`) :  `"2020-05-20T12:52:34.9609375Z"` minimum of ( `cbReceiptMoment` , `cbChargeItems[0].Moment`,   `cbChargeItems[1].Moment`,  `cbPayItems[0].Moment`) = `cbChargeItems[0].Moment`
- start time of start transaction (`ftSignatureType`: `0x4445000000000019`.):   `2020-05-20T13:06:12.0181273Z` 


### Long lasting action - implicit flow
