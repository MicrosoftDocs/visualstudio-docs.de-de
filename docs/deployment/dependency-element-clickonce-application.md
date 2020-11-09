---
title: '&lt;Abhängigkeits &gt; Element (ClickOnce-Anwendung) | Microsoft-Dokumentation'
description: Das Abhängigkeits Element identifiziert eine Plattform-oder Assemblyabhängigkeit, die für die Anwendung erforderlich ist.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#osVersionInfo
- urn:schemas-microsoft-com:asm.v2#os
- http://www.w3.org/2000/09/xmldsig#Transform
- urn:schemas-microsoft-com:asm.v2#dependency
- http://www.w3.org/2000/09/xmldsig#DigestValue
- urn:schemas-microsoft-com:asm.v2#assemblyIdentity
- http://www.w3.org/2000/09/xmldsig#DigestMethod
- http://www.w3.org/2000/09/xmldsig#Transforms
- urn:schemas-microsoft-com:asm.v2#hash
- urn:schemas-microsoft-com:asm.v2#dependentAssembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- manifests [ClickOnce], dependency element
- <dependency> element [ClickOnce application manifest]
ms.assetid: 09d6a1e0-60f8-4fbd-843b-8e49ee3115a3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e7896fa2d39bafc793c5fd74f66f4991cf5e8461
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2020
ms.locfileid: "94382948"
---
# <a name="ltdependencygt-element-clickonce-application"></a>&lt;Abhängigkeits &gt; Element (ClickOnce-Anwendung)
Identifiziert eine Plattform-oder Assemblyabhängigkeit, die für die Anwendung erforderlich ist.

## <a name="syntax"></a>Syntax

```xml

      <dependency>
   <dependentOS
      supportURL
      description
   >
      <osVersionInfo>
         <os
            majorVersion
            minorVersion
            buildNumber
            servicePackMajor
            servicePackMinor
            productType
            suiteType
         />
      </osVersionInfo>
   </dependentOS>
   <dependentAssembly
      dependencyType
      allowDelayedBinding
      group
      codeBase
      size
   >
      <assemblyIdentity
         name
         version
         processorArchitecture
         language
      >
         <hash>
            <dsig:Transforms>
               <dsig:Transform
                  Algorithm
            />
            </dsig:Transforms>
            <dsig:DigestMethod />
            <dsig:DigestValue>
            </dsig:DigestValue>
    </hash>

      </assemblyIdentity>
   </dependentAssembly>
</dependency>
```

## <a name="elements-and-attributes"></a>Elemente und Attribute
 Das `dependency`-Element ist erforderlich. Es können mehrere Instanzen von `dependency` im selben Anwendungs Manifest vorhanden sein.

 Das `dependency` -Element hat keine Attribute und enthält die folgenden untergeordneten Elemente.

### <a name="dependentos"></a>dependentOS
 Optional. Enthält das- `osVersionInfo` Element. Das `dependentOS` -Element und das- `dependentAssembly` Element schließen sich gegenseitig aus: eine oder die andere muss für ein-Element vorhanden sein `dependency` , aber nicht beides.

 `dependentOS` unterstützt die folgenden Attribute.

|attribute|Beschreibung|
|---------------|-----------------|
|`supportUrl`|Optional. Gibt eine Support-URL für die abhängige Plattform an. Diese URL wird dem Benutzer angezeigt, wenn die erforderliche Plattform gefunden wird.|
|`description`|Optional. Beschreibt in Menschen lesbarem Format das Betriebssystem, das durch das- `dependentOS` Element beschrieben wird.|

### <a name="osversioninfo"></a>osVersionInfo
 Erforderlich. Dieses Element ist ein untergeordnetes Element des `dependentOS` -Elements und enthält das `os` -Element. Dieses Element weist keine Attribute auf.

### <a name="os"></a>os
 Erforderlich. Dieses Element ist ein untergeordnetes Element des `osVersionInfo` -Elements. Dieses Element weist folgende Attribute auf.

