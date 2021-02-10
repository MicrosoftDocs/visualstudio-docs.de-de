---
title: Element Vorlagen/Projektvorlagen für SharePoint-Projekt Elemente
description: Erstellen von Element Vorlagen und Projektvorlagen für SharePoint-Projekt Elemente. Erstellen Sie Assistenten für Element Vorlagen und Projektvorlagen.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, creating custom templates
- .spdata files
- projects [SharePoint development in Visual Studio], creating custom templates
- SharePoint projects, creating custom templates
- SharePoint development in Visual Studio, creating custom project and item templates
- project items [SharePoint development in Visual Studio], creating custom templates
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 538bc709ed3af1c7b1424b56c1bd843b127c6ab7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949154"
---
# <a name="create-item-templates-and-project-templates-for-sharepoint-project-items"></a>Erstellen von Element Vorlagen und Projektvorlagen für SharePoint-Projekt Elemente

Wenn Sie einen benutzerdefinierten SharePoint-Projekt Elementtyp definieren, können Sie ihn einer Element Vorlage oder einer Projektvorlage zuordnen. Diese Zuordnung ermöglicht anderen Entwicklern, das Projekt Element in Visual Studio zu verwenden. Sie können auch einen Assistenten für die Vorlage erstellen.

Beispielsweise enthält Visual Studio keine Projektvorlage oder Element Vorlage zum Hinzufügen eines Felds zu einer SharePoint-Website. Sie können einen SharePoint-Projekt Elementtyp definieren, der ein Feld darstellt, und dann eine Element Vorlage erstellen, mit der andere Entwickler das Feld Element einem SharePoint-Projekt hinzufügen können. Oder Sie können eine Projektvorlage erstellen, damit Entwickler ein neues SharePoint-Projekt erstellen können, das das field-Element enthält. In beiden Fällen können Sie auch einen Assistenten bereitstellen, der angezeigt wird, wenn Entwickler ihre Vorlage verwenden. Dieser Assistent kann Informationen von Entwicklern sammeln, um das neue Element oder Projekt zu konfigurieren.

Element Vorlagen und Projektvorlagen sind *ZIP* -Dateien, die Dateien enthalten, die von Visual Studio zum Erstellen eines Projekt Elements oder Projekts verwendet werden. Weitere Informationen zu den Grundlagen von Element Vorlagen und Projektvorlagen finden Sie unter [Erstellen von Projekt-und Element Vorlagen](../ide/creating-project-and-item-templates.md).

## <a name="create-item-templates"></a>Erstellen von Elementvorlagen
 Wenn Sie eine Element Vorlage für ein SharePoint-Projekt Element erstellen, gibt es einige Dateien, die immer erforderlich sind, sowie optionale Dateien, die möglicherweise von bestimmten Typen von Projekt Elementen verwendet werden. Eine exemplarische Vorgehensweise, in der veranschaulicht wird, wie ein SharePoint-Projekt Elementtyp definiert und eine Element Vorlage dafür erstellt wird, finden Sie unter Exemplarische [Vorgehensweise: Erstellen eines benutzerdefinierten Aktionsprojekt Elements mit einer Element Vorlage, Teil 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).

 In der folgenden Tabelle werden die erforderlichen Dateien zum Erstellen einer Element Vorlage für ein SharePoint-Projekt Element aufgelistet.

