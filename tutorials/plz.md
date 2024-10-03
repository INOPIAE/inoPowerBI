# PLZ Bereiche in Power BI

Um deutsche PLZ-Bereiche in Power BI in Flächenkartogrammen darzustellen müssen die Flächenkartogramme in den Optionen von Power BI aktiviert sein.

## Aktivieren von Flächenkartogrammen

![Screenshot Optionen Sicherheitseinstellungen](/sources/plz_optionen1.png)

![Screenshot Optionen Vorschaufeatures](/sources/plz_optionen2.png)

## Einbetten der PLZ-Bereiche in Flächenkartogramme

Zunächst wird ein Flächenkartogramm eingefügt.

![Screenshot Flächenkartogramm einfügen](/sources/plz_flaechenkartogramm.png)

Anschließend wird ein Wert zugewiesen.

Nun wird in den Formateinstellungen in den Karteneinstellungen die Benutzerdefinierte Karte ausgewählt.

![Screenshot Karteneinstellungen](/sources/plz_karteneinstellungen.png)

Danach wird ein Zuordnungstyp ausgewählt. Diese finden sich im Ordner [/samples/plz_d/](/samples/plz_d/).

![Screenshot Zuordnungstyp auswählen](/sources/plz_karteneinstellungen1.png)

Beispiel mit dem 1-stelligen PLZ-Bereich.

![Screenshot Beispiuel 1stelliger PLZ-Bereich](/sources/plz_karte_1stellig.png)

Die Postleitzahlen müssen als Textdaten vorliegen.

Ein Besipiel findet sich [hier](/samples/plz_d/plz.pbix) 

## Erstellung Kartenmaterial

Die Idee zur Erstellung der Zuordnungstypen stammt aus dem Video [https://www.youtube.com/watch?v=ycPf8EmYdFQ](https://www.youtube.com/watch?v=ycPf8EmYdFQ).

Die Rohdaten können von hier [https://www.suche-postleitzahl.org/downloads](https://www.suche-postleitzahl.org/downloads) bezogen werden.

Die Daten werden über [https://mapshaper.org/](https://mapshaper.org/) in die Zuordungsdaten umgewandelt.
