---
title: '&lt;file- &gt; Element (ClickOnce-Anwendung) | Microsoft-Dokumentation'
description: Das File-Element identifiziert alle nicht Assemblydateien, die von der Anwendung heruntergeladen und verwendet werden. Das File-Element ist optional.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://www.w3.org/2000/09/xmldsig#Transform
- urn:schemas-microsoft-com:asm.v2#file
- http://www.w3.org/2000/09/xmldsig#DigestValue
- http://www.w3.org/2000/09/xmldsig#DigestMethod
- http://www.w3.org/2000/09/xmldsig#Transforms
- urn:schemas-microsoft-com:asm.v2#hash
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <file> element [ClickOnce application manifest]
- manifests [ClickOnce], file element
ms.assetid: 56e3490c-eed5-4841-b1bf-eefe778b6ac9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9a4d09d4a0e141359b066f2af31c158f36c96522
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2020
ms.locfileid: "94382740"
---
# <a name="ltfilegt-element-clickonce-application"></a>&lt;file- &gt; Element (ClickOnce-Anwendung)
Identifiziert alle nicht Assemblydateien, die von der Anwendung heruntergeladen und verwendet werden.

## <a name="syntax"></a>Syntax

```xml
<file
    name
    size
    group
    optional
    writeableType
>
    <typelib
        tlbid
        version
        helpdir
        resourceid
        flags
    />
    <comClass
        clsid
        description
        threadingModel
        tlbid
        progid
        miscStatus
        miscStatusIcon
        miscStatusContent
        miscStatusDocPrint
        miscStatusThumbnail
    />
    <comInterfaceExternalProxyStub
        iid
        baseInterface
        numMethods
        name
        tlbid
        proxyStubClass32
    />
    <comInterfaceProxyStub
        iid
        baseInterface
        numMethods
        name
        tlbid
        proxyStubClass32
    />
    <windowClass
        versioned
    />
</file>
```

## <a name="elements-and-attributes"></a>Elemente und Attribute
 Das `file`-Element ist optional. Das Element weist folgende Attribute auf.

|attribute|Beschreibung|
|---------------|-----------------|
|`name`|Erforderlich. Gibt den Namen der Datei an.|
|`size`|Erforderlich. Gibt die Größe der Datei in Bytes an.|
|`group`|Optional, wenn das- `optional` Attribut nicht angegeben oder auf festgelegt ist `false` ; erforderlich, wenn `optional` ist `true` . Der Name der Gruppe, zu der diese Datei gehört. Der Name kann ein beliebiger Unicode-Zeichen folgen Wert sein, der vom Entwickler ausgewählt wird. er wird zum bedarfsgesteuerten herunterladen von Dateien mit der- <xref:System.Deployment.Application.ApplicationDeployment> Klasse verwendet.|
|`optional`|Optional. Gibt an, ob diese Datei beim ersten Ausführen der Anwendung heruntergeladen werden muss oder ob sich die Datei nur auf dem Server befinden soll, bis Sie von der Anwendung bei Bedarf angefordert wird. Wenn `false` oder nicht definiert, wird die Datei heruntergeladen, wenn die Anwendung zum ersten Mal ausgeführt oder installiert wird. Wenn `true` , `group` muss eine angegeben werden, damit das Anwendungs Manifest gültig ist. `optional` kann nicht "true" sein, wenn `writeableType` mit dem Wert angegeben wird `applicationData` .|
|`writeableType`|Optional. Gibt an, dass die Datei eine Datendatei ist. Derzeit ist `applicationData` der einzige gültige Wert.|

## <a name="typelib"></a>typelib
 Das- `typelib` Element ist ein optionales untergeordnetes Element des file-Elements. Das-Element beschreibt die Typbibliothek, die zur COM-Komponente gehört. Das Element weist folgende Attribute auf.

