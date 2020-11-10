---
title: Buildreihenfolge für Ziele |Microsoft-Dokumentation
description: Erfahren Sie, wie Sie die Ausführungsreihenfolge für MSBuild-Ziele angeben, wenn die Eingabe für ein Ziel von der Ausgabe eines anderen Ziels abhängt.
ms.custom: SEO-VS-2020
ms.date: 05/02/2019
ms.topic: conceptual
helpviewer_keywords:
- msbuild, build order
ms.assetid: f4a26339-9f9a-497a-9aa6-0797183d450d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 955c8c496df45bbfce28bdac1571f84649621024
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048057"
---
# <a name="target-build-order"></a>Buildreihenfolge für Ziele

Ziele müssen geordnet werden, wenn die Eingabe für ein Ziel von der Ausgabe eines anderen Ziels abhängt. Sie können diese Attribute verwenden, um die Reihenfolge anzugeben, in der Ziele ausgeführt werden:

- `InitialTargets`. Das `Project`-Attribut gibt die Ziele an, die zuerst ausgeführt werden, auch wenn Ziele in der Befehlszeile oder im `DefaultTargets`-Attribut angegeben sind.

- `DefaultTargets`. Das `Project`-Attribut gibt an, welche Ziele ausgeführt werden, wenn in der Befehlszeile kein Ziel explizit angegeben ist.

- `DependsOnTargets`. Das `Target`-Attribut gibt Ziele an, die ausgeführt werden müssen, bevor das Ziel ausgeführt werden kann.

- `BeforeTargets` und `AfterTargets`. Diese `Target`-Attribute geben an, dass das Ziel vor oder nach den angegebenen Zielen ausgeführt werden soll (MSBuild 4.0).

Ein Ziel wird während eines Builds nie zweimal ausgeführt, auch wenn ein nachfolgendes Ziel im Build von diesem abhängt. Sobald ein Ziel ausgeführt wurde, ist sein Beitrag zum Build abgeschlossen.

Ziele verfügen möglicherweise über ein `Condition`-Attribut. Wenn die angegebene Bedingung `false` ergibt, wird das Ziel nicht ausgeführt und hat keine Auswirkung auf den Build. Weitere Informationen zu Bedingungen finden Sie unter [Bedingungen](../msbuild/msbuild-conditions.md).

## <a name="initial-targets"></a>Ursprüngliche Ziele

Das `InitialTargets`-Attribut des [Projekt](../msbuild/project-element-msbuild.md)-Elements gibt Ziele an, die zuerst ausgeführt werden, auch wenn Ziele in der Befehlszeile oder im `DefaultTargets`-Attribut angegeben sind. Ursprüngliche Ziele werden in der Regel für die Überprüfung von Fehlern verwendet.

Der Wert des `InitialTargets`-Attribut kann eine durch Semikolons getrennte, geordnete Liste von Zielen sein. Das folgende Beispiel gibt an, dass das `Warm`-Ziel ausgeführt wird und dann das `Eject`-Ziel ausgeführt wird.

```xml
<Project InitialTargets="Warm;Eject" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
```

Importierte Projekte haben möglicherweise ihre eigenen `InitialTargets`-Attribute. Alle ursprünglichen Ziele werden zusammen aggregiert und gemäß Reihenfolge ausgeführt.

Weitere Informationen finden Sie unter [Vorgehensweise: Angeben des zuerst zu erstellenden Ziels](../msbuild/how-to-specify-which-target-to-build-first.md).

## <a name="default-targets"></a>Standardziele

Das `DefaultTargets`-Attribut des [Projekt](../msbuild/project-element-msbuild.md)-Elements gibt das Ziel bzw. die Ziele an, die erstellt werden, wenn ein Ziel nicht explizit in einer Befehlszeile angegeben wird.

Der Wert des `DefaultTargets`-Attributs kann eine durch Semikolons getrennte, geordnete Liste von Standardzielen sein. Das folgende Beispiel gibt an, dass das `Clean`-Ziel ausgeführt wird und dann das `Build`-Ziel ausgeführt wird.

```xml
<Project DefaultTargets="Clean;Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
```

Sie können die Standardziele überschreiben, indem Sie den Schalter **-target** in der Befehlszeile verwenden. Das folgende Beispiel gibt an, dass das `Build`-Ziel ausgeführt wird und dann das `Report`-Ziel ausgeführt wird. Wenn Sie Ziele auf diese Weise angeben, werden alle Standardziele ignoriert.

 `msbuild -target:Build;Report`

Wenn ursprüngliche Ziele und Standardziele angegeben werden und keine Befehlszeilenziele angegeben sind, führt MSBuild zuerst die ursprünglichen Ziele und dann die Standardziele aus.

