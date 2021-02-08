---
title: Voraussetzungen der Anwendungs Bereitstellung | Microsoft-Dokumentation
description: Informieren Sie sich über die Voraussetzungen für die Bereitstellung Ihrer Anwendungen, einschließlich der Verwendung des Dialog Felds erforderliche Komponenten und Bootstrapperpakete.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, platform detection
- ClickOnce deployment, prerequisites
- ClickOnce deployment, dependencies
- prerequisites, ClickOnce
- dependencies, ClickOnce
ms.assetid: fc6e047e-ad94-44e8-8ff5-b6d1f4ca7735
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fe8312a4dcaa2efb0b783e89540e5ff9f71f15e6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837800"
---
# <a name="application-deployment-prerequisites"></a>Vorbedingungen für die Anwendungsbereitstellung

Damit die Anwendung erfolgreich installiert und ausgeführt werden kann, müssen Sie zunächst alle Komponenten installieren, von denen die Anwendung auf den Zielcomputer angewiesen ist. Beispielsweise weisen die meisten mit erstellten Anwendungen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] eine Abhängigkeit von der .NET Framework auf. In diesem Fall muss die richtige Version der Common Language Runtime auf dem Zielcomputer vorhanden sein, bevor die Anwendung installiert wird.

 Sie können diese erforderlichen Komponenten im **Dialog Feld** erforderliche Komponenten auswählen und die .NET Framework und alle anderen verteilbaren Komponenten als Teil der-Installation installieren. Dieses Vorgehen wird als *Bootstrapping* bezeichnet. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] generiert ein ausführbares Windows-Programm mit dem Namen *Setup.exe*, das auch als *Boots Trapper* bezeichnet wird. Der Bootstrapper installiert diese erforderlichen Komponenten, bevor die Anwendung ausgeführt wird. Weitere Informationen zum Auswählen dieser Voraussetzungen finden Sie unter [Voraussetzungen (Dialogfeld](../ide/reference/prerequisites-dialog-box.md)).

 Jede erforderliche Komponente ist ein Bootstrapperpaket. Ein Bootstrapperpaket ist eine Gruppe von Verzeichnissen und Dateien, die die Manifestressourcen enthalten, die beschreiben, wie die erforderlichen Komponenten installiert werden. Wenn die erforderlichen Komponenten für die Anwendung nicht im Dialogfeld **Erforderliche Komponenten** aufgeführt sind, können Sie benutzerdefinierte Bootstrapperpakete erstellen und Visual Studio hinzufügen. Dann können Sie die erforderlichen Komponenten im Dialogfeld **Erforderliche Komponenten** auswählen. Weitere Informationen finden Sie unter [Erstellen von Bootstrapperpaketen](../deployment/creating-bootstrapper-packages.md).

 Standardmäßig ist Bootstrapping für die ClickOnce-Bereitstellung aktiviert. Der für die ClickOnce-Bereitstellung generierte Bootstrapper ist signiert. Sie können das Bootstrapping für eine Komponente deaktivieren, aber nur, wenn Sie sicher sind, dass die richtige Version der Komponente bereits auf allen Ziel Computern installiert ist.

## <a name="bootstrapping-and-clickonce-deployment"></a>Bootstrapping und ClickOnce-Bereitstellung
 Vor der Installation einer Anwendung auf einem Client Computer wird [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] der Client von untersucht, um sicherzustellen, dass die im Anwendungs Manifest angegebenen Anforderungen erfüllt sind. Hierzu gehören die folgenden Anforderungen:

- Die mindestens erforderliche Version von Common Language Runtime, die als Assemblyabhängigkeit im Anwendungsmanifest angegeben ist.

- Die für die Anwendung mindestens erforderliche Version des Windows-Betriebssystems, wie im Anwendungsmanifest mit dem `<osVersionInfo>`-Element angegeben. (Siehe [ \<dependency> Element](../deployment/dependency-element-clickonce-application.md).)

- Die minimale Version aller Assemblys, die im globalen Assemblycache (GAC) vorinstalliert werden müssen, wie von assemblyabhängigkeits Deklarationen im Assemblymanifest angegeben.

  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] kann fehlende erforderliche Komponenten bestimmen, und Sie können erforderliche Komponenten mit Bootstrap installieren. Weitere Informationen finden Sie unter Gewusst [wie: Installieren von erforderlichen Komponenten mit einer ClickOnce-Anwendung](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md).

