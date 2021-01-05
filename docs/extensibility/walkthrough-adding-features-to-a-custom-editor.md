---
title: 'Exemplarische Vorgehensweise: Hinzufügen von Funktionen zu einem benutzerdefinierten Editor | Microsoft-Dokumentation'
description: In dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie einem benutzerdefinierten Editor weitere Funktionen hinzufügen, nachdem Sie den Editor erstellt haben.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], custom - add features
ms.assetid: bfe083b6-3e35-4b9c-ad4f-b30b9ff412a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c08af63eaf68701f1a6703ac41fec20368d78931
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2021
ms.locfileid: "97863206"
---
# <a name="walkthrough-add-features-to-a-custom-editor"></a>Exemplarische Vorgehensweise: Hinzufügen von Funktionen zu einem benutzerdefinierten Editor
Nachdem Sie einen benutzerdefinierten Editor erstellt haben, können Sie ihm weitere Funktionen hinzufügen.

## <a name="to-create-an-editor-for-a-vspackage"></a>So erstellen Sie einen Editor für ein VSPackage

1. Erstellen Sie mithilfe der Projektvorlage für Visual Studio-Pakete einen benutzerdefinierten Editor.

     Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Erstellen eines benutzerdefinierten Editors](../extensibility/walkthrough-creating-a-custom-editor.md).

2. Entscheiden Sie, ob Sie möchten, dass Ihr Editor eine einzelne Ansicht oder mehrere Ansichten unterstützt.

     Ein Editor, der den **neuen Fenster** Befehl oder die Formularansicht und die Code Ansicht unterstützt, erfordert separate Dokument Datenobjekte und Dokument Ansichts Objekte. In einem Editor, der nur eine einzelne Ansicht unterstützt, können das Dokument Datenobjekt und das Dokument Ansichts Objekt für dasselbe Objekt implementiert werden.

     Ein Beispiel für mehrere Ansichten finden Sie [unter Unterstützung mehrerer Dokument Sichten](../extensibility/supporting-multiple-document-views.md).

3. Implementieren Sie eine Editorfactory durch Einrichten der- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> Schnittstelle.

     Weitere Informationen finden Sie unter [](/previous-versions/visualstudio/visual-studio-2015/extensibility/editor-factories?preserve-view=true&view=vs-2015)editorfactorys.

4. Entscheiden Sie, ob Sie möchten, dass der Editor die direkte Aktivierung oder die vereinfachte Einbettung verwendet, um das Dokument Ansichts Objekt Fenster zu verwalten.

     Ein vereinfachtes Fenster zum Einbetten eines Editors hostet eine Standarddokument Ansicht, während ein direktes Aktivierungs-Editor-Fenster ein ActiveX-Steuerelement oder ein anderes aktives Objekt als Dokument Ansicht hostet. Weitere Informationen finden Sie unter [vereinfachte Einbettung](../extensibility/simplified-embedding.md) und direkte [Aktivierung](/previous-versions/visualstudio/visual-studio-2015/misc/in-place-activation?preserve-view=true&view=vs-2015).

5. Implementieren Sie die- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle zum Verarbeiten von Befehlen.

6. Dokument Persistenz und Antwort auf externe Dateiänderungen bereitstellen:

    1. Um die Datei beizubehalten, implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> Sie und für das Dokument Datenobjekt des Editors.

    2. Um auf Änderungen externer Dateien zu reagieren, <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx> implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> Sie und für das Dokument Datenobjekt des Editors.

        > [!NOTE]
        > Ruft `QueryService` auf <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx> , um einen Zeiger auf zu erhalten `IVsFileChangeEx` .

