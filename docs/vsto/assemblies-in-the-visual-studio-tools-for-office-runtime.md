---
title: Assemblys in der Visual Studio-Tools für Office-Laufzeit
description: Erfahren Sie, dass Visual Studio automatisch Verweise auf die Visual Studio-Tools für Office-Runtime-Assemblys hinzufügt.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio Tools for Office runtime, assemblies
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 86c3c2b77b6bbea1e609bbea092b44bd1dee1dd4
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96848299"
---
# <a name="assemblies-in-the-visual-studio-tools-for-office-runtime"></a>Assemblys in der Visual Studio-Tools für Office-Laufzeit
  Wenn Sie ein Office-Projekt erstellen, fügt Visual Studio automatisch Verweise auf die [!INCLUDE[vsto_runtime](includes/vsto-runtime-md.md)] -Assemblys hinzu, die für den Projekttyp und das Ziel-.NET Framework des Projekts verwendet werden. In den Office-Erweiterungen für .NET Framework 3.5, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]und [!INCLUDE[net_v45](includes/net-v45-md.md)]sind verschiedene Assemblys vorhanden. Weitere Informationen zu den Office-Erweiterungen finden Sie unter [Visual Studio-Tools for Office Runtime Overview](visual-studio-tools-for-office-runtime-overview.md).

