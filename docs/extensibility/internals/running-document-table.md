---
title: Ausführen der dokumententabelle | Microsoft-Dokumentation
description: Erfahren Sie, wie die Visual Studio-IDE die laufende Dokument Tabelle verwaltet, die alle geöffneten Dokumente im Arbeitsspeicher enthält.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- read locks
- running document table (RDT), IVsDocumentLockHolder interface
- running document table (RDT)
- running document table (RDT), edit locks
- document data objects, running document table
ms.assetid: bbec74f3-dd8e-48ad-99c1-2df503c15f5a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 863a9b1cdb68218539045c9154fc18d845495222
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902886"
---
# <a name="running-document-table"></a>Aktive Dokumenttabelle
Die IDE verwaltet die Liste aller gegenwärtig geöffneten Dokumente in einer internen Struktur, die als Running Document Table (RDT) bezeichnet wird. Diese Liste enthält alle geöffneten Dokumente im Speicher, unabhängig davon, ob diese Dokumente gerade bearbeitet werden. Bei einem Dokument handelt es sich um ein beliebiges Element, das gespeichert wird, einschließlich Dateien in einem Projekt oder in der Hauptprojekt Datei (z. b. eine vcxproj-Datei).

## <a name="elements-of-the-running-document-table"></a>Elemente der laufenden dokumententabelle
 Die Ausführung der dokumententabelle enthält die folgenden Einträge.

