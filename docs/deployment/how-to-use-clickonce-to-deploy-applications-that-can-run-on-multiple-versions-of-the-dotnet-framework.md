---
title: Verwenden von ClickOnce zum Bereitstellen von apps mit mehreren Zielen
description: Erfahren Sie, wie Sie eine Anwendung, die mehrere Versionen der .NET Framework als Ziel verwendet, mithilfe der ClickOnce-Bereitstellungs Technologie bereitstellen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, multiple .NET Framework versions
- ClickOnce deployment, multiple .NET Framework versions
- deploying applications [ClickOnce], multiple .NET Framework versions
ms.assetid: e0a8c330-21bc-4eb2-b936-fd0f3c3221f1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: c87ed73d2c3a26ecc4522c6497ac71e33e46a6c3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889121"
---
# <a name="how-to-use-clickonce-to-deploy-applications-that-can-run-on-multiple-versions-of-the-net-framework"></a>Vorgehensweise: Verwenden von ClickOnce zum Bereitstellen von Anwendungen, die unter mehreren Versionen von .NET Framework ausgeführt werden können
Mithilfe der ClickOnce-Bereitstellungs Technologie können Sie eine Anwendung bereitstellen, die mehrere Versionen der .NET Framework als Ziel hat. Dies erfordert, dass Sie die Anwendungs-und Bereitstellungs Manifeste generieren und aktualisieren.

> [!NOTE]
> Bevor Sie die Anwendung so ändern, dass Sie mehrere Versionen des .NET Framework als Ziel hat, sollten Sie sicherstellen, dass die Anwendung mit mehreren Versionen des .NET Framework ausgeführt wird. Die Version Common Language Runtime unterscheidet sich zwischen .NET Framework 4 und .NET Framework 2,0, .NET Framework 3,0 und .NET Framework 3,5.

 Für diesen Vorgang sind die folgenden Schritte erforderlich:

1. Generieren Sie die Anwendungs-und Bereitstellungs Manifeste.

2. Ändern Sie das Bereitstellungs Manifest, um die verschiedenen .NET Framework Versionen aufzulisten.

3. Ändern Sie die *app.config* Datei, um die kompatiblen .NET Framework Lauf Zeit Versionen aufzulisten.

4. Ändern Sie das Anwendungs Manifest, um abhängige Assemblys als .NET Framework Assemblys zu markieren

5. Signieren Sie das Anwendungs Manifest.

6. Aktualisieren und Signieren Sie das Bereitstellungs Manifest.

### <a name="to-generate-the-application-and-deployment-manifests"></a>So generieren Sie die Anwendungs-und Bereitstellungs Manifeste

- Verwenden Sie den Veröffentlichungs-Assistenten oder die Seite Veröffentlichen des Projekt-Designers, um die Anwendung zu veröffentlichen und die Dateien für die Anwendung und das Bereitstellungs Manifest zu generieren. Weitere Informationen finden Sie unter Gewusst [wie: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten oder der](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md) Seite "veröffentlichen" [, Projekt-Designer](../ide/reference/publish-page-project-designer.md).

### <a name="to-change-the-deployment-manifest-to-list-the-multiple-net-framework-versions"></a>So ändern Sie das Bereitstellungs Manifest, um die mehrere .NET Framework Versionen aufzulisten

1. Öffnen Sie im Verzeichnis veröffentlichen das Bereitstellungs Manifest, indem Sie den XML-Editor in Visual Studio verwenden. Das Bereitstellungs Manifest verfügt über die Dateinamenerweiterung *. Application* .

2. Ersetzen Sie den XML-Code zwischen dem `<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">` -Element und dem- `</compatibleFrameworks>` Element durch XML, das die unterstützten .NET Framework Versionen für Ihre Anwendung auflistet

     In der folgenden Tabelle werden einige der verfügbaren .NET Framework Versionen und der entsprechende XML-Code angezeigt, den Sie dem Bereitstellungs Manifest hinzufügen können.

    |.NET Framework-Version|XML|
    |----------------------------|---------|
    |4 Client|\<framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />|
    |4 Full|\<framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />|
    |3.5 Client|\<framework targetVersion="3.5" profile="Client" supportedRuntime="2.0.50727" />|
    |3.5 Full|\<framework targetVersion="3.5" profile="Full" supportedRuntime="2.0.50727" />|
    |3.0|\<framework targetVersion="3.0" supportedRuntime="2.0.50727" />|

