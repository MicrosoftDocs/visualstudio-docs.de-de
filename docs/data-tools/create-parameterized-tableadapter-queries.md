---
title: Erstellen von parametrisierten TableAdapter-Abfragen
description: Informationen zum Erstellen von parametrisierten TableAdapter-Abfragen. Eine parametrisierte Abfrage gibt Daten zurück, die den Bedingungen einer WHERE-Klausel in der Abfrage entsprechen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], TableAdapters
- TableAdapters, parameterized queries
- data [Visual Studio], searching data
- queries [Visual Studio], creating
- TableAdapters, searching data
- queries [Visual Studio], TableAdapters
ms.assetid: 104d1d19-b5a9-4071-b81e-1b3af08e9c7b
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: e6eb2f6e1358c91a1103615aca67ede4a3561fae
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94436666"
---
# <a name="create-parameterized-tableadapter-queries"></a>Erstellen von parametrisierten TableAdapter-Abfragen

Eine parametrisierte Abfrage gibt Daten zurück, die den Bedingungen einer WHERE-Klausel in der Abfrage entsprechen. Sie können beispielsweise eine Kundenliste parametrisieren, sodass nur Kunden in einem bestimmten Ort angezeigt werden. Fügen Sie dazu `WHERE City = @City` am Ende der SQL-Anweisung hinzu, was eine Liste von Kunden ausgibt.

Sie erstellen parametrisierte TableAdapter-Abfragen in der **DataSet-Designer**. Sie können Sie auch in einer Windows-Anwendung mit dem Befehl **Datenquelle parametrisieren** im Menü **Daten** erstellen. Mit dem Befehl **parameterize Data Source** werden Steuerelemente auf dem Formular erstellt, in die Sie die Parameterwerte eingeben und die Abfrage ausführen können.

> [!NOTE]
> Verwenden Sie beim Erstellen einer parametrisierten Abfrage die-Parameter Notation, die für die Datenbank spezifisch ist, für die Sie programmieren. Zum Beispiel verwenden Access- und OleDb-Datenquellen das Fragezeichen (?) zur Angabe von Parametern, sodass die WHERE-Klausel wie folgt aussieht: `WHERE City = ?`.

## <a name="create-a-parameterized-tableadapter-query"></a>Erstellen einer parametrisierten TableAdapter-Abfrage

### <a name="to-create-a-parameterized-query-in-the-dataset-designer"></a>So erstellen Sie parametrisierte Abfrage im DataSet-Designer

- Erstellen Sie einen neuen TableAdapter und fügen Sie eine WHERE-Klausel mit den gewünschten Parametern zur SQL-Anweisung hinzu. Weitere Informationen finden Sie unter [Erstellen und Konfigurieren von TableAdapters](../data-tools/create-and-configure-tableadapters.md).

     \- oder -

- Fügen Sie eine Abfrage zu einem vorhandenen TableAdapter hinzu und dann eine WHERE-Klausel mit den gewünschten Parametern für die SQL-Anweisung.

### <a name="to-create-a-parameterized-query-while-designing-a-data-bound-form"></a>So erstellen Sie eine parametrisierte Abfrage beim Entwerfen eines datengebundenen Formulars

1. Wählen Sie ein Steuerelement auf dem Formular, das bereits an ein Dataset gebunden ist. Weitere Informationen finden Sie unter [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).

2. Wählen Sie im Menü **Daten** die Option **Abfrage hinzufügen** aus.

3. Füllen Sie das Dialogfeld **Suchkriterien-Generator** aus, und fügen Sie dann eine WHERE-Klausel mit den gewünschten Parametern für die SQL-Anweisung hinzu.

### <a name="to-add-a-query-to-an-existing-data-bound-form"></a>So fügen Sie eine Abfrage einem vorhandenen datengebundenen Formular hinzu

1. Öffnen Sie das Formular im **Windows Forms-Designer**.

2. Wählen Sie im Menü **Daten** die Option Abfrage oder **Smarttags für Daten** **Hinzufügen** aus.

    > [!NOTE]
    > Wenn **Abfrage hinzufügen** im Menü **Daten** nicht verfügbar ist, wählen Sie ein Steuerelement auf dem Formular, das die Datenquelle anzeigt, der Sie die Parametrisierung hinzufügen möchten. Wenn das Formular beispielsweise Daten in einem <xref:System.Windows.Forms.DataGridView>-Steuerelement anzeigt, wählen Sie dieses aus. Wenn das Formular Daten in einzelnen Steuerelementen anzeigt, wählen Sie irgendein datengebundenes Steuerelement.

3. Wählen Sie im Bereich **Datenquellen Tabelle auswählen** die Tabelle aus, der Sie die Parametrisierung hinzufügen möchten.

4. Geben Sie den Namen in das Feld **Neuer Abfragename** ein, wenn Sie eine neue Abfrage erstellen.

     \- oder -

     Wählen Sie eine Abfrage im Feld **Vorhandener Abfragename** aus.

5. Geben Sie im **Textfeld Abfrage** eine Abfrage ein, die Parameter annimmt.

6. Klicken Sie auf **OK**.

     Es wird ein Steuerelement für die Eingabe des Parameters sowie eine Schaltfläche **Laden** zum Formular in einem <xref:System.Windows.Forms.ToolStrip>-Steuerelement hinzugefügt.

### <a name="query-for-null-values"></a>Abfragen von NULL-Werten

TableAdapter-Parametern können NULL-Werte zugewiesen werden, wenn Sie Datensätze Abfragen möchten, die über keinen aktuellen Wert verfügen. Sehen Sie sich beispielsweise die folgende Abfrage mit einem `ShippedDate` Parameter in der- `WHERE` Klausel an:

```sql
SELECT CustomerID, OrderDate, ShippedDate
FROM Orders
WHERE (ShippedDate = @ShippedDate) OR (ShippedDate IS NULL)
```

Wenn es sich um eine Abfrage für einen TableAdapter handelt, könnten Sie alle Bestellungen Abfragen, die nicht mit folgendem Code ausgeliefert wurden:

[!code-csharp[VbRaddataTableAdapters#8](../data-tools/codesnippet/CSharp/create-parameterized-tableadapter-queries_1.cs)]
[!code-vb[VbRaddataTableAdapters#8](../data-tools/codesnippet/VisualBasic/create-parameterized-tableadapter-queries_1.vb)]

So aktivieren Sie eine Abfrage, um NULL-Werte zu akzeptieren:

1. Wählen Sie im **DataSet-Designer** die TableAdapter-Abfrage aus, die NULL-Parameterwerte akzeptieren muss.

2. Wählen Sie im Fenster **Eigenschaften** **die Option** **Parameter** aus, und klicken Sie dann auf die Schaltfläche mit den Auslassungs Punkten ( **...** ).

3. Wählen Sie den Parameter, der NULL-Werte zulässt, und legen Sie die **AllowDBNull** -Eigenschaft auf fest `true` .

## <a name="see-also"></a>Siehe auch

- [Füllen von Datasets mit TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)
