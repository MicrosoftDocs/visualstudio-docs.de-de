---
title: Erstellen und Bereinigen von Projekten und Projektmappen
description: In diesem Artikel erfahren Sie, wie Sie alle oder beliebige der Projekte oder Projektelemente in einer Projektmappe erstellen, neu erstellen oder bereinigen können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
f1_keywords:
- VS.BuildProjectPicker
- vs.batchbuild
helpviewer_keywords:
- Clean Solution command
- builds [Visual Studio], managing
- solution build configurations, starting
- Build Solution command
- project build configurations, starting
- build configurations, starting
- project build configurations, dependencies
- Rebuild Solution command
- solution build configurations, build order
- builds [Visual Studio], preparing
ms.assetid: 710891fd-379e-42c2-a84b-44a7af694ca0
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d2ab8a723b69f4c5930c91a10719a2107ad83003
ms.sourcegitcommit: c9a84e6c01e12ccda9ec7072dd524830007e02a3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2020
ms.locfileid: "92136796"
---
# <a name="build-and-clean-projects-and-solutions-in-visual-studio"></a>Erstellen und Bereinigen von Projekten und Projektmappen in Visual Studio

Mithilfe der in diesem Thema behandelten Verfahren können Sie alle oder einige Projekte oder Projektelemente in einer Projektmappe erstellen, neu erstellen oder bereinigen. Ein ausführliches Tutorial finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer Anwendung](../ide/walkthrough-building-an-application.md).

> [!NOTE]
> Dieses Thema gilt für Visual Studio unter Windows. Informationen zu Visual Studio für Mac finden Sie unter [Erstellen und Bereinigen von Projekten und Projektmappen in Visual Studio für Mac](/visualstudio/mac/building-and-cleaning-projects-and-solutions).

> [!NOTE]
> In Abhängigkeit der von Ihnen gewählten Einstellungen kann sich die Benutzeroberfläche Ihrer Visual Studio Edition von dem unterscheiden, was in diesem Thema beschrieben wird. Klicken Sie auf **Extras** > **Einstellungen importieren/exportieren** und dann auf **Alle Einstellungen zurücksetzen** , um Ihre Einstellungen z.B. in **Allgemein** oder **Visual C++** zu ändern.

## <a name="to-build-rebuild-or-clean-an-entire-solution"></a>So können Sie eine gesamte Projektmappe erstellen, neu erstellen oder bereinigen

1. Wählen Sie im **Projektmappen-Explorer** die Projektmappe aus, oder öffnen Sie sie.

2. Wählen Sie dann auf der Menüleiste **Erstellen** , gefolgt von einem der folgenden Befehle aus:

    - Wählen Sie **Erstellen** oder **Projektmappe erstellen** aus, um nur diejenigen Projektdateien und Komponenten zu kompilieren, die sich seit dem letzten Build geändert haben.

        > [!NOTE]
        > Der Befehl **Erstellen** wandelt sich in **Projektmappe erstellen** , wenn eine Projektmappe mehr als ein Projekt enthält.

    - Wählen Sie **Projektmappe neu erstellen** aus, um die Projektmappe zu „bereinigen“ und anschließend alle Projektdateien und Komponenten zu erstellen.

    - Wählen Sie **Projektmappe bereinigen** aus, um alle eventuellen Interims- und Ausgabedateien zu löschen. Dann bleiben nur die Projekt- und Komponentendateien übrig, und neue Instanzen der Interims- und Ausgabedateien können erstellt werden.

## <a name="to-build-or-rebuild-a-single-project"></a>So erstellen Sie ein einzelnes Projekt oder erstellen es neu

1. Wählen Sie im **Projektmappen-Explorer** das Projekt aus, oder öffnen Sie es.

2. Wählen Sie in der Menüleiste **Erstellen** und dann entweder **Projektname** *erstellen* oder **Projektname** *neu erstellen* aus.

    - Wählen Sie **Projektname** *erstellen* aus, um nur die Projektkomponenten zu erstellen, die sich seit dem letzten Build geändert haben.

    - Wählen Sie **Projektname** *neu erstellen* aus, um das Projekt zu „bereinigen“ und dann die Projektdateien und alle Projektkomponenten zu erstellen.

## <a name="to-build-only-the-startup-project-and-its-dependencies"></a>So erstellen Sie nur das Startprojekt und seine Abhängigkeiten