|attribute|Beschreibung|
|---------------|-----------------|
|`tlbid`|Erforderlich. Die der Typbibliothek zugewiesene GUID.|
|`version`|Erforderlich. Die Versionsnummer der Typbibliothek.|
|`helpdir`|Erforderlich. Das Verzeichnis, das die Hilfedateien für die Komponente enthält. Kann eine Länge von 0 (null) aufweisen.|
|`resourceid`|Optional. Die hexadezimale Zeichen folgen Darstellung des Gebiets Schema Bezeichners (Locale Identifier, LCID). Es handelt sich um eine bis vier hexadezimale Ziffern ohne ein 0x-Präfix und ohne führende Nullen. Die LCID weist möglicherweise einen neutralen unter Sprachen Bezeichner auf.|
|`flags`|Optional. Die Zeichen folgen Darstellung der Typbibliothekflags für diese Typbibliothek. Dabei sollte es sich um einen "eingeschränkten", "Control", "Hidden" und "HASDISKIMAGE" handeln.|

## <a name="comclass"></a>comClass
 Das- `comClass` Element ist ein optionales untergeordnetes Element des- `file` Elements. es ist jedoch erforderlich, wenn die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung eine COM-Komponente enthält, die für die Bereitstellung mithilfe des com-Registrierungs freien com Das Element weist folgende Attribute auf.

|attribute|Beschreibung|
|---------------|-----------------|
|`clsid`|Erforderlich. Die Klassen-ID der COM-Komponente, ausgedrückt als GUID.|
|`description`|Optional. Der Name der Klasse.|
|`threadingModel`|Optional. Das Threading Modell, das von in-Process-COM-Klassen verwendet wird. Wenn diese Eigenschaft NULL ist, wird kein Threading Modell verwendet. Die Komponente wird im Haupt Thread des Clients erstellt, und Aufrufe von anderen Threads werden an diesen Thread gemarshallt. In der folgenden Liste werden die gültigen Werte angezeigt:<br /><br /> `Apartment`, `Free`, `Both` und `Neutral`.|
|`tlbid`|Optional. GUID für die Typbibliothek für diese COM-Komponente.|
|`progid`|Optional. Versions abhängiger Programm Bezeichner, der der COM-Komponente zugeordnet ist. Das Format eines `ProgID` ist `<vendor>.<component>.<version>` .|
|`miscStatus`|Optional. Duplikate in der Assembly manifestieren die Informationen, die vom `MiscStatus` Registrierungsschlüssel bereitgestellt werden. Wenn keine Werte für das-,-,- `miscStatusIcon` `miscStatusContent` oder- `miscStatusDocprint` `miscStatusThumbnail` Attribut gefunden werden, wird der entsprechende Standardwert, der in aufgelistet `miscStatus` wird, für die fehlenden Attribute verwendet. Der Wert kann eine durch Trennzeichen getrennte Liste der Attributwerte aus der folgenden Tabelle sein. Sie können dieses Attribut verwenden, wenn die com-Klasse eine OCX-Klasse ist, die `MiscStatus` Registrierungsschlüssel Werte erfordert.|
|`miscStatusIcon`|Optional. Duplikate in der Assembly manifeden von DVASPECT_ICON bereitgestellten Informationen. Es kann ein Symbol eines Objekts bereitstellen. Der Wert kann eine durch Trennzeichen getrennte Liste der Attributwerte aus der folgenden Tabelle sein. Sie können dieses Attribut verwenden, wenn die com-Klasse eine OCX-Klasse ist, die `Miscstatus` Registrierungsschlüssel Werte erfordert.|
|`miscStatusContent`|Optional. Duplikate in der Assembly manifeden von DVASPECT_CONTENT bereitgestellten Informationen. Sie kann ein zusammengesetztes Dokument bereitstellen, das für einen Bildschirm oder Drucker angezeigt wird. Der Wert kann eine durch Trennzeichen getrennte Liste der Attributwerte aus der folgenden Tabelle sein. Sie können dieses Attribut verwenden, wenn die com-Klasse eine OCX-Klasse ist, die `MiscStatus` Registrierungsschlüssel Werte erfordert.|
|`miscStatusDocPrint`|Optional. Duplikate in der Assembly manifeden von DVASPECT_DOCPRINT bereitgestellten Informationen. Es kann eine Objektdarstellung bereitstellen, die auf dem Bildschirm angezeigt wird, als ob Sie auf einem Drucker gedruckt wird. Der Wert kann eine durch Trennzeichen getrennte Liste der Attributwerte aus der folgenden Tabelle sein. Sie können dieses Attribut verwenden, wenn die com-Klasse eine OCX-Klasse ist, die `MiscStatus` Registrierungsschlüssel Werte erfordert.|
|`miscStatusThumbnail`|Optional. Duplikate in einer Assembly manifeden von DVASPECT_THUMBNAIL bereitgestellten Informationen. Es kann eine Miniaturansicht eines Objekts bereitstellen, das in einem Browsertool angezeigt wird. Der Wert kann eine durch Trennzeichen getrennte Liste der Attributwerte aus der folgenden Tabelle sein. Sie können dieses Attribut verwenden, wenn die com-Klasse eine OCX-Klasse ist, die `MiscStatus` Registrierungsschlüssel Werte erfordert.|

