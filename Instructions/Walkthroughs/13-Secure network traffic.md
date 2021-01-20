---
wts:
    title: '13 – Sicherer Netzwerkdatenverkehr (10 Min.)'
    module: 'Modul 04: Beschreiben der allgemeinen Sicherheit und von Netzwerksicherheitsfeatures'
---
# 13 – Sicherer Netzwerkdatenverkehr

In dieser Anleitung konfigurieren wir eine Netzwerksicherheitsgruppe.

# Aufgabe 1: Erstellen eines virtuellen Computers (10 Min.)

In dieser Aufgabe erstellen wir einen virtuellen Windows Server 2019 Datacenter-Computer. 

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.

2. Suchen Sie auf dem Blatt **Alle Dienste** nach **Virtuelle Computer**, und wählen Sie diese Option aus. Klicken Sie dann auf **+ Hinzufügen**.

3. Auf der Registerkarte **Grundlagen** geben Sie die folgenden Informationen ein (belassen Sie ansonsten die Standardeinstellungen):

    | Einstellungen | Werte |
    |  -- | -- |
    | Abonnement | **Wählen Sie Ihr Abonnement**|
    | Ressourcengruppe | **myRGSecure** (Neu erstellen) |
    | Name des virtuellen Computers | **SimpleWinVM** |
    | Standort | **(US) East US**|
    | Bild | **Windows Server 2019 Datacenter**|
    | Größe | **Standard D2s v3**|
    | Benutzername des Administratorkontos | **azureuser** |
    | Kennwort für das Administratorkonto | **Pa$$w0rd1234**|
    | Regeln für eingehende Ports | **Keine**|
    | | |

4. Wechseln Sie zur Registerkarte **Netzwerk**, und konfigurieren Sie die folgende Einstellung:

    | Einstellungen | Werte |
    | -- | -- |
    | NIC-Netzwerksicherheitsgruppe | **Keine**|
    | | |

5. Wechseln Sie zur Registerkarte **Verwaltung**, und wählen Sie im Abschnitt **Überwachung** die folgende Einstellung aus:

    | Einstellungen | Werte |
    | -- | -- |
    | Startdiagnose | **Deaktivieren**|
    | | |

6. Übernehmen Sie die verbleibenden Standardeinstellungen, und klicken Sie dann auf die Schaltfläche **Überprüfen + Erstellen** am unteren Rand der Seite.

7. Sobald die Validierung bestanden ist, klicken Sie auf die Schaltfläche **Erstellen**. Es kann etwa fünf Minuten dauern, den virtuellen Computer bereitzustellen.

8. Überwachen Sie die Bereitstellung. Das Erstellen der Ressourcengruppe und des virtuellen Computers kann einige Minuten dauern. 

9. Klicken Sie im Bereitstellungsblatt oder im Infobereich auf **Zu Ressource wechseln**. 

10. Klicken Sie auf dem **SimpleWinVM**-Blatt des virtuellen Computers auf **Netzwerk** und überprüfen Sie die Registerkarte **Regeln für eingehende Ports**. Beachten Sie, dass der Netzwerkschnittstelle des virtuellen Computers oder dem Subnetz, an das die Netzwerkschnittstelle angeschlossen ist, keine Netzwerksicherheitsgruppe zugeordnet ist.

    **HINWEIS**: Identifizieren Sie den Namen der Netzwerkschnittstelle. Sie werden dies in der nächsten Aufgabe benötigen.

# Aufgabe 2: Netzwerksicherheitsgruppe erstellen

In dieser Aufgabe erstellen wir eine Netzwerksicherheitsgruppe und ordnen sie der Netzwerkschnittstelle zu.

1. Suchen Sie auf dem Blatt **Alle Dienste** nach **Netzwerksicherheitsgruppen**, und wählen Sie diese Option aus. Klicken Sie anschließend auf **+ Hinzufügen**.

2. Geben Sie die folgenden Einstellungen auf der Registerkarte **Grundlagen** des Blatts **Netzwerksicherheitsgruppe erstellen** an.

    | Einstellung | Wert |
    | -- | -- |
    | Abonnement | **Wählen Sie Ihr Abonnement** |
    | Ressourcengruppe | **myRGSecure** |
    | Name | **myNSGSecure** |
    | Region | **(USA) USA, Osten**  |
    | | |

3. Klicken Sie auf **Überprüfen + Erstellen** und nach der Validierung auf **Erstellen**.

4. Klicken Sie nach dem Erstellen des NSG auf **Zu Ressource wechseln**.

5. Klicken Sie unter **Einstellungen** auf **Netzwerkschnittstellen** und dann auf **+ Zuordnen**.

6. Wählen Sie die in der vorherigen Aufgabe identifizierte Netzwerkschnittstelle aus. 

# Aufgabe 3: Portregel für die Sicherheit eingehender Verbindungen konfigurieren, um RDP zuzulassen

In dieser Aufgabe erlauben wir den RDP-Verkehr zum virtuellen Computer, indem wir eine eingehende Sicherheitsportregel konfigurieren. 

