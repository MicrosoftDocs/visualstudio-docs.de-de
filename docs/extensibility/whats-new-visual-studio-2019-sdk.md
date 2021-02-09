---
title: Neues im Visual Studio 2019 SDK | Microsoft-Dokumentation
description: Das Visual Studio SDK enthält die neuen und aktualisierten Features für Visual Studio 2019, einschließlich Verbesserungen der Editor Registrierung.
ms.custom: SEO-VS-2020
ms.date: 03/29/2019
ms.topic: conceptual
ms.assetid: 4a07607b-0c87-4866-acd8-6d68358d6a47
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 67b916826cdef939bacd906cf16f311f5f2fb30e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99880592"
---
# <a name="whats-new-in-the-visual-studio-2019-sdk"></a>Neuigkeiten im Visual Studio 2019 SDK

Das Visual Studio SDK verfügt über die folgenden neuen und aktualisierten Features für Visual Studio 2019.

## <a name="synchronously-autoloaded-extensions-warning"></a>Warnung für synchron authentifigene Erweiterungen

Benutzern wird jetzt eine Warnung angezeigt, wenn eine Ihrer installierten Erweiterungen beim Start synchron authentifiiert wird. Weitere Informationen zur Warnung finden Sie unter synchron authentifischere [Erweiterungen](synchronously-autoloaded-extensions.md).

## <a name="single-unified-visual-studio-sdk"></a>Einzelnes, einheitliches Visual Studio SDK

Sie können jetzt alle Visual Studio SDK-Ressourcen über ein einzelnes nuget-Paket " [Microsoft. VisualStudio. SDK](https://www.nuget.org/packages/microsoft.visualstudio.sdk)" erhalten.

## <a name="editor-registration-enhancements"></a>Erweiterungen der Editor Registrierung

Seit der Erstellung hat Visual Studio eine benutzerdefinierte Editor Registrierung unterstützt, bei der ein Editor seine Affinität für bestimmte Erweiterungen (z. b. XAML-und RC-Datei) deklarieren oder für eine beliebige Erweiterung (*) geeignet ist. Ab Visual Studio 2019 Version 16,1 haben wir die Unterstützung für die Editor Registrierung erweitert.

### <a name="filenames"></a>Dateinamen

Zusätzlich zu oder statt der Unterstützung für eine bestimmte Dateierweiterung, kann ein Editor registrieren, dass er bestimmte Dateinamen unterstützt, indem er das neue- `ProvideEditorFilename` Attribut auf das Paket des Editors anwendet.

Beispielsweise würde ein Editor, der alle JSON-Dateien unterstützt, dieses Attribut auf das zugehörige `ProvideEditorExtension` Paket anwenden:

```cs
[ProvideEditorExtension(typeof(MyEditor), ".json", MyEditor.Priority)]
```

Beginnend mit 16,1, wenn myeditor nur einige bekannte JSON-Dateien unterstützt, können diese Attribute stattdessen auf das zugehörige `ProvideEditorFilename` Paket angewendet werden:

```cs
[ProvideEditorFilename(typeof(MyEditor), "particular.json", MyEditor.Priority)]
[ProvideEditorFilename(typeof(MyEditor), "special.json",    MyEditor.Priority)]
```

### <a name="uicontexts"></a>UIContexts

Ein Editor kann mindestens eine UIContext-Datei registrieren, die darstellt, wann Sie aktiviert ist. Uicontexts werden registriert, indem eine oder mehrere Instanzen von `ProvideEditorUIContextAttribute` auf das Paket angewendet werden, das den Editor registriert.

Wenn ein Editor uicontexts registriert hat:

- Wenn mindestens einer der registrierten uicontexts aktiv ist, wenn eine Datei mit der angegebenen Erweiterung geöffnet wird, ist der Editor in der Editor-Suche enthalten.
- Wenn keines der registrierten uicontexts aktiv ist, ist der Editor nicht in der Editor-Suche enthalten.

Wenn ein Editor keine uicontexts registriert, ist er immer in der Editor-Suche nach dieser Erweiterung enthalten.

Wenn ein Editor z. b. nur verfügbar ist, wenn ein c#-Projekt geöffnet ist, kann er diese Affinität durch Anwenden eines- `ProvideEditorUIContext` Attributs deklarieren:

```cs
[ProvideEditorUIContext(typeof(MyEditor), KnownUIContexts.CSharpProjectContext)]
```
