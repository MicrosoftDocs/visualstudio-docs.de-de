---
title: Modell für Quell Code Verwaltungs Pakete | Microsoft-Dokumentation
description: Dieses Modell stellt eine Implementierung der Quell Code Verwaltung dar. Der Artikel zeigt die Namen der Klassen, damit Sie leichter erkennen können, wie die Quell Code Verwaltung ausgeführt wird.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], model
ms.assetid: 6164b2d3-a622-4de8-bef3-a6de985e9ebd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 958465fc927464c46befb2422eb1286cda156916
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895660"
---
# <a name="model-for-source-control-packages"></a>Modell für Quellcodeverwaltungspakete
Das folgende Modell stellt ein Beispiel für eine Implementierung der Quell Code Verwaltung dar. Im Modell sehen Sie die Schnittstellen, die Sie implementieren müssen, und die Umgebungs Dienste, die Sie aufzurufen müssen. Wie alle Dienste auch, rufen Sie tatsächlich die Methoden einer bestimmten Schnittstelle auf, die Sie über den Dienst erhalten. Die Namen der Klassen werden identifiziert, damit Sie leichter erkennen können, wie die Quell Code Verwaltung ausgeführt wird.

 ![SCC&#95;TUP-Beispiele](../../extensibility/internals/media/scc_tup.gif "SCC_TUP") Beispiel für ein Quell Code Verwaltungsprojekt

## <a name="interfaces"></a>Schnittstellen
 Sie können die Quell Code Verwaltung für Ihre neuen Projekttypen in Visual Studio mithilfe der Liste der in der folgenden Tabelle gezeigten Schnittstellen implementieren.

|Schnittstelle|Zweck|
|---------------|---------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|Wird von Projekten und Editoren aufgerufen, bevor Sie Dateien speichern oder ändern (geändert) werden. Auf diese Schnittstelle wird mit dem- <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> Dienst zugegriffen.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|Wird von Projekten aufgerufen, um die Berechtigung zum Hinzufügen, entfernen oder Umbenennen einer Datei oder eines Verzeichnisses anzufordern. Diese Schnittstelle wird auch von Projekten aufgerufen, um die Umgebung zu informieren, wenn eine genehmigte Aktion zum Hinzufügen, entfernen oder umbenennen beendet ist. Der Zugriff erfolgt über den- <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> Dienst.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|Wird von einer beliebigen Entität implementiert, die registriert wird, wenn Projekte eine Datei oder ein Verzeichnis hinzufügen, umbenennen oder entfernen. Um die Ereignis Benachrichtigung zu registrieren, wenden Sie an <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A> .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|Wird von Projekten aufgerufen, die beim Quell Code Verwaltungspaket registriert werden sollen, und zum Abrufen von Informationen über den Quell Code Verwaltungsstatus. Auf diese Schnittstelle wird mit dem- <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> Dienst zugegriffen.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Wird vom Projekt implementiert, um auf Quell Code Verwaltungsanforderungen nach Informationen zu Dateien und zum Abrufen der Quell Code Verwaltungs Einstellungen, die für die Projektdatei erforderlich sind, zu reagieren.|

## <a name="see-also"></a>Weitere Informationen
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>
- [Unterstützen der Quellcodeverwaltung](../../extensibility/internals/supporting-source-control.md)
