---
wts:
    title: '14 – Erstellen einer Azure-Richtlinie'
    module: 'Modul 03 – Sicherheit, Datenschutz, Compliance und Vertrauen'
---
# 14 – Erstellen einer Azure-Richtlinie

In dieser exemplarischen Vorgehensweise erstellen wir eine Azure-Richtlinie, um die Bereitstellung von Azure-Ressourcen auf einen bestimmten Standort zu beschränken.

# Aufgabe 1: Erstellen einer Richtlinienzuweisung

In dieser Aufgabe konfigurieren wir die zulässige Standortrichtlinie und weisen sie unserem Abonnement zu. 

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.

2. Suchen Sie auf dem Blatt **Alle Dienste** nach **Richtlinie**, und wählen Sie sie diese Option aus. Klicken Sie im Abschnitt **Dokumenterstellung** auf **Definitionen**.  Nehmen Sie sich einen Moment Zeit, um die Liste der integrierten Richtliniendefinitionen zu überprüfen. Wählen Sie zum Beispiel in der Dropdownliste **Kategorie** nur **Compute** aus. Beachten Sie mithilfe der Definition **Zulässige SKUs für virtuelle Computer** eine Reihe von SKUs für virtuelle Computer angeben können, die Ihre Organisation bereitstellen kann.

3. Wechseln Sie zurück zur Seite **Richtlinie**, und klicken Sie im Abschnitt **Dokumenterstellung** auf **Aufgaben**. Eine Zuweisung ist eine Richtlinie, die so zugewiesen wurde, dass sie innerhalb eines bestimmten Bereichs erfolgt. Beispielsweise könnte dem Abonnementbereich eine Definition zugewiesen werden. 

4. Klicken Sie auf **Richtlinie zuweisen** im oberen Bereich der Seite **Richtlinie - Aufgaben**.

5. Wählen Sie auf der Seite **Richtlinie zuweisen** die Bereichsauswahl aus, indem Sie auf die Auslassungspunkte klicken.

    ![Screenshot der Ausgangspunkte der Bereichsauswahl.](../images/1401.png)

6. Stellen Sie sicher, dass Ihr Abonnement ausgewählt ist. Ihr Abonnementname kann abweichen. Beachten Sie, dass Sie die Richtlinie optional auf eine Ressourcengruppe beschränken können. Übernehmen Sie die Standardeinstellungen, und klicken Sie auf **Auswählen**. 

    **Hinweis**: Ein Bereich bestimmt, für welche Ressourcen oder Gruppen von Ressourcen die Richtlinienzuweisung gilt. In unserem Fall könnten wir diese Richtlinie einer bestimmten Ressourcengruppe zuweisen. Wir haben uns jedoch dafür entschieden, die Richtlinie auf Abonnementebene zuzuweisen. Beachten Sie, dass Ressourcen basierend auf der Bereichskonfiguration ausgeschlossen werden können. Ausschlüsse sind optional.

    ![Screenshot des Bereichs „Bereich“ mit ausgefüllten Feldwerten und hervorgehobener Schaltfläche „Auswählen“. ](../images/1402.png)

