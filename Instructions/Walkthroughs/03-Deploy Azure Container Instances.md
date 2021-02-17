---
wts:
    title: '03 – Bereitstellen von Azure Container Instances (10 Min.)'
    module: 'Modul 02 – Core Azure Services (Workloads)'
---

# 03 – Bereitstellen von Azure Container Instances

In dieser exemplarischen Vorgehensweise erstellen, konfigurieren und implementieren wir einen Docker-Container mithilfe von Azure Container Instances (ACI) im Azure-Portal. Der Container ist eine „Welcome to ACI“-Webanwendung, die eine statische HTML-Seite anzeigt. 

# Aufgabe 1: Erstellen Sie eine Container Instance (10 Min.)

In dieser Aufgabe erstellen wir eine neue Containerinstanz für die Webanwendung. 

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.

2. Suchen Sie auf dem Blatt **Alle Dienste** nach **Container Instances**, und wählen Sie diese Option aus. Klicken Sie anschließend auf **+ Hinzufügen**. 

3. Geben Sie die folgenden grundlegenden Details für die neue Containerinstanz an (belassen Sie die Standardeinstellungen für alles andere so, wie sie sind): 

	| Einstellung| Wert|
	|----|----|
	| Abonnement | **Wählen Sie Ihr Abonnement** |
	| Ressourcengruppe | **myRGContainer** (neu erstellen) |
	| Containername| **mycontainer**|
	| Region | **(USA) USA, Osten** |
	| Imagequelle| **Docker Hub oder andere Registrierung**|
	| Imagetyp| **Öffentlich**|
	| Image| **microsoft/aci-helloworld**|
	| Betriebssystemtyp| **Linux** |
	| Größe| ***Belassen Sie die Standardeinstellung***|
	|||

4. Konfigurieren Sie die Registerkarte „Netzwerk“ (ersetzen Sie **xxxx** durch Buchstaben und Ziffern, sodass der Name global eindeutig ist). Belassen Sie für alle anderen Einstellungen die Standardwerte.

	| Einstellung| Wert|
	|--|--|
	| DNS-Namensbezeichnung| **mycontainerdnsxxxx** |
	|||
	
	**HINWEIS**: Ihr Container ist unter „dns-name-label.region.azurecontainer.io“ öffentlich erreichbar. Wenn Sie die Fehlermeldung **DNS-Namensbezeichnung nicht verfügbar** nach der Bereitstellung erhalten, geben Sie eine andere DNS-Namensbezeichnung an (verwenden Sie nicht „xxxx“) und stellen Sie sie erneut bereit. 


	![Screenshot des Konfigurationsbereichs des Blatts zum Erstellen von Container Instances im Azure-Portal mit eingegebener DNS-Namensbezeichnung. ](../images/0201.png)

5. Klicken Sie auf **Überprüfen + Erstellen**, um die automatische Validierung zu starten.

6. Klicken Sie auf **Erstellen**, um die Containerinstanz zu erstellen. 

7. Überwachen Sie die Bereitstellungsseite und die Seite **Benachrichtigungen**. 

8. Während Sie warten, könnten Sie daran interessiert sein, den [Beispielcode hinter dieser einfachen Anwendung](https://github.com/Azure-Samples/aci-helloworld) anzuzeigen. Durchsuchen Sie den Ordner „\app“. 

# Aufgabe 2: Überprüfen der Bereitstellung der Containerinstanz

In dieser Aufgabe überprüfen wir, ob die Containerinstanz ausgeführt wird, indem wir sicherstellen, dass die Willkommensseite angezeigt wird.

1. Klicken Sie nach Abschluss der Bereitstellung auf **Zu Ressource wechseln**, verknüpfen Sie das Blatt „Bereitstellung“ oder die Verknüpfung mit der Ressource im Benachrichtigungsbereich.

2. Stellen Sie auf dem Blatt **Überblick** von **mycontainer** sicher, dass der **Status** Ihres Containers **Wird ausgeführt** lautet. 

3. Suchen Sie den vollqualifizierten Domänennamen (FQDN).

	![Screenshot des Übersichtsbereichs für den neu erstellten Container im Azure-Portal mit hervorgehobenem FQDN. ](../images/0202.png)

2. Kopieren Sie den vollqualifizierten Domänennamen des Containers in das URL-Textfeld des Webbrowsers, und drücken Sie die **EINGABETASTE**. Die Startseite sollte angezeigt werden. 

	![Screenshot der ACI-Begrüßungsnachricht, die in einem Webbrowser angezeigt wird.](../images/0203.png)

**HINWEIS**: Sie können auch die Container-IP-Adresse in Ihrem Browser verwenden. 

Herzlichen Glückwunsch! Sie haben Azure-Portal verwendet, um eine Anwendung erfolgreich in einem Container in Azure Containerinstanz bereitzustellen.

**HINWEIS**: Um zusätzliche Kosten zu vermeiden, können Sie diese Ressourcengruppe entfernen. Suchen Sie nach Ressourcengruppen, klicken Sie auf Ihre Ressourcengruppe und dann auf **Ressourcengruppe löschen**. Überprüfen Sie den Namen der Ressourcengruppe, und klicken Sie dann auf **Löschen**. Überwachen Sie die **Benachrichtigungen**, um zu sehen, wie der Löschvorgang abläuft.
