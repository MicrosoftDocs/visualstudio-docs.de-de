---
title: Primäre Interop-Assemblys in Office
description: Erfahren Sie, wie Sie die primäre Interop-Assembly (PIA) verwenden, um über ein Office-Projekt auf die Funktionen einer Microsoft Office Anwendung zuzugreifen.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- primary interop assemblies
- assemblies [Office development in Visual Studio], primary interop assemblies
- Office primary interop assemblies
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 190c5785be9d17ee0a25d16ad6342368b658f252
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525220"
---
# <a name="office-primary-interop-assemblies"></a>Primäre Interop-Assemblys in Office

Zur Verwendung der Funktionen einer Microsoft Office-Anwendung in einem Office-Projekt müssen Sie die primäre Interop-Assembly (PIA) für diese Anwendung verwenden. Die PIA ermöglicht es verwaltetem Code, mit dem COM-basierten Objektmodell einer Microsoft Office-Anwendung zu interagieren.

[!include[Add-ins note](includes/addinsnote.md)]

Wenn Sie ein neues Office-Projekt erstellen, fügt Visual Studio Verweise auf die PIAs hinzu, die zum Erstellen des Projekts erforderlich sind. In einigen Szenarien müssen Sie Verweise auf zusätzliche PIAs hinzufügen (beispielsweise, wenn Sie eine Funktion von Microsoft Office Word in einem Projekt für Microsoft Office Excel verwenden möchten).

In diesem Thema werden die folgenden Aspekte der Verwendung von Microsoft Office PIAs in Office-Projekten beschrieben:

