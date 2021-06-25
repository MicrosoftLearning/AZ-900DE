---
wts:
    title: '06 - Erstellen einer SQL-Datenbank (5 Min.)'
    module: 'Modul 02 - Azure-Kerndienste (Workloads)'
---

# 06 - Erstellen einer SQL-Datenbank

In dieser exemplarischen Vorgehensweise erstellen wir eine SQL-Datenbank in Azure und fragen dann die Daten in dieser Datenbank ab.

# Aufgabe 1: Erstellen Sie die Datenbank (5 Min.)

In dieser Aufgabe werden wir eine SQL-Datenbank auf der Grundlage der AdventureWorksLT-Beispieldatenbank erstellen. 

1. Melden Sie sich beim Azure-Portal an unter [**https://portal.azure.com**](https://portal.azure.com).

2. Suchen Sie auf dem Blatt **Alle Dienste** den Eintrag **SQL-Datenbanken**, wählen Sie ihn aus, und klicken Sie auf **+ Hinzufügen, + Erstellen oder auf + Neu**. 

3. Geben Sie auf der Registerkarte **Grundlagen** diese Informationen ein.  

    | Einstellung | Wert | 
    | --- | --- |
    | Abonnement | **Wählen Sie Ihr Abonnement** |
    | Ressourcengruppe | **myRGDb** (neu erstellen) |
    | Datenbankname| **db1** | 
    | | |

3. Klicken Sie neben der Dropdownliste **Server** auf **Neu erstellen**, und geben Sie diese Informationen ein (ersetzen Sie **xxxx** im Servernamen durch Buchstaben und Ziffern, sodass der Name global eindeutig ist). Klicken Sie auf **OK**, wenn Sie fertig sind.

    | Einstellung | Wert | 
    | --- | --- |
    | Servername | **sqlserverxxxx** (muss eindeutig sein) | 
    | Serveradministratoranmeldung | **sqluser** |
    | Kennwort | **Pa$$w0rd1234** |
    | Standort | **(USA) USA, Osten** |
    | Azure-Diensten Zugriff auf den Server erlauben| ***Aktivieren Sie das Kontrollkästchen*** |
    | | |

   ![Screenshot des Bereichs „Server“ und des Bereichs „Neuer Server“, wobei die Felder entsprechend der Tabelle ausgefüllt und die Schaltflächen „Überprüfen + erstellen“ und „OK“ hervorgehoben sind.](../images/0501.png)

4. Wechseln Sie auf die Registerkarte **Netzwerk**, und konfigurieren Sie die folgenden Einstellungen (lassen Sie andere mit ihren Standardeinstellungen). 

    | Einstellung | Wert | 
    | --- | --- |
    | Konnektivitätsmethode | **Öffentlicher Endpunkt** |    
    | Ermöglichen Sie Azure-Diensten und -Ressourcen den Zugriff auf diesen Server | **Ja** |
    | Aktuelle Client-IP-Adresse hinzufügen | **Nein** |
    | | |
    
   ![Screenshot der Registerkarte „Netzwerk“ des Blatts „SQL-Datenbank erstellen“ mit den in der Tabelle gewählten Einstellungen und hervorgehobener Schaltfläche „Überprüfen + erstellen“.](../images/0501b.png)

5. Wechseln Sie in die Registerkarte **Zusätzliche Einstellungen**. Wir werden die AdventureWorksLT-Beispieldatenbank verwenden.

    | Einstellung | Wert | 
    | --- | --- |
    | Vorhandene Daten verwenden | **Stichprobe** |
    | Sortierung | ***Standard verwenden*** |
    | „Enable Azure Defender for SQL“ (Azure Defender für SQL aktivieren) | **Nicht jetzt** |
    | | |

    ![Screenshot der Registerkarte „Zusätzliche Einstellungen“ des Blatts „SQL-Datenbank erstellen“, wobei die Einstellungen gemäß der Tabelle ausgewählt und die Schaltfläche „Überprüfen + erstellen“ hervorgehoben ist.](../images/0501c.png)

6. Klicken Sie auf **Überprüfen + erstellen** und dann auf **Erstellen**, um die Ressourcengruppe, den Server und die Datenbank bereitzustellen. Die Bereitstellung kann etwa 2 bis 5 Minuten dauern.

7. Navigieren Sie zur Registerkarte „Ressource“, um die SQL-Datenbank zu suchen, die Sie erstellt haben. Möglicherweise müssen Sie aktualisieren.

# Aufgabe 2: Testen der Datenbank

In dieser Aufgabe konfigurieren wir den SQL Server und führen eine SQL-Abfrage aus. 

1. Suchen Sie auf dem Blatt **Alle Dienste** nach **SQL-Datenbanken**, und wählen Sie diese Option aus. Vergewissern Sie sich, dass Ihre neue Datenbank erstellt wurde. Möglicherweise müssen Sie die Seite **Aktualisieren**.

    ![Screenshot der gerade bereitgestellten SQL-Datenbank und des SQL-Servers.](../images/0502.png)

2. Klicken Sie auf den Eintrag **db1**, der die von Ihnen erstellte SQL-Datenbank darstellt, und klicken Sie dann auf **Abfrage-Editor (Vorschau)**.

3. Melden Sie sich als **sqluser** mit dem Kennwort **Pa$$$w0rd1234** an.

4. Sie werden sich nicht anmelden können. Lesen Sie den Fehler genau durch und notieren Sie sich die IP-Adresse, die durch die Firewall erlaubt werden muss. 

    ![Screenshot der Anmeldeseite des Abfrage-Editors mit IP-Adressfehler.](../images/0503.png)

5. Klicken Sie auf dem Blatt **db1** auf **Überblick**. 

    ![Screenshot der Seite „SQL-Server“.](../images/0504.png)

6. Klicken Sie auf dem SQL-Server-Blatt **Überblick** auf **Server-Firewall einstellen**.

7. Klicken Sie auf **Client-IP hinzufügen** (obere Menüleiste), um die IP-Adresse hinzuzufügen, auf die in der Fehlermeldung verwiesen wird. Achten Sie darauf, Ihre Änderungen zu **Speichern**. 

    ![Screenshot der Einstellungsseite der SQL-Server-Firewall mit hervorgehobener neuer IP-Regel.](../images/0506.png)

8. Kehren Sie zu Ihrer SQL-Datenbank und der Anmeldeseite von **Abfrage-Editor (Vorschau)** zurück. Versuchen Sie, sich wieder als **sqluser** mit dem Kennwort **Pa$$$w0rd1234** anzumelden. Diesmal sollten Sie Erfolg haben. Beachten Sie, dass es einige Minuten dauern kann, bis die neue Firewallregel bereitgestellt wird. 

9. Sobald Sie sich erfolgreich angemeldet haben, wird das Abfragefenster angezeigt. Geben Sie die folgende Abfrage in den Editor-Bereich ein.

    ```SQL
    SELECT TOP 20 pc.Name as CategoryName, p.name as ProductName
    FROM SalesLT.ProductCategory pc
    JOIN SalesLT.Product p
    ON pc.productcategoryid = p.productcategoryid;
    ```

    ![Screenshot des Abfrage-Editors mit dem Abfragebereich und den Befehlen, die erfolgreich ausgeführt wurden.](../images/0507.png)

10. Klicken Sie auf **Ausführen**, und überprüfen Sie dann die Abfrageergebnisse im Bereich **Ergebnisse**. Die Abfrage sollte erfolgreich ausgeführt werden.

    ![Screenshot des Datenbank-Abfrage-Editor-Bereichs, in dem der SQL-Code erfolgreich ausgeführt wurde und die Ausgabe im Ergebnisbereich sichtbar ist.](../images/0508.png)

Herzlichen Glückwunsch! Sie haben eine SQL-Datenbank in Azure erstellt und die Daten in dieser Datenbank erfolgreich abgefragt.

**HINWEIS**: Um zusätzliche Kosten zu vermeiden, können Sie diese Ressourcengruppe entfernen. Suchen Sie nach Ressourcengruppen, klicken Sie auf Ihre Ressourcengruppe und dann auf **Ressourcengruppe löschen**. Überprüfen Sie den Namen der Ressourcengruppe und klicken Sie dann auf **Löschen**. Überwachen Sie die **Benachrichtigungen**, um zu sehen, wie der Löschvorgang abläuft.
