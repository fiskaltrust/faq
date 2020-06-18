## Question

Was passiert wenn eine TSE ausfällt?

## Metadata tags

lang-de, market-de, middleware, PosCreator, PosDealer, Consultant

## Answer

Bei einem Ausfall der TSE darf mit der Kasse weiter gearbeitet werden (siehe Punkt 7 des AEAO zu § 146a: https://www.bundesfinanzministerium.de/Content/DE/FAQ/2020-02-18-steuergerechtigkeit-belegpflicht.html)


Die lokale fiskaltrust.Middleware speichert in der lokalen Datenbank alle Daten und kann somit alle Funktionen – insbesondere DSFinV-K-Export, PosArchiv, AKO, usw. weiter lückenlos und sicher anbieten.

Wichtig ist nach Beseitigung des Ausfallgrundes das Absetzen eines Nullbeleges, damit die Middleware die Kommunikation mit der TSE wieder aufnimmt: https://docs.fiskaltrust.cloud/doc/interface-doc/doc/appendix-de-kassensichv/reference-tables/service-status-ftstate.html