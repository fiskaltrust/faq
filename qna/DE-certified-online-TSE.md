## Question
Is there any certified Cloud TSE available for Germany?

## Question

I want to roll out with a Cloud TSE and  I do not want to wait any longer. What options do I have?

## Question

I have ordered a Cloud TSE from my dealer. Can I use an uncertified Cloud TSE in my region until a certified version is available?

## Metadata tags
lang-en, market-de, middleware, PosCreator, PosDealer, Consultant

## Answer
Currently (23.09.2020), there is **no certified** Cloud TSE available for the german market. fiskaltrust will offer certified Cloud TSE's in the production environment as soon as they are available on the market. In the meanwhile, we provide uncertified Cloud SignatureCreationUnits for integration and testing in the sandbox environment.

PosDealers can already order fiskaly Cloud TSEs from fiskaltrust by [signing a frame contract.](https://github.com/fiskaltrust/productdescription-de-doc/blob/8a9c3fa62c9dd0c38662c7127a724162703242e3/for-posdealers/02-pre-sales/01-purchase-agreement.md)

If a PosOperator wants to be compliant from now on in a production environment, we recommend to use certified Hardware TSE's.

In general, if PosOperators are using an uncertified TSE in production environment or no TSE at all, it will both result in generating POS-receipts which are not compliant to German law. In most regions of Germany it may be possible to [extend the "Nichtbeanstandungsregelung" under some specific circumstances](https://github.com/fiskaltrust/faq/blob/master/qna/DE-Nichtbeanstandungsregelung.md#regionale-erg%C3%A4nzungen-zur-nichtbeanstandungsregelung). We recommend to refer to a tax advisor to ensure to fulfil all requirements to be fully compliant with the German law.

If all conditions for regional extensions of the "Nichtbeanstandungsregelung" are met, it is possible to already use the fiskaltrust.Middleware to prepare a Cloud-TSE rollout. In this case, it is technically possible to start without Cloud TSE, SCU and initial operation receipt, but already profiting from the fiskaltrust.SecurityMechanism and collecting data for the DSFinV-K export by only using the Queue within a Cashbox.
