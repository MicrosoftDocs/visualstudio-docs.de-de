---
title: Speichern eines benutzerdefinierten Dokuments | Microsoft-Dokumentation
description: Erfahren Sie mehr über den Prozess, der für ein benutzerdefiniertes Dokument für einen Projekttyp auftritt, den Sie der Visual Studio-IDE hinzufügen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, saving custom documents
- projects [Visual Studio SDK], saving custom documents
- editors [Visual Studio SDK], saving custom documents
ms.assetid: 040b36d6-1f0a-4579-971c-40fbb46ade1d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d2d2aa249d6944e33ab9556000c483efdec78f20
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97875678"
---
# <a name="saving-a-custom-document"></a>Speichern eines benutzerdefinierten Dokuments
Die Umgebung verarbeitet die Befehle " **Speichern**", " **Speichern** unter" und " **Alle speichern** ". Wenn ein Benutzer auf " **Speichern**", " **Speichern** unter" **oder "Alles speichern** " im Menü "Datei" klickt oder die Projekt **Mappe** schließt, was zu "Alles speichern" führt, wird der folgende Vorgang ausgeführt.

 ![Speichern des Kunden-Editors](../../extensibility/internals/media/private.gif "Privat") Speichern, speichern unter und Speichern der gesamten Befehls Behandlung für einen benutzerdefinierten Editor

 Dieser Vorgang wird in den folgenden Schritten beschrieben:

1. Für die Befehle " **Speichern** " und " **Speichern** unter" verwendet die Umgebung den <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> Dienst, um das aktive Dokument Fenster zu bestimmen, und damit die Elemente, die gespeichert werden sollen. Sobald das aktive Dokument Fenster bekannt ist, findet die Umgebung den Hierarchie Zeiger und den Element Bezeichner (Itemid) für das Dokument in der aktiven Dokument Tabelle. Weitere Informationen finden Sie unter [Ausführen der Dokument Tabelle](../../extensibility/internals/running-document-table.md).

     Für den Befehl Alle speichern verwendet die Umgebung die Informationen in der laufenden dokumententabelle, um die Liste aller zu speichernden Elemente zu kompilieren.

2. Wenn die Lösung einen-Befehl empfängt <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> , durchläuft Sie den Satz ausgewählter Elemente (d. h. die Mehrfachauswahl, die vom Dienst verfügbar gemacht wird <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> ).

3. Bei jedem Element in der Auswahl verwendet die Projekt Mappe den Hierarchie Zeiger zum Abrufen der- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> Methode, um zu bestimmen, ob der Menübefehl speichern aktiviert werden soll. Wenn ein oder mehrere Elemente geändert werden, ist der Befehl speichern aktiviert. Wenn in der Hierarchie ein Standard-Editor verwendet wird, delegiert die Hierarchie die Abfrage des geänderten Status an den Editor, indem die-Methode aufgerufen wird <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> .

4. Bei jedem ausgewählten Element, das geändert wird, verwendet die Projekt Mappe den Hierarchie Zeiger, um die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> Methode für die entsprechenden Hierarchien aufzurufen.

     Im Fall eines benutzerdefinierten Editors ist die Kommunikation zwischen dem Dokument Datenobjekt und dem Projekt privat. Daher werden alle besonderen Persistenzprobleme zwischen diesen beiden Objekten behandelt.

    > [!NOTE]
    > Wenn Sie Ihre eigene Persistenz implementieren, achten Sie darauf, die-Methode aufzurufen, <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> um Zeit zu sparen. Mit dieser Methode wird überprüft, ob die Datei sicher gespeichert werden kann (z. b. wenn die Datei nicht schreibgeschützt ist).

## <a name="see-also"></a>Weitere Informationen
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Öffnen und Speichern von Projektelementen](../../extensibility/internals/opening-and-saving-project-items.md)
