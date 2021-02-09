---
title: '&lt;EntryPoint- &gt; Element (Office-Entwicklung in Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <entryPoint> element
- <entryPoint> element
- entryPoint element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a75729d4be4aa96c3c118fed126af3ff84c18bcb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910449"
---
# <a name="ltentrypointgt-element-office-development-in-visual-studio"></a>&lt;EntryPoint- &gt; Element (Office-Entwicklung in Visual Studio)
  Durch jedes `entryPoint` -Element im `vstav3` -Namespace wird eine Anpassungsassembly gekennzeichnet, die bei Installation dieser [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] -Anwendung ausgeführt werden sollte.

## <a name="syntax"></a>Syntax

```xml
<entryPoint class>
    <assemblyIdentity />
</entryPoint>
```

## <a name="elements-and-attributes"></a>Elemente und Attribute
 Das `entryPoint` -Element ist erforderlich und befindet sich im `vstav3` -Namespace.

 Jedes `entryPoint` -Element kann nur eine Anpassungsassembly enthalten. In einem Anwendungsmanifest können mehrere `entryPoint` -Elemente definiert werden.

 Das `entryPoint` -Element weist folgende Attribute auf.

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|`class`|Erforderlich. Kennzeichnet eine auszuführende Anpassungsassembly. Die Syntax für dieses Attribut ist *NamespaceName.ClassName*.|

 `entryPoint` weist das folgende Element auf:

### <a name="assemblyidentity"></a>assemblyIdentity
 Erforderlich. Das `assemblyIdentity` -Element im `vstav3` -Namespace verweist auf ein vorhandenes `assemblyIdentity` -Element im [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] -Anwendungsmanifest.

 Die Rolle von `assemblyIdentity` und den zugehörigen Attributen wird in [&#60;assemblyIdentity-&#62; Element &#40;ClickOnce-Anwendungs&#41;](../deployment/assemblyidentity-element-clickonce-application.md)definiert.

## <a name="document-level-customization-example"></a>Beispiel für eine Anpassung auf Dokument Ebene

### <a name="description"></a>BESCHREIBUNG
 Das folgende Codebeispiel veranschaulicht `entryPoint` -Elemente in einem Anwendungsmanifest für eine mit [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]bereitgestellte Office-Projektmappe auf Dokumentebene. Dieses Codebeispiel ist Teil eines größeren Beispiels, das in [Anwendungs Manifesten für Office](../vsto/application-manifests-for-office-solutions.md)-Projektmappen bereitgestellt wird.

### <a name="code"></a>Code

```xml
<vstav3:entryPoint
  class="ContosoExcelWorkbook.ThisWorkbook">
  <assemblyIdentity
    name="ContosoExcelWorkbook"
    version="1.0.0.0"
    language="neutral"
    processorArchitecture="msil" />
</vstav3:entryPoint>
<vstav3:entryPoint
  class="ContosoExcelWorkbook.Sheet1">
  <assemblyIdentity
    name="ContosoExcelWorkbook"
    version="1.0.0.0"
    language="neutral"
    processorArchitecture="msil" />
</vstav3:entryPoint>
<vstav3:entryPoint
  class="ContosoExcelWorkbook.Sheet2">
  <assemblyIdentity
    name="ContosoExcelWorkbook"
    version="1.0.0.0"
    language="neutral"
    processorArchitecture="msil" />
</vstav3:entryPoint>
<vstav3:entryPoint
  class="ContosoExcelWorkbook.Sheet3">
  <assemblyIdentity
    name="ContosoExcelWorkbook"
    version="1.0.0.0"
    language="neutral"
    processorArchitecture="msil" />
</vstav3:entryPoint>
```

## <a name="vsto-add-in-example"></a>Beispiel für ein VSTO-Add-in

### <a name="description"></a>BESCHREIBUNG
 Das folgende Codebeispiel veranschaulicht ein `entryPoint` -Element in einem Anwendungsmanifest für eine mit [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]bereitgestellte Office-Projektmappe auf Anwendungsebene. Dieses Codebeispiel ist Teil eines größeren Beispiels, das in [Anwendungs Manifesten für Office](../vsto/application-manifests-for-office-solutions.md)-Projektmappen bereitgestellt wird.

### <a name="code"></a>Code

```xml
<vstav3:entryPoint
  class="ContosoOutlookAddIn.ThisAddIn">
  <assemblyIdentity
    name="ContosoOutlookAddIn"
    version="1.0.0.0"
    language="neutral"
    processorArchitecture="msil" />
</vstav3:entryPoint>
```

## <a name="see-also"></a>Siehe auch

- [Anwendungs Manifeste für Office-Lösungen](../vsto/application-manifests-for-office-solutions.md)
- [Bereitstellungs Manifeste für Office-Lösungen](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce-Anwendungs Manifest](../deployment/clickonce-application-manifest.md)