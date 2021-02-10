---
title: Laden von Testlaufeinstellungen
description: Hier erfahren Sie, wie Sie für jeden Auslastungstest mehrere Ausführungseinstellungen erstellen und speichern und anschließend eine bestimmte Einstellung für die Ausführung des Tests auswählen.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: reference
helpviewer_keywords:
- load tests, run settings
ms.assetid: de10dabb-02ed-403b-9e6f-0b735524988c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 44cc68a900475c77856053de41ef8b7c5c810d6b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887678"
---
# <a name="load-test-run-settings-properties"></a>Eigenschaften von Laufzeiteinstellungen für Auslastungstests

Mit den Testlaufeinstellungen eines Auslastungstests wird eine Vielzahl anderer Einstellungen festgelegt, einschließlich der Dauer des Tests, der Detailstufe der Ergebniserfassung und der während des Testlaufs erfassten Indikatorensätze. Sie können für jeden Auslastungstest mehrere Testlaufeinstellungen erstellen und speichern. Anschließend können Sie eine bestimmte Einstellung auswählen, die beim Ausführen des Tests verwendet werden soll. Eine Ausgangseinstellung für Testläufe wird beim Erstellen des Auslastungstests mit dem **neuen Auslastungstest-Assistenten** zum Auslastungstest hinzugefügt.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

In den folgenden Tabellen werden die verschiedenen Eigenschaften für Auslastungstestlaufeinstellungen beschrieben. Sie können diese Eigenschaften ändern, um bestimmte Auslastungstestanforderungen zu erfüllen.

Weitere Informationen finden Sie unter [Konfigurieren der Laufzeiteinstellungen für Auslastungstests](../test/configure-load-test-run-settings.md).

## <a name="general-properties"></a>Allgemeine Eigenschaften

|Eigenschaft|Definition|
|-|----------------|
|**Beschreibung**|Eine Beschreibung der Testlaufeinstellungen|
|**Maximale Anzahl von Fehlern pro Typ**|Die maximale Anzahl von Fehlern pro Typ, die für den Auslastungstest gespeichert werden sollen.<br /><br /> Sie können diese Zahl bei Bedarf erhöhen, gleichzeitig erhöht sich dadurch aber auch die Größe und Verarbeitungszeit für das Auslastungstestergebnis.|
|**Maximal im Bericht gemeldete Anforderungs-URLs**|Die maximale Anzahl eindeutiger Anforderungs-URLs für Webleistungstests, für die Ergebnisse in diesem Auslastungstest angezeigt werden.<br /><br /> Sie können diese Zahl bei Bedarf erhöhen, gleichzeitig erhöht sich dadurch aber auch die Größe und Verarbeitungszeit für das Auslastungstestergebnis.|
|**Maximale Anzahl von Schwellenwertverletzungen**|Die maximale Anzahl von Schwellenwertverletzungen, die für diesen Auslastungstest gespeichert werden sollen.<br /><br /> Sie können diese Zahl bei Bedarf erhöhen, gleichzeitig erhöht sich dadurch aber auch die Größe und Verarbeitungszeit für das Auslastungstestergebnis.|
|**Komponententests in Anwendungsdomäne ausführen**|Ein boolescher Wert, durch den bestimmt wird, ob die einzelnen Komponententestassemblys in einer separaten Anwendungsdomäne ausgeführt werden, wenn der Auslastungstest Komponententests enthält. Die Standardeinstellung lautet True.<br /><br /> Wenn für die Komponententests keine separate Anwendungsdomäne oder app.config-Datei für die ordnungsgemäße Funktionsweise benötigt wird, werden die Komponententests durch Festlegen dieser Eigenschaft auf `False` eventuell schneller ausgeführt.|
|**Name**|Der Name der Laufzeiteinstellung, wie er im Knoten **Laufzeiteinstellungen** des **Auslastungstest-Editors** angezeigt wird.|
|**Validierungsebene**|Hiermit wird die höchste Validierungsregelstufe definiert, die in einem Auslastungstest ausgeführt wird. Validierungsregeln sind Webleistungstest-Anforderungen zugeordnet. Jede Validierungsregel besitzt eine zugeordnete Validierungsebene: **Hoch**, **Mittel** oder **Niedrig**. Diese Einstellung für den Auslastungstestlauf gibt an, welche Validierungsregeln bei Ausführung des Webleistungstests innerhalb des Auslastungstests ausgeführt werden. Wenn diese Testlaufeinstellung beispielsweise auf **Mittel** festgelegt ist, werden alle Validierungsregeln ausgeführt, die als **Mittel** oder **Niedrig** markiert sind.|

