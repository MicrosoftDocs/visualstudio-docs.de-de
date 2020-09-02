---
title: 'Gewusst wie: Zuordnen von Schemas zu Arbeitsblättern in Visual Studio'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML schemas [Office development in Visual Studio], mapping
- mappings [Office development in Visual Studio], XML schemas to Excel worksheets
- Excel [Office development in Visual Studio], XML schemas
- worksheets [Office development in Visual Studio], XML schemas
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c8a0437b940953e89e24969314f63df34d223496
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85538137"
---
# <a name="how-to-map-schemas-to-worksheets-inside-visual-studio"></a>Gewusst wie: Zuordnen von Schemas zu Arbeitsblättern in Visual Studio
  Sie können ein XML-Schema einem Arbeitsblatt zuordnen, während das Arbeitsblatt in Visual Studio geöffnet ist. Sie verwenden die gleichen Microsoft Office Excel-Tools, die Sie verwenden, wenn die Arbeitsmappe außerhalb von Visual Studio geöffnet ist. Das Office-Projekt erstellt dieselben Objekte, unabhängig davon, ob Sie das Schema vor oder nach dem Erstellen der Excel-Lösung dem Arbeitsblatt zuordnen.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

> [!NOTE]
> Sie können keine mehrteiligen XML-Schemas in Excel-Lösungen verwenden.

## <a name="to-map-an-xml-schema-to-an-excel-worksheet-in-visual-studio"></a>So ordnen Sie ein XML-Schema einem Excel-Arbeitsblatt in Visual Studio zu

1. Öffnen Sie die Excel-Arbeitsmappe oder das Vorlagen Projekt in Visual Studio.

2. Klicken Sie in das Arbeitsblatt, um den Fokus auf den Designer zu verschieben.

3. Klicken Sie im Menüband auf die Registerkarte **Entwickler** .

    > [!NOTE]
    > Wenn die Registerkarte **Entwickler** nicht sichtbar ist, müssen Sie diese zuerst anzeigen. Weitere Informationen finden Sie unter Gewusst [wie: Anzeigen der Registerkarte "Entwickler" im Menüband](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

4. Klicken Sie in der Gruppe **XML** auf **Quelle**.

     Das Fenster " **XML-Quelle** " wird geöffnet.

5. Klicken Sie im Fenster **XML-Quelle** auf **XML**-Zuordnungen.

     Das Dialogfeld **XML** -Zuordnungen wird geöffnet.

6. Klicken Sie im Dialogfeld **XML** -Zuordnungen auf **Hinzufügen**.

7. Navigieren Sie zu ihrer Schema Datei, wählen Sie Sie aus, und klicken Sie dann auf **Öffnen**.

8. Klicken Sie auf **OK**.

     Das Schema wird im XML- **Quell** Code Fenster dargestellt. In Ihrem Projekt wird ein typisiertes <xref:System.Data.DataSet> basierend auf dem Schema generiert, und eine <xref:System.Windows.Forms.BindingSource> wird erstellt.

9. Ziehen Sie Elemente aus dem **XML-Quell** Code Fenster an die Orte in Ihrem Arbeitsblatt, an denen die entsprechenden Steuerelemente erstellt werden sollen.

     Wenn Sie ein nicht wiederholendes Schema Element ziehen, generiert das Office-Projekt ein Steuerelement, <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> das automatisch an gebunden ist <xref:System.Windows.Forms.BindingSource> .

     Wenn Sie ein sich wiederholendes Schema Element ziehen, generiert das Office-Projekt ein Steuerelement, <xref:Microsoft.Office.Tools.Excel.ListObject> das nicht automatisch an eine Datenquelle gebunden ist. Weitere Informationen finden Sie unter [XML-Schemas und-Daten in Anpassungen auf Dokument Ebene](../vsto/xml-schemas-and-data-in-document-level-customizations.md).

## <a name="see-also"></a>Weitere Informationen
- [Gewusst wie: Zuordnen von Schemas zu Word-Dokumenten in Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [XML-Schemas und-Daten in Anpassungen auf Dokument Ebene](../vsto/xml-schemas-and-data-in-document-level-customizations.md)