Importierte Projekte haben möglicherweise ihre eigenen `DefaultTargets`-Attribute. Die erste `DefaultTargets`-Attribut bestimmt, welche Standardziele ausgeführt werden.

Weitere Informationen finden Sie unter [Vorgehensweise: Angeben des zuerst zu erstellenden Ziels](../msbuild/how-to-specify-which-target-to-build-first.md).

## <a name="first-target"></a>Erstes Ziel

Wenn keine ursprünglichen Ziele, Standardziele oder Befehlszeilenziele vorhanden sind, führt MSBuild das erste Ziel aus, das in der Projektdatei oder einer beliebigen importierten Projektdatei angetroffen wird.

## <a name="target-dependencies"></a>Zielabhängigkeiten

Ziele können Abhängigkeitsbeziehungen unter Zielen beschreiben. Die `DependsOnTargets`-Attribut gibt an, dass ein Ziel von anderen Zielen abhängig ist. Beispiel:

```xml
<Target Name="Serve" DependsOnTargets="Chop;Cook" />
```

informiert MSBuild, dass das `Serve`-Ziel vom `Chop`-Ziel und dem `Cook`-Ziel abhängig ist. MSBuild führt das `Chop`-Ziel und dann das `Cook`-Ziel aus, bevor das `Serve`-Ziel ausgeführt wird.

## <a name="beforetargets-and-aftertargets"></a>Vorher-Ziele und Nachher-Ziele

In MSBuild 4.0 können Sie die Reihenfolge der Ziele mithilfe der `BeforeTargets`- und `AfterTargets`-Attribute angeben.

Betrachten Sie folgendes Skript.

```xml
<Project DefaultTargets="Compile;Link" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="Compile">
        <Message Text="Compiling" />
    </Target>
    <Target Name="Link">
        <Message Text="Linking" />
    </Target>
</Project>
```

Zum Erstellen eines Zwischenziels `Optimize`, das nach dem `Compile`-Ziel, aber vor der `Link`-Ziel ausgeführt wird, fügen Sie das folgende Ziel an einer beliebigen Stelle im `Project`-Element hinzu.

```xml
<Target Name="Optimize"
    AfterTargets="Compile" BeforeTargets="Link">
    <Message Text="Optimizing" />
</Target>
```

## <a name="determine-the-target-build-order"></a>Bestimmen der Buildreihenfolge für Ziele

MSBuild bestimmt die Buildreihenfolge für Ziele wie folgt:

1. `InitialTargets`-Ziele werden ausgeführt.

2. Auf der Befehlszeile mit dem Schalter **-target** angegebene Ziele werden ausgeführt. Wenn Sie keine Ziele in der Befehlszeile angeben, werden die `DefaultTargets`-Ziele ausgeführt. Wenn keine Ziele vorhanden sind, wird das erste gefundene Ziel ausgeführt.

3. Das `Condition`-Attribut des Ziels wird ausgewertet. Wenn das `Condition`-Attribut vorhanden ist und `false` ergibt, wird das Ziel nicht ausgeführt und hat keine weitere Auswirkung auf den Build.

   Andere Ziele, die das bedingte Ziel in `BeforeTargets` oder `AfterTargets` auflisten, werden dennoch in der vorgeschriebenen Reihenfolge ausgeführt.

4. Bevor das Ziel ausgeführt oder übersprungen wird, werden seine `DependsOnTargets`-Ziele ausgeführt, es sei denn, das `Condition`-Attribut wird auf das Ziel angewendet und zu `false` ausgewertet.

   > [!NOTE]
   > Ein Ziel wird als übersprungen angesehen, wenn es nicht ausgeführt wird, weil seine Ausgabeelemente aktuell sind (siehe [inkrementeller Build](../msbuild/incremental-builds.md)). Diese Überprüfung erfolgt unmittelbar vor dem Ausführen der Aufgaben im Ziel und wirkt sich nicht auf die Ausführungsreihenfolge der Ziele aus.

5. Bevor das Ziel ausgeführt oder übersprungen wird, wird jedes andere Ziel ausgeführt, das es in einem `BeforeTargets`-Attribut auflistet.

6. Bevor das Ziel ausgeführt wird, werden sein `Inputs`-Attribut und `Outputs`-Attribut verglichen. Wenn MSBuild feststellt, dass alle Ausgabedateien in Bezug auf die entsprechende(n) Eingabedatei(en) veraltet sind, wird das Ziel von MSBuild ausgeführt. Andernfalls überspringt MSBuild das Ziel.

7. Nachdem das Ziel ausgeführt oder übersprungen wurde, wird jedes andere Ziel ausgeführt, das es in einem `AfterTargets`-Attribut auflistet.

## <a name="see-also"></a>Siehe auch

- [Ziele](../msbuild/msbuild-targets.md)
