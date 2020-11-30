---
title: Anzeigen von Dateien mit dem Befehl "Öffnen mit" | Microsoft-Dokumentation
description: Erfahren Sie, wie ein Projekt den Befehl Öffnen mit in der integrierten Entwicklungsumgebung (IDE) von Visual Studio aufrufen kann, um Dateien anzuzeigen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open With command
- Open With command
- persistence, supporting Open With command
ms.assetid: 53794bc3-1b73-4d40-954e-cfade1abddcf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f2cb6bd44148d470cac68addc09db9e9207e9d70
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2020
ms.locfileid: "96329691"
---
# <a name="display-files-by-using-the-open-with-command"></a>Anzeigen von Dateien mit dem Befehl "Öffnen mit"
Ein Projekt kann die IDE bitten, das Dialogfeld **Öffnen mit** anzuzeigen. Diese Anforderung fordert den Benutzer auf, eine Datei zu öffnen, die über eine Auswahl von Standard-Editoren verfügt. Dieser Prozess wird in den folgenden Schritten beschrieben:

1. Das Projekt ruft <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> auf und gibt den Wert `OSE_UseOpenWithDialog` für den- `OSEOpenDocEditor` Parameter an.

2. Basierend auf der Dateinamenerweiterung des Dokuments bestimmt die IDE, welche Editoren in der Registrierung das angegebene Dokument öffnen können. diese Informationen werden im Dialogfeld **Öffnen mit** angezeigt.

    > [!NOTE]
    > Projekte mit einem intrinsischen Editor, der in das Dialogfeld **Öffnen mit** eingeschlossen werden muss, müssen für jeden Editor eine Editorfactory registrieren. Intrinsische Editoren funktionieren nur in Verbindung mit einem bestimmten Projekttyp, der in der Implementierung der-Methode erzwungen wird <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> . Die IDE verfügt über eine integrierte Editorfactory für den Core-Text-Editor und den Binär-Editor. Die IDE erstellt außerdem eine Instanz einer Editorfactory im Namen jeder registrierten Windows-Datei Zuordnung. Ein Beispiel für eine solche Datei ist Microsoft Word.

3. Sobald der Benutzer im Dialogfeld **Öffnen mit** ein Element auswählt, öffnet die IDE das Dokument durch Aufrufen der- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> Methode. Weitere Informationen finden Sie unter Gewusst [wie: Öffnen von Standard-Editoren](../../extensibility/how-to-open-standard-editors.md).

## <a name="see-also"></a>Siehe auch
- [Öffnen und Speichern von Projekt Elementen](../../extensibility/internals/opening-and-saving-project-items.md)
- [Anzeigen von Dateien mit dem Befehl "Datei öffnen"](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)
- [Vorgehensweise: Öffnen von Standard-Editoren](../../extensibility/how-to-open-standard-editors.md)
