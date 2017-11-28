# Administration {#administration}

Für die Einrichtung von "JustOn Connector for DATEV" ist es wichtig, die Anwendung "nur für Administratoren" zu installieren und allen Nutzern von "JustOn Connector for DATEV" Berechtigungsprofile zuzuweisen.

Als Adminstrator nehmen Sie die meisten Einstellungen in der Salesforce-Ansicht vor, die Sie über "Setup" in Salesforce aufrufen können.

Jeder Nutzer kann einige Nutzer-spezifische Einstellungen für sich im Reiter "Einstellungen" hinterlegen. Die meisten davon kann der Nutzer alternativ auch bei der ersten Datenübertragung von Daten an DATEV speichern. Dazu gehört die Mandantennummer und die Beraternummer und der bevorzugte Übertragungsordner. 

# Was Sie administrieren müssen {#administration-musts}

## Erste Schritte {#administration-erste-schritte}

Annahme: Sie sind Administrator, haben einen Salesforce-Account und möchten JustOn Connector for DATEV für Ihre Organisation installieren.

Bitte führen Sie folgende Schritte durch:

1. Installation der Anwendung "nur für Administratoren"
2. Benutzern ihrer Organisation Berechtigungsprofile zuweisen (und ggf. neue Benutzer anlegen)
3. Rest so lassen wie er im Paket ausgeliefert wurde

### 1. JustOn Connector for DATEV für die Organisation installieren {#administration-installation}

![](/images/10_install_01.png)

Bei der Installation der Anwendung haben Sie drei Möglichkeiten:
* Installation nur für Adminstratoren 
* Installation für alle Nutzer
* Installation für ausgewählte Profile

**Bitte installieren Sie "JustOn Connector for DATEV" mit der Option "Installation nur für Administratoren"**, damit Berechtigungen für die User über Berechtigungssätze vergeben werden können. Damit stellen Sie sicher, dass Updates für Feldberechtigungen korrekt funktionieren, dass die Anwendung konsistent funktioniert und die Nutzer bestmöglich bei GoBD-konformem Arbeiten unterstützt werden.

Wenn Sie die Anwendung mit der Option "für alle Nutzer" oder "für ausgewählte Profile" installieren entstehen in der Anwendung unerwünschter Effekte: Die Metadaten-Objekte für Belege, Belegpositionen und Datenübertragungen werden für jeden Nutzer freigeschaltet und Lese- und Schreibrechte sind dann frei editierbar. 
In diesem Fall können diese Rechte nie über die Zuweisung von Berechtigungssätzen überschrieben werden. Das führt zu manuellem Aufwand für Sie bei Updates, Sie würden "JustOn Connector for DATEV" abweichend der Vorgaben nutzen, und die Anwendung unterstützt dann die Nutzer nicht bestmöglich bei GoBD-konformem Arbeiten.

Bei der Installation geben Sie auch die Art Ihrer Lizenz an. Wenn Sie mit einer Organisations-weiten Lizenz installieren brauchen Sie nichts weiter zu tun.
Bei Installation mit einer Nutzer-Lizenz müssen Sie danach Lizenzen zuweisen (bitte folgen Sie dafür der Beschreibung in den Salesforce-Manuals).


### 2. Benutzern Berechtigungsprofile zuweisen {#berechtigungen-konfigurieren}

Nach der Installation müssen Sie noch Benutzer für die Anwendung anlegen bzw. bestehenden Nutzern Berechtigungsprofile für "JustOn Connector for DATEV" zuweisen. JustOn Connector for DATEV bringt dafür eigene Berechtigungssätze (Permission Sets) für den Zugriff auf App-spezifische Felder, VisualForce-Seiten und APEX-Klassen von "JustOn Connector for DATEV" mit.

Die Berechtigungssätze eines Profils müssen Sie pro Nutzer ein Mal zweisen. Danach bleiben Sie beim Upgraden von JustOn Connector for DATEV für die Nutzer erhalten. Neue Felder oder Funktionen werden in zukünftigen Releases automatisch über die Berechtigungen mit hinzugefügt. Dadurch müssen Sie als Administrator nach einem Upgrade auf eine neuere "JustOn Connector for DATEV-Version" nicht Profile manuell editieren und dort neue Felder hinzufügen.

