---
title: Fehlermeldungen im Workflow-Designer
description: Erfahren Sie mehr über die Arten von Fehlermeldungen, die beim Arbeiten mit Workflow-Designer auftreten können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- WFDErrorMessages.UI
- System.Activities.Presentation.ErrorActivity.UI
- System.Activities.Presentation.View.ErrorView.UI
ms.assetid: 4d8bbc2e-34fc-477f-9140-4adfd70c34a0
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8f3886739cbc6deefd13570ae0f49da7e89ad9b1
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94438034"
---
# <a name="error-messages-in-workflow-designer"></a>Fehlermeldungen im Workflow-Designer

In diesem Thema werden die Arten von Fehlermeldungen beschrieben, die beim Arbeiten mit Workflow-Designer auftreten können.

## <a name="situations-in-which-errors-in-the-workflow-designer-occur"></a>Situationen, in denen Fehler im Workflow-Designer auftreten

Fehler in Workflow-Designer in den folgenden Situationen auftreten:

1. In einem Ausdruck liegt ein Fehler vor.

2. Die Validierungseinschränkungen einer Aktivität wurden nicht erfüllt.

3. Die XAML-Datei enthält Fehler, die bewirken, dass eine Aktivität nicht geladen werden kann.

4. Die XAML-Datei enthält Fehler, die bewirken, dass der Workflow nicht geladen werden kann.

Ungültige Ausdrücke und nicht erfüllte Validierungseinschränkungen bewirken nicht, dass der Workflow nicht erstellt wird. Das Entwickeln des Workflows ist erfolgreich, aber eine <xref:System.Activities.InvalidWorkflowException> wird zur Laufzeit ausgelöst. Wenn die XAML-Datei Fehler enthält, schlägt die Erstellung fehl.

Wenn in Visual Studio ein Workflow geladen wird, werden die Fehler in der **Fehlerliste** angezeigt. Um zu der Aktivität zu navigieren, die die Fehlerquelle ist, doppelklicken Sie auf den Fehler in der **Fehlerliste**.

### <a name="expression-errors"></a>Ausdrucksfehler
 Ein ungültiger Ausdruck wird durch einen roten Kreis mit einem weißen Ausrufezeichen neben dem Ausdruck gekennzeichnet. Wenn Sie den Mauszeiger über dieses Symbol bewegen, wird ein QuickInfo angezeigt, in der die Fehlerquelle beschrieben wird. Klicken Sie in Visual Studio auf den Ausdruck, um die Zeile anzuzeigen, die die Fehlerquelle unterstreicht. Wenn Sie den Mauszeiger über den unterstrichenen Text halten, wird ein QuickInfo mit einer Beschreibung der Fehlerquelle angezeigt.

### <a name="activity-validation-errors"></a>Aktivitätsvalidierungsfehler
 Wenn die Validierungseinschränkungen einer Aktivität nicht erfüllt wurden, wird ein roter Kreis mit einem weißen Ausrufezeichen in der obersten richtigen Ecke der Aktivität angezeigt. Wenn Sie den Mauszeiger über dieses Symbol bewegen, wird ein QuickInfo angezeigt, in der die Fehlerquelle beschrieben wird.

### <a name="xaml-load-errors"></a>XAML-Ladefehler
 Wenn eine Aktivität nicht geladen werden kann, wird ein rotes Feld mit dem Text "Aktivität konnte aufgrund von Fehlern in der XAML nicht geladen werden" angezeigt. Dies tritt normalerweise auf, wenn der Typ der Aktivität nicht aufgelöst werden kann. Die ungültige Aktivität kann im Designer gelöscht werden, indem das rote Feld markiert und gelöscht wird.

### <a name="workflow-load-errors"></a>Workflow-Ladefehler
 Wenn ein Workflow nicht geladen werden kann, wird der Text "Workflow-Designer Probleme mit dem Dokument gefunden" auf der Designer Oberfläche angezeigt, zusammen mit den Ausnahme Informationen, die dazu geführt haben, dass der Workflow nicht geladen werden konnte. Dies tritt in der Regel auf, wenn die XAML-Datei nicht analysiert werden kann.
