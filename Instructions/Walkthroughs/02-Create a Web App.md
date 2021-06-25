---
wts:
    title: '02 - Erstellen einer Web-App (10 Min.)'
    module: 'Modul 02 - Azure-Kerndienste (Workloads)'
---
# 02 - Erstellen einer Web-App

In dieser exemplarischen Vorgehensweise erstellen wir eine neue Web-App, in der ein Docker-Container ausgeführt wird. Der Container zeigt eine Begrüßungsnachricht an. 

# Aufgabe 1: Erstellen Sie eine Web-App (10 Min.)

Azure App Service ist eine Sammlung von vier Diensten, die alle zum Hosten und Ausführen von Webanwendungen dienen. Die vier Dienste (Web-Apps, Mobile Apps, API-Apps und Logic Apps) sehen unterschiedlich aus, funktionieren jedoch letztendlich alle sehr ähnlich. Web-Apps ist der am häufigsten verwendete Dienst der vier Dienste. Diesen Dienst werden wir in diesem Lab verwenden.

In dieser Aufgabe erstellen Sie eine Azure App Service-Web-App. 

1. Melden Sie sich beim [Azure-Portal](http://portal.azure.com/) an. 

2. Suchen Sie auf dem Blatt **Alle Dienste** den Eintrag **App Services**, wählen Sie ihn aus, und klicken Sie auf **+ Hinzufügen, + Erstellen oder auf + Neu**.

3. Geben Sie auf der Registerkarte **Grundlagen** des Blatts **Web-App** die folgenden Einstellungen an (ersetzen Sie **xxxx** im Namen der Web-App durch Buchstaben und Ziffern, sodass der Name global eindeutig ist). Behalten Sie ansonsten die Standardeinstellungen bei, auch für den App Service-Plan. 

    | Einstellung | Wert |
    | -- | -- |
    | Abonnement | **Wählen Sie Ihr Abonnement** |
    | Ressourcengruppe | **myRGWebApp1** (neu erstellen) |
    | Name | **myDockerWebAppxxxx** |
    | Veröffentlichen | **Docker-Container** |
    | Betriebssystem | **Linux** |
    | Region | **USA, Osten** (ignorieren Sie alle Warnungen zur Verfügbarkeit von Dienstplänen) |
    | | |	
    
    **Hinweis** - Denken Sie daran, **xxxx** zu ändern, sodass sich ein eindeutiger **Name** ergibt

4. Klicken Sie auf **Weiter > Docker**, und konfigurieren Sie die Containerinformationen. Der Startupbefehl ist optional und wird in dieser Übung nicht benötigt. 

    **Hinweis:** Dies ist derselbe Container, der in der exemplarischen Vorgehensweise für Container Instances verwendet wurde, um eine Hallo Welt-Meldung anzuzeigen. 

    | Einstellung | Wert |
    | -- | -- |
    | Optionen | **Einzelner Container** |
    | Imagequelle | **Docker Hub** |
    | Zugriffstyp | **Öffentlich** |
    | Image und Tag | **microsoft/aci-helloworld** |
    | | |	


5. Klicken Sie auf **Überprüfen + erstellen**, und klicken Sie dann auf **Erstellen**. 

# Aufgabe 2: Testen der Web-App

In dieser Aufgabe testen wir die Web-App.

1. Warten Sie, bis die Web-App bereitgestellt ist.

2. Klicken Sie in **Benachrichtigungen** auf **Zur Ressource gehen**. 

3. Suchen Sie auf dem Blatt **Überblick** den Eintrag **URL**. 

    ![Screenshot des Web-App-Eigenschaftenblatts. Die URL wird hervorgehoben.](../images/0801.png)

4. Klicken Sie auf **URL**, um die neue Browser-Registerkarte zu öffnen und die Seite „Willkommen bei Azure Container Instances“ anzuzeigen.

    ![Screenshot der Seite „Willkommen bei Azure Container Instances“.](../images/0802.png)

5. Wechseln Sie wieder zum Blatt **Übersicht** Ihrer Web-App, und beachten Sie, dass es mehrere Diagramme enthält. Wenn Sie Schritt 4 einige Male wiederholen, sollte die entsprechende Telemetrie in den Diagrammen angezeigt werden. Dies umfasst die Anzahl der Anfragen und die durchschnittliche Antwortzeit. 

**HINWEIS**: Um zusätzliche Kosten zu vermeiden, können Sie diese Ressourcengruppe entfernen. Suchen Sie nach Ressourcengruppen, klicken Sie auf Ihre Ressourcengruppe und dann auf **Ressourcengruppe löschen**. Überprüfen Sie den Namen der Ressourcengruppe und klicken Sie dann auf **Löschen**. Überwachen Sie die **Benachrichtigungen**, um zu sehen, wie der Löschvorgang abläuft.

