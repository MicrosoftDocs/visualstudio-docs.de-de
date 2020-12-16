---
title: Aktualisieren von Excel-oder Word-Projekten zu .NET Framework 4,5 migriert
description: Sie müssen den Code ändern, wenn das Ziel Framework in .NET Framework 4 oder höher geändert wird, wenn Sie ein Excel-oder Word-Projekt verwenden, das bestimmte Funktionen verwendet.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7bc79a53b62cf9fb0ca0ba533a2ce0d542b08c72
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528424"
---
# <a name="update-excel-and-word-projects-that-you-migrate-to-the-net-framework-45"></a>Aktualisieren von Excel-und Word-Projekten, die Sie zum .NET Framework 4,5 migrieren
  Wenn Sie über ein Excel- oder Word-Projekt verfügen, das eine der folgenden Funktionen verwendet, müssen Sie den Code ändern, wenn das Zielframework in [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher geändert wird:

- [GetVstoObject-Methode und HasVstoObject-Methode](#GetVstoObject)

- [Generierte Klassen in Projekten auf Dokumentebene](#generatedclasses)

- [Windows Forms-Steuerelemente in Dokumenten](#winforms)

- [Ereignisse für Inhaltssteuerelemente in Word](#ccevents)

- [OLEObject-Klasse und OLEControl-Klasse](#ole)

- [Controls.Item(Object)-Eigenschaft](#itemproperty)

- [Von CollectionBase abgeleitete Auflistungen](#collections)

  Sie müssen auch den `Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute` -Verweis und den-Verweis auf die- `Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy` Klasse aus Excel-Projekten entfernen, die auf oder höher ausgerichtet sind [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . Dieses Attribut oder der Klassen Verweis wird von Visual Studio nicht für Sie entfernt.

## <a name="remove-the-excellocale1033-attribute-from-excel-projects"></a>Entfernen des ExcelLocale1033-Attributs aus Excel-Projekten
 Die wurde `Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute` aus dem Teil der Visual Studio 2010-Tools für Office-Laufzeit entfernt, die für Projektmappen verwendet wird, die auf oder höher ausgerichtet sind [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . Die Common Language Runtime (CLR) in [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] und höher übergibt immer die Gebietsschema-ID 1033 an das Excel-Objektmodell. Sie können dieses Attribut nicht mehr zum Deaktivieren dieses Verhaltens verwenden. Weitere Informationen finden Sie unter [Globalisierung und Lokalisierung von Excel-Lösungen](../vsto/globalization-and-localization-of-excel-solutions.md).

### <a name="to-remove-the-excellocale1033attribute"></a>So entfernen Sie das ExcelLocale1033Attribute

1. Öffnen Sie den **Projektmappen-Explorer**, während das Projekt in Visual Studio geöffnet ist.

2. Doppelklicken Sie unter dem Knoten **Eigenschaften** (für C#) oder dem Knoten **Mein Projekt** (für Visual Basic) auf die Codedatei "AssemblyInfo", um diese im Code-Editor zu öffnen.

    > [!NOTE]
    > In Visual Basic-Projekten müssen Sie im **Projektmappen-Explorer** auf die Schaltfläche **Alle Dateien anzeigen** klicken, um die Codedatei "AssemblyInfo" anzuzeigen.

3. Suchen Sie nach `Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute`, und entfernen Sie das Attribut aus der Datei, oder kommentieren Sie es aus.

    ```vb
    <Assembly: ExcelLocale1033Proxy(True)>
    ```

    ```csharp
    [assembly: ExcelLocale1033Proxy(true)]
    ```

## <a name="remove-a-reference-to-the-excellocal1033proxy-class"></a>Entfernen eines Verweises auf die ExcelLocal1033Proxy-Klasse
 Projekte, die mithilfe von Microsoft Visual Studio 2005-Tools für Microsoft Office System erstellt wurden, instanziieren das <xref:Microsoft.Office.Interop.Excel.Application>-Objekt von Excel mithilfe der `Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy`-Klasse. Diese Klasse wurde aus dem Teil der Visual Studio 2010-Tools für Office-Laufzeit entfernt, die für Projektmappen verwendet wird, die auf oder höher ausgerichtet sind [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . Sie müssen die Codezeilen, die auf diese Klasse verweist, daher entfernen oder auskommentieren.

### <a name="to-remove-the-reference-to-the-excellocal1033proxy-class"></a>So entfernen Sie den Verweis auf die ExcelLocal1033Proxy-Klasse

1. Öffnen Sie das Projekt in Visual Studio und dann den **Projektmappen-Explorer**.

2. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für *ThisAddIn.cs* (für c#) oder *ThisAddIn. vb* (für Visual Basic), und wählen Sie dann **Code anzeigen** aus.

3. Entfernen Sie im Code-Editor in der `VSTO generated code` -Region die folgende Codezeile, oder kommentieren Sie sie aus.

    ```vb
    Me.Application = CType(Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy.Wrap(GetType(Excel.Application), Me.Application), Excel.Application)

    ```

    ```csharp
    this.Application = (Excel.Application)Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy.Wrap(typeof(Excel.Application), this.Application);

    ```

## <a name="update-code-that-uses-the-getvstoobject-and-hasvstoobject-methods"></a><a name="GetVstoObject"></a> Aktualisieren von Code, der die GetVstoObject-Methode und HasVstoObject-Methode verwendet
 In Projekten, die auf .NET Framework 3.5 ausgerichtet sind, sind die Methoden `GetVstoObject` oder `HasVstoObject` als Erweiterungsmethoden in einem der folgenden systemeigenen Objekte Ihres Projekts verfügbar: <xref:Microsoft.Office.Interop.Word.Document>, <xref:Microsoft.Office.Interop.Excel.Workbook>, <xref:Microsoft.Office.Interop.Excel.Worksheet> oder <xref:Microsoft.Office.Interop.Excel.ListObject>. Wenn Sie diese Methoden aufrufen, müssen Sie keinen Parameter übergeben. Im folgenden Codebeispiel wird veranschaulicht, wie die GetVstoObject-Methode in einem Word-VSTO-Add-in verwendet wird, das auf die .NET Framework 3,5 abzielt.

```vb
Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _
    Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject()
```

```csharp
Microsoft.Office.Tools.Word.Document vstoDocument =
    Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject();
```

 In Projekten, die auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher ausgerichtet sind, müssen Sie den Code für den Zugriff auf diese Methoden auf eine der folgenden Weisen ändern:

- In den Objekten <xref:Microsoft.Office.Interop.Word.Document>, <xref:Microsoft.Office.Interop.Excel.Workbook>, <xref:Microsoft.Office.Interop.Excel.Worksheet>oder <xref:Microsoft.Office.Interop.Excel.ListObject> können Sie weiterhin auf diese Methoden als Erweiterungsmethoden zugreifen. Allerdings müssen Sie jetzt das von der der `Globals.Factory`-Eigenschaft zurückgegebene Objekt an diese Methoden übergeben.

  ```vb
  Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _
      Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject(Globals.Factory)
  ```

  ```csharp
  Microsoft.Office.Tools.Word.Document vstoDocument =
      Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject(Globals.Factory);
  ```

- Alternativ können Sie auch in dem von der `Globals.Factory`-Eigenschaft zurückgegebenen Objekt auf diese Methoden zugreifen. Wenn Sie auf diese Weise auf die Methoden zugreifen, müssen Sie das systemeigene Objekt, das Sie erweitern möchten, an die Methode übergeben.

  ```vb
  Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _
      Globals.Factory.GetVstoObject(Globals.ThisAddIn.Application.ActiveDocument)
  ```

  ```csharp
  Microsoft.Office.Tools.Word.Document vstoDocument =
      Globals.Factory.GetVstoObject(Globals.ThisAddIn.Application.ActiveDocument);
  ```

  Weitere Informationen finden [Sie unter Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="update-code-that-uses-instances-of-the-generated-classes-in-document-level-projects"></a><a name="generatedclasses"></a> Aktualisieren von Code, der Instanzen der generierten Klassen in Projekten auf Dokument Ebene verwendet
 In Projekten auf Dokumentebene, die auf .NET Framework 3.5 ausgerichtet sind, werden die generierten Klassen in Projekten von den folgenden Klassen in der [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]abgeleitet:

- `ThisDocument`: <xref:Microsoft.Office.Tools.Word.Document>

- `ThisWorkbook`: <xref:Microsoft.Office.Tools.Excel.Workbook>

- `Sheet`*n*:<xref:Microsoft.Office.Tools.Excel.Worksheet>

- `Chart`*n*:<xref:Microsoft.Office.Tools.Excel.ChartSheet>

  In Projekten, die auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher ausgerichtet sind, sind die oben unter [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] aufgeführten Typen Schnittstellen und keine Klassen. Generierte Klassen in Projekten, die auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher ausgerichtet sind, sind von den folgenden neuen Klassen in der [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]abgeleitet:

- `ThisDocument`: <xref:Microsoft.Office.Tools.Word.DocumentBase>

- `ThisWorkbook`: <xref:Microsoft.Office.Tools.Excel.WorkbookBase>

- `Sheet`*n*:<xref:Microsoft.Office.Tools.Excel.WorksheetBase>

- `Chart`*n*:<xref:Microsoft.Office.Tools.Excel.ChartSheetBase>

  Wenn der Code im Projekt auf eine Instanz einer der generierten Klassen als Basisklasse verweist, von der sie abgeleitet ist, müssen Sie den Code ändern.

  In einem Excel-Arbeitsmappenprojekt, das auf .NET Framework 3.5 ausgerichtet ist, verfügen Sie z. B. möglicherweise über eine Hilfsmethode, die einen Teil der Arbeitsvorgänge für Instanzen der generierten `Sheet`*n* -Klassen im Projekt ausführt.

```vb
Private Sub DoSomethingToSheet(ByVal worksheet As Microsoft.Office.Tools.Excel.Worksheet)
    ' Do something to the worksheet object.
End Sub
```

```csharp
private void DoSomethingToSheet(Microsoft.Office.Tools.Excel.Worksheet worksheet)
{
    // Do something to the worksheet object.
}
```

 Wenn Sie das Projekt neu auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher ausrichten, müssen Sie eine der folgenden Änderungen am Code vornehmen:

- Ändern Sie den Code, durch den die `DoSomethingToSheet` -Methode zum Übergeben der <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Base%2A> -Eigenschaft eines <xref:Microsoft.Office.Tools.Excel.WorksheetBase> -Objekts im Projekt aufgerufen wird. Diese Eigenschaft gibt ein <xref:Microsoft.Office.Tools.Excel.Worksheet> -Objekt zurück.

    ```vb
    DoSomethingToSheet(Globals.Sheet1.Base)
    ```

    ```csharp
    DoSomethingToSheet(Globals.Sheet1.Base);
    ```

- Ändern Sie den `DoSomethingToSheet` -Methodenparameter, damit er stattdessen ein <xref:Microsoft.Office.Tools.Excel.WorksheetBase> -Objekt erwartet.

    ```vb
    Private Sub DoSomethingToSheet(ByVal worksheet As Microsoft.Office.Tools.Excel.WorksheetBase)
        ' Do something to the worksheet object.
    End Sub
    ```

    ```csharp
    private void DoSomethingToSheet (Microsoft.Office.Tools.Excel.WorksheetBase worksheet)
    {
        // Do something to the worksheet object.
    }
    ```

## <a name="update-code-that-uses-windows-forms-controls-on-documents"></a><a name="winforms"></a> Aktualisieren von Code, der Windows Forms Steuerelemente in Dokumenten verwendet
 Sie müssen eine **using** -Anweisung (c#) oder eine **Imports** -Anweisung (Visual Basic) für den- <xref:Microsoft.Office.Tools.Excel> Namespace oder den- <xref:Microsoft.Office.Tools.Word> Namespace am Anfang jeder Codedatei hinzufügen, die die Steuerelement Eigenschaft verwendet, um dem Dokument oder Arbeitsblatt Windows Forms Steuerelemente Programm gesteuert hinzuzufügen.

 In Projekten, die auf .NET Framework 3.5 ausgerichtet sind, werden die Methoden, durch die Windows Forms-Steuerelemente (z. B. die `AddButton`-Methode) hinzugefügt werden, in den der <xref:Microsoft.Office.Tools.Excel.ControlCollection>-Klasse und <xref:Microsoft.Office.Tools.Word.ControlCollection>-Klasse definiert.

 In Projekten, die auf oder höher ausgerichtet sind [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] , handelt es sich bei diesen Methoden um Erweiterungs Methoden, die in der Steuerelement Eigenschaft verfügbar sind. Um diese Erweiterungsmethoden verwenden zu können, muss die Codedatei, in der Sie die Methoden verwenden, über die Anweisung **using** oder **Imports** für den Namespace <xref:Microsoft.Office.Tools.Excel> oder <xref:Microsoft.Office.Tools.Word> verfügen. Diese Anweisung wird automatisch in neuen Projekten generiert, die auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher ausgerichtet sind. Allerdings wird die Anweisung in Projekten, die auf .NET Framework 3.5 ausgerichtet sind, nicht automatisch hinzugefügt. Sie müssen sie bei der Neuausrichtung des Projekts hinzufügen.

 Weitere Informationen finden Sie unter [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md).

## <a name="update-code-that-handles-word-content-control-events"></a><a name="ccevents"></a> Aktualisieren von Code, der Word-Inhalts Steuerelement Ereignisse behandelt
 In Projekten, die auf .NET Framework 3.5 ausgerichtet sind, werden diese Ereignisse vom generischen <xref:System.EventHandler%601> -Delegaten behandelt. In Projekten, die auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher ausgerichtet sind, werden diese Ereignisse von anderen Delegaten behandelt.

 In der folgenden Tabelle sind die Ereignisse für Inhaltssteuerelemente in Word und die Delegaten aufgeführt, die in Projekten, die auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher ausgerichtet sind, mit den Ereignissen verknüpft sind.

|Ereignis|Delegat für Projekte unter [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] und höher|
|-----------| - |
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Added>|<xref:Microsoft.Office.Tools.Word.ContentControlAddedEventHandler>|
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.ContentUpdating>|<xref:Microsoft.Office.Tools.Word.ContentControlContentUpdatingEventHandler>|
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Deleting>|<xref:Microsoft.Office.Tools.Word.ContentControlDeletingEventHandler>|
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering>|<xref:Microsoft.Office.Tools.Word.ContentControlEnteringEventHandler>|
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Exiting>|<xref:Microsoft.Office.Tools.Word.ContentControlExitingEventHandler>|
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.StoreUpdating>|<xref:Microsoft.Office.Tools.Word.ContentControlStoreUpdatingEventHandler>|

## <a name="update-code-that-uses-the-oleobject-and-olecontrol-classes"></a><a name="ole"></a> Aktualisieren von Code, der die OLEObject-Klasse und die OLEControl-Klasse verwendet
 In Projekten, die auf .NET Framework 3.5 ausgerichtet sind, können Sie einem Dokument oder Arbeitsblatt benutzerdefinierte Steuerelemente (z. B. Windows Forms-Steuerelemente) mithilfe der Klassen `Microsoft.Office.Tools.Excel.OLEObject` und `Microsoft.Office.Tools.Word.OLEControl` hinzufügen.

 In Projekten, die auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher ausgerichtet sind, wurden diese Klassen durch die Schnittstellen <xref:Microsoft.Office.Tools.Excel.ControlSite> und <xref:Microsoft.Office.Tools.Word.ControlSite> ersetzt. Sie müssen den Code ändern, der auf `Microsoft.Office.Tools.Excel.OLEObject` und `Microsoft.Office.Tools.Word.OLEControl` verweist, damit er stattdessen auf <xref:Microsoft.Office.Tools.Excel.ControlSite> und <xref:Microsoft.Office.Tools.Word.ControlSite> verweist. Abgesehen von den neuen Namen verhalten sich diese Steuerelemente auf die gleiche Weise wie in Projekten, die auf .NET Framework 3.5 ausgerichtet sind.

 Weitere Informationen finden Sie unter [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md).

## <a name="update-code-that-uses-the-controlsitemobject-property"></a><a name="itemproperty"></a> Aktualisieren von Code, der die Controls. Item (Object)-Eigenschaft verwendet
 In Projekten, die auf .NET Framework 3,5 ausgerichtet sind, können Sie die Item-Eigenschaft (Object) des Microsoft.Office.Tools.Word.Doc-Elements verwenden. Steuert oder Auflistung `Microsoft.Office.Tools.Excel.Worksheet.Controls` , um zu bestimmen, ob ein Dokument oder Arbeitsblatt über ein angegebenes Steuerelement verfügt.

 In Projekten, die auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher ausgerichtet sind, wurde die Item-Eigenschaft (Object) aus diesen Auflistungen entfernt. Um zu ermitteln, ob ein Dokument oder Arbeitsblatt ein angegebenes Steuerelement enthält, verwenden Sie stattdessen die enthält-Methode (System. Object) der-oder-Auflistung <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> .

 Weitere Informationen über die Steuerelemente Sammlung von Dokumenten und Arbeitsblättern finden [Sie unter Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md).

## <a name="update-code-that-uses-collections-that-derive-from-collectionbase"></a><a name="collections"></a> Aktualisieren von Code, der von CollectionBase abgeleitete Auflistungen verwendet
 In Projekten, die auf .NET Framework 3,5 abzielen, werden mehrere Auflistungs Typen im [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] von der- <xref:System.Collections.CollectionBase> Klasse abgeleitet, z `Microsoft.Office.Tools.SmartTagCollection` . b., `Microsoft.Office.Tools.Excel.ControlCollection` und `Microsoft.Office.Tools.Word.ControlCollection` .

 In Projekten, die auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher ausgerichtet sind, sind diese Auflistungstypen jetzt Schnittstellen, die nicht von <xref:System.Collections.CollectionBase>abgeleitet sind. Einige Member sind für diese Auflistungstypen nicht mehr verfügbar, z. B. <xref:System.Collections.CollectionBase.Capacity%2A>, <xref:System.Collections.CollectionBase.List%2A>und <xref:System.Collections.CollectionBase.InnerList%2A>.

## <a name="see-also"></a>Weitere Informationen
- [Migrieren von Office-Projektmappen zu den .NET Framework 4 oder höher](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [Inhalts Steuerelemente](../vsto/content-controls.md)
- [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md)
