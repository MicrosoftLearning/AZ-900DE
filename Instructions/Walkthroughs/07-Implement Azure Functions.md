---
wts:
    title: '07 – Implementieren von Azure Functions'
    module: 'Modul 02 – Core Azure Services'
---
# 07 – Implementieren von Azure Functions

In dieser exemplarischen Vorgehensweise erstellen wir eine Funktions-App, um eine Hello-Meldung anzuzeigen, wenn eine HTTP-Anforderung vorliegt. 

# Aufgabe 1: Eine Funktions-App erstellen

In dieser Aufgabe erstellen wir eine Funktions-App.

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.

1. Wählen Sie im Textfeld **Ressourcen, Dienste und Dokumente suchen** oben im Portal **Funktions-App** aus, und klicken Sie dann auf dem Blatt **Funktions-App** auf **Hinzufügen**.

1. Geben Sie auf dem Blatt **Funktions-App** auf der Registerkarte **Basic** die folgenden Einstellungen an (ersetzen Sie **xxxx** im Funktionsnamen durch Buchstaben und Ziffern, sodass der Name global eindeutig ist, und belassen Sie für alle anderen Einstellungen die Standardwerte): 

    | Einstellungen | Wert |
    | -- | --|
    | Abonnement | Der Name Ihres Azure-Abonnements |
    | Ressourcengruppe | Der Name einer neuen Ressourcengruppe **myRGFunction** |
    | Name der Funktions-App | **Funktion-xxxx** |
    | Veröffentlichen | **Code** |
    | Runtime-Stapel | **NET Core** |
    | Region | **USA, Osten** |
    | | |	

1. Klicken Sie auf **Überprüfen + Erstellen**. Klicken Sie nach erfolgreicher Validierung auf **Erstellen**, um mit der Bereitstellung Ihrer neuen Azure Funktions-App zu beginnen.

1. Warten Sie auf die Benachrichtigung, dass die Ressource erstellt wurde.

1. Navigieren Sie zurück in das Blatt **Funktions-App**, klicken Sie auf **Aktualisieren** und überprüfen Sie, ob die neu erstellte Funktions-App den Status **Wird ausgeführt** aufweist. 

    ![Screenshot der Seite „Funktions-App“ mit der neuen Funktions-App.](../images/0701.png)

# Aufgabe 2: Erstellen Sie eine durch HTTP ausgelöste Funktion und testen Sie sie

In dieser Aufgabe verwenden wir die Webhook + API-Funktion, um eine Nachricht anzuzeigen, wenn eine HTTP-Anforderung vorliegt. 

1. Klicken Sie unter **Funktions-App** auf die neu erstellte Funktions-App. 

1. Klicken Sie auf dem Blatt „Funktions-App“ im Abschnitt **Funktionen** auf **Funktionen** und dann auf **+ Hinzufügen**.

    ![Screenshot des Schritts „Entwicklungsumgebung auswählen“ in den Azure Functions für den Bereich „Erste Schritte mit Dot Net“ im Azure-Portal. Die Anzeigeelemente zum Erstellen einer neuen Portalfunktion werden hervorgehoben. Die hervorgehobenen Elemente sind „Erweitern der Funktions-App“, „Hinzufügen einer neuen Funktion“, „Portal“ und die Schaltfläche „Weiter“.](../images/0702.png)

1. Klicken Sie auf der Registerkarte **Vorlagen** unter **Neue Funktion** auf **HTTP-Trigger**. 

    ![Screenshot des Schritts zum Erstellen einer Funktion in Azure Functions für den Bereich „Erste Schritte mit Dot Net“ im Azure-Portal. Die HTTP-Triggerkarte wird hervorgehoben, um die Anzeigeelemente zu veranschaulichen, mit denen einer Azure-Funktion ein neuer Webhook hinzugefügt wird.](../images/0702a.png)

