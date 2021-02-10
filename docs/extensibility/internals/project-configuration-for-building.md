---
title: Projekt Konfiguration zum aufbauen | Microsoft-Dokumentation
description: Erfahren Sie, wie eine Liste von Projektmappenkonfigurationen für eine bestimmte Lösung über das Dialogfeld Projektmappenkonfigurationen in einem neuen Projekttyp verwaltet wird.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], configuration for building
- project configurations, building
ms.assetid: 2c83615d-fa4d-4b9f-b315-7a69b3000da0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b8891d5e68623312049e60730b0239bf7c06e83c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99954474"
---
# <a name="project-configuration-for-building"></a>Projektkonfiguration beim Erstellen
Die Liste der Projektmappenkonfigurationen für eine bestimmte Projekt Mappe wird im Dialogfeld Projektmappenkonfigurationen verwaltet.

 Ein Benutzer kann zusätzliche Projektmappenkonfigurationen erstellen, die jeweils über einen eigenen eindeutigen Namen verfügen. Wenn der Benutzer eine neue Projektmappenkonfiguration erstellt, verwendet die IDE standardmäßig den entsprechenden Konfigurations Namen in den Projekten, oder Debuggen, wenn kein entsprechender Name vorhanden ist. Der Benutzer kann die Auswahl ändern, um bei Bedarf bestimmte Anforderungen zu erfüllen. Die einzige Ausnahme von diesem Verhalten besteht darin, dass das Projekt eine Konfiguration unterstützt, die mit dem Namen der neuen Projektmappenkonfiguration übereinstimmt. Nehmen Sie beispielsweise an, eine Projekt Mappe enthält Projekt1 und "Projekt2". Projekt1 weist Projekt Konfigurationen Debug, Retail und MyConfig1 auf. "Projekt2" weist Projekt Konfigurationen Debug, Retail und MyConfig2 auf.

 Wenn der Benutzer eine neue Projektmappenkonfiguration mit dem Namen MyConfig2 erstellt, bindet Projekt1 die Debugkonfiguration standardmäßig an die Projektmappenkonfiguration. "Projekt2" bindet auch die MyConfig2-Konfiguration standardmäßig an die Projektmappenkonfiguration.

> [!NOTE]
> Bei der Bindung wird die Groß-/Kleinschreibung

 Wenn der Benutzer das **Mehrfachauswahl** Element in der Dropdown Liste Konfiguration auswählt, wird in der Umgebung ein Dialogfeld angezeigt, in dem die Liste der verfügbaren Konfigurationen angezeigt wird.

 ![Mehrere Konfigurationen](../../extensibility/internals/media/vsmultiplecfgs.gif "vsmultiplecfgs") Mehrere Konfigurationen

 In diesem Dialogfeld kann der Benutzer eine oder mehrere Konfigurationen auswählen. Nachdem diese Option ausgewählt wurde, wird im Dialogfeld Eigenschaften Seiten die Schnittmenge der Werte für die ausgewählten Konfigurationen angezeigt.

 Informationen [](../../extensibility/internals/solution-configuration.md) zum Hinzufügen und Umbenennen von Konfigurationen für Projektmappen und Projekte finden Sie unter Projektmappenkonfiguration.

 Projekt Abhängigkeiten und Buildreihenfolge sind von der Projektmappenkonfiguration unabhängig: das heißt, Sie können nur eine Abhängigkeitsstruktur für alle Projekte in der Projekt Mappe einrichten. Wenn Sie mit der rechten Maustaste auf die Projekt Mappe oder das Projekt klicken und die Option Projekt **Abhängigkeiten** oder **projektbuildauftrag** auswählen, wird das Dialogfeld **Projekt Abhängigkeiten** geöffnet. Sie kann auch über das Menü **Projekt** geöffnet werden.

 ![Projekt Abhängigkeiten](../../extensibility/internals/media/vsprojdependencies.gif "vsprojabhängigkeiten") Projekt Abhängigkeiten

 Projekt Abhängigkeiten legen die Reihenfolge fest, in der Projekte erstellt werden. Mithilfe der Registerkarte Buildreihenfolge im Dialogfeld können Sie die genaue Reihenfolge anzeigen, in der Projekte in einer Projekt Mappe erstellt werden, und die Buildreihenfolge auf der Registerkarte Abhängigkeiten ändern.

> [!NOTE]
> Projekte in der Liste, deren Kontrollkästchen aktiviert, aber abgeblendet angezeigt werden, wurden von der Umgebung aufgrund expliziter Abhängigkeiten, die von der- <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> Schnittstelle oder der-Schnittstelle angegeben werden, hinzugefügt <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> . Wenn Sie beispielsweise einen Projekt Verweis von einem [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] Projekt zu einem anderen Projekt hinzufügen, wird automatisch eine Buildabhängigkeit hinzugefügt, die nur durch Löschen des Verweises entfernt werden kann Projekte, deren Kontrollkästchen klar und abgeblendet angezeigt werden, können nicht ausgewählt werden, da dadurch eine Abhängigkeits Schleife erstellt werden würde (z. b. Projekt1 ist von "Projekt2" abhängig, und "Projekt2" ist von Projekt1 abhängig), was den Build bereinigen würde.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Buildprozesse enthalten die typischen Kompilierungs-und Verknüpfungs Vorgänge, die mit einem einzelnen Build-Befehl aufgerufen werden. Zwei weitere Buildprozesse können ebenfalls unterstützt werden: ein Bereinigungs Vorgang zum Löschen aller Ausgabe Elemente aus einem vorherigen Build und eine Aktualisierungs Überprüfung, um zu bestimmen, ob sich ein Ausgabe Element in einer Konfiguration geändert hat.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> -Objekte geben eine entsprechende <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> (von zurückgegebene <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A> ) zurück, um Ihre Buildprozesse zu verwalten. Um den Status eines Buildvorgangs während des Vorgangs zu melden, führen Konfigurationen Aufrufe an <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildStatusCallback> aus, eine von der Umgebung implementierte Schnittstelle und alle anderen Objekte, die an buildstatuseignissen interessiert sind.

 Nach der Erstellung können Konfigurationseinstellungen verwendet werden, um zu bestimmen, ob Sie unter der Kontrolle des Debuggers ausgeführt werden können. Konfigurationen implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> , um das Debugging zu unterstützen.

 Nachdem Sie die Projekt Abhängigkeiten implementiert haben, können Sie die Abhängigkeiten über das Automatisierungs Modellprogramm gesteuert bearbeiten. Sie werden <xref:EnvDTE.SolutionBuild.BuildDependencies%2A> im Automatisierungs Modell aufgerufen. Es sind keine verfügbaren Schnittstellen auf VSIP-API-Ebene verfügbar, die eine direkte Bearbeitung der Projektmappenbuild-Manager-Konfigurationen und ihrer Eigenschaften ermöglichen.

 Darüber hinaus können Sie ein Raster im Fenster "Projekt Abhängigkeiten" bereitstellen. Weitere Informationen finden Sie unter [Eigenschaften Anzeige Raster](../../extensibility/internals/properties-display-grid.md).

## <a name="see-also"></a>Weitere Informationen
- [Verwalten von Konfigurationsoptionen](../../extensibility/internals/managing-configuration-options.md)
- [Projektkonfiguration für die Verwaltung der Bereitstellung](../../extensibility/internals/project-configuration-for-managing-deployment.md)
- [Projektkonfiguration für die Ausgabe](../../extensibility/internals/project-configuration-for-output.md)
