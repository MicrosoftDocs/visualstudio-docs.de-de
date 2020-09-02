---
title: '&lt;Abhängigkeits &gt; Element (ClickOnce-Bereitstellung) | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
- <dependency> element [ClickOnce deployment manifest]
ms.assetid: 9b4d2082-0347-4922-ac70-85f11b913039
caps.latest.revision: 29
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f191b11dfce5b3877d0a31e260e092000a556a5a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187780"
---
# <a name="ltdependencygt-element-clickonce-deployment"></a>&lt;Abhängigkeits &gt; Element (ClickOnce-Bereitstellung)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identifiziert die Version der zu installierenden Anwendung und den Speicherort des Anwendungs Manifests.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
      <dependency>   
   <dependentAssembly  
      preRequisite  
      visible  
      dependencyType  
      codeBase  
      size  
   >   
      <assemblyIdentity   
         name   
         version   
         publicKeyToken   
         processorArchitecture   
         language  
         type  
      />   
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
  
   </dependentAssembly>   
</dependency>  
```  
  
## <a name="elements-and-attributes"></a>Elemente und Attribute  
 Das `dependency`-Element ist erforderlich. Sie besitzt keine Attribute. Ein Bereitstellungs Manifest kann mehrere `dependency` Elemente aufweisen.  
  
 Das- `dependency` Element drückt normalerweise Abhängigkeiten für die Hauptanwendung auf Assemblys aus, die in einer- [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung enthalten Wenn die Main.exe-Anwendung eine Assembly mit dem Namen DotNetAssembly.dll verwendet, muss diese Assembly in einem Abhängigkeits Abschnitt aufgeführt werden. Die Abhängigkeit kann jedoch auch andere Typen von Abhängigkeiten (z. b. Abhängigkeiten von einer bestimmten Version der Common Language Runtime, für eine Assembly im globalen Assemblycache (GAC) oder für ein COM-Objekt Ausdrücken. Da es sich um eine nicht Berührungs fähige Bereitstellungs Technologie handelt, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] kann den Download und die Installation dieser Abhängigkeits Typen nicht initiieren, aber es wird verhindert, dass die Anwendung ausgeführt wird, wenn mindestens eine der angegebenen Abhängigkeiten nicht vorhanden ist.  
  
## <a name="dependentassembly"></a>dependentAssembly  
 Erforderlich. Dieses Element enthält das- `assemblyIdentity` Element. In der folgenden Tabelle werden die von `dependentAssembly` unterstützten Attribute angezeigt.  
  
|attribute|Beschreibung|  
|---------------|-----------------|  
|`preRequisite`|Optional. Gibt an, dass diese Assembly bereits im GAC vorhanden sein soll. Gültige Werte sind `true` und `false`. Wenn `true` , und die angegebene Assembly nicht im GAC vorhanden ist, kann die Anwendung nicht ausgeführt werden.|  
|`visible`|Optional. Identifiziert die Anwendungs Identität der obersten Ebene, einschließlich ihrer Abhängigkeiten. Wird intern von [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] zum Verwalten des Anwendungs Speichers und der Aktivierung verwendet.|  
|`dependencyType`|Erforderlich. Die Beziehung zwischen dieser Abhängigkeit und der Anwendung. Gültige Werte sind:<br /><br /> -   `install`. Die Komponente stellt eine separate Installation aus der aktuellen Anwendung dar.<br />-   `preRequisite`. Die Komponente ist für die aktuelle Anwendung erforderlich.|  
|`codebase`|Optional. Der vollständige Pfad zum Anwendungs Manifest.|  
|`size`|Optional. Die Größe des Anwendungs Manifests (in Bytes).|  
  
## <a name="assemblyidentity"></a>assemblyIdentity  
 Erforderlich. Dieses Element ist ein untergeordnetes Element des `dependentAssembly` -Elements. Der Inhalt von `assemblyIdentity` muss mit dem im Anwendungs Manifest beschriebenen identisch sein [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . In der folgenden Tabelle werden die Attribute des- `assemblyIdentity` Elements angezeigt.  
  
|attribute|Beschreibung|  
|---------------|-----------------|  
|`Name`|Erforderlich. Identifiziert den Namen der Anwendung.|  
|`Version`|Erforderlich. Gibt die Versionsnummer der Anwendung im folgenden Format an: `major.minor.build.revision`|  
|`publicKeyToken`|Erforderlich. Gibt eine hexadezimale Zeichenfolge mit 16 Zeichen an, die die letzten 8 Bytes des SHA-1-Hashs des öffentlichen Schlüssels darstellt, unter dem die Anwendung oder Assembly signiert ist. Der öffentliche Schlüssel, der zum Signieren verwendet wird, muss 2048 Bit oder größer sein.|  
|`processorArchitecture`|Erforderlich. Gibt den Mikroprozessor an. Gültige Werte sind `x86` 32-Bit-Windows und `IA64` für 64-Bit-Windows.|  
|`Language`|Optional. Gibt die zwei teiligen Sprachcodes der Assembly an. Beispielsweise en-US, die für Englisch (USA) steht. Der Standardwert lautet `neutral`. Dieses Element befindet sich im- `asmv2` Namespace.|  
|`type`|Optional. Aus Gründen der Abwärtskompatibilität mit der parallelen Installation von Windows. Der einzige zulässige Wert ist `win32` .|  
  
## <a name="hash"></a>hash  
 Das- `hash` Element ist ein optionales untergeordnetes Element des- `file` Elements. Das `hash` -Element weist keine Attribute auf.  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] verwendet einen algorithmischen Hash aller Dateien in einer Anwendung als Sicherheitsüberprüfung, um sicherzustellen, dass keine der Dateien nach der Bereitstellung geändert wurde. Wenn das `hash` Element nicht enthalten ist, wird diese Überprüfung nicht ausgeführt. Daher wird das Weglassen des- `hash` Elements nicht empfohlen.  
  
## <a name="dsigtransforms"></a>dsig:Transforms  
 Das- `dsig:Transforms` Element ist ein erforderliches untergeordnetes Element des- `hash` Elements. Das `dsig:Transforms` -Element weist keine Attribute auf.  
  
## <a name="dsigtransform"></a>dsig:Transform  
 Das- `dsig:Transform` Element ist ein erforderliches untergeordnetes Element des- `dsig:Transforms` Elements. In der folgenden Tabelle werden die Attribute des- `dsig:Transform` Elements angezeigt.  
  
|attribute|Beschreibung|  
|---------------|-----------------|  
|`Algorithm`|Der Algorithmus, der verwendet wird, um den Digest für diese Datei zu berechnen. Derzeit ist der einzige Wert, der von verwendet [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] wird `urn:schemas-microsoft-com:HashTransforms.Identity` .|  
  
## <a name="dsigdigestmethod"></a>dsig:DigestMethod  
 Das- `dsig:DigestMethod` Element ist ein erforderliches untergeordnetes Element des- `hash` Elements. In der folgenden Tabelle werden die Attribute des- `dsig:DigestMethod` Elements angezeigt.  
  
|attribute|Beschreibung|  
|---------------|-----------------|  
|`Algorithm`|Der Algorithmus, der verwendet wird, um den Digest für diese Datei zu berechnen. Derzeit ist der einzige Wert, der von verwendet [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] wird `http://www.w3.org/2000/09/xmldsig#sha1` .|  
  
