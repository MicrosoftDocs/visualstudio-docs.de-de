---
title: Angeben zusätzlicher Instrumentierungsoptionen | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie Sie Binärdateien über die Visual Studio-IDE oder mithilfe von Befehlszeilentools instrumentieren können.
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.property.advanced
helpviewer_keywords:
- instrumentation, options
- profiling tools, session options
- performance sessions, options
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: aaa6a222ca320ff9e8e3d117c2218e170d67d683
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2021
ms.locfileid: "98721852"
---
# <a name="how-to-specify-additional-instrumentation-options"></a>Vorgehensweise: Angeben zusätzlicher Instrumentierungsoptionen

Sie können Binärdateien über die Visual Studio-IDE oder mithilfe von Befehlszeilentools instrumentieren. Beim Instrumentieren einer Binärdatei in der IDE können Sie die Menge der Daten steuern, die während der Instrumentation erfasst werden. Dazu geben Sie im [VSInstr](../profiling/vsinstr.md)-Tool zusätzliche Instrumentierungsoptionen an. Diese Optionen stehen auf der Sitzungs- oder der Zielebene zur Verfügung. Um beispielsweise während des Instrumentierungsvorgangs bestimmte Funktionen ein- oder auszuschließen, verwenden Sie die zusätzliche Instrumentierungsoption auf der Zielebene.

> [!IMPORTANT]
> Jede Überprüfung, die eingefügt wird, wirkt sich in geringem Maße auf das Verhalten des ursprünglichen Programms aus. Diese Änderung verursacht zum Zeitpunkt der Analyse eine Verlängerung der Analysedauer. Obwohl ein Schätzwert dieser Verlängerung subtrahiert wird, bleiben bei Multithreadanwendungen kleinste Auswirkungen auf die Zeit bestehen. Mithilfe der Optionen des [VSInstr](../profiling/vsinstr.md)-Tools können Sie die Datenerfassung während der Profilerstellung steuern.

## <a name="to-specify-additional-instrumentation-option"></a>So geben Sie zusätzliche Instrumentierungsoptionen an

1. Klicken Sie im **Leistungs-Explorer** mit der rechten Maustaste auf die **Leistungssitzung** und wählen Sie **Eigenschaften** aus.

2. Klicken Sie in den **Eigenschaftenseiten** auf die Eigenschaft **Erweitert**.

3. Geben Sie Optionen im Feld **Zusätzliche Instrumentierungsoptionen** ein.

     Geben Sie z. B. die Profilebene mithilfe von /CONTROL:THREAD an. Eine vollständige Liste der Optionen finden Sie unter [VSInstr](../profiling/vsinstr.md).

4. Klicken Sie auf **OK**.

## <a name="see-also"></a>Siehe auch

[Konfigurieren von Leistungssitzungen](../profiling/configuring-performance-sessions.md)
[Verwenden der Profilerstellungstools über die Befehlszeile](../profiling/using-the-profiling-tools-from-the-command-line.md)