## <a name="logging-properties"></a>Protokolleigenschaften

|Eigenschaft|Definition|
|-|----------------|
|**Maximale Testprotokolle**|Gibt die maximale Anzahl von Testprotokollen an, die für den Auslastungstest gespeichert werden sollen. Wenn der für die maximale Anzahl von Testprotokollen eingegebene Wert erreicht wird, wird das Sammeln von Protokollen durch den Auslastungstest beendet. Daher werden die Protokolle am Anfang des Tests gesammelt, und nicht am Ende. Der Auslastungstest wird weiterhin ausgeführt, bis er abgeschlossen ist.|
|**Protokollhäufigkeit für abgeschlossene Tests speichern**|Gibt die Häufigkeit an, mit der das Testprotokoll geschrieben wird. Die Zahl gibt an, dass von jeder eingegebenen Anzahl von Tests jeweils ein Test im Testprotokoll gespeichert wird. Durch Eingabe des Werts zehn wird z. B. angegeben, dass der zehnte, zwanzigste und dreißigste Test in das Testprotokoll geschrieben wird. Wenn Sie den Wert auf "0" festlegen, werden keine Testprotokolle gespeichert.|
|**Protokoll bei Testfehler speichern**|Ein boolescher Wert, der bestimmt, ob Testprotokolle gespeichert werden, wenn ein Test in einem Auslastungstest fehlschlägt. Der Standardwert ist `True`.<br /><br /> Weitere Informationen finden Sie unter [Vorgehensweise: Angeben, ob Testfehler in Testprotokollen gespeichert werden](../test/how-to-specify-if-test-failures-are-saved-to-test-logs.md)|

Weitere Informationen finden Sie unter [Ändern von Einstellungen für die Auslastungstestprotokollierung](../test/modify-load-test-logging-settings.md).

## <a name="results-properties"></a>Ergebniseigenschaften

|Eigenschaft|Definition|
|-|----------------|
|**Speichertyp**|Die Art der Speicherung von Leistungsindikatoren, die in einem Auslastungstest abgerufen werden. Die folgenden Optionen sind verfügbar:<br /><br /> -   **Datenbank:** Erfordert eine SQL-Datenbank mit einem **Auslastungstest-Ergebnisspeicher**.<br />-   **Keine**.|
|**Speicher für Details der zeitlichen Steuerung**|Hiermit wird festgelegt, welche Details im **Auslastungstest-Ergebnisspeicher** gespeichert werden. Es stehen drei Werte zur Verfügung:<br /><br /> -   **AllIndividualDetails:** Einzelne zeitliche Steuerungswerte werden für alle Tests, Transaktionen und Seiten, die während des Auslastungstests ausgeführt bzw. ausgegeben wurden, im **Auslastungstest-Ergebnisspeicher** erfasst und gespeichert. Dieser Wert ist erforderlich, wenn Sie beabsichtigen, das **Diagramm für Aktivitäten virtueller Benutzer** im **Auslastungstest-Analyzer** zu verwenden.<br />     Weitere Informationen finden Sie unter [Analysieren der Aktivität virtueller Benutzer in der Detailansicht](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).<br />-   **Keine:** Es werden keine einzelnen zeitlichen Steuerungswerte erfasst. Dies ist der Standardwert für Visual Studio 2013 Update 4 und höhere Versionen.<br />-   **StatisticsOnly:** Statt der einzelnen zeitlichen Steuerungswerte für alle Tests, Transaktionen und Seiten, die während des Auslastungstests ausgeführt bzw. ausgegeben wurden, werden im **Auslastungstest-Ergebnisspeicher** nur Statistiken erfasst und gespeichert.<br /><br /> Weitere Informationen finden Sie unter [Gewusst wie: Angeben der Eigenschaft „Speicher für Details der zeitlichen Steuerung“](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md).|

## <a name="sql-tracing-properties"></a>Eigenschaften der SQL-Ablaufverfolgung

|Eigenschaft|Definition|
|-|----------------|
|**Mindestdauer von SQL-Vorgängen, für die Ablaufverfolgung durchgeführt wird**|Notwendige Mindestdauer eines SQL-Vorgangs in Millisekunden, damit dieser von der SQL-Ablaufverfolgung aufgezeichnet wird. Wenn Sie z. B. nach SQL-Vorgängen suchen, die unter Belastung langsam durchgeführt werden, ermöglicht Ihnen diese Einstellung das Ignorieren von schnell ablaufenden Vorgängen.|
|**Verbindungszeichenfolge für SQL-Ablaufverfolgung**|Die Verbindungszeichenfolge für den Zugriff auf die Datenbank, für die eine SQL-Ablaufverfolgung durchgeführt werden soll.|
|**SQL-Ablaufverfolgungsverzeichnis**|Der Speicherort, an dem die SQL-Ablaufverfolgungsdatei nach Abschluss der Aufzeichnung gespeichert wird. Dieses Verzeichnis muss über Schreibberechtigungen für SQL Server und Leseberechtigungen für den Controller verfügen.|
|**SQL-Ablaufverfolgung aktiviert**|Hiermit wird die Ablaufverfolgung von SQL-Vorgängen aktiviert. Der Standardwert ist `False`.|