|Element|Beschreibung|
|-------------|-----------------|
|Dokumentmoniker|Eine Zeichenfolge, die das Dokument Datenobjekt eindeutig identifiziert. Dies wäre der absolute Dateipfad für ein Projekt System, das Dateien verwaltet (z. b. c:\myproject\meinedatei). Diese Zeichenfolge wird auch für Projekte verwendet, die in anderen speichern als Dateisystemen gespeichert werden, z. b. gespeicherte Prozeduren in einer-Datenbank. In diesem Fall kann das Projekt System eine eindeutige Zeichenfolge erfinden, die erkannt und ggf. analysiert werden kann, um zu bestimmen, wie das Dokument gespeichert werden soll.|
|Hierarchie Besitzer|Das Hierarchie Objekt, das das Dokument besitzt, wie von einer- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Schnittstelle dargestellt.|
|Element-ID|Element Bezeichner für ein bestimmtes Element in der Hierarchie. Dieser Wert ist für alle Dokumente in der Hierarchie, die das Dokument besitzt, eindeutig, aber dieser Wert ist nicht garantiert in verschiedenen Hierarchien eindeutig.|
|Dokument Datenobjekt|Dies ist mindestens ein `IUnknown`<br /><br /> -Objekts. Die IDE erfordert keine bestimmte Schnittstelle, die über die `IUnknown` Schnittstelle für das Dokument Datenobjekt eines benutzerdefinierten Editors hinausgeht. Bei einem Standard-Editor ist die Implementierung der-Schnittstelle des Editors jedoch <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> erforderlich, um Datei Persistenz-Aufrufe aus dem Projekt zu verarbeiten. Weitere Informationen finden Sie unter [Speichern eines Standard Dokuments](../../extensibility/internals/saving-a-standard-document.md).|
|Flags|Flags, die Steuern, ob das Dokument gespeichert wird, ob eine Lese-oder Bearbeitungs Sperre angewendet wird usw., können angegeben werden, wenn dem RDT Einträge hinzugefügt werden. Weitere Informationen finden Sie unter der <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>-Enumeration.|
|Sperrenanzahl bearbeiten|Anzahl der Bearbeitungs sperren. Eine Bearbeitungs Sperre gibt an, dass das Dokument in einem Editor zum Bearbeiten geöffnet ist. Wenn die Anzahl der Bearbeitungs Sperren auf NULL übergeht, wird der Benutzer aufgefordert, das Dokument zu speichern, wenn es geändert wurde. Wenn Sie z. b. jedes Mal, wenn Sie ein Dokument mit dem **neuen Fenster** Befehl in einem Editor öffnen, eine Bearbeitungs Sperre für dieses Dokument im RDT hinzugefügt wird. Damit eine Bearbeitungs Sperre festgelegt werden kann, muss das Dokument über eine Hierarchie-oder Element-ID verfügen.|
|Anzahl von Lese Sperren|Anzahl der Lese sperren. Eine Lesesperre gibt an, dass das Dokument durch einen Mechanismus gelesen wird, z. b. einen Assistenten. Eine Lesesperre enthält ein Dokument, das im RDT aktiv ist, und zeigt an, dass das Dokument nicht bearbeitet werden kann. Sie können auch dann eine Lesesperre festlegen, wenn das Dokument keine Hierarchie-oder Element-ID enthält. Diese Funktion ermöglicht es Ihnen, ein Dokument im Arbeitsspeicher zu öffnen und in den RDT einzugeben, ohne dass sich das Dokument in einer Hierarchie befindet. Diese Funktion wird nur selten verwendet.|
|Sperreninhaber|Eine Instanz einer <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> Schnittstelle. Der Sperr Inhaber wird durch Funktionen wie Assistenten implementiert, die Dokumente außerhalb eines Editors öffnen und bearbeiten. Ein Sperr Halter ermöglicht der Funktion, dem Dokument eine Bearbeitungs Sperre hinzuzufügen, um zu verhindern, dass das Dokument geschlossen wird, während es noch bearbeitet wird. Normalerweise werden Bearbeitungs Sperren nur von Dokument Fenstern (d. h. Editoren) hinzugefügt.|

 Jedem Eintrag im RDT ist eine eindeutige Hierarchie oder Element-ID zugeordnet, die im Allgemeinen einem Knoten im Projekt entspricht. Alle Dokumente, die zur Bearbeitung verfügbar sind, befinden sich in der Regel in einer Hierarchie In dem RDT vorgenommene Einträge steuern, welches Projekt bzw. – genauer – welche Hierarchie aktuell das Dokument Datenobjekt besitzt, das bearbeitet wird. Mithilfe der Informationen im RDT kann die IDE verhindern, dass Dokumente gleichzeitig von mehr als einem Projekt geöffnet werden.

 Außerdem steuert die Hierarchie die Persistenz von Daten und verwendet die Informationen in der RDT, um die Dialogfelder **Speichern** und **Speichern** unter zu aktualisieren. Wenn Benutzer ein Dokument ändern und dann den Befehl **Exit** aus dem Menü **Datei** auswählen, werden Sie von der IDE zum Dialogfeld **Änderungen speichern** aufgefordert, um alle Projekte und Projekt Elemente anzuzeigen, die zurzeit geändert werden. Dadurch können Benutzer auswählen, welche Dokumente gespeichert werden sollen. Die Liste der zu speichernden Dokumente (d. h. die Dokumente, die Änderungen aufweisen) werden aus dem RDT generiert. Alle Elemente, die beim Beenden der Anwendung im Dialogfeld " **Änderungen speichern** " angezeigt werden, sollten Datensätze im RDT enthalten. Der RDT koordiniert, welche Dokumente gespeichert werden und ob der Benutzer über einen Speichervorgang mit den Werten, die im Flags-Eintrag für jedes Dokument angegeben sind, aufgefordert wird. Weitere Informationen zu den RDT-Flags finden Sie unter der- <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> Enumeration.

