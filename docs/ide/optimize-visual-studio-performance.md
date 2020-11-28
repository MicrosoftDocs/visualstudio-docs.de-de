---
title: Verbessern der Leistung, wenn Visual Studio langsam ist
titleSuffix: ''
description: Lernen Sie, die Visual Studio-Leistung zu verbessern, wenn Sie feststellen, dass Visual Studio langsam ist.
ms.custom: SEO-VS-2020
ms.date: 04/11/2018
ms.topic: conceptual
helpviewer_keywords:
- performance [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- vs.performancecenter
ms.workload:
- multiple
ms.openlocfilehash: 6e6f93b7709144e6682bc54d5686fde5ff650f56
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/25/2020
ms.locfileid: "95871469"
---
# <a name="optimize-visual-studio-performance"></a>Optimieren der Visual Studio-Leistung

Dieser Artikel enthält einige Vorschläge, die Sie ausprobieren können, wenn Visual Studio langsam ausgeführt wird. Weitere Vorschläge zum Verbessern der Leistung finden Sie unter [Tipps und Tricks für die Leistung von Visual Studio](../ide/visual-studio-performance-tips-and-tricks.md).

## <a name="upgrade-visual-studio"></a>Upgrade auf Visual Studio

Wenn Sie derzeit Visual Studio 2015 verwenden, laden Sie [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) oder [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) kostenlos herunter, um die verbesserte Leistung dieses Tools zu testen. Projektmappen werden in Visual Studio 2015 zwei- bis dreimal schneller geladen. Auch in anderen Bereichen wurde die Leistung verbessert. Visual Studio 2017 und Visual Studio 2019 können parallel zu Visual Studio 2015 installiert werden. Sie können das Tool also bedenkenlos ausprobieren.

::: moniker range="vs-2017"

Wenn Sie derzeit Visual Studio 2017 verwenden, stellen Sie sicher, dass Sie Version 15.6 oder höher ausführen. Die Daten zeigen, dass Projektmappen in Version 15.6 zwei- bis dreimal schneller geladen werden. Sie können sie [hier](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)herunterladen.

::: moniker-end

## <a name="extensions-and-tool-windows"></a>Erweiterungen und Toolfenster

Möglicherweise haben Sie Erweiterungen installiert, die Visual Studio verlangsamen. Hilfe zur Verwaltung von Erweiterungen, um die Leistung zu verbessern, finden Sie unter [Ändern von Erweiterungseinstellungen zum Verbessern der Leistung](../ide/optimize-visual-studio-startup-time.md#extensions).

Möglicherweise sind auch Toolfenster vorhanden, die Visual Studio verlangsamen. Hilfe zur Verwaltung von Toolfenstern finden Sie unter [Ändern von Erweiterungseinstellungen zum Verbessern der Leistung](../ide/optimize-visual-studio-startup-time.md#tool-windows).

## <a name="hardware"></a>Hardware

Wenn Sie vorhanden, Ihre Hardware zu aktualisieren, hat ein SSD-Datenträger (Solid State Drive) positivere Auswirkungen auf die Leistung als zusätzlicher Arbeitsspeicher (RAM) oder eine schnellere CPU.

Wenn Sie einen SSD-Datenträger hinzufügen, installieren Sie Windows im Gegensatz zu einem Festplattenlaufwerk für eine optimale Leistung auf diesem Laufwerk. Es ist jedoch nicht wichtig, auf welchem Laufwerk Sie Ihre Visual Studio-Projektmappen speichern.

Führen Sie Ihre Projektmappe jedoch nicht über ein USB-Laufwerk aus. Kopieren Sie diese auf Ihren HDD- oder SSD-Datenträger.

## <a name="help-us-improve"></a>Helfen Sie uns dabei, noch besser zu werden!

Ihr Feedback hilft uns dabei, uns zu verbessern. Verwenden Sie das Feature **Problem melden**, um eine Ablaufverfolgung aufzuzeichnen und diese an uns zu senden. Klicken Sie auf das Feedbacksymbol neben der **Schnellstartleiste**, oder klicken Sie in der Menüleiste auf **Hilfe** > **Feedback senden** > **Problem melden**. Weitere Informationen finden Sie unter [Melden eines Problems mit Visual Studio](../ide/how-to-report-a-problem-with-visual-studio.md).

## <a name="see-also"></a>Weitere Informationen

- [Tipps und Tricks für die Leistungssteigerung](../ide/visual-studio-performance-tips-and-tricks.md)
- [Blog zu Visual Studio: Schnelleres Laden von Projektmappen mit Visual Studio 2017 (Version 15.6)](https://devblogs.microsoft.com/visualstudio/load-solutions-faster-with-visual-studio-2017-version-15-6/)
