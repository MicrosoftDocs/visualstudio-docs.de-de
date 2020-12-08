---
title: Anpassen von Features der Benutzeroberfläche mithilfe von Erweiterbarkeits Schnittstellen
description: Erfahren Sie, dass die Office-Entwicklungs Tools in Visual Studio Erweiterbarkeits Schnittstellen bereitstellen, die Sie beim Anpassen von Benutzeroberflächen Funktionen unterstützen.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ICustomTaskPaneConsumer interface
- IRibbonExtensibility interface
- UI customizing [Office development in Visual Studio]
- user interfaces [Office development in Visual Studio], customizing
- application-level add-ins [Office development in Visual Studio], extensibility interfaces
- customizing UI features [Office development in Visual Studio]
- FormRegionStartup interface
- add-ins [Office development in Visual Studio], extensibility interfaces
- extensibility interfaces [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 436f426eee6c90476997f416bab907c8e17f94cc
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845621"
---
# <a name="customize-ui-features-by-using-extensibility-interfaces"></a>Anpassen von Features der Benutzeroberfläche mithilfe von Erweiterbarkeits Schnittstellen
  Die Office-Entwicklungstools in Visual Studio umfassen Klassen und Designer, mit denen viele Implementierungsdetails behandelt werden können, wenn Sie sie zum Erstellen von benutzerdefinierten Aufgabenbereichen, Menübandanpassungen und Outlook-Formularbereichen in einem VSTO-Add-In verwenden. Sie können jedoch zudem die *Erweiterbarkeitsschnittstelle* manuell für jede Funktion implementieren, wenn Sie über besondere Anforderungen verfügen.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

## <a name="overview-of-extensibility-interfaces"></a>Übersicht über Erweiterbarkeits Schnittstellen
 Microsoft Office definiert eine Gruppe von Erweiterbarkeitsschnittstellen, die COM-VSTO-Add-Ins implementieren können, um bestimmte Funktionen wie das Menüband anzupassen. Diese Schnittstellen bieten die vollständige Kontrolle über die Funktionen, auf die sie den Zugriff gewähren. Die Implementierung dieser Schnittstellen erfordert jedoch das entsprechende Know-how in Bezug auf die COM-Interoperabilität in verwalteten Code. In einigen Fällen ist das Programmierungsmodell von diesen Schnittstellen auch nicht intuitiv für Entwickler, die an .NET Framework gewöhnt sind.

 Wenn Sie ein VSTO-Add-In erstellen, indem Sie die Office-Projektvorlagen in Visual Studio verwenden, müssen Sie nicht die Erweiterbarkeitsschnittstellen implementieren, um Funktionen wie das Menüband anzupassen. Die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] implementiert diese Schnittstellen für Sie. Sie können stattdessen intuitivere Klassen und Designer verwenden, die Visual Studio bereitstellt. Sie können die Erweiterbarkeitsschnittstellen bei Bedarf jedoch direkt in Ihr VSTO-Add-In implementieren.

 Weitere Informationen zu den Klassen und Designern, die Visual Studio für diese Funktionen bereitstellt, finden Sie unter [benutzerdefinierte Aufgaben](../vsto/custom-task-panes.md)Bereiche, [Menüband-Designer](../vsto/ribbon-designer.md)und [Erstellen von Outlook-Formular](../vsto/creating-outlook-form-regions.md)Bereichen.

## <a name="extensibility-interfaces-you-can-implement-in-a-vsto-add-in"></a>Erweiterbarkeits Schnittstellen, die Sie in einem VSTO-Add-in implementieren können
 Die folgende Tabelle führt die Erweiterbarkeitsschnittstellen auf, die Sie implementieren können, sowie die Anwendungen, die sie unterstützen.

|Schnittstelle|BESCHREIBUNG|Anwendungen|
|---------------|-----------------|------------------|
|<xref:Microsoft.Office.Core.IRibbonExtensibility>|Implementieren Sie diese Schnittstelle zum Anpassen der Menüband-Benutzeroberfläche. **Hinweis:**  Sie können einem Projekt ein Menü **Band Element (XML)** hinzufügen, um eine Standard <xref:Microsoft.Office.Core.IRibbonExtensibility> Implementierung in Ihrem VSTO-Add-in zu generieren. Weitere Informationen finden Sie unter [Ribbon XML](../vsto/ribbon-xml.md).|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> InfoPath 2010<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Project<br /><br /> Visio<br /><br /> Word|
|<xref:Microsoft.Office.Core.ICustomTaskPaneConsumer>|Implementieren Sie diese Schnittstelle zum Erstellen eines benutzerdefinieren Aufgabenbereichs.|Excel<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Word|
|<xref:Microsoft.Office.Interop.Outlook.FormRegionStartup>|Implementieren Sie diese Schnittstelle zum Erstellen eines Outlook-Formularbereichs.|Outlook|

 Es gibt verschiedene andere Erweiterbarkeitsschnittstellen, die durch Microsoft Office definiert werden, beispielsweise <xref:Microsoft.Office.Core.IBlogExtensibility>, <xref:Microsoft.Office.Core.EncryptionProvider>und <xref:Microsoft.Office.Core.SignatureProvider>. Visual Studio unterstützt nicht die Implementierung dieser Schnittstellen in einem VSTO-Add-In, das mithilfe der Office-Projektvorlagen erstellt wurde.