1. Akzeptieren Sie auf dem Blatt **Neue Funktion** auf der Registerkarte **Details** den Standardnamen **Neue Funktion** und die **Autorisierungsstufe**, und klicken Sie dann auf **Funktion erstellen**. 

    ![Screenshot des Schritts zum Erstellen einer Funktion in Azure Functions für den Bereich „Erste Schritte mit Dot Net“ im Azure-Portal. Die Schaltflächen „Webhook + API“ und „Erstellen“ sind hervorgehoben, um die Anzeigeelemente zu veranschaulichen, mit denen einer Azure-Funktion ein neuer Webhook hinzugefügt wird](../images/0703.png)

1. Klicken Sie im Blatt **HttpTrigger1** im Abschnitt **Entwickler** auf **Code + Test**. 

1. Prüfen Sie unter **HttpTrigger1 \| **Überprüfen Sie im Blatt **Code + Test** den automatisch generierten Code und beachten Sie, dass der Code auf das Ausführen einer HTTP-Anforderung und das Protokollieren von Informationen ausgelegt ist. Beachten Sie außerdem, dass die Funktion eine Hello-Meldung mit einem Namen zurückgibt. 

    ![Screenshot des Funktionscodes. Die „Hallo“-Meldung ist hervorgehoben.](../images/0704.png)

1. Klicken Sie auf **Funktions-URL abrufen** im oberen Abschnitt des Funktions-Editors. 

1. Stellen Sie sicher, dass der Wert in der Dropdown-Liste **Schlüssel** auf **Standard** gesetzt ist, und klicken Sie auf **Kopieren** um die Funktions-URL zu kopieren. 

    ![Screenshot des URL-Bereichs „Funktion abrufen“ im Funktionseditor im Azure-Portal. Die Anzeigeelemente „Funktions-URL abrufen“, „Tasten-Dropdown festlegen“ und „URL kopieren“ sind hervorgehoben, um anzugeben, wie die Funktions-URL vom Funktionseditor abgerufen und kopiert werden kann.](../images/0705.png)

1. Öffnen Sie eine neue Browser-Registerkarte und fügen Sie die kopierte Funktions-URL in die Adressleiste Ihres Webbrowsers ein. Wenn die Seite angefordert wird, wird die Funktion ausgeführt. Beachten Sie die ausgegebene Nachricht, dass die Funktion einen Namen im Anforderungstext benötigt.

    ![Screenshot der Meldung „Geben Sie einen Namen an“.](../images/0706.png)

1. Fügen Sie **&name=*yourname*** an das Ende der URL an.

    **Hinweis**: Ersetzen Sie ***yourname*** durch Ihren Vornamen. Wenn Sie beispielsweise Cindy heißen, ähnelt die endgültige URL der folgenden URL `https://azfuncxxx.azurewebsites.net/api/HttpTrigger1?code=X9xx9999xXXXXX9x9xxxXX==&name=cindy`

    ![Screenshot einer hervorgehobenen Funktions-URL und eines angehängten Beispielbenutzernamens in der Adressleiste eines Webbrowsers. Die Hello-Meldung und der Benutzername werden ebenfalls hervorgehoben, um die Ausgabe der Funktion im Hauptbrowserfenster zu veranschaulichen.](../images/0707.png)

1. Wenn Ihre Funktion ausgeführt wird, wird jeder Aufruf verfolgt. Kehren Sie zum Anzeigen der Traces im Azure-Portal zurück zum Blatt **HttpTrigger1 \| Code + Test** zurück, und klicken Sie auf **Monitor**.

    ![Screenshot eines Protokolls mit Ablaufverfolgungsinformationen, das sich aus der Ausführung der Funktion im Funktions-Editor im Azure-Portal ergibt.](../images/0709.png) 

Herzlichen Glückwunsch! Sie haben eine Funktions-App erstellt, um eine Hello-Meldung anzuzeigen, wenn eine HTTP-Anforderung vorliegt. 

**Hinweis**: Um zusätzliche Kosten zu vermeiden, können Sie diese Ressourcengruppe entfernen. Suchen Sie nach Ressourcengruppen, klicken Sie auf Ihre Ressourcengruppe und dann auf **Ressourcengruppe löschen**. Überprüfen Sie den Namen der Ressourcengruppe, und klicken Sie dann auf **Löschen**. Überwachen Sie die **Benachrichtigungen**, um zu sehen, wie der Löschvorgang abläuft.
