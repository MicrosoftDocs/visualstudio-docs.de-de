---
title: Grundlagen der Buildkonfiguration
description: Hier erfahren Sie, dass Sie Buildkonfigurationen benötigen, wenn Sie Ihre Projekte mit unterschiedlichen Einstellungen in Visual Studio kompilieren müssen.
ms.custom: SEO-VS-2020
ms.date: 01/20/2020
ms.technology: vs-ide-compile
ms.topic: conceptual
f1_keywords:
- SolutionProperties.ActiveConfig
- vs.build.newprojectconfiguration
- vc.proj.configurationsctrl.multipleconfigs
- vs.build.editsolutionconfigurations
- vs.build.editprojectconfigurations
- vs.multipleconfigurations
- vs.build.newsolutionconfiguration
- VS.ConfigurationManager
- VS.MultipleConfig
helpviewer_keywords:
- solution build configurations, about build configurations
- build configurations
- project build configurations
- build configurations, advanced
- projects [Visual Studio], build configuration
- solutions [Visual Studio], build configuration
ms.assetid: 934c727d-3a22-429c-bd13-3552cecf2e24
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3c6037bd6ed3b7899ff00bce202df7707356683a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971400"
---
# <a name="understand-build-configurations"></a>Grundlagen der Buildkonfiguration

Sie benötigen Buildkonfigurationen, wenn Sie Ihre Projekte mit unterschiedlichen Einstellungen kompilieren müssen. **Debug** und **Release** beispielsweise sind Konfigurationen, bei denen zum Kompilieren verschiedene Compileroptionen verwendet werden.  Eine Konfiguration ist aktiv und wird in der Befehlsleiste oben in der IDE angezeigt.

![Aktive Konfiguration](media/understanding-build-configurations/active-config.png)

> [!NOTE]
> Dieses Thema gilt für Visual Studio unter Windows. Informationen zu Visual Studio für Mac finden Sie unter [Buildkonfigurationen in Visual Studio für Mac](/visualstudio/mac/configurations).

Konfiguration und Plattform steuern, wo die kompilierten Ausgabedateien gespeichert werden. Wenn Visual Studio ein Projekt kompiliert, wird die Ausgabe in der Regel in einem Projektunterordner platziert, der gemäß der aktiven Konfiguration benannt ist (z. B. *bin/Debug/x86*). Dieses Verhalten kann jedoch geändert werden.

Sie können eigene Buildkonfigurationen auf Projektmappen- und Projektebene erstellen. Die Projektmappenkonfiguration bestimmt, welche Projekte im Build enthalten sind, wenn diese Konfiguration aktiv ist. Es werden nur diejenigen Projekte kompiliert, die in der aktiven Projektmappenkonfiguration angegeben sind. Wenn im Konfigurations-Manager mehrere Plattformen ausgewählt werden, werden alle Projekte für diese Plattform kompiliert. Die Projektkonfiguration bestimmt, welche Buildeinstellungen und Compileroptionen beim Kompilieren des Projekts verwendet werden.

Konfiguration können mit **Configuration Manager** ausgewählt, geändert oder gelöscht werden. Wählen Sie zum Öffnen in der Menüleiste **Erstellen** > **Konfigurations-Manager** aus, oder geben Sie im Suchfeld einfach den Begriff **Konfiguration** ein. Sie können auch die Liste **Projektmappenkonfigurationen** auf der Symbolleiste **Standard** zum Auswählen einer Konfiguration verwenden, oder Sie öffnen den **Configuration Manager**.

![Konfigurations-Manager](media/understanding-build-configurations/config-manager.png)

> [!NOTE]
> Falls auf der Symbolleiste keine Einstellungen für Projektmappenkonfigurationen enthalten sind und Sie nicht auf den **Configuration Manager** zugreifen können, sind möglicherweise [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] Entwicklungseinstellungen aktiviert. Weitere Informationen finden Sie unter [Vorgehensweise: Verwalten von Buildkonfigurationen mit aktivierten Visual Basic Developer-Einstellungen](../ide/how-to-manage-build-configurations-with-visual-basic-developer-settings-applied.md).