Als Administrator dürfen Sie Benutzern Berechtigungssätze hinzufügen oder entfernen. 

**Hinweis:** Falls Sie neue Benutzer benötigen, so können Sie diesen im Setup über *Benutzer verwalten > Benutzer* und dort über den Button *Neuer Benutzer* anlegen. Bitte legen Sie sie als "Standard User" an. Bitte stellen Sie sicher, dass Sie nach der Neuanlage eines Benutzers diesem Berechtigungen für "JustOn Connector for DATEV" zuweisen.

Für "JustOn Connector for DATEV" sind Rechteprofile in drei verschiedenen Ausprägungen möglich:

| **Name** | **Beschreibung** | **Berechtigungssatzzuweisungen** |
| --- | --- |  --- |  --- | 
| **Lesender Nutzer** | Der Nutzer kann nur Daten lesen.<br/><br/>Konkret bedeutet das:<ul><li>Alle drei Reiter: „Belege“, „Datenübertragungen“ und „Einstellungen“ sind sichtbar</li><li>Der Nutzer kann in den Reitern „Belege“ und „Datenübertragungen“ alle Datensätze lesen, sieht aber keine Anwendungs-spezifischen Aktions-Buttons oder Aktions-Links (kein Anlegen, Ändern, Löschen, usw.)</li><li>Im Reiter „Einstellungen“ sieht der Nutzer eine Fehlermeldung statt dem Inhalt der Seite (Reiter nicht ausblendbar, da VisualForce-Seite)</li></ul> | DATEV Read-Only | 
| **Nutzer mit Schreibrecht** | Der Nutzer kann <ul><li>Belege lesen, anlegen, ändern und löschen (soweit zulässig)</li><li>Datenübertragungen nur lesen</li><li>Im Reiter „Einstellungen“ die Sachkontenlänge verändern und speichern</li></ul> | Customize Application <br/>+ DATEV Read/Write |
| **Nutzer mit Schreib- und Übertragungsrecht** | Der Nutzer kann, soweit im Rahmen von JustOn Connector for DATEV zulässig<ul><li>Belegdaten anlegen, ändern und löschen</li><li>die Sachkontenlänge ändern und speichern</li><li>Einstellungen für die Datenübertragung ändern und speichern</li></ul>Er kann außerdem alle Aktionen tätigen, die eine DATEV-Authentisierung benötigen, er kann also<ul><li>Datenübertragungen anlegen, neu übertragen, löschen</li><li>Den Status einer Datenübertragung aktualisieren und Übertragungsprotokolle einsehen</li></ul> | Customize Application <br/>+ DATEV Read/Write <br/>+ DATEV Manage Accounting Jobs |

Die oben genannten Rechteprofile können Sie über folgende Berechtigungssätze abbilden:

| **Name Berechtigungssatz** | **Beschreibung** | **Hinweis** |
| --- | --- | --- |
| **DATEV Read-Only** | <ul><li>Lesen von Belegen und Datenübertragungen</li></ul> | Kann ohne andere JustOn Connector for DATEV-Berechtungungen zugewiesen werden. |
| **Customize Application** | <ul><li>Lesen und Ändern der "JustOn Connector for DATEV"-spezifischen Einstellungen im Reiter "Einstellungen" (z.B. Feld Sachkontenlänge)</li></ul> | **Salesforce-übergreifender Berechtigungssatz**, der es dem Anwender erlaubt, benutzerdefinierte Einstellungen zu hinterlegen. |
| **DATEV Read/Write** | <ul><li>Lesen / Anlegen / Ändern / Löschen von Belegen (soweit zulässig)</li><li>Lesen von Datenübertragungen</li></ul> | Kann ohne andere JustOn Connector for DATEV-Berechtungungen zugewiesen werden. |
| **DATEV Manage Accounting Jobs** | Erlaubt alle Aktionen durchzuführen, die eine DATEV-Authentisierung benötigen:<br/><ul><li>Anlegen einer Datenübertragung</li><li>Neuübertragung an DATEV</li><li>Löschen einer Datenübertragung</li><li>Status einer Datenübertragung aktualisieren und Übertragungsprotokoll einsehen</li></ul> | **Zusatzrecht** (nur für Nutzer mit Berechtigung DATEV Read/Write zuweisen). |
| **DATEV Full Access (disable sharing)** | Falls in der Organisation Sharing Rules verwendet werden können Sie mit diesem Recht für den Nutzer für JustOn Connector for DATEV die Sharing Rules überschreiben, d.h. der Nutzer sieht dann alle JustOn Connector for DATEV Datensätze der Organisation. | **Zusatzrecht** (zusätzlich zu allen anderen JustOn Connector for DATEV-Berechtigungen vergebbar). |

