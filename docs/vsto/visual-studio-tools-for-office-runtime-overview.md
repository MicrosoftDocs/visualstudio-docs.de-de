---
title: Übersicht über Visual Studio-Tools für Office-Laufzeit
description: Visual Studio 2010-Tools für Office-Laufzeit muss auf Endbenutzer Computern installiert werden, um Lösungen ausführen zu können, die mit den Microsoft Office Developer Tools erstellt werden.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office runtime [Office development in Visual Studio], about Office runtime
- VSTOLoader.dll
- runtime loader [Office development in Visual Studio]
- Office runtime [Office development in Visual Studio], assemblies
- Office runtime [Office development in Visual Studio]
- runtime [Office development in Visual Studio], assemblies
- vstoee.dll
- Visual Studio Tools for Office runtime
- Office solutions [Office development in Visual Studio], runtime
- solutions [Office development in Visual Studio], runtime
- versions [Office development in Visual Studio], runtime
- assemblies [Office development in Visual Studio], runtime
- runtime [Office development in Visual Studio], about VSTO runtime
- solution loader [Office development in Visual Studio]
- runtime [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 16431a9ba2fe56b88f9f6b7f2c874c75bfad61c3
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97526267"
---
# <a name="visual-studio-tools-for-office-runtime-overview"></a>Übersicht über Visual Studio-Tools für Office-Laufzeit
  Zum Ausführen von Projektmappen, die mit den Microsoft Office Developer Tools in Visual Studio erstellt werden, muss die Visual Studio 2010-Tools für Office-Laufzeit auf den Endbenutzer Computern installiert sein. Weitere Informationen finden Sie unter Vorgehens [Weise: Installieren des Visual Studio-Tools für die weitervertreibbare Office-Laufzeit](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md). Die Visual Studio 2010-Tools für Office-Laufzeit besteht aus zwei Hauptkomponenten:

- Den Office-Erweiterungen für .NET Framework. Diese Komponenten sind verwaltete Assemblys, die die Kommunikationsebene zwischen der Projektmappe und der Microsoft Office-Anwendung bereitstellen. Weitere Informationen finden Sie Untergrund Legendes [zu den Office-Erweiterungen für die .NET Framework](#officeextensions).

- Dem Office-Projektmappenladeprogramm. Bei dieser Komponente handelt es sich um einen Satz nicht verwalteter DLLs, die Office-Anwendungen verwenden, um die Laufzeit und Projektmappen zu laden. Weitere Informationen finden Sie Untergrund Legendes [zum Office](#UnmanagedLoader)-projektmappenlade Modul.

  Die Laufzeit kann auf unterschiedliche Weise installiert werden. In Abhängigkeit von der Konfiguration des Computers werden unterschiedliche Laufzeitkomponenten installiert, wenn Sie die Laufzeit installieren. Weitere Informationen finden Sie unter [Visual Studio-Tools for Office Runtime Installation Szenarios](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).

## <a name="understand-the-office-extensions-for-the-net-framework"></a><a name="officeextensions"></a> Verstehen der Office-Erweiterungen für die .NET Framework
 Die Visual Studio 2010-Tools für Office-Laufzeit enthält Office-Erweiterungen für die .NET Framework 3,5, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] und höher. Projektmappen, die auf die einzelnen Versionen von .NET Framework abzielen, verwenden die entsprechenden Erweiterungen für die jeweilige Version.

 Diese Erweiterungen bestehen aus Assemblys, die von den Projektmappen verwendet werden, um Office-Anwendungen zu automatisieren und zu erweitern. Wenn Sie ein Office-Projekt erstellen, fügt Visual Studio Verweise automatisch Verweise auf die Assemblys hinzu, die für den Projekttyp und das Ziel-.NET Framework des Projekts verwendet werden. Weitere Informationen zu den Assemblys in den Office-Erweiterungen finden Sie unter Assemblys [in der Visual Studio-Tools für Office-Laufzeit](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md).

### <a name="design-differences-in-the-office-extensions"></a>Entwurfs Unterschiede in den Office-Erweiterungen
 Bei den meisten Typen, die Sie in Office-Erweiterungen für .NET Framework 3.5 verwenden, handelt es sich um Klassen. Dies sind die gleichen Klassen, die in früheren Versionen der [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]enthalten waren. Im Gegensatz dazu sind die meisten Typen, die Sie in Office-Erweiterungen für [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher verwenden, Schnittstellen. Wenn Sie z. B. auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher abzielen, sind der <xref:Microsoft.Office.Tools.Excel.Worksheet> -Typ und der <xref:Microsoft.Office.Tools.Word.Document> -Typ Schnittstellen statt Klassen.

 In den meisten Fällen ist der Code, den Sie in Office-Projektmappen schreiben, derselbe, unabhängig davon, ob die Projektmappe auf .NET Framework 3.5 oder [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]abzielt. Bestimmte Funktionen erfordern jedoch anderen Code, wenn Sie auf andere Versionen von .NET Framework abzielen. Weitere Informationen finden Sie unter Migrieren von Office-Projektmappen [zum .NET Framework 4 oder](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)höher.

### <a name="interfaces-in-the-office-extensions-for-the-net-framework-4-or-later"></a>Schnittstellen in den Office-Erweiterungen für die .NET Framework 4 oder höher
 Die meisten Schnittstellen in den Office-Erweiterungen für [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher sind nicht für eine Implementierung durch Benutzercode vorgesehen. Die einzigen Schnittstellen, die Sie direkt implementieren können, haben einen Namen, der mit dem Buchstaben **I** beginnt, z. B. <xref:Microsoft.Office.Tools.Excel.ISmartTagExtension>.

 Alle Schnittstellen, die nicht mit **dem Buchstaben** beginnen, werden intern von der Visual Studio 2010-Tools für Office-Laufzeit implementiert, und diese Schnittstellen können sich in zukünftigen Versionen ändern. Um Objekte zu erstellen, die diese Schnittstellen implementieren, verwenden Sie im Projekt die vom `Globals.Factory`-Objekt bereitgestellten Methoden. Verwenden Sie z. B. die <xref:Microsoft.Office.Tools.Excel.SmartTag>-Methode, um ein Objekt abzurufen, das die `Globals.Factory.CreateSmartTag`-Schnittstelle implementiert. Weitere Informationen zu `Globals.Factory` finden Sie unter [globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md).

### <a name="enable-type-equivalence-and-embedded-types-in-projects-that-target-the-net-framework-4-or-later"></a>Aktivieren von typäquivalenz und eingebetteten Typen in Projekten, die auf die .NET Framework 4 oder höher abzielen
 Da das Objektmodell der Office-Erweiterungen für [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher auf Schnittstellen basiert, können Sie die Typäquivalenzfunktion in Visual C# und Visual Basic in Visual Studio verwenden, um Typinformationen von [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] in die Projektmappe einzubetten. Mithilfe dieser Funktion können Office-Projektmappen und die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] voneinander unabhängige Versionen verwenden. Wenn die Projektmappe beispielsweise die <xref:Microsoft.Office.Tools.Word.Document> -Schnittstelle als eingebetteten Typ verwendet und die nächste Version der Laufzeit der <xref:Microsoft.Office.Tools.Word.Document> -Schnittstelle Member hinzufügt, funktioniert die Projektmappe immer noch mit der nächsten Version der Laufzeit. Wenn die Projektmappe die <xref:Microsoft.Office.Tools.Word.Document> -Schnittstelle nicht als eingebetteten Typ verwendet, funktioniert die Projektmappe nicht mehr mit der nächsten Version der Laufzeit.

 Standardmäßig wird die Typäquivalenzfunktion nicht aktiviert, wenn Sie ein Office-Projekt erstellen, das auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher ausgerichtet ist. Wenn Sie diese Funktion aktivieren möchten, legen Sie die Eigenschaft **Interoptypen einbetten** von einem der folgenden Assemblyverweise im Projekt auf **True** fest:

- Microsoft.Office.Tools.dll

- Microsoft.Office.Tools.Common.dll

- Microsoft.Office.Tools.Excel.dll

- Microsoft.Office.Tools.Outlook.dll

- Microsoft.Office.Tools.Word.dll

  Nachdem Sie diese Änderung vorgenommen haben, werden Typinformationen für alle vom Projekt verwendeten Laufzeittypen in die Projektmappenassembly eingebettet, wenn Sie das Projekt erstellen. Diese eingebetteten Typinformationen werden anstelle der Typinformationen in den Assemblys, auf die verwiesen wird, von der Projektmappe zur Laufzeit verwendet.

## <a name="understand-the-office-solution-loader"></a><a name="UnmanagedLoader"></a> Grundlegendes zum Office Solution Loader
 Visual Studio-Tools für Office-Laufzeit schließt mehrere nicht verwaltete DLLs ein, die Office-Anwendungen verwenden, um die Laufzeit sowie Office-Projektmappen zu laden. Obwohl Sie in der Regel nie direkt mit diesen DLLs arbeiten müssen, können Kenntnisse über ihren Zweck Ihnen dabei helfen, die Architektur der Office-Projektmappen besser zu verstehen.

 Informationen dazu, wie diese Komponenten während des Ladevorgangs verwendet werden, finden Sie unter [Architektur von Anpassungen auf Dokument Ebene](../vsto/architecture-of-document-level-customizations.md) und [Architektur von VSTO-Add-ins](../vsto/architecture-of-vsto-add-ins.md).

### <a name="vstoeedll"></a>vstoee.dll
 Wenn ein Benutzer eine Anpassung auf Dokument Ebene öffnet oder ein VSTO-Add-in startet, ruft die Office-Anwendung *VSTOEE.dll* auf, um die Aufgaben auszuführen, die zum Laden von erforderlich sind [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .

 *VSTOEE.dll* stellt sicher, dass die richtige Version von [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] für die Lösung und die installierte Version von Office geladen wird. Obwohl mehrere Versionen von [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] auf demselben Computer installiert werden können, wird jeweils nur eine Instanz von *VSTOEE.dll* installiert. Dies ist der *VSTOEE.dll* , der in der neuesten Version der Laufzeit enthalten war, die auf dem Computer installiert ist. Weitere Informationen zu den verschiedenen Versionen von, die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] für andere Projektmappen verwendet werden können, finden Sie unter Ausführen von Projektmappen [in verschiedenen Versionen von Microsoft Office](../vsto/running-solutions-in-different-versions-of-microsoft-office.md).

### <a name="vstoloaderdll"></a>VSTOLoader.dll
 Nachdem *VSTOEE.dll* die entsprechende Version von geladen [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] hat, führt *VSTOLoader.dll* den größten Teil der Arbeit aus, die zum Laden der Projektmappenassembly erforderlich ist. *VSTOLoader.dll* führt verschiedene Aktionen aus:

- Es erstellt eine Anwendungsdomäne für jede Projektmappenassembly.

- Es führt einen Satz von Sicherheitsüberprüfungen aus, um zu überprüfen, ob die Projektassembly über die Berechtigung zum Ausführen verfügt.

- Es lädt die Version der Office-Erweiterungen für das .NET Framework, das für die Projektmappe erforderlich ist.

  *VSTOLoader.dll* führt auch mehrere Aufgaben aus, die speziell für VSTO-Add-ins gelten:

- Es implementiert die <xref:Extensibility.IDTExtensibility2> -Schnittstelle. <xref:Extensibility.IDTExtensibility2> ist eine COM-Schnittstelle, die alle VSTO-Add-Ins für Microsoft Office-Anwendungen implementieren müssen. Diese Schnittstelle definiert Methoden, die die Anwendung aufruft, um mit dem VSTO-Add-In zu kommunizieren.

- Es implementiert die IManagedAddin-Schnittstelle. Diese Schnittstelle wird von Office-Anwendungen zum Laden von VSTO-Add-Ins verwendet. Weitere Informationen finden Sie unter [IManagedAddin-Schnittstelle](../vsto/imanagedaddin-interface.md).

## <a name="understand-the-32-bit-and-64-bit-versions-of-the-runtime"></a>Verstehen der 32-Bit-und 64-Bit-Versionen der Laufzeit
 Es gibt separate 64-Bit-und 32-Bit-Versionen der Visual Studio 2010-Tools für Office-Laufzeit. Diese Versionen der Laufzeit werden verwendet, um Projektmappen in 64-Bit- und 32-Bit-Editionen von Office auszuführen. Die folgende Tabelle zeigt, welche Version der Laufzeit für jede Kombination von Windows und Office erforderlich ist.

|Edition von Windows|Edition von Microsoft Office|Erforderliche Version der Visual Studio Tools for Office-Laufzeit.|
|------------------------|---------------------------------|--------------------------------------------------------------------|
|32 Bit|32 Bit|32 Bit|
|64-Bit|32-Bit|64-Bit|
|64-Bit|64-Bit|64-Bit|

 Wenn Sie Office installieren, wird die erforderliche [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] -Version zusammen mit Office installiert. Wenn Sie z. B. die 64-Bit-Edition von Office unter einer 64-Bit-Version von Windows installieren, wird auch die 64-Bit-Version von [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] installiert. Weitere Informationen zum Installieren von [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] mit Office finden Sie unter [Visual Studio-Tools for Office Runtime Installation Szenarios](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).

 Mit der 64-Bit-Version von Office können auch Office-Projektmappen ausgeführt werden, die mit Projektvorlagen für 2007 Microsoft Office System in Visual Studio 2008 erstellt wurden. Es können jedoch keine Office-Projektmappen ausgeführt werden, die mit Projektvorlagen für Microsoft Office 2003 in Visual Studio 2008 erstellt wurden, oder Office-Projektmappen, die mit Visual Studio 2005 erstellt wurden. Weitere Informationen finden Sie unter [Ausführen von Projektmappen in verschiedenen Versionen von Microsoft Office](../vsto/running-solutions-in-different-versions-of-microsoft-office.md).

## <a name="repair-the-visual-studio-2010-tools-for-office-runtime"></a>Reparieren der Visual Studio 2010-Tools für Office-Laufzeit
 Wenn Sie die Laufzeit reparieren müssen, öffnen Sie in der Systemsteuerung **Programme und Funktionen** oder **Software** , wählen Sie in der Liste der Programme die **Microsoft Visual Studio 2010-Tools für Office-Laufzeit** aus, und klicken Sie dann auf **Deinstallieren**. Das ausgeführte Setupprogramm ermöglicht es Ihnen, die Laufzeit zu reparieren. Wenn Sie auf **Ändern** klicken, ist keine Option zum Reparieren der Laufzeit verfügbar.

## <a name="see-also"></a>Weitere Informationen
- [Visual Studio-Tools für Installationsszenarien für Office-Runtime](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)
- [Assemblys in der Visual Studio-Tools für Office-Laufzeit](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md)
- [Architektur von Office-Projektmappen in Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [Architektur von Anpassungen auf Dokument Ebene](../vsto/architecture-of-document-level-customizations.md)
- [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)
- [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Aktualisieren und Migrieren von Office-Lösungen](../vsto/upgrading-and-migrating-office-solutions.md)