## <a name="assemblies-in-the-office-extensions-for-the-net-framework-4-and-the-net_v45"></a>Assemblys in den Office-Erweiterungen für die .NET Framework 4 und die [!INCLUDE[net_v45](includes/net-v45-md.md)]
 In der folgenden Tabelle sind die Assemblys aufgeführt, die in Office-Erweiterungen für [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] und [!INCLUDE[net_v45](includes/net-v45-md.md)]enthalten sind. Dokumentation zu den Namespaces und Typen in diesen Assemblys finden Sie unter [verwaltete Referenz &#40;Office-Entwicklung in Visual Studio&#41;](managed-reference-office-development-in-visual-studio.md).

|Assemblyname|BESCHREIBUNG|
|-------------------|-----------------|
|Microsoft.Office.Tools.Common.dll|Stellt folgende Typen bereit:<br /><br /> -Typen zum Erstellen von Menü Band Anpassungen und Smarttags. **Hinweis:**      Smarttags sind in [!INCLUDE[Excel_14_short](includes/excel-14-short-md.md)] und veraltet [!INCLUDE[Word_14_short](includes/word-14-short-md.md)] .<br />-Typen zum Erstellen von Aktionsbereichen in Anpassungen auf Dokument Ebene und benutzerdefinierten Aufgabenbereichen in VSTO-Add-Ins.|
|Microsoft.Office.Tools.Excel.dll|Stellt Schnittstellen bereit, die Hostelemente und Hoststeuerelemente für Excel-Projekte und unterstützende Typen darstellen. Weitere Informationen finden Sie unter [Automatisieren von Excel mithilfe von erweiterten Objekten](automating-excel-by-using-extended-objects.md).|
|Microsoft.Office.Tools.Outlook.dll|Enthält Typen, mit denen Sie benutzerdefinierte Formularbereiche in VSTO-Add-Ins für Outlook erstellen können.|
|Microsoft.Office.Tools.Word.dll|Stellt Schnittstellen bereit, die Hostelemente und Hoststeuerelemente für Word-Projekte und unterstützende Typen darstellen. Weitere Informationen finden Sie unter [Automatisieren von Word mithilfe von erweiterten Objekten](automating-word-by-using-extended-objects.md).|
|Microsoft.Office.Tools.v4.0.Framework.dll|Stellt folgende Typen bereit:<br /><br /> : Ausnahmen, die von der Visual Studio-Tools für die Office-Laufzeit ausgelöst werden können.<br />-Attribute, die Sie beim Erstellen von Outlook-Formular Bereichen verwenden können.|
|Microsoft.Office.Tools.dll|Stellt Typen bereit, die zur Infrastruktur der Visual Studio-Tools für Office-Laufzeit gehören und nicht für die direkte Verwendung durch den Code vorgesehen sind.|
|Microsoft.VisualStudio.Tools.Applications.Runtime.dll|Stellt folgende Typen bereit:<br /><br /> -Das- <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> Attribut und die- <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> Schnittstelle, die Sie zum Zwischenspeichern von Datenobjekten in einer Anpassung auf Dokument Ebene verwenden können. Weitere Informationen finden Sie unter zwischen [Speichern von Daten](caching-data.md).<br />-Die- <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> Schnittstelle, die Sie implementieren können, um zusätzliche Installationsschritte als abschließenden Schritt des ClickOnce-Installationsprogramms für eine Office-Projekt Mappe auszuführen. Weitere Informationen finden Sie unter Bereitstellen einer Office-Projekt Mappe [mithilfe von ClickOnce](deploying-an-office-solution-by-using-clickonce.md).<br />: Ausnahmen, die von der Visual Studio-Tools für die Office-Laufzeit ausgelöst werden können.<br />-Andere Typen, die Teil der Visual Studio-Tools für die Office-Lauf Zeit Infrastruktur sind und nicht für die direkte Verwendung im Code vorgesehen sind.|
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll|Stellt folgende Typen bereit:<br /><br /> -Die- <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> Klasse, die Sie zum Anfügen von Anpassungsassemblys an Dokumente und zum Zugriff auf die zwischengespeicherten Daten in Dokumenten verwenden können. Weitere Informationen finden Sie unter [Verwalten von Dokumenten auf einem Server mit der ServerDocument-Klasse](managing-documents-on-a-server-by-using-the-serverdocument-class.md).<br />: Mehrere Klassen, die die Hierarchie der zwischengespeicherten Daten in einer Anpassung auf Dokument Ebene darstellen. Weitere Informationen finden Sie unter [zugreifen auf Daten in Dokumenten auf dem Server](accessing-data-in-documents-on-the-server.md).|

 Projekte, die auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder [!INCLUDE[net_v45](includes/net-v45-md.md)] abzielen, verweisen auch auf die folgenden Assemblys. Diese Assemblys sind nicht Teil der verteilbaren [!INCLUDE[vsto_runtime](includes/vsto-runtime-md.md)] . Vielmehr handelt es sich um abhängige Assemblys, die mit Ihrer Lösung bereitgestellt werden müssen. Standardmäßig werden sie in den Ausgabeordner für die Erstellung für das Projekt kopiert (die Eigenschaft **Lokale Kopie** für diese Assemblys wird auf **True** festgelegt). Wenn Sie das Projekt mithilfe von ClickOnce bereitstellen, sind diese Assemblys im generierten Paket enthalten.

|Assemblyname|BESCHREIBUNG|
|-------------------|-----------------|
|Microsoft.Office.Tools.Common.v4.0.Utilities.dll|Stellt die Basisklassen für die generierte `ThisAddIn` -Klasse in VSTO-Add-In-Projekten und die generierte Menübandklasse in allen Projekten bereit.|
|Microsoft.Office.Tools.Excel.v4.0.Utilities.dll|Stellt folgende Typen bereit:<br /><br /> -Basisklassen für die generierten- `ThisWorkbook` und- `Sheet` Klassen in Projekten auf Dokument Ebene für Excel.<br />-Windows Forms Steuerelemente, die Sie für Arbeitsblätter in Excel-Projekten verwenden können.|
|Microsoft.Office.Tools.Outlook.v4.0.Utilities.dll|Stellt Basisklassen für die generierten `ThisAddIn` - und Formularbereichsklassen in Outlook-Projekten bereit.|
|Microsoft.Office.Tools.Word.v4.0.Utilities.dll|Stellt folgende Typen bereit:<br /><br /> -Basisklassen für die generierte- `ThisDocument` Klasse in Projekten auf Dokument Ebene für Word.<br />-Windows Forms Steuerelemente, die Sie für Dokumente in Word-Projekten verwenden können.|

## <a name="assemblies-in-the-office-extensions-for-the-net-framework-35"></a>Assemblys in den Office-Erweiterungen für den .NET Framework 3,5
 In der folgenden Tabelle sind die Assemblys aufgeführt, die in den Office-Erweiterungen für .NET Framework 3.5. enthalten sind. Dokumentation zu den Namespaces und Klassen in diesen Assemblys finden Sie im folgenden Referenz Abschnitt in der Visual Studio 2008-Dokumentation: [http://go.microsoft.com/fwlink/?LinkId=160658](managed-reference-office-development-in-visual-studio.md) .

|Assemblyname|BESCHREIBUNG|
|-------------------|-----------------|
|Microsoft.Office.Tools.Common.v9.0.dll|Stellt folgende Typen bereit:<br /><br /> -Die Microsoft. Office. Tools. AddIn-Basisklasse für VSTO-Add-Ins.<br />-Klassen zum Erstellen von Menü Band Anpassungen und Smarttags. **Hinweis:**      Smarttags sind in [!INCLUDE[Excel_14_short](includes/excel-14-short-md.md)] und veraltet [!INCLUDE[Word_14_short](includes/word-14-short-md.md)] .<br />-Klassen zum Erstellen von Aktionsbereichen in Anpassungen auf Dokument Ebene und benutzerdefinierten Aufgabenbereichen in VSTO-Add-Ins.|
|Microsoft.Office.Tools.Excel.v9.0.dll|Stellt Hostelemente und Hoststeuerelemente für Excel-Lösungen bereit. Weitere Informationen finden Sie unter [Automatisieren von Excel mithilfe von erweiterten Objekten](automating-excel-by-using-extended-objects.md).|
|Microsoft.Office.Tools.Outlook.v9.0.dll|Stellt Klassen bereit, mit denen Sie benutzerdefinierte Formularbereiche in Outlook-VSTO-Add-Ins erstellen können.|
|Microsoft.Office.Tools.Word.v9.0.dll|Stellt Hostelemente und Hoststeuerelemente für Word--Lösungen bereit. Weitere Informationen finden Sie unter [Automatisieren von Word mithilfe von erweiterten Objekten](automating-word-by-using-extended-objects.md).|
|Microsoft.Office.Tools.v9.0.dll|Stellt folgende Typen bereit:<br /><br /> -Die [RemoteBindableComponent](/previous-versions/visualstudio/visual-studio-2008/bb546360(v=vs.90)) -Klasse, die die Daten Bindungsfunktionen für Host Steuerelemente in Anpassungen auf Dokument Ebene bereitstellt.<br />-Andere Typen, die Teil der Visual Studio-Tools für die Office-Lauf Zeit Infrastruktur sind und nicht für die direkte Verwendung im Code vorgesehen sind.|
|Microsoft.VisualStudio.Tools.Applications.Runtime.v9.0.dll|Stellt folgende Typen bereit:<br /><br /> -Das- <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> Attribut und die- <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> Schnittstelle, die Sie zum Zwischenspeichern von Datenobjekten in einer Anpassung auf Dokument Ebene verwenden können. Weitere Informationen finden Sie unter zwischen [Speichern von Daten](caching-data.md).<br />: Ausnahmen, die von der Visual Studio-Tools für die Office-Laufzeit ausgelöst werden können.<br />-Andere Typen, die Teil der Visual Studio-Tools für die Office-Lauf Zeit Infrastruktur sind und nicht für die direkte Verwendung im Code vorgesehen sind.|
|Microsoft.VisualStudio.Tools.Applications.Runtime.v10.0.dll|Stellt die <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction>-Schnittstelle bereit, die Sie implementieren können, um zusätzliche Installationsschritte als abschließenden Schritt des ClickOnce-Installationsprogramms für eine Office-Lösung auszuführen. Weitere Informationen finden Sie unter [Erweiterte Office-Lösungs Bereitstellung](/previous-versions/visualstudio/visual-studio-2010/dd234217(v=vs.100)).|
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.v10.0.dll|Stellt folgende Typen bereit:<br /><br /> -Die- <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> Klasse, die Sie zum programmgesteuerten Anfügen von Anpassungsassemblys an Dokumente und zum Zugriff auf die zwischengespeicherten Daten in Dokumenten verwenden können. Weitere Informationen finden Sie unter [Verwalten von Dokumenten auf einem Server mit der ServerDocument-Klasse](managing-documents-on-a-server-by-using-the-serverdocument-class.md).<br />: Mehrere Klassen, die die Hierarchie der zwischengespeicherten Daten in einer Anpassung auf Dokument Ebene darstellen. Weitere Informationen finden Sie unter [zugreifen auf Daten in Dokumenten auf dem Server](accessing-data-in-documents-on-the-server.md).|
|Microsoft.VisualStudio.Tools.Office.Runtime.v10.0.dll|Stellt folgende Typen bereit:<br /><br /> -Die Klassen "Microsoft. VisualStudio. Tools. Office. Runtime. Security. AddInSecurityEntry" und "Microsoft. VisualStudio. Tools. Office. Runtime. Security. UserInclusionList", die Sie verwenden können, um Benutzer Aufnahme Listeneinträge zu erstellen, um Office-Projektmappen, die auf .NET Framework 3,5 abzielen, eine Vertrauensstellung zu gewähren.<br />-Andere Typen, die Teil der Visual Studio-Tools für die Office-Lauf Zeit Infrastruktur sind und nicht für die direkte Verwendung im Code vorgesehen sind.|

## <a name="see-also"></a>Siehe auch
- [Übersicht über Visual Studio-Tools für Office-Laufzeit](visual-studio-tools-for-office-runtime-overview.md)
- [Visual Studio-Tools für Installationsszenarien für Office-Runtime](visual-studio-tools-for-office-runtime-installation-scenarios.md)