# DATEVconnect von Salesforce Lightning auf Salesforce Classic umstellen {#lightning-to-classic}
In der Standardkonfiguration wird DATEVconnect mit Anpassungen für die Lightning-Benutzeroberfläche ausgeliefert. Im Paket sind zudem Anpassungen enthalten, die die Benutzung von DATEVconnect in der Salesforce-Classic-Benutzeroberfläche erleichtern. Dieses Dokument beschreibt die Aktivierung der Classic-Anpassungen.

**Wenn Sie die Anpassungen für Classic aktivieren, kann es sein, dass Lightning-Nutzer an bestimmten Stellen mit der Classic-Benutzeroberfläche in Berührung kommen.**

Die Classic-Anpassungen konzentrieren sich auf die Bereiche Tabs und Record-Detailseiten.

## Tabs überschreiben {#lightning-to-classic-tabs}
Im Paket enthalten sind Visualforce-Seiten die es erlauben, auf den Tabs für Belege und Datenübertragungen sofort zur Listenansicht zu wechseln. Zudem wird auf der Liste der Datenübertragungen ein Auftragsstatus eingeblendet.

Die Tabs können über *Setup > Erstellen > Objekte > Accounting Document (Item) / Data Transfer > Schaltflächen, Links und Aktionen* eingeschaltet werden:

| **Objekt** | **Bezeichnung** | **Überschreiben mit Visualforce-Seite** | **Funktion** |
| --- | --- |  --- |  --- | 
| Accounting Document | Registerkarte Belege | AccountingDocumentTab | Weiterleitung zur Listenansicht |
| Accounting Document Item | Registerkarte Belegpositionen | AccoutingDetailTab | Weiterleitung zur Listenansicht | 
| Data Transfer | Registerkarte Datenübertragungen | AccountingJobTab | Anzeige von aktiven Datenübertragungen | 

## Neuer Datensatz/Detailseiten überschreiben {#lightning-to-classic-detailseiten}
Das Paket enthält Visualforce-Seiten, die es erlauben, die Beleg-Anlage und die Detailansichten zu verbessern.

Die Seiten können über *Setup > Erstellen > Objekte > Accounting Document (Item) / Data Transfer > Schaltflächen, Links und Aktionen* eingeschaltet werden:

| **Objekt** | **Bezeichnung** | **Überschreiben mit Visualforce-Seite** | **Funktion** |
| --- | --- |  --- |  --- |
| Accounting Document | Neu | NewAccountingDocumentAndDetail | Erlaubt die gleichzeitige Anlage eines Belegs mit Belegposition | 
| Data Transfer| Anzeigen | AccountingJobView | Anzeige von aktiven Datenübertragungen | 


# Weitere Informationen zur Administration (im Standardfall ändern Sie hier nichts) {#administration-weitere-infos}

