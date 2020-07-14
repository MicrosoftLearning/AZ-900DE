---
wts:
    title: '13 – Implementieren von Azure Key Vault'
    module: 'Modul 03 – Sicherheit, Datenschutz, Compliance und Vertrauen'
---
# 13 – Implementieren von Azure Key Vault

In dieser exemplarischen Vorgehensweise erstellen wir einen Azure Key Vault und erstellen dann ein Kennwortgeheimnis in diesem Schlüsseltresor. Dabei wird ein sicher gespeichertes, zentral verwaltetes Kennwort für die Verwendung mit Anwendungen bereitgestellt.

# Aufgabe 1: Einen Azure Key Vault erstellen

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.

2. Suchen Sie im Blatt **Alle Dienste** die Option **Schlüsseltresore**, und wählen Sie sie aus. Wählen Sie dann **+ Hinzufügen** aus.

3. Konfigurieren Sie den Schlüsseltresor (ersetzen Sie **xxxx** im Namen des Schlüsseltresors durch Buchstaben und Ziffern, sodass der Name global eindeutig ist). Belassen Sie ansonsten die Standardeinstellungen.

    | Einstellung | Wert | 
    | --- | --- |
    | Abonnement | **Verwenden Sie Ihr Abonnement** |
    | Ressourcengruppe | **myRGKV** (Neu erstellen) |
    | Schlüsseltresorname | **keyvaulttestxxx** |
    | Ort | **USA, Osten** |
    | Tarif | **Standard** |
    | | |

4. Klicken Sie auf **Überprüfen + Erstellen **, und klicken Sie dann auf **Erstellen**. 

5. Wenn der neue Schlüsseltresor bereitgestellt ist, klicken Sie auf **Zu Ressource wechseln**. Sie können aber auch nach Ihrem neuen Schlüsseltresor suchen. 

6. Klicken Sie auf die Schlüsseltresor-Registerkarte **Übersicht**, und beachten Sie die Angabe für **DNS-Name**. Anwendungen, die Ihren Tresor über die REST-API verwenden, werden diesen URI benötigen.

7. Nehmen Sie sich einen Moment Zeit, um einige der anderen wichtigen Schlüsseltresoroptionen zu durchsuchen. Prüfen Sie unter **Einstellungen** die Einträge **Schlüssel**, **Geheimnisse**, **Zertifikate**, **Zugriffsrichtlinien** und **Firewalls und virtuelle Netzwerke**.

    **Hinweis**: Ihr Azure-Konto ist das einzige, das berechtigt ist, Vorgänge für diesen neuen Tresor auszuführen. Wenn Sie wünschen, können Sie dies im Abschnitt **Einstellungen** unter **Zugriffsrichtlinien** ändern.

# Aufgabe 2: Dem Schlüsseltresor einen geheimen Schlüssel hinzufügen
        
In dieser Aufgabe fügen wir dem Schlüsseltresor ein Kennwort hinzu. 

1. Klicken Sie unter **Einstellungen** auf **Geheimnisse** und dann auf **Generieren / Importieren**.

2. Konfigurieren Sie das Geheimnis. Belassen Sie für die anderen Werte die Standardeinstellungen. Beachten Sie, dass Sie ein Aktivierungs- und Ablaufdatum festlegen können. Beachten Sie, dass Sie das Geheimnis auch deaktivieren können.

    | Einstellung | Wert | 
    | --- | --- |
    | Uploadoptionen | **Manuell** |
    | Name | **ExamplePassword** |
    | Wert | **hVFkk96** |
    | | |

3. Klicken Sie auf **Erstellen**.

4. Sobald der geheime Schlüssel erfolgreich erstellt wurde, klicken Sie auf **ExamplePassword**. Beachten Sie, dass der Status **Aktiviert** lautet.

5. Klicken Sie auf die aktuelle Version, und beachten Sie die **Geheimnis-ID**. Dies ist der URL-Wert, den Sie jetzt mit Anwendungen verwenden können. Er bietet ein zentral verwaltetes und sicher gespeichertes Kennwort.

6. Klicken Sie auf die Schaltfläche **Geheimniswert anzeigen**, um das zuvor angegebene Kennwort anzuzeigen.

Herzlichen Glückwunsch! Sie haben einen Azure Key Vault erstellt und anschließend in diesem Schlüsseltresor ein Kennwortgeheimnis erstellt. Damit steht ein sicher gespeichertes, zentral verwaltetes Kennwort für die Nutzung mit Anwendungen zur Verfügung.

**Hinweis**: Um zusätzliche Kosten zu vermeiden, können Sie diese Ressourcengruppe entfernen. Suchen Sie nach Ressourcengruppen, klicken Sie auf Ihre Ressourcengruppe und dann auf **Ressourcengruppe löschen**. Überprüfen Sie den Namen der Ressourcengruppe, und klicken Sie dann auf **Löschen**. Überwachen Sie die **Benachrichtigungen**, um zu sehen, wie der Löschvorgang abläuft.
