---
title: Kompilieren und Erstellen
description: In diesem Artikel erfahren Sie, wie Sie Projekte und Projektmappen in Visual Studio für Mac kompilieren und erstellen können.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: FB253757-DB00-4889-A6BF-E44722E25BD1
ms.topic: overview
ms.openlocfilehash: d5613a47785f1bb3fbb2a56f8458bba1946930e7
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2021
ms.locfileid: "98719800"
---
# <a name="compiling-and-building-in-visual-studio-for-mac"></a>Kompilieren und Generieren in Visual Studio für Mac

Mit Visual Studio für Mac können Sie Anwendungen und Assemblys während der Entwicklung Ihres Projekts erstellen. Es ist wichtig, Ihren Code früh und häufig zu kompilieren und zu erstellen, damit Sie Typenkonflikte und andere Kompilierzeitfehler identifizieren können.

## <a name="building-from-the-ide"></a>Erstellen aus der IDE

Mit Visual Studio für Mac können Sie Builds erstellen und umgehend ausführen, während Sie weiterhin die Kontrolle über Buildfunktionen haben. Visual Studio für Mac verwendet MSBuild als zugrundeliegendes Buildsystem.

Alle Projekte und Projektmappen, die in der IDE erstellt werden, weisen eine Standardbuildkonfiguration auf, die den Kontext des Builds definiert. Diese Konfigurationen können bearbeitet werden, oder Sie können Sie selbst erstellen. Das Erstellen oder Modifizieren dieser Konfigurationen aktualisiert automatisch die Projektdatei, die dann von MSBuild verwendet wird, um das Projekt zu erstellen.

Weitere Informationen zum Erstellen Ihrer eigenen Projekte und Projektmappen in der IDE finden Sie im Handbuch [Erstellen und Bereinigen von Projekten und Projektmappen in Visual Studio](building-and-cleaning-projects-and-solutions.md).

Mit Visual Studio für Mac können Sie auch:

* Den Ausgabepfad ändern. Diesen können Sie in den Optionen Ihres Projekts bearbeiten.

    ![Ändern des Ausgabepfads](media/compiling-and-building-image4.png)

* Den Ausführlichkeitsgrad der Buildausgabe ändern:

    ![Ändern des Ausführlichkeitsgrads des Builds](media/compiling-and-building-image5.png)

* Benutzerdefinierte Befehle vor, während oder nach dem Erstellen oder Bereinigen hinzufügen:

    ![Hinzufügen benutzerdefinierter Befehle](media/compiling-and-building-image6.png)

## <a name="building-from-command-line"></a>Erstellen über die Befehlszeile

Sie können die Build-Engine von MSBuild verwenden, um Anwendungen über die Befehlszeile zu erstellen.

Weitere Informationen zum Verwenden von MSBuild finden Sie in den Artikeln zu [MSBuild](/visualstudio/msbuild/msbuild).

## <a name="building-from-azure-pipelines"></a>Erstellen mit Azure Pipelines

* [Erstellen Ihrer Xamarin-App](/vsts/pipelines/apps/mobile/xamarin?view=vsts&preserve-view=true&tabs=vsts)
* [Fortlaufende Integration in Xamarin](https://developer.xamarin.com/guides/cross-platform/ci/)

## <a name="see-also"></a>Weitere Informationen

- [Kompilieren und Erstellen (Visual Studio unter Windows)](/visualstudio/ide/compiling-and-building-in-visual-studio)