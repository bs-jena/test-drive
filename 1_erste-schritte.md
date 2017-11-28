# Erste Schritte {#erste-schritte}

## Was ist JustOn Connector for DATEV? {#was-ist-dco}
Mit der Salesforce-App „JustOn Connector for DATEV" können Sie Ihre digitalen Belege, Rechnungs- und Kassendaten aus angebundenen Salesforce-Anwendungen einfach und komfortabel zu Ihrem Steuerberater bei DATEV übertragen. Die Daten werden sicher ins DATEV Rechenzentrum übermittelt und stehen Ihrem Steuerberater in den Anwendungen von DATEV Unternehmen online zur Erstellung der Finanzbuchführung zur Verfügung.

Sie können Daten aus allen Salesforce-Anwendungen übertragen, die eine Integration für „JustOn Connector for DATEV“ umgesetzt haben. Daten werden gesammelt pro Buchungsmonat und Art des Belegs (Ausgangsrechnung, Eingangsrechnung oder Kasse) an DATEV übertragen. 

Beim Übertragen der Daten an DATEV müssen Sie sich mit einem DATEV-Authentifizierungsmedium anmelden. Ihr Steuerberater bestellt und konfiguriert die notwendigen Produkte für Sie. Für die Nutzung von "JustOn Connector for DATEV" und die Anwendungen von "DATEV Unternehmen online" können Ihnen Folgekosten bei DATEV entstehen. 

## Welche Voraussetzungen muss ich erfüllen, um JustOn Connector for DATEV nutzen zu können? {#voraussetzungen}

Um Daten über "JustOn Connector for DATEV" an DATEV zu übertragen gibt es zwei Voraussetzungen: 

*	**Ihr Steuerberater arbeitet mit DATEV Software** und legt Sie als Mandant in DATEV Unternehmen online an – dorthin werden Ihre Daten übertragen.

*	Sie besitzen **ein DATEV-Authentifizierungsmedium**, <br/> also entweder 
    
  * eine auf Ihrem Smartphone installierte DATEV-App, den DATEV SmartLogin. Die App gibt es für iOS oder Android. Alle Infos zum DATEV SmartLogin finden Sie unter https://www.datev.de/info-db/1080654. Mit der App lesen Sie über Ihr Smartphone zur Authentisierung einen QR-Code vom Bildschirm ein und geben den Zugriff mit einem Passwort frei.
    Die App können Sie frei herunterladen. Zur Freischaltung erhalten Sie für die Nutzung der App zwei Codes von DATEV, einen per E-Mail und einen per Post. Diese Codes tragen Sie einmalig in der App ein. 

     <br/>oder

   * einen  USB-Stick, den DATEV mIDentity Stick, mit einer eingelegten Zugangsberechtigungskarte, der DATEV SmartCard. Der USB-Stick muss in den USB-Port Ihres Rechners gesteckt werden. Die SmartCard erfordert die Eingabe eines Passwortes. Um die SmartCard zu nutzen müssen Sie einmalig ein Sicherheitsprogramm von DATEV herunterladen und und auf ihrem PC installieren.
    Hinweis: Die DATEV SmartCard funktioniert nur unter dem Betriebssystem Windows und mit dem Internet Explorer ab Version 9.<br/>
        ![](/images/02_smartcard.jpg.jpg)
    
    Beide Authentifizierungsmedien können Sie über Ihren Steuerberater bestellen und einrichten lassen. 



## Installation {#installation}
Um „JustOn Connector for DATEV“ zu nutzen installieren Sie die Anwendung zunächst über den Salesforce AppExchange. 

**Achtung: Bitte installieren Sie "JustOn Connector for DATEV" NUR mit der Option "Installation nur für Administratoren"** (siehe [Was Sie administrieren müssen - Installation](4_administration.md#administration-installation)).


## JustOn Connector for DATEV in Salesforce einrichten {#dco-einrichten}
Sie können in "JustOn Connector for DATEV" mit drei verschiedenen Berechtigungsprofilen arbeiten:

* **Lesender Nutzer**: Der Nutzer kann Belege und Datenübertragungen ansehen. 
* **Nutzer mit Schreibrecht**: Der Nutzer kann Belege aus anderen Salesforce-Anwendungen an JustOn Connector for DATEV transferieren und Belege und Datenübertragungen ansehen.
* **Nutzer mit Schreib- und Übertragungsrecht**: Der Nutzer kann Belege aus anderen Anwendungen an JustOn Connector for DATEV transferieren, Belege und Datenübertragungen ansehen und Daten an DATEV übertragen. Dieser Nutzer benötigt ein DATEV-Authentisierungsmedium.

Bitte lassen Sie sich eines dieser Profile vom Administrator einrichten (Beschreibung siehe [Administration](4_administration.md#administration)). Berechtigungsprofile werden in Salesforce über sogenannte Berechtigungssätze gepflegt.

**Hinweis:** Ohne eine Zuweisung eines Berechtigungsprofils können Sie JustOn Connector for DATEV nicht oder nicht korrekt nutzen.

Nutzer, die Belege aus Vorsystemen übertragen oder Daten an DATEV übertragen können, müssen zudem **VOR** Nutzung von JustOn Connector for DATEV im Reiter "Einstellungen" **prüfen, ob die Sachkontenlänge für ihre Finanzbuchführung korrekt hinterlegt ist**. Wie Sie die Sachkontenlänge einstellen können Sie im Abschnitt [Sachkontenlänge](2-3_einstellungen.md#sachkontenlaenge) nachlesen.
