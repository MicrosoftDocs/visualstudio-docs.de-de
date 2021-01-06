---
title: 'Test Bereich 5: Ändern der Quell Code Verwaltung | Microsoft-Dokumentation'
description: Dieser Testbereich des Quell Code Verwaltungs-Plug-ins deckt das Ändern der Quell Code Verwaltung mithilfe des Befehls "Quell Code Verwaltung ändern" ab.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], changing
- source control plug-ins, changing source control
ms.assetid: fdf09e00-108c-4d51-bbd5-72452d52a490
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3c4b0f33f0c898d4b9992acad6ed4035e350df2b
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97876271"
---
# <a name="test-area-5-change-source-control"></a>Testbereich 5: Ändern der Quellcodeverwaltung
Dieser Testbereich des Quell Code Verwaltungs-Plug-ins deckt das Ändern der Quell Code Verwaltung über den Befehl Quell Code Verwaltung **ändern** ab.

 Der Befehl "Quell Code Verwaltung **ändern** " bietet vier grundlegende Funktionen für den Benutzer:

- **Zwick**

   Ermöglicht es einem Benutzer, einen Quell Code Verwaltungs Link zwischen einer Projekt Mappe/einem Projekt und dem Versionsspeicher einzurichten oder wiederherzustellen.

- **Bindung**

   Entfernt ein Projekt/eine Projekt Mappe aus der Quell Code Verwaltung pro Verbindung.

- **Verbindung herstellen/trennen:**

  Schaltet den Status "verbunden" oder "Offline" der kontrollierten Lösung um, die in Bereich 3 abgedeckt wird. Weitere Informationen finden Sie unter [Test Bereich 3: Auschecken/rückgängig machen](../../extensibility/internals/test-area-3-check-out-undo-checkout.md).

