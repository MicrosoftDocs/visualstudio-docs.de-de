---
title: Problembehandlung von Netzwerk- oder Proxyfehlern
description: Finden Sie Lösungen für netzwerk- oder proxybezogene Fehler, die beim Installieren oder Verwenden von Visual Studio hinter einer Firewall oder einem Proxyserver auftreten können.
ms.date: 10/29/2019
ms.topic: troubleshooting
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
- list of domains, locations, URLs, Visual Studio
- proxy errors, Visual Studio
ms.assetid: ''
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 1e5af6f11a6b5036b50f44abaf50c5adfe18487b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99959180"
---
# <a name="troubleshoot-network-related-errors-when-you-install-or-use-visual-studio"></a>Beheben von Netzwerkfehlern beim Installieren oder Verwenden von Visual Studio

Hier erfahren Sie, welche Lösungen für die häufigsten netzwerk- oder proxybezogenen Fehler zur Verfügung stehen, die beim Installieren oder Verwenden von Visual Studio hinter einer Firewall oder einem Proxyserver auftreten können.

## <a name="error-proxy-authorization-required"></a>Fehler: „Proxyautorisierung erforderlich“

Dieser Fehler tritt normalerweise auf, wenn Benutzer über einen Proxyserver mit dem Internet verbunden sind, und der Proxyserver die Aufrufe einiger Netzwerkressourcen blockiert, die von Visual Studio ausgeführt werden.

### <a name="to-fix-this-proxy-error"></a>So beheben Sie diesen Proxyfehler

- Starten Sie Visual Studio neu. Das Dialogfeld Proxy-Authentifizierung sollte angezeigt werden. Geben Sie bei Aufforderung Ihre Anmeldeinformationen in das Dialogfeld ein.

- Wenn das Problem durch einen Neustart von Visual Studio nicht behoben wird, liegt dies möglicherweise daran, dass Ihr Proxyserver keine Anmeldeinformationen für Adressen von Typ „http:&#47;&#47;go.microsoft.com“, sondern für Adressen vom Typ „&#42;.visualStudio.microsoftcom“ erwartet. Für diese Server müssen Sie die folgenden URLs möglicherweise einer Zulassungsliste hinzufügen, um die Blockierung aller Anmeldeszenarien in Visual Studio aufzuheben:

  - &#42;.windows.net

  - &#42;.microsoftonline.com

  - &#42;.visualstudio.microsoft.com

  - &#42;.microsoft.com

  - &#42;.live.com

- Sie können die Adresse „http:&#47;&#47;go.microsoft.com“ andernfalls aus der Zulassungsliste entfernen, damit das Dialogfeld „Proxyauthentifizierung“ beim Neustart von Visual Studio sowohl für die Adresse „http:&#47;&#47;go.microsoft.com“ als auch die Serverendpunkte angezeigt wird.

  -ODER-

- Wenn Sie die standardmäßigen Anmeldeinformationen mit Ihrem Proxy verwenden möchten, können Sie Folgendes tun:

::: moniker range="vs-2017"

  1. Suchen Sie **devenv.exe.config** (die Konfigurationsdatei „devenv.exe“) in **%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE** oder **%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE**.

  2. Suchen Sie in der Konfigurationsdatei die `<system.net>`-Sperre und fügen Sie dann diesen Code hinzu:

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress="http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      Sie müssen die korrekte Proxy-Adresse für Ihr Netzwerk in `proxyaddress="<http://<yourproxy:port#>` einfügen.

     > [!NOTE]
     > Weitere Informationen finden Sie auf den Seiten zu den Elementen [&lt;defaultProxy&gt; (Netzwerkeinstellungen)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings/) und [&lt;proxy&gt; (Netzwerkeinstellungen)](/dotnet/framework/configure-apps/file-schema/network/proxy-element-network-settings).

::: moniker-end

::: moniker range="vs-2019"

  1. Suchen Sie **devenv.exe.config** (die Konfigurationsdatei „devenv.exe“) in **%ProgramFiles%\Microsoft Visual Studio\2019\Enterprise\Common7\IDE** oder **%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Enterprise\Common7\IDE**.

  2. Suchen Sie in der Konfigurationsdatei die `<system.net>`-Sperre und fügen Sie dann diesen Code hinzu:

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress="http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      Sie müssen die korrekte Proxy-Adresse für Ihr Netzwerk in `proxyaddress="<http://<yourproxy:port#>` einfügen.

     > [!NOTE]
     > Weitere Informationen finden Sie auf den Seiten zu den Elementen [&lt;defaultProxy&gt; (Netzwerkeinstellungen)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings/) und [&lt;proxy&gt; (Netzwerkeinstellungen)](/dotnet/framework/configure-apps/file-schema/network/proxy-element-network-settings).

::: moniker-end

## <a name="error-disconnected-from-visual-studio-when-attempting-to-report-a-problem"></a>Fehler: „Getrennt von Visual Studio“ beim Versuch, ein Problem zu melden

Dieser Fehler tritt normalerweise auf, wenn Benutzer über einen Proxyserver mit dem Internet verbunden sind und der Proxyserver die Aufrufe einiger Netzwerkressourcen durch Visual Studio blockiert.

### <a name="to-fix-this-proxy-error"></a>So beheben Sie diesen Proxyfehler

1. Suchen Sie in **%Programme (x86)%\Microsoft Visual Studio\Installer** oder in **%Programme%\Microsoft Visual Studio\Installer** nach **feedback.exe.config** (feedback.exe-Konfigurationsdatei).

