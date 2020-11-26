---
title: Richtlinien für die Quell Code Verwaltung für Projekte und Editoren
description: Erfahren Sie mehr über die Richtlinien, die Projekte und Editoren einhalten sollten, um die Quell Code Verwaltung zu unterstützen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], guidelines for projects and editors
ms.assetid: 2483cce5-321c-4d3c-9c5c-ee8385263f74
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fdd7e23840701981eaea46b44355c34b55b37a33
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2020
ms.locfileid: "96190134"
---
# <a name="additional-source-control-guidelines-for-projects-and-editors"></a>Weitere Richtlinien zur Quell Code Verwaltung für Projekte und Editoren
Es gibt eine Reihe von Richtlinien, die von Projekten und Editoren befolgt werden sollten, um die Quell Code Verwaltung zu unterstützen.

## <a name="guidelines"></a>Richtlinien
 Das Projekt oder der Editor sollte auch folgende Aktionen ausführen, um die Quell Code Verwaltung zu unterstützen:

|Bereich|Project|Editor|Details|
|----------|-------------|------------|-------------|
|Private Kopien von Dateien|X||Die Umgebung unterstützt private Kopien von Dateien. Das heißt, jede Person, die sich im Projekt eingetragen hat, verfügt über eine eigene private Kopie der Dateien in diesem Projekt.|
|ANSI/Unicode-Persistenz|X|X|Wenn Sie den Persistenzcode schreiben, speichern Sie Dateien im ANSI-Format, da die meisten Programme der Quell Code Verwaltung Unicode derzeit nicht unterstützen.|
|Dateien aufzählen|X||Das Projekt muss eine bestimmte Liste aller Dateien darin enthalten, und es muss in der Lage sein, die Liste der Dateien mithilfe von <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> oder <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (VSH_PROPID_First_Child/Next_Sibling) aufzuzählen. Das Projekt sollte außerdem Elementnamen über seine Implementierung verfügbar machen <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetMkDocument%2A> und Namenssuche (einschließlich spezieller Dateien) über seine Implementierung unterstützen <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A> .|
|Textformat|X|X|Wenn möglich, sollten Dateien im Textformat vorliegen, um die Zusammenführung unterschiedlicher Versionen zu unterstützen. Dateien, die nicht im Textformat vorliegen, können später nicht mit anderen Versionen der Datei zusammengeführt werden. Das bevorzugte Textformat ist XML.|
|Verweis basiert|X||Verweis basierte Projekte werden in der Quell Code Verwaltung problemlos unterstützt. Verzeichnis basierte Projekte werden jedoch auch von der Quell Code Verwaltung unterstützt, solange das Projekt bei Bedarf eine Liste der zugehörigen Dateien erstellt, unabhängig davon, ob diese Dateien auf dem Datenträger vorhanden sind. Wenn Sie ein Projekt aus der Quell Code Verwaltung öffnen, wird die Projektdatei zuerst vor einer Ihrer Dateien heruntergefahren.|
|Beibehalten von Objekten und Eigenschaften in vorhersag barer Reihenfolge|X|X|Speichern Sie die Dateien in einer vorhersagbaren Reihenfolge, z. b. in alphabetischer Reihenfolge|
|Erneut laden|X|X|Wenn sich eine Datei auf dem Datenträger ändert, muss Sie in der Lage sein, Sie erneut zu laden. Wenn Sie an der Quell Code Verwaltung teilnehmen, lädt die Umgebung Daten für Sie neu, indem Sie Ihre- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> Implementierung aufrufen. Die schwierigste groß-und Kleinschreibung besteht darin, dass ein Auschecken auftritt, wenn Sie ivsqueryeditquerysave:: aufgerufen haben <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> und Verarbeitungs Informationen sind. Der Code zum erneuten Laden muss jedoch in dieser Situation ausgeführt werden können.<br /><br /> Die Umgebung lädt Projektdateien automatisch erneut. Ein Projekt muss jedoch implementieren, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> Wenn es über unterstützte Hierarchien verfügt, um das erneute Laden von masted-Projektdateien zu unterstützen.|

## <a name="see-also"></a>Weitere Informationen
- [Quell Code Verwaltung unterstützen](../../extensibility/internals/supporting-source-control.md)
