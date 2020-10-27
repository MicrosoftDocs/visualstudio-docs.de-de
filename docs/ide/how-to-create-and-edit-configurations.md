---
title: 'Vorgehensweise: Erstellen und Bearbeiten von Konfigurationen'
description: Hier erfahren Sie, wie Sie Visual Studio zum Erstellen und Bearbeiten mehrerer Buildkonfigurationen für Ihre Lösung verwenden können.
ms.custom: SEO-VS-2020
ms.date: 06/21/2017
ms.technology: vs-ide-compile
ms.topic: how-to
helpviewer_keywords:
- solution build configurations, editing
- build configurations, creating
- solution build configurations, creating
- build configurations, editing
- builds [Visual Studio], setting up
- property pages
- Configuration Manager
- project build configurations, creating
- project build configurations, editing
ms.assetid: 19be121c-148e-4ece-bbfc-d20b08cfc3f7
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 635fc18965361967269b7260b6abaab279ffb52d
ms.sourcegitcommit: c9a84e6c01e12ccda9ec7072dd524830007e02a3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2020
ms.locfileid: "92136822"
---
# <a name="how-to-create-and-edit-configurations"></a>Vorgehensweise: Erstellen und Bearbeiten von Konfigurationen

Es können mehrere Buildkonfigurationen für eine Projektmappe erstellt werden. Zum Beispiel können Sie ein Debugbuild konfigurieren, das von den Testern zum Suchen und Beheben von Problemen verwendet werden kann, und Sie können unterschiedliche Builds konfigurieren, die Sie an verschiedene Kunden verteilen können.

> [!NOTE]
> Dieses Thema gilt für Visual Studio unter Windows. Informationen zu Visual Studio für Mac finden Sie unter [Erstellen und Bearbeiten von Konfigurationen in Visual Studio für Mac](/visualstudio/mac/create-and-edit-configurations).

## <a name="create-build-configurations"></a>Erstellen von Buildkonfigurationen

Sie können das Dialogfeld **Konfigurations-Manager** verwenden, um neue Buildkonfigurationen zu erstellen oder um vorhandene auszuwählen oder zu ändern.

Öffnen Sie im **Projektmappen-Explorer** das Kontextmenü für die Projektmappe, und klicken Sie dann auf **Konfigurations-Manager** , um das Dialogfeld **Konfigurations-Manager** zu öffnen.

> [!NOTE]
> Wenn der Befehl **Konfigurations-Manager** nicht im Kontextmenü angezeigt wird, suchen Sie auf der Menüleiste im Menü **Erstellen** . Wenn der Befehl dort ebenfalls nicht angezeigt wird, klicken Sie auf der Menüleiste auf **Extras** > **Optionen** , und erweitern Sie anschließend im linken Bereich des Dialogfelds **Optionen** die Optionen **Projekte und Projektmappen** > **Allgemein** , und aktivieren Sie im rechten Bereich das Kontrollkästchen **Erweiterte Buildkonfigurationen anzeigen** .

Sie können im Dialogfeld **Konfigurations-Manager** die Dropdownliste **Konfiguration der aktuellen Projektmappe** verwenden, um eine Projektmappen-weite Buildkonfiguration auszuwählen, eine vorhandene zu ändern oder eine neue Konfiguration zu erstellen. Sie können die Dropdownliste **Aktive Projektmappenplattform** verwenden, um die Plattform auszuwählen, auf die die Konfiguration ausgerichtet ist, eine vorhandene zu ändern, oder eine neue Plattform hinzuzufügen. Im Bereich **Projektkontexte** werden die Projekte in der Projektmappe aufgeführt. Für jedes Projekt können Sie eine projektspezifische Konfiguration und Plattform auswählen, vorhandene ändern oder eine neue Konfiguration erstellen bzw. eine neue Plattform hinzufügen. Sie können auch Kontrollkästchen aktivieren, die angeben, ob jedes Projekt bei Verwendung der Projektmappe-weiten Konfiguration zum Erstellen oder Bereitstellen der Projektmappe eingeschlossen wird.

Nachdem Sie die gewünschte Konfigurationen festgelegt haben, können Sie die für diese Konfigurationen geeigneten Projekteigenschaften festlegen.

### <a name="set-properties-based-on-configurations"></a>Festlegen von Eigenschaften auf der Grundlage von Konfigurationen

Um Eigenschaften auf der Grundlage von Konfigurationen festzulegen, öffnen Sie im **Projektmappen-Explorer** das Kontextmenü für ein Projekt und wählen dann **Eigenschaften** aus. Sie können Eigenschaften für die Konfigurationen festlegen. Bei einer Releasekonfiguration können Sie beispielsweise angeben, dass Code bei Erstellung der Projektmappe optimiert wird, und bei einer Debugkonfiguration können Sie angeben, dass das Symbol `DEBUG` für die bedingte Kompilierung enthalten ist.

