## Question
How is the cancellation of activities and items to be represented in the iPOS?

## Question
How are receipts reversed?

## Metadata tags
lang-de, market-de, middleware, PosCreator, PosDealer

## Answer

### Cancellation of operations and items
- Cancellation of operations
    - Subsequent process cancellation (DSFinV-K 4.2.2) 
        - The cancellation-receipt is a separate receipt which is to be identified by BON_STORNO = "1". The signs of MENGE, BRUTTO, NETTO and UST must be reversed. 
        For unique identification cbPreviousReceiptReference is to be used accordingly.           
        - The new cancellation-receipt to be created must be marked with the ReceiptCaseFlag "reverse/voided receipt", 0x000000000004000000. 
        - This marks the receipt in DSFinV-K with BON_STORNO = "1".
        - The statement in DSFinV-K p. 80 that BON_STORNO may not be used if a negative reversal of the transaction is made is correct in this respect, as this refers to the original receipt to be reversed.
    - Immediate process cancellation (DSFinV-K 4.2.1) 
        - Immediate transaction cancellation is only carried out in the same way as "Subsequent transaction cancellation".
        - Since fiskaltrust does not support "old" cash registers which are not yet connected to a TSE, the immediate transaction cancellation by subsequent marking of the document with the cancellation flag "BON_STORNO" by the ft.interface is NOT supported.
        - The transaction type "AV document reversal" can therefore not be used either.
    - Cancellation of positions (DSFinV-K 4.2.3) 
        - As with the transaction cancellation, an additional item data record must be created. The signs of MENGE, BRUTTO, NETTO and UST must be reversed.
        - The cancellation of items by subsequently marking the item with the cancellation flag "P_STORNO" must not be used.

### DSFinV-K: https://fiskaltrust.de/dsfinv-k/ 
#### Representation of special events
##### 4.2.1 Immediate process cancellations
Immediate transaction cancellation is only possible for systems that are not linked to a TSE (e.g. cash registers that can be used with transitional arrangements until 31.12.2022), if a cash voucher has been generated but the transaction does not take place immediately (e.g. because the customer has forgotten the money). Only in these cases can an immediate cancellation be made.
The display can be done in two ways:
* BON_STORNO is set to "1", otherwise the data record remains unchanged (in particular, no second data record is created; only in these cases may the transaction category "AV document reversal" be used), or
* Proceed as described below for "Subsequent operation cancellation".
##### 4.2.2 Subsequent process cancellations
Special rules apply to the subsequent cancellation of a transaction:
* The original document remains unchanged.
* The reversal document is a separate document, which must be identified by BON_STORNO = "1". In this case, you must specify the activity category with "Document" (analogous to the original document). The signs should be reversed.
In order to enable a reference to the original transaction, special reference fields for unique identification are included in the DSFinV-K.
From a sales tax perspective, a cancellation invoice is part of the invoice correction process. Just as for invoices, the statutory mandatory information according to § 14 para. 4 UStG (German VAT Act) also applies to invoice corrections.

#### 4.2.3 Cancellation of positions
Cancellations to be carried out at item level take place in the area of bonuses.
Either set P_STORNO to "1" in the original position (without creating a second data row) or create an additional position data record in which QUANTITY, GROSS, NET and UST are displayed with negative signs. In this case P_STORNO must not be set to "1".
Once the transaction has been signed in the TSE, the field P_STORNO may no longer be used.

#### 4.2.5 Operations with negative positions
If items with a negative sign occur in a receipt due to, for example, goods returns, discounts or position cancellations, they are displayed as in a normal sale. Only the sign for the field QUANTITY changes (and thus automatically the sign of POS_BRUTTO, POS_NETTO and POS_UST in the file Bonpos_UST, see 3.1.1.1).

#### Appendix B BON_TYP (transaction type)
The following transaction types (receipt types) are distinguished:
…
* AVBelegstorno
AV document cancellation
The transaction category "AVBelegstorno" indicates all transactions that are completely reversed. The use is only permitted within a cash balance. The use of AVBelegstorno is dependent on the POS system and is intended for POS systems that only use a reversal indicator on the original document instead of an offsetting entry.
The AVBelegstorno displays a complete reversal of the original receipt, so that all amounts are no longer included in the cash balance.
Note: The AVBelegstorno does not mean the negative representation of a document. For this, you must continue to use the transaction category "Document" with reversed debit/credit signs and without a reversal indicator. In these cases, it should be noted that a reference to the original operation must be made.
Look out! As soon as a TSE is used at a cash register, it is technically no longer possible to use the transaction type "AVBelegstorno" correctly, since each document has already been signed by the TSE before the reversal indicator is set. In this respect, subsequent "zeroing" of a document is no longer possible.

#### Chapter: Single Recording Module
##### 11. file "Bonkopf" (transactions.csv)
###### BON_STORNO
Field type: Character
Field length: 1
Short description: The activation (value: "1") of this field marks the cancellation of a single receipt. An entry is mandatory ("0" or "1"). BON_STORNO may only be set to "1" if a complete transaction is "cancelled" immediately and without an offsetting entry, but not if a negative reverse posting of the transaction is made. Cf. comments on points 4.2.1 and 4.2.2.

###### P_STORNO
Field type: Character
Field length: 1
Brief description: Position reversal indicator. If the field is activated (value = "1"), this is a cancelled item (immediately during data entry).

#### Annex I Definition of "type" and "dates" of the operation; QR code
##### 1. definition of the data structures for transfer to the security module
…
###### Cash voucher
processType: Kassenbeleg-V1
processData: <Vorgangstyp>^<Brutto-Steuerumsätze>^<Zahlungen>
Trennzeichen: ^ (Unicode U+005E)
<Vorgangstyp>:
<Task type>:
The transaction type according to DSFinV-K can have the following values:

* AVBelegstorno
