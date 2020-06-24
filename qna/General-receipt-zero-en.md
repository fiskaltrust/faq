## Question
What is a zero receipt?

## Metadata tags
lang-en, market-all, middleware, PosCreator, PosDealer, PosOperator, Consultant

## Answer
A zero receipt is a universal data carrier and storage. The cash register sends a receipt with an empty charge items block (_ftChargeItem_) and an empty pay items block (_ftPayItem_) which logically contain a total amount of “0”.

The fiskaltrust.SecurityMechanism sends the necessary blocks, such as the receipt header, the charge item block, and the signature block in the response. This response is either printed or issued electronically and has to be archived.

For example a start receipt or stop receipt is a special case of a zero receipt.