- [Separate primäre Interop-Assemblys zum Erstellen und Ausführen von Projekten](#separateassemblies)

- [Verwenden von Features mehrerer Microsoft Office Anwendungen in einem einzelnen Projekt](#usingfeatures)

- [Vollständige Liste primärer Interop-Assemblys für Microsoft Office-Anwendungen](#pialist)

Weitere Informationen zu primären Interop-Assemblys finden Sie unter [primäre](/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100))Interopassemblys.

<a name="separateassemblies"></a>

## <a name="separate-primary-interop-assemblies-to-build-and-run-projects"></a>Separate primäre Interop-Assemblys zum Erstellen und Ausführen von Projekten

Visual Studio verwendet unterschiedliche Sätze von PIAs auf dem Entwicklungscomputer. Diese unterschiedlichen Assemblysätze befinden sich an den folgenden Speicherorten:

- Ordner im Verzeichnis "Programme"

  Diese Kopien der Assemblys werden verwendet, wenn Sie Code schreiben und Projekte erstellen. Visual Studio installiert diese Assemblys automatisch.

- Der globale Assemblycache

  Diese Kopien der Assemblys werden bei einigen Entwicklungsaufgaben verwendet, z. B. wenn Sie Projekte ausführen oder debuggen. Visual Studio installiert und registriert diese Assemblys nicht; Sie müssen dies selbst tun.

### <a name="primary-interop-assemblies-in-the-program-files-directory"></a>Primäre Interop-Assemblys im Verzeichnis "Programme"

Bei der Installation von Visual Studio werden die PIAs automatisch an einem Speicherort im Dateisystem außerhalb des globalen Assemblycaches installiert. Wenn Sie ein neues Projekt erstellen, fügt Visual Studio automatisch Verweise auf diese Kopien der PIAs zu Ihrem Projekt hinzu. Visual Studio verwendet diese PIA-Kopien anstelle der Assemblys im globalen Assemblycache, um Typverweise aufzulösen, wenn Sie das Projekt entwickeln und erstellen.

Diese Kopien der PIAs helfen dabei, mehrere Entwicklungsprobleme im Zusammenhang mit Visual Studio zu vermeiden. Diese können auftreten, wenn unterschiedliche Versionen der PIAs im globalen Assemblycache registriert werden.

Ab Visual Studio 2017 werden diese Kopien der PIAs an den folgenden freigegebenen Speicherorten auf dem Entwicklungs Computer installiert:

- `%ProgramFiles%\Microsoft Visual Studio\Shared\Visual Studio Tools for Office\PIA\`

- (oder `%ProgramFiles(x86)%\Microsoft Visual Studio\Shared\Visual Studio Tools for Office\PIA\` auf 64-Bit-Betriebssystemen)

> [!NOTE]
> Für ältere Versionen von Visual Studio werden diese PIAs in der Visual Studio-Tools für den Ordner office\pia unter dem `%ProgramFiles%` Ordner für diese Version von Visual Studio installiert.
> Zum Beispiel: `%ProgramFiles(x86)%\Microsoft Visual Studio 14.0\Visual Studio Tools for Office\PIA\`

### <a name="primary-interop-assemblies-in-the-global-assembly-cache"></a>Primäre Interop-Assemblys im globalen Assemblycache

Für die Ausführung bestimmter Entwicklungsaufgaben müssen die PIAs im globalen Assemblycache auf dem Entwicklungscomputer installiert und registriert sein. In der Regel werden die PIAs automatisch installiert, wenn Sie Office auf dem Entwicklungscomputer installieren. Weitere Informationen finden Sie unter [Konfigurieren eines Computers zum Entwickeln von Office](../vsto/configuring-a-computer-to-develop-office-solutions.md)-Projektmappen.

Zur Ausführung von Office-Lösungen sind die Office-PIAs auf Endbenutzercomputern nicht erforderlich. Weitere Informationen finden Sie unter [Entwerfen und Erstellen von Office-](../vsto/designing-and-creating-office-solutions.md)Projektmappen.

<a name="usingfeatures"></a>

## <a name="use-features-of-multiple-microsoft-office-applications-in-a-single-project"></a>Verwenden von Features mehrerer Microsoft Office Anwendungen in einem einzelnen Projekt

Jede Office-Projektvorlage in Visual Studio wird im Hinblick auf die Arbeit mit einer einzelnen Microsoft Office-Anwendung entworfen. Um Funktionen in mehreren Microsoft Office-Anwendungen oder in einer Anwendung bzw. Komponente zu verwenden, die kein Projekt in Visual Studio besitzt, müssen Sie einen Verweis auf die erforderlichen PIAs hinzufügen.

In den meisten Fällen sollten Sie Verweise auf die PIAs hinzufügen, die von Visual Studio unter dem `%ProgramFiles(x86)%\Microsoft Visual Studio\Shared\Visual Studio Tools for Office\PIA\` Verzeichnis installiert werden. Diese Versionen der Assemblys werden im Dialogfeld Verweis- **Manager** auf der Registerkarte **Framework** angezeigt. Weitere Informationen finden Sie unter Gewusst [wie: Ausrichten von Office-Anwendungen mithilfe primärer Interop](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)-Assemblys.

Wenn Sie die PIAs im globalen Assemblycache installiert und registriert haben, werden diese Versionen im Dialogfeld **Verweis-Manager** auf der Registerkarte **COM** angezeigt. Vermeiden Sie es, Verweise auf diese Versionen hinzuzufügen, da sonst bei ihrer Verwendung Entwicklungsprobleme auftreten können. Wenn verschiedene Versionen der PIAs im globalen Assemblycache registriert sind, bindet das Projekt automatisch an die Version der Assembly, die zuletzt registriert wurde - auch dann, wenn Sie im Dialogfeld **Verweis-Manager** auf der Registerkarte **COM** eine andere Version angeben.

> [!NOTE]
> Einige Assemblys werden einem Projekt automatisch hinzugefügt, wenn eine Assembly hinzugefügt wird, die auf sie verweist. Beispielsweise werden Verweise auf die Assemblys `Office.dll` und `Microsoft.Vbe.Interop.dll` automatisch hinzugefügt, wenn Sie einen Verweis auf die Word-, Excel-, Outlook-, Microsoft Forms-oder Graph-Assemblys hinzufügen.

<a name="pialist"></a>

## <a name="primary-interop-assemblies-for-microsoft-office-applications"></a>Primäre Interop-Assemblys für Microsoft Office Anwendungen

In der folgenden Tabelle werden die primären Interop-Assemblys aufgelistet, die für und verfügbar sind [!INCLUDE[Office_16_short](../vsto/includes/office-16-short-md.md)] [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] .

<br/>

|Office-Anwendung oder Office-Komponente|Name der primären Interop-Assembly|
|-------------------------------------|-----------------------------------|
|Microsoft Access 14.0-Objektbibliothek<br /><br /> Microsoft Access 15,0-Objektbibliothek|Microsoft.Office.Interop.Access.dll|
|Objektbibliothek der Microsoft Office 14.0 Access-Datenbank-Engine<br /><br /> Objektbibliothek der Microsoft Office 15.0 Access-Datenbank-Engine|Microsoft.Office.Interop.Access.Dao.dll|
|Microsoft Excel 14.0-Objektbibliothek<br /><br /> Microsoft Excel 15,0-Objektbibliothek|[Microsoft.Office.Interop.Excel.dll](/dotnet/api/microsoft.office.interop.excel?view=excel-pia&preserve-view=true)|
|Microsoft Graph 14.0-Objektbibliothek(wird von PowerPoint, Access und Word für Diagramme verwendet)<br /><br /> Microsoft Graph 15.0-Objektbibliothek|Microsoft.Office.Interop.Graph.dll|
|Microsoft InfoPath 2.0-Typbibliothek (nur für InfoPath 2007)|[Microsoft.Office.Interop.InfoPath.dll](/dotnet/api/microsoft.office.interop.infopath?view=infopath-form&preserve-view=true)|
|Microsoft InfoPath-XML-Interop-Assembly (nur für InfoPath 2007)|Microsoft.Office.Interop.InfoPath.Xml.dll|
|Microsoft Office 14.0-Objektbibliothek (gemeinsam genutzte Office-Funktionen)<br /><br /> Microsoft Office 15,0-Objektbibliothek (gemeinsam genutzte Office-Funktionen)|office.dll|
|Microsoft Office Outlook-Ansichtssteuerelement (kann auf Webseiten und in Anwendungen für den Zugriff auf den Posteingang verwendet werden)|Microsoft.Office.Interop.OutlookViewCtl.dll|
|Microsoft Outlook 14.0-Objektbibliothek<br /><br /> Microsoft Outlook 15,0-Objektbibliothek|[Microsoft.Office.Interop.Outlook.dll](/dotnet/api/microsoft.office.interop.outlook?view=outlook-pia&preserve-view=true)|
|Microsoft PowerPoint 14.0-Objektbibliothek<br /><br /> Microsoft PowerPoint 15,0-Objektbibliothek|Microsoft.Office.Interop.PowerPoint.dll|
|Microsoft Project 14.0-Objektbibliothek<br /><br /> Microsoft Project 15,0-Objektbibliothek|[Microsoft.Office.Interop.MSProject.dll](/dotnet/api/microsoft.office.interop.msproject?view=office-project-server&preserve-view=true)|
|Microsoft Publisher 14.0-Objektbibliothek<br /><br /> Microsoft Publisher 15,0-Objektbibliothek|Microsoft.Office.Interop.Publisher.dll|
|Microsoft SharePoint Designer 14.0-Webobjekt-Verweisbibliothek|Microsoft.Office.Interop.SharePointDesigner.dll|
|Microsoft SharePoint Designer 14.0-Seitenobjekt-Verweisbibliothek|Microsoft.Office.Interop.SharePointDesignerPage.dll|
|Microsoft smartags 2,0-Typbibliothek **Hinweis:**  Smarttags sind in [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] und veraltet [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)] .|Microsoft.Office.Interop.SmartTag.dll|
|Microsoft Visio 14.0-Typbibliothek<br /><br /> Microsoft Visio 15,0-Typbibliothek|Microsoft.Office.Interop.Visio.dll|
|Microsoft Visio 14.0-Typbibliothek für "Speichern als Web"<br /><br /> Microsoft Visio 15,0-Typbibliothek für "Speichern als Web"|Microsoft.Office.Interop.Visio.SaveAsWeb.dll|
|Microsoft Visio 14.0-Typbibliothek für Zeichnungssteuerelemente<br /><br /> Microsoft Visio 15,0-Typbibliothek für Zeichnungssteuerelemente|Microsoft.Office.Interop.VisOcx.dll|
|Microsoft Word 14.0-Objektbibliothek<br /><br /> Microsoft Word 15,0-Objektbibliothek|[Microsoft.Office.Interop.Word.dll](/dotnet/api/microsoft.office.interop.word?view=word-pia&preserve-view=true)|
|Microsoft Visual Basic for Applications Erweiterung 5.3|Microsoft.Vbe.Interop.dll|

### <a name="binding-redirect-assemblies"></a>Bindungsassemblys

Wenn Sie die Office-PIAs im globalen Assemblycache installieren und registrieren (entweder mit Office oder durch das Installieren des verteilbaren Pakets für die PIAs), werden die Bindungsumleitungsassemblys ebenfalls nur im globalen Assemblycache installiert. Diese Assemblys helfen sicherzustellen, dass die richtige Version der primären Interop-Assemblys zur Laufzeit geladen wird.

Wenn eine Projektmappe, die auf eine Assembly für [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] verweist, beispielsweise auf einem Computer mit der [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] -Version derselben primären Interop-Assembly ausgeführt wird, weist die Bindungsumleitungsassembly die [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] -Laufzeit an, die [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] -Version der primären Interop-Assembly zu laden.

Weitere Informationen finden Sie unter Gewusst [wie: Aktivieren und Deaktivieren der automatischen Bindungs Umleitung](/dotnet/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection).

## <a name="see-also"></a>Weitere Informationen

- [Gewusst wie: Ausrichten von Office-Anwendungen über primäre Interop-Assemblys](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Übersicht über das Excel-Objektmodell](../vsto/excel-object-model-overview.md)
- [InfoPath-Lösungen](../vsto/infopath-solutions.md)
- [Übersicht über das Outlook-Objektmodell](../vsto/outlook-object-model-overview.md)
- [PowerPoint-Lösungen](../vsto/powerpoint-solutions.md)
- [Projektmappen](../vsto/project-solutions.md)
- [Übersicht über das Visio-Objektmodell](../vsto/visio-object-model-overview.md)
- [Übersicht über das Word-Objektmodell](../vsto/word-object-model-overview.md)
- [Allgemeine Referenz &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/general-reference-office-development-in-visual-studio.md)