## <a name="command-menu-access"></a>Befehlsmenü Zugriff
 Der folgende [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierte Entwicklungs Umgebungs Menü Pfad wird in den Testfällen verwendet.

 Quell Code Verwaltung ändern:**Datei**, **Quell** Code Verwaltung, Quell Code Verwaltung **ändern**.

## <a name="test-cases"></a>Testfälle
 Im folgenden werden bestimmte Testfälle für den Testbereich zum **Ändern des Quell** Code Verwaltungs Befehls angezeigt.

### <a name="case-5a-bind"></a>Fall 5a: Bind
 BIND ermöglicht dem Benutzer das Hinzufügen von Quellcode-Steuerungsinformationen zu den ausgewählten Projekten und Projektmappen. Der Benutzer wird in der Regel aufgefordert, ein Projekt in der Quell Code Verwaltung zu identifizieren, dem diese hinzugefügt werden sollen. Der Benutzer kann im Rahmen dieses Vorgangs kein neues Projekt in der Quell Code Verwaltung erstellen (im Gegensatz zur Quell Code Verwaltung hinzufügen).

| Aktion | Test Schritte | Erwartete Ergebnisse zur Überprüfung |
| - | - | - |
| An leeren Speicherort binden | 1. Erstellen Sie ein Projekt.<br />2. Fügen Sie die Projekt Mappe der Quell Code Verwaltung hinzu.<br />3. Öffnen Sie das Dialogfeld "Quell Code Verwaltung **ändern** " (**Datei**, **Quell** Code Verwaltung, Quell Code Verwaltung **ändern**).<br />4. Klicken Sie auf **Bindung** aufheben.<br />5. Dialogfeld "Warnung akzeptieren", wenn es angezeigt wird.<br />6. Wählen Sie alle Elemente aus.<br />7. Klicken Sie auf **binden**.<br />8. Navigieren Sie zu einem leeren Speicherort in einem Quell Code Verwaltungs Speicher.<br />9. Klicken Sie auf **OK** , um das Dialogfeld Quell Code Verwaltung **ändern** zu schließen.<br />10. Klicken Sie im Bestätigungs Dialogfeld **mit diesen Bindungen auf Fortfahren** .<br />11. Klicken Sie im Dialogfeld Warnung auf **OK** , wenn es angezeigt wird.<br />12. checken Sie alles ein. Wenn dieser Schritt erfolgreich ist, fahren Sie mit dem nächsten Schritt fort.<br />13. Öffnen Sie die Projekt Mappe aus der Quell Code Verwaltung an einem neuen Speicherort. | `Result from Step 12:`<br /><br /> Die Projekt Mappe und das Projekt sind an das neue Ziel im Versionsspeicher gebunden und geschrieben.<br /><br /> Projektmappen-und Projektdateien werden eingeglichen.<br /><br /> Versionsspeicher-Projekt Hierarchie entspricht der Ordnerhierarchie des Projekts auf dem Datenträger.<br /><br /> `Result from Step 13:`<br /><br /> Alle Projekt Elemente werden heruntergeladen. |
| An Speicherort binden, der mit dem Client synchronisiert ist | 1. Erstellen Sie ein Projekt.<br />2. Fügen Sie die Projekt Mappe der Quell Code Verwaltung hinzu.<br />3. Erstellen Sie ein Duplikat der Projekt Mappe und des Projekts im Versionsspeicher (Freigabe und Verzweigung bei Verwendung von [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] ).<br />4. Öffnen Sie das Dialogfeld "Quell Code Verwaltung **ändern** " (**Datei**, **Quell** Code Verwaltung, Quell Code Verwaltung **ändern**).<br />5. Aufheben der Bindung für alle.<br />6. Klicken Sie auf **OK** , um das Dialogfeld Quell Code Verwaltung **ändern** zu schließen.<br />7. Öffnen Sie das Dialogfeld **Quell** Code Verwaltung erneut.<br />8. Wählen Sie alle aus.<br />9. Klicken Sie auf **binden**.<br />10. Navigieren Sie zum verzweigten Speicherort der Projekt Mappe und des Projekts (aus Schritt 3).<br />11. Klicken Sie auf **OK** , um das Dialogfeld Quell Code Verwaltung **ändern** zu schließen.<br />12. aktuelle rekursiv für alle Elemente erhalten. | Dateiinhalt nach dem Get-Wert ist der gleiche wie vor dem Get-Wert. |
| An Speicherort binden, der nicht mit dem Client synchronisiert ist | 1. Erstellen Sie ein Projekt.<br />2. Fügen Sie die Projekt Mappe der Quell Code Verwaltung hinzu.<br />3. Erstellen Sie ein Duplikat der Projekt Mappe und des Projekts im Versionsspeicher (Freigabe und Verzweigung bei Verwendung von [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] ).<br />4. ändern Sie die Dateien im verzweigten Projekt im Versionsspeicher.<br />5. Öffnen Sie das Dialogfeld "Quell Code Verwaltung **ändern** " (**Datei**, **Quell** Code Verwaltung, Quell Code Verwaltung **ändern**).<br />6. Aufheben der Bindung für alle.<br />7. Klicken Sie auf **OK** , um das Dialogfeld Quell Code Verwaltung **ändern** zu schließen.<br />8. Dialogfeld "Quell Code Verwaltung **ändern** " erneut öffnen.<br />9. Wählen Sie alle aus.<br />10. Klicken Sie auf **binden**.<br />11. Navigieren Sie zu verzweigter Position für Projekt Mappe und Projekt.<br />12. Klicken Sie auf **OK** , um das Dialogfeld Quell Code Verwaltung **ändern** zu schließen.<br />13. Dialogfeld "Warnung akzeptieren", wenn es angezeigt wird.<br />14. aktuelle rekursive für alle Elemente erhalten. | Dateien, die in Schritt 4 geändert wurden, werden ebenfalls lokal geändert. |
| Projekt Mappe binden, die nie unter Quell Code Verwaltung war | 1. Erstellen Sie einen leeren Ordner in der Quell Code Verwaltung.<br />2. Erstellen Sie ein Client Projekt.<br />3. Öffnen Sie das Dialogfeld "Quell Code Verwaltung **ändern** " (**Datei**, **Quell** Code Verwaltung, Quell Code Verwaltung **ändern**).<br />4. binden Sie die Projekt Mappe an eine leere Position in der Quell Code Verwaltung.<br />5. Klicken Sie auf **OK** , um das Dialogfeld Quell Code Verwaltung **ändern** zu schließen.<br />6. Klicken Sie im Bestätigungs Dialogfeld **mit diesen Bindungen auf Fortfahren** .<br />7. Klicken Sie im Dialogfeld Warnung auf **OK** , wenn es angezeigt wird. | Die Projekt Mappe wird der Quell Code Verwaltung hinzugefügt.<br /><br /> Projekt Mappe und Projekt sind ausgecheckt. |
| Bindung Abbrechen | 1. Erstellen Sie ein Projekt.<br />2. Fügen Sie die Projekt Mappe der Quell Code Verwaltung hinzu.<br />3. Öffnen Sie das Dialogfeld Quell Code Verwaltung ändern.<br />4. Aufheben der Bindung für alle.<br />5. Klicken Sie auf " **OK** ", um das Dialogfeld zu schließen. Wenn dieser Schritt erfolgreich ist, fahren Sie mit dem nächsten Schritt fort.<br />6. Öffnen Sie das Dialogfeld Quell Code Verwaltung **ändern** erneut.<br />7. Binden an nicht verknüpften Speicherort.<br />8. Klicken Sie auf **Abbrechen**. | `Result from Step 5:`<br /><br /> Die Lösung befindet sich nicht mehr unter Quell Code Verwaltung.<br /><br /> `Result from Step 8:`<br /><br /> Die Lösung befindet sich noch nicht in der Quell Code Verwaltung. |

### <a name="case-5b-unbind"></a>Fall 5b: Aufheben der Bindung
 Bindung aufheben entfernt Quell Code Verwaltungsinformationen aus Projekten und ihrer Projekt Mappe. Die betroffenen Projekte und Lösungen basieren auf einer Mischung aus Benutzer Auswahl und der Art und Weise, wie die Elemente der Quell Code Verwaltung hinzugefügt wurden.

|Aktion|Test Schritte|Erwartete Ergebnisse zur Überprüfung|
|------------|----------------|--------------------------------|
|Aufheben der Bindung einer Projekt Mappe mit einem Datei System oder einem lokalen IIS-Webprojekt und einem Client Projekt|1. Erstellen Sie ein Datei System oder ein lokales IIS-Webprojekt.<br />2. Fügen Sie die Projekt Mappe der Quell Code Verwaltung hinzu.<br />3. Fügen Sie der Projekt Mappe ein neues Client Projekt hinzu.<br />4. Wenn Sie dazu aufgefordert werden, sollten Sie die Lösung Auschecken.<br />5. Öffnen Sie das Dialogfeld Quell Code Verwaltung **ändern** .<br />6. Klicken Sie auf **Bindung** aufheben.<br />7. Klicken Sie auf **OK** , um das Dialogfeld zu schließen.<br />8. versuchen Sie, Projektmappen, Projekte, Projektmappenelemente und Projekt Elemente auszuchecken.|Projektmappen und Projekte befinden sich nicht in der Quell Code Verwaltung.<br /><br /> Menübefehle der Quell Code Verwaltung werden nicht angezeigt.|
|Aufheben der Bindung Abbrechen|1. Erstellen Sie ein Projekt.<br />2. Fügen Sie die Projekt Mappe der Quell Code Verwaltung hinzu.<br />3. Öffnen Sie das Dialogfeld Quell Code Verwaltung **ändern** .<br />4. Klicken Sie auf **Bindung für alle** aufheben.<br />5. Klicken Sie auf **Abbrechen**.|Die Projekt Mappe befindet sich unter Quell Code Verwaltung.|

### <a name="case-5c-rebind"></a>Fall 5c: Neu binden
 Die erneute Bindung ist einfach eine Kombination aus Bindung und Bindung – der Prozess der erneuten Bindung eines Projekts oder einer Projekt Mappe, das zuvor unter Quell Code Verwaltung war und dessen Bindung aufgehoben wurde.

|Aktion|Test Schritte|Erwartete Ergebnisse zur Überprüfung|
|------------|----------------|--------------------------------|
|Neubinden von Projektmappen und Projekten, ohne das Dialogfeld Quell Code Verwaltung **ändern** zu schließen|1. Erstellen Sie ein Projekt.<br />2. Fügen Sie die Projekt Mappe der Quell Code Verwaltung hinzu.<br />3. Öffnen Sie das Dialogfeld Quell Code Verwaltung **ändern** .<br />4. Klicken Sie auf **Bindung** aufheben.<br />5. Wählen Sie alle Zeilen aus.<br />6. Klicken Sie auf **binden**.<br />7. Klicken Sie auf **OK** , um das Dialogfeld Quell Code Verwaltung **ändern** zu schließen.<br />8. Wenn Sie dazu aufgefordert werden, übernehmen zu lassen|Projekt Mappe und Projekt befinden sich unter Quell Code Verwaltung.|
|Projekt nur dann erneut binden, wenn Dialogfeld "Quell Code Verwaltung **ändern** "|1. Erstellen Sie ein Projekt.<br />2. Fügen Sie der Quell Code Verwaltung nur das Projekt hinzu, indem Sie (Datei >Quell Code Verwaltung >ausgewählte Projekte zur Quell Code Verwaltung hinzufügen.<br />3. Öffnen Sie das Dialogfeld Quell Code Verwaltung ändern.<br />4. heben Sie die Bindung nur für das Projekt auf.<br />5. binden Sie nur das Projekt.|Die Lösung bleibt unverändert.<br /><br /> Das Projekt bleibt gesteuert.|
|Projekt Mappe nur dann erneut binden, wenn Dialogfeld "Quell Code Verwaltung **ändern** "|1. Erstellen Sie ein Projekt.<br />2. Fügen Sie der Quell Code Verwaltung mithilfe von (**Datei**, **Quell** Code Verwaltung, **Hinzufügen ausgewählter Projekte zur Quell** Code Verwaltung) nur die Projekt Mappe hinzu.<br />3. Öffnen Sie das Dialogfeld Quell Code Verwaltung **ändern** .<br />4. heben Sie die Bindung nur für die Projekt Mappe auf (Dialogfeld "Quell Code Verwaltung **ändern** " nicht.)<br />5. binden Sie nur die Projekt Mappe.<br />6. Klicken Sie auf **OK** , um das Dialogfeld zu schließen.<br />7. sehen Sie sich die Lösungs-und Projektmappenelemente (sofern vorhanden) an.|Die Lösung wird weiterhin gesteuert.<br /><br /> Das Projekt bleibt unkontrolliert.|
|Projekt Mappe/Projekt nur dann erneut binden, wenn dasselbe Verzeichnis|1. Erstellen Sie ein Projekt.<br />2. Fügen Sie der Quell Code Verwaltung mithilfe von (**Datei**, **Quell** Code Verwaltung, **Hinzufügen ausgewählter Projekte zur Quell** Code Verwaltung) nur das Projekt hinzu.<br />3. Schließen Sie die Projekt Mappe.<br />4. Erstellen Sie eine neue Projekt Mappe mit mindestens zwei Projekten.<br />5. Fügen Sie die Projekt Mappe der Quell Code Verwaltung hinzu.<br />6. Fügen Sie das in Schritt 1 erstellte Projekt aus der Quell Code Verwaltung hinzu.<br />7. akzeptieren Sie das Auschecken der Lösung, wenn Sie dazu aufgefordert werden<br />8. Überprüfen Sie die gesamte Projekt Mappe.<br />9. Öffnen Sie das Dialogfeld Quell Code Verwaltung **ändern** .<br />10. Wählen Sie das hinzugefügte Projekt (aus Schritt 6) aus, und klicken Sie auf **Bindung** aufheben.<br />11. Klicken Sie auf **OK** , um das Dialogfeld zu schließen.<br />12. übernehmen Sie die Kasse, wenn Sie dazu aufgefordert<br />13. Dialogfeld "Quell Code Verwaltung **ändern** " erneut öffnen.<br />14. Wählen Sie das hinzugefügte Projekt (aus Schritt 6) aus, und klicken Sie auf **binden**.<br />15. Wählen Sie den ursprünglichen Speicherort aus.|Projektmappen und Projekte bleiben weiterhin gesteuert.|

## <a name="see-also"></a>Weitere Informationen
- [Testleitfaden für Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
