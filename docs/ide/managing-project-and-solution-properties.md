---
title: Verwalten von Projekt- und Projektmappeneigenschaften
description: Erfahren Sie, wie Sie die Projekteigenschaften und Projektmappeneigenschaften in Visual Studio verwalten können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0cef610da1bcbfe7cb9c6c7ab5a806b74e07e177
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99959414"
---
# <a name="manage-project-and-solution-properties"></a>Verwalten von Projekt- und Projektmappeneigenschaften

Projekte haben Eigenschaften, die viele Aspekte der Kompilierung, des Debuggens, des Testens und des Bereitstellens steuern. Einige Eigenschaften gibt es für alle Projekttypen, und einige gelten nur für bestimmte Sprachen oder Plattformen. Sie erhalten Zugriff auf die Projekteigenschaften, indem Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Projektknoten klicken und **Eigenschaften** auswählen. Alternativ können Sie **Eigenschaften** in das Suchfeld in der Menüleiste eingeben und **Eigenschaftenfenster** aus den Suchergebnissen auswählen.

![Kontextmenü „Projekt“](../ide/media/vs2015_proj_prop_menu.gif)

.NET-Projekte haben womöglich außerdem einen Eigenschaftenknoten in der Projektstruktur selbst.

![Knoten "Eigenschaften" in der Struktur des Projektmappen-Explorers](../ide/media/vs2015_props_se.png)

> [!NOTE]
> Dieses Thema gilt für Visual Studio unter Windows. Informationen zu Visual Studio für Mac finden Sie unter [Verwalten von Projektmappen und Projekteigenschaften (Visual Studio für Mac)](/visualstudio/mac/managing-solutions-and-project-properties).

## <a name="project-properties"></a>Projekteigenschaften

Projekteigenschaften werden in Gruppen organisiert, und jede Gruppe hat eine eigene Eigenschaftenseite. Diese kann je nach Sprache und Projekttyp unterschiedlich aussehen.

### <a name="c-visual-basic-and-f-projects"></a>C#-, Visual Basic- und F#-Projekte

In C#-, Visual Basic- und F#-Projekten sind Eigenschaften im **Projekt-Designer** verfügbar. Folgende Abbildung zeigt die Eigenschaftsseite **Build** für ein WPF-Projekt in C#:

![Visual Studio-Projekt-Designer](../ide/media/vs2015_proppage_build.png)

Informationen zu den einzelnen Eigenschaftsseiten im **Projekt-Designer** finden Sie unter [Project properties reference (Referenz zu Projekteigenschaften)](../ide/reference/project-properties-reference.md).

> [!TIP]
> Projektmappen besitzen ebenso wie Projektelemente einige Eigenschaften. Auf diese Eigenschaften wird nicht über den **Projekt-Designer**, sondern über das [Eigenschaftenfenster](../ide/reference/properties-window.md) zugegriffen.

### <a name="c-and-javascript-projects"></a>C++- und JavaScript-Projekte

C++- und JavaScript-Projekte haben eine andere Benutzeroberfläche zum Verwalten von Projekteigenschaften. Die folgende Abbildung zeigt eine Eigenschaftenseite für ein C++-Projekt (JavaScript-Seiten sind ähnlich):

![Visual C&#43;&#43;-Projekteigenschaften](../ide/media/vs2015_projprops_cpp.png)

Informationen zu C++-Projekteigenschaften finden Sie unter [Arbeiten mit Projekteigenschaften (C++)](/cpp/build/working-with-project-properties). Weitere Informationen zu JavaScript-Eigenschaften finden Sie unter [Eigenschaftenseiten, JavaScript](../ide/reference/property-pages-javascript.md).

## <a name="solution-properties"></a>Lösungseigenschaften

Um auf Eigenschaften für die Projektmappe zuzugreifen, klicken Sie mit der rechten Maustaste auf den Projektmappenknoten im **Projektmappen-Explorer** und wählen **Eigenschaften** aus. In diesem Dialogfeld können Sie Projektkonfigurationen für **Debug-** oder **Releasebuilds** festlegen. Sie können auswählen, welche Projekte beim Drücken von **F5** als Startprojekt verwendet werden sollen, und Sie können Codeanalyseoptionen festlegen.

## <a name="see-also"></a>Weitere Informationen

- [Projektmappen und Projekte in Visual Studio](../ide/solutions-and-projects-in-visual-studio.md)
- [Verwalten von Projektmappen und Projekteigenschaften (Visual Studio für Mac)](/visualstudio/mac/managing-solutions-and-project-properties)
