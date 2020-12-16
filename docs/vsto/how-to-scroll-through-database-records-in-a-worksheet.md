---
title: 'Gewusst wie: Scrollen durch Datenbankdaten Sätze in einem Arbeitsblatt'
description: Erfahren Sie, wie Sie den Designer verwenden können, um ein einzelnes Feld aus einer Datenbanktabelle in einem Microsoft Excel-Arbeitsblatt anzuzeigen.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- databases [Office development in Visual Studio], scrolling records
- records [Office development in Visual Studio], scrolling
- data [Office development in Visual Studio], scrolling database records
- worksheets [Office development in Visual Studio], scrolling records
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 536a3cca0337e8879e64cbc3ffc15b8411c201b6
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528175"
---
# <a name="how-to-scroll-through-database-records-in-a-worksheet"></a>Gewusst wie: Scrollen durch Datenbankdaten Sätze in einem Arbeitsblatt
  Im folgenden Verfahren wird gezeigt, wie der-Designer verwendet wird, um ein einzelnes Feld aus einer Datenbanktabelle in einem Microsoft Office Excel-Arbeitsblatt mit Steuerelementen anzuzeigen, die es dem Endbenutzer ermöglichen, einen Bildlauf durch alle Datensätze auszuführen.

 Der Designer kann nur in Projekten auf Dokument Ebene verwendet werden. Sie können jedoch auch Steuerelemente hinzufügen und diese zur Laufzeit Programm gesteuert an Daten binden. Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: einfache Datenbindung in einem VSTO-Add-in-Projekt](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md).

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

## <a name="to-scroll-through-database-records-in-a-worksheet"></a>So Scrollen Sie durch Datenbankdaten Sätze in einem Arbeitsblatt

1. Öffnen Sie ein Excel-Anwendungsprojekt in Visual Studio.

2. Öffnen Sie das Fenster **Datenquellen** , und erstellen Sie eine Datenquelle aus der Datenbank. Weitere Informationen finden Sie unter [Hinzufügen neuer Verbindungen](../data-tools/add-new-connections.md).

3. Erweitern Sie die Tabelle, die die Daten enthält, die Sie anzeigen möchten, und wählen Sie die jeweilige Spalte aus.

4. Öffnen Sie die Liste der Steuerelemente, und wählen Sie **NamedRange** aus.

5. Ziehen <xref:Microsoft.Office.Tools.Excel.NamedRange> Sie das Steuerelement auf die Zelle, in der die Daten angezeigt werden sollen.

6. Fügen Sie auf der Registerkarte **Windows Forms** der **Toolbox** dem <xref:System.Windows.Forms.BindingNavigator> Arbeitsblatt ein-Steuerelement hinzu, und richten Sie die Steuerelemente ein, die Sie verwenden möchten. Weitere Informationen finden Sie unter [Übersicht über das BindingNavigator-Steuerelement &#40;Windows Forms&#41;](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms).

## <a name="see-also"></a>Weitere Informationen
- [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)