Standardmäßig sind die Konfigurationen **Debug** und **Release** in Projekten, die mithilfe von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Vorlagen erstellt werden, enthalten. Eine **Debug**-Konfiguration unterstützt das Debuggen einer App, und mit einer **Release**-Konfiguration wird eine Version der App kompiliert, die bereitgestellt werden kann. Weitere Informationen finden Sie unter [Vorgehensweise: Festlegen von Debug- und Releasekonfigurationen](../debugger/how-to-set-debug-and-release-configurations.md). Sie können zudem benutzerdefinierte Projektmappenkonfigurationen und Projektkonfigurationen erstellen. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen und Bearbeiten von Konfigurationen](../ide/how-to-create-and-edit-configurations.md).

## <a name="solution-configurations"></a>Projektmappenkonfigurationen

Mit einer Projektmappenkonfiguration wird festgelegt, wie bestimmte Projekte in der Projektmappe erstellt und bereitgestellt werden. Um eine Projektmappenkonfiguration zu ändern oder eine neue, in **Configuration Manager**, unter **Konfiguration der aktuellen Projektmappe** zu definieren, wählen Sie **Neu** oder **Bearbeiten** aus.

Jeder Eintrag im Feld **Projektkontexte** in einer Projektmappenkonfiguration stellt ein Projekt der Projektmappe dar. Für jede Kombination von **Konfiguration der aktuellen Projektmappe** und **Aktive Projektmappenplattform** können Sie die Verwendungsart des Projekts festlegen. (Weitere Informationen zu Projektmappenplattformen finden Sie unter [Grundlagen zu Buildplattformen](../ide/understanding-build-platforms.md).)

Wenn Sie eine neue Projektmappenkonfiguration definieren und das Kontrollkästchen **Neue Projektkonfigurationen erstellen** aktivieren, weist [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] die neue Konfiguration allen Projekten automatisch zu. Dem entsprechend wird die neue Plattform von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] allen Projekten automatisch zugewiesen, wenn Sie eine neue Plattformkonfiguration definieren und das Kontrollkästchen **Neue Projektplattformen erstellen** aktivieren. Wenn Sie ein Projekt hinzufügen, das auf neue Plattform ausgerichtet ist, wird diese Plattform in Visual Studio der Liste der Projektmappenplattformen hinzugefügt und allen Projekten zugewiesen. Sie können die Einstellungen für jedes Projekt weiterhin ändern.

Die aktive Projektmappenkonfiguration stellt der IDE auch Kontext bereit. Wenn Sie z.B. an einem Projekt arbeiten und in der Konfiguration angegeben ist, dass es für ein mobiles Gerät erstellt wird, werden in der **Toolbox** nur die Elemente angezeigt, die in einem Projekt für ein mobiles Gerät verwendet werden können.

## <a name="project-configurations"></a>Projektkonfigurationen

Die Konfiguration und die Plattform, auf die ein Projekt ausgerichtet ist, legen gemeinsam fest, welche Buildeinstellungen und Compileroptionen beim Kompilieren verwendet werden sollen. Ein Projekt kann für jede Kombination aus Konfiguration und Plattform über unterschiedliche Einstellungen verfügen. Um die Eigenschaften eines Projekts zu ändern, öffnen Sie das Kontextmenü für das Projekt im **Projektmappen-Explorer**, und klicken Sie dann auf **Eigenschaften**.  Wählen Sie im Projekt-Designer oben auf der Registerkarte **Build** eine aktive Konfiguration aus, um die zugehörigen Buildeinstellungen zu bearbeiten.

![Konfigurationen im Projekt-Designer](media/understanding-build-configurations/project-designer-configuration.png)

## <a name="building-multiple-configurations"></a>Erstellen mehrerer Konfigurationen

Wenn Sie eine Projektmappe mit dem Befehl **Erstellen** > **Projektmappe erstellen** kompilieren, erstellt Visual Studio nur die aktive Konfiguration. Alle in dieser Projektmappenkonfiguration angegebenen Projekte werden erstellt, und die einzige erstellte Projektkonfiguration ist die in der aktiven Projektmappenkonfiguration und der aktiven Projektmappenplattform angegebene Konfiguration, die in der Symbolleiste von Visual Studio angezeigt wird. Beispielsweise **Debug** und **x86**. Weitere definierte Konfigurationen und Plattformen werden nicht erstellt.