## <a name="cominterfaceexternalproxystub"></a>comInterfaceExternalProxyStub
 Das- `comInterfaceExternalProxyStub` Element ist ein optionales untergeordnetes Element des- `file` Elements, kann jedoch erforderlich sein, wenn die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung eine COM-Komponente enthält, die für die Bereitstellung mithilfe von com registriert werden soll. Das-Element enthält die folgenden Attribute.

|attribute|Beschreibung|
|---------------|-----------------|
|`iid`|Erforderlich. Die Schnittstellen-ID (IID), die von diesem Proxy bereitgestellt wird. Die IID muss eine geschweifte Klammer aufweisen.|
|`baseInterface`|Optional. Die IID der Schnittstelle, von der die Schnittstelle abgeleitet wird, auf die von verwiesen `iid` wird.|
|`numMethods`|Optional. Die Anzahl der Methoden, die von der-Schnittstelle implementiert werden.|
|`name`|Optional. Der Name der Schnittstelle, wie er im Code angezeigt wird.|
|`tlbid`|Optional. Die Typbibliothek, die die Beschreibung der Schnittstelle enthält, die vom-Attribut angegeben wird `iid` .|
|`proxyStubClass32`|Optional. Ordnet eine IID einer CLSID in 32-Bit-Proxy-DLLs zu.|

## <a name="cominterfaceproxystub"></a>comInterfaceProxyStub
 Das- `comInterfaceProxyStub` Element ist ein optionales untergeordnetes Element des- `file` Elements, kann jedoch erforderlich sein, wenn die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung eine COM-Komponente enthält, die für die Bereitstellung mithilfe von com registriert werden soll. Das-Element enthält die folgenden Attribute.

|attribute|Beschreibung|
|---------------|-----------------|
|`iid`|Erforderlich. Die Schnittstellen-ID (IID), die von diesem Proxy bereitgestellt wird. Die IID muss eine geschweifte Klammer aufweisen.|
|`baseInterface`|Optional. Die IID der Schnittstelle, von der die Schnittstelle abgeleitet wird, auf die von verwiesen `iid` wird.|
|`numMethods`|Optional. Die Anzahl der Methoden, die von der-Schnittstelle implementiert werden.|
|`Name`|Optional. Der Name der Schnittstelle, wie er im Code angezeigt wird.|
|`Tlbid`|Optional. Die Typbibliothek, die die Beschreibung der Schnittstelle enthält, die vom-Attribut angegeben wird `iid` .|
|`proxyStubClass32`|Optional. Ordnet eine IID einer CLSID in 32-Bit-Proxy-DLLs zu.|
|`threadingModel`|Optional. Optional. Das Threading Modell, das von in-Process-COM-Klassen verwendet wird. Wenn diese Eigenschaft NULL ist, wird kein Threading Modell verwendet. Die Komponente wird im Haupt Thread des Clients erstellt, und Aufrufe von anderen Threads werden an diesen Thread gemarshallt. In der folgenden Liste werden die gültigen Werte angezeigt:<br /><br /> `Apartment`, `Free`, `Both` und `Neutral`.|

## <a name="windowclass"></a>windowClass
 Das- `windowClass` Element ist ein optionales untergeordnetes Element des- `file` Elements, kann jedoch erforderlich sein, wenn die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung eine COM-Komponente enthält, die für die Bereitstellung mithilfe von com registriert werden soll. Das-Element verweist auf eine von der COM-Komponente definierte Fenster Klasse, auf die eine Version angewendet werden muss. Das-Element enthält die folgenden Attribute.

