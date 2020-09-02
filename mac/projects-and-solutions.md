---
title: Projekte und Projektmappen
description: Dieses Dokument enthält eine Übersicht der Projekte und Projektmappen in Visual Studio für Mac.
ms.topic: overview
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/23/2019
ms.assetid: 8254505D-D96E-48BD-8A5E-CF6A917897EA
ms.openlocfilehash: 92e7a47f7ea2b931c0b923d10e115843d315d024
ms.sourcegitcommit: 26178b116cbf7353fee6ca989b8d872114f7b405
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/01/2020
ms.locfileid: "89284303"
---
# <a name="projects-and-solutions-in-visual-studio-for-mac"></a>Projekte und Projektmappen in Visual Studio für Mac

Dieser Artikel bietet eine Übersicht über die Konzepte *Projekt* und *Projektmappe* in Visual Studio für Mac.

> [!NOTE] 
> Dieses Thema gilt für Visual Studio für Mac. Informationen zu Visual Studio unter Windows finden Sie unter [Projektmappen und Projekte in Visual Studio](/visualstudio/ide/solutions-and-projects-in-visual-studio).

## <a name="projects"></a>Projekte

Wenn Sie in Visual Studio für Mac eine neue Anwendung, eine neue Website usw. erstellen, beginnen Sie mit einem Projekt. Das Projekt enthält alle Dateien (Quellcode, Bilder, Datendateien usw.), die zum Kompilieren in eine ausführbare Datei, Bibliothek oder Website erforderlich sind.

Ein Projekt wird durch eine Datei (z.B. `.csproj` für C#-Projekte) definiert, die den XML-Code zur Definition der Datei- und Ordnerhierarchie, der Pfade zu Dateien sowie der projektspezifischen Einstellungen enthält, beispielsweise der Buildeinstellungen.

Wenn ein Projekt von Visual Studio für Mac geladen wird, verwendet das Lösungspad die Projektdatei, um die Dateien und Ordner in Ihrem Projekt anzuzeigen. Während der Kompilierung liest MSBuild die Einstellungen aus der Projektdatei, um die ausführbare Datei zu erstellen.

## <a name="solutions"></a>Projektmappen

Eine *Projektmappe* ist ein Container, der ein oder mehrere verwandte Projekte gruppiert. Projektmappen werden von einer Textdatei (mit der Erweiterung `.sln`) in einem individuellen Format beschrieben. Diese Datei sollte nicht manuell bearbeitet werden.

## <a name="managing-projects-in-the-solution-pad"></a>Verwalten von Projekten im Lösungspad

Sobald ein Projekt erstellt oder geladen wurde, können Sie das Lösungspad verwenden, um das Projekt oder die Projektmappe und die darin enthaltenen Dateien anzuzeigen und zu verwalten. Die folgende Abbildung zeigt das Lösungspad mit einer .NET Core-Projektmappe, die zwei Projekte enthält:

![Beispielprojektmappe mit mehreren Projekten](media/solution-example.png)

Sie können die Eigenschaften von Projekten und Projektmappen verwalten, indem Sie auf den Namen des Projekts oder der Projektmappe doppelklicken, oder indem Sie mit der rechten Maustaste darauf klicken und **Optionen** auswählen.

Weitere Informationen zu diesen Optionen finden Sie im Artikel [Verwalten von Projekt- und Projektmappeneigenschaften](managing-solutions-and-project-properties.md).

## <a name="see-also"></a>Siehe auch

- [Projektmappen und Projekte in Visual Studio](/visualstudio/ide/solutions-and-projects-in-visual-studio)