|Erforderliche Datei|BESCHREIBUNG|
|-------------------|-----------------|
|Eine *spdata* -Datei|Diese XML-Datei gibt den Inhalt und das Standardverhalten des Projekt Elements an. Diese Datei muss in der Element Vorlage enthalten sein. Weitere Informationen zum Inhalt von *spdata* -Dateien finden Sie unter [Schema Referenz für SharePoint-Projekt Elemente](../sharepoint/sharepoint-project-item-schema-reference.md).|
|Eine *VSTEMPLATE* -Datei.|Diese Datei bietet Visual Studio die Informationen, die erforderlich sind, um die Vorlage im Dialogfeld **Neues Element hinzufügen** anzuzeigen und ein Projekt Element aus der Vorlage zu erstellen. Diese Datei muss in der Element Vorlage enthalten sein. Weitere Informationen finden Sie unter [Visual Studio-Vorlagen-Metadatendateien](/previous-versions/visualstudio/visual-studio-2010/xsxc3ete\(v\=vs.100\)).|
|Eine Visual Studio-Erweiterungsassembly, die die- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> Schnittstelle implementiert.|Diese Assembly definiert das Laufzeitverhalten des Projekt Elements. Diese Assembly muss mit der Element Vorlage im VSIX-Paket enthalten sein. Weitere Informationen finden Sie unter [Definieren von benutzerdefinierten SharePoint-Projekt Elementtypen](../sharepoint/defining-custom-sharepoint-project-item-types.md) und bereitstellen [von Erweiterungen für die SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).|

 In der folgenden Tabelle sind einige der gängigsten optionalen Dateien aufgelistet, die in der-Element Vorlage enthalten sein können. Einige Typen von Projekt Elementen erfordern möglicherweise andere Dateien, die hier nicht aufgeführt sind.

| Optionale Datei | BESCHREIBUNG |
|----------------------| - |
| *Elements.xml* | Eine *featureelementdatei* . Diese Datei definiert die Benutzeroberfläche und das Verhalten der vom Projekt Element erstellten Anpassung. Jeder Anpassungstyp, z. b. Listen Instanzen, Inhaltstypen oder benutzerdefinierte Aktionen, verfügt über ein anderes Schema, das den Inhalt dieser Datei definiert. Weitere Informationen finden Sie unter [Baustein: Features](/previous-versions/office/developer/sharepoint-2010/ee537350(v=office.14)) und [Funktions Schemas](/previous-versions/office/developer/sharepoint-2010/ms414322(v=office.14)). |
| *Schema.xml* | Die Schema Datei für Listen Definitionen. Weitere Informationen finden Sie unter [Baustein: Listen und Dokument Bibliotheken](/previous-versions/office/developer/sharepoint-2010/ee534985(v=office.14)) und [Schema.xml](/previous-versions/office/developer/sharepoint-2010/ms459356(v=office.14)). |
| *. WebPart* | Eine *webpartdefinitions* Datei. Diese Datei enthält Eigenschafts Einstellungen für ein WebPart. Weitere Informationen finden Sie unter [Building Block: Webparts](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)). |
| *.ascx* | Eine ASP.net UserControl-Datei. Mit dieser Datei wird die Benutzeroberfläche eines visuellen Webparts definiert. |
| *. aspx* | Eine ASP.net-Auslagerungs Datei. Diese Datei enthält XML-Markup, das eine Anwendungsseite definiert. |
| *CS* -oder *VB* -Dateien | Diese Code Dateien definieren das Verhalten von SharePoint-Anpassungen, die über ein Programmiermodell verfügen, auf das von Visual c# oder Visual Basic Code, wie z. b. Anwendungs Seiten, Webparts und Workflows, zugegriffen werden kann. |

## <a name="create-project-templates"></a>Erstellen von Projektvorlagen
 Wenn Sie eine SharePoint-Projektvorlage erstellen, gibt es einige Dateien, die immer erforderlich sind, sowie optionale Dateien, die möglicherweise von bestimmten Projekttypen verwendet werden. In der Regel enthalten SharePoint-Projekte mindestens ein SharePoint-Projekt Element. Dies ist jedoch nicht erforderlich. Beispielsweise können Sie eine SharePoint-Projektvorlage definieren, die nur für die Bereitstellung von SharePoint-Lösungen verwendet werden soll, die in anderen Projekten erstellt wurden.

 Eine exemplarische Vorgehensweise, die veranschaulicht, wie ein SharePoint-Projekt Elementtyp definiert und eine Projektvorlage dafür erstellt wird, finden Sie unter Exemplarische Vorgehensweise [: Erstellen eines Website Spalten-Projekt Elements mit einer Projektvorlage, Teil 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).

 In der folgenden Tabelle werden die Dateien aufgelistet, die in einer SharePoint-Projektvorlage enthalten sein müssen.

