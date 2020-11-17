---
title: Visual Studio-Tools für Unity | Microsoft-Dokumentation
description: Hier finden Sie eine Übersicht über die Visual Studio-Tools für Unity. Dabei handelt es sich um eine kostenlose Visual Studio-Erweiterung, die Sie dabei unterstützt, plattformübergreifende Spiele und Apps mit Unity zu entwickeln.
ms.custom: ''
ms.date: 10/25/2019
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: overview
ms.assetid: 6cabc626-5310-4622-a743-210a9abb5535
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: ee4e9e0dc9df4eb5decb3fc9c2afb0411e9cb75c
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2020
ms.locfileid: "93405380"
---
# <a name="visual-studio-tools-for-unity"></a>Visual Studio Tools für Unity
![Visual Studio Tools für Unity](../media/hero.png)

## <a name="overview"></a>Übersicht
Visual Studio-Tools für Unity ist eine kostenlose Erweiterung, die Visual Studio zu einem leistungsstarken Tool zur Entwicklung plattformübergreifender Spiele mit Unity macht.

Der Unity-Editor eignet sich hervorragend für das Zusammensetzen Ihres Spiels, bietet aber keine Möglichkeit, Code zu schreiben. Mit Visual Studio-Tools für Unity können Sie die vertrauten Codebearbeitungs-, Debugging- und Produktivitätsfunktionen von Visual Studio nutzen, um Editor- und Spielskripts für Ihr Unity-Projekt mithilfe von C# zu erstellen. Darüber hinaus können Sie die leistungsstarken Debuggingfunktionen von Visual Studio einsetzen.

Doch Visual Studio-Tools für Unity hat noch mehr zu bieten, nämlich eine umfassende Integration in den Unity-Editor, sodass Sie für das Erledigen einfacher Aufgaben weniger Zeit für das Hin- und Herwechseln benötigen. Hinzu kommen Unity-spezifische Produktivitätsverbesserungen und ein einfacher Zugriff auf die Unity-Dokumentation.

### <a name="compatible-with-visual-studio-community-on-windows-and-macos-and-bundled-with-unity"></a>Kompatibel mit Visual Studio Community unter Windows und macOS sowie im Paket mit Unity
Visual Studio und Visual Studio Community für Mac sind kostenlos verfügbar und in Installationen von Unity enthalten. Weitere Informationen zur Installation und Einrichtung finden Sie in der [Dokumentation zu den ersten Schritten mit Visual Studio-Tools für Unity](getting-started-with-visual-studio-tools-for-unity.md).

## <a name="intellisense-for-unity-messages"></a>IntelliSense für Unity-Nachrichten
Die Codevervollständigung von IntelliSense vereinfacht die [Implementierung von Unity-API-Meldungen](using-visual-studio-tools-for-unity.md#intellisense-for-unity-api-messages) wie `OnCollisionEnter`, einschließlich der Parameter.

![IntelliSense-Dialogfenster mit OnCollisionEnter](../media/vs/intellisense-example.png)

## <a name="superior-debugging"></a>Leistungsstarkes Debugging
Visual Studio-Tools für Unity unterstützt die robusten [Debuggingfunktionen](using-visual-studio-tools-for-unity.md#unity-debugging), die Sie von Visual Studio erwarten:

* Breakpoints setzen, einschließlich bedingter Breakpoints
* Auswertung komplexer Ausdrücke im Überwachungsfenster.
* Überprüfen und Ändern des Werts von Variablen und Argumenten.
* Detailsuchen in komplexen Objekten und Datenstrukturen.

![Anhalten bei einem Breakpoint zum Untersuchen von Variablen](../media/vs/debugging-inspecting.png)

## <a name="integrated-suggestions-for-best-practices-and-performance-insights"></a>Integrierte Vorschläge für bewährte Methoden und Leistungserkenntnisse
Profitieren Sie beim Schreiben von Code von den Best Practices, die Visual Studio aufgrund der umfassenden Unterstützung von Unity-Projekten bietet.

![Zeichenfolgenvergleich beim VS-Refactoring mit CompareTag](../media/vs/unity-diagnostics.png)

## <a name="codelens-support-for-unity-scripts-and-messages"></a>Unterstützung von CodeLens für Unity-Skripts und -Meldungen
Unity-Skript- und -Meldungsfunktionen werden mit Hinweisen versehen, damit Sie leichter erkennen können, was von Unity bereitgestellt wird und was Ihr Code ist.

 ![Neues Skript mit CodeLens-Hinweisen für Unity-Skripts und Unity-Meldungen](../media/vs/codelens-support.png)

> [!NOTE]
> Die Unterstützung für CodeLens ist in Visual Studio 2019 verfügbar.

## <a name="optimized-view-of-all-your-scripts-to-match-unity"></a>Optimierte Ansicht all Ihrer Skripts für die Anpassung an Unity
Der Unity-Projekt-Explorer (UPE) ist eine alternative Möglichkeit anstelle des üblichen Projektmappen-Explorers zum Anzeigen Ihrer Projektdateien. Der Unity-Projekt-Explorer filtert die angezeigten Dateien und stellt diese in einer Hierarchie dar, die Unity entspricht (**Ansicht > Unity-Projekt-Explorer** in Visual Studio 2019).

![Unity-Projekt-Explorer](../media/vs/unity-project-explorer.png)

> [!NOTE]
> Der Unity-Projekt-Explorer ist in Visual Studio 2019 verfügbar. In Visual Studio für Mac weist das Projektmappenpad standardmäßig ein ähnliches Verhalten für Unity-Projekte auf. Es sind keine zusätzlichen Ansichten erforderlich.

* [Erste Schritte mit Visual Studio-Tools für Unity](getting-started-with-visual-studio-tools-for-unity.md)
