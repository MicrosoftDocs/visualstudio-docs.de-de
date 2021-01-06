---
title: Projekt "sonstige Dateien" | Microsoft-Dokumentation
description: Erfahren Sie mehr über die beiden Typen von Editoren, die zum Öffnen von Dateien in einem Visual Studio-Projekt verwendet werden können, und die Rolle des Projekts, um zu bestimmen, welcher Editor verwendet werden soll.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- files, adding existing files to solutions
- Miscellaneous Files project
- Solution Items folder
- files, opening with Miscellaneous Files project
ms.assetid: 93a278a8-d4f4-400b-8945-4f1b0a2b5bac
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a963b4d452a5d8ea9e0556b232f488e93dc0a29c
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97876778"
---
# <a name="miscellaneous-files-project"></a>Verschiedene Projektdateien
Wenn ein Benutzer Projekt Elemente öffnet, weist die IDE dem Projekt "sonstige Dateien" alle Elemente zu, die keine Mitglieder einer Projekt Mappe sind.

 Projekte spielen eine bedeutende Rolle beim bestimmen, welcher Editor verwendet wird, wenn ein Benutzer ein Projekt Element öffnet. Ein Projekt kann so entworfen werden, dass bestimmte Dateien mit einem projektspezifischen Editor oder einem Standard Editor geöffnet werden.

 Für einen projektspezifischen Editor ist es in der Regel erforderlich, dass der Benutzer über besondere Kenntnisse verfügt oder besondere Schnittstellen aus dem Projekt verwendet. Weitere Informationen finden Sie unter Gewusst [wie: Öffnen von Project-Specific-Editoren](../../extensibility/how-to-open-project-specific-editors.md).

 Mit einem Standard-Editor kann eine beliebige Datei einer bestimmten Erweiterung in jedem Projekt geöffnet werden. Der Benutzer kann einige Standard-Editoren, z. b. den [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Text-Editor, für Projekte anpassen, aber weiterhin sein öffentliches Zeichen beibehalten. Standard-Editoren werden mithilfe der- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> Methode erstellt.

 Wenn kein Projekt in der Projekt Mappe antwortet, dass ein Projekt Element geöffnet werden kann, stellt die IDE ein spezielles Projekt namens "sonstige Dateien" bereit, mit dem eine beliebige Datei geöffnet wird.

 Dieses spezielle Projekt ermöglicht das Öffnen einer Datei außerhalb des Kontexts eines Projekts. Während der Verarbeitung der- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> Methode antwortet das Projekt "sonstige Dateien" immer mit einer sehr niedrigen Priorität. Aus diesem Grund ergibt das Projekt "sonstige Dateien" immer alle Projekte mit höherer Priorität, die Dateien öffnen können.

 Das Projekt "sonstige Dateien" erfordert nicht, dass der Benutzer es explizit mit dem Dialogfeld " **Neues Projekt** " erstellt. Außerdem verwaltet das Projekt "sonstige Dateien" eine Liste von Projekt Membern nicht dauerhaft. Es wird ein optionales Feature verwendet, um eine Liste der zuletzt verwendeten Dateien für jeden Benutzer aufzuzeichnen.

## <a name="see-also"></a>Weitere Informationen
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>
- <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>
- [Gewusst wie: Öffnen von projektspezifischen Editoren](../../extensibility/how-to-open-project-specific-editors.md)
- [Gewusst wie: Öffnen von Standard-Editoren](../../extensibility/how-to-open-standard-editors.md)
- [Hinzufügen von Projekt- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Hinzufügen von Projekt- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md)
