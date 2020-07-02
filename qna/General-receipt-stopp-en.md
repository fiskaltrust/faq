## Question
What is a stop receipt?

## Metadata tags
lang-en, market-all, middleware, PosCreator, PosDealer, PosOperator, Consultant

## Answer
The _stop receipt_ is required for scheduled decommissioning of the fiskaltrust.SecurityMechanism and/or cash registers. The _stop receipt_ is used to switch off any further: receipt chaining, up-counters, and totalizer storage. It also concludes the data collection log.

This receipt has a meaningful response from fiskaltrust.SecurityMechanism only the one time in order to stop operative calculations and the operation of a queue. After receiving a _stop receipt_ the queue will be closed. There will be no positive response from the fiskaltrust.SecurityMechanism to the cash register when a receipt is sent to a closed queue.

A closed queue cannot be reopened with a start receipt. Instead, a new queue must be created and initialised with a _start receipt_.
