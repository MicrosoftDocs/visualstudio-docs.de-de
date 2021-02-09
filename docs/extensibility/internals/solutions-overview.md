---
title: Übersicht über Lösungen
description: Erfahren Sie mehr über die internale einer Lösung für Erweiterungs Entwickler, die mit Lösungen in Visual Studio-Erweiterungen arbeiten möchten.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, about solutions
ms.assetid: 3b21e3a1-170a-4485-941e-6b04b7b27886
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 91903954f490e5845e01ddbf4b7aa4767f2ceacc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99846542"
---
# <a name="solutions-overview"></a>Übersicht über Lösungen

Eine Lösung ist eine Gruppierung von einem oder mehreren Projekten, die zusammenarbeiten, um eine Anwendung zu erstellen. Die Projekt-und Statusinformationen, die sich auf die Lösung beziehen, werden in zwei verschiedenen Projektmappendateien gespeichert. Die [Projektmappendatei (. sln)](solution-dot-sln-file.md) ist Text basiert und kann unter Quell Code Verwaltung platziert und von Benutzern gemeinsam genutzt werden. Die [Benutzer Option für die Projekt Mappe (suo)](solution-user-options-dot-suo-file.md) ist binär. Folglich kann die SUO-Datei nicht unter Quell Code Verwaltung platziert werden und enthält benutzerspezifische Informationen.

Jedes VSPackage kann in beide Arten von Projektmappendateien schreiben. Aufgrund der Art der Dateien gibt es zwei verschiedene Schnittstellen, die implementiert werden, um in Sie zu schreiben. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> -Schnittstelle schreibt Textinformationen in die SLN-Datei, und die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> Schnittstelle schreibt binäre Datenströme in die SUO-Datei.

> [!NOTE]
> Ein Projekt muss nicht explizit einen Eintrag für sich selbst in die Projektmappendatei schreiben. die Umgebung übernimmt diese für das Projekt. Wenn Sie der Projektmappendatei nicht nur zusätzlichen Inhalt hinzufügen möchten, müssen Sie das VSPackage daher nicht auf diese Weise registrieren.

Jedes VSPackage, das die Lösungs Persistenz unterstützt, verwendet drei Schnittstellen: die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> Schnittstelle, die von der Umgebung implementiert und vom VSPackage aufgerufen wird, und `IVsPersistSolutionProps` und `IVsPersistSolutionOpts` , die beide durch das VSPackage implementiert werden. Die `IVsPersistSolutionOpts` Schnittstelle muss nur implementiert werden, wenn private Informationen vom VSPackage in die SUO-Datei geschrieben werden sollen.

Wenn eine Projekt Mappe geöffnet wird, findet der folgende Prozess statt.

1. Die Umgebung wird von der Umgebung gelesen.

2. Wenn die Umgebung eine findet `CLSID` , wird das entsprechende VSPackage geladen.

3. Wenn ein VSPackage geladen wird, ruft die Umgebung `QueryInterface` für <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> die Schnittstelle, die das VSPackage erfordert, eine Schnittstelle auf.

   - Beim Lesen aus einer SLN-Datei ruft die Umgebung `QueryInterface` für auf `IVsPersistSolutionProps` .

   - Beim Lesen aus einer SUO-Datei ruft die Umgebung `QueryInterface` für auf `IVsPersistSolutionOpts` .

   Spezifische Informationen zur Verwendung dieser Dateien finden Sie in der [Lösung (). Sln)-Datei](../../extensibility/internals/solution-dot-sln-file.md) -und Projektmappenbenutzeroptionen [(. Suo)](../../extensibility/internals/solution-user-options-dot-suo-file.md).

> [!NOTE]
> Wenn Sie eine neue Projektmappenkonfiguration erstellen möchten, die aus den Konfigurationen von zwei Projekten besteht und ein drittes aus dem Build ausschließt, müssen Sie die Eigenschaften Seiten-Benutzeroberfläche oder-Automatisierung verwenden. Sie können die Projektmappenbuild-Manager-Konfigurationen und ihre Eigenschaften nicht direkt ändern, aber Sie können den Projektmappenbuild-Manager mithilfe der- `SolutionBuild` Klasse von DTE im Automatisierungs Modell bearbeiten. Weitere Informationen zum Konfigurieren von Lösungen finden Sie [](../../extensibility/internals/solution-configuration.md)unter Projektmappenkonfiguration.

## <a name="see-also"></a>Weitere Informationen

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>
