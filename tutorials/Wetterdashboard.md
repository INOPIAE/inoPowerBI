# Wetter Dashboard

Das Wetter Dashboard bezieht seine Daten kostenfrei von [https://openweathermap.org/](https://openweathermap.org/).

Die Daten werden per Power Automate mittels REST API regelmäßig in einem SharePoint-Ordner abgelegt.

Power BI aktualisiert regelmäßig die Daten aus dem SharePoint-Ordner.

## Vorarbeiten

### Openwathermap

Zunächst muss ein Konto auf [https://openweathermap.org/](https://openweathermap.org/) angelegt werden und dort wird ein API Key angelegt.

![Screenshot API Seite auswählen](/sources/wetter-API-Key-Menue.png)

Nach dem Einloggen wird über My API keys die Seite zur Verwaltung der API Keys geöffnet.

![Screenshot API Keys verwalten](/sources/wetter-API-Key-Seite.png)

Bei Create Key wird der NAme des Projektes ein gegebn und mit Generate ein neuer API Key erstellt.

Dieser wird in den Power Automate Prozessen benötigt.

### SharePoint

Auf der eigenen Sharepoint-Umgebung muss eine SharePoint Site angelegt sein. 

Dort wird ein Ordner mit dieser Struktur angelegt:

Ordner
- Dashboard
- Daten
    - forecast
    - historie

![Screenshot Ordnerstruktur](/sources/wetter-ordnerstruktur.png)

Im Ordner Dashboard wird das Dashboard abgelegt.

Im Ordner Daten werden die notwendigen Daten abgelegt.
Dies sind die Datei orte.xlsx, die die Angaben zu den Orten enthält, deren Daten ausgewertet werden sollen, und die Datei weathertranslation.xlsx, die die Übersetzung zu den Wettersymbolen enthält.

Im Ordner Daten - forecast werden die Daten der 5 Tagesprognose über Power Automate in Dateien mit dem Namen forecast-XX.json abgelegt.

Im Ordner Daten - historie werden stündlich die aktuellen Wetterdaten über Power Automate in Dateien mit dem Namen data-XX-YYYYMMDD_hhmm.json abgelegt.

## Arbeiten in Power Automate

Es werden zwei Flows in Power Automate angelegt. Diese können manuell angelegt werden oder über die beiden Zip-Dateien  im Ordner [/samples/wetter/](/samples/wetter/) importiert werden. 

Falls die Dateien importiert werden, müssen diese gemäß der weiteren Angaben angepasst werden. Der Import wird [hier](https://github.com/INOPIAE/inoPowerAutomate/blob/master/tutorials/importexportflow.md) beschrieben.


### Forecast

Der Flow für den Forecast sieht so aus:

![Screenshot Flow Forecast](/sources/wetter-forecast-flow.png)

Einstellungen für den Abruf der Koordinaten aus der Datei orte.xlsx.

![Screenshot Orte Abfruf](/sources/wetter-forecast-tabelle.png)

Einstellungen für den API Abruf

![Screenshot API Forecast](/sources/wetter-forecast-http.png)

Hier müssen folgende Werte angepasst werden:
- appid mit dem API Key von openweathermap

Einstellung für das Speichern der Daten

![Screenshot Datei Forecast](/sources/wetter-forecast-datei.png)

Hier müssen folgende Werte angepasst werden:
- Webseiteadresse mit der URL zu SharePoint Site. Dieser wird über das Dropdownmenü ausgewählt.
- Ordnerpfad mit dem Pfad zum Datenordner. Dieser wird über das Menü ausgewählt.

### Historie

Der Flow für den stündlichen Abruf der Historie sieht so aus:

![Screenshot Flow Stündlich](/sources/wetter-stündlich-flow.png)

Einstellungen für den Zeitstempel

![Screenshot API Stündlich](/sources/wetter-stündlich-zeitstempel.png)

Einstellungen für den Abruf der Koordinaten aus der Datei orte.xlsx.

![Screenshot Orte Abfruf](/sources/wetter-forecast-tabelle.png)

Einstellungen für den API Abruf

![Screenshot API Stündlich](/sources/wetter-stündlich-http.png)

Hier müssen folgende Werte angepasst werden:
- appid mit dem API Key von openweathermap

Einstellung für das Speichern der Daten

![Screenshot Datei Stündlich](/sources/wetter-stündlich-datei.png)

Hier müssen folgende Werte angepasst werden:
- Webseiteadresse mit der URL zu SharePoint Site. Dieser wird über das Dropdownmenü ausgewählt.
- Ordnerpfad mit dem Pfad zum Datenordner. Dieser wird über das Menü ausgewählt.

## Arbeiten in Power BI

Die Datei Wetter.pbit wird geöffnet.

Danach müssen die Pfade zum SharePoint angepasst werden.

Dazu wird der Power Query Editor geöffnet.

![Screenshot Power BI Power Query starten](/sources/wetter-pqeditor-start.png)

![Screenshot Power BI Power Query anpassen](/sources/wetter-pqeditor.png)

Im Power Query Editore werden diese beiden Angaben angepasst:

- SharepointFolder - hier wird der Pfad zum Datenordner angebenen. Leerzeichen im Pfad werden normal angegeben. Z.B. https://mydomain.tld.com/sites/MeineSite/Shared Documents/wetter/daten/
- SharepointURL - hier wird der Pfad zur SharePoint Site angegeben. Z.B. https://mydomain.tld.com/sites/MeineSite

Anschließend wird Power Query mit Scließen und übernehmen geschlossen.

Nun kann das Dashboard veröffentlicht werden.

nach der Veröffentlichung muss der Arbeitsbereich, in den das Dashboard veröffentlicht wurde, geöffnet und das Semantikmodell des Dashbaords angepasst werden.

![Screenshot Einstellung Semantikmodell öffen](/sources/wetter-pbi-einstellungen.png)

Dazu werden die drei Punkte des Semantikmodells angeklickt und der Punkt Einstellungen angeklickt.

![Screenshot Einstellung Semantikmodell anpassen](/sources/wetter-pbi-einstellungen-arbeiten.png)

In den Einstellungen müssen zum Einem die Datenquellen Anmeldeinformationen bearbeitet werden.

Es müssen alle Angaben angeklickt und aktuallisiert werden.

![Screenshot Einstellung Anmeldeinformation](/sources/wetter-pbi-einstellungen-anmeldung.png)

Hier sollten die Einstellung aus dem Screenshot übernommen werden.

Zum Anderem müssen die Angaben für das Aktualsieren eingstellt werden.