|attribute|Beschreibung|
|---------------|-----------------|
|`majorVersion`|Erforderlich. Gibt die Hauptversionsnummer des Betriebssystems an.|
|`minorVersion`|Erforderlich. Gibt die neben Versionsnummer des Betriebssystems an.|
|`buildNumber`|Erforderlich. Gibt die Buildnummer des Betriebssystems an.|
|`servicePackMajor`|Erforderlich. Gibt die Service Pack Hauptnummer des Betriebssystems an.|
|`servicePackMinor`|Optional. Gibt die Service Pack neben Version des Betriebssystems an.|
|`productType`|Optional. Identifiziert den Wert des Produkttyps. Gültige Werte sind `server`, `workstation` und `domainController`. Für Windows 2000 Professional lautet der Wert dieses Attributs z `workstation` . b..|
|`suiteType`|Optional. Identifiziert eine auf dem System verfügbare Produktsuite oder den Konfigurationstyp des Systems. Gültige Werte sind `backoffice`, `blade`, `datacenter`, `enterprise`, `home`, `professional`, `smallbusiness`, `smallbusinessRestricted` und `terminal`. Für Windows 2000 Professional lautet der Wert dieses Attributs z `professional` . b..|

### <a name="dependentassembly"></a>dependentAssembly
 Optional. Enthält das- `assemblyIdentity` Element. Das `dependentOS` -Element und das- `dependentAssembly` Element schließen sich gegenseitig aus: eine oder die andere muss für ein-Element vorhanden sein `dependency` , aber nicht beides.

 `dependentAssembly` weist die folgenden Attribute auf.

| attribute | Beschreibung |
|-----------------------| - |
| `dependencyType` | Erforderlich. Gibt den Typ der Abhängigkeit an. Gültige Werte sind `preprequisite` und `install`. Eine `install` Assembly wird als Teil der Anwendung installiert [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . Eine `prerequisite` Assembly muss im globalen Assemblycache (GAC) vorhanden sein, bevor die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung installiert werden kann. |
| `allowDelayedBinding` | Erforderlich. Gibt an, ob die Assembly zur Laufzeit Programm gesteuert geladen werden kann. |
| `group` | Optional. Wenn das- `dependencyType` Attribut auf festgelegt ist `install` , bestimmt eine benannte Gruppe von Assemblys, die nur bei Bedarf installiert werden. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Herunterladen von Assemblys bei Bedarf mit der API für die ClickOnce-Bereitstellung unter Verwendung des Designers](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer.md).<br /><br /> Wenn auf festgelegt `framework` und das- `dependencyType` Attribut auf festgelegt ist `prerequisite` , legt die Assembly als Teil der .NET Framework fest. Der globale Assemblycache (GAC) wird bei der Installation auf .NET Framework 4 und höheren Versionen nicht für diese Assembly geprüft. |
| `codeBase` | Erforderlich, wenn das- `dependencyType` Attribut auf festgelegt ist `install` . Der Pfad zur abhängigen Assembly. Kann entweder ein absoluter Pfad oder ein Pfad in Bezug auf die Codebasis des Manifests sein. Dieser Pfad muss ein gültiger URI sein, damit das Assemblymanifest gültig ist. |
| `size` | Erforderlich, wenn das- `dependencyType` Attribut auf festgelegt ist `install` . Die Größe der abhängigen Assembly in Bytes. |

### <a name="assemblyidentity"></a>assemblyIdentity
 Erforderlich. Dieses Element ist ein untergeordnetes Element des `dependentAssembly` -Elements und weist folgende Attribute auf.

|attribute|Beschreibung|
|---------------|-----------------|
|`name`|Erforderlich. Identifiziert den Namen der Anwendung.|
|`version`|Erforderlich. Gibt die Versionsnummer der Anwendung im folgenden Format an: `major.minor.build.revision`|
|`publicKeyToken`|Optional. Gibt eine hexadezimale Zeichenfolge mit 16 Zeichen an, die die letzten 8 Bytes des `SHA-1` Hashwerts des öffentlichen Schlüssels darstellt, unter dem die Anwendung oder Assembly signiert ist. Der öffentliche Schlüssel, der zum Signieren des Katalogs verwendet wird, muss mindestens 2048 Bits aufweisen.|
|`processorArchitecture`|Optional. Gibt den Prozessor an. Gültige Werte sind `x86` 32-Bit-Windows und `I64` für 64-Bit-Windows.|
|`language`|Optional. Gibt die zwei teiligen Sprachcodes (z. b. en-US) der Assembly an.|

