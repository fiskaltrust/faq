## Question
How to handle degraded mode?

## Metadata tags
lang-en, market-fr, middleware, PosCreator

## Answer
If the receipt can not be signed by the fiskaltrust.SecurityMechanism the POS-System must print **mode dégradé** on the receipt.

When the fiskaltrust.Middleware can sign the receipts again all the receipts signed with the “degraded” mode, have to be entered (manually/automatically), sent to the fiskaltrust.SecurityMechanism and printed again, as regular receipts. Then the degraded and the new receipts must be archived together.

A good practice is to send a message in the technical log with the following content:

```JSON
{
  "code": 70,
  "description": "Start of degraded mode",
  "moment": "2020-03-22T06:10:52.6395741Z"
}
```

to document the beginning of the degraded mode. When normal functionality returns, the following message should be sent to the technical log, to document the event.

```JSON
{
  "code": 120,
  "description": "End of degraded mode",
  "moment": "2020-03-22T09:23:22.6015741Z"
}
```