7. Koordinieren Sie Dokument Bearbeitungs Ereignisse mit der Quell Code Verwaltung. Führen Sie die folgenden Schritte aus:

    1. Rufen Sie einen Zeiger auf auf, `IVsQueryEditQuerySave2` indem Sie `QueryService` für aufrufen <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> .

    2. Wenn das erste Bearbeitungs Ereignis auftritt, wird die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> Methode aufgerufen.

         Diese Methode fordert den Benutzer auf, die Datei auszuchecken, wenn Sie nicht bereits ausgecheckt ist. Stellen Sie sicher, dass die Bedingung "Datei nicht ausgecheckt" behandelt wird, um Fehler zu verhindern.

    3. Auf ähnliche Weise können Sie vor dem Speichern der Datei die-Methode aufzurufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> .

         Diese Methode fordert den Benutzer auf, die Datei zu speichern, wenn Sie nicht gespeichert wurde, oder wenn Sie sich seit der letzten Speicherung geändert hat.

8. Aktivieren Sie das Fenster **Eigenschaften** , um Eigenschaften für Text anzuzeigen, der im Editor ausgewählt ist. Führen Sie die folgenden Schritte aus:

    1. <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A>Jedes Mal, wenn die Textauswahl geändert wird, wird die Implementierung von übergeben <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> .

    2. Rufen Sie `QueryService` für <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> den Dienst auf, um einen Zeiger auf zu erhalten <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> .

