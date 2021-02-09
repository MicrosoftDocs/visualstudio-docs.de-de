---
title: '&lt;EntryPoint- &gt; Element (ClickOnce-Anwendung) | Microsoft-Dokumentation'
description: Das entryPoint-Element identifiziert die Assembly, die ausgeführt werden soll, wenn diese ClickOnce-Anwendung auf einem Client Computer ausgeführt wird.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#commandLine
- urn:schemas-microsoft-com:asm.v2#entryPoint
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <entryPoint> element [ClickOnce application manifest]
- manifests [ClickOnce], entryPoint element
ms.assetid: 10ad3083-10c1-4189-a870-9bba2eab244f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d5c35d94001ae1e883e2bd76650f248d7e0364d2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893892"
---
# <a name="ltentrypointgt-element-clickonce-application"></a>&lt;EntryPoint- &gt; Element (ClickOnce-Anwendung)
Identifiziert die Assembly, die ausgeführt werden soll, wenn diese [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung auf einem Client Computer ausgeführt wird.

## <a name="syntax"></a>Syntax

```xml
<entryPoint
   name
>
   <assemblyIdentity
      name
      version
      processorArchitecture
      language
   />
   <commandLine
      file
      parameters
   />
   <customHostRequired />
   <customUX />
</entryPoint>
```

## <a name="elements-and-attributes"></a>Elemente und Attribute
 Das `entryPoint` -Element ist erforderlich und befindet sich im `urn:schemas-microsoft-com:asm.v2` -Namespace. Es darf nur ein- `entryPoint` Element in einem Anwendungs Manifest definiert sein.

 Das `entryPoint` -Element hat das folgende Attribut.

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|`name`|Dies ist optional. Dieser Wert wird von .NET Framework nicht verwendet.|

 `entryPoint` hat die folgenden Elemente:

## <a name="assemblyidentity"></a>assemblyIdentity
 Erforderlich. Die-Rolle `assemblyIdentity` und die zugehörigen Attribute werden im- [ \<assemblyIdentity> Element](../deployment/assemblyidentity-element-clickonce-application.md)definiert.

 Das `processorArchitecture` -Attribut dieses Elements und des- `processorArchitecture` Attributs, das in `assemblyIdentity` an anderer Stelle im Anwendungs Manifest definiert ist, müssen mit identisch sein.

## <a name="commandline"></a>commandLine
 Erforderlich. Muss ein untergeordnetes Element des- `entryPoint` Elements sein. Sie verfügt über keine untergeordneten Elemente und verfügt über die folgenden Attribute.

| attribute | Beschreibung |
|--------------| - |
| `file` | Erforderlich. Ein lokaler Verweis auf die Startassembly für die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung. Dieser Wert darf keinen Schrägstrich (/) oder umgekehrter Schrägstrich ( \\ ) Pfad Trennzeichen enthalten. |
| `parameters` | Erforderlich. Beschreibt die Aktion, die mit dem Einstiegspunkt ausgeführt werden soll. Der einzige gültige Wert ist `run` . Wenn eine leere Zeichenfolge angegeben wird, `run` wird angenommen. |

## <a name="customhostrequired"></a>customHostRequired
 Dies ist optional. Gibt an, dass diese Bereitstellung eine Komponente enthält, die in einem benutzerdefinierten Host bereitgestellt wird und keine eigenständige Anwendung ist.

 Wenn dieses Element vorhanden ist, `assemblyIdentity` dürfen das-Element und das-Element `commandLine` nicht auch vorhanden sein. Wenn dies der Fall ist, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wird während der Installation ein Validierungs Fehler ausgegeben.

 Dieses Element hat keine Attribute und keine untergeordneten Elemente.

## <a name="customux"></a>customUX
 Dies ist optional. Gibt an, dass die Anwendung von einem benutzerdefinierten Installer installiert und verwaltet wird, und erstellt keinen Startmenü-Eintrag, keine Verknüpfung oder Software Eintrag.

```xml
<customUX xmlns="urn:schemas-microsoft-com:clickonce.v1" />
```

 Eine Anwendung, die das customUX-Element enthält, muss ein benutzerdefiniertes Installationsprogramm bereitstellen, das mithilfe der- <xref:System.Deployment.Application.InPlaceHostingManager> Klasse installations Vorgänge ausführt. Eine Anwendung mit diesem Element kann nicht durch Doppelklicken auf das zugehörige Manifest oder setup.exe erforderliche Boots Trapper installiert werden. Mit dem benutzerdefinierten Installationsprogramm können Einträge im Startmenü, Verknüpfungen und Software Einträge erstellt werden. Wenn das benutzerdefinierte Installationsprogramm den Eintrag "Software" nicht erstellt, muss er den von der-Eigenschaft bereitgestellten Abonnement Bezeichner speichern <xref:System.Deployment.Application.GetManifestCompletedEventArgs.SubscriptionIdentity%2A> und dem Benutzer die Möglichkeit geben, die Anwendung später durch Aufrufen der-Methode zu deinstallieren <xref:System.Deployment.Application.InPlaceHostingManager.UninstallCustomUXApplication%2A> . Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Erstellen eines benutzerdefinierten Installers für eine ClickOnce-Anwendung](../deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application.md).

## <a name="remarks"></a>Bemerkungen
 Dieses Element identifiziert die Assembly und den Einstiegspunkt für die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung.

 Sie können nicht verwenden `commandLine` , um zur Laufzeit Parameter an Ihre Anwendung zu übergeben. Sie können auf Abfrage Zeichenfolgen-Parameter für eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellung über die der Anwendung zugreifen <xref:System.AppDomain> . Weitere Informationen finden Sie unter Gewusst [wie: Abrufen von Abfrage Zeichenfolgen-Informationen in einer Online-ClickOnce-Anwendung](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).

## <a name="example"></a>Beispiel
 Das folgende Codebeispiel veranschaulicht ein- `entryPoint` Element in einem Anwendungs Manifest für eine- [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung. Dieses Codebeispiel ist Teil eines größeren Beispiels, das für das [ClickOnce-Anwendungs Manifest](../deployment/clickonce-application-manifest.md) -Thema bereitgestellt wird.

```xml
<!-- Identify the main code entrypoint. -->
<!-- This code runs the main method in an executable assembly. -->
  <entryPoint>
    <assemblyIdentity
      name="MyApplication"
      version="1.0.0.0"
      language="neutral"
      processorArchitecture="x86" />
    <commandLine file="MyApplication.exe" parameters="" />
  </entryPoint>
```

## <a name="see-also"></a>Weitere Informationen
- [ClickOnce-Anwendungs Manifest](../deployment/clickonce-application-manifest.md)
