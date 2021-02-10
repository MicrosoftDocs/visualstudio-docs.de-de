---
title: Inkrementelle Builds | Microsoft-Dokumentation
description: Lernen Sie inkrementelle Builds von MSBuild kennen, die so optimiert sind, dass aktuelle Ausgabedateien nicht ausgeführt werden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, incremental builds
ms.assetid: 325e28c7-4838-4e3f-b672-4586adc7500c
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f1237128852cec39ff49204e1c269f10153b42ab
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914076"
---
# <a name="incremental-builds"></a>Inkrementelle Builds

Inkrementelle Builds sind Buildvorgänge, die so optimiert werden, dass Ziele mit Ausgabedateien, die hinsichtlich der zugehörigen Eingabedateien aktuell sind, nicht ausgeführt werden. Zielelemente können über ein `Inputs`-Attribut, das die Elemente angibt, die das Ziel als Eingabe erwartet, sowie ein `Outputs`-Attribut verfügen, das die Elemente angibt, die es als Ausgabe erzeugt. MSBuild versucht, zwischen den Werten dieser Attribute eine 1:1-Zuordnung zu erzielen. Wenn eine 1:1-Zuordnung vorhanden ist, vergleicht MSBuild den Zeitstempel jedes Eingabeelements mit dem Zeitstempel des zugehörigen Ausgabeelements. Ausgabedateien ohne 1:1-Zuordnung werden mit allen Eingabedateien verglichen. Ein Element wird als aktuell betrachtet, wenn dessen Ausgabedatei genau so alt oder neuer als seine Eingabedatei oder -dateien ist.

> [!NOTE]
> Wenn MSBuild die Eingabedateien auswertet, werden nur die Inhalte der Liste in der aktuellen Ausführung berücksichtigt. Änderungen an der Liste seit dem letzten Build führen nicht automatisch dazu, dass ein Ziel veraltet ist.

Wenn alle Ausgabeelemente aktuell sind, überspringt MSBuild das Ziel. Mit diesem *inkrementellen Build* kann die Buildgeschwindigkeit für das Ziel entscheidend erhöht werden. Wenn nur einige Dateien aktuell sind, führt MSBuild das Ziel aus, überspringt jedoch die aktuellen Elemente und bringt so alle Elemente auf den aktuellen Stand. Dieser Prozess wird als *partieller inkrementeller Build* bezeichnet.

1:1-Zuordnungen werden in der Regel durch Elementtransformationen erzeugt. Weitere Informationen finden Sie unter [Transformationen](../msbuild/msbuild-transforms.md).

 Betrachten Sie das folgende Ziel.

```xml
<Target Name="Backup" Inputs="@(Compile)"
    Outputs="@(Compile->'$(BackupFolder)%(Identity).bak')">
    <Copy SourceFiles="@(Compile)" DestinationFiles=
        "@(Compile->'$(BackupFolder)%(Identity).bak')" />
</Target>
```

Die durch den `Compile`-Elementtyp dargestellten Dateien werden in ein Sicherungsverzeichnis kopiert. Die Sicherungsdateien weisen die Erweiterung *.bak* auf. Wenn die durch den `Compile`-Elementtyp dargestellten Dateien oder die entsprechenden Sicherungsdateien nach dem Ausführen des Sicherungsziels nicht gelöscht oder geändert werden, wird das Sicherungsziel in nachfolgenden Builds übersprungen.

## <a name="output-inference"></a>Ausgaberückschluss

MSBuild bestimmt durch Vergleich des `Inputs`-Attributs mit dem `Outputs`-Attribut eines Ziels, ob dieses ausgeführt werden muss. Idealerweise bleibt der nach einem inkrementellen Build vorhandene Satz von Dateien unabhängig davon gleich, ob die zugeordneten Ziele ausgeführt werden oder nicht. Da sich Eigenschaften und Elemente, die von Aufgaben erstellt oder geändert werden, auf den Build auswirken können, muss MSBuild deren Werte auch dann ableiten, wenn das Ziel, das sich auf sie auswirkt, übersprungen wird. Dieser Prozess wird als *Ausgaberückschluss* bezeichnet.

Drei Fälle werden unterschieden:

- Das Ziel weist ein `Condition`-Attribut auf, das zu `false` ausgewertet wird. In diesem Fall wird das Ziel nicht ausgeführt, und hat keine Auswirkungen auf den Build.

- Das Ziel weist veraltete Ausgaben auf und wird ausgeführt, um diese auf den aktuellen Stand zu bringen.

- Das Ziel weist keine veralteten Ausgaben auf und wird übersprungen. MSBuild wertet das Ziel aus und nimmt Änderungen an Elementen und Eigenschaften vor, als ob das Ziel ausgeführt worden wäre.

Zur Unterstützung der inkrementellen Kompilierung müssen Aufgaben sicherstellen, dass der `TaskParameter`-Attributwert jedes `Output`-Elements gleich einem Aufgabeneingabeparameter ist. Im Folgenden finden Sie einige Beispiele:

```xml
<CreateProperty Value="123">
    <Output PropertyName="Easy" TaskParameter="Value" />
</CreateProperty>
```

Dieser Code erstellt die Easy-Eigenschaft mit dem Wert „123“ unabhängig davon, ob das Ziel ausgeführt oder übersprungen wird.

Ab MSBuild 3.5 wird der Ausgaberückschluss automatisch für Element- und Eigenschaftengruppen in einem Ziel ausgeführt. `CreateItem`-Aufgaben sind in einem Ziel nicht erforderlich und sollten vermieden werden. Zudem sollten `CreateProperty`-Aufgaben in einem Ziel nur verwendet werden, um zu bestimmen, ob dieses ausgeführt wurde.

Vor MSBuild 3.5 können Sie die Aufgabe [CreateItem](../msbuild/createitem-task.md) verwenden.

## <a name="determine-whether-a-target-has-been-run"></a>Bestimmen, ob ein Ziel ausgeführt wurde

Aufgrund des Ausgaberückschlusses müssen Sie einem Ziel eine `CreateProperty`-Aufgabe hinzufügen, um Eigenschaften und Elemente untersuchen und so bestimmen zu können, ob das Ziel ausgeführt wurde. Fügen Sie dem Ziel die Aufgabe `CreateProperty` hinzu, und weisen Sie dieser ein `Output`-Element zu, dessen `TaskParameter` auf „ValueSetByTask“ festgelegt ist.

```xml
<CreateProperty Value="true">
    <Output TaskParameter="ValueSetByTask" PropertyName="CompileRan" />
</CreateProperty>
```

Wenn das Ziel ausgeführt wird, erstellt dieser Code die Eigenschaft „CompileRan“ und weist ihr den Wert `true` zu. Wenn das Ziel übersprungen wird, wird CompileRan nicht erstellt.

## <a name="see-also"></a>Siehe auch

- [Ziele](../msbuild/msbuild-targets.md)
