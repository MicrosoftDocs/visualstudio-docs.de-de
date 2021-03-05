---
title: Problembehandlung bei der Vorlagen Ermittlung in Visual Studio | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie die Diagnoseprotokollierung für die Problembehandlung bei der Bereitstellung benutzerdefinierter Projekte und Vorlagen im Visual Studio SDK aktivieren.
ms.custom: SEO-VS-2020
ms.date: 01/02/2018
ms.topic: troubleshooting
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1ea99c1d74c06ab42ff86f07de4cf5c76e95de43
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151323"
---
# <a name="troubleshooting-template-installation"></a>Problembehandlung der Vorlagen Installation

Wenn bei der Bereitstellung der Projekt-oder Element Vorlagen Probleme auftreten, können Sie die Diagnoseprotokollierung aktivieren.

::: moniker range="vs-2017"

1. Erstellen Sie eine pkgdef-Datei im Ordner *Common7\IDE\CommonExtensions* für die Installation. Beispiel: *c:\Programme (x86) \Microsoft Visual studio\2017\enterprise\common7\ide\commonextensions\enablepkgdeflogging.pkgdef*.

::: moniker-end

::: moniker range=">=vs-2019"

1. Erstellen Sie eine pkgdef-Datei im Ordner *Common7\IDE\CommonExtensions* für die Installation. Beispiel: *c:\Programme (x86) \Microsoft Visual studio\2019\enterprise\common7\ide\commonextensions\enablepkgdeflogging.pkgdef*.

::: moniker-end

2. Fügen Sie der pkgdef-Datei Folgendes hinzu:

    ```
    [$RootKey$\VsTemplate]
    "EnableTemplateDiscoveryLog"=dword:00000001
    ```

3. Öffnen Sie eine [Developer-Eingabeaufforderung](../ide/reference/command-prompt-powershell.md) für die-Installation, und führen Sie aus `devenv /updateConfiguration` .

::: moniker range="vs-2017"

4. Öffnen Sie Visual Studio, und starten Sie die Dialogfelder Neues Projekt und neues Element, um beide Vorlagen Strukturen zu initialisieren.

   Das Vorlagen Protokoll wird jetzt in **%LocalAppData%\microsoft\visualstudio\15.0_ [InstanceId] \VsTemplateDiagnosticsList.csv** angezeigt (die InstanceId entspricht der Installations-ID Ihrer Instanz von Visual Studio). Jede Vorlagen Struktur Initialisierung fügt Einträge an dieses Protokoll an.

::: moniker-end

::: moniker range=">=vs-2019"

4. Öffnen Sie Visual Studio, und starten Sie die Dialogfelder **Neues Projekt** und **Neues Element** erstellen, um beide Vorlagen Strukturen zu initialisieren.

   Das Vorlagen Protokoll wird jetzt in **%LocalAppData%\microsoft\visualstudio\16.0_ [InstanceId] \VsTemplateDiagnosticsList.csv** angezeigt (die InstanceId entspricht der Installations-ID Ihrer Instanz von Visual Studio). Jede Vorlagen Struktur Initialisierung fügt Einträge an dieses Protokoll an.

::: moniker-end

Die Protokolldatei enthält die folgenden Spalten:

- **Fullpathto Template** mit den folgenden Werten:

  - 1 für die manifestressourcenbasierte Bereitstellung

  - 0 für Datenträger basierte Bereitstellung

- **Templatefilename**

- Weitere Vorlagen Eigenschaften

> [!NOTE]
> Um die Protokollierung zu deaktivieren, entfernen Sie entweder die pkgdef-Datei, oder ändern Sie den Wert von `EnableTemplateDiscoveryLog` in `dword:00000000` , und führen Sie dann `devenv /updateConfiguration` erneut aus.

## <a name="see-also"></a>Weitere Informationen

- [Erstellen von benutzerdefinierten Projekt-und Element Vorlagen](creating-custom-project-and-item-templates.md)
- [Problembehandlung für Visual Studio](/troubleshoot/visualstudio/welcome-visual-studio/)
