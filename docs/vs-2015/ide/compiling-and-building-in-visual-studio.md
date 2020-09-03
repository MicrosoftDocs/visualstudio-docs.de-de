---
title: Kompilieren und Erstellen
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- builds [Visual Studio], about building in Visual Studio
- custom build steps, types of builds
ms.assetid: c7958821-285f-4e28-9e7a-b5d8b40336a1
caps.latest.revision: 30
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d8ec7d6508ec025a2b2005754da03bdd4db38943
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "74300267"
---
# <a name="compiling-and-building-in-visual-studio"></a>Kompilieren und Generieren in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können Visual Studio verwenden, um während eines Entwicklungszyklus in kurzen Abständen Anwendungen, Assemblys und ausführbare Programme zu erstellen. Indem Sie den Code häufig erstellen, können Sie Kompilierungsfehler, z. B: falsche Syntax, falsch geschriebene Schlüsselwörter und Typenkonflikte, früher identifizieren. Sie können auch Laufzeitfehler, z. B. Logik- und Semantikfehler, erkennen und beheben, indem Sie häufig Debugversionen des Codes erstellen und ausführen.

 Nachdem die Entwicklung eines Projekts oder einer Projektmappe vollständig abgeschlossen wurde und auch das Debuggen in ausreichendem Maße erfolgt ist, werden die Komponenten in ein Releasebuild kompiliert. Standardmäßig wird ein Releasebuild dahingehend optimiert und entworfen, dass es kleiner ist als eine Debugversion und schneller ausgeführt werden kann. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer Anwendung](../ide/walkthrough-building-an-application.md).

## <a name="choosing-a-build-method"></a>Auswählen einer Erstellungsmethode
 Sie können eine Anwendung mithilfe der Standardbuildoptionen in der IDE, an einer Eingabeaufforderung oder unter Verwendung von Team Foundation Build erstellen. Bei jedem dieser Optionen wird MSBuild als zugrunde liegende Technologie verwendet, und jeder Ansatz bietet bestimmte in der folgenden Tabelle aufgeführte Vorteile.

|Erstellungsmethode|Vorteile|Weitere Informationen finden Sie unter|
|------------------|--------------|--------------------------|
|Verwenden von IDE|– Sie können Builds leichter erstellen und sofort ausführen.<br />– Sie können Multiprozessorbuilds für C++- und C#-Projekte ausführen.<br />– Sie können einige Aspekte des Buildsystems anpassen.|[Erstellen und Bereinigen von Projekten und Projektmappen in Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)|
|Ausführen einer MSBuild-Befehlszeile|– Sie können Projekte erstellen, ohne Visual Studio zu installieren.<br />– Sie können Multiprozessorbuilds für alle Projekttypen ausführen.<br />– Sie können die meisten Bereiche des Buildsystems anpassen.|[MSBuild](../msbuild/msbuild.md)|
|Verwenden von Team Foundation Build|– Sie können den Buildprozess automatisieren. Beispielsweise können Sie ein Projekt oder mehrere Projekte jede Nacht oder bei jedem Einchecken dieses Code ausführen. Sie können Projekte auch auf freigegebenen Buildservern anstatt auf dem Entwicklungscomputer erstellen.<br />– Sie können den Code, den Sie erstellen möchten, die auszuführenden Tests und andere allgemeine Optionen schnell festlegen.<br />– Sie können den Buildworkflow ändern und ggf. Buildaktivitäten zum Ausführen benutzerdefinierter Aufgaben erstellen.|[Erstellen der Anwendung](/azure/devops/pipelines/index)|

## <a name="building-from-the-ide"></a>Erstellen aus der IDE
 Wenn Sie ein Projekt erstellen, werden dafür standardmäßige Buildkonfigurationen definiert, und ihm wird eine Projektmappenbuildkonfiguration zugewiesen, um Kontext für Builds bereitzustellen. Projektmappenkonfigurationen definieren, wie die Projekte im Projektmappen-Explorer erstellt und bereitgestellt werden. Bei Projektkonfigurationen handelt es sich um einen Satz von Projekteigenschaften, die für eine Plattform und einen Buildtyp eindeutig sind (beispielsweise die Win32-Version). Sie können diese Standardkonfigurationen bearbeiten, und Sie können eigene Konfigurationen erstellen. Weitere Informationen finden Sie unter [Einführung in den Projekt-Designer](https://msdn.microsoft.com/898dd854-c98d-430c-ba1b-a913ce3c73d7) und [NICHT IM BUILD: Gewusst wie: Ändern von Projekteigenschaften und Konfigurationseinstellungen](https://msdn.microsoft.com/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67).

 Aus der IDE können Sie die folgenden zusätzlichen Aufgaben ausführen:

- [Ändern Sie das Buildausgabeverzeichnis](../ide/how-to-change-the-build-output-directory.md).

- [Identifizieren von Projekten, die zum ordnungsgemäßen Erstellen von der Ausgabe eines anderen Projekt abhängig sind](../ide/how-to-create-and-remove-project-dependencies.md).

- [Ändern der Informationsmenge, die im Buildprotokoll oder im Ausgabefenster für Builds enthalten ist](../ide/how-to-view-save-and-configure-build-log-files.md).

- [Ausblenden bestimmter Compilerwarnungen für Visual C#, Visual C++ oder Visual Basic](../ide/how-to-suppress-compiler-warnings.md).

- [Angeben benutzerdefinierter Aktionen für das Vor- und Nachkompilieren eines Builds](../ide/specifying-custom-build-events-in-visual-studio.md).

- Verbessern der Buildleistung mithilfe von parallelen Builds. Weitere Informationen finden Sie unter [Paralleles Erstellen von mehreren Projekten](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md) oder im Blogbeitrag [Tuning C++ build parallelism](https://blogs.msdn.microsoft.com/msbuild/2010/03/07/tuning-c-build-parallelism-in-vs2010/) (Optimieren des parallelen Erstellens für C++).

## <a name="see-also"></a>Weitere Informationen
 [Exemplarische Vorgehensweise: Erstellen einer Anwendung](../ide/walkthrough-building-an-application.md) [Grundlagen der Buildkonfiguration](../ide/understanding-build-configurations.md) [Grundlagen zu Buildplattformen](../ide/understanding-build-platforms.md) [erstellen (Kompilieren) Websiteprojekte](https://msdn.microsoft.com/library/a9cbb88c-8fff-4c67-848b-98fbfd823193) [So wird es gemacht: Erstellen und Entfernen von Projektabhängigkeiten](../ide/how-to-create-and-remove-project-dependencies.md)
