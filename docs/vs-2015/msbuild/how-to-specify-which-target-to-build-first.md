---
title: 'Vorgehensweise: Angeben des zuerst zu erstellenden Ziels | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- DefaultTargets attribute [MSBuild]
- MSBuild, specifying the defalut target
- MSBuild, DefaultTargets attribute
ms.assetid: a580ba5b-2919-42d2-ae38-1af991e0205a
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7d7d47746aed2e663eb1fa25e3bb9ca2c6bed2c9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68178339"
---
# <a name="how-to-specify-which-target-to-build-first"></a>Gewusst wie: Angeben des zuerst zu erstellenden Ziels
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Eine Projektdatei kann ein oder mehrere `Target`-Elemente enthalten, die definieren, wie das Projekt erstellt wird. Die [!INCLUDE[vstecmsbuildengine](../includes/vstecmsbuildengine-md.md)] ( [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] )-Engine erstellt das erste gefundene Projekt und alle Abhängigkeiten, es sei denn, die Projektdatei enthält ein- `DefaultTargets` Attribut, ein- `InitialTargets` Attribut oder ein-Ziel wird in der Befehlszeile mithilfe des **/target** -Schalters angegeben.  
  
## <a name="using-the-initialtargets-attribute"></a>Verwenden des InitialTargets-Attributs  
 Das `InitialTargets`-Attribut des `Project`-Elements gibt ein Ziel an, das zuerst ausgeführt wird, auch wenn Ziele in der Befehlszeile oder im `DefaultTargets`-Attribut angegeben sind.  
  
#### <a name="to-specify-one-initial-target"></a>Angeben eines ersten Ziels  
  
- Geben Sie das Standardziel im `InitialTargets`-Attribut des `Project`-Elements an. Zum Beispiel:  
  
   `<Project InitialTargets="Clean">`  
  
  Sie können mehrere erste Ziele im `InitialTargets`-Attribut angeben, indem Sie die Ziele nacheinander aufführen und mithilfe eines Semikolons voneinander trennen. Die Ziele in der Liste werden nacheinander ausgeführt.  
  
#### <a name="to-specify-more-than-one-initial-target"></a>Mehr als ein erstes Ziel angeben  
  
- Listen Sie die ersten Ziele durch Semikolons getrennt im `InitialTargets`-Attribut des `Project`-Elements auf. Geben Sie zum Beispiel zum Ausführen des `Clean`-Ziels und anschließend des `Compile`-Ziels Folgendes ein:  
  
     `<Project InitialTargets="Clean;Compile">`  
  
## <a name="using-the-defaulttargets-attribute"></a>Verwenden des DefaultTargets-Attributs  
 Das `DefaultTargets`-Attribut des `Project`-Elements gibt das Ziel bzw. die Ziele an, die erstellt werden, wenn ein Ziel nicht explizit in der Befehlszeile angegeben wird. Wenn Ziele jeweils in `InitialTargets` und `DefaultTargets`-Attributen angegeben sind und kein Ziel in der Befehlszeile angegeben ist, führt [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] die im `InitialTargets`-Attribut angegebenen Ziele aus, gefolgt von den Zielen, die im `DefaultTargets`-Attribut angegeben sind.  
  
#### <a name="to-specify-one-default-target"></a>Ein Standardziel angeben  
  
- Geben Sie das Standardziel im `DefaultTargets`-Attribut des `Project`-Elements an. Zum Beispiel:  
  
   `<Project DefaultTargets="Compile">`  
  
  Sie können mehrere erste Ziele im `DefaultTargets`-Attribut angeben, indem Sie die Ziele nacheinander aufführen und mithilfe eines Semikolons voneinander trennen. Die Ziele in der Liste werden nacheinander ausgeführt.  
  
#### <a name="to-specify-more-than-one-default-target"></a>Mehr als ein erstes Ziel angeben  
  
- Listen Sie die ersten Ziele durch Semikolons getrennt im `DefaultTargets`-Attribut des `Project`-Elements auf. Geben Sie zum Beispiel zum Ausführen des `Clean`-Ziels und anschließend des `Compile`-Ziels Folgendes ein:  
  
     `<Project DefaultTargets="Clean;Compile">`  
  
## <a name="using-the-target-switch"></a>Verwenden des /target-Schalters  
 Wenn kein Standardziel in der Projektdatei definiert ist oder Sie dieses Standardziel nicht verwenden möchten, können Sie den Befehls Zeilenschalter **/target** verwenden, um ein anderes Ziel anzugeben. Die mit dem Schalter **/target** angegebenen Ziele werden anstelle der Ziele ausgeführt, die vom-Attribut angegeben werden `DefaultTargets` . Die im `InitialTargets`-Attribut angegebenen Ziele werden immer zuerst ausgeführt.  
  
#### <a name="to-use-a-target-other-than-the-default-target-first"></a>Zuerst ein anderen Ziels und nicht das Standardziel verwenden  
  
- Legen Sie das Ziel mithilfe des Befehls Zeilenschalters **/target** als erstes Ziel fest. Zum Beispiel:  
  
     `msbuild file.proj /target:Clean`  
  
#### <a name="to-use-several-targets-other-than-the-default-targets-first"></a>So können Sie zuerst mehrere Ziele, die nicht die Standardziele sind, verwenden  
  
- Auflisten der durch Semikolons oder Kommas getrennten Ziele mithilfe des Befehls Zeilenschalters **/target** . Zum Beispiel:  
  
     `msbuild <file name>.proj /t:Clean;Compile`  
  
## <a name="see-also"></a>Weitere Informationen
  [MSBuild](msbuild.md)  
 [Lern](../msbuild/msbuild-targets.md)   
 [Vorgehensweise: Bereinigen eines Builds](../msbuild/how-to-clean-a-build.md)