Wenn Sie mehrere Konfigurationen und Plattformen in einer Aktion erstellen möchten, können Sie die Option **Erstellen** > **Batch erstellen** in Visual Studio verwenden. Um auf dieses Feature zuzugreifen, drücken Sie **STRG**+**Q**, um das Suchfeld zu öffnen, und geben `Batch build` ein. Der Befehl „Batch erstellen“ ist nicht für alle Projekttypen verfügbar. Weitere Informationen finden Sie unter [How to: Gleichzeitiges Erstellen mehrerer Konfigurationen](how-to-build-multiple-configurations-simultaneously.md)

## <a name="how-visual-studio-assigns-project-configurations"></a>Zuweisen von Projektkonfigurationen in Visual Studio

Wenn Sie eine neue Projektmappenkonfiguration definieren und keine Einstellungen von einer vorhandenen kopieren, werden in Visual Studio zum Zuweisen standardmäßiger Projektkonfigurationen die folgenden Kriterien angewendet. Die Kriterien werden in der angezeigten Reihenfolge ausgewertet.

1. Wenn ein Projekte einen Konfigurationsname ( *\<configuration name> \<platform name>* ) enthält, der genau dem Namen der neuen Projektmappenkonfiguration entspricht, wird diese Konfiguration zugewiesen. In Konfigurationsnamen wird die Groß-/Kleinschreibung nicht beachtet.

1. Wenn das Projekt über einen Konfigurationsnamen verfügt, in dem der der Namensteil der Konfiguration der neuen Projektmappenkonfiguration entspricht, wird diese Konfiguration unabhängig des Plattformteils zugewiesen.

1. Gibt es auch danach noch keine Übereinstimmung, wird die erste im Projekt aufgeführte Konfiguration zugewiesen.

## <a name="how-visual-studio-assigns-solution-configurations"></a>Zuweisen von Projektmappenkonfigurationen in Visual Studio

Wenn Sie eine Projektkonfiguration erstellen (indem Sie in **Configuration Manager** im Dropdownmenü der Spalte **Konfiguration** für dieses Projekt die Option **Neu** auswählen) und das Kontrollkästchen **Neue Projektmappenkonfigurationen erstellen** aktivieren, wird in Visual Studio nach einer gleich benannten Projektmappenkonfiguration gesucht, um das Projekt auf jeder davon unterstützten Plattform zu erstellen. In einigen Fällen werden vorhandene Projektmappenkonfigurationen von Visual Studio umbenannt, oder es werden neue definiert.

In Visual Studio werden die folgenden Kriterien für die Zuweisung von Projektmappenkonfigurationen verwendet.

- Wenn in einer Projektkonfiguration keine Plattform oder nur eine einzige Plattform angegeben ist, wird entweder eine Projektmappenkonfiguration gesucht, deren Name dem der neuen Projektkonfiguration entspricht, oder es wird eine solche hinzugefügt. Der Standardname dieser Projektmappenkonfiguration enthält keinen Plattformnamen und weist das Format *\<project configuration name>* auf.

- Wenn von einem Projekt mehrere Plattformen unterstützt werden, wird eine Projektmappenkonfiguration für jede unterstützte Plattform gesucht oder hinzugefügt. Der Name jeder Projektmappenkonfiguration umfasst sowohl den Namen der Projektkonfiguration als auch den Plattformnamen und verfügt über das Format *\<project configuration name> \<platform name>* .

## <a name="see-also"></a>Siehe auch

- [Exemplarische Vorgehensweise: Erstellen einer Anwendung](../ide/walkthrough-building-an-application.md)
- [Kompilieren und Erstellen](../ide/compiling-and-building-in-visual-studio.md)
- [Projektmappen und Projekte](../ide/solutions-and-projects-in-visual-studio.md)
- [C/C++-Buildverweis](/cpp/build/reference/c-cpp-building-reference)
- [Grundlagen zu Buildplattformen](understanding-build-platforms.md)
- [Buildkonfigurationen (Visual Studio für Mac)](/visualstudio/mac/configurations)