|Erforderliche Datei|BESCHREIBUNG|
|-------------------|-----------------|
|Eine *VSTEMPLATE* -Datei|Diese Datei bietet Visual Studio die Informationen, die erforderlich sind, um die Vorlage im Dialogfeld **Neues Projekt** anzuzeigen und ein Projekt aus der Vorlage zu erstellen. Weitere Informationen finden Sie unter [Visual Studio-Vorlagen-Metadatendateien](/previous-versions/visualstudio/visual-studio-2010/xsxc3ete\(v\=vs.100\)).|
|Eine *csproj* -oder *vbproj* -Datei|Dies ist die Projektdatei. Der Inhalt und die Konfigurationseinstellungen des Projekts werden definiert.|
|*Package.package*|Diese Datei definiert das Bereitstellungs Paket für das Projekt. Wenn Sie den Paket-Designer verwenden, um das Projektmappenpaket für Ihr Projekt anzupassen, speichert Visual Studio Daten über das Lösungspaket in dieser Datei.<br /><br /> Wenn Sie eine benutzerdefinierte SharePoint-Projektvorlage erstellen, empfiehlt es sich, nur den mindestens erforderlichen Inhalt in die *Package. Package* -Datei einzufügen und das Projektmappenpaket mithilfe der APIs im- <xref:Microsoft.VisualStudio.SharePoint.Packages> Namespace in einer Erweiterung zu konfigurieren, die der Projektvorlage zugeordnet ist. Wenn Sie dies tun, ist die Projektvorlage vor zukünftigen Änderungen an der Struktur der *Package. Package* -Datei geschützt. Ein Beispiel, das veranschaulicht, wie Sie eine *Package. Package* -Datei mit nur den mindestens erforderlichen Inhalten erstellen, finden Sie unter Exemplarische Vorgehensweise [: Erstellen eines Website Spalten-Projekt Elements mit einer Projektvorlage, Teil 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).<br /><br /> Wenn Sie die Paketdatei " *Package. Package* " direkt ändern möchten, können Sie den Inhalt mit dem Schema unter " *% Program Files (x86)% \ Microsoft Visual Studio 11.0 \ xml\schemas\packagemodelschema.xsd*" überprüfen.|
|*Package.Template.xml*|Diese Datei stellt die Grundlage für die projektmappenmanifest-Datei (*manifest.xml*) für das SharePoint-Lösungspaket (*. wsp*) dar, das aus dem Projekt generiert wird. Sie können dieser Dateiinhalt hinzufügen, wenn Sie ein Verhalten angeben möchten, das nicht von Benutzern Ihres Projekt Typs geändert werden soll. Weitere Informationen finden Sie unter [Building Block: Solutions](/previous-versions/office/developer/sharepoint-2010/ee537008(v=office.14)) and [Solution Schema](/sharepoint/dev/schema/solution-schema).<br /><br /> Wenn Sie ein Projektmappenpaket aus dem Projekt erstellen, führt Visual Studio den Inhalt des *Pakets Package. Package* und der *Package.Template.xml* Dateien in der projektmappenmanifest-Datei zusammen. Weitere Informationen zum Erstellen von Lösungs Paketen finden Sie unter Gewusst [wie: Erstellen eines SharePoint-Lösungs Pakets mithilfe von MSBuild-Tasks](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md).|

 In der folgenden Tabelle sind die optionalen Dateien aufgeführt, die in der Projektvorlage enthalten sein können.

