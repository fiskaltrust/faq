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
4. In the special case of long lasting actions (DE: lang anhaltender Bestellvorgang): Start time of the first order (DE: Startzeitpunkt der ersten „Bestellung“ im Bondruck) 

The datetime of the receipt creation can be transmitted in the recept request by using the field `ReceiptRequest.cbReceiptMoment`. It must be provided in UTC.

For a receipt request of type `pos-receipt`, the ftMiddleware returns 3 dates in the signature block that can be used for printing on the receipt:

1. time of the start transaction submitted to the TSE (`ftSignatureType`: `0x4445000000000019`).
2. time of the finish transaction submitted to the TSE (`ftSignatureType`: `0x444500000000001A`).
3. calculated start time of the action = the minimum of the datetimes (`ReceiptRequest.cbReceiptMoment,ftChargeItem[i].Moment, ftPayItem[i].Moment`) transmitted to the ft.Middleware in the pos-receipt request. The entry has the signature type: `ftSignatureType`: `0x444500000000001F`.

Depending on your usecase you can decide which returned datetimes you want to print. For example, in the normal case (no long lasting action) you may print the calculated start time of the action  (`ftSignatureType`: `0x444500000000001F`) as the start time of the action (DE: Zeitpunkt des Vorgangbeginns) on your receipt.

If for example your usecase is a long lasting action - assuming that you transmitted the first ordered charge item having the datetime (`ftChargeItem.Moment`) of that order - you may want to use the calculated start time of the action (`ftSignatureType`: `0x444500000000001F`) as the starttime of the first order (DE: Startzeitpunkt der ersten „Bestellung“ im Bondruck.). Furthermore, you may use the returned time of the start transaction (`ftSignatureType`: `0x4445000000000019`) as the start time of the action (DE: Zeitpunkt des Vorgangbeginns).

You can find start time examples [here](../examples/DE-action-start-de.md).