## <a name="dsigdigestvalue"></a>dsig:DigestValue  
 Das- `dsig:DigestValue` Element ist ein erforderliches untergeordnetes Element des- `hash` Elements. Das `dsig:DigestValue` -Element weist keine Attribute auf. Der Textwert ist der berechnete Hash für die angegebene Datei.  
  
## <a name="remarks"></a>Bemerkungen  
 Bereitstellungs Manifeste verfügen in der Regel über ein einzelnes- `assemblyIdentity` Element, das den Namen und die Version des Anwendungs Manifests identifiziert.  
  
## <a name="example"></a>Beispiel  
 Das folgende Codebeispiel zeigt ein- `dependency` Element in einem [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Bereitstellungs Manifest.  
  
```  
<!-- Identify the assembly dependencies -->  
<dependency>  
  <dependentAssembly dependencyType="install" allowDelayedBinding="true" codebase="MyApplication.exe" size="16384">  
    <assemblyIdentity name="MyApplication" version="0.0.0.0" cultural="neutral" processorArchitecture="msil" />  
    <hash>  
      <dsig:Transforms>  
        <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
      </dsig:Transforms>  
      <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
       <dsig:DigestValue>YzXYZJAvj9pgAG3y8jXUjC7AtHg=</dsig:DigestValue>  
    </hash>  
  </dependentAssembly>  
</dependency>  
```  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird eine Abhängigkeit von einer Assembly angegeben, die bereits im GAC installiert ist.  
  
```  
<dependency>  
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
    <assemblyIdentity name="GACAssembly" version="1.0.0.0" language="neutral" processorArchitecture="msil" />  
  </dependentAssembly>  
</dependency>  
```  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird eine Abhängigkeit von einer bestimmten Version des Common Language Runtime angegeben.  
  
```  
<dependency>  
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
    <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50215.0" />  
  </dependentAssembly>  
</dependency>  
```  
  
## <a name="example"></a>Beispiel  
 Das folgende Codebeispiel gibt eine Betriebssystem Abhängigkeit an.  
  
```  
<dependency>  
   <dependentOS supportUrl="http://www.microsoft.com" description="Microsoft Windows Operating System">  
      <osVersionInfo>  
         <os majorVersion="4" minorVersion="10" />  
      </osVersionInfo>  
   </dependentOS>  
</dependency>  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [ClickOnce-Bereitstellungs Manifest](../deployment/clickonce-deployment-manifest.md)   
 [\<dependency>-Element](../deployment/dependency-element-clickonce-application.md)
