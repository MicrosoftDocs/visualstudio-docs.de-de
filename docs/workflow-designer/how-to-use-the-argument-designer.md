---
title: 'Workflow-Designer: Gewusst wie: Verwenden des Argument-Designers'
description: Erfahren Sie mehr über den Argument-Designer und die Verwendung des Argument-Designers, um zuzulassen, dass Daten in eine und aus einer Aktivität fließen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- System.Activities.Presentation.View.ArgumentDesigner.UI
- System.Activities.Presentation.View.DesignTimeArgument.UI
ms.assetid: 64813fd5-1ea1-499a-98b4-ab2a44b7ee5e
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9b97368a942747046aa7641771f84a9f2ed41e11
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894100"
---
# <a name="how-to-use-the-argument-designer"></a>Vorgehensweise: Verwenden des Argument-Designers

Mit dem Argument-Designer können Daten problemlos in eine und aus einer Aktivität fließen. Greifen Sie auf den Designer zu, indem Sie auf die Schaltfläche **Argumente** in der linken unteren Ecke der Entwurfs Canvas klicken. Der Designer enthält eine Liste von Argumenten, die in tabellarischer Form angezeigt werden und nach den einzelnen Spaltenüberschriften sortiert werden können, mit Ausnahme der **Standardwert** Spalte. Für jedes Argument werden der Name, die Richtung (ein/aus/ein/aus/Eigenschaft), der Typ und ein Standardausdruckswert (sofern vorhanden) angegeben. Der Name und der Standardausdruckswert sind bearbeitbare Textfelder, und der Typ und die Richtung sind Dropdownlisten. Weitere Informationen finden Sie unter [Variablen und Argumente (.net)](/dotnet/framework/windows-workflow-foundation/variables-and-arguments).

## <a name="to-create-a-new-argument"></a>So erstellen Sie ein neues Argument

1. Öffnen Sie in Visual Studio eine Workflow-oder Aktivitäts Lösung.

2. Öffnen Sie den Argument-Designer, indem Sie auf die Schaltfläche **Argumente** in der linken unteren Ecke der Entwurfs Canvas klicken. Der Argument-Designer wird angezeigt.

3. Klicken Sie auf die leere Zeile mit der Bezeichnung **Create Argument**. Dadurch wird eine neue Zeile mit einem neuen Argument mit den folgenden Standardwerten hinzugefügt: argumentx für den **Namen** , wobei x eine ganze Zahl mit einem Anfangswert von 1 ist, der automatisch erhöht wird, um eindeutige Argument Namen zu erstellen, **in** für die **Richtung** und **Zeichenfolge** für den **Argumenttyp**. Für den **Standardwert** wird kein Wert hinzugefügt. Sie können diese Werte jederzeit während des Workflowentwurfs ändern.

    > [!NOTE]
    > Wählen Sie zum Löschen eines Arguments das Argument aus, indem Sie darauf klicken, und drücken Sie dann die ENTF **-Taste.**

## <a name="see-also"></a>Weitere Informationen

- [Verwenden des Workflow-Designers](developing-applications-with-the-workflow-designer.md)
- [Variablen und Argumente](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)
