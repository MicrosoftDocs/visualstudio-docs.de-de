---
title: RDT_ReadLock Verwendung | Microsoft-Dokumentation
description: Erfahren Sie mehr über die _VSRDTFLAGS. RDT_ReadLock Flag, das Logik zum Sperren eines Dokuments in der laufenden dokumententabelle bereitstellt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- RDT_ReadLock
- visible
- RDT_EditLock
- invisible
ms.assetid: b935fc82-9d6b-4a8d-9b70-e9a5c5ad4a55
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2c946d69cf1aded072d27e7c6ccbdf28f1122571
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97875387"
---
# <a name="rdt_readlock-usage"></a>RDT_ReadLock-Verwendung

[_VSRDTFLAGS. RDT_ReadLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_ReadLock>) ist ein Flag, das Logik zum Sperren eines Dokuments in der laufenden dokumententabelle (RDT) bereitstellt. Dies ist die Liste aller Dokumente, die derzeit in der Visual Studio-IDE geöffnet sind. Dieses Flag bestimmt, wann Dokumente geöffnet werden und ob ein Dokument in der Benutzeroberfläche sichtbar ist oder unsichtbar im Arbeitsspeicher gehalten wird.

Im Allgemeinen verwenden Sie [_VSRDTFLAGS. RDT_ReadLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_ReadLock>) , wenn einer der folgenden Punkte zutrifft:

- Sie möchten ein Dokument unsichtbar und schreibgeschützt öffnen, aber es wurde noch nicht festgelegt und <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> muss es besitzen.

- Sie möchten, dass der Benutzer aufgefordert wird, ein Dokument zu speichern, das unsichtbar geöffnet war, bevor der Benutzer es in der Benutzeroberfläche angezeigt und dann versucht hat, es zu schließen.

## <a name="how-to-manage-visible-and-invisible-documents"></a>Verwalten von sichtbaren und unsichtbaren Dokumenten

Wenn ein Benutzer ein Dokument in der Benutzeroberfläche öffnet, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> muss ein Besitzer für das Dokument und ein _VSRDTFLAGS erstellt werden [. RDT_EditLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_EditLock>) Flag muss festgelegt werden. Wenn kein <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Besitzer eingerichtet werden kann, wird das Dokument nicht gespeichert, wenn der Benutzer auf **Alle speichern** klickt oder die IDE schließt. Dies bedeutet, dass ein Dokument nicht sichtbar ist, wo es im Arbeitsspeicher geändert wird, und der Benutzer aufgefordert wird, das Dokument beim Herunterfahren zu speichern oder zu speichern, wenn **Alles speichern** ausgewählt ist, `RDT_ReadLock` kann nicht verwendet werden. Stattdessen müssen Sie einen verwenden `RDT_EditLock` und einen registrieren, <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> Wenn ein [__VSREGDOCLOCKHOLDER. RDLH_WeakLockHolder](<xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER.RDLH_WeakLockHolder>) -Flag.

## <a name="rdt_editlock-and-document-modification"></a>RDT_EditLock und Dokument Änderung

Das vorherige angezeigte Flag gibt an, dass das unsichtbare Öffnen des Dokuments den Wert ergibt, `RDT_EditLock` Wenn das Dokument vom Benutzer in einem sichtbaren **DocumentWindow** geöffnet wird. In diesem Fall wird dem Benutzer eine **Save** -Eingabeaufforderung angezeigt, wenn das sichtbare **DocumentWindow** geschlossen wird. `Microsoft.VisualStudio.Package.Automation.OAProject.CodeModel` Implementierungen, die den <xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager> Dienst verwenden, funktionieren anfänglich, wenn nur ein ausgeführt `RDT_ReadLock` wird (d. h., wenn das Dokument unsichtbar geöffnet wird, um Informationen zu analysieren). Wenn das Dokument später geändert werden muss, wird die Sperre auf eine schwache **RDT_EditLock** aktualisiert. Wenn der Benutzer das Dokument dann in einem sichtbaren **DocumentWindow** öffnet, `CodeModel` wird die schwache- `RDT_EditLock` Version freigegeben.

Wenn der Benutzer dann das Dokument " **DocumentWindow** " schließt und " **Nein** " auswählt, wenn er zum Speichern des geöffneten Dokuments aufgefordert wird, `CodeModel` gibt die Implementierung alle Informationen im Dokument aus und öffnet das Dokument nicht sichtbar von der Festplatte, wenn das nächste Mal Weitere Informationen für das Dokument erforderlich sind. Die Feinheiten dieses Verhaltens ist eine Instanz, in der der Benutzer das **DocumentWindow-Fenster** des unsichtbar geöffneten Dokuments öffnet, es ändert, schließt und dann **Nein** auswählt, wenn Sie zum Speichern des Dokuments aufgefordert werden. Wenn in diesem Fall das Dokument über eine verfügt `RDT_ReadLock` , wird das Dokument nicht geschlossen, und das geänderte Dokument bleibt unsichtbar im Speicher geöffnet, auch wenn der Benutzer das Dokument nicht speichern wollte.

Wenn das unsichtbare Öffnen des Dokuments eine schwache verwendet `RDT_EditLock` , wird die Sperre erreicht, wenn der Benutzer das Dokument sichtbar öffnet und keine anderen Sperren aufrechterhalten werden. Wenn der Benutzer das **DocumentWindow** schließt und bei der Aufforderung zum Speichern des Dokuments **Nein** auswählt, muss das Dokument aus dem Arbeitsspeicher geschlossen werden. Dies bedeutet, dass der unsichtbare Client RDT-Ereignisse Abhören muss, um dieses Vorkommen zu verfolgen. Wenn das Dokument das nächste Mal benötigt wird, muss es erneut geöffnet werden.
