---
title: ParallelForEach &lt; T- &gt; Aktivitäts Designer | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ParallelForEach`1.UI
ms.assetid: e93a4843-aef2-4d3e-9a0a-a2d3d1411aa7
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4c659e941a8503a0d5ff601fea23fcec69b2bbcf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672611"
---
# <a name="parallelforeachlttgt-activity-designer"></a>ParallelForEach &lt; T- &gt; Aktivitäts Designer
Die <xref:System.Activities.Statements.ParallelForEach%601>-Aktivität listet die Elemente einer Auflistung auf und führt gleichzeitig, asynchron im gleichen Thread, eine eingebettete Anweisung für jedes Element der Auflistung aus. Verwenden Sie diese Flusssteuerungsaktivität statt der <xref:System.Activities.Statements.Sequence>-Aktivität, wenn von den untergeordneten Aktivitäten dieser Aktivität erwartet werden kann, dass sie in den Leerlauf übergehen.

 Die <xref:System.Activities.Statements.ParallelForEach%601>-Aktivität verfügt über die <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>-Eigenschaft, die einen benutzerdefinierten [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]-Ausdruck enthält. Die <xref:System.Activities.Statements.ParallelForEach%601>-Aktivität wertet diese Eigenschaft aus, nachdem alle Branches abgeschlossen sind. Wenn **true**ausgewertet wird, wird die- <xref:System.Activities.Statements.ParallelForEach%601> Aktivität abgeschlossen, ohne dass die anderen Verzweigungen ausgeführt werden. Wenn das-Element <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> nicht als **true**ausgewertet wird, wird die-Aktivität abgeschlossen, <xref:System.Activities.Statements.ParallelForEach%601> Wenn alle untergeordneten Aktivitäten abgeschlossen sind.

## <a name="the-parallelforeacht-activity"></a>Die ParallelForEach- \<T> Aktivität
 <xref:System.Activities.Statements.ParallelForEach%601> Listet seine Werte auf und plant den <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> für jeden Wert, auf den er aufzählt. Es wird nur der <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> geplant. Wie der Textkörper ausgeführt wird, hängt davon ab, ob der <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> in den Leerlauf übergeht.

 Geht der <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> nicht in den Leerlauf über, erfolgt die Ausführung in umgekehrter Reihenfolge, da die geplanten Aktivitäten als Stapel behandelt werden, also die letzte geplante Aktivität als erste ausgeführt wird. Wenn Sie z. b. über eine Auflistung von {1,2,3,4} in verfügen <xref:System.Activities.Statements.ParallelForEach%601> und eine " **Write teline** " als Text verwenden, um den Wert zu schreiben. Sie haben 4, 3, 2, 1 in der Konsole gedruckt. Dies liegt daran, dass die Schreibweise nicht **in** den Leerlauf wechselt, sodass nach der Planung von vier **Schreib** Voraktivitäten die Ausführung mit einem Stapel Verhalten (zuerst in der letzten Ausgabe) erfolgt ist.

 Wenn aber Aktivitäten im <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> in den Leerlauf übergehen können, etwa eine <xref:System.ServiceModel.Activities.Receive>-Aktivität oder eine <xref:System.Activities.Statements.Delay>-Aktivität, ergibt sich Folgendes. Dann ist es nicht notwendig, auf den Abschluss zu warten. <xref:System.Activities.Statements.ParallelForEach%601> versucht dann, die nächste geplante Textkörperaktivität auszuführen. Wenn auch diese in den Leerlauf übergeht, bewegt sich <xref:System.Activities.Statements.ParallelForEach%601> zum Textkörper der nächsten Aktivität.

### <a name="using-the-parallelforeacht-activity-designer"></a>Verwenden des ParallelForEach- \<T> Aktivitäts Designers
 Der **ParallelForEach \<T> ** -Aktivitäts Designer befindet sich in der Kategorie **Ablauf Steuerung** der **Toolbox**, auf die Sie zugreifen können, indem Sie auf der linken Seite von auf die Registerkarte **Toolbox** klicken (Sie können auch im [!INCLUDE[wfd2](../includes/wfd2-md.md)] Menü **Ansicht** den Befehl **Symbolleiste** auswählen oder STRG + ALT + X drücken).

 Der **ParallelForEach \<T> ** -Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der- [!INCLUDE[wfd2](../includes/wfd2-md.md)] Oberfläche dort abgelegt werden, wo Aktivitäts Designer normalerweise platziert werden, z. b. innerhalb eines **Sequence** -Aktivitäts Designers. Nach dem Ablegen in [!INCLUDE[wfd2](../includes/wfd2-md.md)] wird eine-Aktivität erstellt <xref:System.Activities.Statements.ParallelForEach%601> , die standardmäßig eine <xref:System.Activities.Activity.DisplayName%2A> von **ParallelForEach enthält \<Int32> .**

### <a name="parallelforeacht-properties-in-the-workflow-designer"></a>ParallelForEach- \<T> Eigenschaften im Workflow-Designer
 In der folgenden Tabelle werden die nützlichsten Eigenschaften der <xref:System.Activities.Statements.ParallelForEach%601>-Aktivität aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.

|Eigenschaftenname|Erforderlich|Verbrauch|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Falsch|Gibt den benutzerfreundlichen Anzeigenamen des Aktivitätsdesigners im Header an. Der Standardwert ist **ParallelForEach \<Int32> **. Der Wert kann optional im **Eigenschaften** Raster oder direkt im Header des Aktivitäts Designers bearbeitet werden.|
|<xref:System.Activities.Statements.ParallelForEach%601.Body%2A>|Falsch|Die Aktivität, die für jedes Element in der Auflistung ausgeführt werden soll. Um die-Aktivität hinzuzufügen, legen Sie <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> eine Aktivität aus der Toolbox in das Feld **Body** mit dem Hinweis Text "Aktivität hier ablegen" des **ParallelForEach \<T> ** -Aktivitäts Designers ab.|
|**TypeArgument**|Richtig|Der Typ der Elemente in der Auflistung, die <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> durch den generischen Parameter *T*angegeben werden. Standardmäßig ist **TypeArgument** auf **Int32**festgelegt. Um den Typ T im **ParallelForEach \<T> ** -Aktivitäts Designer zu ändern, ändern Sie den Wert des Kombinations Felds **TypeArgument** im Eigenschaften Raster.|
|<xref:System.Activities.Statements.ParallelForEach%601.Values%2A>|Richtig|Die Auflistung, deren Elemente durchlaufen werden. Um den festzulegen, geben Sie im Feld <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] **Werte** des **ForEach \<T> ** -Aktivitäts Designers im Feld mit dem Hinweis Text "VB-Ausdruck eingeben" oder im Feld " **Werte** " im **Eigenschaften** Fenster einen-Ausdruck ein.|
|<xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>||Die Auswertung erfolgt nach Abschluss der einzelnen Iterationen. Ergibt die Auswertung True, werden die geplanten ausstehenden Iterationen abgebrochen. Wenn diese Eigenschaft nicht festgelegt ist, werden alle geplanten Anweisungen bis zur Beendigung ausgeführt.|

 Standardmäßig hat der Schleifeniterator die Bezeichnung "item". Sie können den Namen der Iteratorvariablen im Feld **foreach** des **ParallelForEach \<T> ** -Aktivitäts Designers ändern. Der Schleifeniterator kann in den untergeordneten Elementen der <xref:System.Activities.Statements.ParallelForEach%601>-Aktivität in Ausdrücken verwendet werden.

## <a name="see-also"></a>Weitere Informationen
 [Sequence](../workflow-designer/sequence-activity-designer.md) [Parallele](../workflow-designer/parallel-activity-designer.md) Ablauf [Steuerung](../workflow-designer/control-flow-activity-designers.md) der Sequenz