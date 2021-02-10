---
title: Übersicht über die Festlegung von Zielversionen mit MSBuild | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie mit MSBuild eine Anwendung kompilieren, die auf verschiedenen Versionen von .NET Framework und auf verschiedenen Systemplattformen ausgeführt werden kann.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: eecbcd65-9fbc-4307-a321-46d3c3b79b12
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9d448adb2ba898eabdbac304c0087176e6ed7119
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918990"
---
# <a name="msbuild-multitargeting-overview"></a>Übersicht über die Festlegung von Zielversionen mit MSBuild

Mit MSBuild können Sie eine Anwendung kompilieren, die auf verschiedenen Versionen von .NET Framework und auf verschiedenen Systemplattformen ausgeführt werden kann. Beispielsweise können Sie die gleiche Anwendung für die Ausführung in .NET Framework 2.0 auf einer 32-Bit-Plattform und für die Ausführung in .NET Framework 4.5 auf einer 64-Bit-Plattform kompilieren.

> [!IMPORTANT]
> Trotz des Namens „Festlegung von Zielversionen“ hat ein Projekt immer nur jeweils ein Framework und eine Plattform als Ziel.

 Dies sind einige Funktionen von MSBuild für die Festlegung von Zielversionen:

- Sie können Anwendungen entwickeln, die auf frühere Versionen von .NET Framework abzielen, z. B. Version 2.0, 3.5 oder 4.

- Sie können neben .NET Framework auch auf andere Frameworks abzielen, z. B. auf das Silverlight-Framework.

- Sie können auf ein *Frameworkprofil* abzielen, das einer vordefinierten Teilmenge eines Zielframeworks entspricht.

- Sie können ebenfalls auf neu veröffentlichte Service Packs für die aktuelle .NET Framework-Version abzielen.

- Durch die Festlegung von Zielversionen mit MSBuild wird garantiert, dass von einer Anwendung nur die im Zielframework und die auf der Zielplattform verfügbaren Funktionen verwendet werden.

## <a name="target-framework-and-platform"></a>Zielframework und -plattform

 Ein *Zielframework* ist die Version von .NET Framework, in der ein erstelltes Projekt ausgeführt werden soll, und eine *Zielplattform* ist die Systemplattform, auf der das erstellte Projekt ausgeführt werden soll.  Beispielsweise können Sie eine Anwendung für die Ausführung in .NET Framework 2.0 auf einer 32-Bit-Plattform entwickeln, die mit der 80x86-Prozessorfamilie (x86) kompatibel ist. Die Kombination von Zielframework und Zielplattform wird als *Zielkontext* bezeichnet. Weitere Informationen finden Sie unter [Zielframework und -Zielplattform](../msbuild/msbuild-target-framework-and-target-platform.md).

## <a name="toolset-toolsversion"></a>Toolset (ToolsVersion)

 Ein Toolset umfasst die Tools, Aufgaben und Ziele, die verwendet werden, um die Anwendung zu erstellen. Ein Toolset umfasst Compiler wie *csc.exe* und *vbc.exe*, die Datei mit allgemeinen Zielen (*microsoft.common.targets*) und die Datei mit allgemeinen Aufgaben (*microsoft.common.tasks*). Das 4.5-Toolset kann verwendet werden, um auf die .NET Framework-Versionen 2.0, 3.0, 3.5, 4 und 4.5 abzuzielen. Das 2.0-Toolset kann dagegen nur für .NET Framework Version 2.0 verwendet werden. Weitere Informationen finden Sie unter [Toolset (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md).

## <a name="reference-assemblies"></a>Verweisassemblys

 Die Verweisassemblys, die im Toolset angegeben sind, helfen Ihnen beim Entwerfen und Erstellen einer Anwendung. Diese Verweisassemblys ermöglichen nicht nur einen bestimmten Zielbuild, sondern beschränken die Komponenten und Funktionen in der Visual Studio-IDE auch auf die mit dem Ziel kompatiblen Komponenten und Funktionen. Weitere Informationen finden Sie unter [Auflösen von Assemblys zur Entwurfszeit](../msbuild/resolving-assemblies-at-design-time.md).

## <a name="configure-targets-and-tasks"></a>Konfigurieren von Zielen und Aufgaben

 Sie können MSBuild-Ziele und -Aufgaben so konfigurieren, dass sie prozessextern mit MSBuild ausgeführt werden, damit Sie auf Kontexte abzielen können, die sich stark von dem unterscheiden, in dem Sie die Ausführung eigentlich vorgesehen haben.  Beispielsweise können Sie auf eine 32-Bit-.NET Framework 2.0-Anwendung abzielen, während der Entwicklungscomputer auf einer 64-Bit-Plattform mit .NET Framework 4.5 ausgeführt wird. Weitere Informationen finden Sie unter [Konfigurieren von Zielen und Aufgaben](../msbuild/configuring-targets-and-tasks.md).

## <a name="troubleshooting"></a>Problembehandlung

 Es können Fehler angezeigt werden, wenn Sie versuchen, auf eine Assembly zu verweisen, die nicht Teil des Zielkontexts ist. Weitere Informationen zu diesen Fehlern und wie Sie diese beheben können, finden Sie unter [Problembehandlung bei .NET Framework-Zielversionsfehlern](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).
