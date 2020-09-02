---
title: VSIXLanguagePack-Element (VSIX-Sprachpaket Schema) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
ms.assetid: 767f5c22-8b87-49ca-92aa-a7a3f026469f
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e2e1df362fddeab5be98ff90460a8a1a7d4b7876
ms.sourcegitcommit: 26178b116cbf7353fee6ca989b8d872114f7b405
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/01/2020
ms.locfileid: "89284337"
---
# <a name="vsixlanguagepack-element-vsix-language-pack-schema"></a>VSIXLanguagePack-Element (Schema für das VSIX-Sprachpaket)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Erforderlich. Stellt das Stamm Element für ein VSIX-Sprachpaket bereit. Das VSIX-Sprachpaket enthält lokalisierte Installationsinformationen für ein VSIX-Paket.  
  
## <a name="syntax"></a>Syntax  
  
```  
<VSIXLanguagePack>  
  <LocalizedName>...</LocalizedName>  
  <LocalizedDescription>...</LocalizedDescription>  
  <MoreInfoURL>...</MoreInfoURL>  
  <License>...</License>  
</VSIXLanguagePack>  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|attribute|BESCHREIBUNG|  
|---------------|-----------------|  
|`xmlns`|Der XML-Namespace, in dem das VSIX-Sprachpaket Schema definiert ist.|  
  
## <a name="xmlns-attribute"></a>xmlns-Attribut  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|`http://schemas.microsoft.com/developer/vsx-schema-lp/2010`|Erforderlich. Der Speicherort der Datei, die das Schema für Sprachpakete definiert.|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|BESCHREIBUNG|  
|-------------|-----------------|  
|[LocalizedName-Element](../extensibility/localizedname-element-vsix-language-pack-schema.md)|Erforderlich. Der lokalisierte Name der zu installierenden Erweiterung.|  
|[LocalizedDescription-Element](../extensibility/localizeddescription-element-vsix-language-pack-schema.md)|Erforderlich. Die lokalisierte Beschreibung der zu installierenden Erweiterung.|  
|[MoreInfoURL-Element](../extensibility/moreinfourl-element-vsix-language-pack-schema.md)|Optional. Ein Link zu lokalisierten Informationen über die Erweiterung.|  
|[License-Element](../extensibility/license-element-vsix-language-pack-schema.md)|Optional. Der Pfad einer lokalisierten Version der Lizenzdatei für die Erweiterung.|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|BESCHREIBUNG|  
|-------------|-----------------|  
|Keine||  
  
## <a name="element-information"></a>Elementinformationen  
  
|                 |                                                           |
|-----------------|-----------------------------------------------------------|
|    Namespace    | `http://schemas.microsoft.com/developer/vsx-schema-lp/2010` |
|   Name des Schemas   |                 VSIX-Sprachpaket Schema                 |
| Validierungsdatei |                Vsixlanguagepackschema. xsd                 |
|  Kann leer sein   |                            Nein                             |
  
## <a name="see-also"></a>Siehe auch  
 [VSX Language Pack Schema Referenz](../extensibility/vsx-language-pack-schema-reference.md) [Lokalisieren von VSIX-Paketen](../extensibility/localizing-vsix-packages.md) [VSIX-Erweiterungs Schema 1,0 Referenz](/previous-versions/dd393700(v=vs.110))
