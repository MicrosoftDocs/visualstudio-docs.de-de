---
title: Anwendungs Manifeste für Office-Lösungen
description: Erfahren Sie, wie ein Anwendungs Manifest eine XML-Datei ist, die die Assemblys beschreibt, die in eine Microsoft Office-Lösung geladen werden.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5a16d0f438d06cbfa48538bb3e370ed9b334ad16
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96847922"
---
# <a name="application-manifests-for-office-solutions"></a>Anwendungs Manifeste für Office-Lösungen
  Ein Anwendungsmanifest ist eine XML-Datei, die die Assemblys beschreibt, die in einer Microsoft Office-Projektmappe geladen werden. Die Microsoft Office Entwicklungs Tools in Visual Studio verwenden das [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] Schema des Anwendungs Manifests, das in der [ClickOnce-Anwendungs Manifest](../deployment/clickonce-application-manifest.md) -Referenz definiert ist.

 Anwendungsmanifeste für Office-Projektmappen verwenden die folgenden [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] -Elemente und -Attribute.

|Element|BESCHREIBUNG|Attributes|
|-------------|-----------------|----------------|
|[&#60;Assembly&#62; Element &#40;ClickOnce-Anwendung&#41;](../deployment/assembly-element-clickonce-deployment.md)|Erforderlich. Ein Element der obersten Ebene.|**manifestVersion**|
|[&#60;assemblyIdentity-&#62; Element &#40;ClickOnce-Anwendung&#41;](../deployment/assemblyidentity-element-clickonce-deployment.md)|Erforderlich. Gibt die primäre Assembly der [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] -Anwendung an.|**name**<br /><br /> **version**<br /><br /> **PublicKeyToken**<br /><br /> **ProcessorArchitecture**<br /><br /> **language**|
|[&#60;trustInfo-&#62; Element &#40;ClickOnce-Anwendung&#41;](../deployment/trustinfo-element-clickonce-application.md)|Gibt die Sicherheitsanforderungen der Anwendung an.|Keine|
|[&#60;EntryPoint&#62; Element &#40;ClickOnce-Anwendung&#41;](../deployment/entrypoint-element-clickonce-application.md)|Erforderlich. Gibt den Einstiegspunkt des Anwendungscodes für die Ausführung an.|**name**<br /><br /> **dependencyname**<br /><br /> **customHostSpecified**|
|[&#60;Abhängigkeits&#62; Element &#40;ClickOnce-Anwendung&#41;](../deployment/dependency-element-clickonce-deployment.md)|Erforderlich. Gibt jede Abhängigkeit an, die für die Ausführung der Anwendung erforderlich ist. Gibt optional Assemblys an, die vorinstalliert werden müssen.|Keine|
|[&#60;Datei&#62; Element &#40;ClickOnce-Anwendung&#41;](../deployment/file-element-clickonce-application.md)|Erforderlich. Gibt jede Nicht-Assemblydatei an, die von der Anwendung verwendet wird. Kann COM-Isolationsdaten (Component Object Model) enthalten, die der Datei zugeordnet sind.|**name**<br /><br /> **size**|

 Anwendungsmanifeste für Office-Projektmappen verwenden das folgenden Element im `co.v1` -Elemente.

```xml
<entryPoint>
    <co.v1:customHostSpecified />
</entryPoint>
```

 Diese Anwendungsmanifeste weisen auch die folgenden Elemente und Attribute im `vstav3` -Namespace auf.

```xml
<addIn>
  <entryPointsCollection>
    <entryPoints>
      <entryPoint>
      </entryPoint>
    </entryPoints>
  </entryPointsCollection>
  <update></update>
  <postActions>
    <postAction>
      <postActionData>
      </postActionData>
    <postAction>
  </postActions>
  <application>
    <customizations>
      <customization>
      </customization>
    </customizations>
  </application
</addIn>
```

|Element|BESCHREIBUNG|Attributes|
|-------------|-----------------|----------------|
|[&#60;customhostspezifiziertes&#62; Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/customhostspecified-element-office-development-in-visual-studio.md)|Erforderlich. Markiert das Manifest ausdrücklich als Office-Projektmappe.|Keine|
|[&#60;Add-&#62; Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/addin-element-office-development-in-visual-studio.md)|Erforderlich. Speichert Einstiegspunkte in einem einzelnen Namespace.|Keine|
|[&#60;entryPointsCollection&#62; Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/entrypointscollection-element-office-development-in-visual-studio.md)|Erforderlich. Gruppiert alle Assemblys für eine oder mehrere Office-Projektmappen.|**id**|
|[&#60;entryPoints&#62; Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md)|Erforderlich. Gruppiert alle Assemblys, die in einer Office-Projektmappe ausgeführt werden.|Keine|
|[&#60;EntryPoint&#62; Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/entrypoint-element-office-development-in-visual-studio.md)|Erforderlich. Gibt die Assemblys an, die in einer Office-Projektmappe ausgeführt werden.|**class**<br /><br /> **Bedingungen**|
|[&#60;aktualisieren Sie&#62; Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/update-element-office-development-in-visual-studio.md)|Erforderlich. Konfiguriert Updates für die Projektmappe.|**enabled**<br /><br /> **expiration**|
|[&#60;von postActions&#62; Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/postactions-element-office-development-in-visual-studio.md)|Dies ist optional. Gruppiert alle Aktionen nach der Bereitstellung, die nach der Installation von Office-Projektmappen ausgeführt werden.|Keine|
|[&#60;postAction-&#62; Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/postaction-element-office-development-in-visual-studio.md)|Dies ist optional. Gibt eine Aktion nach der Bereitstellung an.|Keine|
|[&#60;postaktiondata&#62;-Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/postactiondata-element-office-development-in-visual-studio.md)|Dies ist optional. Konfiguriert Daten für eine Aktion nach der Bereitstellung.|Keine|
|[&#60;Anwendungs&#62; Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/application-element-office-development-in-visual-studio.md)|Erforderlich. Umschließt die anwendungsspezifischen Informationen in einem einzelnen Knoten.|Keine|
|[&#60;Anpassungen&#62; Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/customizations-element-office-development-in-visual-studio.md)|Erforderlich. Speichert alle anwendungshostspezifischen Informationen in einem separaten Namespace.|Keine|
|[&#60;Anpassung&#62; Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/customization-element-office-development-in-visual-studio.md)|Erforderlich. Speichert anwendungshostspezifische Informationen in einem separaten Namespace.|**xmlns**|
|[&#60;Dokument&#62; Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/document-element-office-development-in-visual-studio.md)|Nur für Projektmappen auf Dokumentebene erforderlich. Speichert anpassungsspezifische Informationen.|**SolutionID**|
|[&#60;appAddin&#62; Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/appaddin-element-office-development-in-visual-studio.md)|Nur für Projektmappen auf Anwendungsebene erforderlich. Speichert anpassungsspezifische Informationen.|**application**<br /><br /> **LoadBehavior**<br /><br /> **keyName**|
|[&#60;FriendlyName&#62; Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/friendlyname-element-office-development-in-visual-studio.md)|Dies ist optional. Speichert den Namen des VSTO-Add-Ins, das in der Liste der installierten VSTO-Add-Ins angezeigt wird.|Keine|
|[&#60;Description&#62; Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/description-element-office-development-in-visual-studio.md)|Nur für VSTO-Add-Ins erforderlich. Speichert die Beschreibung, die in der Liste der installierten Programme angezeigt wird.|Keine|
|[&#60;FormRegions&#62; Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/formregions-element-office-development-in-visual-studio.md)|Nur für Outlook-VSTO-Add-Ins erforderlich, die Formularbereiche enthalten.|Keine|
|[&#60;FormRegion&#62; Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/formregion-element-office-development-in-visual-studio.md)|Nur für Outlook-VSTO-Add-Ins erforderlich, die Formularbereiche enthalten.|**Name**|
|[&#60;vstoRuntime-&#62; Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/vstoruntime-element-office-development-in-visual-studio.md)|Erforderlich. Beschreibt eine bestimmte Version der Visual Studio Tools for Office-Laufzeit, die von der Office-Projektmappe unterstützt wird.|**Abgabe**<br /><br /> **version**<br /><br /> **supportUrl**|

## <a name="remarks"></a>Bemerkungen
 Anwendungs- und Bereitstellungsmanifeste in Office-Projektmappen können manuell bearbeitet werden. Anschließend müssen Sie die Anwendungs-und Bereitstellungs Manifeste mithilfe der Manifest Generation and Editing Tool (*mage.exe* und *mageui.exe*) erneut signieren. Weitere Informationen finden Sie unter Gewusst [wie: Erneutes Signieren von Anwendungs-und Bereitstellungs Manifesten](../deployment/how-to-re-sign-application-and-deployment-manifests.md).

## <a name="file-location"></a>Dateispeicherort
 Ein Anwendungsmanifest ist für eine einzelne Version einer Projektmappe spezifisch. Aus diesem Grund müssen die Anwendungsmanifeste getrennt von Bereitstellungsmanifesten gespeichert werden. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] platziert die versionsspezifischen Dateien in einem Unterverzeichnis, das gemäß der zugewiesenen Version im Unterverzeichnis *Application Files* im Ordner „Publish“ benannt wird.

## <a name="file-name-syntax"></a>Dateinamenssyntax
 Der Name einer Anwendungs Manifest-Datei muss der vollständige Name und die Erweiterung der Anwendung sein, wie im **assemblyIdentity** -Element angegeben, gefolgt von der Erweiterung *. Manifest*. Beispielsweise würde ein Anwendungs Manifest, das auf die *OutlookAddIn1.dll* Anpassung verweist, die folgende Dateiname-Syntax verwenden.

 `OutlookAddIn1.dll.manifest`

## <a name="see-also"></a>Siehe auch

- [Bereitstellungs Manifeste für Office-Lösungen](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce-Anwendungs Manifest](../deployment/clickonce-application-manifest.md)