---
title: Laden einer Teilmenge von Projekten
description: Erfahren Sie mehr über Projektmappenfilterung und darüber, wie Sie damit schnell eine Teilmenge von Projekten in eine Projektmappe laden können.
ms.custom: SEO-VS-2020
ms.date: 04/22/2019
ms.prod: visual-studio-dev16
ms.topic: conceptual
helpviewer_keywords:
- filtered solution
- solution filtering
author: jillre
ms.author: stsu
manager: jmartens
monikerRange: '>= vs-2019'
ms.openlocfilehash: eae0d02e1fff3f9ad5b35384e6ccab599805372b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869387"
---
# <a name="filtered-solutions-in-visual-studio"></a>Gefilterte Projektmappen in Visual Studio

Große Entwicklungsteams arbeiten häufig mit einer einzigen großen Projektmappe, die viele Projekten enthält. Einzelne Entwickler arbeiten jedoch in der Regel mit einer kleinen Teilmenge dieser Projekte. Zur Leistungsverbesserung beim Öffnen großer Projektmappen wird in Visual Studio 2019 nun die *Projektmappenfilterung* eingeführt. Mit der Projektmappenfilterung können Sie eine Projektmappe öffnen, in der nur ausgewählte Projekte geladen sind. Durch das Laden einer Teilmenge von Projekten in einer Projektmappe wird die Zeit zum Laden und Erstellen einer Projektmappe sowie für den Testlauf einer Projektmappe verringert. Zudem wird eine zielgerichtetere Überprüfung ermöglicht.

Folgende Funktionen stehen zur Verfügung:

- Sie können Code schneller abrufen, indem Sie eine Projektmappe öffnen, ohne eines der zugehörigen Projekte zu laden. Nachdem die Projektmappe geöffnet wurde, können Sie selektiv auswählen, welche Projekte geladen werden sollen.

- Wenn Sie eine Projektmappe erneut öffnen, merkt sich Visual Studio, welche Projekte in der vorherigen Sitzung geladen wurden, und lädt nur diese Projekte.

- Sie können eine Projektmappenfilterdatei erstellen, um mindestens eine Konfiguration für das Laden von Projekten zu speichern, oder die Konfiguration für Teammitglieder freizugeben.

## <a name="open-a-filtered-solution"></a>Öffnen einer gefilterten Projektmappe