Einige Einstellungen von JustOn Connector for DATEV müssen für die korrekte Funktionsweise von JustOn Connector for DATEV und für die bestmögliche Unterstützung bei GoBD-konformem Arbeiten so bleiben wie nach der Installation ausgeliefert. Das betrifft 
* Zur Änderung durch den Nutzer gesperrte Felder, wie z.B. für die Felder "Festgeschrieben" und "Aus Drittsystem" im Beleg (für korrekte Funktionsweise von "JustOn Connector for DATEV")
* Die Protollierung von Änderungen an Feldern (für bestmögliche Unterstützung bei GoBD-konformem Arbeiten)

**Bitte ändern Sie diese Einstellungen nicht und weisen Sie auch die Nutzer darauf hin, dass diese Einstellungen nicht geändert werden dürfen.**

## Automatische Protokollierung von Feldänderungen innerhalb von "JustOn Connector for DATEV"  {#admin-protokollierung-feldänderungen}

Nach der Installation von "JustOn Connector for DATEV" ist die Protokollierung von Feldänderungen in "JustOn Connector for DATEV" bereits so konfiguriert, dass Sie sie bei bestmöglichen GoBD-konformem Arbeiten unterstützt.

Die Protokollierung kann jeder Nutzer im jeweiligen Datenobjekt (Beleg, Belegposition oder in der Datenübertragung) selbst einsehen.

Konfiguriert wird die Protokollierung im Bereich Setup unter “Einrichten" --> "Erstellen” --> „Objekte“ --> dort zu AccountingDocuments, Accounting Document Details und DataTransfer die jeweiligen Seiten aufrufen. Änderungen werden für alle die Felder protokolliert, die im Abschnitt „Benutzerdefinierte Felder & Beziehungen“ das Häkchen „Verlauf verfolgen“ gesetzt haben (=History Tracking).

In Salesforce können standardmässig  maximal 20 Felder pro Objekt protokolliert werden.

Änderungen hier sind jedem Nutzer möglich, allerdings werden Änderungen als administrative Änderungen im Setup-Aktivierungsprotokoll angezeigt ("Verlaufsverfolgung für Accounting-Document-Feld "xy" deaktiviert."). Nach einer solchen Änderung durch den Nutzer arbeitet er nicht mehr GoBD-konform.

Für die Änderung von Anhängen und die Anlage / das Löschen von Objekten, die im Objekt enthalten sind (für "JustOn Connector for DATEV" Anlegen / Löschen von Belegposition in einem Beleg) können nicht protokolliert werden. Wo diese Änderungen nicht erlaubt sind werden sie über Validierungen im Code verhindert.

**Achtung:** Falls Sie oder die Nutzer die Protokollierung in einzelnen Feldern abschalten verlieren Sie bestmögliche Unterstützung bei GoBD-konformem Arbeiten. Nutzer können die Protokollierung aus dem Layout entfernen, die Einstellungen zur Verlaufsverfolgung am Feld selbst müssen aber bestehen bleiben, andernfalls ist das Tracking für das Feld abgeschaltet.
 

## Automatische Protokollierung von administrativen Änderungen an "JustOn Connector for DATEV" {#admin-protokollierung} 

Alle administrativen Änderungen an "JustOn Connector for DATEV" werden über einen Zeitraum von sechs Monaten in Salesforce protokolliert. Dazu gehören unter anderem:
* Die Zuweisung oder das Entfernen von Berechtigungssätzen für Nutzer
* Ab- oder Anschaltung der Verlaufsprotokollierung Feldänderungen (kann jeder Nutzer!)
* Das Entfernen von Validierungsregeln (kann jeder Nutzer!)

Das Protokoll können Sie im Bereich *Setup* unter *Verwalten > Sicherheitssteuerungen > Setup-Aktivierungsprotokoll anzeigen* (im englischen: *View Setup Audit Trail*) einsehen. 

Diese Protokollierung (der Setup Audit Trail) ist nicht abschaltbar.

Falls Sie das Protokoll über sechs Monate hinaus sichern möchten können Sie es in der Ansicht als CSV herunterladen und archivieren (Achtung: Dieses Vorgehen ist nicht manipulationssicher).


## Anzahl gleichzeitiger Prozesse für eine Datenübertragung konfigurieren {#konfig-prozesse-datenuebertragung}

