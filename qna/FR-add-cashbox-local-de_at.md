## Question
Wie erstelle ich eine CashBox (lokal)

## Metadata tags
lang-de, lang-at, market-fr, middleware, PosCreator, PosDealer, PosOperator, Consultant

## Answer
Für die Erstellung einer CashBox müssen einige Voraussetzungen erfüllt sein.

Zunächst muss eine gültige SIREN in die Stammdaten des Unternehmens eingetragen und eingecheckt werden. Der zweite Schritt ist eine gültige Verkaufsstelle (Outlet). Dazu muss die Adresse des Outlets und eine SIRET eingegeben und überprüft werden.

**Erster Schritt:**<br>Erstellen Sie im Konfigurationsmenü eine Signaturerstellungseinheit (SCU). Während der Erstellung müssen Sie die richtige Verkaufsstelle auswählen.

**Zweiter Schritt:**<br>Gehen Sie zum Konfigurationsmenü und öffnen Sie den Befehl Queue. Durch Klicken auf die Schaltfläche Neu anlegen starten Sie die Erstellung. Akzeptieren Sie das vorausgewählte SQLite-Paket. Die Package Version sollte das neueste 1.2-Paket sein (ohne das Postfix “-dev“). Die Standort ID muss mit der im vorherigen Schritt ausgewählten identisch sein. Fügen Sie eine eindeutige CashBox Identifikation hinzu.

Speichern Sie diese Konfiguration und fügen Sie im folgenden Fenster eine http-URL hinzu, ohne einen der anderen Werte zu ändern. Speichern Sie die Konfiguration.

**Dritter Schritt:**<br>Suchen Sie die kürzlich erstellte Warteschlange in der Liste. Auf der rechten Seite befinden sich vier Konfigurationsschaltflächen. Klicken Sie auf das erste (das Rechteck mit dem Pfeil). Wählen Sie die SCU aus, die Sie im ersten Schritt erstellt haben, und klicken Sie auf Speichern und schließen.

Seien Sie vorsichtig bei diesem Schritt, die SCU kann für diese Warteschlange nachträglich nicht mehr geändert werden.

**Vierter Schritt:**<br>Im CashBox-Befehl des Konfigurationsmenüs müssen Sie auf die Schaltfläche + Hinzufügen klicken. Geben Sie eine Beschreibung ein und wählen Sie erneut dieselbe Verkaufsstelle wie in den vorherigen Schritten. Nachdem Sie auf Speichern geklickt haben, finden Sie eine neue CashBox in der Liste. Klicken Sie auf die Schaltfläche mit dem Hand-Symbol. Ziehen Sie nun die kürzlich erstellte Warteschlange von links nach rechts. Überprüfen Sie, ob die richtige Verkaufsstelle ausgewählt ist, und klicken Sie auf Speichern.

**Letzter Schritt:**<br>Klicken Sie in der Zeile der CashBox auf die Schaltfläche Rebuild Configuration (Kreispfeile).
Jetzt können Sie einen der drei Launcher herunterladen und den fiskaltrust.Service auf Ihrem lokalen Computer installieren.
