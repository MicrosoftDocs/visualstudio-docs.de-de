---
title: Erste Schritte mit Visual Studio-Tools für Unity | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie Visual Studio für die Unity-Entwicklung installieren und einrichten.
ms.custom: ''
ms.date: 01/27/2021
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: how-to
ms.assetid: 66b5b4eb-13b5-4071-98d2-87fafa4598a8
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
zone_pivot_groups: platform
ms.openlocfilehash: e05a94ecf9cf690f46299684c82f2b3961a783c8
ms.sourcegitcommit: 585547ea7363ab1b6bb9d41f6d008cbe478d1a3b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/27/2021
ms.locfileid: "98912567"
---
# <a name="get-started-with-visual-studio-and-unity"></a>Einstieg in Visual Studio und Unity

> [!NOTE]
> In dieser Anleitung wird davon ausgegangen, dass Sie Unity bereits mit dem Unity-Hub-Programm installiert haben Wenn Sie noch nicht mit Unity vertraut sind, empfehlen wir Ihnen, Unity Learn zu besuchen und zuerst den [Unity Essentials-Lernpfad](https://learn.unity.com/pathway/unity-essentials) abzuschließen.

## <a name="install-unity-support-for-visual-studio"></a>Installieren der Unity-Unterstützung für Visual Studio

Visual Studio-Tools für Unity ist eine kostenlose Erweiterung, die Unterstützung für das Schreiben und Debuggen von c# und mehr bietet. Eine komplette Liste der Erweiterungen finden Sie in der [Übersicht über die Tools für Unity](./visual-studio-tools-for-unity.md) .

:::zone pivot="windows"

> [!NOTE]
> Dieses Installationshandbuch ist für Visual Studio vorgesehen. Wenn Sie Visual Studio Code verwenden, besuchen Sie die [Dokumentation zur Unity-Entwicklung mit vs Code](https://code.visualstudio.com/docs/other/unity).

1. [Laden Sie den Visual Studio-Installer herunter](/visualstudio/docs/install/install-visual-studio.md), oder führen Sie ihn aus, wenn er bereits installiert
2. Klicken Sie für die gewünschte Version von Visual Studio auf **Ändern** (sofern bereits installiert) oder **Installieren** (für neue Installationen).
3. Scrollen Sie auf der Registerkarte **Arbeits Auslastungen** zum Abschnitt **Gaming** , und wählen Sie die Arbeitsauslastung **Spieleentwicklung mit Unity** aus.

    ![Feld "Spieleentwicklung mit Unity-Arbeitsauslastung" im Installer](../media/vs/unity-workload.png)

:::zone-end
:::zone pivot="macos"

> [!NOTE]
> Dieses Installationshandbuch ist für Visual Studio für Mac. Wenn Sie Visual Studio Code verwenden, besuchen Sie die [Dokumentation zur Unity-Entwicklung mit vs Code](https://code.visualstudio.com/docs/other/unity).

Tools für Unity sind in der Installation von Visual Studio für Mac enthalten, und es sind keine separaten Installationsschritte erforderlich. Sie können dies im Menü **Visual Studio für Mac > Extensions > Spieleentwicklung** überprüfen. **Visual Studio für Mac Tools für Unity** sollten aktiviert werden.

![Erweiterungs-Manager-Ansicht mit aktivierten Visual Studio für Mac Tools für Unity](../media/vsm/unity-workload.png)

:::zone-end

## <a name="check-for-updates"></a>Suchen nach Updates

Es wird empfohlen, Visual Studio und Visual Studio für Mac zu aktualisieren, damit Sie über die neuesten Fehlerbehebungen, Features und Unity-Unterstützung verfügen. Dies erfordert keine Aktualisierung der Unity-Versionen.

:::zone pivot="windows"

1. Klicken Sie auf das Menü **Hilfe > nach Updates suchen** .

    ![Menü "nach Updates suchen" in Visual Studio 2019](../media/vs/check-for-updates.png)

2. Wenn ein Update verfügbar ist, wird in der Visual Studio-Installer eine neue Version angezeigt. Klicken Sie auf die Schaltfläche **Aktualisieren**.

:::zone-end
:::zone pivot="macos"

1. Klicken Sie auf das Menü **Visual Studio für Mac > nach Updates suchen...** , um das **Visual Studio-Update** Dialogfeld zu öffnen.
2. Wenn ein Update verfügbar ist, klicken Sie auf die Schaltfläche **Installieren** .

:::zone-end

## <a name="configure-unity-to-use-visual-studio"></a>Konfigurieren von Unity für die Verwendung von Visual Studio

Standardmäßig sollte Unity bereits für die Verwendung von Visual Studio oder Visual Studio für Mac als Skript-Editor konfiguriert sein. Sie können dies bestätigen oder den externen Skript-Editor in eine bestimmte Version von Visual Studio über den Unity-Editor ändern.

:::zone pivot="windows"

1. Wählen Sie im Unity-Editor das Menü **> Einstellungen bearbeiten** aus.
2. Wählen Sie auf der linken Seite die Registerkarte **externe Tools** aus.
3. Die Dropdown Liste **externer Skript-Editor** bietet eine Möglichkeit, verschiedene Installationen von Visual Studio auszuwählen. Sie können auch in der Dropdown Liste auf **Durchsuchen** klicken, um eine nicht aufgelistete Version hinzuzufügen.

    ![Das Einstellungsmenü "externe Tools" im Unity-Editor unter Windows](../media/vs/preferences-external-tools.png)

4. Navigieren Sie bei Auswahl von **Durchsuchen...** zum Verzeichnis **Common7/IDE** in Ihrem Visual Studio-Installationsverzeichnis, und wählen Sie **devenv.exe** aus. Klicken Sie anschließend auf **Öffnen**.
5. Sobald Visual Studio in der Liste **Externer Skript-Editor** ausgewählt ist, überprüfen Sie, ob das Kontrollkästchen **Editoranhängen** aktiviert ist.
6. Schließen Sie das Dialogfeld **Einstellungen**, um die Konfiguration abzuschließen.

:::zone-end
:::zone pivot="macos"

1. Wählen Sie im Unity-Editor das Menü **Unity > Einstellungen** aus.
2. Wählen Sie auf der linken Seite die Registerkarte **externe Tools** aus.
3. Die Dropdown Liste **externer Skript-Editor** bietet eine Möglichkeit, verschiedene Installationen von Visual Studio auszuwählen. Sie können auch in der Dropdown Liste auf **Durchsuchen** klicken, um eine nicht aufgelistete Version hinzuzufügen.

    ![Das Einstellungsmenü "externe Tools" im Unity-Editor unter macOS](../media/vsm/preferences-external-tools.png)

4. Schließen Sie das Dialogfeld **Einstellungen**, um die Konfiguration abzuschließen.

:::zone-end

## <a name="next-steps"></a>Nächste Schritte

 Informationen zum Arbeiten mit und Debuggen Ihres Unity-Projekts in Visual Studio finden Sie unter [Verwenden von Visual Studio-Tools für Unity](using-visual-studio-tools-for-unity.md).
