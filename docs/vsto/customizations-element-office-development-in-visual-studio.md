---
title: '&lt;customialisierungen- &gt; Element (Office-Entwicklung in Visual Studio)'
description: Erfahren Sie, wie das Anpassungselement des vstov4-Namespace alle Informationen zum Installieren und Laden der einzelnen Office-Projektmappen enthält.
titleSuffix: ''
ms.custom: seodec18, SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- <customizations> element
- customizations element
- application manifests [Office development in Visual Studio], <customizations> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 27b20a13d96b8fc23fcde2dbb8f14d1f1f27ceea
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99849930"
---
# <a name="ltcustomizationsgt-element-office-development-in-visual-studio"></a>&lt;customialisierungen- &gt; Element (Office-Entwicklung in Visual Studio)
  Das `customizations` -Element des `vstov4` -Namespace enthält alle Informationen zum Installieren und Laden der einzelnen Office-Projektmappen.

## <a name="syntax-for-document-level-customizations"></a>Syntax für Anpassungen auf Dokument Ebene

```xml
<customizations>
  <customization
    id
    <document
      solutionId
    />
  </customization>
</customizations>
```

## <a name="syntax-for-vsto-add-ins"></a>Syntax für VSTO-Add-Ins

```xml
<customizations>
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
</customizations>
```

## <a name="elements-and-attributes"></a>Elemente und Attribute
 Das `customizations` -Element enthält bestimmte Informationen zu den einzelnen Office-Projektmappen. Dieses Element muss sich im folgenden Namespace befinden: `vstov4=urn:schemas-microsoft-com:vsto.v4`. Untergeordnete Elemente der Assembly müssen sich ebenfalls in diesem Namespace befinden.

 Das `customizations` -Element weist keine Attribute auf.

 Das `customizations` -Element hat das folgende untergeordnete Element:

### <a name="customization"></a>Anpassung
 Erforderlich. Das- `customization` Element im- `vstov4` Namespace wird in [&#60;Anpassung&#62; Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/customization-element-office-development-in-visual-studio.md)definiert.

## <a name="example-of-a-document-level-customization"></a>Beispiel für eine Anpassung auf Dokument Ebene

### <a name="description"></a>Beschreibung
 Im folgenden Codebeispiel wird das `customizations` -Element für eine Anpassung auf Dokumentebene veranschaulicht.

> [!NOTE]
> Dieses Codebeispiel ist Teil eines größeren Beispiels, das in [Anwendungs Manifesten für Office](../vsto/application-manifests-for-office-solutions.md)-Projektmappen bereitgestellt wird.

### <a name="code"></a>Code

```xml
<vstov4:customizations
  xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4">
  <vstov4:customization>
    <vstov4:document
      solutionId="73e" />
  </vstov4:customization>
</vstov4:customizations>
```

## <a name="example-of-a-vsto-add-in"></a>Beispiel für ein VSTO-Add-in

### <a name="description"></a>Beschreibung
 Im folgenden Codebeispiel wird das- `customizations` Element für ein VSTO-Add-in veranschaulicht. Das Add-In ist ein Outlook-VSTO-Add-in, das Formularbereiche enthält. Dieses Codebeispiel ist Teil eines größeren Beispiels, das in [Anwendungs Manifesten für Office](../vsto/application-manifests-for-office-solutions.md)-Projektmappen bereitgestellt wird.

### <a name="code"></a>Code

```xml
<vstov4:customizations
  xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4">
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
</vstov4:customizations>
```

## <a name="see-also"></a>Siehe auch

- [Anwendungs Manifeste für Office-Lösungen](../vsto/application-manifests-for-office-solutions.md)
- [Bereitstellungs Manifeste für Office-Lösungen](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce-Anwendungs Manifest](../deployment/clickonce-application-manifest.md)