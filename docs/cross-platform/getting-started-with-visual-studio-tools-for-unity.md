---
title: Erste Schritte mit Visual Studio-Tools für Unity | Microsoft-Dokumentation
description: In diesem Artikel erhalten Sie Informationen zu den ersten Schritten mit Visual Studio-Tools für Unity. Außerdem erfahren Sie, wie Sie Visual Studio installieren und Unity für die Verwendung mit Visual Studio konfigurieren, und Sie erhalten Informationen zur Unterstützung für ältere Versionen.
ms.custom: ''
ms.date: 05/11/2020
ms.technology: vs-unity-tools
ms.topic: how-to
ms.assetid: 66b5b4eb-13b5-4071-98d2-87fafa4598a8
author: indiesaudi
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 223458a448a4b32c3e9480f7189d5dc636ce8375
ms.sourcegitcommit: 01c1b040b12d9d43e3e8ccadee20d6282154faad
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/14/2020
ms.locfileid: "92039450"
---
# <a name="get-started-with-visual-studio-tools-for-unity"></a>Erste Schritte mit Visual Studio-Tools für Unity

## <a name="install-visual-studio"></a>Installieren von Visual Studio

### <a name="unity-bundled-installation"></a>Gebündelte Installation von Unity

Ab Unity 2018.1 ist Visual Studio der standardmäßige C#-Skript-Editor-IDE für Unity und im Unity-Download-Assistenten sowie im Unity Hub-Installationstool enthalten.

