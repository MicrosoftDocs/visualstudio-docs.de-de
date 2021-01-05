---
title: Details zur Konfiguration der Quell Code Verwaltung | Microsoft-Dokumentation
description: Erfahren Sie mehr über das Implementieren der Quell Code Verwaltung für einen Projekttyp in Visual Studio. dazu gehört das Konfigurieren des Projekt Systems oder Editors, um Berechtigungen anzufordern.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], configuration details
ms.assetid: adbee9fc-7a2e-4abe-a3b8-e6615bcd797f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: efed4592bfa0b697d66f377430cc5998d3e9e5d3
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97875504"
---
# <a name="source-control-configuration-details"></a>Konfigurationsdetails für die Quellcodeverwaltung
Um die Quell Code Verwaltung zu implementieren, müssen Sie das Projekt System oder den Editor ordnungsgemäß für folgende Aufgaben konfigurieren:

- Anfordern der Berechtigung für den Übergang in den geänderten Zustand

- Anfordern der Berechtigung zum Speichern einer Datei

- Anfordern der Berechtigung zum Hinzufügen, entfernen oder Umbenennen von Dateien im Projekt

## <a name="request-permission-to-transition-to-changed-state"></a>Anfordern der Berechtigung für den Übergang in den geänderten Zustand
 Ein Projekt oder Editor muss die Berechtigung zum Übergang in den geänderten Zustand (geändert) anfordern, indem aufgerufen wird <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> . Jeder Editor, der implementiert, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A> muss aufruft <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> und empfängt eine Genehmigung, um das Dokument vor der Rückgabe für von der Umgebung zu ändern `True` <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A> . Bei einem Projekt handelt es sich im Wesentlichen um einen Editor für eine Projektdatei. Daher ist die gleiche Verantwortung für die Implementierung der Änderungs Zustandsüberwachung für die Projektdatei, wie ein Text-Editor für die Dateien. Die Umgebung verarbeitet den geänderten Zustand der Projekt Mappe, aber Sie müssen den geänderten Status aller Objekte, die die Projekt Mappe referenziert, aber nicht speichert, wie z. b. eine Projektdatei oder deren Elemente, verarbeiten. Wenn das Projekt oder der Editor für die Verwaltung der Persistenz eines Elements zuständig ist, ist es im Allgemeinen für die Implementierung der Änderungs Zustandsüberwachung verantwortlich.

 Als Antwort auf den-Befehl `IVsQueryEditQuerySave2::QueryEditFiles` kann die Umgebung folgende Aktionen ausführen:

- Ablehnen Sie den aufzurufenden Änderungs Wechsel. in diesem Fall muss der Editor oder das Projekt im unveränderten Zustand bleiben.

- Geben Sie an, dass die Dokument Daten neu geladen werden sollen. Bei einem Projekt lädt die Umgebung die Daten für das Projekt neu. Ein Editor muss die Daten vom Datenträger durch seine <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> Implementierung neu laden. In beiden Fällen kann sich der Kontext im Projekt oder im Editor ändern, wenn die Daten erneut geladen werden.

  Es ist eine komplexe und schwierige Aufgabe, die entsprechenden `IVsQueryEditQuerySave2::QueryEditFiles` Aufrufe auf eine vorhandene Codebasis zu über können. Daher sollten diese Aufrufe während der Erstellung des Projekts oder Editors integriert werden.

## <a name="request-permission-to-save-a-file"></a>Anfordern der Berechtigung zum Speichern einer Datei
 Bevor ein Projekt oder Editor eine Datei speichert, muss Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> oder aufruft <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> . Bei Projektdateien werden diese Aufrufe automatisch von der Projekt Mappe abgeschlossen, die weiß, wann eine Projektdatei gespeichert werden soll. Editoren sind für diese Aufrufe zuständig, es sei denn, die Editor Implementierung von `IVsPersistDocData2` verwendet die Hilfsfunktion <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A> . Wenn `IVsPersistDocData2` der Editor auf diese Weise implementiert, wird der-oder-Aufrufe `IVsQueryEditQuerySave2::QuerySaveFile` `IVsQueryEditQuerySave2::QuerySaveFiles` für Sie durchgeführt.

> [!NOTE]
> Nehmen Sie diese Aufrufe immer vorzeitig an – d. h., wenn der Editor in der Lage ist, einen Abbruch zu empfangen.

## <a name="request-permission-to-add-remove-or-rename-files-in-the-project"></a>Anfordern der Berechtigung zum Hinzufügen, entfernen oder Umbenennen von Dateien im Projekt
 Bevor ein Projekt eine Datei oder ein Verzeichnis hinzufügen, umbenennen oder entfernen kann, muss die entsprechende Methode aufgerufen werden, `IVsTrackProjectDocuments2::OnQuery*` um die Berechtigung aus der Umgebung anzufordern. Wenn die Berechtigung erteilt wird, muss das Projekt den Vorgang beenden und dann die entsprechende `IVsTrackProjectDocuments2::OnAfter*` Methode zum Benachrichtigen der Umgebung auffordern, dass der Vorgang beendet ist. Das Projekt muss die Methoden der <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> -Schnittstelle für alle Dateien (z. b. spezielle Dateien) und nicht nur für die übergeordneten Dateien aufzurufen. Datei Aufrufe sind obligatorisch, aber Verzeichnis Aufrufe sind optional. Wenn das Projekt über Verzeichnisinformationen verfügt, sollten die entsprechenden Methoden aufgerufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> werden. wenn diese Informationen jedoch nicht vorhanden sind, werden die Verzeichnisinformationen von der Umgebung abgeleitet.

 Das Projekt sollte die Methoden von `IVsTrackProjectDocuments2` beim Öffnen oder Schließen des Projekts nicht aufzurufen. Listener, die diese Informationen beim Start wünschen, können auf das <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> Ereignis warten und die Lösung durchlaufen, um die benötigten Informationen zu finden. Beim Herunterfahren sind diese Informationen nicht erforderlich. `IVsTrackProjectDocuments2` wird von bereitgestellt <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> .

 Für jede Aktion zum Hinzufügen, umbenennen und entfernen gibt es eine `OnQuery*` -Methode und eine- `OnAfter*` Methode. Ruft die- `OnQuery*` Methode auf, um die Berechtigung zum Hinzufügen, umbenennen oder Entfernen der Datei oder des Verzeichnisses anzufordern. Ruft die `OnAfter*` -Methode auf, nachdem die Datei oder das Verzeichnis hinzugefügt, umbenannt oder entfernt wurde und der Projektzustand den neuen Status wieder gibt.

## <a name="see-also"></a>Weitere Informationen

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>
- [Unterstützen der Quellcodeverwaltung](../../extensibility/internals/supporting-source-control.md)
