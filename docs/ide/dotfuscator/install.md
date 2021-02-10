---
title: Installieren von Dotfuscator Community
ms.date: 03/28/2019
ms.devlang: dotnet
ms.topic: how-to
keywords: dotfuscator, dotfuscator community, dotfuscator ce, preemptive, preemptive solutions, preemptive protection, protection, community edition, obfuskation, .NET, kostenlos, visual studio 2017, visual studio 2019, visual studio, installieren
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator Community
- Dotfuscator
- obfuscation
- protection
- Dotfuscator installer
- Dotfuscator setup
- install Dotfuscator
- installing Dotfuscator
- set up Dotfuscator
description: Finden Sie heraus, wie Sie die Kopie von Dotfuscator Community, die kostenlos in Visual Studio enthalten ist, installieren.
ms.assetid: f2146651-e24a-4e24-ade8-8ddee8ff4e43
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: 9f4ca634aa226437b6d8790837c9f95f778a00c0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99924759"
---
# <a name="install-dotfuscator-community"></a>Installieren von Dotfuscator Community

Dotfuscator Community ist jetzt eine optionale Komponente von Visual Studio.
In dieser Anleitung erfahren Sie, wie Sie Dotfuscator Community installieren.

> [!NOTE]
> Zusätzlich zu den Dotfuscator Community-Versionen, die mit Releases von Visual Studio einhergehen, veröffentlicht auch PreEmptive Solutions in regelmäßigen Abständen aktualisierte Versionen auf der PreEmptive Solutions-Website.
> Wenn Sie die **neueste Version** direkt herunterladen möchten, statt sie mit Visual Studio zu installieren, **[klicken Sie hier, um zur Seite „Downloads“ von Dotfuscator zu gelangen][download]** .

## <a name="within-visual-studio"></a>In Visual Studio

::: moniker range="vs-2019"

Sie können Dotfuscator Community in der Visual Studio-IDE installieren:

1. Geben Sie im **Suchfeld** (STRG+Q) `dotfuscator` ein. <br/> <br/> ![Suchfeld](media/install_in_vs19_12.png) <br/> <br/>

2. Wählen Sie in den angezeigten Suchergebnissen unter der Überschrift *Komponenten***Install PreEmptive Protection – Dotfuscator** (PreEmptive Protection installieren – Dotfuscator) aus.
   * Wenn stattdessen unter der Überschrift *Menüs***PreEmptive Protection – Dotfuscator Community** (PreEmptive Protection – Dotfuscator Community) angezeigt wird, ist Dotfuscator Community bereits installiert. Wählen Sie diese Option aus, um mit den [ersten Schritten][get-started] zu beginnen.

3. Ein Fenster für den Visual Studio-Installer wird geöffnet – schon so voreingestellt, dass Dotfuscator Community installiert wird.
   > [!NOTE]
   > Möglicherweise müssen Sie Administratoranmeldeinformationen eingeben, damit Sie fortfahren können.

4. Klicken Sie im Visual Studio-Installer auf *Installieren*. <br/> <br/> ![Klicken auf „Installieren“.](media/install_in_vs19_34.png) <br/> <br/>

::: moniker-end

::: moniker range="vs-2017"

Sie können Dotfuscator Community in der Visual Studio-IDE installieren:

1. Geben Sie `dotfuscator` in die **Schnellstart**-Suchleiste (STRG+Q) ein. <br/> <br/> ![Schnellstart](media/install_from_vs_12.png) <br/> <br/>

2. Wählen Sie in den angezeigten Schnellstartergebnisse unter der Überschrift *Installieren* **PreEmptive Protection – Dotfuscator (Individual Component) (PreEmptive Protection – Dotfuscator (Einzelne Komponente))** aus.
   * Wenn stattdessen unter der Überschrift *Menüs* **Extras – PreEmptive Protection – Dotfuscator** angezeigt wird, ist Dotfuscator CE bereits installiert. Wählen Sie diese Option aus, um mit den [ersten Schritten][get-started] zu beginnen.

3. Ein Fenster für den Visual Studio-Installer wird geöffnet – schon so voreingestellt, dass Dotfuscator Community installiert wird.
   > [!NOTE]
   > Möglicherweise müssen Sie Administratoranmeldeinformationen eingeben, damit Sie fortfahren können.

4. Klicken Sie im Visual Studio-Installer auf *Installieren*. <br/> <br/> ![Klicken auf „Installieren“.](media/install_from_vs_345.png) <br/> <br/>

::: moniker-end

Sobald die Installation abgeschlossen ist, [können Sie Dotfuscator Community verwenden][get-started].

## <a name="during-visual-studio-installation"></a>Während der Installation von Visual Studio

Wenn Sie Visual Studio noch nicht installiert haben, können Sie den Installer von der [Visual Studio-Website][vs-install] herunterladen.
Wenn Sie diesen ausführen, zeigt er Installationsoptionen für die ausgewählte Visual Studio-Edition an.

::: moniker range="vs-2019"

![Installationsoptionen](media/install_ui.png)

::: moniker-end

::: moniker range="vs-2017"

![Installationsoptionen](media/install_ui_17.png)

::: moniker-end

Anschließend können Sie Dotfuscator Community als einzelne Komponente von Visual Studio installieren:

1. Wählen Sie die Registerkarte **Einzelne Komponenten** aus.
2. Setzen Sie unter *Codetools* ein Häkchen bei dem Element *PreEmptive Protection – Dotfuscator*.<br/> <br/> ![Einzelne Komponenten](media/install_individually_12.png) <br/> <br/>
3. Im Panel *Zusammenfassung* wird *PreEmptive Protection – Dotfuscator* im Bereich *Einzelne Komponenten* angezeigt. <br/> <br/> ![Zusammenfassungsbereich](media/install_individually_3.png) <br/> <br/>
4. Alle weiteren Installationseinstellungen können Sie Ihrer Umgebung entsprechend vornehmen.
5. Wenn alles für die Installation von Visual Studio vorbereitet ist, klicken Sie auf die Schaltfläche *Installieren*.

Sobald die Installation abgeschlossen ist, können Sie Dotfuscator Community verwenden. Weitere Informationen finden Sie [auf der „Erste Schritte“-Seite des vollständigen Dotfuscator Community-Benutzerhandbuchs][get-started].

## <a name="see-also"></a>Siehe auch

[Dieses Thema im vollständigen Dotfuscator Community-Benutzerhandbuch](https://www.preemptive.com/dotfuscator/ce/docs/help/)

<!-- Copyright © 2019 PreEmptive Solutions, LLC -->

[vs-install]:  https://visualstudio.microsoft.com/downloads/
[get-started]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html

[download]:  https://www.preemptive.com/products/dotfuscator/downloads

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_install.html