## <a name="test-iterations-properties"></a>Eigenschaften von Testiterationen

|Eigenschaft|Definition|
|-|----------------|
|**Testiterationen**|Gibt die Gesamtzahl einzelner Tests an, die vor dem Abschließen des Auslastungstests ausgeführt werden müssen. Diese Eigenschaft ist nur gültig, wenn die Eigenschaft "Testiterationen verwenden" den Wert `True` hat.|
|**Testiterationen verwenden**|Wenn "Testiterationen verwenden" den Wert `True` aufweist, wird der Auslastungstest so lange ausgeführt, bis die Anzahl der innerhalb des Auslastungstests durchgeführten einzelnen Tests den in der Eigenschaft "Testiterationen" angegebenen Wert erreicht. In diesem Fall werden die zeitbasierten Einstellungen Aufwärmdauer, Testlaufdauer und Abkühldauer ignoriert. Wenn "Testiterationen verwenden" den Wert `False` hat, werden alle Zeitsteuerungseinstellungen angewendet und "Testiterationen" ignoriert.|

Weitere Informationen finden Sie unter [Vorgehensweise: Angeben der Anzahl von Testiterationen in einer Testlaufeinstellung für Auslastungstests](../test/how-to-specify-the-number-of-test-iterations-in-a-load-test.md).

## <a name="timing-properties"></a>Zeitsteuerungseigenschaften

|Eigenschaft|Definition|
|-|----------------|
|**Abkühldauer**|Die Abkühldauer für den Test im Format hh:mm:ss. Einzelne innerhalb eines Auslastungstests ausgeführte Tests sind nach Ende des Auslastungstests möglicherweise noch aktiv. Diese Tests können noch während der Abkühldauer weiter ausgeführt werden, bis sie abgeschlossen sind oder das Ende der Abkühldauer erreicht wurde. Standardmäßig wird keine Abkühldauer eingestellt. Die einzelnen Tests werden beendet, sobald der Auslastungstest auf der Grundlage der Einstellung für die Testlaufdauer beendet wird.|
|**Testlaufdauer**|Die Dauer des Tests, im Format hh:mm:ss.|
|**Samplingrate**|Der Intervall zum Erfassen von Leistungsindikatorwerten, im Format hh:mm:ss.<br /><br /> Weitere Informationen finden Sie unter [Vorgehensweise: Angeben der Abtastrate](../test/how-to-specify-the-sample-rate-for-a-load-test.md).|
|**Aufwärmdauer**|Die Zeitspanne zwischen dem Beginn des Tests und dem Beginn der Aufzeichnung von Beispieldaten, im Format hh:mm:ss. Diese Einstellung wird häufig verwendet, um stufenweise virtuelle Benutzer zu laden, damit eine bestimmte Auslastung erreicht wird, bevor die Aufzeichnung der Samplingwerte beginnt. Die in der Aufwärmzeitspanne aufgezeichneten Beispielwerte werden im **Auslastungstest-Analyzer** angezeigt.|

## <a name="webtest-connections-properties"></a>WebTest-Verbindungseigenschaften

