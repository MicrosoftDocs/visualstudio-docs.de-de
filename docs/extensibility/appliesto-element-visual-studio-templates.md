---
title: AppliesTo-Element (Visual Studio-Vorlagen) | Microsoft-Dokumentation
description: Informieren Sie sich über das AppliesTo-Element und darüber, wie es einen optionalen Ausdruck angibt, mit dem eine oder mehrere Funktionen verglichen werden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 8fb1334b-d78c-405f-98b4-786e9f6b58d7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 48f1d7e0011b3f195224d8e55072ccd4c7666802
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876120"
---
# <a name="appliesto-element-visual-studio-templates"></a>AppliesTo-Element (Visual Studio-Vorlagen)

Gibt einen optionalen Ausdruck an, um eine oder mehrere Funktionen abzugleichen (siehe <xref:Microsoft.VisualStudio.Shell.Interop.VsProjectCapabilityExpressionMatcher> ). Funktionen werden von Projekttypen über die Hierarchie als Eigenschafts [__VSHPROPID5 verfügbar gemacht. VSHPROPID_ProjectCapabilities](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID5.VSHPROPID_ProjectCapabilities>). Dadurch kann die Vorlage von mehreren Projekttypen gemeinsam genutzt werden, die über geläufige anwendbare Funktionen verfügen.

Dieses Element ist optional. Es kann maximal eine Instanz in einer Vorlagendatei geben. Dieses Element ermöglicht einer Elementvorlage nur, auf Grundlage der Funktionen des ausgewählten aktiven Projekts als anwendbar zu optieren. Es kann nicht verwendet werden, um eine Elementvorlage nicht anwendbar zu machen. Wenn `AppliesTo` fehlt oder der Ausdruck nicht erfolgreich optiert, wird `TemplateID` oder `TemplateGroupID` verwendet, um die Vorlage anwendbar zu machen, wie mit früheren Versionen des Produkts.

Eingeführt in Visual Studio 2013 Update 2. Weitere Informationen zum Verweisen auf die richtige Version finden Sie unter referenzieren von Assemblys, [die im Visual Studio 2013 SDK-Update 2](/previous-versions/dn632168(v=vs.120))

```xml
<VSTemplate>
   <TemplateData>
      <AppliesTo>
```

## <a name="syntax"></a>Syntax

```xml
<AppliesTo>Capability1</AppliesTo>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

Keine

### <a name="child-elements"></a>Untergeordnete Elemente

Keine

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Kategorisiert die Vorlage.|

## <a name="text-value"></a>Textwert

Ein Textwert ist erforderlich. Dieser Text gibt die Funktionen des Projekts an.

Gültige Ausdruckssyntax ist folgendermaßen definiert:

- Der Funktions Ausdruck, z. b. "(VisualC &#124; CSharp) + (MSTest &#124; nunit)".

- Das "&#124;" ist der or-Operator.

- Die Zeichen "&" und "+" sind sowohl-als auch-Operatoren.

- Das Zeichen "!" ist der Operator NOT.

- Klammern erzwingen die Auswertungsreihenfolge.

- Eine leerer oder NULL-Ausdruck wird als Übereinstimmung ausgewertet.

- Projektfunktionen können ein beliebiges Zeichen mit Ausnahme der folgenden reservierten Zeichen sein: "'":;, +-*/ \\ ! ~&#124;&% $ @ ^ () = {} [] <>? \t\b\n\r

## <a name="example"></a>Beispiel

Im folgenden Beispiel werden drei unterschiedliche Vorlagen gezeigt. `Template1` gilt entweder für alle c#-Projekttypen oder für einen beliebigen anderen Projekttyp, der die Funktion unterstützt `WindowsAppContainer` . `Template2` gilt für alle c#-Projekte beliebiger Art. `Template3` gilt für C#-Projekte, die keine `WindowsAppContainer` sind Projekte.

```xml
<!--  Template 1 -->
<?xml version="1.0" encoding="utf-8"?>
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <AppliesTo>CSharp | WindowsAppContainer</AppliesTo>
    </TemplateData>
</VSTemplate>

<!--  Template 2 -->
<?xml version="1.0" encoding="utf-8"?>
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <AppliesTo>CSharp</AppliesTo>
    </TemplateData>
</VSTemplate>

<!--  Template 1 -->
<?xml version="1.0" encoding="utf-8"?>
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <AppliesTo>CSharp_Class + (!WindowsAppContainer)</AppliesTo>
    </TemplateData>
</VSTemplate>
```

## <a name="see-also"></a>Siehe auch

- [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)
- [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)
