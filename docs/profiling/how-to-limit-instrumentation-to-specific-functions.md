---
title: Einschränken der Instrumentierung auf bestimmte Funktionen | Microsoft-Dokumentation
description: Hier erfahren Sie, wie Sie die Instrumentierung und Datensammlung auf mindestens eine Funktion einschränken, indem Sie die Optionen auf der Seite „Erweitert“ oder auf den Eigenschaftenseiten der Zielbinärdatei einstellen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- performance tools, limiting instrumentation to functions
ms.assetid: bd98d6bf-2560-4eba-b063-2facb09f87c4
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 92825f77b1c94a7545b399dbc1cb35ecefb8218d
ms.sourcegitcommit: 8e15b434bf5db3e0f719320ca82682df1a3da110
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/27/2021
ms.locfileid: "98883331"
---
# <a name="how-to-limit-instrumentation-to-specific-functions"></a>Vorgehensweise: Einschränken der Instrumentierung auf bestimmte Funktionen
Sie können die Instrumentierung und Datensammlung auf eine oder mehr Funktionen einschränken, indem Sie die Optionen unter der Seite **Erweitert** der **Leistungssitzung** oder die Zielbinärdateieigenschaften einstellen.

- Wenn Sie die Funktionen auf der Eigenschaftenseite der Leistungssitzung angeben, werden nur diese Funktionen in allen instrumentierten Binärdateien der Sitzung instrumentiert.

- Wenn Sie die Funktionen auf der Eigenschaftenseite einer Zielbinärdatei angeben, werden nur die Funktionen, die in dieser bestimmten Binärdatei sind, instrumentiert. Funktionen in anderen Leistungsbinärdateien werden wie gewohnt instrumentiert.

  Das beschränken der Datensammlung auf diese Weise wird nur unterstützt, wenn die Instrumentierungs-Profilerstellungsmethode ausgewählt ist.

> [!NOTE]
> Sie können auch die Seite **Erweitert** der Eigenschaftenseiten **Leistungssitzung** verwenden, um andere Einstellungen zu verwenden, die für das Befehlszeilen-Instrumentierungstool [VSInstr](../profiling/vsinstr.md) verfügbar sind.

### <a name="to-limit-instrumentation-to-specific-functions-in-a-performance-session"></a>So beschränken Sie die Instrumentierung auf bestimmte Funktionen in einer Leistungssitzung

1. Klicken Sie im **Leistungs-Explorer** mit der rechten Maustaste auf den Namen der Sitzung, und klicken Sie dann auf **Eigenschaften**.

    Das Dialogfeld **Eigenschaftenseiten** wird angezeigt.

2. Klicken Sie im Dialogfeld **Eigenschaftenseiten** auf **Erweitert**

3. Verwenden Sie im Textfeld **Zusätzliche Instrumentierungsoptionen** den folgenden Syntax, um den Namen der zu instrumentierenten Funktionen einzugeben:

    **/include:** `FuncSpec` **[;** `FuncSpec` **]** `...`

    `FuncSpec` ist der Namespace und der Funktionsname. Es hat das Format `Namespace` **::** `FunctionName`. Trennen Sie mehrere Funktionen mit einem Semikolon. Verwenden Sie ein Sternchen (\*), um einen Platzhalter für ein oder mehrere Zeichen anzugeben. Beispiel: **/include:MyNS::\\** _ gibt alle Funktionen im Namespace „MyNS“ an.

   > [!NOTE]
   > Öffnen Sie zum Auflisten der Funktionen in einer Binärdatei ein Eingabeaufforderungsfenster im Installationsverzeichnis der Profilerstellungstools (weitere Informationen finden Sie unter [Angeben des Pfads zu Befehlszeilentools](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)), und geben Sie dann _ *vsinstr /DumpFuncs** ein.

### <a name="to-limit-instrumentation-to-specific-functions-in-a-binary"></a>So beschränken Sie die Instrumentierung auf eine bestimmte Funktion in einer Binärdatei

1. Suchen Sie im **Leistungs-Explorer** den Namen der Binärdatei im Knoten **Ziele** der Leistungssitzung.

2. Klicken Sie mit der rechten Maustaste auf den Namen der Binärdatei, und klicken Sie anschließend auf **Eigenschaften**.

    Das Dialogfeld **Eigenschaftenseiten** wird angezeigt.

3. Klicken Sie im Dialogfeld **Eigenschaftenseiten** auf **Erweitert**

4. Verwenden Sie im Textfeld **Zusätzliche Instrumentierungsoptionen** den folgenden Syntax, um den Namen der zu instrumentierenten Funktionen einzugeben:

    **/include:** `FuncSpec` **[;** `FuncSpec` **]** `...`

    `FuncSpec` ist der Namespace und der Funktionsname. Es hat das Format `Namespace` **::** `FunctionName`. Trennen Sie mehrere Funktionen mit einem Semikolon. Verwenden Sie ein Sternchen (\*), um einen Platzhalter für ein oder mehrere Zeichen anzugeben. Beispiel: **/include:MyNS::\\** _ gibt alle Funktionen im Namespace „MyNS“ an.

   > [!NOTE]
   > Öffnen Sie zum Auflisten der Funktionen in einer Binärdatei ein Eingabeaufforderungsfenster im Installationsverzeichnis der Profilerstellungstools (weitere Informationen finden Sie unter [Angeben des Pfads zu Befehlszeilentools](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)), und geben Sie dann _ *vsinstr /DumpFuncs** ein.

## <a name="see-also"></a>Siehe auch
- [Steuerung der Datensammlung](../profiling/controlling-data-collection.md)
- [How to: Beschränken der Instrumentierung auf bestimmte DLLs](../profiling/how-to-limit-instrumentation-to-specific-dlls.md)
- [How to: Angeben zusätzlicher Instrumentierungsoptionen](../profiling/how-to-specify-additional-instrumentation-options.md)
