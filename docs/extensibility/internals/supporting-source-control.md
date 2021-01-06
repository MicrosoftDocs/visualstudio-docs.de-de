---
title: Unterstützen der Quell Code Verwaltung | Microsoft-Dokumentation
description: Erfahren Sie, wie Visual Studio Datei Checkouts, Check-ins und andere Quell Code Verwaltungsvorgänge für Ihr Projekt oder Ihren Editor unterstützt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], supporting
ms.assetid: 567acde3-354e-4f39-8d99-0ef86c103396
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4e722770ad1db4b85dbc2a5a8754d9158b6ee436
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97876453"
---
# <a name="supporting-source-control"></a>Unterstützen der Quellcodeverwaltung
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] unterstützt Datei Checkouts, Check-ins und andere Quell Code Verwaltungsvorgänge für Ihr Projekt oder Ihren Editor. Als Quell Code [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Verwaltungs Client ist für die Interaktion mit einem Quell Code Verwaltungspaket wie konzipiert, [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] das Archivierungs-, Versions-und Steuerungsfunktionen für einen dynamisch definierten Satz von Dateien bereitstellt.

## <a name="in-this-section"></a>In diesem Abschnitt
- [Modell für Quellcodeverwaltungspakete](../../extensibility/internals/model-for-source-control-packages.md)

 Beschreibt die Schnittstellen, die ein Projekttyp implementieren muss, um die Quell Code Verwaltung

- [Entwurfsentscheidungen](../../extensibility/internals/source-control-design-decisions.md)

 Stellt Fragen bereit, mit deren Antworten die Implementierung eines Projekt Typs geändert wird.

- [Konfigurationsdetails](../../extensibility/internals/source-control-configuration-details.md)

 Beschreibt, wie die unterstützende Quell Code Verwaltung die Implementierung eines Projekt Typs ändert.

- [Zusätzliche Richtlinien für Projekte und Editoren](../../extensibility/internals/additional-source-control-guidelines-for-projects-and-editors.md)

 Erläutert bewährte Methoden für Projekttypen und Editoren.

- [Runtime-Details](../../extensibility/internals/source-control-runtime-details.md)

 Beschreibt, wie ein Projekt registriert wird, wenn ein Benutzer es einem Quell Code Verwaltungssystem hinzufügt.

## <a name="reference"></a>Verweis
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> Gibt dem Umgebungs-oder Quell Code Verwaltungspaket an, dass eine Datei im Arbeitsspeicher geändert oder gespeichert wird.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> Ermöglicht Projekten und Hierarchien das Registrieren mit der Quell Code Verwaltung und das Abrufen von Informationen über den Status der Quell Code Verwaltung.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> Wird in einem Projekt System implementiert, um die Quell Code Verwaltung für Projektdateien und Projekt Elemente bereitzustellen.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> Wird von Projekten verwendet, um die Umgebung für die Berechtigung zum Hinzufügen, entfernen oder Umbenennen einer Datei oder eines Verzeichnisses in einer Projekt Mappe abzufragen.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> Benachrichtigt Clients über Änderungen, die an Projektdateien oder-Verzeichnissen vorgenommen wurden.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Projekttypen](../../extensibility/internals/project-types.md)

 Bietet eine Übersicht über Projekte als grundlegende Bausteine der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierten Entwicklungsumgebung (Integrated Development Environment, IDE). Links werden für weitere Themen bereitgestellt, in denen erläutert wird, wie Projekte das Erstellen und Kompilieren von Code steuern.
