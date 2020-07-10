---
wts:
    title: '11 – Erstellen eines virtuellen Computers mithilfe der CLI'
    module: 'Modul 02 – Core Azure Services'
---
# 11 – Erstellen eines virtuellen Computers mithilfe der CLI

In dieser exemplarischen Vorgehensweise konfigurieren wir die Cloud Shell, erstellen mithilfe von Azure CLI eine Ressourcengruppe und einen virtuellen Computer und überprüfen die Empfehlungen von Azure Advisor. 

# Aufgabe 1: Die Cloud Shell konfigurieren

In dieser Aufgabe konfigurieren wir Cloud Shell. 

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.

2. Öffnen Sie im Azure-Portal die Option **Azure Cloud Shell**, indem Sie auf das Symbol oben rechts im Azure-Portal klicken.

    ![Screenshot des Azure Cloud Shell-Symbols im Azure-Portal.](../images/1002.png)

3. Wenn Sie die Cloud Shell bereits verwendet haben, fahren Sie mit der nächsten Aufgabe fort. 

4. Wenn Sie aufgefordert werden, entweder **Bash** oder **PowerShell** auszuwählen, wählen Sie **Bash** aus. 

5. Wenn Sie dazu aufgefordert werden, klicken Sie auf **Speicher erstellen**, und warten Sie, bis die Azure Cloud Shell initialisiert ist. 

# Aufgabe 2: Ressourcengruppe und virtuellen Computer erstellen

In dieser Aufgabe verwenden wir Azure CLI, um eine Ressourcengruppe und einen virtuellen Computer zu erstellen.  

1. Stellen Sie sicher, dass **Bash** im Dropdownmenü oben links im Cloud Shell-Bereich ausgewählt ist (wählen Sie andernfalls diese Option aus).

    ![Screenshot der Azure-Portal Azure Cloud-Shell mit hervorgehobenem Bash-Dropdown.](../images/1002a.png)

2. Erstellen Sie in der Bash-Sitzung im Cloud Shell-Bereich eine neue Ressourcengruppe. 

    ```cli
    az group create --name myRGCLI --location EastUS
    ```

3. Überprüfen Sie, ob die Ressourcengruppe erstellt wurde.

    ```cli
    az group list --output table
    ```

4. Erstellen Sie einen neuen virtuellen Computer. Stellen Sie sicher, dass auf jede Zeile mit Ausnahme der letzten Zeile ein umgekehrter Schrägstrich (`\`) folgt. Wenn Sie den gesamten Befehl in derselben Zeile eingeben, verwenden Sie keine umgekehrten Schrägstriche. 

    ```cli
    az vm create \
    --name myVMCLI \
    --resource-group myRGCLI \
    --image UbuntuLTS \
    --location EastUS \
    --admin-username azureuser \
    --admin-password Pa$$w0rd1234
    ```

    >**Hinweis**: Wenn Sie die Befehlszeile auf einem Windows-Computer verwenden, ersetzen Sie den umgekehrten Schrägstrich (`\`) durch das Caretzeichen (`^`).
    
    **Hinweis**: Die Ausführung des Befehls dauert 2 bis 3 Minuten. Der Befehl erstellt einen virtuellen Computer und verschiedene damit verbundene Ressourcen wie Speicher-, Netzwerk- und Sicherheitsressourcen. Fahren Sie mit dem nächsten Schritt erst dann fort, wenn die Bereitstellung des virtuellen Computers abgeschlossen ist. 

5. Wenn der Befehl ausgeführt wurde, schließen Sie im Browserfenster den Cloud Shell-Bereich.

6. Suchen Sie im Azure-Portal nach **Virtuelle Computer**, und überprüfen Sie, ob **myVMCLI** ausgeführt wird.

    ![Screenshot der Seite „Virtuelle Computer“, wobei myVMPS ausgeführt wird.](../images/1101.png)


# Aufgabe 3: Befehle in der Cloud Shell ausführen

In dieser Aufgabe üben wir das Ausführen von CLI-Befehlen über Cloud Shell. 

1. Öffnen Sie im Azure-Portal die Option **Azure Cloud Shell**, indem Sie auf das Symbol oben rechts im Azure-Portal klicken.

2. Stellen Sie sicher, dass **Bash** im Dropdown-Menü oben links des Cloud Shell-Bereichs ausgewählt ist.

3. Rufen Sie Informationen zu dem von Ihnen bereitgestellten virtuellen Computer ab, einschließlich Name, Ressourcengruppe, Ort und Status. Beachten Sie, dass PowerState **ausgeführt wird**.

    ```cli
    az vm show --resource-group myRGCLI --name myVMCLI --show-details --output table 
    ```

4. Halten Sie den virtuellen Computer an. Beachten Sie die Meldung, dass die Abrechnung weiterläuft, bis die Zuordnung des virtuellen Computers aufgehoben wird. 

    ```cli
    az vm stop --resource-group myRGCLI --name myVMCLI
    ```

5. Überprüfen Sie den Status Ihres virtuellen Computers. PowerState sollte jetzt den Wert **angehalten** haben.

    ```cli
    az vm show --resource-group myRGCLI --name myVMCLI --show-details --output table 
    ```

# Aufgabe 4: Azure Advisor-Empfehlungen überprüfen

In dieser Aufgabe überprüfen wir die Empfehlungen von Azure Advisor.

   **Hinweis:** Wenn Sie das vorherige Lab (Erstellen eines virtuellen Computers mithilfe von PowerShell) abgeschlossen haben, haben Sie diese Aufgabe bereits ausgeführt. 

1. Suchen Sie auf Blatt **Alle Dienste** nach **Advisor**, und wählen Sie diese Option aus. 

2. Wählen Sie im Blatt **Advisor** den Eintrag **Überblick** aus. Beachten Sie, dass Empfehlungen nach Hochverfügbarkeit, Sicherheit, Leistung und Kosten gruppiert sind. 

    ![Screenshot der Seite „Advisor-Übersicht“. ](../images/1103.png)

3. Wählen Sie **Alle Empfehlungen** aus und nehmen Sie sich die Zeit, um die einzelnen Empfehlungen und vorgeschlagenen Maßnahmen anzuzeigen. 

    **Hinweis:** Die Empfehlungen sind je nach Ihren Ressourcen unterschiedlich. 

    ![Screenshot der Advisor-Seite „Alle Empfehlungen“. ](../images/1104.png)

4. Beachten Sie, dass Sie die Empfehlungen als CSV- oder PDF-Datei herunterladen können. 

5. Beachten Sie, dass Sie Warnungen erstellen können. 

6. Wenn Sie Zeit haben, experimentieren Sie weiter mit Azure CLI. 

Herzlichen Glückwunsch! Sie haben Cloud Shell konfiguriert, einen virtuellen Computer mit Azure CLI erstellt, Azure CLI-Befehle geübt und Advisor-Empfehlungen angesehen.

**Hinweis**: Um zusätzliche Kosten zu vermeiden, können Sie diese Ressourcengruppe entfernen. Suchen Sie nach Ressourcengruppen, klicken Sie auf Ihre Ressourcengruppe und dann auf **Ressourcengruppe löschen**. Überprüfen Sie den Namen der Ressourcengruppe, und klicken Sie dann auf **Löschen**. Überwachen Sie die **Benachrichtigungen**, um zu sehen, wie der Löschvorgang abläuft.
