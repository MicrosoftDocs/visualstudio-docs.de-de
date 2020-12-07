---
title: Ausführen eines Komponententest als 64-Bit-Prozess
description: Hier erfahren Sie, wie Sie Komponententests ausführen und Code-Coverage-Informationen als 64-Bit-Prozess erfassen. Sie benötigen einen 64-Bit-Computer.
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: how-to
helpviewer_keywords:
- unit tests, creating
- unit tests, running
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 7d18a97a3cf8f680e7bfe3d679e8e57f7cc716fb
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2020
ms.locfileid: "96329067"
---
# <a name="run-a-unit-test-as-a-64-bit-process"></a>Ausführen eines Komponententest als 64-Bit-Prozess

Wenn Sie über einen 64-Bit-Computer verfügen, können Sie Komponententests ausführen und Code Coverage-Informationen als 64-Bit-Prozess erfassen.

## <a name="to-run-a-unit-test-as-a-64-bit-process"></a>So führen Sie einen Komponententest als 64-Bit-Prozess aus

1. Wenn Ihr Code oder Ihre Tests als 32-Bit/x86-Prozess kompiliert wurden, Sie diese nun aber als 64-Bit-Prozess ausführen möchten, kompilieren Sie sie als **Beliebige CPU**.

   ::: moniker range="vs-2017"
   Alternativ dazu können Sie Ihr Projekt in Visual Studio 2017 auch als **64-Bit-Prozess** kompilieren.
   ::: moniker-end

    > [!TIP]
    > Maximale Flexibilität erhalten Sie, wenn Sie die Testprojekte mit der Konfiguration **Beliebige CPU** kompilieren. Die Ausführung ist dann sowohl auf 32- als auch auf 64-Bit-Agents möglich. Es hat keine Vorteile, Testprojekte mit der **64-Bit**-Konfiguration zu kompilieren, es sei denn, Sie rufen Code auf, der nur unter 64-Bit unterstützt wird.

2. Richten Sie die Komponententests als 64-Bit-Prozess ein.

   ::: moniker range=">=vs-2019"
   Klicken Sie im Visual Studio-Menü auf **Test** und anschließend auf **Prozessorarchitektur für AnyCPU-Projekte**. Wählen Sie **x64** zum Ausführen der Tests als 64-Bit-Prozess aus.
   ::: moniker-end
   ::: moniker range="vs-2017"
   Klicken Sie im Visual Studio-Menü auf **Test**, **Testeinstellungen** und anschließend auf **Prozessorarchitektur**. Wählen Sie **x64** zum Ausführen der Tests als 64-Bit-Prozess aus.
   ::: moniker-end

   \- oder -

   Geben Sie `<TargetPlatform>x64</TargetPlatform>` in einer *RUNSETTINGS*-Datei an. Ein Vorteil dieser Methode ist, dass Sie Gruppen von Einstellungen in verschiedenen Dateien angeben und schnell zwischen verschiedenen Einstellungen wechseln können. Sie können auch die Einstellungen zwischen Projektmappen kopieren. Weitere Informationen hierzu finden Sie unter [Konfigurieren von Komponententests mithilfe einer RUNSETTINGS-Datei](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).

## <a name="see-also"></a>Siehe auch

- [Ausführen von Komponententests mit dem Test-Explorer](../test/run-unit-tests-with-test-explorer.md)
- [Ausführen von Komponententests für Code](../test/unit-test-your-code.md)