|Eigenschaft|Definition|
|-|----------------|
|**WebTest-Verbindungsmodell**|Dadurch wird die Verwendung von Verbindungen vom Auslastungstest-Agent zum Webserver für Webleistungstests gesteuert, die innerhalb eines Auslastungstests ausgeführt werden. Es sind drei Webleistungstest-Verbindungsmodelle verfügbar:<br /><br /> – Das Modell **Verbindungen pro Benutzer** simuliert das Verhalten eines Benutzers, der einen realen Browser verwendet. Wenn Internet Explorer 6 oder Internet Explorer 7 simuliert wird, verwendet jeder virtuelle Benutzer, der einen Webleistungstest ausführt, eine oder zwei dedizierte Verbindungen mit dem Webserver. Die erste Verbindung wird hergestellt, wenn im Webleistungstest die erste Anforderung ausgegeben wird. Eine zweite Verbindung wird möglicherweise verwendet, wenn eine Seite mehrere abhängige Anforderungen enthält. Diese Anforderungen werden mithilfe der beiden Verbindungen parallel ausgegeben. Diese Verbindungen werden für nachfolgende Anforderungen im Webleistungstest erneut verwendet. Die Verbindungen werden nach Beendigung des Webleistungstests getrennt. Ein Nachteil dieses Modells ist, dass die Anzahl von Verbindungen, die auf dem Agent-Computer geöffnet bleiben, sehr hoch sein kann (bis zum Zweifachen der Benutzerauslastung). Die Benutzerauslastung, die von einem einzelnen Auslastungstest-Agent gesteuert werden kann, wird daher durch die Ressourcen begrenzt, die zur Unterstützung dieser Verbindungen notwendig sind. Wenn Internet Explorer 8 simuliert wird, werden sechs gleichzeitige Verbindungen unterstützt.<br />– Beim Modell **Verbindungspool** werden die Ressourcen auf dem Auslastungstest-Agent geschont, indem Verbindungen zum Webserver von mehreren virtuellen Benutzern von Webleistungstests gemeinsam verwendet werden. Wenn die Benutzerauslastung die Größe des Verbindungspools übersteigt, werden Verbindungen für die Webleistungstests, die von verschiedenen virtuellen Benutzern ausgeführt werden, gemeinsam verwendet. Dies bedeutet, dass ein Webleistungstest möglicherweise mit dem Auslösen einer Anforderung warten muss, wenn die Verbindung von einem anderen Webleistungstest genutzt wird. Die durchschnittliche Wartezeit für das Senden von Anforderungen durch einen Webleistungstest wird vom Leistungsindikator für die durchschnittliche Verbindungswartezeit des Auslastungstests aufgezeichnet. Dieser Wert sollte weniger als die durchschnittliche Antwortzeit für eine Seite betragen. Ist dies nicht der Fall, ist die Größe des Verbindungspools wahrscheinlich zu klein.<br />– Beim Modell **Verbindung pro Testiteration** wird für jede Testiteration eine dedizierte Verbindung verwendet.|
|**WebTest-Verbindungspoolgröße**|Gibt die maximale Anzahl von Verbindungen zwischen dem Auslastungstest-Agent und dem Webserver an. Dies gilt nur für das Modell **Verbindungspool**.|

## <a name="change-run-setting-properties"></a>Ändern der Eigenschaften von Laufzeiteinstellungen

Sie können dem Auslastungstest weitere Testlaufeinstellungen mit anderen Eigenschafteneinstellungen hinzufügen, damit Sie den Auslastungstest unter anderen Bedingungen ausführen können. Sie können z. B. eine neue Testeinstellung hinzufügen und eine andere Samplingrate verwenden oder eine längere Ausführungsdauer angeben. Sie können nur jeweils eine Testlaufeinstellung verwenden und müssen diese als aktiv markieren. Ein Beispiel finden Sie unter [Vorgehensweise: Auswählen der aktiven Laufzeiteinstellung für einen Auslastungstest](../test/how-to-select-the-active-run-setting-for-a-load-test.md).

So ändern Sie Laufzeiteinstellungen:

1. Öffnen Sie einen Auslastungstest.

2. Erweitern Sie den Ordner **Laufzeiteinstellungen**.

3. Klicken Sie auf einen **Laufzeiteinstellungen**-Knoten.

4. Klicken Sie im Menü **Ansicht** auf **Eigenschaftenfenster**.

     Das **Eigenschaftenfenster** wird mit den Eigenschaften für die ausgewählte Laufzeiteinstellung angezeigt.

5. Verwenden Sie das **Eigenschaftenfenster**, um die Laufzeiteinstellungen zu ändern. Ändern Sie beispielsweise die Testlaufdauer in **00:05:00**, um den Test fünf Minuten lang auszuführen.

    > [!NOTE]
    > Eine vollständige Liste der Laufzeiteinstellungseigenschaften und deren Beschreibungen finden Sie unter [Eigenschaften von Laufzeiteinstellungen für Auslastungstests](../test/load-test-run-settings-properties.md).

6. Speichern Sie den Auslastungstest, wenn Sie das Ändern der Eigenschaften abgeschlossen haben. Klicken Sie im Menü **Datei** auf **Speichern**.

> [!NOTE]
> Zu den Testlaufeinstellungen gehören auch die Indikatorensatzzuordnungen. Weitere Informationen finden Sie unter [Festlegen von Indikatorensätzen und Schwellenwertregeln für Computer in einem Auslastungstest](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

## <a name="see-also"></a>Weitere Informationen

- [Konfigurieren der Laufzeiteinstellungen für Auslastungstests](../test/configure-load-test-run-settings.md)
