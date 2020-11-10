---
title: 'Workflow-Designer: Gewusst wie: Verwenden des Imports-Designers'
description: Erfahren Sie, wie der Import-Designer Ihnen ermöglicht, Namespaces für die Typen einzugeben, die Sie in Ihren Ausdrücken verwenden werden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- System.Activities.Presentation.View.ImportDesigner.UI
ms.assetid: 61328ab6-9b66-4e12-8630-22e30ee8c9d1
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6bdf33227263e8158f956fa8c6509d93e8116e9b
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94437839"
---
# <a name="how-to-use-the-imports-designer"></a>Vorgehensweise: Verwenden des Imports-Designers

Der Importe-Designer ermöglicht es Ihnen, Namespaces für die Typen einzugeben, die Sie in den Ausdrücken verwenden. Ähnlich wie bei den **Imports** -oder **using** -Schlüsselwörtern in Visual Basic und c# können Sie mit dem Angeben von Namespaces im Imports-Designer einfach einen Typnamen in ihren Ausdruck anstelle eines voll qualifizierten Versions Typnamens eingeben.

Der Importe-Designer reagiert sowohl auf Änderungen, die in der Benutzeroberfläche vorgenommen werden, als auch auf Änderungen, die beim Speichern des Workflows gespeichert werden. Wenn der Workflow gespeichert wird, können dem Importe-Designer automatisch Namespaces hinzugefügt werden. Hierzu gehört Folgendes:

- Namespaces für alle Typen, die in Variablen- und Argumentdeklarationen verwendet werden.

- Namespaces für alle Typen, die in Ausdrücken verwendet werden.

- Beliebige andere Namespaces, die zum Serialisieren des Workflows erforderlich sind (z. B., Namespaces, die von benutzerdefinierten Aktivitäten im Workflow verwendet werden).

  Wenn der Workflow gespeichert wird, wird Ihnen möglicherweise auffallen, dass einige Namespaces, die Sie manuell gelöscht haben, wegen der in der vorangehenden Liste beschriebenen Logik automatisch wieder dem Importe-Designer hinzugefügt werden.

## <a name="to-add-a-namespace-to-the-list-of-imported-namespaces"></a>So fügen Sie der Liste der importierten Namespaces einen Namespace hinzu

1. Öffnen Sie eine WCF-Workflow Dienst Anwendung, eine Workflow Konsolenanwendung oder ein Aktivitäts Bibliotheksprojekt in Visual Studio oder einer neu gehosteten Workflow Anwendung.

2. Klicken Sie am unteren Rand der Haupt Canvas auf **Importe** . Der Import-Designer wird angezeigt.

3. Geben Sie einen Namespace ein, oder wählen Sie einen Namespace im Dropdownlisten-Steuerelement am oberen Rand des Import-Designers aus.

     Während der Eingabe wird eine Liste gültiger Namespaces angezeigt, die mit den eingegebenen Zeichen übereinstimmen.

4. Drücken **Sie die Eingabe** Taste, um den Namespace der Liste hinzuzufügen.

5. Wenn Sie einen Namespace aus der Liste entfernen möchten, wählen Sie den Namespace aus, und drücken Sie dann die ENTF **-Taste auf der Tastatur** . Beachten Sie, dass ein Namespace nur gelöscht werden kann, wenn er nicht gültig ist, z. B., wenn das Projekt nicht mehr auf die Assembly verweist, die den Namespace enthält.
