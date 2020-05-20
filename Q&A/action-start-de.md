## Question
How is the start time of the action determined for the german market?

## Question
How can I set the start time of an action for the german market?

## Question
Which start times of an action must be printed on the receipt in germany?

## Metadata tags
lang-en, market-de, middleware

## Answer
On the receipt 3 datetimes, in special cases even 4 datetimes must be printed:

1. Date of receipt issuance/creation (DE: Datum der Belegausgabe)
2. Start time of the action (DE: Zeitpunkt des Vorgangbeginns)
3. End time of the action (DE: Zeitpunkt der Vorgangsbeendigung)
4. In the special case of long lasting actions (DE: lang anhaltender Bestellvorgang): Start time of the first order (DE: Startzeitpunkt der ersten „Bestellung“ im Bondruck.) 

The datetime of the receipt creation can be transmitted in the recept request by using the field `ReceiptRequest.cbReceiptMoment`. It must be provided in UTC.

The start time of the action is calculated by fiskaltrust. It is the minimum of the datetimes transmitted to the ft.Middleware in the receipt request (`ReceiptRequest.cbReceiptMoment`), charge items (`ftChargeItem.Moment`) and pay items (`ftPayItem.Moment`). You can find its value returned as a part of the response in the signature block entry with  `ftSignatureType`: `0x444500000000001F`.

The end time of the action is set by fiskaltrust by using the datetime of the finish transaction sent to the TSE. You can find its value as a part of the response in the signature block entry with  `ftSignatureType`: `0x444500000000001F`.

There is no separate special start time for long lasting actions returned by fiskaltrust. If you want to receive it as a strat time of the action in the signature block (`ftSignatureType`: `0x444500000000001F`) then you have to add an empty charge item to your reques having `ftChargeItem.Moment` set to the date of the first order. In this case fiskaltrust will consider that item for calculating the datetime of the start of the action as described above.

Fiskaltrust also returns the datetime of the start transaction submitted to the TSE for the current receipt request. It can be found in the signatures block by the `ftSignatureType`: `0x4445000000000019`.

Depending on your case you can decide wich returned datetimes you want to print. For example if your usecase is a long lasting action, you may want to add an empty charge item with the datetime of the first order to your request and use the calculated start time of the action (`ftSignatureType`: `0x444500000000001F`) as the starttime of the first order. Furthermore you may use the start transaction time (`ftSignatureType`: `0x4445000000000019`) for this usecase as the start time of the action.
