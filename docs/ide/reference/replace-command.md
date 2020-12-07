---
title: Befehl "Ersetzen"
description: Hier erfahren Sie mehr über den Befehl „Ersetzen“ und darüber, wie dieser mithilfe einiger Optionen auf der Registerkarte „In Dateien ersetzen“ des Fensters „Suchen und Ersetzen“ Text in Dateien ersetzt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- edit.replace
helpviewer_keywords:
- Edit.Replace command
- Replace command
ms.assetid: a15767f1-5a3d-44f5-8c77-7b0f1157f340
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2db7b59c1982f706cc6d2b18039870871ffa1039
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304040"
---
# <a name="replace-command"></a>Befehl "Ersetzen"
Ersetzt Text in Dateien mit einem Teil der Optionen, die auf der Registerkarte **In Dateien ersetzen** im Fenster **Suchen und Ersetzen** verfügbar sind.

## <a name="syntax"></a>Syntax

```
Edit.Replace findwhat replacewith [/all] [/case]
[/doc|/proc|/open|/sel] [/hidden] [/options] [/reset] [/up]
[/wild|/regex] [/word]
```

## <a name="arguments"></a>Argumente
`findwhat`

Erforderlich. Der Text, für den eine Übereinstimmung ermittelt werden soll.

`replacewith`

Erforderlich. Der Text, durch den der übereinstimmende Text ersetzt werden soll

## <a name="switches"></a>Switches
/all oder /a

Optional. Ersetzt den Suchtext bei jedem Vorkommen durch den Ersetzungstext

/case oder /c

Optional. Übereinstimmungen treten nur auf, wenn die groß und klein geschriebenen Zeichen mit den im `findwhat`-Argument angegebenen übereinstimmen.

/doc oder/d

Optional. Sucht nur im aktuellen Dokument. Geben Sie nur einen der verfügbaren Suchbereiche an (`/doc`, `/proc`, `/open` oder `/sel`).

/hidden oder /h

Optional. Sucht nach ausgeblendetem und reduziertem Text, z.B. nach den Metadaten eines Designzeit-Steuerelements, einem ausgeblendeten Bereich in einem umrissenen Dokument oder einer reduzierten Klasse bzw. Methode

/open oder /o

Optional. Sucht in allen geöffneten Dokumenten, als wären sie ein einziges Dokument. Geben Sie nur einen der verfügbaren Suchbereiche an (`/doc`, `/proc`, `/open` oder `/sel`).

/options oder /t

Optional. Zeigt eine Liste der aktuellen Optionseinstellungen für die Suche an und führt keine Suche aus.

/proc oder /p

Optional. Sucht nur in der aktuellen Prozedur. Geben Sie nur einen der verfügbaren Suchbereiche an (`/doc`, `/proc`, `/open` oder `/sel`).

/regex oder /r

Optional. Verwendet vordefinierte Sonderzeichen im `findwhat`-Argument als Notationen, die Textmuster anstelle von Literalzeichen darstellen. Eine vollständige Liste von Zeichen für reguläre Ausdrücke finden Sie unter [Reguläre Ausdrücke](../../ide/using-regular-expressions-in-visual-studio.md).

/reset oder /e

Optional. Legt die Suchoptionen wieder auf die Standardeinstellungen fest und führt keine Suche aus.

/sel oder /s

Optional. Sucht nur in der aktuellen Auswahl. Geben Sie nur einen der verfügbaren Suchbereiche an (`/doc`, `/proc`, `/open` oder `/sel`).

/up oder /u

Optional. Sucht von der aktuellen Position in der Datei bis zum Anfang der Datei. Standardmäßig beginnt die Suche bei der aktuellen Position in der Datei und wird bis zum Ende der Datei ausgeführt.

/wild oder /l

Optional. Verwendet vordefinierte Sonderzeichen im `findwhat`-Argument als Notationen, um ein Zeichen oder eine Abfolge von Zeichen darzustellen.

/word oder /w

Optional. Sucht nur nach ganzen Wörtern

## <a name="example"></a>Beispiel
In diesem Beispiel wird `btnSend` in allen geöffneten Dokumenten durch `btnSubmit` ersetzt.

```
>Edit.Replace btnSend btnSubmit /open
```

## <a name="see-also"></a>Siehe auch

- [Suchen und Ersetzen von Text](../../ide/finding-and-replacing-text.md)
- [Befehlsfenster](../../ide/reference/command-window.md)
- [Feld „Suchen/Befehl“](../../ide/find-command-box.md)
- [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
