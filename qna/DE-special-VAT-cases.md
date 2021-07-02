## Question
How can I set a special case VAT ID to my charge item for the German market?

## Question
How can I use the iPOS interface to address special DSFinV-k VAT IDs grater than 1000?

## Metadata tags
lang-en, market-de, middleware, PosCreator

## Answer

This special VAT Rate IDs to be used in the DSFinV-K export for the range > 1000 can be adderessed in the carge items by using a `ftChargeItemCase` that is intended for an "unknown vat":

- `0x4445000000000007`-  undefined type of service for DE unknown vat
- `0x4445000000000017`-  delivery unknown vat
- `0x444500000000001F`-  other services unknown vat
- `0x444500000000001F`-  returnable vat unknown
- `0x444500000000002F`-  returnable reverse vat unknown
- `0x4445000000000037`-  discount unknown vat
- `0x444500000000003F`-  extra charge unknown vat
- `0x4445000000000047`-  unreal grant unknown vat
- `0x4445000000000057`-  tip to owner unknown vat
- `0x4445000000000067`-  coupon sales unknown vat
- `0x444500000000006F`-  coupon redeem unknown vat
- `0x4445000000000077`-  receivable creation unknown vat
- `0x444500000000007F`-  receivable reduction unknown vat
- `0x4445000000000087`-  down payment creation unknown vat
- `0x444500000000008F`-  down payment reduction unknown vat

Additionally the field `chargeItem.VATRate` must be set to the value of the special VAT Rate to be used. For example: 

```json
"cbChargeItems":[
   {
      "VATRate":14.25,
      "ftChargeItemCase":4919338167972134943
   }
]
```

If you set the field `chargeItem.VATRate` to 0.0, than the ft.Middleware will map to the DSFinV-k VAT ID 7. For any other value the ft.Middleware will map to a DSFinV-k VAT ID > 1000 by multiplying the given `chargeItem.VATRate` value with 100 and adding 1000. In our example above this will result into the `DSFinV-k VAT ID = (14.25 * 100) + 1000 = 2425`.
