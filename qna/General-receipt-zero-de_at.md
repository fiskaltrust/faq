## Question
Was ist ein Null-Beleg?

## Metadata tags
lang-de, lang-at, market-all, middleware, PosCreator, PosDealer, PosOperator, Consultant

## Answer
Ein Null-Beleg ist für den fiskaltrust.Middleware ein universeller Datenträger und Speichermedium. Die Registrierkasse sendet einen Beleg mit einem leeren Produktblock (_ftChargeItem_) und einem leeren Zahlungsblock (_ftPayItem_), die logischerweise einen Gesamtbetrag von “0,00” enthalten.

Der fiskaltrust.SecurityMechanism sendet die erforderlichen Blöcke, z. B. den Belegkopf, den Produktblock und den Signaturblock in der Antwort. Diese Antwort wird entweder gedruckt oder elektronisch ausgegeben und muss archiviert werden.

Beispielsweise ist ein Start- oder Stoppbeleg ein Sonderfall eines Null-Belegs.