### <a name="to-change-the-appconfig-file-to-list-the-compatible-net-framework-runtime-versions"></a>So ändern Sie die app.config Datei, um die kompatiblen .NET Framework Runtime-Versionen aufzulisten

1. Öffnen Sie in Projektmappen-Explorer die *app.config* Datei mit dem XML-Editor in Visual Studio.

2. Ersetzen (oder fügen) Sie den XML-Code zwischen dem `<startup>` -Element und dem- `</startup>` Element durch XML, das die unterstützten .NET Framework Laufzeiten für die Anwendung auflistet.

     In der folgenden Tabelle werden einige der verfügbaren .NET Framework Versionen und der entsprechende XML-Code angezeigt, den Sie dem Bereitstellungs Manifest hinzufügen können.

    |Laufzeitversion .NET Framework|XML|
    |------------------------------------|---------|
    |4 Client|\<supportedRuntime version="v4.0.30319" sku=".NETFramework,Version=v4.0,Profile=Client" />|
    |4 Full|\<supportedRuntime version="v4.0.30319" sku=".NETFramework,Version=v4.0" />|
    |3.5 Full|\<supportedRuntime version="v2.0.50727"/>|
    |3.5 Client|\<supportedRuntime version="v2.0.50727" sku="Client"/>|

### <a name="to-change-the-application-manifest-to-mark-dependent-assemblies-as-net-framework-assemblies"></a>So ändern Sie das Anwendungs Manifest, um abhängige Assemblys als .NET Framework Assemblys

1. Öffnen Sie im Verzeichnis veröffentlichen das Anwendungs Manifest, indem Sie den XML-Editor in Visual Studio verwenden. Das Bereitstellungs Manifest verfügt über die Dateinamenerweiterung " *. Manifest* ".

2. Fügen Sie `group="framework"` den Abhängigkeits-XML-Code für die sentinassemblys hinzu ( `System.Core` , `WindowsBase` , `Sentinel.v3.5Client` und `System.Data.Entity` ). Der XML-Code sollte beispielsweise wie folgt aussehen:

   ```xml
   <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" group="framework">
   ```

3. Aktualisieren Sie die Versionsnummer des- `<assemblyIdentity>` Elements für Microsoft. Windows. CommonLanguageRuntime auf die Versionsnummer für die .NET Framework, die den kleinsten gemeinsamen Nenner ist. Wenn die Anwendung beispielsweise .NET Framework 3,5 und .NET Framework 4 als Ziel verwendet, verwenden Sie die Versionsnummer 2.0.50727.0, und die XML sollte wie folgt aussehen:

   ```xml
   <dependency>
     <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">
       <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50727.0" />
     </dependentAssembly>
   </dependency>
   ```

### <a name="to-update-and-re-sign-the-application-and-deployment-manifests"></a>So können Sie die Anwendungs-und Bereitstellungs Manifeste aktualisieren und erneut signieren

- Aktualisieren und Signieren Sie die Anwendungs-und Bereitstellungs Manifeste. Weitere Informationen finden Sie unter Gewusst [wie: Erneutes Signieren von Anwendungs-und Bereitstellungs Manifesten](../deployment/how-to-re-sign-application-and-deployment-manifests.md).

## <a name="see-also"></a>Weitere Informationen
- [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)
- [\<compatibleFrameworks>-Element](../deployment/compatibleframeworks-element-clickonce-deployment.md)
- [\<dependency>-Element](../deployment/dependency-element-clickonce-application.md)
- [ClickOnce-Bereitstellungs Manifest](../deployment/clickonce-deployment-manifest.md)
- [Konfigurationsdateischema](/dotnet/framework/configure-apps/file-schema/index)
