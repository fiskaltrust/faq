## Question
Welche (Fehler)Meldungen können bei der automatisierten Kommunikation mit FinanzOnline auftreten?

## Metadata tags

lang-de, market-at, portal, webshop, bundle-carefree, consulting, documentation, security, PosDealer, PosOperator, PosCreator, Consultant

## Answer

Folgende (Fehler)Meldungen können bei der automatisierten Kommunikation mit FinanzOnline auftreten:

### RC:0 = Aufruf OK 

Die Verarbeitung der Meldung bzw. Belegprüfung bei FinanzOnline konnte erfolgreich durchgeführt werden.

Es ist kein weiterer Eingriff erforderlich, bitte kontrollieren Sie dennoch, ob alle notwendigen Meldungen/Prüfungen korrekt durchgeführt wurden. Die Rückmeldung „Aufruf ok“ bezieht sich nur auf die technisch korrekte Durchführung des Vorgangs.

### RC:-2 = Der Aufruf des Webservices ist wegen Wartungsarbeiten nicht möglich.

FinanzOnline ist temporär nicht verfügbar, es ist daher keine automatisierte Übermittlung möglich.

Die Wartungsarbeiten bei FinanzOnline müssen abgewartet werden, bitte kontrollieren Sie danach ob alle offenen Meldungen/Prüfungen erfolgreich durchgeführt werden konnten.

Beachten Sie hierbei auch unsere News zum Betriebsstatus.

### RC:-3 = Es ist ein technischer Fehler aufgetreten.

Hierbei handelt es sich um einen technischen Fehler seitens FinanzOnline.

Kontaktieren Sie die BMF Hotline unter +43 50 233790

### RC: 4 = Mit der angegebenen Seriennummer konnte beim angegebenen Vertrauensdiensteanbieter kein Zertifikat gefunden werden.

Bei manueller Anmeldung des Zertifikats bei FinanzOnline wurde entweder eine falsche Seriennummer eingetragen oder ein abweichender Vertrauensdiensteanbieter ausgewählt.

Sie können die Anmeldung des Zertifikats automatisch über das fiskaltrust.Portal durchführen, hierbei kann es nicht zu solchen Abweichungen kommen.

### RC: 7 = Der Ordnungsbegriff im Zertifikat ist nicht dem registrierten Unternehmen zugeordnet. Wenden Sie sich bitte an Ihren Vetrauensdiensteanbieter.

Das Zertifikat wurde auf eine abweichende UID-Nummer personalisiert. Bitte kontrollieren Sie die UID-Nummer und erwerben ein neues Zertifikat, sollte dieses nicht korrekt personalisiert sein.

oder:

Sie haben einen WebService User im fiskaltrust.Portal eingetragen, welcher nicht zu Ihrem Unternehmen gehört. Prüfen Sie den WebService User oder legen Sie einen neuen in FinanzOnline an und aktualisieren Sie diesen im fiskaltrust.Portal.

### RC: B1= Die Registrierkasse mit der angegebenen Kassenidentifikationsnummer ist bereits registriert.

Es wurde in FinanzOnline bereits eine Kasse mit dieser KassenID angemeldet. Dies kann manuell direkt in FinanzOnline oder in einer vorangegangenen automatischen Meldung im fiskaltrust.Portal durchgeführt worden sein.

Achtung: FinanzOnline gleich nur die KassenID ab, eine Prüfung des AES-Schlüssels wird hier nicht durchgeführt. Sollte manuell ein abweichender AES-Schlüssel eingegeben worden sein, so ist keine korrekte Belegprüfung möglich.

### RC: B5= Der angegebene Zeitpunkt darf nicht vor dem Zeitpunkt der letzten Statusänderung liegen.

Es wurde versucht eine Meldung (Ausfall- oder Wiederinbetriebnahme) abzusetzen, ohne die chronologische Reihenfolge zu beachten. Bei FinanzOnline werden Meldungen nur in der korrekten Reihenfolge akzeptiert, sollte zwischenzeitlich etwas manuell direkt in FinanzOnline gemeldet worden sein, so kann es bei den automatisierten Meldungen über das fiskaltrust.Portal zu einer solchen Fehlermeldung kommen.

Bitte kontrollieren Sie den aktuell gesetzten Status für Ihre Registrierkasse oder Ihr Zertifikat mittels Statusprüfung, sofern dieser mit dem tatsächlichen Status (in Betrieb oder ausgefallen) übereinstimmt, so markieren Sie die fehlgeschlagene Meldung als „ignorieren fehlgeschlagen“.

### RC: B8= Nur in Betrieb befindliche registrierte oder ausgefallene Registrierkassen dürfen außer Betrieb genommen werden.

Es wurde versucht eine Registrierkasse außer Betrieb zu nehmen, welche noch nicht in Betrieb genommen wurde oder aktuell den Status außer Betrieb hat.

