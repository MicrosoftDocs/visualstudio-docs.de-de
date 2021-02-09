---
title: 'Vorgehensweise: Öffnen von Standard-Editoren | Microsoft-Dokumentation'
description: Erfahren Sie, wie Sie die OpenItem-Methode mit einem Standard-Editor implementieren. Die IDE bestimmt einen Standard Editor für einen bestimmten Dateityp.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], opening
- projects [Visual Studio SDK], opening standard editors
ms.assetid: d5ce10f9-047a-4b74-aa1d-295128898b89
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 163d042ffb08a60d5673e64cf6bab94f7a2f1d63
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99850454"
---
# <a name="how-to-open-standard-editors"></a>Vorgehensweise: Öffnen von Standard-Editoren
Wenn Sie einen Standard-Editor öffnen, können Sie der IDE einen Standard Editor für einen bestimmten Dateityp festlegen, anstatt einen projektspezifischen Editor für die Datei anzugeben.

 Führen Sie das folgende Verfahren aus, um die-Methode zu implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> . Dadurch wird eine Projektdatei in einem Standard-Editor geöffnet.

## <a name="to-implement-the-openitem-method-with-a-standard-editor"></a>So implementieren Sie die OpenItem-Methode mit einem Standard-Editor

1. Ruft <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> ( `RDT_EditLock` ) auf, um zu bestimmen, ob die Dokument Datenobjekt Datei bereits geöffnet ist.

2. Wenn die Datei bereits geöffnet ist, können Sie die Datei durch Aufrufen der-Methode neu anordnen, indem Sie den <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> Wert `IDO_ActivateIfOpen` für den- `grfIDO` Parameter angeben.

     Wenn die Datei geöffnet ist und das Dokument einem anderen Projekt als dem aufrufenden Projekt gehört, empfängt das Projekt eine Warnung, dass der zu öffnende Editor von einem anderen Projekt aus ist. Das Datei Fenster wird dann angezeigt.

3. Wenn das Dokument nicht geöffnet ist oder nicht in der ausgelaufenden dokumententabelle enthalten ist, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> müssen Sie die-Methode ( `OSE_ChooseBestStdEditor` ) zum Öffnen eines Standard-Editors für die Datei aufzurufen.

     Wenn Sie die-Methode aufzurufen, führt die IDE die folgenden Aufgaben aus:

    1. Die IDE scannt den Unterschlüssel Editoren/{guideditortype}/Extensions in der Registrierung, um zu bestimmen, welcher Editor die Datei öffnen kann und die höchste Priorität hat.

    2. Nachdem die IDE ermittelt hat, welcher Editor die Datei öffnen kann, ruft die IDE auf <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> . Die Implementierung dieser Methode durch den Editor gibt Informationen zurück, die erforderlich sind, damit die IDE aufruft <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> und das neu geöffnete Dokument aufruft.

    3. Zum Schluss lädt die IDE das Dokument mithilfe der üblichen persistenzschnittstelle, z <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> . b..

    4. Wenn die IDE bereits festgestellt hat, dass die Hierarchie oder das Hierarchie Element verfügbar ist, ruft die IDE die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> Methode für das Projekt auf, um einen Kontext Zeiger auf Projektebene abzurufen, <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> der mit dem-Methodenaufruf zurückgegeben werden soll <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> .

4. Gibt einen <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> Zeiger auf die IDE zurück, wenn die IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> für Ihr Projekt aufruft, wenn Sie möchten, dass der Editor Kontext aus dem Projekt abruft.

     Wenn Sie diesen Schritt ausführen, kann das Projekt dem Editor weitere Dienste anbieten.

     Wenn die Dokument Ansicht oder das Dokument Ansichts Objekt erfolgreich in einem Fensterrahmen positioniert wurde, wird das Objekt mit seinen Daten initialisiert, indem aufgerufen wird <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.LoadDocData%2A> .

## <a name="see-also"></a>Weitere Informationen
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [Öffnen und Speichern von Projekt Elementen](../extensibility/internals/opening-and-saving-project-items.md)
- [Gewusst wie: Öffnen von projektspezifischen Editoren](../extensibility/how-to-open-project-specific-editors.md)
- [Gewusst wie: Öffnen von Editoren für geöffnete Dokumente](../extensibility/how-to-open-editors-for-open-documents.md)
- [Anzeigen von Dateien mit dem Befehl "Datei öffnen"](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)
