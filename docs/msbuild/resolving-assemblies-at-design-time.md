---
title: Auflösen von Assemblys zur Entwurfszeit | Microsoft-Dokumentation
description: Erfahren Sie, wie MSBuild Verweise auf Assemblys zur Entwurfszeit mithilfe von Referenzassemblys im Zielpaket auflöst.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild
ms.assetid: 20dae076-733e-49c1-a2e9-b336757ae21d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 515c99a4d73abcb3a287f3f4026723bd8050b360
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048489"
---
# <a name="resolve-assemblies-at-design-time"></a>Auflösen von Assemblys zur Entwurfszeit

Wenn Sie über die Registerkarte **.NET** des Dialogfelds **Verweis hinzufügen** einen Verweis auf eine Assembly hinzufügen, zeigt der Verweis auf eine Zwischenverweisassembly, also eine Assembly, die alle Typ- und Signaturinformationen, aber nicht notwendigerweise Code enthält. Auf der Registerkarte **.NET** sind Verweisassemblys aufgeführt, die Laufzeitassemblys in .NET Framework entsprechen. Außerdem werden Verweisassemblys aufgeführt, die den Laufzeitassemblys in den von Drittanbietern verwendeten registrierten AssemblyFoldersEx-Ordnern entsprechen.

## <a name="multi-targeting"></a>Festlegung von Zielversionen

 Mit Visual Studio können Sie Zielversionen von .NET Framework erstellen, die auf verschiedenen .NET Framework-Versionen ausgeführt werden. Wenn eine neue .NET Framework-Version veröffentlicht wird, kann das Framework mit einem Paket zur Festlegung von Zielversionen installiert werden und wird automatisch als Ziel in Visual Studio angezeigt.

## <a name="how-type-resolution-works"></a>So funktioniert Typauflösung

 Zur Laufzeit löst die CLR die Typen in der Assembly auf, indem sie die GAC, das Verzeichnis *bin* und alle Prüfpfade durchsucht. Dies wird vom Fusion-Ladeprogramm gehandhabt. Aber woher weiß das Fusion-Ladeprogramm, wonach gesucht werden soll? Dies hängt von der zur Entwurfszeit (als die Anwendung erstellt wurde) festgelegten Auflösung ab.

 Während des Builds löst der Compiler mithilfe von Verweisassemblys Anwendungstypen auf. In den Versionen 2.0, 3.0, 3.5, 4, 4.5 und 4.5.1 von .NET Framework werden die Verweisassemblys bei der Installation von .NET Framework mitinstalliert.

 Die Verweisassemblys werden durch das Paket zur Festlegung von Zielversionen bereitgestellt, das mit der entsprechenden Version des .NET Framework-SDKs geliefert wird. Das Framework selbst stellt nur die Laufzeitassemblys bereit. Zur Erstellung von Anwendungen müssen sowohl .NET Framework als auch das entsprechende .NET Framework-SDK installiert werden.

 Wenn Sie auf eine bestimmte Version von .NET Framework abzielen, löst das Buildsystem mithilfe der Verweisassemblys im Paket zur Festlegung von Zielversionen alle Typen auf. Zur Laufzeit löst das Fusion-Ladeprogramm dieselben Typen in die Laufzeitassemblys auf, die sich in der Regel im GAC befinden.

 Wenn Verweisassemblys nicht verfügbar sind, löst das Buildsystem Assemblytypen mithilfe der Laufzeitassemblys auf. Da Laufzeitassemblys im GAC nicht durch Nebenversionsnummern unterschieden werden, ist es möglich, dass die falsche Assembly aufgelöst wird. Dies könnte beispielsweise geschehen, wenn beim Abzielen auf Version 3.0 auf eine neue in .NET Framework, Version 3.5, eingeführte Methode verwiesen wird. Der Build wird erfolgreich erstellt, und die Anwendung wird auf dem Buildcomputer ausgeführt, ist aber nur auf Computern lauffähig, auf denen Version 3.5 installiert ist.

 Das Paket zur Festlegung von Zielversionen, das jetzt mit dem .NET Framework SDK geliefert wird, enthält eine Liste (auch Neuverteilungsliste (redist) genannt) aller Laufzeitassemblys dieser Version des Frameworks, sodass es unmöglich ist, dass das Buildsystem Typen anhand der falschen Assemblyversion auflöst.

## <a name="see-also"></a>Siehe auch
- [Weiterführende Konzepte](../msbuild/msbuild-advanced-concepts.md)
