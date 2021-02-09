---
title: Legacy Code Analyse deaktivieren
ms.date: 10/04/2019
description: Erfahren Sie, wie Sie die binäre Code Analyse in Visual Studio aktivieren und deaktivieren. Weitere Informationen finden Sie unter Konfigurieren dieses Features in Projekten mit verwaltetem Code.
ms.custom: SEO-VS-2020
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: c10aa602c2c9af3c51812073d62d5bd9bff06664
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860073"
---
# <a name="how-to-enable-and-disable-binary-code-analysis-for-managed-code"></a>Gewusst wie: Aktivieren und Deaktivieren der binären Code Analyse für verwalteten Code

Sie können die Legacy-Code Analyse (binäre Analyse) so konfigurieren, dass Sie nach jedem Build eines Projekts mit verwaltetem Code ausgeführt wird. Sie können auch andere Einstellungen für jede Buildkonfiguration haben, z. b. Debug und Release.

> [!NOTE]
> Die Legacy Analyse ist für neuere Projekttypen wie .net Core und .NET Standard-apps nicht verfügbar. Diese Projekte verwenden [.NET Compiler Platform basierten Code Analysen](roslyn-analyzers-overview.md) , um den Code zu analysieren, sowohl Live als auch zur Buildzeit. Informationen zum Deaktivieren der Quell Code Analyse in diesen Projekten finden Sie unter [Deaktivieren der Quell Code Analyse](disable-code-analysis.md).

So aktivieren oder deaktivieren Sie die Legacy Code Analyse:

1. Wählen Sie in **Projektmappen-Explorer** das Projekt aus, halten Sie es (oder klicken Sie mit der rechten Maustaste darauf), und wählen Sie **Eigenschaften** aus.

2. Wechseln Sie im Dialogfeld Eigenschaften für das Projekt zur Registerkarte **Code Analyse** .

3. Geben Sie den Buildtyp in der **Konfiguration** und die Zielplattform in der **Plattform** an. (Nur Non-.net Core/. NET Standard-Projekte.)

::: moniker range="vs-2017"

4. Aktivieren bzw. deaktivieren Sie das Kontrollkästchen **Code Analyse bei Build aktivieren** , um die automatische Code Analyse zu aktivieren bzw. zu deaktivieren.

::: moniker-end

::: moniker range=">=vs-2019"

4. Zum Aktivieren oder Deaktivieren der automatischen Code Analyse aktivieren bzw. deaktivieren Sie das Kontrollkästchen **auf Build ausführen** im Abschnitt **binäre Analysen** .

   ![Ausführen der binären Code Analyse für die Buildoption in Visual Studio](media/run-on-build-binary-analyzers.png)

::: moniker-end

> [!NOTE]
> Das Deaktivieren der binären Code Analyse beim Build wirkt sich nicht auf [.NET Compiler Platform basierten Code](roslyn-analyzers-overview.md)Analysen aus, die immer bei Build ausgeführt werden, wenn Sie Sie als nuget-Paket installiert haben. Weitere Informationen zum Deaktivieren der Analyse von diesen Analyzern finden [Sie unter Deaktivieren der Quell Code Analyse](disable-code-analysis.md).
