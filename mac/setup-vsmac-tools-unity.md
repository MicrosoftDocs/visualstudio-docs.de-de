---
title: Setup von Visual Studio für Mac-Tools für Unity
titleSuffix: ''
ms.custom: SEO-VS-2020
description: Einrichten und Installieren von Unity-Tools für die Verwendung in Visual Studio für Mac
author: therealjohn
ms.author: johmil
ms.date: 06/18/2019
ms.assetid: 83FDD7A3-5D16-4B4B-9080-078E3FB5C623
ms.topic: how-to
ms.openlocfilehash: b516acca7b9e9be2dda72dd22ec3361c523f3d19
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584242"
---
# <a name="set-up-visual-studio-for-mac-tools-for-unity"></a>Einrichten von Visual Studio für Mac-Tools für Unity

In diesem Abschnitt werden die ersten Schritte für die Verwendung von Visual Studio für Mac-Tools für Unity erläutert.

## <a name="install-visual-studio-for-mac"></a>Installieren von Visual Studio für Mac

### <a name="unity-bundled-installation"></a>Gebündelte Installation von Unity

Ab Unity 2018.1 ist Visual Studio für Mac die C#-Standard-IDE (IDE = Integrated Development Environment, integrierte Entwicklungsumgebung) für Unity und im Unity-Download-Assistenten sowie im Unity Hub-Installationstool enthalten. Laden Sie Unity unter [store.unity.com](https://store.unity.com/) herunter.

Stellen Sie während der Installation sicher, dass Visual Studio für Mac in der Liste der Komponenten ausgewählt ist, die mit Unity installiert werden sollen:

#### <a name="unity-hub"></a>Unity Hub

![Installation von Unity Hub](media/setup-vsmac-tools-unity-image7.png)

#### <a name="unity-download-assistant"></a>Unity-Download-Assistent

![Installation mit dem Unity-Download-Assistenten](media/setup-vsmac-tools-unity-image8.png)

#### <a name="check-for-updates-to-visual-studio-for-mac"></a>Suchen nach Updates für Visual Studio für Mac

Die Version von Visual Studio für Mac, die in der Installation von Unity enthalten ist, ist möglicherweise nicht aktuell. Es wird empfohlen, nach Updates zu suchen, damit Sie Zugriff auf die aktuellen Tools und Features haben.

* [Aktualisieren von Visual Studio für Mac](update.md)

### <a name="manual-installation"></a>Manuelle Installation

Wenn Sie bereits Unity 5.6.1 oder höher installiert haben, Visual Studio für Mac jedoch nicht, können Sie Visual Studio für Mac manuell installieren. Alle Editionen von Visual Studio für Mac enthalten Visual Studio für Mac-Tools für Unity, einschließlich der kostenlosen Community Edition:

* Laden Sie unter [visualstudio.microsoft.com](https://visualstudio.microsoft.com/) Visual Studio für Mac herunter.
* Visual Studio für Mac-Tools für Unity werden automatisch während des Installationsprozesses installiert.
* Weitere Informationen zur Installation finden Sie im [Installationshandbuch](./installation.md).

> [!NOTE]
> Visual Studio für Mac-Tools für Unity erfordert Unity 5.6.1 oder höher. Überprüfen Sie, ob Visual Studio-Tools für Unity in Ihrer Version von Unity aktiviert sind, indem Sie im Unity-Menü auf **About Unity** (Informationen zu Unity) klicken und unten links im Dialogfeld nach dem Text „Visual Studio-Tools für Unity aktiviert“ suchen.
>
> ![Informationen zu Unity](media/setup-vsmac-tools-unity-image3.png)

## <a name="confirm-that-the-visual-studio-for-mac-tools-for-unity-extension-is-enabled"></a>Aktivierung der Erweiterung „Visual Studio für Mac-Tools für Unity“ bestätigen

Obwohl die Erweiterung „Visual Studio für Mac-Tools für Unity“ standardmäßig aktiviert sein sollte, können sie dies bestätigen, indem Sie die installierte Versionsnummer überprüfen:

1. Klicken Sie im Menü von Visual Studio auf **Erweiterungen...** .

   ![Auswählen von Erweiterungen](media/setup-vsmac-tools-unity-image1.png)

2. Erweitern Sie den Abschnitt „Spieleentwicklung“ und bestätigen Sie den Eintrag „Visual Studio für Mac-Tools für Unity“.

   ![Anzeigen des Eintrags „Unity“](media/setup-vsmac-tools-unity-image2.png)

## <a name="configure-unity-for-use-with-visual-studio-for-mac"></a>Konfigurieren von Unity für die Verwendung mit Visual Studio für Mac

Ab Unity 2018.1 sollte Visual Studio als Standard für den externen Skript-Editor in Unity festgelegt sein. Sie können dies bestätigen oder den externen Skript-Editor in Visual Studio ändern:

1. Klicken Sie im Unity-Menü auf **Einstellungen...** .

   ![Auswählen von Einstellungen](media/setup-vsmac-tools-unity-image4.png)

2. Klicken Sie im Dialogfeld "Einstellungen" auf die Registerkarte **Externe Tools**.

3. Klicken Sie in der Dropdownliste des externen Skript-Editors auf **Visual Studio**, falls dieses aufgelistet ist und andernfalls auf **Durchsuchen...** .

   ![Auswählen von Visual Studio](media/setup-vsmac-tools-unity-image5.png)

4. Wenn Sie auf **Durchsuchen...** geklickt haben, navigieren Sie zum Anwendungsverzeichnis, wählen Sie Visual Studio aus, und klicken Sie auf **Öffnen**.

   ![„Öffnen“ auswählen](media/setup-vsmac-tools-unity-image6.png)

5. Sobald Visual Studio in der Liste des **externen Skript-Editors** ausgewählt wurde, schließen Sie das Dialogfeld „Einstellungen“, um den Konfigurationsprozess abzuschließen.