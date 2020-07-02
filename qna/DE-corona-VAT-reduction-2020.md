## Question
Welche Änderungen ergeben sich aufgrund der befristeten Absenkung der Umsatzsteuersätze ab dem 01.07.2020?

## Question
Wird das fiskaltrust.iPOS aufgrund der Umsatzsteuersatzsenkung geändert?

## Metadata tags
lang-de, market-de, middleware, PosCreator, PosDealer, Consultant

## Answer

### Steuerliche Beurteilung

#### 1. Befristeten Absenkung der Umsatzsteuersätze von 19% auf 16% und von 7% auf 5%
Durch das zweite Corona-Steuerhilfegesetz werden vom 01.07.2020 bis 31.12.2020 der allgemeine Umsatzsteuersatz von 19% auf 16% (§ 12 Abs. 1 UStG) sowie der
ermäßigte Umsatzsteuersatz von 7% auf 5% (§ 12 Abs. 2 UStG) gesenkt.

#### 2. Befristete Absenkung des Umsatzsteuersatzes für Speisen in Restaurants und Gaststätten von 19% auf 7%
Die Regelung gilt ab dem 01.07.2020 und ist bis zum 30.06.2021 befristet.
Da die obige Regelung der Reduktion von 7% auf 5% (siehe 1.) auch für diesen Fall gilt, beträgt der Umsatzsteuersatz auf Speisen in Restaurants und Gaststätten 
- vom 1.7.2020 bis 31.12.2020: 5%
- vom 1.1.2020 bis 30.06.2020: 7%

Dies führt dazu, dass in allen Kassen zweimal, in Restaurants und Gaststätten dreimal Anpassungen vorgenommen werden müssen.

### Keine Änderung des fiskaltrust.iPOS
Das fiskaltrust.iPOS ist seit Beginn an derart flexibel aufgebaut und auf eine Änderung eines Steuersatzes vorbereitet, dass keine grundsätzliche Änderung erforderlich ist.

### Abbildung im json-request an die ft.Middleware
#### Änderung am 01.07.2020, am 01.01.2021 sowie am 01.07.2021
Die geänderte steuerliche Vorgabe ist durch korrekte json-requests an die ft.Middleware zu senden. Es ändert sich nur der Steuersatz, nicht jedoch die Leistungsart.
Dies bedeutet, dass die bisherigen ftChargeItemCases für den allgemeinen Umsatzsteuersatz (z.B. für Lieferungen 0x4445000000000011) 
sowie für den ermäßigten Umsatzsteuersatz (z.B. für Lieferungen 0x4445000000000012) ab 01.07.2020 weiter verwendet werden müssen.
https://docs.fiskaltrust.cloud/doc/interface-doc/doc/appendix-de-kassensichv/reference-tables/type-of-service-ftchargeitemcase.html

Die Kassa hat jedoch immer den korrekten Mehrwertsteuersatz im Feld VATRate zu senden. 

https://docs.fiskaltrust.cloud/doc/interface-doc/doc/general/data-structures/data-structures.html 

Daher ist 
- der"alte" Steuersatz von 19% bis zum 30.06.2020 und 
- der temporär, "neue" Steuersatz von 16% ab 01.07.2020 
im request zu senden.

Die Umstellung vom "alten" auf den "neuen" Steuersatz ist durch einen Tagesabschlusses (daily-closing request) zu trennen bzw. dadurch zu markieren.

### Zeitliche Zuordnung
Der Zeitpunkt der Ausführung einer Lieferungen bzw. einer sonstige Leistung ist für die Anwendung des korrekten Steuersatzes relevant.
Hiefür ist die steuerliche Beurteilung des Unternehmens z.B. durch eine/n SteuerberaterIn maßgeblich.

### Behandlung von Sonderfällen
Beispielsweise sind Anzahlungen, Vorauszahlungen, Jahreskarten, Abonnements, Dauerleistungen, Bauleistungen, Pfand, Einzweck- und Mehrzweckgutscheine in Hinblick auf diese zeitliche Zuordnung besonders zu behandeln.
In diesen Sonderfällen, welche zur Verwendung eines anderen (alten) Umsatzsteuersatzes führen, sind die jeweils korrekten Umsatzsteuersätze (19%, 16%, 7% oder 5%) im VATRate eines json-request zu verwenden.
Die ft.Middleware trennt die Umsatzsteuersätze aufgrund der gesendeten Information für den korrekten Export im DSFinV-K.