1. Navigieren Sie im Azure-Portal zum Blatt des virtuellen Computers **SimpleWinVM**. 

2. Klicken Sie im Bereich **Übersicht** auf **Verbinden**.

3. Versuchen Sie, über RDP eine Verbindung zum virtuellen Computer herzustellen. Standardmäßig erlaubt die Netzwerksicherheitsgruppe kein RDP. Schließen Sie das Fehlerfenster. 

    ![Screenshot der Fehlermeldung, die besagt, dass die Verbindung zum virtuellen Computer fehlgeschlagen ist.](../images/1201.png)

4. Scrollen Sie im Blatt „Virtueller Computer“ nach unten zum Abschnitt **Einstellungen** und klicken Sie auf **Netzwerk**. Beachten Sie, dass die eingehenden Regeln für die Netzwerksicherheitsgruppe **myNSGSecure (an die Netzwerkschnittstelle angeschlossen: myVMNic)** den gesamten eingehenden Datenverkehr mit Ausnahme des Datenverkehrs innerhalb des virtuellen Netzwerks und der Load Balancer-Tests verweigert.

5. Klicken Sie auf der Registerkarte **Regeln für eingehende Ports** auf **Regel für eingehende Ports hinzufügen**. Klicken Sie auf **Hinzufügen**, wenn Sie fertig sind. 

    | Einstellung | Wert |
    | -- | -- |
    | Quelle | **Beliebig**|
    | Quellportbereiche | **\*** |
    | Ziel | **Beliebig** |
    | Zielportbereiche | **3389** |
    | Protokoll | **TCP** |
    | Aktion | **Zulassen** |
    | Priorität | **300** |
    | Name | **AllowRDP** |
    | | |

6. Warten Sie bis zum Bereitstellen der Regel, und versuchen Sie dann erneut sich per RDP mit dem virtuellen Computer zu verbinden. Diesmal sollten Sie Erfolg haben. Denken Sie daran, der Benutzername ist **azureuser**, und das Passwort lautet **Pa$$w0rd1234**.

# Aufgabe 4: Ausgehende Sicherheitsportregel konfigurieren, um den Internetzugriff zu verweigern

In dieser Aufgabe erstellen wir eine NSG-Regel für ausgehende Ports, die den Internetzugriff verweigert, und testen dann, ob die Regel funktioniert.

1. Fahren Sie in der RDP-Sitzung Ihres virtuellen Computers fort. 

2. Öffnen Sie nach dem Start der Maschine den **Internet Explorer**-Browser. 

3. Stellen Sie sicher, dass Sie auf **https://www.bing.com** zugreifen können, und schließen Sie dann Internet Explorer. Sie müssen sich durch die erweiterten Sicherheits-Popups von IE durcharbeiten. 

    **HINWEIS**: Wir konfigurieren nun eine Regel, um den ausgehenden Internetzugang zu verweigern. 

4. Navigieren Sie im Azure-Portal zurück zum Blatt des virtuellen Computers **SimpleWinVM**. 

5. Klicken Sie unter **Einstellungen** auf **Netzewerk** und dann auf **Regeln für ausgehende Ports**.

6. Beachten Sie, dass es die Regel **AllowInternetOutbound** gibt. Dies ist eine Standardregel und kann nicht entfernt werden. 

7. Klicken Sie auf **Regel für ausgehende Ports hinzufügen** rechts von der Netzwerksicherheitsgruppe **myNSGSecure (an die Netzwerkschnittstelle angeschlossen: myVMNic)** und konfigurieren Sie eine neue ausgehende Sicherheitsregel mit einer höheren Priorität, die den Internetverkehr verweigert. Klicken Sie auf  **Hinzufügen**, wenn Sie fertig sind. 

    | Einstellung | Wert |
    | -- | -- |
    | Quelle | **Beliebig**|
    | Quellportbereiche | **\*** |
    | Ziel | **Diensttag** |
    | Zieldiensttag | **Internet** |
    | Zielportbereiche | **\*** |
    | Protokoll | **TCP** |
    | Aktion | **Verweigern** |
    | Priorität | **4000** |
    | Name | **DenyInternet** |
    | | |

8. Kehren Sie zu Ihrer RDP-Sitzung zurück. 

9. Wechseln Sie zu **https://www.microsoft.com**. Die Seite sollte nicht angezeigt werden. Möglicherweise müssen Sie sich durch zusätzliche erweiterte Sicherheits-Popups im IE durcharbeiten.  

**HINWEIS**: Um zusätzliche Kosten zu vermeiden, können Sie diese Ressourcengruppe entfernen. Suchen Sie nach Ressourcengruppen, klicken Sie auf Ihre Ressourcengruppe und dann auf **Ressourcengruppe löschen**. Überprüfen Sie den Namen der Ressourcengruppe und klicken Sie dann auf **Löschen**. Überwachen Sie die **Benachrichtigungen**, um zu sehen, wie der Löschvorgang abläuft.