### <a name="hash"></a>hash
 Das- `hash` Element ist ein optionales untergeordnetes Element des- `assemblyIdentity` Elements. Das `hash` -Element weist keine Attribute auf.

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] verwendet einen algorithmischen Hash aller Dateien in einer Anwendung als Sicherheitsüberprüfung, um sicherzustellen, dass keine der Dateien nach der Bereitstellung geändert wurde. Wenn das `hash` Element nicht enthalten ist, wird diese Überprüfung nicht ausgeführt. Daher wird das Weglassen des- `hash` Elements nicht empfohlen.

### <a name="dsigtransforms"></a>dsig:Transforms
 Das- `dsig:Transforms` Element ist ein erforderliches untergeordnetes Element des- `hash` Elements. Das `dsig:Transforms` -Element weist keine Attribute auf.

### <a name="dsigtransform"></a>dsig:Transform
 Das- `dsig:Transform` Element ist ein erforderliches untergeordnetes Element des- `dsig:Transforms` Elements. Das `dsig:Transform` -Element weist folgende Attribute auf.

| attribute | Beschreibung |
|-------------| - |
| `Algorithm` | Der Algorithmus, der verwendet wird, um den Digest für diese Datei zu berechnen. Derzeit ist der einzige Wert, der von verwendet [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wird `urn:schemas-microsoft-com:HashTransforms.Identity` . |

### <a name="dsigdigestmethod"></a>dsig:DigestMethod
 Das- `dsig:DigestMethod` Element ist ein erforderliches untergeordnetes Element des- `hash` Elements. Das `dsig:DigestMethod` -Element weist folgende Attribute auf.

| attribute | Beschreibung |
|-------------| - |
| `Algorithm` | Der Algorithmus, der verwendet wird, um den Digest für diese Datei zu berechnen. Derzeit ist der einzige Wert, der von verwendet [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wird `http://www.w3.org/2000/09/xmldsig#sha1` . |

### <a name="dsigdigestvalue"></a>dsig:DigestValue
 Das- `dsig:DigestValue` Element ist ein erforderliches untergeordnetes Element des- `hash` Elements. Das `dsig:DigestValue` -Element weist keine Attribute auf. Der Textwert ist der berechnete Hash für die angegebene Datei.

## <a name="remarks"></a>Hinweise
 Alle von der Anwendung verwendeten Assemblys müssen über ein entsprechendes- `dependency` Element verfügen. Abhängige Assemblys enthalten keine Assemblys, die im globalen Assemblycache als Plattformassemblys vorinstalliert werden müssen.

## <a name="example"></a>Beispiel
 Das folgende Codebeispiel veranschaulicht `dependency` Elemente in einem [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungs Manifest. Dieses Codebeispiel ist Teil eines größeren Beispiels, das für das [ClickOnce-Anwendungs Manifest](../deployment/clickonce-application-manifest.md) -Thema bereitgestellt wird.

```xml
<dependency>
  <dependentOS>
    <osVersionInfo>
      <os
        majorVersion="4"
        minorVersion="10"
        buildNumber="0"
        servicePackMajor="0" />
    </osVersionInfo>
  </dependentOS>
</dependency>
<dependency>
  <dependentAssembly
    dependencyType="preRequisite"
    allowDelayedBinding="true">
    <assemblyIdentity
      name="Microsoft.Windows.CommonLanguageRuntime"
      version="4.0.20506.0" />
  </dependentAssembly>
</dependency>

<dependency>
  <dependentAssembly
    dependencyType="install"
    allowDelayedBinding="true"
    codebase="MyApplication.exe"
    size="4096">
    <assemblyIdentity
      name="MyApplication"
      version="1.0.0.0"
      language="neutral"
      processorArchitecture="x86" />
    <hash>
      <dsig:Transforms>
        <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />
      </dsig:Transforms>
      <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />
      <dsig:DigestValue>DpTW7RzS9IeT/RBSLj54vfTEzNg=</dsig:DigestValue>
    </hash>
  </dependentAssembly>
</dependency>
```

## <a name="see-also"></a>Siehe auch
- [ClickOnce-Anwendungs Manifest](../deployment/clickonce-application-manifest.md)
- [\<dependency> gewisses](../deployment/dependency-element-clickonce-deployment.md)