> [!NOTE]
> Um die Werte in den Manifesten zu ändern, die von Tools wie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und *MageUI.exe* generiert wurden, müssen Sie das Anwendungsmanifest in einem Text-Editor bearbeiten. Signieren Sie anschließend die Anwendungs- und Bereitstellungsmanifeste erneut. Weitere Informationen finden Sie unter Gewusst [wie: Erneutes Signieren von Anwendungs-und Bereitstellungs Manifesten](../deployment/how-to-re-sign-application-and-deployment-manifests.md).

 Wenn Sie Visual Studio und ClickOnce für die Bereitstellung der Anwendung verwenden, hängen die standardmäßig ausgewählten Bootstrapperpakete von der .NET Framework-Version in der Projektmappe ab. Wenn Sie jedoch die .NET Framework-Zielversion ändern, müssen Sie die Optionen im Dialogfeld **Erforderliche Komponenten** manuell aktualisieren.

|.NET Framework-Zielversion|Ausgewählte Bootstrapperpakete|
|---------------------------|------------------------------------|
|.NET Framework 4 Client Profile|.NET Framework 4 Client Profile<br /><br /> Windows Installer 3.1|
|.NET Framework 4|.NET Framework 4<br /><br /> Windows Installer 3.1|

 Bei der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]-Bereitstellung verweist die Seite *Publish.htm*, die vom [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]-Webpublishing-Assistenten generiert wird, auf einen Link, mit dem nur die Anwendung installiert wird, oder auf einen Link, mit dem die Anwendung und die Bootstrappingkomponenten installiert werden.

 Wenn Sie den Boots Trapper mithilfe des ClickOnce-Veröffentlichungs-Assistenten oder der Seite "veröffentlichen" in Visual Studio generieren, wird der *Setup.exe* automatisch signiert. Wenn Sie jedoch das Zertifikat des Kunden zum Signieren des Bootstrappers verwenden möchten, können Sie die Datei später signieren.

## <a name="bootstrapping-and-msbuild"></a>Bootstrapping und MSBuild
 Wenn Sie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Ihre Anwendungen nicht verwenden, sondern stattdessen in der Befehlszeile kompilieren, können Sie die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bootstrapping-Anwendung mithilfe einer Microsoft-Build-Engine-Aufgabe (MSBuild) erstellen. Weitere Informationen finden Sie unter [GenerateBootstrapper-Aufgabe](../msbuild/generatebootstrapper-task.md).

 Als Alternative zum Bootstrapping können Sie Komponenten mit einem elektronischen Softwareverteilungssystem wie Microsoft Systems Management Server (SMS) vorab bereitstellen.

## <a name="bootstrapper-setupexe-command-line-arguments"></a>Bootstrapper-Befehlszeilenargumente („Setup.exe“)
 Der  von generierteSetup.exe[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und die MSBuild-Aufgaben unterstützen den folgenden Satz von Befehlszeilen Argumenten. Alle anderen Argumente werden an das Anwendungsinstallations Programm weitergeleitet.

 Wenn Sie bootstrapperoptionen ändern, müssen Sie den Boots Trapper ohne Vorzeichen ändern und dann die Bootstrapperdatei später signieren.

| Befehlszeilenargument | Beschreibung |
| - | - |
| **-?, -h, -help** | Zeigt das Dialogfeld der Hilfe an. |
| **-url, -componentsurl** | Zeigt die gespeicherte URL und Komponenten-URLs für diese Installation an. |
| **-URL =**`location` | Legt die URL fest, unter der *Setup.exe* nach der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung sucht. |
| **-componentsurl=** `location` | Legt die URL fest, unter der *Setup.exe* nach den Abhängigkeiten sucht, z. b. die .NET Framework. |
| **-homesite=** `true` **&#124;** `false` | Bei `true` werden die Abhängigkeiten vom bevorzugten Speicherort auf der Website des Anbieters heruntergeladen. Diese Einstellung überschreibt die Einstellung **-componentsurl** . Wenn `false` , werden die Abhängigkeiten von der durch **-componentsurl** angegebenen URL heruntergeladen. |

## <a name="operating-system-support"></a>Betriebssystemunterstützung
 Der Visual Studio-Boots Trapper wird auf Windows Server 2008 Server Core oder Windows Server 2008 R2 Server Core nicht unterstützt, da er eine Serverumgebung mit geringer Wartung mit eingeschränkter Funktionalität bereitstellt. Die Server Core-Installationsoption unterstützt z. b. nur das .NET Framework 3,5 Server Core-Profil, das die Visual Studio-Funktionen, die von der vollständigen .NET Framework abhängen, nicht ausführen kann.

## <a name="see-also"></a>Weitere Informationen
- [Auswählen einer Strategie für die ClickOnce-Bereitstellung](../deployment/choosing-a-clickonce-deployment-strategy.md)
- [ClickOnce-Sicherheit und -Bereitstellung](../deployment/clickonce-security-and-deployment.md)