## <a name="use-extensibility-interfaces"></a>Verwenden von Erweiterbarkeits Schnittstellen
 Implementieren Sie zum Anpassen einer Benutzeroberflächenfunktion mithilfe einer Erweiterbarkeitsschnittstelle die entsprechende Schnittstelle in Ihrem VSTO-Add-In-Projekt. Überschreiben Sie anschließend die Methode <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> , um eine Instanz der Klasse zurückzugeben, die die Schnittstelle implementiert.

 Eine Beispielanwendung, die die Implementierung der <xref:Microsoft.Office.Core.IRibbonExtensibility> <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> -,-und- <xref:Microsoft.Office.Interop.Outlook.FormRegionStartup> Schnittstellen in einem VSTO-Add-in für Outlook veranschaulicht, finden Sie im Beispiel UI Manager unter [Office-Entwicklungs Beispiele](../vsto/office-development-samples.md).

### <a name="example-of-implementing-an-extensibility-interface"></a>Beispiel für das Implementieren einer Erweiterbarkeits Schnittstelle
 Das folgende Codebeispiel veranschaulicht eine einfache Implementierung der <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> -Schnittstelle zum Erstellen eines benutzerdefinierten Aufgabenbereichs. Im Beispiel werden zwei Klassen definiert:

- Die `TaskPaneHelper` -Klasse implementiert <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> zum Erstellen und Anzeigen eines benutzerdefinierten Aufgabenbereichs.

- Die `TaskPaneUI` -Klasse stellt die Benutzeroberfläche des Aufgabenbereichs bereit. Die Attribute für die `TaskPaneUI` -Klasse machen die Klasse sichtbar für COM, wodurch Microsoft Office-Anwendungen die Klasse erkennen können. In diesem Beispiel ist die Benutzeroberfläche ein leeres <xref:System.Windows.Forms.UserControl>. Sie können jedoch Steuerelemente hinzufügen, indem Sie den Code ändern.

  > [!NOTE]
  > Damit die `TaskPaneUI` -Klasse für COM verfügbar ist, müssen Sie zudem die Eigenschaft **Für COM-Interop registrieren** für das Projekt festlegen.

  [!code-vb[Trin_SimpleExtensibilityInterface#1](../vsto/codesnippet/VisualBasic/Trin_SimpleExtensibilityInterface/ThisAddIn.vb#1)]
  [!code-csharp[Trin_SimpleExtensibilityInterface#1](../vsto/codesnippet/CSharp/Trin_SimpleExtensibilityInterface/ThisAddIn.cs#1)]

  Weitere Informationen zum Implementieren von <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> finden Sie unter [Erstellen von benutzerdefinierten Aufgabenbereichen im 2007 Office-System](/previous-versions/office/developer/office-2007/aa338197(v=office.12)) in der Microsoft Office-Dokumentation.

### <a name="example-of-overriding-the-requestservice-method"></a>Beispiel für das Überschreiben der RequestService-Methode
 Das folgende Codebeispiel veranschaulicht, wie die Methode <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> überschrieben wird, um eine Instanz der Klasse `TaskPaneHelper` aus dem vorherigen Codebeispiel zurückzugeben. Es prüft die Werte des Parameters *serviceGuid* , um zu bestimmen, welche Schnittstelle angefordert wird, und gibt dann ein Objekt zurück, das diese Schnittstelle implementiert.

 [!code-vb[Trin_SimpleExtensibilityInterface#2](../vsto/codesnippet/VisualBasic/Trin_SimpleExtensibilityInterface/ThisAddIn.vb#2)]
 [!code-csharp[Trin_SimpleExtensibilityInterface#2](../vsto/codesnippet/CSharp/Trin_SimpleExtensibilityInterface/ThisAddIn.cs#2)]

## <a name="see-also"></a>Siehe auch
- [Office-Entwicklungs Beispiele und Exemplarische Vorgehensweisen](../vsto/office-development-samples-and-walkthroughs.md)
- [Program mieren von VSTO-Add-ins](../vsto/programming-vsto-add-ins.md)
- [Entwickeln von Office-Lösungen](../vsto/developing-office-solutions.md)
- [Code in VSTO-Add-Ins aus anderen Office-Projektmappen aufzurufen](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)
- [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)
