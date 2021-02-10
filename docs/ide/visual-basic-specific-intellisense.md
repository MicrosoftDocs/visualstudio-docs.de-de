---
title: IntelliSense für Visual Basic
description: Hier erfahren Sie, wie Sie die IntelliSense-Features des Quellcode-Editors für Visual Basic verwenden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.Basic.IntelliSense
helpviewer_keywords:
- IntelliSense [Visual Basic]
- IntelliSense [Visual Studio], Visual Basic
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1420165c8ca574c74efe6911bb9c5635e729a260
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955553"
---
# <a name="intellisense-for-visual-basic-code-files"></a>IntelliSense für Visual Basic-Codedateien

Der Quellcode-Editor von Visual Basic stellt die folgenden IntelliSense-Features bereit:

## <a name="syntax-tips"></a>Tipps zur Syntax

In den Tipps zur Syntax wird die Syntax der Anweisung angezeigt, die Sie eintippen. Dies ist für Anweisungen wie [Declare](/dotnet/visual-basic/language-reference/statements/declare-statement) nützlich.

## <a name="automatic-completion"></a>Automatische Vervollständigung

- Vervollständigung unterschiedlicher Schlüsselwörter

     Wenn Sie beispielsweise `goto` und ein Leerzeichen eingeben, zeigt IntelliSense eine Liste der definierten Bezeichnungen in einem Dropdownmenü. Andere unterstützte Schlüsselwörter sind unter anderem `Exit`, `Implements`, `Option` und `Declare`.

- Vervollständigung für `Enum` und `Boolean`

    Wenn eine Anweisung auf einen Member einer Enumeration verweist, zeigt IntelliSense eine Liste der Members der `Enum`-Aufzählung. Wenn eine Anweisung auf `Boolean` verweist, zeigt IntelliSense ein Dropdownmenü mit TRUE und FALSE an.

Die Vervollständigung kann standardmäßig deaktiviert werden. Wählen Sie hierzu von der Eigenschaftenseite **Allgemein** im Ordner **Visual Basic****Member automatisch auflisten** aus.

Sie können die Vervollständigung manuell aufrufen, indem Sie auf „Member auflisten“ oder „Wort vervollständigen“ klicken oder **ALT**+**NACH-RECHTS-TASTE** drücken. Weitere Informationen finden Sie unter [Verwenden von IntelliSense](../ide/using-intellisense.md).

## <a name="intellisense-in-zone"></a>IntelliSense pro Zone

„IntelliSense pro Zone“ hilft Visual Basic-Entwicklern, die Anwendungen über [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bereitstellen müssen und durch Einstellungen für teilweise vertrauenswürdige Anwendungen eingeschränkt sind. Mithilfe dieser Funktion

- wird Ihnen ermöglicht, die Berechtigungen auszuwählen, mit der die Anwendung ausgeführt wird.

- werden APIs in der ausgewählten Zone in „Member auflisten“ als verfügbar angezeigt und APIs, die zusätzliche Berechtigungen erfordern, als nicht verfügbar angezeigt.

Weitere Informationen finden Sie unter [Code Access Security for ClickOnce Applications (Codezugriffssicherheit für ClickOnce-Anwendungen)](../deployment/code-access-security-for-clickonce-applications.md).

## <a name="filtered-completion-lists"></a>Gefilterte Vervollständigungslisten

In Visual Basic verfügen IntelliSense-Vervollständigungslisten über zwei Registersteuerelemente, die sich am unteren Rand der Liste befinden. Die Registerkarte **Allgemein**, die standardmäßig ausgewählt ist, zeigt Elemente, die am häufigsten zur Vervollständigung der Anweisung verwendet werden, die Sie schreiben. Die Registerkarte **Alle** zeigt alle Elemente an, die für die automatische Vervollständigung verfügbar sind, darunter auch diejenigen, die sich auch auf der Registerkarte **Allgemein** befinden.

## <a name="see-also"></a>Siehe auch

- [Verwendung von IntelliSense](../ide/using-intellisense.md)
