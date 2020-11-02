---
title: 'Vorgehensweise: Angeben des zuerst zu erstellenden Ziels | Microsoft-Dokumentation'
description: Erfahren Sie, wie Sie anfängliche Ziele oder Standardziele angeben, die in MSBuild-Projektdateien zuerst erstellt werden sollen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- DefaultTargets attribute [MSBuild]
- MSBuild, specifying the defalut target
- MSBuild, DefaultTargets attribute
ms.assetid: a580ba5b-2919-42d2-ae38-1af991e0205a
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a9ce8f17e70344445f95e8b4742838e40a92fe88
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436189"
---
# <a name="how-to-specify-which-target-to-build-first"></a>Vorgehensweise: Angeben des zuerst zu erstellenden Ziels

Eine Projektdatei kann ein oder mehrere `Target`-Elemente enthalten, die definieren, wie das Projekt erstellt wird. Die Microsoft-Build-Engine (MSBuild) erstellt das erste gefundene Ziel sowie alle Abhängigkeiten – es sei denn, die Projektdatei enthält ein `DefaultTargets`-Attribut, ein `InitialTargets`-Attribut oder ein Ziel, das an der Befehlszeile unter Verwendung des Parameters **-target** angegeben wurde.
## <a name="use-the-initialtargets-attribute"></a>Verwenden des InitialTargets-Attributs

Das `InitialTargets`-Attribut des `Project`-Elements gibt ein Ziel an, das zuerst ausgeführt wird, auch wenn Ziele in der Befehlszeile oder im `DefaultTargets`-Attribut angegeben sind.

#### <a name="to-specify-one-initial-target"></a>Angeben eines ersten Ziels

- Geben Sie das Standardziel im `InitialTargets`-Attribut des `Project`-Elements an. Zum Beispiel:

   `<Project InitialTargets="Clean">`

  Sie können mehrere erste Ziele im `InitialTargets`-Attribut angeben, indem Sie die Ziele nacheinander aufführen und mithilfe eines Semikolons voneinander trennen. Die Ziele in der Liste werden nacheinander ausgeführt.

#### <a name="to-specify-more-than-one-initial-target"></a>Mehr als ein erstes Ziel angeben

- Listen Sie die ersten Ziele durch Semikolons getrennt im `InitialTargets`-Attribut des `Project`-Elements auf. Geben Sie zum Beispiel zum Ausführen des `Clean`-Ziels und anschließend des `Compile`-Ziels Folgendes ein:

     `<Project InitialTargets="Clean;Compile">`

## <a name="use-the-defaulttargets-attribute"></a>Verwenden des DefaultTargets-Attributs

 Das `DefaultTargets`-Attribut des `Project`-Elements gibt das Ziel bzw. die Ziele an, die erstellt werden, wenn ein Ziel nicht explizit in der Befehlszeile angegeben wird. Wenn sowohl im Attribut `InitialTargets` als auch im Attribut `DefaultTargets` Ziele angegeben sind und kein Ziel über die Befehlszeile angegeben wurde, führt MSBuild die im `InitialTargets`-Attribut angegebenen Ziele aus, gefolgt von den Zielen, die im `DefaultTargets`-Attribut angegeben sind.

#### <a name="to-specify-one-default-target"></a>Ein Standardziel angeben

- Geben Sie das Standardziel im `DefaultTargets`-Attribut des `Project`-Elements an. Zum Beispiel:

   `<Project DefaultTargets="Compile">`

  Sie können mehrere erste Ziele im `DefaultTargets`-Attribut angeben, indem Sie die Ziele nacheinander aufführen und mithilfe eines Semikolons voneinander trennen. Die Ziele in der Liste werden nacheinander ausgeführt.

#### <a name="to-specify-more-than-one-default-target"></a>Mehr als ein erstes Ziel angeben

- Listen Sie die ersten Ziele durch Semikolons getrennt im `DefaultTargets`-Attribut des `Project`-Elements auf. Geben Sie zum Beispiel zum Ausführen des `Clean`-Ziels und anschließend des `Compile`-Ziels Folgendes ein:

     `<Project DefaultTargets="Clean;Compile">`

## <a name="use-the--target-switch"></a>Verwenden des Schalters -target

 Wenn kein Standardziel in der Projektdatei definiert ist oder Sie das Standardziel nicht verwenden möchten, können Sie den Befehlszeilenschalter **-target** verwenden, um ein anderes Ziel anzugeben. Das Ziel oder die Ziele, die mit dem Schalter **-target** angegeben werden, werden anstelle der durch das `DefaultTargets`-Attribut angegebenen Ziele ausgeführt. Die im `InitialTargets`-Attribut angegebenen Ziele werden immer zuerst ausgeführt.

#### <a name="to-use-a-target-other-than-the-default-target-first"></a>Zuerst ein anderen Ziels und nicht das Standardziel verwenden

- Geben Sie das Ziel als das erste Ziel mithilfe des Befehlszeilenschalters **-target** an. Zum Beispiel:

     `msbuild file.proj -target:Clean`

#### <a name="to-use-several-targets-other-than-the-default-targets-first"></a>So können Sie zuerst mehrere Ziele, die nicht die Standardziele sind, verwenden

- Listen Sie die Ziele (getrennt durch Semikolons oder Kommas) mit dem Befehlszeilenschalter **-target** auf. Zum Beispiel:

     `msbuild <file name>.proj -t:Clean;Compile`

## <a name="see-also"></a>Weitere Informationen

- [MSBuild](../msbuild/msbuild.md)
- [Ziele](../msbuild/msbuild-targets.md)
- [How to: Bereinigen eines Builds](../msbuild/how-to-clean-a-build.md)