- Laden Sie Unity unter [store.unity.com](https://store.unity.com/) herunter.

Stellen Sie während der Installation sicher, dass Visual Studio in der Liste der Komponenten ausgewählt ist, die mit Unity installiert werden sollen:

#### <a name="unity-hub"></a>Unity Hub

:::moniker range="vs-2017"
![Installation von Unity Hub](media/vs-2017/vstu-unity-hub.png)
:::moniker-end
:::moniker range=">=vs-2019"
![Installation von Unity Hub](media/vs-2019/vstu-unity-hub.png)
:::moniker-end

:::moniker range="vs-2017"

#### <a name="unity-download-assistant"></a>Unity-Download-Assistent

![Installation mit dem Unity-Download-Assistenten](media/vs-2017/vstu-download-assistant.png)

Die Version von Visual Studio, die in der Installation von Unity enthalten ist, ist möglicherweise nicht aktuell. Wenn Sie aufgefordert werden, Visual Studio 2017 zu installieren, empfiehlt es sich, eine neuere Version von Visual Studio manuell zu installieren.
:::moniker-end

### <a name="manual-installation"></a>Manuelle Installation

Wenn Sie Visual Studio bereits installiert haben oder eine manuelle Installation bevorzugen, führen Sie den Visual Studio-Installer aus.

1. [Laden Sie den Visual Studio-Installer herunter](../install/install-visual-studio.md), oder öffnen Sie ihn, wenn er bereits installiert ist.

1. Klicken Sie für die gewünschte Version von Visual Studio auf **Ändern** (sofern bereits installiert) oder **Installieren** (für neue Installationen).

1. Scrollen Sie auf der Registerkarte **Workloads** zum Abschnitt **Mobil und Gaming** , und wählen Sie die Workload **Spieleentwicklung mit Unity** aus.

   :::moniker range="vs-2017"
   ![Unity-Workload](media/vs-2017/vstu-unity-workload.png)
   :::moniker-end
   :::moniker range=">=vs-2019"
   ![Unity-Workload](media/vs-2019/vstu-unity-workload.png)
   :::moniker-end

1. Klicken Sie in der unteren rechten Ecke des Installer-Fensters auf **Ändern** (sofern bereits installiert) oder **Installieren** (für neue Installationen).

#### <a name="check-for-updates-to-visual-studio"></a>Suchen nach Updates für Visual Studio

Es wird empfohlen, nach Updates innerhalb von Visual Studio zu suchen, um sicherzustellen, dass Sie Zugriff auf die aktuellen Tools und Features haben. Dadurch wird das Unity-Projekt nicht fehlerhaft.

- [Visual Studio aktualisieren](../install/update-visual-studio.md)

## <a name="configure-unity-for-use-with-visual-studio"></a>Konfigurieren von Unity für die Verwendung mit Visual Studio

Ab Unity 2018.1 sollte Visual Studio als Standard für den externen Skript-Editor in Unity festgelegt sein. Sie können dies bestätigen oder den externen Skript-Editor in eine spezifische Version von Visual Studio ändern:

1. Wählen Sie im Menü **Bearbeiten** die Option **Einstellungen...** aus.

   :::moniker range="vs-2017"
   ![Auswählen von Einstellungen](media/vs-2017/vstu-unity-preferences.png)
   :::moniker-end
   :::moniker range=">=vs-2019"
   ![Auswählen von Einstellungen](media/vs-2019/vstu-unity-preferences.png)
   :::moniker-end

2. Klicken Sie im Dialogfeld "Einstellungen" auf die Registerkarte **Externe Tools** .

3. Wählen Sie in der Dropdownliste **Externer Skript-Editor** Ihre gewünschte Version von Visual Studio aus, falls diese aufgelistet ist, oder andernfalls **Durchsuchen...**

   :::moniker range="vs-2017"
   ![Auswählen von Visual Studio](media/vs-2017/vstu-unity-external-tools.png)
   :::moniker-end
   :::moniker range=">=vs-2019"
   ![Auswählen von Visual Studio](media/vs-2019/vstu-unity-external-tools.png)
   :::moniker-end

4. Navigieren Sie bei Auswahl von **Durchsuchen...** zum Verzeichnis **Common7/IDE** in Ihrem Visual Studio-Installationsverzeichnis, und wählen Sie **devenv.exe** aus. Klicken Sie dann auf **Öffnen** .

   :::moniker range="vs-2017"
   ![Auswählen von „Öffnen“](media/vs-2017/vstu-browse-for-application.png)
   :::moniker-end
   :::moniker range=">=vs-2019"
   ![Auswählen von „Öffnen“](media/vs-2019/vstu-browse-for-application.png)
   :::moniker-end

5. Sobald Visual Studio in der Liste **Externer Skript-Editor** ausgewählt ist, überprüfen Sie, ob das Kontrollkästchen **Editoranhängen** aktiviert ist.

6. Schließen Sie das Dialogfeld **Einstellungen** , um die Konfiguration abzuschließen.

## <a name="support-for-older-versions"></a>Unterstützung älterer Versionen

Laden Sie Visual Studio-Tools für Unity aus dem Visual Studio Marketplace herunter, und installieren Sie sie. Sie müssen das richtige Paket für Ihre Version von Visual Studio installieren.

- Für Visual Studio 2015 Community, Visual Studio 2015 Professional oder Visual Studio 2015 Enterprise:

   [Visual Studio 2015-Tools für Unity herunterladen](https://marketplace.visualstudio.com/items?itemName=SebastienLebreton.VisualStudio2015ToolsforUnity)

> [!NOTE]
> Visual Studio-Tools für Unity setzt Unity 5.2 und höher voraus sowie eine Version von Visual Studio, die Erweiterungen unterstützt (z.B. Visual Studio Community, Professional, Premium oder Enterprise). Überprüfen Sie, ob Visual Studio-Tools für Unity in Ihrer Installation von Unity aktiviert sind, indem Sie im **Hilfemenü** die Option **Informationen zu Unity** auswählen und unten links im Dialogfeld nach dem Text „Microsoft Visual Studio-Tools für Unity aktiviert“ suchen.
> ![Informationen zu Unity](media/vs-2019/vstu-about-unity.png)

## <a name="next-steps"></a>Nächste Schritte

 Informationen zum Arbeiten mit und Debuggen von Unity-Projekten in Visual Studio finden Sie unter [Verwenden von Visual Studio-Tools für Unity](../cross-platform/using-visual-studio-tools-for-unity.md).
