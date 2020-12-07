---
title: Optionen, Text-Editor, C/C++, Ansicht
description: Hier erfahren Sie, wie Sie mithilfe der Seite „Ansicht“ im Abschnitt „C/C++“ das Standardverhalten von Wellenlinien im Code, inaktivem Code, der Gliederung und mehr in Visual Studio ändern.
ms.custom: SEO-VS-2020
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.View
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.View
- VS.ToolsOptionsPages.Text_Editor.C\C++.View
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 68d08953ca3c493f3b3e42dd4ddd84bc19bdfd6e
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/25/2020
ms.locfileid: "96041073"
---
# <a name="options-text-editor-cc-view"></a>Optionen, Text-Editor, C/C++, Ansicht

Verwenden Sie diesen Eigenschaftenseiten, um das Standardverhalten des Code-Editors zu ändern, wenn Sie in C oder C++ programmieren.

Wählen Sie **Tools** > **Optionen** aus, erweitern Sie **Text-Editor** und dann **C/C++** , und wählen Sie **Ansicht** aus, um auf diese Eigenschaftenseite zuzugreifen.

## <a name="code-squiggles"></a>Wellenlinien im Code

Sie können die folgenden Einstellungen aktivieren oder deaktivieren, um festzulegen, wie der Text-Editor Wellenlinien im Code für C und C++ behandelt:

- **Macros in Skipped Browsing Regions** (Makros in übersprungenen Suchbereichen): Definiert, wie Makros hervorgehoben werden, die sich in von der Suchdatenbank übersprungenen Bereichen befinden, darunter Makros, deren Definitionen geschweifte Klammern beinhalten.

- **Macros Convertible to constexpr** (Makros können in constexpr konvertiert werden): Definiert, wie Makrodefinitionen hervorgehoben werden, die in `constexpr`-Definitionen konvertiert werden können.

## <a name="inactive-code"></a>Inaktiver Code

- **Inaktive Blocks anzeigen:** Inaktive Präprozessorblocks werden unterschiedlich eingefärbt.

- **Durchlässigkeit inaktiven Codes deaktivieren:** Anstelle der Durchlässigkeit für inaktive Codeblocks wird eine Volltonfarbe verwendet.

- **Durchlässigkeitsprozentsatz inaktiven Codes:** Der Durchlässigkeitsprozentsatz inaktiver Codeblocks.

## <a name="miscellaneous"></a>Sonstiges

- **Kommentaraufgaben aufzählen:** Quelldateien auf VS-Token prüfen und Vorkommnisse im Aufgabenlistenfenster aufführen.

- **Übereinstimmende Token hervorheben:** Einschließende Klammern oder Syntax werden hervorgehoben, wenn der Cursor über ein übereinstimmendes Element bewegt wird.

## <a name="outlining"></a>Gliedern

- **Gliederung aktivieren:** Startet den Gliederungsmodus beim Öffnen einer Datei.

- **Pragmabereiche gliedern:** Automatische Gliederung von `#pragma`-Bereichblocks.

- **Anweisungsblocks gliedern:** Automatische Gliederung von Anweisungsblocks.

## <a name="see-also"></a>Siehe auch

- [Festlegen von sprachspezifischen Editor-Optionen](../../ide/reference/setting-language-specific-editor-options.md)
- [Umgestaltung in C++ (VC-Blog)](https://devblogs.microsoft.com/cppblog/all-about-c-refactoring-in-visual-studio-2015-preview/)
