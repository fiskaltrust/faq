## Question
Was ist ein Stopp-Beleg?

## Metadata tags
lang-de, lang-at, market-all, middleware, PosCreator, PosDealer, PosOperator, Consultant

## Answer
Der _Stopp-Beleg_ ist für die geplante Außerbetriebnahme von Sicherheitsmechanismen und/oder Registrierkassen erforderlich. Mit diesem Beleg wird die Verkettung der Belege, das Summieren der Umsatzzähler und die fortlaufende Belegnummerierung angehalten. Er schließt auch das Datenerfassungsprotokoll ab.

Dieser Beleg erhält nur beim ersten Mal eine aussagekräftige Antwort vom fiskaltrust.SecurityMechanism. Nach Erhalt eines _Stopp-Belegs_ wird die Queue endgültig und unwiderruflich geschlossen. Falls eine Quittung an eine geschlossene Warteschlange gesendet wird, sendet der fiskaltrust.SecurityMechanism keine positive Antwort.

Eine geschlossene Warteschlange kann mit einem _Start-Beleg_ nicht erneut eröffnet werden. Stattdessen muss eine neue Warteschlange erzeugt und mit einem eigenen _Start-Beleg_ initialisiert werden.
