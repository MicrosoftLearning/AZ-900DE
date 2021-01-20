---
wts:
    title: '19 – Verwenden des Azure-Preisrechners (10 Min.)'
    module: 'Modul 06: Beschreiben von Azure Cost Management und der Vereinbarungen zum Servicelevel'
---
# 19 – Verwenden des Preisrechners

In dieser exemplarischen Vorgehensweise verwenden wir den Azure-Preisrechner, um einen Kostenvoranschlag für einen virtuellen Azure-Computer und zugehörige Netzwerkressourcen zu erstellen.

# Aufgabe 1: Konfigurieren des Preisrechners (10 Min.)

In dieser Aufgabe schätzen wir die Kosten einer Infrastruktur-Stichprobe mithilfe des Azure-Preisrechners ab. 

**Hinweis**: Um eine Azure-Preisrechnerschätzung zu erstellen, enthält diese exemplarische Vorgehensweise Beispielkonfigurationen für den virtuellen Computer und die zugehörigen Ressourcen. Verwenden Sie diese Beispielkonfigurationen, oder stellen Sie stattdessen dem Azure-Preisrechner Details zu Ihren *tatsächlichen* Ressourcenanforderungen zur Verfügung.

1. Navigieren Sie in einem Browser zur [Azure-Preisrechner](https://azure.microsoft.com/de-de/pricing/calculator/)-Webseite.

2. Klicken Sie auf der Registerkarte **Produkte** auf **Virtual Machines**, um Details zu Ihrer Konfiguration des virtuellen Computers hinzuzufügen. Scrollen Sie nach unten, um die Details des virtuellen Computers anzuzeigen. 

3. Ersetzen Sie den Text **Ihre Schätzung** und **Virtuelle Computer** mit aussagekräftigeren Namen für Ihre Azure-Preisrechnerschätzung und Ihre Konfiguration des virtuellen Computers. In dieser exemplarischen Vorgehensweise wird **Meine Preisrechnerschätzung** für die Schätzung und **Virtueller Windows-Computer** für die Konfiguration des virtuellen Computers verwendet.

   ![Screenshot des VM-Konfigurationsbereichs auf der Azure-Webseite für Preisrechnerschätzung. Der hervorgehobene Schätzungsname und der Konfigurationsname des virtuellen Computers geben an, wie ein Schätzungsname und ein Konfigurationsname für den virtuellen Computer zu einer Schätzung des Azure-Preisrechners hinzugefügt werden.](../images/1901.png)

4. Ändern Sie die Standardkonfiguration des virtuellen Computers.

    | Region | Betriebssystem | Typ |
    |------|----------------|----|
    | Europa, Norden | Windows | (Nur Betriebssystem) |
    | | |

    | Ebene | Instanz |
    |----|--------|
    | Standard | A2: 2 Kernspeicher, 3,5 GB RAM, 135 GB temporärer Speicher |
    | | |

   ![Screenshot des VM-Konfigurationsbereichs auf der Azure-Webseite für Preisrechnerschätzung. Die hervorgehobenen Beispiele für vom Benutzer eingegebene Konfigurationseigenschaftswerte des virtuellen Computers geben an, wie eine Konfiguration des virtuellen Computers in einer Azure-Preisrechnerschätzung angegeben wird.](../images/1902.png)

    **Hinweis**: Die Spezifikationen und Preise der Instanzen des virtuellen Computers können von denen in diesem Beispiel abweichen. Folgen Sie dieser exemplarischen Vorgehensweise, indem Sie eine Instanz auswählen, die dem Beispiel so genau wie möglich entspricht. Wählen Sie im Menü **Mehr Info** rechts **Produktdetails** aus, um Details zu den verschiedenen Produktoptionen des virtuellen Computers anzuzeigen.

5. Legen Sie **Abrechnungsoption** auf **Vorausbezahlung** fest.

   ![Screenshot des Bereichs mit den Abrechnungsoptionen des virtuellen Computers auf der Azure-Webseite für Preisrechnerschätzung. Die hervorgehobene Abrechnungsoption „Vorausbezahlung“ gibt an, wie eine Abrechnungsoption für einen virtuellen Computer in einer Azure-Preisrechnerschätzung angegeben wird.](../images/1903.png)

6. In Azure wird ein Monat als 730 Stunden definiert. Wenn Ihr virtueller Computer jeden Monat zu 100 Prozent verfügbar sein muss, setzen Sie den Wert für Stunden pro Monat auf `730`. In diesem exemplarischen Vorgehensweise muss ein virtueller Computer jeden Monat zu 50 Prozent verfügbar sein.

    Belassen Sie die Anzahl der virtuellen Computer auf `1`, und ändern Sie den Wert für Stunden pro Monat zu `365`.

   ![Screenshot des Bereichs mit den Abrechnungsoptionen des virtuellen Computers auf der Azure-Webseite für Preisrechnerschätzung. Die hervorgehobene Zahl von Instanzen des virtuellen Computers und Stunden pro Monat gibt an, wie die Anzahl von Instanzen und Stunden pro Monat für einen virtuellen Computer in einer Schätzung des Azure-Preisrechners bestimmt wird.](../images/1904.png)

7. Ändern Sie im Bereich **Verwaltete BS-Datenträger** die standardmäßige VM-Speicherkonfiguration.

    | Ebene | Diskgröße | Zahl der Disks | Momentaufnahme | Speichertransaktionen |
    | ---- | --------- | --------------- | -------- | -------------------- |
    | HDD Standard | S30: 1.024 GiB | 1 | Aus | 10.000 |

   ![Screenshot des Optionsbereichs für verwaltete Betriebssystemdatenträger auf der Azure-Preisberechnungs-Webseite. Die hervorgehobenen Optionen für Stufentyp, Datenträgergröße, Anzahl der Datenträger und Anzahl der Speichertransaktionen geben an, wie eine Speicherkonfiguration für einen virtuellen Computer in einer Azure-Preisrechnerschätzung angegeben wird.](../images/1905.png)

8. Informationen zum Hinzufügen von Netzwerkbandbreite zu Ihrer Schätzung finden Sie oben auf der Azure-Preisrechner-Webseite. Klicken Sie auf **Netzwerk** im Produktmenü links und dann auf die Kachel **Bandbreite**. Klicken Sie im Meldungsdialogfeld **Bandbreite hinzugefügt** auf **Anzeigen**.

   ![Screenshot des Bereichs für Netzwerkprodukte auf der Azure-Preisrechner-Webseite. Die hervorgehobenen Kacheln „Netzwerk“, „Bandbreite hinzufügen“ und „Bandbreite anzeigen“ geben an, wie Details einer Netzwerkbandbreiten-Konfiguration in einer Azure-Preisrechnerschätzung hinzugefügt und angezeigt werden.](../images/1906.png)

9. Fügen Sie einen Namen für die Bandbreitenkonfiguration Ihres virtuellen Computers hinzu. In diesem exemplarischen Beispiel lautet der Name **Bandbreite: Windows-VM**. Ändern Sie die standardmäßige Bandbreitenkonfiguration, indem Sie die folgenden Details hinzufügen.

    | Region | Betrag für ausgehende Datenübertragung in Zone 1 |
    | ------ | -------------------------------------- |
    | Europa, Norden | 50 GB |

   ![Screenshot des Konfigurationsbereichs für die Netzwerkbandbreite auf der Webseite der Azure-Preisrechners. Die hervorgehobenen Beispiele für vom Benutzer eingegebene Bandbreiten-Eigenschaftswerte geben an, wie eine Bandbreitenkonfiguration für einen virtuellen Computer innerhalb einer Azure-Preisrechnerschätzung angegeben wird.](../images/1907.png)

10. Kehren Sie zum Hinzufügen eines Application Gateway zum Anfang der Azure-Preisrechner-Webseite zurück. Klicken Sie im Produktmenü **Netzwerk** auf die Kachel **Application Gateway**. Klicken Sie im Meldungsdialogfeld **Application Gateway** auf **Anzeigen**.

    ![Screenshot des Bereichs für Netzwerkprodukte auf der Azure-Preisrechner-Webseite. In den hervorgehobenen Kacheln „Netzwerk“, „Application Gateway hinzufügen“ und „Application Gateway anzeigen“ wird angegeben, wie Details einer Application Gateway-Konfiguration in einer Azure-Preisrechnerschätzung hinzugefügt und angezeigt werden.](../images/1908.png)

11. Fügen Sie einen Namen für Ihre Application Gateway-Konfiguration hinzu. In dieser exemplarischen Vorgehensweise ist der Name **App Gateway: Windows-VM**. Ändern Sie die Standardkonfiguration des Application Gateway, indem Sie die folgenden Details hinzufügen.

    | Region | Ebene | Größe |
    | ------ | ---- | ---- |
    | Europa, Norden | Basic | Klein |
    | | |

    | Instanzen | Stunden |
    | ------- | ------- |
    | 1 | 365 |
    | | |

    | Verarbeitete Daten |
    | -------------- |
    | 50 GB |
    | | |

    | Zone 1: Nordamerika, Europa |
    | ----------------------------- |
    | 50 GB |
    | | |

    ![Screenshot des Application Gateway-Konfigurationsbereichs auf der Webseite für die Azure-Preisrechnerschätzung.](../images/1909.png)


# Aufgabe 2: Preisschätzung überprüfen

In dieser Aufgabe werden die Ergebnisse des Azure-Preisrechners überprüft. 

1. Scrollen Sie zum Ende der Azure-Preisrechner-Webseite, um die Gesamtsumme der **Geschätzten monatlichen Kosten** anzuzeigen.

    **Hinweis**: Informieren Sie sich über die verschiedenen Optionen, die im Azure-Preisrechner verfügbar sind. In dieser exemplarischen Vorgehensweise müssen Sie beispielsweise die Währung auf Euro aktualisieren.

2. Ändern Sie die Währung in Euro und wählen Sie dann **Export**, um eine Kopie des Kostenvoranschlags für die Offline-Anzeige im Microsoft Excel-Format (`.xlsx`) herunterzuladen.

    ![Screenshot der geschätzten monatlichen Gesamtkosten auf der Webseite für die Azure-Preisrechnerschätzung. Die hervorgehobene Euro-Währungsoption gibt an, wie die in einer Azure-Preisrechnerschätzung verwendete Währung geändert werden kann. Die hervorgehobene Exportoption zeigt, wie Sie eine Kopie eines Kostenvoranschlags für die Offline-Anzeige herunterladen.](../images/1910.png)

    ![Screenshot einer Beispielschätzung des Azure-Preisrechners in Microsoft Excel.](../images/1911.png)

Herzlichen Glückwunsch! Sie haben einen Kostenvoranschlag aus dem Azure-Preisrechner heruntergeladen.