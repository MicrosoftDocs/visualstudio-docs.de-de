---
title: Support-URL für erforderliche Komponenten in der ClickOnce
description: Erfahren Sie, wie eine ClickOnce-Bereitstellung die Voraussetzungen für die Anwendung der ClickOnce-Anwendung prüft und wie die Bereitstellung fehlende Voraussetzungen erfüllt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, prerequisites
- ClickOnce deployment, URLs
ms.assetid: 590742c3-a286-4160-aa75-7a441bb2207b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 585ea1a558b91ac733670ad94a9a3e0be33f1348
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876315"
---
# <a name="how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment"></a>Vorgehensweise: Angeben einer Support-URL für einzelne erforderliche Komponenten in einer ClickOnce-Bereitstellung
Eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellung kann eine Reihe von Voraussetzungen testen, die auf dem Client Computer verfügbar sein müssen, damit die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung ausgeführt werden kann. Zu diesen Abhängigkeiten gehören die erforderliche Mindestversion des .NET Framework, die Version des Betriebssystems und alle Assemblys, die im globalen Assemblycache (Global Assembly Cache, GAC) vorinstalliert werden müssen. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]kann jedoch keine dieser erforderlichen Komponenten installieren. Wenn eine Voraussetzung nicht gefunden wird, wird die Installation einfach angehalten, und es wird ein Dialogfeld angezeigt, in dem die Gründe für die Installation

 Es gibt zwei Methoden zum Installieren der erforderlichen Komponenten. Sie können Sie mit einer Boots Trapper-Anwendung installieren. Alternativ können Sie eine Support-URL für einzelne erforderliche Komponenten angeben, die Benutzern im Dialogfeld angezeigt wird, wenn die Voraussetzungen nicht gefunden werden. Die Seite, auf die diese URL verweist, kann Links zu Anweisungen für die Installation der erforderlichen Voraussetzungen enthalten. Wenn eine Anwendung keine Unterstützungs-URL für eine einzelne Voraussetzung angibt, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] zeigt die im Bereitstellungs Manifest für die Anwendung als Ganzes angegebene Support-URL an, sofern diese definiert ist.

 Obwohl [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , *Mage.exe* und *MageUI.exe* zum Generieren von bereit Stellungen verwendet werden können [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , unterstützt keines dieser Tools direkt die Angabe einer Support-URL für die einzelnen Voraussetzungen. In diesem Dokument wird beschrieben, wie Sie das Anwendungs Manifest und das Bereitstellungs Manifest für die Bereitstellung so ändern, dass diese unterstützten URLs

### <a name="specify-a-support-url-for-an-individual-prerequisite"></a>Geben Sie eine Support-URL für eine einzelne Voraussetzung an

1. Öffnen Sie das Anwendungs Manifest (die *Manifest* -Datei) für die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung in einem Text-Editor.

2. Fügen Sie das-Attribut für eine erforderliche Betriebssystem `supportUrl` Komponente dem- `dependentOS` Element hinzu:

   ```xml
    <dependency>
       <dependentOS supportUrl="http://www.adatum.com/MyApplication/wrongOSFound.htm">
         <osVersionInfo>
           <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" servicePackMinor="0" />
         </osVersionInfo>
       </dependentOS>
     </dependency>
   ```

3. Um eine Voraussetzung für eine bestimmte Version des Common Language Runtime zu erhalten, fügen Sie das-Attribut dem-Eintrag hinzu, der `supportUrl` `dependentAssembly` die Common Language Runtime Abhängigkeit angibt:

   ```xml
     <dependency>
       <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/wrongClrVersionFound.htm">
         <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.30319.0" />
       </dependentAssembly>
     </dependency>
   ```

4. Um eine Voraussetzung für eine Assembly zu erhalten, die im globalen Assemblycache vorinstalliert werden muss, legen Sie `supportUrl` für das-Element fest, `dependentAssembly` das die erforderliche Assembly angibt:

   ```xml
     <dependency>
       <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/missingSampleGACAssembly.htm">
         <assemblyIdentity name="SampleGACAssembly" version="5.0.0.0" publicKeyToken="04529dfb5da245c5" processorArchitecture="msil" language="neutral" />
       </dependentAssembly>
     </dependency>
   ```

5. Dies ist optional. Öffnen Sie für Anwendungen, die auf die .NET Framework 4 abzielen, das Bereitstellungs Manifest (die *Anwendungs* Datei) für die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung in einem Text-Editor.

6. Fügen Sie für eine .NET Framework 4-Voraussetzung das-Attribut dem- `supportUrl` `compatibleFrameworks` Element hinzu:

   ```xml
   <compatibleFrameworks  xmlns="urn:schemas-microsoft-com:clickonce.v2" supportUrl="http://adatum.com/MyApplication/CompatibleFrameworks.htm">
     <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />
     <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />
   </compatibleFrameworks>
   ```

7. Nachdem Sie das Anwendungs Manifest manuell geändert haben, müssen Sie das Anwendungs Manifest mit Ihrem digitalen Zertifikat erneut signieren und dann das Bereitstellungs Manifest aktualisieren und erneut signieren. Verwenden Sie die *Mage.exe* -oder *MageUI.exe* SDK-Tools, um diese Aufgabe zu erledigen, wenn Sie diese Dateien mithilfe von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] löscht ihre manuellen Änderungen. Weitere Informationen zum Verwenden von Mage.exe zum erneuten Signieren von Manifesten finden Sie unter Gewusst [wie: Erneutes Signieren von Anwendungs-und Bereitstellungs Manifesten](../deployment/how-to-re-sign-application-and-deployment-manifests.md).

## <a name="net-framework-security"></a>.NET Framework-Sicherheit
 Die Support-URL wird im Dialogfeld nicht angezeigt, wenn die Anwendung für die Ausführung mit teilweiser Vertrauenswürdigkeit markiert ist.

## <a name="see-also"></a>Weitere Informationen
- [Mage.exe (Tool zum Generieren und Bearbeiten von Manifesten)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [Exemplarische Vorgehensweise: Manuelles Bereitstellen einer ClickOnce-Anwendung](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
- [\<compatibleFrameworks>-Element](../deployment/compatibleframeworks-element-clickonce-deployment.md)
- [ClickOnce und Authenticode](../deployment/clickonce-and-authenticode.md)
- [Vorbedingungen für die Anwendungsbereitstellung](../deployment/application-deployment-prerequisites.md)