Weitere Informationen zu den Einstellungen für die Eigenschaftenseiten finden Sie unter [Verwalten von Projekt- und Projektmappeneigenschaften](../ide/managing-project-and-solution-properties.md).

## <a name="create-a-project-configuration"></a>Erstellen einer Projektkonfiguration

1. Öffnen Sie das Dialogfeld **Konfigurations-Manager** .

2. Wählen Sie in der Spalte **Projekt** ein Projekt aus.

3. Wählen Sie im Dropdownmenü **Konfiguration** für dieses Projekt die Option **Neu** aus.

     Das Dialogfeld **Neue Projektkonfiguration** wird angezeigt.

4. Geben Sie im Feld **Name** einen Namen für die neue Konfiguration ein.

5. Wenn Sie die Eigenschafteneinstellungen aus einer bereits vorhandenen Projektkonfiguration verwenden möchten, wählen Sie eine Konfiguration aus der Dropdownliste **Copy settings from** (Einstellungen kopieren von) aus.

6. Um gleichzeitig eine Projektmappen-weite Konfiguration zu erstellen, aktivieren Sie das Kontrollkästchen **Create new solution configuration** (Neue Projektmappenkonfigurationen erstellen).

## <a name="rename-a-project-configuration"></a>Umbenennen einer Projektkonfiguration

1. Öffnen Sie das Dialogfeld **Konfigurations-Manager** .

2. Wählen Sie in der Spalte **Projekt** das Projekt aus, das über die Projektkonfiguration verfügt, die Sie umbenennen möchten.

3. Wählen Sie im Dropdownmenü **Konfiguration** für dieses Projekt die Option **Bearbeiten** aus.

     Das Dialogfeld **Projektkonfigurationen bearbeiten** wird angezeigt.

4. Markieren Sie den Projektkonfigurationsnamen, den Sie ändern möchten.

5. Wählen Sie **Umbenennen** aus, und geben Sie einen neuen Namen ein.

## <a name="create-and-modify-solution-wide-build-configurations"></a>Erstellen und Ändern von Projektmappen-weiten Buildkonfigurationen

### <a name="to-create-a-solution-wide-build-configuration"></a>So erstellen Sie eine Projektmappen-weite Buildkonfiguration

1. Öffnen Sie das Dialogfeld **Konfigurations-Manager** .

2. Wählen Sie in der Dropdownliste **Konfiguration der aktuellen Projektmappe** die Option **Neu** aus.

     Das Dialogfeld **Neue Projektmappenkonfiguration** wird angezeigt.

3. Geben Sie im Textfeld **Name** einen Namen für die neue Konfiguration ein.

4. Wenn Sie die Einstellungen aus einer bereits vorhandenen Projektmappenkonfiguration verwenden möchten, wählen Sie eine Konfiguration aus der Dropdownliste **Copy settings from** (Einstellungen kopieren von) aus.

5. Um Projektkonfigurationen gleichzeitig zu erstellen, aktivieren Sie das Kontrollkästchen **Neue Projektkonfigurationen erstellen** .

### <a name="to-rename-a-solution-wide-build-configuration"></a>So benennen Sie eine Projektmappen-weite Buildkonfiguration um

1. Öffnen Sie das Dialogfeld **Konfigurations-Manager** .

2. Wählen Sie in der Dropdownliste **Konfiguration der aktuellen Projektmappe** die Option **Bearbeiten** aus.

     Das Dialogfeld **Projektmappenkonfigurationen bearbeiten** wird angezeigt.

3. Markieren Sie den Namen der umzubenennenden Projektmappenkonfiguration.

4. Wählen Sie **Umbenennen** aus, und geben Sie einen neuen Namen ein.

### <a name="to-modify-a-solution-wide-build-configuration"></a>So ändern Sie eine Projektmappen-weite Buildkonfiguration

1. Öffnen Sie das Dialogfeld **Konfigurations-Manager** .

2. Wählen Sie in der Dropdownliste **Konfiguration der aktuellen Projektmappe** die gesuchte Konfiguration aus.

3. Wählen Sie im Bereich **Projektkontexte** für jedes Projekt die gewünschte **Konfiguration** und **Plattform** aus, und klicken Sie auf **Erstellen** oder **Bereitstellen** .

## <a name="see-also"></a>Siehe auch

- [Grundlagen der Buildkonfiguration](../ide/understanding-build-configurations.md)
- [Erstellen und Bereinigen von Projekten und Projektmappen in Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Verwalten von Projekt- und Projektmappeneigenschaften](managing-project-and-solution-properties.md)
- [Erstellen und Bearbeiten von Buildkonfigurationen (Visual Studio für Mac)](/visualstudio/mac/create-and-edit-configurations)
