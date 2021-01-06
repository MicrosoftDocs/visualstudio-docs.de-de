---
title: Persistenz und die laufende Dokument Tabelle | Microsoft-Dokumentation
description: Erfahren Sie, wie Projekte das Öffnen, speichern und Umbenennen von Dokumenten in der laufenden Dokument Tabelle koordinieren, die den Dokument Zustand in der Visual Studio-IDE nachverfolgt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, managing
- IVsPersistHierarchyItem interface, implementing
- architecture, persistence
- running document table (RDT), architecture
ms.assetid: 27117eae-6c58-4189-a61a-1397a43b5ecf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bfc480c8b4a41fe29900681289ad08c54d3c1f31
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97875959"
---
# <a name="persistence-and-the-running-document-table"></a>Persistenz und die aktive Dokumenttabelle
In der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE sind Projekte vollständig für die Verwaltung der Persistenz ihrer Projekt Elemente verantwortlich, die Sie mit dem Dienst erreichen <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> . Dokumente sind die grundlegende Einheit der Persistenz in der Visual Studio-Umgebung. Projekte koordinieren das Öffnen, speichern und Umbenennen von Dokumenten mit der laufenden dokumententabelle (RDT), einer Ressource, die den Status aller geöffneten Dokumente nachverfolgt.

## <a name="managing-persistence"></a>Verwalten der Persistenz
 Projekte steuern den Persistenzdienst der Umgebung durch Implementieren der- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> Schnittstelle. Obwohl die Umgebung nicht direkt ein Dokument anfordert, sich selbst beizubehalten, wird das zuständige Projekt (oder die Hierarchie) aufgefordert, das Dokument zu speichern. Dies ermöglicht es dem Projekt, seine Projekt Elementdaten in lokalen Dateien, Remote Dateien, einer Datenbank, einem Repository oder einem anderen Medium zu speichern.

 Die globale Umgebung verwaltet den RDT. In der Umgebung werden Einträge für alle geöffneten Fenster und Dokumente im RDT verwaltet, sodass Sie spezielle Benachrichtigungen erhalten können, z. b. Wenn eine Projekt Mappe geschlossen wird. Außerdem ermöglicht der RDT es der Umgebung, die entsprechenden Knoten in **Projektmappen-Explorer** zu verfolgen. Der RDT verwaltet einen Datensatz pro geöffnetes, dauerhaften Objekt, einschließlich Projektdateien und Projekt Element Dokumenten.

## <a name="see-also"></a>Weitere Informationen
- [Aktive Dokumenttabelle](../../extensibility/internals/running-document-table.md)
- [Auswahl und Aktualität in der IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