Sie können eine Projektmappe direkt im Dialogfeld **Projekt öffnen** oder über die [Befehlszeile](#command-line) öffnen, ohne ihre Projekte zu laden.

### <a name="open-project-dialog"></a>Dialogfeld „Projekt öffnen“

Um eine Projektmappe zu öffnen, ohne ihre Projekte zu laden, verwenden Sie das Dialogfeld **Projekt öffnen**:

1. Wählen Sie auf der Menüleiste **Datei** > **Öffnen** > **Projekt/Projektmappe** aus.

2. Wählen Sie im Dialogfeld **Projekt öffnen** die Projektmappe und anschließend **Do not load projects** (Projekte nicht laden) aus.

   ![Dialogfeld „Projekt öffnen“ in Visual Studio mit aktivierter Option „Do not load projects“ (Projekte nicht laden)](media/filtered-solutions/do-not-load-projects.png)

3. Wählen Sie **Öffnen** aus.

   Die Projektmappe wird geöffnet, ohne dass sämtliche zugehörigen Projekte geladen werden.

4. Wählen sie im **Projektmappen-Explorer** die Projekte aus, die Sie laden möchten (drücken Sie während des Klickens **STRG**, wenn Sie mehrere Projekte auswählen möchten). Klicken Sie anschließend mit der rechten Maustaste auf das Projekt, und wählen Sie **Projekt erneut laden** aus.

   ![Erneutes Laden mehrerer Projekte in den Projektmappen-Explorer von Visual Studio](media/filtered-solutions/reload-project.png)

   Visual Studio merkt sich, welche Projekte Sie beim nächsten lokalen Öffnen der Projektmappe laden.

### <a name="command-line"></a>Befehlszeile

(Neu in Visual Studio 2019 Version 16.1.)

Um eine Projektmappe über die Befehlszeile zu öffnen, ohne ihre Projekte zu laden, verwenden Sie die Befehlszeilenoption [`/donotloadprojects`](../ide/reference/donotloadprojects-devenv-exe.md) wie im folgenden Beispiel:

```cmd
devenv /donotloadprojects MySln.sln
```

## <a name="toggle-unloaded-project-visibility"></a>Umschalten der Sichtbarkeit von nicht geladener Projekte

Sie können im **Projektmappen-Explorer** mithilfe einer der folgenden Auswahlmöglichkeiten entweder alle Projekte in der Projektmappe oder nur die geladenen Projekte anzeigen:

- Klicken Sie mit der rechten Maustaste auf Ihre Projektmappe, und wählen Sie **Show Unloaded Projects** (Nicht geladene Projekte einblenden) oder **Hide Unloaded Projects** (Nicht geladene Projekte ausblenden) aus.

- Wählen Sie den Projektmappenknoten aus, um die Schaltfläche **Alle Dateien anzeigen** zu aktivieren; klicken Sie auf die Schaltfläche, um die Sichtbarkeit ungeladener Projekte umzuschalten.

   ![Schaltfläche „Alle Dateien anzeigen“ im Projektmappen-Explorer von Visual Studio](media/filtered-solutions/show-all-files.PNG)

## <a name="load-project-dependencies"></a>Laden von Projektabhängigkeiten

In einer Projektmappe, in die nur ausgewählte Projekte geladen werden, sind möglicherweise nicht alle Projektabhängigkeiten eines Projekts geladen. Stellen Sie mit der Menüoption **Projektabhängigkeiten laden** sicher, dass alle Projekte, von denen ein Projekt abhängt, auch geladen werden. Klicken Sie mit der rechten Maustaste im **Projektmappen-Explorer** auf ein oder mehrere geladene Projekte, und wählen Sie **Projektabhängigkeiten laden** aus.

![Laden von Projektabhängigkeiten in Visual Studio 2019](media/filtered-solutions/load-project-dependencies.png)

## <a name="solution-filter-files"></a>Projektmappen-Filterdateien

Wenn Sie Ihre Konfiguration für das Laden von Projekten freigeben oder für die Quellcodeverwaltung committen möchten, können Sie eine Projektmappen-Filterdatei (mit der Erweiterung *SLNF*) erstellen. Wenn Sie eine Projektmappen-Filterdatei öffnen, wird die Projektmappe in Visual Studio geöffnet. In der Projektmappe sind alle angegebenen Projekte geladen und alle nicht geladenen Projekte ausgeblendet. Sie können die Ansicht [umschalten](#toggle-unloaded-project-visibility), sodass die nicht geladenen Projekte angezeigt werden.

Projektmappen-Filterdateien unterscheiden sich visuell von regulären Projektmappendateien durch das zusätzliche Trichtersymbol in dem Symbol neben der Projektmappe im **Projektmappen-Explorer**. Neben dem Namen der Projektmappe werden auch der Name des Filters und die Anzahl der geladenen Projekte angezeigt.

![Im Projektmappen-Explorer von Visual Studio geöffnete Projektmappen-Filterdatei](media/filtered-solutions/solution-filter.PNG)

> [!NOTE]
> Wenn nach der Erstellung der Projektmappen-Filterdatei neue Projekte zur ursprünglichen Projektmappe hinzugefügt werden, werden diese im **Projektmappen-Explorer** als nicht geladene Projekte angezeigt.

### <a name="create-a-solution-filter-file"></a>Erstellen einer Projektmappen-Filterdatei

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf die Projektmappe, und wählen Sie **Save As Solution Filter** (Als Projektmappenfilter speichern) aus.

   ![Menü „Save As Solution Filter“ (Als Projektmappenfilter speichern) im Projektmappen-Explorer von Visual Studio](media/filtered-solutions/save-as-solution-filter.png)

2. Wählen Sie einen Namen und Speicherort für die Projektmappen-Filterdatei aus.

Nachdem Sie eine Projektmappen-Filterdatei erstellt haben, wird diese für den leichteren Zugriff zu Ihrer Liste **Zuletzt geöffnete Projekte und Projektmappen** hinzugefügt:

![„Zuletzt verwendete öffnen“ in Visual Studio](media/filtered-solutions/open-recent.png)

## <a name="see-also"></a>Weitere Informationen

- [Anpassen der Dateischachtelung im Projektmappen-Explorer](file-nesting-solution-explorer.md)
- [Optimieren der Visual Studio-Leistung](optimize-visual-studio-performance.md)
