## Question

Was passiert wenn eine TSE ausfällt?

## Metadata tags

lang-de, market-de, middleware, PosCreator, PosDealer, Consultant

## Answer

Bei einem Ausfall der TSE darf mit der Kasse weiter gearbeitet werden (siehe Punkt 7 des AEAO zu § 146a: https://www.bundesfinanzministerium.de/Content/DE/FAQ/2020-02-18-steuergerechtigkeit-belegpflicht.html)


Die lokale fiskaltrust.Middleware speichert in der lokalen Datenbank alle Daten und kann somit alle Funktionen – insbesondere DSFinV-K-Export, PosArchiv, AKO, usw. weiter lückenlos und sicher anbieten.

Nach Wiederherstellung der Kommunikation mit der TSE ist das Senden eines Nullbeleges durch die Kassa an die ft.MW erforderlich. Mit diesem Nullbeleg versucht die Middleware den ordnungsgemäßen Betrieb mit der TSE wieder herzustellen. Wir empfehlen, diesen Nullbeleg durch einen Benutzereingriff zu veranlassen, da hierdurch der laufende Betrieb der Kassa möglichst wenig beeinflusst wird. Falls die Kommunikation mit der ft.MW weiterhin nicht möglich ist, muss der Vorgang, ein Nullbeleg zu senden, wiederholt werden, bis die Kommunikation mit der TSE wieder ordnungsgemäß erfolgt.
Siehe: https://github.com/fiskaltrust/interface-doc/blob/master/doc/appendix-de-kassensichv/reference-tables/service-status-ftstate.md"