Es gibt zwei globale, also Organisations-übergreifende Einstellungen für Datenübertragungen in "JustOn Connector for DATEV":

* Anzahl gleichzeitiger Prozesse (Batches) für die Vorbereitung einer Datenübertragung (also die XML-Generierung)
* Anzahl gleichzeitiger Prozesse (Batches) für die Datenübertragung

Beides sind Scopes, die Sie im Bereich *Setup* unter *Entwickeln > Benutzerdefinierte Einstellungen* konfigurieren können. Wählen Sie dort das Objekt "Batch-Settings" mit der Beschreibung "Batch Settings for DATEV Client" aus der Liste aus und klicken Sie auf der Folgeseite in der Zeile "Scope" in der Liste auf den Link **"Verwalten"**.


| **Name** | **Kurzbeschreibung** | **Möglicher Wertebereich** | **Empfohlener Wert** | **Beschreibung** |
| --- | --- | --- | --- | --- | 
| **BatchGenerateJob** | Anzahl gleichzeitiger Prozesse (Batches) bei der Vorbereitung einer Datenübertragung | 1 - 1000 |**1** | Bei der Datenübertragung an DATEV werden alle Daten Salesforce-seitig zunächst in XML-Daten geparst. Alle Daten werden per default in einem Prozess / Batch geparst. Soll, um eine höhere Geschwindigkeit zu erreichen, in mehr als einem Prozess gleichzeitig geparst werden, so kann hier die Anzahl der Prozess angegeben werden. |
| **BatchTransferJob** | Anzahl gleichzeitiger Prozesse (Batches) bei der Datenübertragung| 1-100 | **50** | Bei der Datenübertragung an DATEV werden die Daten in mehreren Prozessen / Batches übertragen. Das geschieht in so vielen Prozessen wie möglich und wie maximal über dieses Feld vorgegeben. |

Erläuterung zum Scope: Der Scope ist ein positiver Integer-Wert, der für die Methode Database.executeBatch(batch, scope) verwendet wird. 

Beide Batch-Jobs (BatchGenerateJob und BatchTransferJob) sind gebaut, um mit Tausenden von Belegen mit Belegbildern als Anhängen umzugehen. Die Grenzen der Salesforce-Plattform diktieren die maximal Anzahl an Datensätzen, die von einer Batch-Ausführung gehandhabt werden können.

**Achtung:** Die Einstellung gilt global für alle Benutzer der Org(anisation)!

**Hinweis** Bei sehr großen Anhängen ist es evtl. empfehlenswert, die Anzahl der Scopes zu erhöhen, falls die Übertragung mit Fehler abgebrochen wurde. In einem Batch sind Salesforce-seitig maximal 5 MB erlaubt. (DATEV erlaubt max. 20 MB per Datenübertragung).

## Zwischenseite über Infos zu Authentisierungsvoraussetzungen für einen Nutzer aus- oder einblenden {#splash-screen}

Nutzern, die das Recht besitzen, Daten an DATEV zu übertragen, wird bei Aufruf der ersten Aktion, die eine Authentisierung benötigt, eine Zwischenseite angezeigt, die über Authentisierungsvoraussetzungen informiert (u.a. Nutzer braucht ein DATEV-Authentisierungsmedium). Der Nutzer kann in der Seite einen Haken setzen, so dass ihm die Seite nie wieder angezeigt wird.

Falls Sie als Administrator die Seite für Nutzer vorab ausblenden möchten (z.B. weil Sie wissen dass Sie alle Voraussetzungen erfüllen) oder die Seite für einen Nutzer wieder einblenden möchten, so können Sie sie hier konfigurieren:<br/>
Im Setup über *Entwickeln > Benutzerdefinierte Einstellungen* und in der Tabelle in der Zeile "Settings" auf den Link "Verwalten" klicken. In der Liste der Nutzer für den Nutzer links auf den Link "Bearbeiten" klicken und den Haken bei "DATEV Splash Screen nicht anzeigen" setzen oder entfernen.

![](/images/10_user-settings_02.png)



