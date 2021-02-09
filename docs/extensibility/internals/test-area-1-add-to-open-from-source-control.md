---
title: 'Test Bereich 1: Hinzufügen von To-Open aus der Quell Code Verwaltung | Microsoft-Dokumentation'
description: Dieser Testbereich der Quell Code Verwaltung umfasst das Platzieren von Projektmappen oder Projekten in der Quell Code Verwaltung und das Abrufen von Projektmappen aus der Quell Code Verwaltung.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], adding and opening solutions
- source control plug-ins, adding and opening solutions
ms.assetid: 5b3b5b08-5e9b-41be-ac72-c63957faed22
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dbcbc197a610f7caf2a1641a291db18fcea9dbda
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99898326"
---
# <a name="test-area-1-add-toopen-from-source-control"></a>Testbereich 1: Hinzufügen/Öffnen über die Quellcodeverwaltung
Dieser Testbereich der Quell Code Verwaltung umfasst das Platzieren von Projektmappen oder Projekten in der Quell Code Verwaltung und das Abrufen von Projektmappen aus der Quell Code Verwaltung.

## <a name="command-menu-access"></a>Befehlsmenü Zugriff
 Die folgenden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierten Menü Pfade der Entwicklungsumgebung werden in den Testfällen verwendet:

- [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]Öffnen Sie unter Quell Code Verwaltung: **Datei**, **Öffnen**, **Projekt** Mappe, und suchen Sie nach / dem [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] Speicherort.

- Öffnen Sie für andere Quellcodeverwaltungs-Plug-ins aus der Quell Code Verwaltung: **Datei**, **Quell** Code Verwaltung, **aus Quell** Code Verwaltung öffnen.

- Zur Quell Code Verwaltung hinzufügen: **Datei**, **Quell** Code Verwaltung, Projekt **Mappe zur Quell Code Verwaltung hinzufügen**, **Quell** Code Verwaltung, **Ausgewählte Projekte zur Quell Code Verwaltung hinzufügen**.

- Kontextmenü (Projekt/Projekt Mappe), Projekt Mappe **zur Quell Code Verwaltung hinzufügen**.

- Aus Quell Code Verwaltung hinzufügen: **Datei**, **Quell** Code Verwaltung, **Projekt aus Quell Code Verwaltung hinzufügen**.

- Für [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] ist auch hinzufügen aus Quell Code Verwaltung über **Datei**, **Hinzufügen**, **vorhandenes Projekt** verfügbar. Suchen Sie nach dem [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] Speicherort.

  > [!NOTE]
  > Der Pfad einer lokalen Datei oder eines lokalen IIS-Servers (Webserver) kann in diesem Test verwendet werden.

## <a name="expected-behavior"></a>Erwartetes Verhalten

- Für jeden unterstützten Projekttyp sollte ein Benutzer in der Lage sein, die Quell Code Verwaltung "hinzufügen" und "aus" zu öffnen.

- Wenn ein Projekt zur Quell Code Verwaltung hinzugefügt wird, \<*ProjectName*> wird eine entsprechende vspscc-Datei (Projekt Hinweis Datei) erstellt. Sie enthält die Liste der Ausschluss Dateien und Verbindungsinformationen. Löschen Sie diese Datei nicht, da Sie Informationen enthält, die für das projektspezifisch sind.

- Wenn eine Projekt Mappe zur Quell Code Verwaltung hinzugefügt wird, wird eine entsprechende \<*SolutionName*> vssscc-Datei (Triple S) erstellt. Die Textdatei enthält die Verbindungsinformationen und eine Ausschluss Datei Liste, ähnlich der Projekt Hinweis Datei. Diese Datei ist temporär und nur in der Quellcode-Verwaltungs Datenbank vorhanden.

- Wenn eine Projekt Mappe aus der Quell Code Verwaltung geöffnet wird, \<*SolutionName*> wird eine vsscc (Double S)-Datei, die nur in der Quellcode-Verwaltungs Datenbank vorhanden ist, lokal in einer temporären Datei erstellt. Diese Datei enthält den Pfad aus dem projektmappenverbindungs-Ordner zur Projektmappendatei. Diese Datei ist temporär, und die lokale Kopie wird gelöscht, wenn der Vorgang "aus Quell Code Verwaltung öffnen" abgeschlossen wurde.

- Nachdem ein Projekt zur Quell Code Verwaltung hinzugefügt wurde, können Sie sämtliche Quell Code Verwaltungs Aktionen ausführen (Auschecken, Get usw.).

## <a name="test-cases"></a>Testfälle
 Im folgenden werden bestimmte Testfälle für den Testbereich zum Hinzufügen zu/öffnen aus der Quell Code Verwaltung angezeigt.

### <a name="case-1a-add-solution-to-source-control"></a>Fall 1a: Hinzufügen der Projektmappe zur Quellcodeverwaltung
 Dieser Testfall konzentriert sich auf das Hinzufügen von Lösungen zur Quell Code Verwaltung.

