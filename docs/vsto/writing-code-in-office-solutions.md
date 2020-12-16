---
title: Schreiben von Code in Office-Lösungen
description: Erfahren Sie, wie Sie Code in Microsoft Office Lösungen schreiben und erfahren, wie die Office-Objekt Modelle im verwalteten Code verfügbar gemacht werden.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.Project.RefactoringCancelled
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], writing code
- managed code [Office development in Visual Studio]
- Office development in Visual Studio, programming languages supported
- Office applications [Office development in Visual Studio], automating
- Office applications [Office development in Visual Studio], writing code
- writing code for Office solutions
- programming [Office development in Visual Studio], model
- Automation [Office development in Visual Studio], managed code
- application development [Office development in Visual Studio], programming model
- Office solutions [Office development in Visual Studio], writing code
- automating Office applications
- application development [Office development in Visual Studio], writing code
- application development [Office development in Visual Studio], automating
- Office projects [Office development in Visual Studio], changing namespaces
- solutions [Office development in Visual Studio], programming model
- programming [Office development in Visual Studio]
- namespaces [Office developmentin Visual Studio], changing in Office solutions
- projects [Office development in Visual Studio], writing code
- Office applications [Office development in Visual Studio], programming model
- managed code extensions [Office development in Visual Studio], writing code
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 40ea589cb4406a383876b1f16721f18fc48ebadd
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97526023"
---
# <a name="write-code-in-office-solutions"></a>Schreiben von Code in Office-Lösungen
  Einige Aspekte beim Schreiben von Code in Office-Projekten unterscheiden sich von anderen Projekttypen. Viele dieser Unterscheide haben mit der Art zu tun, wie die Office-Objektmodelle im verwalteten Code verfügbar gemacht werden. Andere Unterschiede beziehen sich auf den Entwurf von Office-Projekten.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="managed-code-and-office-programming"></a>Verwalteter Code und Office-Programmierung
 Die Schlüsseltechnologie, die das Erstellen integrierter Microsoft Office-Projektmappen ermöglicht, ist die Automatisierung. Automatisierung ist Teil der COM-Technologie (Component Object Model). Automatisierung ermöglicht Ihnen die Verwendung von Code zum Erstellen und Steuern von Softwareobjekten, die von einer Anwendung, einer DLL oder einem ActiveX-Steuerelement verfügbar gemacht wird, die bzw. das die entsprechende Programmierschnittstelle unterstützt.