### TSE-ProcessData-Container sowie DSFinV-K Steuerpositionen
Die ft.Middleware verwendet die TSE entsprechend der BSI-Richtlinien sowie des DSFinV-K.
#### TSE-ProcessData-Container
Dies bedeutet, die fünf bestehenden TSE-ProcessData-Container bleiben erhalten und werden nicht erweitert. 1. Regelsteuersatz, 2. ermäßigter Steuersatz, usw.
#### DSFinV-K Steuerpositionen

In der folgenden Übersicht werden die Umsatzsteuerschlüssel mit Beschreibung und den Umsatzsteuersätzen dargestellt. Über die IDs 1 – 4 werden die im Zeitpunkt der Erfassung des Geschäftsvorfalls gültigen Umsatzsteuersätze nach §§ 12 und 24 UStG erfasst.

Ist für die Erfassung des Geschäftsvorfalls auch ein vormals gültiger Umsatzsteuersatz zu verwenden, werden hierfür die historischen Umsatzsteuersätze unter den IDs 11 bzw. 21 (allgemeiner Steuersatz) und 12 bzw. 22 (ermäßigter Steuersatzsatz) berücksichtigt.

Anpassungen (ab ID 1000) können individuell für den Unternehmer nach einem Kassenabschluss jederzeit vorgenommen werden und sind in den entsprechenden Systembeschreibungen bzw. Verfahrensdokumentationen zu dokumentieren.

Anpassungen der IDs bis 999 bleiben der DFKA-Taxonomie und der DSFinV-K vorbehalten und sind in den Begleitdokumenten bei Änderungen zu dokumentieren und zu erläutern." (Kap. 3.2.6)

| ID | USt-Satz | Beschreibung |
| :--- | :--- | :--- |
| 1 | | Zum Zeitpunkt der Erfassung des Geschäftsvorfalls geltender allgemeiner Steuersatz (§ 12 Abs. 1 UStG) |
| 2 | | Zum Zeitpunkt der Erfassung des Geschäftsvorfalls geltender ermäßigter Steuersatz (§ 12 Abs. 2 UStG) | 
| 3 | 10,70% | Durchschnittsatz (§ 24 Abs. 1 Nr. 3 UStG) übrige Fälle |
| 4 | 5,50% | Durchschnittsatz (§ 24 Abs. 1 Nr. 1 UStG) |
| 5 | 0,00% | Nicht Steuerbar |
| 6 | 0,00% | Umsatzsteuerfrei |
| 7 | 0,00% | UmsatzsteuerNichtErmittelbar |
| 11 | 19,00% | Historischer allgemeiner Steuersatz (§ 12 Abs. 1 UStG) |
| 12 | 7,00% | Historischer ermäßigter Steuersatz (§ 12 Abs. 2 UStG) |
| 21 | 16,00% | Historischer allgemeiner Steuersatz (§ 12 Abs. 1 UStG) |
| 22 | 5,00% | Historischer ermäßigter Steuersatz (§ 12 Abs. 2 UStG) |
| bis 999 | | reserviert für Änderungen DSFinV-K |
| ab 1000 | | individuelle Sachverhalte (§ 13b UStG, o.ä.) |

Da die Container (für die TSE) oder die IDs (für DSFinV-K) nicht für einen Steuersatz sondern einen Steuertyp stehen, sind durch die ft.Middleware alle Abbildungen möglich.

BMF-Entwurf eines begleitenden BMF-Schreibens ["Befristete Absenkung des allgemeinen und ermäßigten Umsatzsteuersatzes zum 1. Juli
2020":](https://www.bundesfinanzministerium.de/Content/DE/Downloads/BMF_Schreiben/Steuerarten/Umsatzsteuer/2020-06-23-befristete-Senkung-umsatzsteuer-juli-2020-erste-aktualisierung.pdf?__blob=publicationFile&v=2)

=======
Bundesregierung: [Steuerentlastungen-Coronavirus](https://www.bundesregierung.de/breg-de/themen/coronavirus/steuerentlastungen-coronavirus-1750826)

BMWI, 12.06.2020 -PRESSEMITTEILUNG: [Wirtschaftliche Entwicklung - Unbürokratische Umsetzung der Mehrwertsteuersenkung bei Preisangaben durch pauschale Rabatte möglich](https://www.bmwi.de/Redaktion/DE/Pressemitteilungen/2020/20200612-unbuerokratische-umsetzung-der-mehrwertsteuersenkung-bei-preisangaben-durch-pauschale-rabatte-moeglich.html)