|Aktion|Test Schritte|Erwartete Ergebnisse zur Überprüfung|
|------------|----------------|--------------------------------|
|Projekt Mappe mit einem Client Projekt zur Quell Code Verwaltung hinzufügen|1. Erstellen Sie ein Client Projekt.<br />2. Fügen Sie die Projekt Mappe zur Quell Code Verwaltung hinzu (**Datei**, **Quell** Code Verwaltung, Projekt Mappe zur Quell Code Verwaltung **Hinzufügen**).|Projekt Mappe/Projekt wurde der Quell Code Verwaltung hinzugefügt.|
|Projekt Mappe mit einem Datei System oder einem lokalen IIS-Webprojekt zur Quell Code Verwaltung hinzufügen|1. Erstellen Sie ein Datei System oder ein lokales IIS-Webprojekt (verwenden Sie die Schaltfläche Durchsuchen, um auf den Speicherort des Projekts zu zeigen. der Pfad bestimmt, welcher Typ von Webprojekt erstellt wird).<br />2. Fügen Sie die Projekt Mappe zur Quell Code Verwaltung hinzu (**Datei**, **Quell** Code Verwaltung, Projekt Mappe zur Quell Code Verwaltung **Hinzufügen**).|Projekt Mappe/Projekt wurde der Quell Code Verwaltung hinzugefügt.|
|Projekt Mappe mit einem Remote-Website-Webprojekt zur Quell Code Verwaltung hinzufügen|1. Erstellen Sie ein Remote Website-Webprojekt.<br />2. Fügen Sie die Projekt Mappe zur Quell Code Verwaltung hinzu (**Datei**, **Quell** Code Verwaltung, Projekt Mappe zur Quell Code Verwaltung **Hinzufügen**).<br />3. Klicken Sie im Dialogfeld FrontPage-Zugriffs Warnung auf **OK** .|Die Projekt Mappe wurde der Quell Code Verwaltung hinzugefügt.<br /><br /> Das Remote Standortprojekt befindet sich nicht in der Quell Code Verwaltung. (Remote Standort Projekte müssen von einem eigenen IIS-Server gesteuert werden.)|
|Fügen Sie der Quell Code Verwaltung eine einzelne Projekt Mappe hinzu, indem **Sie ausgewählte Projekte zur Quell Code Verwaltung hinzufügen**.|1. Erstellen Sie eine einzelne Projekt Mappe.<br />2. Fügen Sie der Quell Code Verwaltung nur eine Projekt Mappe als Auswahl hinzu (**Datei**, **Quell** Code Verwaltung, **Ausgewählte Projekte zur Quell Code Verwaltung hinzufügen**). Wenn dieser Schritt erfolgreich ist, fahren Sie mit dem nächsten Schritt fort.<br />3. Fügen Sie der Quell Code Verwaltung ein Projekt als Auswahl hinzu (**Datei**, **Quell** Code Verwaltung, der Quell Code Verwaltung **Ausgewählte Projekte hinzufügen**).<br />4. Klicken Sie auf " **Ja** ", um das Projekt dem gleichen Speicherort hinzuzufügen.<br />5. Klicken Sie auf **Auschecken** im Dialogfeld **zum Bearbeiten** Auschecken.|`Result from Step 2:`<br /><br /> Das Projekt und alle Dateien im Projekt verfügen über einen ausgecheckten Quell Code Verwaltungs Indikator, und in einer QuickInfo wird "nicht unter Quell Code Verwaltung" angezeigt.<br /><br /> `Result from Step 5:`<br /><br /> Die Projekt-und Projektmappendatei befinden sich im selben Ordner in der Quell Code Verwaltung.|
|Hinzufügen einer Projekt Mappe zur Quell Code Verwaltung Abbrechen|1. Erstellen Sie eine einzelne Projekt Mappe.<br />2. versuchen Sie, der Quell Code Verwaltung ein Projekt und eine Projekt Mappe hinzuzufügen. Wenn dieser Schritt erfolgreich ist, fahren Sie mit dem nächsten Schritt fort.<br />3. Abbrechen, nachdem Sie sich im Quell Code Verwaltungssystem befinden.|`Result from Step 2:`<br /><br /> Das Dialogfeld Quell Code Verwaltung für Projekt Speicherort festlegen wird nur einmal angezeigt.<br /><br /> `Result from Step 3:`<br /><br /> Das Hinzufügen des Projekts wurde abgebrochen, das Projekt/die Projekt Mappe befindet sich nicht unter Quell Code Verwaltung, und alle Menüs zur Quell Code Verwaltung|

### <a name="case-1b-open-solution-from-source-control"></a>Fall 1B. Projekt Mappe aus Quell Code Verwaltung öffnen
 Dieser Testfall konzentriert sich auf das Öffnen von Lösungen aus der Quell Code Verwaltung.