1. Klicken Sie in der Menüleiste auf **Extras** > **Optionen** .

2. Klappen Sie im Dialogfeld **Optionen** den Knoten **Projekte und Projektmappen** auf, und wählen Sie dann die Seite **Erstellen und Ausführen** aus.

     Das Dialogfeld **Erstellen und Ausführen** > **Projekte und Projektmappen** > **Optionen** wird geöffnet.

3. Aktivieren Sie das Kontrollkästchen **Nur Startprojekte und Abhängigkeiten zur Laufzeit ausführen** .

     Wenn dieses Kontrollkästchen aktiviert ist, werden nur das aktuelle Startprojekt und seine Abhängigkeiten erstellt, wenn Sie einen der folgenden Schritte ausführen:

    - Wählen Sie auf der Menüleiste **Debuggen** > **Starten** ( **F5** ) aus.

    - Wählen Sie auf der Menüleiste **Erstellen** > **Projektmappe erstellen** ( **STRG**+**UMSCHALT**+**B** )aus.

    Wenn dieses Kontrollkästchen deaktiviert ist, werden alle Projekte, ihre Abhängigkeiten und die Projektmappendateien erstellt, wenn Sie einen der vorstehenden Befehle ausführen. Standardmäßig ist dieses Kontrollkästchen deaktiviert.

## <a name="to-build-only-the-selected-visual-c-project"></a>So erstellen Sie nur das ausgewählte Visual C++-Projekt

Wählen Sie ein [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]-Projekt aus, und wählen Sie dann auf der Menüleiste **Erstellen** > **Nur Projekt** und einen der folgenden Befehle aus:

- **Projektname** *nur erstellen*

- **Projektname** *nur neu erstellen*

- **Projektname** *nur bereinigen*

- **Projektname** *nur verknüpfen*

Diese Befehle betreffen nur das ausgewählte [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]-Projekt, d.h. Projektabhängigkeiten oder Projektmappendateien werden nicht erstellt, neu erstellt, bereinigt oder gelinkt. Abhängig von Ihrer Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] enthält das Untermenü **Nur Projekt** möglicherweise noch weitere Befehle.

## <a name="to-compile-multiple-c-project-items"></a>So kompilieren Sie mehrere C++-Projektelemente

Wählen Sie im **Projektmappen-Explorer** mehrere Dateien aus, die kompilierbare Aktionen aufweisen, öffnen Sie das Kontextmenü für eine dieser Dateien, und wählen Sie dann **Kompilieren** aus.

Wenn die Dateien Abhängigkeiten aufweisen, werden die Dateien in der Reihenfolge der Abhängigkeit kompiliert. Beim Kompilieren tritt ein Fehler auf, wenn für die Dateien ein vorkompilierter Header erforderlich ist, der zum Zeitpunkt des Kompilierens nicht verfügbar ist. Der Kompiliervorgang verwendet die aktuelle Konfiguration der aktiven Projektmappe.

## <a name="to-stop-a-build"></a>So beenden Sie einen Build

Führen Sie einen der folgenden Schritte aus:

- Wählen Sie auf der Menüleiste **Erstellen** > **Abbrechen** aus.

- Drücken Sie **STRG**+**Pause** .

## <a name="see-also"></a>Siehe auch

- [How to: Anzeigen, Speichern und Konfigurieren von Buildprotokolldateien](../ide/how-to-view-save-and-configure-build-log-files.md)
- [Erhalten von Buildprotokollen](../msbuild/obtaining-build-logs-with-msbuild.md)
- [Kompilieren und Erstellen](../ide/compiling-and-building-in-visual-studio.md)
- [Grundlagen der Buildkonfiguration](../ide/understanding-build-configurations.md)
- [Vorgehensweise: Set debug and release configurations (Vorgehensweise: Festlegen von Debug- und Releasekonfigurationen)](../debugger/how-to-set-debug-and-release-configurations.md)
- [Referenz zur C/C++-Erstellung](/cpp/build/reference/c-cpp-building-reference)
- [Devenv-Befehlszeilenschalter](../ide/reference/devenv-command-line-switches.md)
- [Projektmappen und Projekte](../ide/solutions-and-projects-in-visual-studio.md)
- [Erstellen und Bereinigen von Projekten und Projektmappen (Visual Studio für Mac)](/visualstudio/mac/building-and-cleaning-projects-and-solutions)
