---
title: Verpacken & Bereitstellungs Informationen in Projekt Elementen
description: Fügen Sie Paket-und Bereitstellungs Daten in SharePoint-Projekt Elementen mithilfe von Featureeigenschaften, Funktions Empfängern, Projekt Ausgabe verweisen und sicheren Steuerelement Entitäten hinzu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.SafeControlEntries
- VS.SharePointTools.Project.ProjectOutputReference
- VS.SharePointTools.Project.FeatureProperties
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, safe controls
- project output references [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, feature properties
- SharePoint development in Visual Studio, project output references
- SharePoint development in Visual Studio, advanced packaging tools
- feature properties [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, feature receiver
- feature receiver [SharePoint development in Visual Studio]
- safe controls [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f05e2035338ea4c2d0e45bb9d135d618b938e4ca
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889537"
---
# <a name="provide-packaging-and-deployment-information-in-project-items"></a>Bereitstellen von Pack- und Bereitstellungsinformationen in Projektelementen
  Alle SharePoint-Projekt Elemente in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] verfügen über Eigenschaften, mit denen Sie zusätzliche Daten bereitstellen können, wenn das Projekt in SharePoint bereitgestellt wird. Dort stehen die folgenden Eigenschaften zur Auswahl:

- Funktionseigenschaften

- Funktions Empfänger

- Projektausgabeverweise

- Einträge für sicheres Steuerelement

  Diese Eigenschaften werden im **Eigenschaften** Fenster angezeigt.

## <a name="feature-properties"></a>Funktionseigenschaften
 Verwenden Sie die Eigenschaft **Funktionseigenschaften** , um die Daten anzugeben, die von der Funktion verwendet werden. Bei Funktionseigenschaften handelt es sich um einen Satz von Werten (gespeichert als Schlüssel-Wert-Paare), der in einer Funktion enthalten ist, wenn Sie in SharePoint bereitgestellt wird. Nach dem Bereitstellen der Funktion können Sie im Code auf die Eigenschaftswerte zugreifen.

 Wenn Sie einem Projekt Element einen Funktions Eigenschafts Wert hinzufügen, wird der Wert als Element im Manifest der Funktion des Elements hinzugefügt. In einem Business Data Connectivity (BDC)-Modellprojekt wird z. b. die Feature-Eigenschaft Model filename wie folgt angezeigt:

```xml
<Property Key="ModelFileName" Value="BdcModel1\BdcModel1.bdcm" />
```

 Nachdem Sie einen Funktions Eigenschafts Wert festgelegt haben, wird er in der *spdata* -Datei des Projekts als FeatureProperty-Element hinzugefügt. Weitere Informationen über den Zugriff auf die Eigenschaften in SharePoint finden Sie unter [spfeaturepropertycollection-Klasse](/previous-versions/office/sharepoint-server/ms461895(v=office.15)).

 Identische Funktions Eigenschaftswerte aus allen Projekt Elementen werden im FeatureManifest zusammengeführt. Wenn jedoch zwei verschiedene Projekt Elemente denselben Funktions Eigenschafts Schlüssel mit nicht übereinstimmenden Werten angeben, tritt ein Validierungs Fehler auf.

 Um Featureeigenschaften direkt der Funktions Datei (*. Feature*) hinzuzufügen, müssen Sie die [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint-Objektmodell Methode abrufen <xref:Microsoft.VisualStudio.SharePoint.Features.IPropertyCollection.Add%2A> . Wenn Sie diese Methode verwenden, beachten Sie, dass dieselbe Regel zum Hinzufügen identischer Funktions Eigenschaftswerte in Funktionseigenschaften auch für Eigenschaften gilt, die der Featuredatei direkt hinzugefügt werden.

## <a name="feature-receiver"></a>Funktions Empfänger
 Funktions Empfänger sind Code, der ausgeführt wird, wenn bestimmte Ereignisse in der enthaltenden Funktion eines Projekt Elements auftreten. Beispielsweise können Sie Funktions Empfänger definieren, die ausgeführt werden, wenn das Feature installiert, aktiviert oder aktualisiert wird. Eine Möglichkeit, einen Funktions Empfänger hinzuzufügen, besteht darin, ihn direkt zu einer Funktion hinzuzufügen, wie in Exemplarische Vorgehensweise [: Hinzufügen von Funktions Ereignis Empfängern](../sharepoint/walkthrough-add-feature-event-receivers.md)beschrieben. Eine andere Möglichkeit besteht darin, in der Eigenschaft **Funktions Empfänger** auf einen Funktions Empfänger Klassennamen und eine Assembly zu verweisen.

### <a name="direct-method"></a>Direkte Methode
 Wenn Sie einem Feature einen Funktions Empfänger direkt hinzufügen, wird eine Codedatei unter dem **Funktions** Knoten in Projektmappen-Explorer platziert. Wenn Sie die SharePoint-Lösung erstellen, wird der Code in eine Assembly kompiliert und in SharePoint bereitgestellt. Standardmäßig verweisen die **clusterassembly** und die **Empfängerklasse** der Funktionseigenschaften auf den Klassennamen und die Assembly.

### <a name="reference-method"></a>Reference-Methode
 Eine weitere Möglichkeit zum Hinzufügen eines Funktions Empfängers besteht darin, mithilfe der Eigenschaft " **Funktions Empfänger** " eines Projekt Elements auf eine Merkmals Empfänger-Assembly zu verweisen. Der Eigenschafts Wert für den Funktions Empfänger verfügt über zwei untergeordnete Eigenschaften: **Assembly** und **Klassen Name**. Die Assembly muss den voll qualifizierten Namen "Strong" verwenden, und der Klassenname muss den vollständigen Typnamen aufweisen. Weitere Informationen finden Sie unter [Assemblys mit starkem Namen](/previous-versions/dotnet/netframework-4.0/wd40t7ad(v=vs.100)). Nach der Bereitstellung der Lösung in SharePoint verwendet die Funktion den Funktions Empfänger, auf den verwiesen wird, um featureereignisse zu behandeln.

 Zum Erstellungs Zeitpunkt der Lösung werden die Funktions Empfänger-Eigenschaftswerte in der Funktion und ihren Projekten zusammengeführt, um die ReceiverAssembly-und ReceiverClass-Attribute des Feature-Elements im FeatureManifest der SharePoint-Lösungs Datei (*wsp*-Datei) festzulegen. Wenn die Eigenschaftswerte für Assembly und Klassen Name eines Projekt Elements und eines Features festgelegt sind, müssen die Werte für das Projekt Element und die Funktions Eigenschaft daher identisch sein. Wenn die Werte nicht identisch sind, tritt ein Validierungs Fehler auf. Wenn ein Projekt Element auf eine Featureempfängerassembly verweisen soll, die nicht von der Funktion verwendet wird, die das Feature verwendet, verschieben Sie es in eine andere Funktion.

 Wenn Sie auf eine Merkmals Empfängerassembly verweisen, die sich nicht bereits auf dem Server befindet, müssen Sie auch die Assemblydatei selbst in das Paket einschließen. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] wird nicht für Sie hinzugefügt. Wenn Sie die Funktion bereitstellen, wird die Assemblydatei entweder in den [!INCLUDE[TLA#tla_gac](../sharepoint/includes/tlasharptla-gac-md.md)] Ordner des Systems oder den Ordner bin im physischen SharePoint-Verzeichnis kopiert. Weitere Informationen finden Sie unter Gewusst wie [: Hinzufügen und Entfernen zusätzlicher](../sharepoint/how-to-add-and-remove-additional-assemblies.md)Assemblys.

 Weitere Informationen zu Funktions Empfängern finden Sie unter [Funktions Ereignis Empfänger](/previous-versions/office/developer/sharepoint-2007/bb862634(v=office.12)) -und [featureereignisse](/previous-versions/office/developer/sharepoint-2010/ms469501(v=office.14)).

## <a name="project-output-references"></a>Projekt Ausgabe Verweise
 Die Eigenschaft Projekt Ausgabe Verweise gibt eine Abhängigkeit (z. b. eine Assembly) an, die für das Projekt Element ausgeführt werden muss. Angenommen, die Projekt Mappe verfügt über ein BDC-Projekt und ein-Klassenprojekt. Wenn das BDC-Projekt eine Abhängigkeit von der Assembly aufweist, die vom-Klassenprojekt ausgegeben wird, können Sie in der Projekt Ausgabe Verweis-Eigenschaft des BDC-Projekts auf die Assembly verweisen. Wenn das BDC-Projekt verpackt ist, ist die abhängige Assembly im Paket enthalten.

 Projekt Ausgabe Verweise sind in der Regel Assemblys, aber in einigen Fällen (z. b. Silverlight-Projekten) können andere Dateitypen sein.

 Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen eines Projekt Ausgabe Verweises](../sharepoint/how-to-add-a-project-output-reference.md).

## <a name="safe-control-entries"></a>Einträge für sicheres Steuerelement
 SharePoint bietet einen Sicherheitsmechanismus, der als Safe Control-Einträge bezeichnet wird, um den Zugriff von nicht vertrauenswürdigen Benutzern auf bestimmte Steuerelemente einzuschränken. Mithilfe von SharePoint können nicht vertrauenswürdige Benutzer ASPX-Seiten auf dem SharePoint-Server hochladen und erstellen. Um zu verhindern, dass diese Benutzer unsicheren Code zu ASPX-Seiten hinzufügen, schränkt SharePoint den Zugriff auf *sichere Steuerelemente* ein. Sichere Steuerelemente sind aspx-Steuerelemente und Webparts, die als sicher gekennzeichnet sind und von jedem Benutzer auf Ihrer Website verwendet werden können. Weitere Informationen finden Sie unter [Schritt 4: Hinzufügen des Webparts zur Liste der sicheren Steuerelemente](/previous-versions/office/developer/sharepoint-2007/ms581321(v=office.12)).

 Jedes SharePoint-Projekt Element in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] verfügt über eine Eigenschaft mit dem Namen " **Safe Control** "-Einträge, die zwei boolesche unter Eigenschaften aufweisen: **sicher** und **sicher für Skripts**. Die Safe-Eigenschaft gibt an, ob nicht vertrauenswürdige Benutzer auf ein Steuerelement zugreifen können. Die Eigenschaft "Safe Against Script" gibt an, ob nicht vertrauenswürdige Benutzer die Eigenschaften eines Steuer Elements anzeigen und ändern können.

 Verweise auf sichere Steuerelemente werden auf assemblybasis referenziert. Sie fügen der Assembly eines Projekts sichere Steuerelement Einträge hinzu, indem Sie Sie in der Eigenschaft " **Safe Control Entries** " des Projekt Elements eingeben. Sie können jedoch auch über die Registerkarte **erweitert** im **Paket-Designer** sichere Steuerelement Einträge zu einer projekterassembly hinzufügen, wenn Sie dem Paket eine zusätzliche Assembly hinzufügen. Weitere Informationen finden Sie unter Gewusst wie [: Markieren von Steuerelementen als sichere Steuerelemente](../sharepoint/how-to-mark-controls-as-safe-controls.md) oder [Registrieren einer Webpartassembly als sicheres Steuer](/previous-versions/office/developer/sharepoint2003/dd587360(v=office.11))Element.

### <a name="xml-entries-for-safe-controls"></a>XML-Einträge für sichere Steuerelemente
 Wenn Sie einem Projekt Element oder der Assembly des Projekts einen Eintrag für ein sicheres Steuerelement hinzufügen, wird ein Verweis in das Paket Manifest im folgenden Format geschrieben:

```xml
<Assemblies>
    <Assembly Location="<assembly name>.dll"
      DeploymentTarget="<'GlobalAssemblyCache' or 'WebApplication'">>
        <SafeControls>
            <SafeControl Assembly="<assembly name>.dll" Namespace=
              "<SharePoint project name>" Safe="<true/false>"
                TypeName="<control name>"
                SafeAgainstScript="<true/false>" />
        </SafeControls>
    </Assembly>
</Assemblies>
```

## <a name="see-also"></a>Weitere Informationen
- [Packen und Bereitstellen von SharePoint-Lösungen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
- [Verwenden von Modulen zum Einbinden von Dateien in eine Projektmappe](../sharepoint/using-modules-to-include-files-in-the-solution.md)
- [Erweiterte SharePoint-Paket Erstellung und-Bereitstellung](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