9. Ermöglicht Benutzern das ziehen und Ablegen von Elementen zwischen dem Editor und der **Toolbox** oder zwischen externen Editoren (z. b. Microsoft Word) und der **Toolbox**. Führen Sie die folgenden Schritte aus:

    1. Implementieren Sie `IDropTarget` im Editor, um die IDE zu warnen, dass der Editor ein Ablage Ziel ist.

    2. Implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> Sie die-Schnittstelle für die Sicht, damit der Editor Elemente in der **Toolbox** aktivieren und deaktivieren kann.

    3. Implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A> `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox> Sie, und rufen Sie für den-Dienst auf, um einen Zeiger auf die <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> Schnittstellen und

         Mit diesen Schritten kann Ihr VSPackage neue Elemente zur **Toolbox** hinzufügen.

10. Entscheiden Sie, ob Sie weitere optionale Features für den Editor benötigen.

    - Wenn Sie möchten, dass der Editor Befehle zum Suchen und ersetzen unterstützt, implementieren Sie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget> .

    - Wenn Sie ein Dokument Gliederungs Tool Fenster in Ihrem Editor verwenden möchten, implementieren Sie `IVsDocOutlineProvider` .

    - Wenn Sie eine Statusleiste im Editor verwenden möchten, implementieren Sie, <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> und fordern Sie `QueryService` für <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> an, um einen Zeiger auf zu erhalten `IVsStatusBar` .

         Beispielsweise kann ein Editor Zeilen-/Spalteninformationen, den Auswahlmodus (Stream/Box) und den Einfügemodus (INSERT/OVERSTRIKE) anzeigen.

    - Wenn Sie möchten, dass der Editor den-Befehl unterstützt `Undo` , wird empfohlen, das OLE-rückgängig-Manager-Modell zu verwenden. Als Alternative können Sie den-Editor direkt verarbeiten lassen `Undo` .

11. Erstellen Sie Registrierungsinformationen, einschließlich der GUIDs für das VSPackage, die Menüs, den Editor und andere Funktionen.

     Im folgenden finden Sie ein allgemeines Beispiel für Code, den Sie in das *RGS* -Datei Skript einfügen, um zu veranschaulichen, wie ein Editor ordnungsgemäß registriert wird.

    ```csharp
    NoRemove Editors
    {
          ForceRemove {...guidEditor...} = s 'RTF Editor'
          {
             val Package = s '{...guidVsPackage...}'
             ForceRemove Extensions
             {
                val rtf = d 50
             }
          }
    }
    NoRemove Menus
    {
          val {...guidVsPackage...} = s ',203,11'
    }
    ```

12. Implementieren der kontextbezogenen Hilfe Unterstützung.

     Dieser Schritt ermöglicht es Ihnen, F1-Hilfe und dynamische Hilfefenster Unterstützung für Elemente in Ihrem Editor bereitzustellen. Weitere Informationen finden Sie unter Gewusst [wie: Bereitstellen von Kontext für Editoren](/previous-versions/visualstudio/visual-studio-2015/extensibility/how-to-provide-context-for-editors?preserve-view=true&view=vs-2015).

13. Machen Sie durch Implementieren der-Schnittstelle ein Automatisierungs Objektmodell aus dem Editor verfügbar `IDispatch` .

     Weitere Informationen finden Sie unter [Contributing to the Automation Model](../extensibility/internals/contributing-to-the-automation-model.md).

## <a name="robust-programming"></a>Stabile Programmierung

- Die Editor-Instanz wird erstellt, wenn die IDE die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> Methode aufruft. Wenn der Editor mehrere Ansichten unterstützt, `CreateEditorInstance` erstellt sowohl die Dokument Daten als auch die Dokument Ansichts Objekte. Wenn das Dokument Datenobjekt bereits geöffnet ist, wird ein Wert ungleich NULL `punkDocDataExisting` an den Wert übermittelt `IVsEditorFactory::CreateEditorInstance` . Die Editorfactory-Implementierung muss bestimmen, ob ein vorhandenes Dokument Datenobjekt kompatibel ist, indem entsprechende Schnittstellen abgefragt werden. Weitere Informationen finden Sie [unter unterstützen mehrerer Dokument Ansichten](../extensibility/supporting-multiple-document-views.md).

- Wenn Sie den vereinfachten Einbettungs Ansatz verwenden, implementieren Sie die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> Schnittstelle.

- Wenn Sie die direkte Aktivierung verwenden möchten, implementieren Sie die folgenden Schnittstellen:

   <xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>

   <xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>

   <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>

  > [!NOTE]
  > Die- `IOleInPlaceComponent` Schnittstelle wird verwendet, um die Zusammenführung von OLE 2-Menüs

   Ihre `IOleCommandTarget` Implementierung verarbeitet Befehle wie **Ausschneiden**, **Kopieren** und **Einfügen**. Wenn `IOleCommandTarget` Sie implementieren, entscheiden Sie, ob Ihr Editor eine eigene *vsct* -Datei benötigt, um eine eigene Befehlsmenü Struktur zu definieren, oder ob Sie von definierte Standard Befehle implementieren kann [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . In der Regel verwenden Editoren die Menüs der IDE und definieren ihre eigenen Symbolleisten. Es ist jedoch häufig notwendig, dass ein Editor zusätzlich zur Verwendung des Standard Befehlssatzes der IDE seine eigenen spezifischen Befehle definiert. Der Editor muss die verwendeten Standard Befehle deklarieren und dann alle neuen Befehle, Kontextmenüs, Menüs der obersten Ebene und Symbolleisten in einer *vsct* -Datei definieren. Wenn Sie einen direkten Aktivierungs-Editor erstellen, implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> und definieren Sie die Menüs und Symbolleisten für den Editor in einer *vsct* -Datei anstelle der OLE 2-Menü Zusammenführung.

- Um die Überfüllung des Menübefehls in der Benutzeroberfläche zu verhindern, sollten Sie die vorhandenen Befehle in der IDE verwenden, bevor Sie neue Befehle erfinden. Freigegebene Befehle sind in " *sharedcmddef. vsct* " und " *shellcmddef. vsct*" definiert. Diese Dateien werden standardmäßig im Unterverzeichnis visualstudiointegration\common\inc der-Installation installiert [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] .

- `ISelectionContainer` kann sowohl eine einfache als auch eine Mehrfachauswahl Ausdrücken. Jedes ausgewählte Objekt wird als Objekt implementiert `IDispatch` .

- Die IDE implementiert `IOleUndoManager` als einen Dienst, der von einem <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> oder als Objekt zugänglich ist, das durch instanziiert werden kann <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> . Der Editor implementiert die- `IOleUndoUnit` Schnittstelle für jede `Undo` Aktion.

- Es gibt zwei Stellen, in denen ein benutzerdefinierter Editor Automatisierungs Objekte verfügbar machen kann:

  - `Document.Object`

  - `Window.Object`

## <a name="see-also"></a>Weitere Informationen

- [Zum Automatisierungs Modell beitragen](../extensibility/internals/contributing-to-the-automation-model.md)