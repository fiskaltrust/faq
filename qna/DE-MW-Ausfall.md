## Question

Was passiert wenn die fiskaltrust.Middleware nicht erreichbar ist?

## Metadata tags

lang-de, market-de, middleware, PosCreator, PosDealer, Consultant

## Answer

Bei einem Ausfall der fiskaltrust.Middleware darf mit der Kasse weiter gearbeitet werden (siehe Punkt 7 des AEAO zu § 146a: https://www.bundesfinanzministerium.de/Content/DE/FAQ/2020-02-18-steuergerechtigkeit-belegpflicht.html)

Die TSE ist in dem Fall ebenso nicht erreichbar.

- Die Kasse kann im „Ausfallmodus“ weiter betrieben werden.
- Durch die Nacherfassung der ausgefallenen Belege können alle Daten, die während des Ausfalls von der Kasse gespeichert wurden, an die fiskaltrust.Middelware gesendet werden, sobald diese wieder erreichbar ist. 

Durch die Nacherfassung können alle gesetzlich erforderlichen Funktionen wie z.B. DSFinV-K-Export, PosArchiv, AKO, usw. dennoch erfüllt werden.
Die Behandlung des Ausfalls wird in der Interface-Dokumentation in [docs.fiskaltrust](https://docs.fiskaltrust.cloud/doc/interface-doc/doc/general/cash-register-integration/cash-register-integration.html#workflow---failure-of-communication-or-failure-of-the-fiskaltrustmiddleware-timeout) beschrieben.

