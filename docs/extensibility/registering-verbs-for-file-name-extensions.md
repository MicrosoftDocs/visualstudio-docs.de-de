---
title: Registrieren von Verben für Dateinamen Erweiterungen | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie mithilfe eines shellschlüssels ein Verb registrieren, das einem programmgesteuerten Bezeichner für eine Dateierweiterung zugeordnet ist.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- verbs, registering
ms.assetid: 81a58e40-7cd0-4ef4-a475-c4e1e84d6e06
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 10e1b158ab62cfedfb6171a0a3874cfe14e89caf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837003"
---
# <a name="register-verbs-for-file-name-extensions"></a>Registrieren von Verben für Dateinamen Erweiterungen
Die Zuordnung einer Dateinamenerweiterung zu einer Anwendung hat im Allgemeinen eine bevorzugte Aktion, die auftritt, wenn ein Benutzer auf eine Datei doppelklickt. Diese bevorzugte Aktion ist mit einem Verb verknüpft, z. b. öffnen, das der Aktion entspricht.

 Sie können Verben, die einem programmatischen Bezeichner (ProgID) für eine Erweiterung zugeordnet sind, mithilfe des shellschlüssels, der sich unter **HKEY_CLASSES_ROOT \{ ProgID} \Shell** befindet, registrieren. Weitere Informationen finden Sie unter [Dateitypen](/windows/desktop/shell/fa-file-types).

## <a name="register-standard-verbs"></a>Standard Verben registrieren
 Das Betriebssystem erkennt die folgenden Standard Verben:

- Öffnen

- Bearbeiten

- Abspielen

- Drucken

- Vorschau

  Registrieren Sie nach Möglichkeit ein Standard-Verb. Die häufigste Wahl ist das geöffnete Verb. Verwenden Sie das Bearbeitungs Verb nur dann, wenn es einen deutlichen Unterschied zwischen dem Öffnen der Datei und dem Bearbeiten der Datei gibt. Wenn Sie z. b *. eine htm* -Datei öffnen, wird Sie im Browser angezeigt, während beim Bearbeiten einer *htm* -Datei ein HTML-Editor gestartet wird. Standard Verben werden mit dem Gebiets Schema des Betriebssystems lokalisiert.

> [!NOTE]
> Wenn Sie Standard Verben registrieren, legen Sie den Standardwert für den geöffneten Schlüssel nicht fest. Der Standardwert enthält die Anzeige Zeichenfolge im Menü. Das Betriebssystem stellt diese Zeichenfolge für Standard Verben bereit.

 Projektdateien müssen registriert werden, um eine neue Instanz von zu starten, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Wenn ein Benutzer die Datei öffnet. Das folgende Beispiel veranschaulicht eine standardmäßige Verb Registrierung für ein- [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Projekt.

```
[HKEY_CLASSES_ROOT\.csproj]
@="VisualStudio.csproj.8.0"

[HKEY_CLASSES_ROOT\.csproj\OpenWithList]
[HKEY_CLASSES_ROOT\.csproj\OpenWithList\VSLauncher.exe]
@=""

[HKEY_CLASSES_ROOT\.csproj\OpenWithProgids]
"VisualStudio.csproj.8.0"=""

[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe]
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell]
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open]
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open\Command]
@="C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe \"%1\""

[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0]
@="C# Project file"

[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\DefaultIcon]
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,0"

[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell]
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open]
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open\Command]
@="\"C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe\" \"%1\""
```

 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Registrieren Sie einen ddeexec-Schlüssel, um eine Datei in einer vorhandenen Instanz von zu öffnen. Das folgende Beispiel veranschaulicht eine standardmäßige Verb Registrierung für eine [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] *CS* -Datei.

```
[HKEY_CLASSES_ROOT\.cs]
@="VisualStudio.cs.8.0"

[HKEY_CLASSES_ROOT\.cs\OpenWithList]
[HKEY_CLASSES_ROOT\.cs\OpenWithList\devenv.exe]
@=""

[HKEY_CLASSES_ROOT\.cs\OpenWithProgids]
"VisualStudio.cs.8.0"=""

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0]
@="C# Source file"

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\DefaultIcon]
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,1"

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell]
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open]
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\Command]
@="\"C:\\VisualStudioPath\\Common7\\IDE\\devenv.exe\" /dde \"%1\""

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec]
@="Open(\"%1\")"

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Application]
@="VisualStudio.8.0"

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Topic]
@="system"
```

## <a name="set-the-default-verb"></a>Festlegen des Standard Verbs
 Das Standardverb ist die Aktion, die ausgeführt wird, wenn ein Benutzer auf eine Datei im Windows-Explorer doppelklickt. Das Standardverb ist das Verb, das als Standardwert für den **HKEY_CLASSES_ROOT \\ *ProgID*\Shell** -Schlüssel angegeben wird. Wenn kein Wert angegeben wird, ist das Standardverb das erste Verb, das in der **HKEY_CLASSES_ROOT \\ *ProgID*\shellschlüsselliste** angegeben ist.

> [!NOTE]
> Wenn Sie das Standard Verb für eine Erweiterung in einer parallelen Bereitstellung ändern möchten, berücksichtigen Sie die Auswirkungen auf die Installation und Entfernung. Während der Installation wird der ursprüngliche Standardwert überschrieben.

## <a name="see-also"></a>Weitere Informationen
- [Parallele Dateizuordnungen verwalten](../extensibility/managing-side-by-side-file-associations.md)
