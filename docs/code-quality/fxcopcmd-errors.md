---
title: FxCopCmd-Fehler
ms.date: 10/19/2016
description: Erfahren Sie mehr über die Fehlercodes, die vom FxCopCmd-Befehl zurückgegeben werden. Sehen Sie sich an, welche Art von Fehler die einzelnen Codes darstellen, und erfahren Sie, wie Sie schwerwiegende Fehler erkennen.
ms.custom: SEO-VS-2020
ms.topic: reference
helpviewer_keywords:
- FxCopCmd errors
ms.assetid: bb614ed0-1b7c-4b56-99ae-da50ef6cfef9
ms.author: mikejo
author: mikejo5000
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: efeabd85bbf2753dd3f5e37a43e0918b7f95d7fe
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860216"
---
# <a name="fxcopcmd-tool-errors"></a>Fehler des FxCopCmd-Tools

"FxCopCmd" berücksichtigt nicht alle Fehler als schwerwiegend. Wenn FxCopCmd über ausreichende Informationen zum Ausführen einer partiellen Analyse verfügt, führt es die Analyse durch und meldet Fehler, die aufgetreten sind. Der Fehlercode, bei dem es sich um eine 32-Bit-Ganzzahl handelt, enthält eine bitweise Kombination numerischer Werte, die Fehlern entsprechen.

In der folgenden Tabelle werden die von FxCopCmd zurückgegebenen Fehlercodes beschrieben:

|Fehler|Numerischer Wert|
|-----------|-------------------|
|Keine Fehler|0x0|
|Analysefehler|0x1|
|Regelausnahmen|0x2|
|Fehler beim Laden des Projekts|0x4|
|Fehler beim Laden der Assembly|0x8|
|Fehler beim Laden der Regel Bibliothek.|0x10|
|Fehler beim Laden des Berichts|0x20|
|Ausgabefehler|0x40|
|Fehler beim Wechseln der Befehlszeile.|0x80|
|Initialisierungsfehler|0x100|
|Assemblyverweifehler|0x200|
|Buildbreakingmessage|0x400|
|Unbekannter Fehler.|0x1000000|

Bei schwerwiegenden Fehlern wird ein **Analysefehler** zurückgegeben. Gibt an, dass die Analyse nicht abgeschlossen werden konnte. Der Fehlercode enthält ggf. auch die zugrunde liegende Ursache des schwerwiegenden Fehlers. Die folgenden Bedingungen generieren schwerwiegende Fehler:

- Die Analyse konnte aufgrund unzureichender Eingaben nicht durchgeführt werden.

- Die Analyse hat eine Ausnahme ausgelöst, die von FxCopCmd nicht behandelt wird.

- Die angegebene Projektdatei wurde nicht gefunden oder ist beschädigt.

- Die Output-Option wurde nicht angegeben, oder die Datei konnte nicht geschrieben werden.

> [!NOTE]
> Der FxCopCmd-Rückgabetyp verweist darauf, dass der **Fehler** 0x200 allein eine Warnung und kein Fehler ist. Dieser Rückgabecode gibt an, dass indirekte Verweise fehlen, aber von FxCopCmd verarbeitet werden konnte. Die Warnung bedeutet, dass es möglich ist, dass einige Analyseergebnisse kompromittiert wurden. **Fehler** beim Behandeln von Assemblyverweisen als Fehler, wenn er mit einem anderen Rückgabecode kombiniert wird.

## <a name="see-also"></a>Weitere Informationen

- [Anwendungsfehler bei der Codeanalyse](../code-quality/code-analysis-application-errors.md)
