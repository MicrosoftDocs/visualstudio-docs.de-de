---
title: '&lt;Anpassungs &gt; Element (Office-Entwicklung in Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <customization> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1239c6749f25bf4bce7a1f5cc89a2a8430c98a4d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544871"
---
# <a name="ltcustomizationgt-element-office-development-in-visual-studio"></a>&lt;Anpassungs &gt; Element (Office-Entwicklung in Visual Studio)
  Das `customization` -Element des `vstov4` -Namespace beschreibt eine bestimmte Office-Projektmappe. Die untergeordneten Elemente sind für Anpassungen auf Dokumentebene und für VSTO-Add-Ins unterschiedlich.

## <a name="syntax-for-document-level-customizations"></a>Syntax für Anpassungen auf Dokument Ebene

```xml
<customization
  id
  <document
    solutionId
  />
</customization>
```

## <a name="syntax-for-vsto-add-ins"></a>Syntax für VSTO-Add-Ins

```xml
<customization
  id
  <appAddin
    application
    loadBehavior
    keyName>
  <friendlyName></friendlyName>
  <description></description>
  <formRegions></formRegions>
</customization>
```

## <a name="elements-and-attributes"></a>Elemente und Attribute
 Das `customization` -Element enthält anpassungsspezifische Informationen. Dieses Element muss sich im folgenden Namespace befinden: `vstov4=urn:schemas-microsoft-com:vsto.v4`. Für jede Office-Projektmappe ist ein `customization` -Element vorhanden. Wenn Sie z. B. in einer Bereitstellung mit mehreren Projekten drei Office-Projektmappen bereitstellen, befinden sich im Anwendungsmanifest drei `customization` -Elemente.

 Untergeordnete Elemente der Assembly müssen sich ebenfalls in diesem Namespace befinden.

 Das `customization` -Element hat das folgende Attribut.

|attribute|Beschreibung|
|---------------|-----------------|
|`id`|Ist für eine Bereitstellung mit mehreren Projekten erforderlich. Das `id` -Element kennzeichnet eine Office-Projektmappe eindeutig.|

### <a name="document-level-customizations"></a>Anpassungen auf Dokument Ebene
 Das `customization` -Element hat das folgende untergeordnete Element:

#### <a name="document"></a>Dokument
 Das- `document` Element im- `vstov4` Namespace wird in [&#60;Document&#62;-Elements &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/document-element-office-development-in-visual-studio.md)definiert.

### <a name="vsto-add-ins"></a>VSTO-Add-Ins
 Das `customization` -Element hat das folgende untergeordnete Element:

#### <a name="appaddin"></a>appAddin
 Das- `appAddin` Element im- `vstov4` Namespace wird in [&#60;appAddin&#62;-Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/appaddin-element-office-development-in-visual-studio.md)definiert.

## <a name="example-of-a-document-level-customization"></a>Beispiel für eine Anpassung auf Dokument Ebene

### <a name="description"></a>Beschreibung
 Im folgenden Codebeispiel wird das `customization` -Element für eine Anpassung auf Dokumentebene veranschaulicht. Dieses Codebeispiel ist Teil eines größeren Beispiels, das in [Anwendungs Manifesten für Office](../vsto/application-manifests-for-office-solutions.md)-Projektmappen bereitgestellt wird.

### <a name="code"></a>Code

```xml
<vstov4:customization>
  <vstov4:document
    solutionId="73e" />
</vstov4:customization>
```

## <a name="example-of-a-vsto-add-in"></a>Beispiel für ein VSTO-Add-in

### <a name="description"></a>Beschreibung
 Im folgenden Codebeispiel wird das- `customization` Element für ein VSTO-Add-in veranschaulicht. Das Add-In ist ein Outlook-VSTO-Add-in, das Formularbereiche enthält. Dieses Codebeispiel ist Teil eines größeren Beispiels, das in [Anwendungs Manifesten für Office](../vsto/application-manifests-for-office-solutions.md)-Projektmappen bereitgestellt wird.

### <a name="code"></a>Code

```xml
<vstov4:customization>
  <vstov4:appAddIn
    application="Outlook"
    loadBehavior="3"
    keyName="ContosoOutlookAddIn">
    <vstov4:friendlyName>
      ContosoOutlookAddIn
    </vstov4:friendlyName>
    <vstov4:description>
      ContosoOutlookAddIn - Outlook VSTO Add-in
      created with Visual Studio Tools for Office
    </vstov4:description>
    <vstov4:formRegions>
      <vstov4:formRegion
          name="OutlookAddIn1.FormRegion1">
        <vstov4:messageClass name="IPM.Note" />
        <vstov4:messageClass name="IPM.Contact" />
        <vstov4:messageClass name="IPM.Appointment" />
      </vstov4:formRegion>
    </vstov4:formRegions>
  </vstov4:appAddIn>
</vstov4:customization>
```

## <a name="see-also"></a>Siehe auch

- [Anwendungs Manifeste für Office-Lösungen](../vsto/application-manifests-for-office-solutions.md)
- [Bereitstellungs Manifeste für Office-Lösungen](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce-Anwendungs Manifest](../deployment/clickonce-application-manifest.md)