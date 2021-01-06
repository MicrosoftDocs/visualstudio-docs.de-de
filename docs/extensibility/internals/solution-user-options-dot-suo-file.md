---
title: Projektmappenbenutzeroptionen (. SUO-Datei | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Projektmappenbenutzeroptionen (. suo), die benutzerspezifische Lösungs Optionen in einer strukturierten Speicherdatei enthalten, die in einem binären Format gespeichert ist.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .suo files, VSPackages
- suo files, VSPackages
- solutions, .suo files
- solutions, user options
- solution user options (.suo) file
ms.assetid: 75258e0d-600d-4a3d-94f4-3d7ac12cb47c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b2a5386e8329bb3ca51ca88a2449e223bb8d73d
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97876753"
---
# <a name="solution-user-options-suo-file"></a>Datei mit Benutzeroptionen in Projektmappen (SUO)
Die Benutzeroptionen für die Projekt Mappe (. suo) enthalten Optionen für benutzerspezifische Lösungen. Diese Datei sollte nicht in die Quell Code Verwaltung eingeklickt werden.

 Bei der Projektmappen-Benutzeroptionen Datei (. suo) handelt es sich um eine strukturierte Speicher-oder Verbund Datei, die in einem binären Format gespeichert ist. Sie speichern Benutzerinformationen in Streams mit dem Namen des Streams, der der Schlüssel ist, der zum Identifizieren der Informationen in der SUO-Datei verwendet wird. Die Benutzer Optionsdatei für die Projekt Mappe wird zum Speichern der Benutzer Einstellungs Einstellungen verwendet und automatisch erstellt, wenn Visual Studio eine Projekt Mappe speichert.

 Wenn die Umgebung eine SUO-Datei öffnet, listet Sie alle zurzeit geladenen VSPackages auf. Wenn ein VSPackage die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> Schnittstelle implementiert, ruft die Umgebung die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> Methode für das VSPackage auf, um alle Daten aus der SUO-Datei zu laden.

 Es liegt in der Verantwortung des VSPackages, zu wissen, welche Streams es möglicherweise in die SUO-Datei geschrieben hat. Für jeden Datenstrom, den er geschrieben hat, ruft das VSPackage über an die Umgebung zurück, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> um einen bestimmten Stream zu laden, der durch den Schlüssel identifiziert wird. Dies ist der Name des Streams. Die Umgebung ruft dann an das VSPackage zurück, um den jeweiligen Stream zu lesen und den Namen des Streams und einen `IStream` Zeiger auf die-Methode zu übergeben <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> .

 An diesem Punkt wird ein weiterer aufrufener aufgerufen, `LoadUserOptions` um zu überprüfen, ob ein anderer Abschnitt der SUO-Datei vorhanden ist, der gelesen werden muss. Dieser Prozess wird fortgesetzt, bis alle Datenströme in der SUO-Datei von der Umgebung gelesen und verarbeitet wurden.

 Wenn die Projekt Mappe gespeichert oder geschlossen wird, ruft die Umgebung die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A> Methode mit einem Zeiger auf die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A> Methode auf. Ein `IStream` , das die zu speichernden Binär Informationen enthält, wird an die-Methode weitergegeben <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A> , die die Informationen dann in die SUO-Datei schreibt und die-Methode erneut aufruft, um zu über `SaveUserOptions` prüfen, ob ein anderer Datenstrom in die SUO-Datei geschrieben werden kann.

 Diese beiden Methoden, `SaveUserOptions` und `WriteUserOptions` , werden rekursiv für jeden Datenstrom aufgerufen, der in der SUO-Datei gespeichert werden soll. dabei wird der-Zeiger an übergeben `IVsSolutionPersistence` . Sie werden rekursiv aufgerufen, um das Schreiben mehrerer Streams in die SUO-Datei zu ermöglichen. Auf diese Weise werden die Benutzerinformationen mit der Projekt Mappe beibehalten und sind beim nächsten Öffnen der Lösung garantiert.

## <a name="see-also"></a>Weitere Informationen
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- [Lösungen](../../extensibility/internals/solutions-overview.md)
