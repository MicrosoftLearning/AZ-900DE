---
wts:
    title: '20 – Verwenden des Azure-TCO-Rechners'
    module: 'Modul 04 – Azure-Preise und -Support'
---
# 20 – Verwenden des Azure-Gesamtbetriebskostenrechners


In dieser exemplarischen Vorgehensweise verwenden Sie den Gesamtbetriebskostenrechner, um einen Kostenvergleichsbericht für eine lokale Umgebung zu erstellen.

**Hinweis**: Diese exemplarische Vorgehensweise enthält Beispieldefinitionen der lokalen Infrastruktur und Workloads für ein typisches Rechenzentrum. Verwenden Sie zum Erstellen eines Gesamtbetriebskosten-Rechner-Berichts die Beispieldefinitionen, oder geben Sie Details Ihrer *tatsächlich* lokalen Infrastruktur und Arbeitsauslastungen an.

# Aufgabe 1: Konfigurieren des Gesamtbetriebskostenrechners

In dieser Aufgabe fügen wir dem Rechner Infrastrukturinformationen hinzu. 

1. Navigieren Sie in einem Browser zur Seite [Gesamtkostenrechner](https://azure.microsoft.com/de-de/pricing/tco/calculator/).

2. Um Details zu Ihrer lokalen Serverinfrastruktur hinzuzufügen, klicken Sie im Bereich **Workloads definieren** auf **+ Serverworkload hinzufügen**.

    | Einstellungen | Wert |
    | -- | -- |
    | Name | **Server: Windows-VMs** |
    | Workload | **Windows-/Linux-Server** |
    | Umgebung | **Virtuelle Computer** |
    | Betriebssystem | **Windows** |  
    | VMs | **50** |
    | Virtualisierung | **Hyper-V** |
    | Kern(e) | **8**|
    | RAM (GB) | **16** |
    | Optimieren nach | **CPU** |
    |  Windows Server 2008/2008 R2 | **Aus** |
    | | |

3. Wählen Sie **+ Server-Arbeitsauslastung hinzufügen** aus, um eine Zeile für eine neue Definition der Server-Arbeitsauslastungen zu erstellen. 

    | Einstellungen | Wert |
    | -- | -- |
    | Name | **Server: Linux-VMs** |
    | Workload | **Windows-/Linux-Server** |
    | Umgebung | **Virtuelle Computer** |
    | Betriebssystem | **Linux** |  
    | VMs | **50** |
    | Virtualisierung | **VMware** |
    | Kern(e) | **8**|
    | RAM (GB) | **16** |
    | Optimieren nach | **CPU** |
    |  Windows Server 2008/2008 R2 | **Aus** |
    | | |

4. Klicken Sie im Bereich **Speicher** auf **Speicher hinzufügen**.

    | Einstellungen | Wert |
    | -- | -- |
    | Name | **Serverspeicher** |
    | Speichertyp | **Lokale Festplatte/SAN** |
    | Datenträgertyp | **Festplattenlaufwerk** |
    | Kapazität | **60 TB** |  
    | Sicherung | **120 TB** |
    | Archivierung | **0 TB** |
    | | |

5. Fügen Sie im Bereich **Netzwerk** Bandbreite hinzu. 

    | Einstellungen | Wert |
    | -- | -- |
    | Ausgehende Bandbreite | 15 TB|
    | | |

6. Klicken Sie auf **Weiter**.

7. Prüfen Sie die Optionen, und nehmen Sie erforderliche Anpassungen vor. 

    | Einstellungen | Wert |
    | -- | -- |
    | Währung | **Euro** |
    | | |

8. Klicken Sie auf **Weiter**.

# Aufgabe 2: Ergebnisse überprüfen und eine Kopie speichern

In dieser Aufgabe werden wir die Empfehlungen zur Kosteneinsparung überprüfen und einen Bericht herunterladen. 

1. Lesen Sie die Azure-Empfehlungen und -Visualisierungen zur Kosteneinsparung.

    | Einstellungen | Wert |
    | -- | -- |
    | Zeitrahmen| **3 Jahre** |
    | Region | **Europa, Norden** |
    | | |


2. Um die von Ihnen angegebenen Informationen zu ändern, gehen Sie zum Ende der Seite, und klicken Sie auf **Zurück**. 

3. Um eine PDF-Kopie des Berichts zu speichern oder zu drucken, klicken Sie auf **Herunterladen**.

    ![Screenshot des Berichtsbereichs des Gesamtbetriebskostenrechners in Azure. Die hervorgehobenen und ausgefüllten Eingabefelder geben an, wie der Zeitrahmen des Gesamtbetriebskostenrechners auf drei Jahre und die Region auf Nordeuropa eingestellt wird. Ein Diagramm zeigt die Kosten für lokale Infrastruktur und Workloads im Vergleich zu den durch die Verwendung von Azure reduzierten Kosten.](../images/2001.png)

Herzlichen Glückwunsch! Sie haben den Gesamtbetriebskosten-Rechner verwendet, um einen Kostenvergleichsbericht für eine lokale Umgebung zu erstellen.