### <a name="understand-primary-interop-assemblies"></a>Informationen zu primären Interopassemblys
 Viele Funktionen der Microsoft Office-Anwendungen sind für die Automatisierung zugänglich. Sie können verwalteten Code (z. B. Visual Basic oder C#) jedoch nicht direkt zum Automatisieren von Office-Anwendungen verwenden. Zum Automatisieren von Office-Anwendungen mithilfe von verwaltetem Code müssen die primären Office-Interopassemblys verwendet werden. Mithilfe der primären Interopassemblys kann verwalteter Code mit dem COM-basierten Objektmodell der Office-Anwendungen interagieren.

 Jede Microsoft Office-Anwendung verfügt über eine primäre Interopassembly (PIA). Wenn Sie in Visual Studio ein Office-Projekt erstellen, wird dem Projekt automatisch ein Verweis auf die entsprechende PIA hinzugefügt. Zum Automatisieren der Funktionen anderer Office-Anwendungen aus dem Projekt muss der entsprechenden primären Interopassembly (PIA) manuell ein Verweis hinzugefügt werden. Weitere Informationen finden Sie unter Gewusst [wie: Ausrichten von Office-Anwendungen mithilfe primärer Interop](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)-Assemblys.

### <a name="use-primary-interop-assemblies-at-design-time-and-runtime"></a>Verwenden primärer Interop-Assemblys zur Entwurfszeit und zur Laufzeit
 Die Office-PIAs müssen im globalen Assemblycache auf dem Entwicklungscomputer installiert und registriert sein, damit Sie die meisten Entwicklungsaufgaben ausführen können. Weitere Informationen finden Sie unter [Konfigurieren eines Computers zum Entwickeln von Office](../vsto/configuring-a-computer-to-develop-office-solutions.md)-Projektmappen.

 Die Office-PIAs sind jedoch auf Endbenutzercomputern nicht erforderlich, um Office-Projektmappen auszuführen, für die als Zielversion [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher festgelegt wurde. Weitere Informationen finden Sie unter [Entwerfen und Erstellen von Office-](../vsto/designing-and-creating-office-solutions.md)Projektmappen.

### <a name="use-types-in-primary-interop-assemblies"></a>Verwenden von Typen in primären Interop-Assemblys
 Die Office-PIAs enthalten eine Kombination von Typen, die das Objektmodell der Office-Anwendungen und zusätzliche Infrastrukturtypen verfügbar machen, die nicht zur direkten Verwendung im Code vorgesehen sind. Eine Übersicht über die Typen in den Office-PIAs finden Sie unter [Übersicht über Klassen und Schnittstellen in den primären Interop-](/previous-versions/office/office-12/ms247299\(v\=office.12\))Assemblys von Office.

 Da die Typen in den Office-PIAs Typen in den COM-basierten Objektmodellen entsprechen, unterscheidet sich die Art der Verwendung dieser Typen von der anderer verwalteter Typen. Zum Beispiel hängt die Art, wie Sie Methoden mit optionalen Parameter in einer primären Interopassembly von Office aufrufen, von der im Projekt verwendeten Programmiersprache ab. Weitere Informationen finden Sie unter den folgenden Themen:

- [Optionale Parameter in Office](../vsto/optional-parameters-in-office-solutions.md)-Projektmappen.

- [Späte Bindung in Office](../vsto/late-binding-in-office-solutions.md)-Projektmappen.

## <a name="program-model-of-office-projects"></a>Programm Modell von Office-Projekten
 Alle Office-Projekte schließen mindestens eine generierte Klasse ein, die den Einstiegspunkt für den Code darstellt. Diese Klassen bieten auch Zugriff auf das Objektmodell der Hostanwendung und Zugriff auf Funktionen wie Aktionsbereiche und benutzerdefinierte Aufgabenbereiche.

### <a name="understand-the-generated-classes"></a>Grundlegendes zu den generierten Klassen
 In Projekten auf Dokumentebene für Excel und Word ähnelt die generierte Klasse einem Objekt der obersten Ebene im Objektmodell der Anwendung. Die generierte `ThisDocument` -Klasse in einem Word-Dokumentprojekt stellt beispielsweise dieselben Member wie die <xref:Microsoft.Office.Interop.Word.Document> -Klasse im Word-Objektmodell bereit. Weitere Informationen zu den generierten Klassen in Projekten auf Dokument Ebene finden Sie unter [Program mieren von Programmen auf Dokument Ebene](../vsto/programming-document-level-customizations.md).

 In VSTO-Add-In-Projekten wird eine generierte Klasse namens `ThisAddIn`bereitgestellt. Diese Klasse ähnelt keiner Klasse im Objektmodell der Hostanwendung. Diese Klasse stellt stattdessen das VSTO-Add-in selbst dar und stellt Member bereit, mit denen Sie auf das Objektmodell der Host Anwendung zugreifen und auf andere Funktionen zugreifen können, die für VSTO-Add-Ins verfügbar sind. Weitere Informationen finden Sie unter [Program VSTO Add-ins](../vsto/programming-vsto-add-ins.md).

 Alle generierten Klassen in Office-Projekte enthalten die Ereignishandler `Startup` und `Shutdown` . In der Regel wird diesen Ereignishandlern Code hinzugefügt, um mit dem Schreiben von Code zu beginnen. Um das VSTO-Add-In zu initialisieren, können Sie dem `Startup` -Ereignishandler Code hinzufügen. Um vom VSTO-Add-In verwendete Ressourcen zu bereinigen, können Sie dem `Shutdown` -Ereignishandler Code hinzufügen. Weitere Informationen finden Sie unter [Ereignisse in Office-Projekten](../vsto/events-in-office-projects.md).

### <a name="access-the-generated-classes-at-run-time"></a>Zugreifen auf die generierten Klassen zur Laufzeit
 Wenn eine Office-Lösung geladen wird, wird jede generierte Klasse im Projekt von [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] instanziiert. Sie können auf diese Objekte von einem beliebigen Code im Projekt mithilfe der `Globals` -Klasse zugreifen. Beispielsweise können Sie die- `Globals` Klasse verwenden, um Code in der- `ThisAddIn` Klasse von einem Ereignishandler einer Menü Band Schaltfläche in einem VSTO-Add-in aufzurufen.

 Weitere Informationen finden Sie unter [globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md).

### <a name="namespace-considerations-in-office-solutions"></a>Überlegungen zu Namespaces in Office-Lösungen
 Der *Standardnamespace* (oder *Stammnamespace* in Visual Basic) eines Office-Projekts kann nach dem Erstellen des Projekts nicht mehr geändert werden. Der Standardnamespace entspricht immer dem Projektnamen, den Sie beim Erstellen des Projekts angegeben haben. Wenn Sie das Projekt umbenennen, ändert sich der Standardnamespace nicht. Weitere Informationen zum Standard Namespace in Projekten finden Sie Unterseite " [Anwendung", Projekt-Designer &#40;C&#35;&#41;](../ide/reference/application-page-project-designer-csharp.md) und [Anwendungsseite, Projekt-Designer &#40;Visual Basic&#41;](../ide/reference/application-page-project-designer-visual-basic.md).

### <a name="change-the-namespace-of-host-item-classes-in-c-projects"></a>Ändern des Namespace von Host Element Klassen in c#-Projekten
 Hostelementklassen (z. B. die `ThisAddIn`-, `ThisWorkbook`- oder `ThisDocument` -Klassen) verfügen über eigene Namespaces in Visual C#-Office-Projekten. Der Namespace für Hostelemente im Projekt entspricht standardmäßig dem Projektnamen, den Sie beim Erstellen des Projekts angegeben haben.

 Verwenden Sie die Eigenschaft **Namespace für Hostelement** , um den Namespace der Hostelemente in einem Visual C#-Office-Projekt zu ändern. Weitere Informationen finden Sie unter [Eigenschaften in Office-Projekten](../vsto/properties-in-office-projects.md).

## <a name="supported-programming-languages-in-office-projects"></a>Unterstützte Programmiersprachen in Office-Projekten
 Die Office-Projektvorlagen in Visual Studio unterstützen nur die Programmiersprachen Visual Basic und Visual C#. Daher sind diese Projektvorlagen nur unter den Knoten **Visual Basic** und **Visual C#** des Dialogfelds **Neues Projekt** in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]verfügbar. Weitere Informationen finden Sie unter Gewusst [wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

## <a name="language-choice-and-office-programming"></a>Sprachauswahl und Office-Programmierung
 Microsoft Office und Visual Basic for Applications (VBA) wurden so entwickelt, dass sie ineinander greifen, um den Workflow der Anwendungsanpassung zu optimieren. Visual Basic hat einige dieser Entwicklungen geerbt. Visual Basic unterstützt z. B. optionale Parameter, d. h. im Vergleich zu Visual C# können Sie beim Aufruf einiger Methoden in den primären Interopassemblys von Microsoft Office weniger Code schreiben.

## <a name="program-with-visual-basic-vs-visual-c-in-office-solutions"></a>Program mieren mit Visual Basic im Vergleich zu Visual c# in Office-Projektmappen
 Sie können Office-Lösungen entweder mit Visual Basic oder Visual C# erstellen. Da die Microsoft Office-Objektmodelle zur Verwendung mit Microsoft Visual Basic for Applications (VBA) entwickelt wurden, können Visual Basic-Entwickler problemlos mit den von den Microsoft Office-Anwendungen verfügbar gemachten Objekten arbeiten. Visual C#-Entwickler können größtenteils die gleichen Funktionen wie Visual Basic-Entwickler nutzen, aber in einigen Fällen müssen sie zusätzlichen Code verfassen, um die Office-Objektmodelle verwenden zu können. Es gibt auch einige Unterschiede zwischen den grundlegenden Programmierfunktionen für die Office-Entwicklung und in Visual Basic und C# geschriebenem verwalteten Code.

<!-- markdownlint-disable MD003 MD020 -->
## <a name="key-differences-between-visual-basic-and-visual-c"></a>Wichtige Unterschiede zwischen Visual Basic und Visual C #
<!-- markdownlint-enable MD003 MD020 -->

In der folgenden Tabelle werden die wichtigsten Unterschiede zwischen Visual Basic und Visual C# bei der Office-Entwicklung angezeigt.

|Funktion|BESCHREIBUNG|Visual Basic-Unterstützung|Visual C#-Unterstützung|
|-------------|-----------------|--------------------------|------------------------|
|Optionale Parameter|Viele Microsoft Office-Methoden verfügen über Parameter, die nicht erforderlich sind, wenn Sie die Methode aufrufen. Wenn kein Wert für den Parameter übergeben wird, wird ein Standardwert verwendet.|Visual Basic unterstützt optionale Parameter.|Visual C# unterstützt in den meisten Fällen optionale Parameter. Weitere Informationen finden Sie unter [optionale Parameter in Office](../vsto/optional-parameters-in-office-solutions.md)-Projektmappen.|
|Übergeben von Parametern durch einen Verweis|Optionale Parameter können in den meisten der primären Interopassemblys von Microsoft Office als Wert übergeben werden. In manchen primären Interopassemblys müssen optionale Parameter, die Referenztypen akzeptieren, jedoch als Verweis übergeben werden.<br /><br /> Weitere Informationen zu Wert-und Verweistyp Parametern finden Sie unter [übergeben von Argumenten als Wert und als Verweis &#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference) (für Visual Basic) und [übergeben von Parametern &#40;C&#35; Programmier Handbuch&#41;](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters).|Es sind keine weiteren Aufgaben erforderlich, um Parameter als Verweis zu übergeben. Der Visual Basic-Compiler übergibt die Parameter automatisch durch einen Verweis, wenn dies erforderlich ist.|In den meisten Fällen übergibt der Visual C#-Compiler automatisch die Parameter durch einen Verweis, wenn dies erforderlich ist. Weitere Informationen finden Sie unter [optionale Parameter in Office](../vsto/optional-parameters-in-office-solutions.md)-Projektmappen.|
|Parametrisierte Eigenschaften|Einige Eigenschaften akzeptieren Parameter und fungieren als schreibgeschützte Funktionen.|Visual Basic unterstützt Eigenschaften, die Parameter akzeptieren.|Visual C# unterstützt Eigenschaften, die Parameter akzeptieren.|
|Spätes Binden|Bei der späten Bindung werden die Eigenschaften von Objekten zur Laufzeit bestimmt, statt Variablen zur Entwurfszeit in den Objekttyp umzuwandeln.|Visual Basic führt späte Bindungen aus, wenn **Option Strict** deaktiviert ist. Wenn **Option Strict** aktiviert ist, müssen Objekte explizit konvertiert und Typen im <xref:System.Reflection> -Namespace verwendet werden, um auf spät gebundene Member zugreifen zu können. Weitere Informationen finden Sie unter [späte Bindung in Office](../vsto/late-binding-in-office-solutions.md)-Projektmappen.|Visual C# führt späte Bindungen in Projekten aus, für die als Zielversion [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]festgelegt wurde. Weitere Informationen finden Sie unter [späte Bindung in Office](../vsto/late-binding-in-office-solutions.md)-Projektmappen.|

## <a name="key-differences-between-office-development-and-managed-code"></a>Wichtige Unterschiede zwischen der Office-Entwicklung und verwaltetem Code
 In der folgenden Tabelle werden die wichtigsten Unterschiede zwischen der Office-Entwicklung und verwaltetem Code angezeigt, der mit Visual Basic und Visual C# geschrieben wurde.

|Funktion|BESCHREIBUNG|Visual Basic- und Visual C#-Unterstützung|
|-------------|-----------------|-----------------------------------------|
|Arrayindizes|Die unteren Arraygrenzen der Auflistungen in Microsoft Office-Anwendungen beginnen mit 1. Visual Basic und Visual C# verwenden 0-basierte Arrays. Weitere Informationen finden Sie unter [Arrays &#40;C&#35; Programming Guide&#41;](/dotnet/csharp/programming-guide/arrays/index) und [Arrays in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/arrays/index).|Um auf das erste Element einer Auflistung im Objektmodell einer Microsoft Office-Anwendung zuzugreifen, verwenden Sie den Index 1 statt 0.|

## <a name="see-also"></a>Weitere Informationen

- [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)
- [Globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md)
- [Ereignisse in Office-Projekten](../vsto/events-in-office-projects.md)
- [Gewusst wie: Ausrichten von Office-Anwendungen über primäre Interop-Assemblys](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Gewusst wie: Erstellen von Ereignis Handlern in Office-Projekten](../vsto/how-to-create-event-handlers-in-office-projects.md)
- [Späte Bindung in Office-Projektmappen](../vsto/late-binding-in-office-solutions.md)
- [Gemeinsame Entwicklung von Office-Lösungen](../vsto/collaborative-development-of-office-solutions.md)
