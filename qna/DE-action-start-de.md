## Question
How is the start time of a transaction (business case) determined for the German market?

## Question
How can I set the start time of a transaction for the German market?

## Question
Which start times of a transaction must be printed on the receipt in Germany?

## Metadata tags
lang-en, market-de, middleware

## Answer
The receipt must contain three date/time pairs, in cases of long-lasting sales preparation processes even four:

1. Date and time of receipt issuance/creation (DE: Datum der Belegausstellung)
2. Start date and time of the transaction (DE: Zeitpunkt des Vorgangbeginns)
3. End date and time of the transaction (DE: Zeitpunkt der Vorgangsbeendigung)
4. In the special case of long-lasting sales preparation processes (DE: lang anhaltende verkaufsvorbereitende Vorgänge): Start date and time of the first transaction (order); (DE: Startzeitpunkt der ersten Transaktion „Bestellung“)

The time of the receipt creation can be transmitted in the receipt request by using the field `ReceiptRequest.cbReceiptMoment`. It must be provided in UTC.

For a receipt request of type `pos-receipt`, fiskaltrust.Middleware returns three dates in the signature block that can be used for printing the receipt:

1. Time of the start transaction as provided by the TSE (`ftSignatureType`: `0x4445000000000019`).
2. Time of the finish transaction as provided by the TSE (`ftSignatureType`: `0x444500000000001A`).
3. Calculated start time of the action = the minimum of the date/time pairs (`ReceiptRequest.cbReceiptMoment,ftChargeItem[i].Moment, ftPayItem[i].Moment`) sent  to fiskaltrust.Middleware in the pos-receipt request. The entry has the signature type: `ftSignatureType`: `0x444500000000001F`.

Depending on your use case you have to decide which of the returned date and times you have to print. For example, in normal cases (no long-lasting sales preparation process) you may print the calculated start time of the transaction  (`ftSignatureType`: `0x444500000000001F`) as the start time of the transaction  (DE: Zeitpunkt des Vorgangbeginns) on your receipt.

On the other hand, if your use case includes long-lasting sales preparation process - assuming that you sent the first ordered charge item having the datetime (`ftChargeItem.Moment`) of that order - you may want to use the calculated start time of the transaction (`ftSignatureType`: `0x444500000000001F`) as the start time of the first sales preparation (DE: Startzeitpunkt der ersten verkaufsvorbereitenden Vorgangs). Furthermore, you may use the returned time of the start transaction (`ftSignatureType`: `0x4445000000000019`) as the start time of the transaction (DE: Zeitpunkt des Vorgangbeginns).

You can find start time examples [here](../examples/DE-action-start-de.md).
