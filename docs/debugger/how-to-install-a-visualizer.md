---
title: Installieren einer Schnellansicht | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie Sie eine Schnellansicht installieren, damit Sie diese zum Debuggen in Visual Studio verwenden können.
ms.custom: SEO-VS-2020
ms.date: 06/10/2020
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, visualizers
- visualizers, installing
ms.assetid: 3310ef43-515c-4d97-b0f9-51047247d3da
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2521983a797b676b9136ca14b733eb7afd054e27
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99904277"
---
# <a name="how-to-install-a-visualizer"></a>Vorgehensweise: Installieren einer Schnellansicht
Nachdem Sie eine Schnellansicht erstellt haben, müssen Sie die Schnellansicht installieren, sodass sie in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zur Verfügung steht. Das Installieren einer Schnellansicht ist einfach.

> [!NOTE]
> In UWP-Apps werden nur die Schnellansichten Standardtext, HTML, XML und JSON unterstützt. Benutzerdefinierte (von Benutzern erstellte) Schnellansichten werden nicht unterstützt.

::: moniker range=">=vs-2019"
### <a name="to-install-a-visualizer-for-visual-studio-2019"></a>Installieren einer Schnellansicht für Visual Studio 2019

1. Suchen Sie die DLL, die die erstellte Schnellansicht enthält.

   In der Regel ist es am besten, wenn sowohl für die debuggerseitige DLL als auch für die zu debuggende DLL **Beliebige CPU** als Zielplattform angegeben ist. Für die debuggerseitige DLL muss entweder **Beliebige CPU** oder **32-Bit** ausgewählt sein. Die Zielplattform für die zu debuggende DLL sollte dem Prozess für zu debuggende Komponenten entsprechen.

2. Kopieren Sie die [debuggerseitige](create-custom-visualizers-of-data.md#to-create-the-debugger-side) DLL (und alle davon abgängigen DLLs) an einen der folgenden Speicherorte:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`

3. Kopieren Sie die [zu debuggende](create-custom-visualizers-of-data.md#to-create-the-visualizer-object-source-for-the-debuggee-side) DLL an einen der folgenden Speicherorte:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers\` *Framework*

    - `My Documents\` *VisualStudioVersion* `\Visualizers\` *Framework*

    *Framework* kann hier Folgendes sein:
    - `net2.0` für zu debuggende Komponenten, die die `.NET Framework`-Runtime ausführen
    - `netstandard2.0` für zu debuggende Komponenten, die eine Runtime verwenden, die `netstandard 2.0` unterstützt (`.NET Framework v4.6.1+` oder `.NET Core 2.0+`)
    - `netcoreapp` für zu debuggende Komponenten, die die `.NET Core`-Runtime ausführen (Unterstützung für `.NET Core 2.0+`)

   Eine zu debuggende DLL ist erforderlich, wenn Sie eine eigenständige Schnellansicht erstellen möchten. Diese DLL enthält Code für das Datenobjekt, das Methoden von <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> implementieren kann.

   Wenn Sie den zu debuggenden Code mehrfach anvisieren, muss die zu debuggende DLL im Ordner für den minimal unterstützten Zielframeworkmoniker (TFM) abgelegt werden.

4. Starten Sie die Debugsitzung neu.

> [!NOTE]
> Das Verfahren unterscheidet sich in Visual Studio 2017 und älteren Versionen. Lesen Sie die [vorherige Version](how-to-install-a-visualizer.md?view=vs-2017&preserve-view=true) dieses Artikels.
::: moniker-end

::: moniker range="vs-2017"
### <a name="to-install-a-visualizer-for-visual-studio-2017-and-older"></a>Installieren einer Schnellansicht für Visual Studio 2017 und ältere Versionen

> [!IMPORTANT]
> Nur .NET Framework-Schnellansichten werden in Visual Studio 2017 und älteren Versionen unterstützt.

1. Suchen Sie die DLL, die die erstellte Schnellansicht enthält.

2. Kopieren Sie die DLL an einen der folgenden Speicherorte:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`

3. Starten Sie die Debugsitzung neu.

> [!NOTE]
> Wenn Sie eine verwaltete Schnellansicht zum Remotedebuggen verwenden möchten, kopieren Sie die DLL-Datei in denselben Pfad auf dem Remotecomputer.
::: moniker-end

## <a name="see-also"></a>Siehe auch
- [Erstellen benutzerdefinierter Schnellansichten](../debugger/create-custom-visualizers-of-data.md)
- [How to: Schreiben einer Schnellansicht](create-custom-visualizers-of-data.md)