## <a name="edit-locks-and-read-locks"></a>Sperren und Lesen von Sperren
 Sperren und Lese Sperren befinden sich im RDT. Das Dokument Fenster erhöht und Dekremente die Bearbeitungs Sperre. Wenn ein Benutzer also ein neues Dokument Fenster öffnet, wird die Anzahl der Bearbeitungs Sperren um 1 erhöht. Wenn die Anzahl der Bearbeitungs Sperren Null erreicht, wird die Hierarchie signalisiert, die Daten für das zugeordnete Dokument beizubehalten oder zu speichern. Die Hierarchie kann die Daten dann in beliebiger Weise persistent speichern, einschließlich der Speicherung als Datei oder als Element in einem Repository. Sie können die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.LockDocument%2A> Methode in der- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> Schnittstelle verwenden, um Bearbeitungs Sperren und Lese Sperren hinzuzufügen, und die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> Methode, um diese Sperren zu entfernen.

 Wenn das Dokument Fenster für einen Editor instanziiert wird, fügt der Fensterrahmen normalerweise automatisch eine Bearbeitungs Sperre für das Dokument in der RDT hinzu. Wenn Sie jedoch eine benutzerdefinierte Ansicht eines Dokuments erstellen, das kein Standarddokument Fenster verwendet (d. h., es implementiert nicht die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> Schnittstelle), müssen Sie eine eigene Bearbeitungs Sperre festlegen. Beispielsweise wird in einem Assistenten ein Dokument bearbeitet, ohne in einem Editor geöffnet zu werden. Damit Dokument Sperren von Assistenten und ähnlichen Entitäten geöffnet werden können, müssen diese Entitäten die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> Schnittstelle implementieren. Um Ihren Dokument Sperr Inhaber zu registrieren, müssen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> -Methode aufzurufen und Ihre- <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> Implementierung übergeben. Dadurch wird dem RDT der Inhaber der Dokument Sperre hinzugefügt. Ein anderes Szenario für die Implementierung eines Dokument Sperr Inhabers besteht darin, dass Sie ein Dokument über ein spezielles Tool Fenster öffnen. In diesem Fall ist es nicht möglich, dass das Tool Fenster das Dokument schließt. Wenn Sie sich jedoch als Inhaber der Dokument Sperre im RDT registrieren, kann die IDE Ihre Implementierung der-Methode aufzurufen, <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder.CloseDocumentHolder%2A> um das Dokument zu schließen.

## <a name="other-uses-of-the-running-document-table"></a>Andere Verwendungszwecke der laufenden dokumententabelle
 Andere Entitäten in der IDE verwenden den RDT zum Abrufen von Informationen über Dokumente. Beispielsweise verwendet der Quellcodeverwaltungs-Manager den RDT, um dem System mitzuteilen, dass ein Dokument im Editor erneut geladen werden soll, nachdem die neueste Version der Datei abgerufen wurde. Zu diesem Zweck sucht der Quellcodeverwaltungs-Manager nach den Dateien im RDT, um festzustellen, ob diese offen sind. Wenn dies der Fall ist, prüft der Quellcodeverwaltungs-Manager zunächst, ob die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> Methode die-Methode implementiert. Wenn das Projekt die-Methode nicht implementiert <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> , prüft der Quellcodeverwaltungs-Manager direkt, ob eine Implementierung der- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> Methode für das Dokument Datenobjekt erfolgt.

 Die IDE verwendet auch den RDT, um ein geöffnetes Dokument neu zu machen (in den Vordergrund zu stellen), wenn ein Benutzer dieses Dokument anfordert. Weitere Informationen finden Sie unter [Anzeigen von Dateien mit dem Befehl "Datei öffnen](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)". Führen Sie einen der folgenden Schritte aus, um zu bestimmen, ob eine Datei im RDT geöffnet ist.

- Fragt den dokumentmoniker ab (d. h. den vollständigen Dokument Pfad), um herauszufinden, ob das Element geöffnet ist.

- Verwenden Sie die Hierarchie-oder Element-ID, um das Projekt System nach dem vollständigen Dokument Pfad zu Fragen, und suchen Sie dann das Element im RDT.

## <a name="see-also"></a>Weitere Informationen
- [RDT_ReadLock-Verwendung](../../extensibility/internals/rdt-readlock-usage.md)
- [Persistenz und die aktive Dokumenttabelle](../../extensibility/internals/persistence-and-the-running-document-table.md)