2. Überprüfen Sie in der Konfigurationsdatei, ob der folgende Code vorhanden ist. Falls der Code nicht vorhanden ist, fügen Sie ihn vor der letzten `</configuration>`-Zeile ein.

   ```xml
   <system.net>
       <defaultProxy useDefaultCredentials="true" />
   </system.net>
   ```

## <a name="error-the-underlying-connection-was-closed"></a>Fehler; „Die zugrunde liegende Verbindung wurde geschlossen“

Wenn Sie Visual Studio in einem privaten Netzwerk mit einer Firewall verwenden, kann Visual Studio möglicherweise keine Verbindung mit einigen Netzwerkressourcen herstellen. Dies kann auch Azure DevOps Services für Anmeldung und Lizenzierung, NuGet und Azure-Dienste betreffen. Falls Visual Studio keine Verbindung mit einer dieser Ressourcen herstellen kann, wird möglicherweise die folgende Fehlermeldung angezeigt:

  **The underlying connection was closed: An unexpected error occurred on send** (Die zugrunde liegende Verbindung wurde geschlossen: Beim Senden ist ein unerwarteter Fehler aufgetreten.)

Visual Studio verwendet das Protokoll Transport Layer Security (TLS) 1.2 für die Verbindung mit Netzwerkressourcen. Sicherheitsappliances blockieren in einigen privaten Netzwerken bestimmte Serververbindungen, wenn Visual Studio TLS 1.2 verwendet.

### <a name="to-fix-this-connection-error"></a>So beheben Sie diesen Verbindungsfehler

Lassen Sie Verbindungen mit den folgenden URLs zu:

- https:&#47;&#47;management.core.windows.net

- https:&#47;&#47;app.vssps.visualstudio.com

- https:&#47;&#47;login.microsoftonline.com

- https:&#47;&#47;login.live.com

- https:&#47;&#47;go.microsoft.com

- https:&#47;&#47;graph.windows.net

- https:&#47;&#47;app.vsspsext.visualstudio.com

- &#42;.azurewebsites.net (für Azure-Verbindungen)

- &#42;.visualstudio.microsoft.com

- cdn.vsassets.io (Hosting von CDN-Inhalten (Content Delivery Network))

- &#42;.gallerycdn.vsassets.io (hostet Azure DevOps Services-Erweiterungen)

- static2.sharepointonline.com (Hosting von Ressourcen wie beispielsweise Schriftarten, die Visual Studio im Office Fabric UI-Kit verwendet)

- &#42;.nuget.org (für NuGet-Verbindungen)

  > [!NOTE]
  > URLs von privaten NuGet-Servern sind in dieser Liste möglicherweise nicht enthalten. Sie können in „%APPData%\Nuget\NuGet.Config“ überprüfen, welche NuGet-Server Sie verwenden.

## <a name="error-failed-to-parse-id-from-parent-process"></a>Fehler: „Failed to parse ID from parent process“ (Die Analyse der ID des übergeordneten Prozesses ist fehlgeschlagen.)

Diese Fehlermeldung kann auftreten, wenn Sie einen Visual Studio-Bootstrapper und eine „response.json“-Datei auf einem Netzwerklaufwerk verwenden. Die Benutzerkontensteuerung in Windows ist die Ursache für diesen Fehler.

Der Fehler kann wegen dem folgenden Grund auftreten: Ein zugeordnetes Netzwerklaufwerk oder eine [UNC](/dotnet/standard/io/file-path-formats#unc-paths)-Freigabe wird mit dem Zugriffstoken eines Benutzers verknüpft. Wenn die Benutzerkontensteuerung aktiviert ist, werden zwei [Benutzerzugriffstoken](/windows/win32/secauthz/access-tokens) erstellt: Eines *mit* Administratorzugriff und eines *ohne* Administratorzugriff. Wenn ein Netzwerklaufwerk oder die Freigabe erstellt wird, wird das aktuelle Zugriffstoken des Benutzers mit dieser verknüpft. Da der Bootstrapper mit Administratorrechten ausgeführt werden muss, kann er nicht auf das Netzwerklaufwerk oder die Freigabe zugreifen, wenn keine Verknüpfung mit einem Benutzerzugriffstoken besteht, das über Administratorzugriff verfügt.

### <a name="to-fix-this-error"></a>So beheben Sie diesen Fehler

Sie können den `net use`-Befehl verwenden oder die Gruppenrichtlinieneinstellung der Benutzerkontensteuerung ändern. Weitere Informationen zu diesen Problemumgehungen und zur Implementierung dieser finden Sie in den folgenden Microsoft-Supportartikeln:

* [Zugeordnete Laufwerke sind nicht über eine Eingabeaufforderung mit erhöhten Rechten verfügbar, wenn die Benutzerkontensteuerung zur „Eingabeaufforderung von Anmeldeinformationen“ in Windows konfiguriert ist](https://support.microsoft.com/help/3035277/mapped-drives-are-not-available-from-an-elevated-prompt-when-uac-is-co)
* [Programme können nach Aktivierung der Benutzerkontensteuerung auf Windows-Betriebssystemen möglicherweise auf einige Netzwerkspeicherorte nicht zugreifen](https://support.microsoft.com/en-us/help/937624/programs-may-be-unable-to-access-some-network-locations-after-you-turn)

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Weitere Informationen

* [Installieren und Verwenden von Visual Studio hinter einer Firewall oder einem Proxyserver](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)
* [Administratorhandbuch für Visual Studio 2017 RC](visual-studio-administrator-guide.md)
* [Installieren von Visual Studio](install-visual-studio.md)
