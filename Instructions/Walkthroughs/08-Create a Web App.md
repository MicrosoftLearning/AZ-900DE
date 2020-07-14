---
wts:
    title: '08 – Erstellen einer Web-App'
    module: 'Modul 02 – Core Azure Services'
---
# 08 – Erstellen einer Web-App

In dieser exemplarischen Vorgehensweise erstellen wir eine neue Web-App, in der ein Docker-Container ausgeführt wird. Der Container zeigt eine Begrüßungsnachricht an. 

# Aufgabe 1: Eine Web-App erstellen

Azure App Service ist eine Sammlung von vier Diensten, die alle zum Hosten und Ausführen von Webanwendungen dienen. Die vier Dienste (Web-Apps, Mobile Apps, API-Apps und Locic Apps) sehen unterschiedlich aus, funktionieren jedoch letztendlich alle sehr ähnlich. Web-Apps ist der am häufigsten verwendete Dienst der vier Dienste. Diesen Dienst werden wir in diesem Lab verwenden.

In dieser Aufgabe erstellen Sie eine Azure App Service-Web-App. 

1. Melden Sie sich beim [Azure-Portal](http://portal.azure.com/) an. 

2. Suchen Sie im Blatt **Alle Dienste** den Eintrag **App Services**, wählen Sie ihn aus, und klicken Sie auf **+ Hinzufügen**.

3. Geben Sie auf der Registerkarte **Grundlagen** auf dem **Web-App**-Blatt die folgenden Einstellungen an (Ersetzen Sie **xxxx** im Namen der Web-App mit Buchstaben und Ziffern, so dass der Name global eindeutig ist). Behalten Sie ansonsten die Standardeinstellungen bei, auch für den App Service-Plan. 

    | Einstellung | Wert |
    | -- | -- |
    | Abonnement | **Wählen Sie Ihr Abonnement** |
    | Ressourcengruppe | **myRGWebApp1** (Neu erstellen) |
    | Name | **myDockerWebAppxxxx** |
    | Veröffentlichen | **Docker-Container** |
    | Betriebssystem | **Linux** |
    | Region | **USA, Osten** (ignorieren Sie alle Warnungen zur Verfügbarkeit von Dienstplänen) |
    | | |	

4. Klicken Sie auf **Weiter > Docker** und konfigurieren Sie die Containerinformationen. Der Startupbefehl ist optional und wird in dieser Übung nicht benötigt. 

    **Hinweis:** Dies ist derselbe Container, der in der exemplarischen Vorgehensweise für Container Instances verwendet wurde, um eine Hallo Welt-Meldung anzuzeigen. 

    | Einstellung | Wert |
    | -- | -- |
    | Optionen | **Einzelner Container** |
    | Bildquelle | **Docker Hub** |
    | Zugriffstyp | **Öffentlich** |
    | Bild und Tag | **Microsoft / Aci-Helloworld** |
    | | |	


5. Klicken Sie auf **Überprüfen + Erstellen **, und klicken Sie dann auf **Erstellen**. 

# Aufgabe 2: Web-App testen

In dieser Aufgabe testen wir die Web-App.

1. Warten Sie, bis die Web-App bereitgestellt ist.

2. Klicken Sie in **Benachrichtigungen** auf **Zur Ressource gehen**. 

3. Suchen Sie im Blatt **Überblick** den Eintrag **URL**. 

    ![Screenshot des Web-App-Eigenschaftenblatts. Die URL wird hervorgehoben.](../images/0801.png)

4. Klicken Sie auf **URL**, um die neue Browser-Registerkarte zu öffnen und die Seite „Willkommen bei Azure Container Instances“ anzuzeigen.

    ![Screenshot der Seite „Willkommen bei Azure Container Instances“.](../images/0802.png)

5. Wechseln Sie wieder zum Blatt **Übersicht** Ihrer Web-App, und beachten Sie, dass es mehrere Diagramme enthält. Wenn Sie Schritt 4 einige Male wiederholen, sollte die entsprechende Telemetrie in den Diagrammen angezeigt werden. Dies umfasst die Anzahl der Anfragen und die durchschnittliche Antwortzeit. 

**Hinweis**: Um zusätzliche Kosten zu vermeiden, können Sie diese Ressourcengruppe entfernen. Suchen Sie nach Ressourcengruppen, klicken Sie auf Ihre Ressourcengruppe und dann auf **Ressourcengruppe löschen**. Überprüfen Sie den Namen der Ressourcengruppe, und klicken Sie dann auf **Löschen**. Überwachen Sie die **Benachrichtigungen**, um zu sehen, wie der Löschvorgang abläuft.

