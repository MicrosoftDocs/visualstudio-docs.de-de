---
title: Combo-Element | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- Combos element (VSCT XML schema)
- VSCT XML schema elements, Combos
ms.assetid: 392e3063-f0a0-4130-9583-23bd2aa3fa36
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: daa89266d653743a743f42e5f0b8e11c954adc1a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184410"
---
# <a name="combo-element"></a>Combo-Element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Definiert Befehle, die in einem Kombinations Feld angezeigt werden. Es gibt vier Arten von Kombinations Feldern: dropdowncombo, dynamiccombo, indexcombo und mrucombo.  
  
## <a name="syntax"></a>Syntax  
  
```  
<combo guid="guidMyCommandSet" id="MyCommand" defaultWidth="20" idCommandList="MyCommandListID" priority="0x102" type="DropDownCombo">  
  <Parent>... </Parent  
  <CommandFlag>... </CommandFlag>  
  <Strings>... </Strings>  
</combo>  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|attribute|Beschreibung|  
|---------------|-----------------|  
|guid|Erforderlich. GUID des GUID-/ID-befehlsbezeichners.|  
|id|Erforderlich. ID des GUID-/ID-befehlsbezeichners.|  
|DefaultWidth|Erforderlich. Eine ganze Zahl, die eine Pixel Breite für das Kombinations Feld angibt.|  
|idcommandlist|Erforderlich. Eine ID, die an das aktive Befehl wird-Ziel gesendet wird, um die Liste der Elemente abzurufen, die im Kombinations Feld angezeigt werden sollen. Die ID weist den gleichen GUID-Bereich wie das Steuerelement auf.|  
|priority|Optional. Ein numerischer Wert, der die Priorität angibt.|  
|type|Optional. Ein-Enumerationswert, der den Typ der Schaltfläche angibt.<br /><br /> Wenn nicht angegeben, wird die Schaltfläche verwendet.<br /><br /> Dropdowncombo<br /> Das VSPackage ist dafür verantwortlich, den Inhalt für dieses Kombinations Feld auszufüllen. Der Benutzer kann nichts in das Textfeld dieser Dropdown-Dropdown-Datei eingeben.<br /><br /> Dynamiccombo<br /> Das VSPackage ist für das Ausfüllen der Inhalte dieses Kombinations Felds verantwortlich. Der Benutzer kann dieses Kombinations Feld bearbeiten und darin Elemente auswählen.<br /><br /> Indexcombo<br /> Identisch mit dynamiccombo, außer dass es den Index des Elements anstatt seines Texts auslöst.<br /><br /> Mrucombo<br /> Wird von der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) im Auftrag des VSPackage ausgefüllt.  Der Benutzer kann in diesem Kombinations Feld bearbeiten. Die IDE speichert bis zu den letzten 16 Einträgen pro Kombinations Feld.<br /><br /> Wenn der Benutzer etwas im Kombinations Feld auswählt oder etwas neues eingibt, benachrichtigt die IDE das entsprechende VSPackage.|  
|Bedingung|Optional. Siehe [bedingte Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|Parent|Optional. Das übergeordnete Element der Schaltfläche.|  
|CommandFlag|Erforderlich. Siehe [Befehlsflag-Element](../extensibility/command-flag-element.md). Die gültigen CommandFlag-Werte für eine Schaltfläche lauten wie folgt.<br /><br /> -CaseSensitive<br /><br /> -Commandwellonly<br /><br /> -Defaultdeaktiviert<br /><br /> -Defaultinvisible<br /><br /> -Dynamicvisibility<br /><br /> -FilterKeys<br /><br /> -Iconandtext<br /><br /> -Noautocomplete<br /><br /> -Nobuttoncustomize<br /><br /> -Nocustomize<br /><br /> -Nokeycustomize<br /><br /> -Stretchhorizontal|  
|Zeichenfolgen|Erforderlich. Siehe [Strings-Element](../extensibility/strings-element.md). Das untergeordnete ButtonText-Element muss definiert werden.|  
|Anmerkung|Optionaler Kommentar.|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[Commands-Element](../extensibility/commands-element.md)|Stellt die Auflistung von Befehlen auf der VSPackage-Symbolleiste dar.|  
  
## <a name="example"></a>Beispiel  
  
```  
<Combo guid="guidWidgetPackage" id="cmdidInsertOptions"  
  defaultWidth="100" idCommandList="cmdidGetInsertOptionsList">  
  <CommandFlag>DynamicVisibility</CommandFlag>  
  <Strings>  
    <ButtonText>Select Insert Options</ButtonText>  
  </Strings>  
</Combo>  
  
<Combo guid="guidWidgetPackage" id="cmdidInsertOptions"  
  priority="0x0500" type="DropDownCombo" defaultWidth="100"  
  idCommandList="cmdidGetInsertOptionsList">  
  <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">  
  <CommandFlag>DynamicVisibility</CommandFlag>  
  <Strings>  
    <ButtonText>Select Insert Options</ButtonText>  
  </Strings>  
</Combo>  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [VSCT-Dateien (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
