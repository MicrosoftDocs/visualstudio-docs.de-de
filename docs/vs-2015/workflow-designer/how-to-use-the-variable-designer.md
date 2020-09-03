---
title: 'Gewusst wie: Verwenden des Variablen-Designers | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.DesignTimeVariable.UI
ms.assetid: 0318dfb0-bf8f-4f92-9b86-ae4c1b2161ad
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4744864824da5efb238e9af1a5a12fcef79ea4ff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659072"
---
# <a name="how-to-use-the-variable-designer"></a>Vorgehensweise: Verwenden des Variablen-Designers
Der Variablen-Designer dient zum Erstellen von Variablen in Datenbindungsszenarien und bedingten Anweisungen. Der Zugriff auf den Designer erfolgt durch Klicken auf die Schaltfläche **Variablen** in der unteren linken Ecke der Entwurfs Canvas. Der Designer enthält eine Liste von Variablen, die in einem tabellarischen Format angezeigt werden, und kann nach den einzelnen Spalten Headern sortiert werden, mit Ausnahme der **Standard** Spalte. Jede Variable verfügt über einen Namen, einen Variablentyp, einen Gültigkeitsbereich und ggf. über einen Standardwert. Der Name und der Standardwert sind bearbeitbare Textfelder, der Typ und der Gültigkeitsbereich sind Dropdownlisten. Der Gültigkeitsbereich entspricht der Aktivität, die beim Aufrufen des Variablen-Designers ausgewählt wurde. Wenn eine Variable nicht innerhalb des Gültigkeitsbereichs der Auswahl erstellt werden kann, wird standardmäßig der Gültigkeitsbereich der nächsten Vorgängeraktivität der Auswahl verwendet, in dem die Variable erstellt werden kann. [!INCLUDE[crabout](../includes/crabout-md.md)] zu Variablen und Argumenten finden Sie unter [Variablen und Argumente](https://msdn.microsoft.com/library/d03dbe34-5b2e-4f21-8b57-693ee49611b8).

 Die Sortierreihenfolge wird erst übernommen, wenn der Benutzer eines der Sortiersteuerelemente explizit verwendet, den Variablen-Designer schließt und erneut öffnet oder eine andere Variable erstellt.

### <a name="to-create-a-new-variable"></a>So erstellen Sie eine neue Variable

1. Öffnen Sie in [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] eine Workflow- oder Aktivitätsprojektmappe.

2. Wählen Sie im Zeichenbereich eine Aktivität im Workflow aus.

3. Öffnen Sie den Variablen-Designer, indem Sie auf die Schaltfläche **Variablen** in der unteren linken Ecke der Entwurfs Canvas klicken. Der Variablen-Designer wird angezeigt.

4. Klicken Sie auf die leere Zeile mit der Bezeichnung **Variable erstellen**. Dadurch wird eine neue Zeile mit einer neuen Variablen mit den folgenden Standardwerten hinzugefügt: VariableX für den **Namen** , wobei x eine ganze Zahl mit einem Anfangswert von 1 ist, der automatisch inkrementiert wird, um eindeutige Variablennamen, **Zeichenfolge** für den **Variablentyp**und **Sequenz** für den **Bereich**zu erstellen. Für den **Standard**Wert wird kein Wert hinzugefügt. Sie können diese Werte jederzeit während des Workflowentwurfs ändern.

    > [!NOTE]
    > Wählen Sie zum Löschen einer Variablen die Variable aus, indem Sie darauf klicken, und drücken Sie dann die ENTF **-Taste.**

## <a name="see-also"></a>Weitere Informationen
 Verwenden [der Workflow-Designer](../workflow-designer/using-the-workflow-designer.md) [Variablen und Argumente](https://msdn.microsoft.com/library/d03dbe34-5b2e-4f21-8b57-693ee49611b8) Gewusst [wie: Verwenden des Argument-Designers](../workflow-designer/how-to-use-the-argument-designer.md)