|Optionale Datei|BESCHREIBUNG|
|-------------------|-----------------|
|SharePoint-Projektelemente|Sie können eine oder mehrere spdata-Dateien einschließen, die SharePoint-Projekt Elementtypen definieren. Jede *spdata* -Datei muss über eine übereinstimmende <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> Implementierung in einer Erweiterungsassembly verfügen, die im VSIX-Paket mit der Projektvorlage enthalten ist. Weitere Informationen finden Sie unter [Erstellen von Element Vorlagen](#create-item-templates).<br /><br /> In der Regel enthalten SharePoint-Projekte mindestens ein SharePoint-Projekt Element. Dies ist jedoch nicht erforderlich.|
|*\<featureName>. Feature*|Diese Datei definiert ein SharePoint-Feature, das zum Gruppieren mehrerer Projekt Elemente für die Bereitstellung verwendet wird. Wenn Sie den Funktions-Designer verwenden, um eine Funktion in Ihrem Projekt anzupassen, speichert Visual Studio Daten über das Feature in dieser Datei. Wenn Sie die Projekt Elemente in verschiedene Funktionen gruppieren möchten, können Sie mehrere Featuredateien *einschließen.*<br /><br /> Wenn Sie eine benutzerdefinierte SharePoint-Projektvorlage erstellen, wird empfohlen, dass Sie nur den mindestens erforderlichen Inhalt *in jede* Featuredatei einschließen und Features konfigurieren, indem Sie die APIs im- <xref:Microsoft.VisualStudio.SharePoint.Features> Namespace in einer Erweiterung verwenden, die mit der Projektvorlage verknüpft ist. Wenn Sie dies tun, ist die Projektvorlage vor zukünftigen Änderungen an der Struktur der *Funktions* Datei geschützt. Ein Beispiel, das veranschaulicht, *wie eine* Featuredatei mit nur den mindestens erforderlichen Inhalten erstellt wird, finden Sie unter Exemplarische Vorgehensweise [: Erstellen eines Projekt Elements für eine Website Spalte mit einer Projektvorlage, Teil 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).<br /><br /> Wenn *Sie eine* Featuredatei direkt ändern möchten, können Sie den Inhalt mit dem Schema unter *% Program Files (x86)% \ Microsoft Visual Studio 11.0 \ xml\schemas\featuremodelschema.xsd* überprüfen.|
|*\<featureName>.Template.xml*|Diese Datei enthält die Basis für die featuremanifestressdatei (*Feature.xml*) für jede Funktion, die aus dem Projekt generiert wird. Sie können dieser Dateiinhalt hinzufügen, wenn Sie ein Verhalten angeben möchten, das nicht von Benutzern Ihres Projekt Typs geändert werden soll. Weitere Informationen finden Sie unter [Baustein: Features](/previous-versions/office/developer/sharepoint-2010/ee537350(v=office.14)) und [Feature.xml](/sharepoint/dev/schema/feature-xml-files) Dateien.<br /><br /> Wenn Sie ein Projektmappenpaket aus dem Projekt erstellen, führt Visual Studio die Inhalte der einzelnen featuredateipaare und *\<featureName>.Template.xml* Dateien in einer featuremanifesteindatei zusammen. *\<featureName>* Weitere Informationen zum Erstellen von Lösungs Paketen finden Sie unter Gewusst [wie: Erstellen eines SharePoint-Lösungs Pakets mithilfe von MSBuild-Tasks](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md).|

## <a name="create-wizards-for-item-templates-and-project-templates"></a>Erstellen von Assistenten für Element Vorlagen und Projektvorlagen
 Nachdem Sie einen SharePoint-Projekt Elementtyp definiert und mit einem Element oder einer Projektvorlage verknüpft haben, können Sie auch einen Assistenten erstellen. Der Assistent wird angezeigt, wenn ein Entwickler die Element Vorlage verwendet, um das SharePoint-Projekt Element einem Projekt hinzuzufügen, oder wenn ein Entwickler die Projektvorlage zum Erstellen eines neuen Projekts verwendet, das das SharePoint-Projekt Element enthält. Der Assistent kann verwendet werden, um Informationen von Entwicklern zu sammeln und das neue SharePoint-Projekt Element zu initialisieren.

 Exemplarische Vorgehensweisen, die veranschaulichen, wie Assistenten für Element Vorlagen und Projektvorlagen erstellt werden, finden Sie unter Exemplarische [Vorgehensweise: Erstellen eines benutzerdefinierten Aktionsprojekt Elements mit einer Element Vorlage, Teil 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md) und Exemplarische Vorgehensweise [: Erstellen eines Website Spalten-Projekt Elements mit einer Projektvorlage, Teil 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).

## <a name="see-also"></a>Weitere Informationen

- [Definieren von benutzerdefinierten SharePoint-Projekt Elementtypen](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Aktionsprojekt Elements mit einer Element Vorlage, Teil 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Aktionsprojekt Elements mit einer Element Vorlage, Teil 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)
- [Exemplarische Vorgehensweise: Erstellen eines Projekt Elements für eine Website Spalte mit einer Projektvorlage, Teil 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [Exemplarische Vorgehensweise: Erstellen eines Projekt Elements für eine Website Spalte mit einer Projektvorlage, Teil 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)
- [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)