|Aktion|Test Schritte|Erwartete Ergebnisse zur Überprüfung|
|------------|----------------|--------------------------------|
|Öffnen einer Projekt Mappe, die ein Client Projekt aus der Quell Code Verwaltung enthält|1. Erstellen Sie ein Client Projekt.<br />2. Fügen Sie die Projekt Mappe der Quell Code Verwaltung hinzu.<br />3. Schließen Sie die Projekt Mappe.<br />4. Öffnen Sie die Projekt Mappe aus der Quell Code Verwaltung an einem neuen Speicherort.|Projekt Mappe/Projekt in der Quell Code Verwaltung geöffnet.|
|Öffnen einer Projekt Mappe, die ein lokales oder IIS-Webprojekt aus der Quell Code Verwaltung enthält|1. Erstellen Sie ein lokales oder IIS-Webprojekt.<br />2. Fügen Sie die Projekt Mappe der Quell Code Verwaltung hinzu.<br />3. Schließen Sie die Projekt Mappe.<br />4. Öffnen Sie die Projekt Mappe aus der Quell Code Verwaltung an einem neuen Speicherort.|Projekt Mappe/Projekt in der Quell Code Verwaltung geöffnet.|
|Öffnen einer Projekt Mappe, die ein Remoteweb Projekt aus der Quell Code Verwaltung enthält|1. Erstellen Sie ein Remote Website-Webprojekt.<br />2. Fügen Sie die Projekt Mappe der Quell Code Verwaltung hinzu. Wenn dieser Schritt erfolgreich ist, fahren Sie mit dem nächsten Schritt fort.<br />3. Schließen Sie die Projekt Mappe.<br />4. Öffnen Sie die Projekt Mappe aus der Quell Code Verwaltung an einem neuen Speicherort.|`Result from Step 2:`<br /><br /> Das Web für Remote Websites befindet sich nicht unter Quell Code Verwaltung.<br /><br /> `Result from Step 4:`<br /><br /> Die Lösung wurde über die Quell Code Verwaltung geöffnet.<br /><br /> Das Remote Standortprojekt wird geladen, aber es befindet sich nicht unter Quell Code Verwaltung.|

### <a name="case-1c-add-solution-from-source-control"></a>Fall 1c: Hinzufügen der Projektmappe aus der Quellcodeverwaltung
 Bei diesem Testfall werden Lösungen aus der Quell Code Verwaltung hinzugefügt.

|Aktion|Test Schritte|Erwartete Ergebnisse zur Überprüfung|
|------------|----------------|--------------------------------|
|Zu leerer Projekt Mappe hinzufügen – eine einzelne Projekt Mappe|1. Erstellen Sie eine einzelne Projekt Mappe.<br />2. Fügen Sie die Projekt Mappe der Quell Code Verwaltung hinzu.<br />3. Schließen Sie die Projekt Mappe.<br />4. Erstellen Sie eine zweite leere Projekt Mappe.<br />5. Fügen Sie die zuvor gesteuerte Projekt Mappe aus der Quell Code Verwaltung hinzu (**Datei**, **Quell** Code Verwaltung, **Projekt aus Quell Code Verwaltung hinzufügen**).|Das hinzugefügte Projekt wird in **Projektmappen-Explorer** angezeigt und ist eingeglichen.|
|Zur Projekt Mappe mit einem einzelnen Projekt hinzufügen – einzelnes Projekt|1. Erstellen Sie eine Projekt Mappe mit einem einzelnen Projekt.<br />2. Fügen Sie die Projekt Mappe der Quell Code Verwaltung hinzu.<br />3. Schließen Sie die Projekt Mappe.<br />4. Erstellen Sie eine zweite leere Projekt Mappe.<br />5. Fügen Sie die zuvor gesteuerte Projekt Mappe aus der Quell Code Verwaltung hinzu (**Datei**, **Quell** Code Verwaltung, **Projekt aus Quell Code Verwaltung hinzufügen**).|Das hinzugefügte Projekt wird in **Projektmappen-Explorer** angezeigt und ist eingeglichen.|
|Zu Projekt Mappe hinzufügen – Projekt Mappe durch Auswahl zur Quell Code Verwaltung hinzugefügt|1. Erstellen Sie eine Projekt Mappe mit einem Projekt.<br />2. Fügen Sie der Quell Code Verwaltung nur eine Projekt Mappe als Auswahl hinzu. Wenn dieser Schritt erfolgreich ist, fahren Sie mit dem nächsten Schritt fort.<br />3. Schließen Sie die Projekt Mappe.<br />4. Erstellen Sie eine neue Projekt Mappe.<br />5. Fügen Sie die zuvor gesteuerte Projekt Mappe aus der Quell Code Verwaltung hinzu (**Datei**, **Quell** Code Verwaltung, **Projekt aus Quell Code Verwaltung hinzufügen**).|`Result from Step 2:`<br /><br /> Das Projekt befindet sich nicht in der Quell Code Verwaltung.<br /><br /> `Result from Step 5:`<br /><br /> Wenn die erste Projekt Mappe Projektmappenelemente enthielt, können Sie nicht aus der Quell Code Verwaltung hinzugefügt werden, sodass Sie nicht angezeigt werden.<br /><br /> Das Projekt aus der ersten Projekt Mappe erscheint als nicht verfügbar.|

## <a name="see-also"></a>Weitere Informationen
- [Testleitfaden für Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
