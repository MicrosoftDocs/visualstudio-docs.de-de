---
title: Dokument Daten und Dokument Ansicht in benutzerdefinierten Editoren | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document data and document view
ms.assetid: 71eea623-f566-4feb-84cd-ca1ba71bc493
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6d4b14558a435d6ad9da32726508d81185961410
ms.sourcegitcommit: ba966327498a0f67d2df2291c60b62312f40d1d3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/06/2020
ms.locfileid: "93414463"
---
# <a name="document-data-and-document-view-in-custom-editors"></a>Dokument Daten und Dokument Ansicht in benutzerdefinierten Editoren
Ein benutzerdefinierter Editor besteht aus zwei Teilen: einem Dokument Datenobjekt und einem Dokument Ansichts Objekt. Wie der Name bereits vermuten lässt, stellt das Dokument Datenobjekt die anzuzeigenden Textdaten dar. Ebenso stellt das Dokument Ansichts Objekt (oder "View") ein oder mehrere Fenster dar, in denen das Dokument Datenobjekt angezeigt werden soll.

## <a name="document-data-object"></a>Dokument Datenobjekt
 Ein Dokument Datenobjekt ist eine Datendarstellung von Text im Text Puffer. Es handelt sich um ein COM-Objekt, in dem Dokument Text und andere Informationen gespeichert werden. Das Dokument Datenobjekt verarbeitet außerdem die Dokument Persistenz und ermöglicht mehrere Ansichten der Daten. Weitere Informationen finden Sie unter

 <xref:EnvDTE80.Window2.DocumentData%2A> und [Dokument Fenster](../extensibility/internals/document-windows.md).

 Benutzerdefinierte Editoren und Designer können sich dafür entscheiden, das <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> Objekt oder ihren eigenen benutzerdefinierten Puffer zu verwenden. <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> folgt dem vereinfachten Einbettungs Modell für einen Standard Editor, unterstützt mehrere Ansichten und stellt Ereignis Schnittstellen bereit, die zum Verwalten mehrerer Ansichten verwendet werden.

## <a name="document-view-object"></a>Dokument Ansichts Objekt
 Ein Fenster, in dem Code und anderer Text angezeigt werden, wird als Dokument Ansicht oder-Sicht bezeichnet. Wenn Sie einen Editor erstellen, können Sie entweder eine einzelne Ansicht auswählen, in der Text in einem einzelnen Fenster angezeigt wird. Oder Sie können eine mehrere Ansicht auswählen, in der Text in mehr als einem Fenster angezeigt wird. Ihre Auswahl hängt von Ihrer Anwendung ab. Wenn Sie z. b. eine Seite-an-Seite-Bearbeitung benötigen, wählen Sie mehrere anzeigen aus. Jede Ansicht ist einem Eintrag in der integrierten Entwicklungsumgebung (IDE), in der die Dokument Tabelle (RDT) ausgeführt wird, zugeordnet. Anzeige Fenster gehören zu einem Projekt oder einem <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Objekt.

 Wenn der Editor mehrere Ansichten eines Dokument Datenobjekts unterstützt, müssen die Dokument Daten und die Dokument Ansichts Objekte getrennt sein. Andernfalls können Sie gruppiert werden. Weitere Informationen finden Sie [unter Unterstützung mehrerer Dokument Ansichten](../extensibility/supporting-multiple-document-views.md).

 Die IDE benachrichtigt Sichten über Ereignisse (z. b., wenn eine Projekt Mappe, die ein Dokument enthält, geschlossen wird), indem ein Element Bezeichner (Itemid) für jeden Eintrag in der laufenden Dokument Tabelle abgeglichen wird. Weitere Informationen hierzu finden Sie unter [Ausführen der Dokument Tabelle](../extensibility/internals/running-document-table.md).

 Es gibt zwei Optionen zum Erstellen einer Ansicht für einen benutzerdefinierten Editor. Eine ist das direkte Aktivierungs Modell, bei dem die Ansicht in einem Fenster mit einem ActiveX-Steuerelement oder einem Dokument Datenobjekt gehostet wird. Das zweite ist das vereinfachte Einbettungs Modell, bei dem die Ansicht von gehostet wird [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> zum Verarbeiten von Fenster Befehlen implementiert wird. Weitere Informationen zum direkten Aktivierungs Modell finden Sie unter direkte [Aktivierung](/previous-versions/visualstudio/visual-studio-2015/misc/in-place-activation?preserve-view=true&view=vs-2015). Weitere Informationen über das vereinfachte Einbettungs Modell finden Sie unter [vereinfachte Einbettung](../extensibility/simplified-embedding.md).

## <a name="see-also"></a>Weitere Informationen

- [Unterstützung mehrerer Dokument Sichten](../extensibility/supporting-multiple-document-views.md)
- [Vereinfachte Einbettung](../extensibility/simplified-embedding.md)
- [Gewusst wie: Anfügen von Sichten an Dokument Daten](../extensibility/how-to-attach-views-to-document-data.md)
- [Dokument Sperr Inhaber-Verwaltung](../extensibility/document-lock-holder-management.md)
- [Ansichten für einzelne und mehrere Registerkarten](../extensibility/single-and-multi-tab-views.md)
- [Speichern eines Standard Dokuments](../extensibility/internals/saving-a-standard-document.md)
- [Persistenz und die laufende Dokument Tabelle](../extensibility/internals/persistence-and-the-running-document-table.md)
- [Bestimmen, welcher Editor eine Datei in einem Projekt öffnet](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)