7. Wählen Sie die Schaltfläche mit den Auslassungspunkten **Richtliniendefinition** aus. Geben Sie in das Feld **Suche** die Zeichenfolge **Standort** ein, und klicken Sie auf die Definition **Zulässige Standorte** und dann auf **Auswählen**.

    **Hinweis**: Die Richtliniendefinition **Zulässige Standorte** gibt einen Speicherort an, an dem alle Ressourcen bereitgestellt werden müssen. Wenn ein anderer Speicherort ausgewählt wird, ist die Bereitstellung nicht zulässig. Weitere Informationen finden Sie auf der Seite [Azure Policy-Beispiele](https://docs.microsoft.com/de-de/azure/governance/policy/samples/index).

   ![Screenshot des Bereichs „Verfügbare Definitionen“ mit verschiedenen hervorgehobenen Feldern und ausgewählter Option „Überwachungs-VMs, die keine verwalteten Datenträger verwenden“.](../images/1403.png)

8.  Wechseln Sie im Bereich **Richtlinie zuweisen** zur Registerkarte **Parameter**, klicken Sie auf den Pfeil am Ende des Felds **Zulässige Standorte**, und wählen Sie aus der nachfolgenden Liste **Japan, Westen** aus. Lassen Sie alle anderen Werte unverändert, und klicken Sie auf **Überprüfen + Erstellen** und dann auf **Erstellen**.

    ![Screenshot des Bereichs „Richtlinie zuweisen“ mit verschiedenen Feldern, die zusammen mit dem angegebenen Standort „Japan, Westen“ und der Schaltfläche „Zuweisen“ hervorgehoben sind.](../images/1404.png)

9. Die Richtlinienzuweisung **Zulässige Standorte** ist jetzt auf der Liste **Richtlinie - Aufgaben** aufgeführt und in Kraft getreten und setzt die Richtlinie auf der von uns angegebenen Bereichsebene (Abonnementebene) durch.

# Aufgabe 2: Testen der Richtlinie für zulässige Standorte

In dieser Aufgabe testen wir die Richtlinie für zulässige Standorte. 

1. Suchen Sie im Azure-Portal auf dem Blatt **Alle Dienste** nach **Speicherkonten**, und wählen Sie diese Option aus. Klicken Sie anschließend auf **+ Hinzufügen**.

2. Konfigurieren Sie das Speicherkonto (ersetzen Sie **xxxx** im Namen des Speicherkontos mit Buchstaben und Ziffern, so dass der Name global eindeutig ist). Belassen Sie ansonsten die Standardeinstellungen. 

    | Einstellung | Wert | 
    | --- | --- |
    | Abonnement | **Verwenden Sie Ihr Abonnement** |
    | Ressourcengruppe | **myRGPolicy** (Neu erstellen) |
    | Name des Speicherkontos | **storageaccountxxxx** |
    | Ort | **(USA) USA, Osten** |
    | | |

3. Klicken Sie auf **Überprüfen + Erstellen** und dann auf **Erstellen**. 

4. Sie erhalten die Fehlermeldung „Bereitstellung fehlgeschlagen“, die besagt, dass die Ressource von der Richtlinie nicht zugelassen wurde, einschließlich des Richtliniennamens **Zulässige Standorte**.

# Aufgabe 3: Richtlinienzuweisung löschen

In dieser Aufgabe entfernen wir die Zuweisung und den Test der zulässigen Richtlinienzuweisung. 

Wir werden die Richtlinienzuweisung löschen, um sicherzustellen, dass wir bei zukünftigen Arbeiten, die wir ausführen möchten, nicht blockiert werden.

1. Suchen Sie auf dem Blatt **Alle Dienste** nach **Richtlinie**, und wählen Sie diese Option aus. Klicken Sie anschließend auf Ihre Richtlinie **Zulässige Standorte**.

    **Hinweis**: Auf dem Blatt **Richtlinie** können Sie den Konformitätszustand der verschiedenen Richtlinien anzeigen, die Sie zugewiesen haben.

    **Hinweis**: Mit der Richtlinie „Zulässiger Standort“ werden möglicherweise nicht konforme Ressourcen angezeigt. In diesem Fall handelt es sich um Ressourcen, die vor der Richtlinienzuweisung erstellt wurden.

2. Klicken Sie im obersten Menü auf **Arbeitsauftrag löschen**.

   ![Screenshot des Menüelements „Zuweisung löschen“.](../images/1407.png)

3. Bestätigen Sie, dass Sie die Richtlinienzuweisung löschen möchten, indem Sie im Dialogfeld **Zuweisung löschen** auf **Ja** klicken.

4. Versuchen Sie, ein anderes Speicherkonto zu erstellen, um sicherzustellen, dass die Richtlinie nicht mehr gültig ist.

    **Hinweis**: Häufige Szenarien, in denen die Richtlinie **Zulässige Standorte** nützlich sein kann, wären: 
    - *Kostenverfolgung*: Sie können unterschiedliche Abonnements für unterschiedliche regionale Standorte haben. Die Richtlinie wird sicherstellen, dass alle Ressourcen in der vorgesehenen Region bereitgestellt werden, um die Kostenverfolgung zu unterstützen. 
    - *Datenresidenz und Sicherheitskonformität*: Sie können auch Anforderungen an die Datenaufbewahrung haben und Abonnements pro Kunde oder bestimmten Workloads erstellen und festlegen, dass alle Ressourcen in einem bestimmten Rechenzentrum bereitgestellt werden müssen, um die Complianceanforderungen bezüglich Daten und Sicherheit zu gewährleisten.

Herzlichen Glückwunsch! Sie haben eine Azure-Richtlinie erstellt, die die Bereitstellung von Azure-Ressourcen auf ein bestimmtes Rechenzentrum beschränkt.

**Hinweis**: Um zusätzliche Kosten zu vermeiden, können Sie diese Ressourcengruppe entfernen. Suchen Sie nach Ressourcengruppen, klicken Sie auf Ihre Ressourcengruppe und dann auf **Ressourcengruppe löschen**. Überprüfen Sie den Namen der Ressourcengruppe, und klicken Sie dann auf **Löschen**. Überwachen Sie die **Benachrichtigungen**, um zu sehen, wie der Löschvorgang abläuft.