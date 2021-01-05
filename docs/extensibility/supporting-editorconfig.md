---
title: Sprachdienst für die Unterstützung von editorconfig erweitern
description: Informationen zu den Änderungen, die zum Aktualisieren eines sprach Dienstanbieter zur Unterstützung von editorconfig-Dateien durchführen Ersetzen Sie eine globale sprachspezifische Option durch eine Kontext Option.
ms.custom: SEO-VS-2020
ms.date: 11/22/2017
ms.topic: conceptual
helpviewer_keywords:
- editorconfig [extensibility]
- editorconfig, supporting in a language service
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0c635df2301822fc1bb982df44912527d53c9ef6
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/21/2020
ms.locfileid: "97716106"
---
# <a name="supporting-editorconfig-for-your-language-service"></a>Unterstützung von editorconfig für Ihren Sprachdienst

Mit [editorconfig](https://editorconfig.org/) -Dateien können Sie allgemeine Text-Editor-Optionen (z. b. Einzugs Größe) auf Projektbasis beschreiben. Weitere Informationen zur Unterstützung von editorconfig-Dateien in Visual Studio finden Sie unter [Erstellen von portablen Editor-Einstellungen mit editorconfig](../ide/create-portable-custom-editor-options.md).

In den meisten Fällen ist bei der Implementierung eines Visual Studio-Sprachdiensts keine zusätzliche Arbeit erforderlich, um universelle EditorConfig-Eigenschaften zu unterstützen. Der Haupteditor ermittelt und liest die .editorconfig-Datei automatisch, wenn Benutzer Dateien öffnen, und er legt den entsprechenden Textpuffer und die Ansichtsoptionen fest. Bei bearbeitbaren Änderungen, z. b. Registerkarten und Leerzeichen, können einige Sprachdienste jedoch eine geeignete kontextabhängige Text Ansichts Option verwenden, anstatt globale Einstellungen zu verwenden. In diesen Fällen muss der Sprachdienst aktualisiert werden, um EditorConfig-Dateien zu unterstützen.

Im folgenden sind die Änderungen aufgeführt, die erforderlich sind, um einen Sprachdienst zur Unterstützung von editorconfig-Dateien zu aktualisieren, indem eine globale _sprachspezifische_ Option durch eine _Kontext_ Option ersetzt wird:

## <a name="indent-style"></a>Einzugsgröße

Sprachspezifische Optionen | Kontextoptionen
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.fInsertTabs<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs|!textBufferOptions.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)<br/>!textView.Options.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)

## <a name="indent-size"></a>Einzugsgröße

Sprachspezifische Optionen | Kontextoptionen
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uIndentSize<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.IndentSize|textBufferOptions.GetOptionValue(DefaultOptions.IndentSizeOptionId)<br/>textView.Options.GetOptionValue(DefaultOptions.IndentSizeOptionId)

## <a name="tab-size"></a>Tabulatorgröße

Sprachspezifische Optionen | Kontextoptionen
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uTabSize<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.TabSize|textBufferOptions.GetOptionValue(DefaultOptions.TabSizeOptionId)<br/>textView.Options.GetOptionValue(DefaultOptions.TabSizeOptionId)

## <a name="see-also"></a>Weitere Informationen

- [Erstellen portabler Editor-Einstellungen mit editorconfig](../ide/create-portable-custom-editor-options.md)
- [Erweitern des Editors und der Sprachdienste](../extensibility/extending-the-editor-and-language-services.md)