Sollte die Registrierkasse noch nicht in Betrieb genommen worden sein, so ist eine Außerbetriebnahme nicht notwendig, bitte markieren Sie die Meldung im fiskaltrust.Portal als „ignorieren fehlgeschlagen“.

Sollte die Registrierkasse temporär außer Betrieb genommen worden sein, so müssen Sie diese zunächst wieder in Betrieb melden (automatisiert über das fiskaltrust.Portal möglich) um Sie in Folge außer Betrieb zu nehmen.

Achtung – bei der Außerbetriebnahme handelt es sich um eine endgültige Abmeldung der Registrierkasse, sollten Sie einen temporären Ausfall melden wollen, so wählen Sie bitte die Option „als ausgefallen melden“.

### RC: B9= Nur in Betrieb befindliche Registrierkassen dürfen als ausgefallen gemeldet werden.

Es wurde versucht eine Registrierkasse als temporär ausgefallen zu melden, welche noch nicht in Betrieb genommen wurde.

Kontrollieren Sie die Anmeldung Ihrer Registrierkasse bei FinanzOnline oder erstellen Sie eine automatisierte Inbetriebnahmemeldung im fiskaltrust.Portal. Anschließend kann der Ausfall automatisch gemeldet werden.

### RC: B18= Nur in Betrieb befindliche oder ausgefallene Signaturerstellungseinheiten dürfen endgültig außer Betrieb genommen werden.

Es wurde versucht eine Signaturerstellungseinheit außer Betrieb zu nehmen, welche noch nicht in Betrieb genommen wurde oder aktuell den Status außer Betrieb hat.

Sollte die Signaturerstellungseinheit noch nicht in Betrieb genommen worden sein, so ist eine Außerbetriebnahme nicht notwendig, bitte markieren Sie die Meldung im fiskaltrust.Portal als „ignorieren fehlgeschlagen“.

Sollte die Signaturerstellungseinheit temporär außer Betrieb genommen worden sein, so müssen Sie diese zunächst wieder in Betrieb melden (automatisiert über das fiskaltrust.Portal möglich) um Sie in Folge außer Betrieb zu nehmen.

Achtung – bei der Außerbetriebnahme handelt es sich um eine endgültige Abmeldung der Signaturerstellungseinheit, sollten Sie einen temporären Ausfall melden wollen, so wählen Sie bitte die Option „als ausgefallen melden“.

### RC: B19= Nur in Betrieb befindliche Signaturerstellungseinheiten dürfen als ausgefallen gemeldet werden.

Es wurde versucht eine Signaturerstellungseinheit als temporär ausgefallen zu melden welche noch nicht in Betrieb genommen wurde.

Kontrollieren Sie die Anmeldung Ihrer Signaturerstellungseinheit bei FinanzOnline oder erstellen Sie eine automatisierte Inbetriebnahmemeldung im fiskaltrust.Portal. Anschließend kann der Ausfall automatisch gemeldet werden.

### Fehlermeldung: Obwohl der vorliegende Beleg gesetzeskonform zustande gekommen ist, war die Registrierkasse zum Belegerstellungzeitpunkt laut FinanzOnline als „ausgefallen“ gemeldet. Bitte melden Sie das Ende des Ausfalls über FinanzOnline.

Es wurde ein Beleg zur Prüfung übermittelt, welcher korrekt erstellt und signiert ist, allerdings zu einem Zeitpunkt als  die Registrierkasse als temporär ausgefallen gemeldet war.

Kontrollieren Sie den aktuellen Status Ihrer Registrierkasse bei FinanzOnline (automatisiert über das fiskaltrust.Portal möglich) und erstellen Sie, falls notwendig, einen neuen Beleg sobald die Kasse wieder in Betrieb gemeldet wurde.

### Fehlermeldung: Der vorliegende Startbeleg passt nicht zum aktuellen Stand der Registrierung Ihrer Registrierkasse in FinanzOnline.

Es wurde ein Startbeleg geprüft, welcher zu einem Zeitpunkt erstellt wurde, an dem die Registrierkasse nicht korrekt bei FinanzOnline angemeldet war.

Prüfen Sie die Anmeldung der Registrierkasse in FinanzOnline und führen Sie diese ggf. erneut durch (automatisiert über das fiskaltrust.Portal möglich). Sollte dies nicht ausreichen um den vorliegenden Startbeleg korrekt zu prüfen, so ist die Erstellung eines neuen Starbelegs erforderlich. Kontaktieren Sie unseren Support.

### Fehlermeldung: Der vorliegende Beleg kann nicht gültig geprüft werden, da die im maschinenlesbaren Code angegebene Kassenidentifikationsnummer keiner über FinanzOnline registrierten Kasse zugeordnet werden konnte.

Es wurde ein Startbeleg zur Prüfung übermittelt, welcher zu einem Zeitpunkt erstellt wurde, an dem die Registrierkasse nicht oder nicht korrekt bei FinanzOnline angemeldet war.