|attribute|Beschreibung|
|---------------|-----------------|
|`versioned`|Optional. Steuert, ob der in der Registrierung verwendete interne Name der Fenster Klasse die Version der Assembly enthält, die die Fenster Klasse enthält. Der Wert dieses Attributs kann `yes` oder sein `no` . Der Standardwert ist `yes`. Der Wert `no` sollte nur verwendet werden, wenn die gleiche Fenster Klasse durch eine Seite-an-Seite-Komponente und eine äquivalente nicht parallele Komponente definiert ist und Sie diese als dieselbe Fenster Klasse behandeln möchten. Beachten Sie, dass die üblichen Regeln zur Fenster Klassen Registrierung zutreffen – nur die erste Komponente, die die Fenster Klasse registriert, kann Sie registrieren, da auf Sie keine Version angewendet wird.|

## <a name="hash"></a>hash
 Das- `hash` Element ist ein optionales untergeordnetes Element des- `file` Elements. Das `hash` -Element weist keine Attribute auf.

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] verwendet einen algorithmischen Hash aller Dateien in einer Anwendung als Sicherheitsüberprüfung, um sicherzustellen, dass keine der Dateien nach der Bereitstellung geändert wurde. Wenn das `hash` Element nicht enthalten ist, wird diese Überprüfung nicht ausgeführt. Daher wird das Weglassen des- `hash` Elements nicht empfohlen.

 Wenn ein Manifest eine Datei enthält, die nicht mit einem Hash versehen ist, kann dieses Manifest nicht digital signiert werden, da Benutzer den Inhalt einer Datei ohne Hash nicht überprüfen können.

## <a name="dsigtransforms"></a>dsig:Transforms
 Das- `dsig:Transforms` Element ist ein erforderliches untergeordnetes Element des- `hash` Elements. Das `dsig:Transforms` -Element weist keine Attribute auf.

## <a name="dsigtransform"></a>dsig:Transform
 Das- `dsig:Transform` Element ist ein erforderliches untergeordnetes Element des- `dsig:Transforms` Elements. Das `dsig:Transform` -Element weist folgende Attribute auf.

| attribute | Beschreibung |
|-------------| - |
| `Algorithm` | Der Algorithmus, der verwendet wird, um den Digest für diese Datei zu berechnen. Derzeit ist der einzige Wert, der von verwendet [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wird `urn:schemas-microsoft-com:HashTransforms.Identity` . |

## <a name="dsigdigestmethod"></a>dsig:DigestMethod
 Das- `dsig:DigestMethod` Element ist ein erforderliches untergeordnetes Element des- `hash` Elements. Das `dsig:DigestMethod` -Element weist folgende Attribute auf.

| attribute | Beschreibung |
|-------------| - |
| `Algorithm` | Der Algorithmus, der verwendet wird, um den Digest für diese Datei zu berechnen. Derzeit ist der einzige Wert, der von verwendet [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wird `http://www.w3.org/2000/09/xmldsig#sha1` . |

## <a name="dsigdigestvalue"></a>dsig:DigestValue
 Das- `dsig:DigestValue` Element ist ein erforderliches untergeordnetes Element des- `hash` Elements. Das `dsig:DigestValue` -Element weist keine Attribute auf. Der Textwert ist der berechnete Hash für die angegebene Datei.

## <a name="remarks"></a>Hinweise
 Dieses Element identifiziert alle nicht Assemblydateien, die die Anwendung bilden, insbesondere die Hashwerte für die Überprüfung der Datei. Dieses Element kann auch Component Object Model (com)-Isolations Daten enthalten, die der Datei zugeordnet sind. Wenn eine Datei geändert wird, muss die Datei des Anwendungs Manifests auch aktualisiert werden, um die Änderung widerzuspiegeln.

## <a name="example"></a>Beispiel
 Im folgenden Codebeispiel werden `file` Elemente in einem Anwendungs Manifest für eine mit bereitgestellte Anwendung veranschaulicht [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

```xml
<file name="Icon.ico" size="9216">
  <hash>
    <dsig:Transforms>
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />
    </dsig:Transforms>
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />
    <dsig:DigestValue>lVoj+Rh6RQ/HPNLOdayQah5McrI=</dsig:DigestValue>
  </hash>
</file>
```

## <a name="see-also"></a>Siehe auch
- [ClickOnce-Anwendungs Manifest](../deployment/clickonce-application-manifest.md)