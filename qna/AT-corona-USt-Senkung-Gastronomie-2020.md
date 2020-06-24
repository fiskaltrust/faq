## Question
Was haben Kassenhersteller im Zusammenhang mit der Einführung des 5%igen Umsatzsteuersatzes ab 1.7.2020 zu beachten?

## Question
Welche Varianten gibt es bei technische Umstellung der Registrierkassen auf den reduzierten Umsatzsteuersatz 2020 gibt es?

## Question
Information des BMF zur Umstellung Registrierkassen betreffend Einführung des 5%igen Umsatzsteuersatzes?

## Metadata tags
lang-de, market-at, middleware, PosCreator, PosDealer, Consultant

## Answer

### Information des BMF betreffend die Umsatzsteuersenkung
Zur Unterstützung der Gastronomie, der Kulturbranche sowie des Publikationsbereichs, die von der COVID-19-Krise in einem besonderen Ausmaß betroffen sind, soll zusätzlich zu den bisher getroffenen Maßnahmen, befristet vom 1.7.2020 bis 31.12.2020 ein ermäßigter Umsatzsteuersatz iHv 5% eingeführt werden.

BMF, 24.06.2020
- [Information betreffend die Umsatzsteuersenkung](https://www.bmf.gv.at/dam/jcr:47c824a7-5ab7-413e-af28-e0f7565a0efe/Information%20betreffend%20die%20Umsatzsteuersenkung.pdf)
- [NEU: Senkung des Umsatzsteuersatzes auf 5% und Auswirkungen auf Registrierkassen](https://www.bmf.gv.at/public/informationen/informationen-coronavirus/registrierkassen.html)

### Einhaltung der Bestimmungen für Registrierkassen
Der Erlass zur Einzelaufzeichnungs-, Registrierkassen- und Belegerteilungspflicht enthält hinsichtlich der Sicherheitseinrichtung (RKSV) bereits jetzt eine Auffang-Regelung (Zuweisung zum Betrag-Satz-Null), die den angekündigten 5%-Steuersatz abdeckt. Diese Auffang-Regelung wird beibehalten und ergänzt.

Es ist beabsichtigt, darüber hinaus 3 weitere Alternativen zu ermöglichen. Die Alternativen stellen sich somit wie folgt dar:

------------- Für den Fall der gesetzlichen Umsetzung des 5%-igen Umsatzsteuersatzes beabsichtigte Regelungen ----------

### Zur Signatur- bzw. Siegelerstellung:
Umsätze, welche nach den Übergangsbestimmungen gemäß § 28 UStG einem ermäßigten Steuersatz unterliegen, welcher von den Steuersätzen gemäß § 10 UStG abweicht, werden wie folgt einem Betrag-Satz oder in Alternative 4 mehreren Betrag-Sätzen zuzuordnen sein: entweder Alternative 1: dem Feld Betrag-Satz-Null oder Alternative 2: dem Feld Betrag-Satz-Besonders Alternative 3: dem Feld Betrag-Satz-Ermaessigt-1 oder Alternative 4: den bisherigen Feldern nach § 10 UStG

Die gewählte Variante ist zu dokumentieren (beispielsweise durch Aufbewahrung einer diesbezüglichen Information zur Registrierkassa bzw. zum Kassensystem). Sofern bei Verwendung mehrerer Registrierkassen durch einen Unternehmer unterschiedliche Alternativen zum Einsatz kommen, ist pro Registrierkasse zu dokumentieren, welche Alternative gewählt wurde.

### Zur Belegausstellung:
Umsätze, welche nach den Übergangsbestimmungen gemäß § 28 UStG dem ermäßigten Steuersatz von 5 % unterliegen, sind auf dem Beleg unter diesem ermäßigten Steuersatz von 5% auszuweisen.

Es bestehen auch keine Bedenken, wenn dieser Ausweis des ermäßigten Steuersatzes von 5 % durch eine entsprechende Textanmerkung auf dem Beleg erfolgt, oder eine händische Korrektur bzw. eine Korrektur mittels eines Stempels auf dem Beleg vorgenommen wird.“

### Kommentar fiskaltrust:
Bei korrekter Verwendung des fiskaltrust.Interface sind alle zulässigen Varianten des BMF möglich.
Auch der RKSV-Export wird entsprechend korrekt erstellt.
Infos für Kassenhersteller zur korrekten Verwendung der Steuersätze sind hier zu finden: [https://docs.fiskaltrust.cloud / AT-ftChargeItemCases](https://docs.fiskaltrust.cloud/doc/interface-doc/doc/appendix-at-rksv/reference-tables/reference-tables.html#type-of-service-ftchargeitemcase)

### Muster zur Dokumentation der gewählten Variante zur Abbildung des 5%-igen USt-Satzes

| Unternehmen: | Fröhlicher Kassenbetreiber GmbH |
| :--- | :--- |
| Finanzamt/Steuernummer: |09-123/4567 |
| Kassenidentifikationsnummer: | fiskaltrust1 |

Die Abbildung des Umsätze mit dem reduzierten Steuersatzes in Höhe von 5% im Zeitraum nach dem 30.6.2020 bis vor dem 1.1.2021 wird wie folgt dokumentiert.

#### 1. Signatur- bzw. Siegelerstellung:

Umsätze, welche nach den Übergangsbestimmungen gemäß § 28 UStG einem ermäßigten Steuersatz unterliegen, welcher von den Steuersätzen gemäß § 10 UStG abweicht, werden nach der folgenden Variante zugeordnet:

- [ ] Alternative 1: Feld Betrag-Satz-Null oder
- [ ] Alternative 2: Feld Betrag-Satz-Besonders
- [ ] Alternative 3: Feld Betrag-Satz-Ermaessigt-1 oder
- [ ] Alternative 4: Bisher verwendete Felder nach § 10 UStG (20%, 10%, 13% bzw. Besonders)

#### 2. Zur Belegausstellung:

Der Ausweis des ermäßigten Steuersatzes von 5 % auf dem Beleg erfolgt, auf dem Beleg durch:

- [ ] korrekte Darstellung des Steuersatzes von 5 %
- [ ] entsprechende Textanmerkung, dass der korrekte Steuersatzes 5 % ist
- [ ] händische Korrektur, dass der Steuersatzes 5 % beträgt
- [ ] Korrektur mittels eines Stempels, dass der Steuersatzes 5 % beträgt

| Datum | Unterschrift für den Steuerpflichtigen: |
| :--- | :--- |
| __________________ | ______________________________________________________ |