Prüfen Sie die Anmeldung Ihrer Registrierkasse in FinanzOnline und führen Sie diese ggf. (erneut) durch (automatisiert über das fiskaltrust.Portal möglich). Sollte bei der Anmeldung ein falscher AES-Schlüssel angegeben worden sein, so ist dieser in FinanzOnline zu berichtigen bevor eine korrekte Prüfung möglich ist.

### Fehlermeldung: Der vorliegende Beleg konnte nicht gültig geprüft werden, da die zur Belegerstellung verwendete Signatur- bzw. Siegelerstellungseinheit laut FinanzOnline nicht auf Ihr Unternehmen registriert wurde.

Es wurde ein Startbeleg zur Prüfung übermittelt, welcher zu einem Zeitpunkt erstellt wurde, an dem die Signaturerstellungseinheit nicht oder nicht korrekt bei FinanzOnline angemeldet war.

Prüfen Sie die Anmeldung Ihrer Signaturerstellungseinheit in FinanzOnline und führen Sie diese ggf. (erneut) durch (automatisiert über das fiskaltrust.Portal möglich). Sollte bei der Anmeldung eine falsche Zertifikatsseriennummer oder ein abweichender Vertrauensdiensteanbieter angegeben worden sein, so ist dies in FinanzOnline zu berichtigen, bevor eine korrekte Prüfung möglich ist.

### fiskaltrust Statuscodes der Meldungen sowie Belegprüfungen im Portal K

| FinanzOnline Meldungen          |                                                              |
| ------------------------------- | ------------------------------------------------------------ |
| done                            | Meldung/ Statusabfrage erfolgreich an FinanzOnline übermittelt |
| new                             | Meldung empfangen, noch nicht verarbeitet                    |
| redirect                        | Verarbeitung der Meldung begonnen, warte auf Rückmeldung von FinanzOnline |
| incident                        | Verarbeitung der Meldung begonnen, kein Anspruch vorhanden. Erwerb einer Meldung RK oder SEE erforderlich. Upgrade auf Sorglos möglich. |
| donemanual                      | Manuell eingetragener Status welcher signalisiert dass diese Meldungen durch den Steuerpflichtigen oder seinen steuerlichen Vertreter manuell in FinanzOnline durchgeführt wurde. |
| duplicated                      | Interne Duplikatserkennung. Diese Meldung wird nicht ein zweites Mal an FinanzOnline übermittelt. |
| duplicatedmanual                | Manuelle Anwahl um Duplikate nicht weiter zu verarbeiten.    |
| duplicatedignore                | Manuelle Anwahl um Duplikate nicht weiter zu verarbeiten.    |
| donebyconsultant                | Manuelle Anwahl für Meldungen welche durch den Berater / steuerlichen Vertreter in FinanzOnline durchgeführt wurden. |
| failed                          | Keine Meldung an FinanzOnline, die Rückmeldung in den Details enthält weitere Informationen. |
| failedignore                    | Manuelle Anwahl um eine fehlgeschlagene Meldung nicht erneut zu verarbeiten. |
|                                 |                                                              |
|                                 |                                                              |
| **FinanzOnline Belegprüfungen** |                                                              |
| valid                           | Dieser Beleg wurde korrekt geprüft.                          |
| new                             | Belegprüfung empfangen, noch nicht verarbeitet               |
| incident                        | Verarbeitung der Belegprüfung begonnen, kein Anspruch vorhanden. Erwerb einer FOn Belegprüfung erforderlich. Upgrade auf Sorglos möglich. |
| redirect                        | Verarbeitung der Meldung begonnen, warte auf Rückmeldung von FinanzOnline. |
| validmanual                     | Manuell eingetragener Status welcher signalisiert dass dieser Beleg durch den Steuerpflichtigen oder seinen steuerlichen Vertreter erfolgreich manuell in FinanzOnline geprüft wurde. |
| validbyconsultant               | Manuelle Anwahl für Belegprüfungen welche durch den Berater / steuerlichen Vertreter in FinanzOnline durchgeführt wurden. |
| invalid                         | Belegprüfung fehlerhaft, die Rückmeldung in den Details enthält weitere Informationen. |
| invalidignore                   | Manuelle Anwahl um eine fehlgeschlagene Belegprüfung nicht erneut zu verarbeiten. |
| invalidbyconsultant             | Manuelle Anwahl um eine fehlgeschlagene Belegprüfung nicht erneut zu verarbeiten. |
| invalidmanual                   | Manuelle Anwahl um eine fehlgeschlagene Belegprüfung nicht erneut zu verarbeiten. |
| duplicated                      | Interne DuplikatserkennungDiese Meldung wird nicht ein zweites Mal an FinanzOnline übermittelt. |
| duplicatedignore                | Manuelle Anwahl um Duplikate nicht weiter zu verarbeiten.    |

------

Diese Inhalte sind urheberrechtlich und dürfen nur mit schriftlicher Genehmigung von fiskaltrust weiter verwendet werden.
Alle Preise und Informationen vorbehaltlich Irrtum und Änderungen. Stand 04.04.2019.