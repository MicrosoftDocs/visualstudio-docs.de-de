---
title: Befehl „In Dateien suchen“ | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- edit.findinfiles
helpviewer_keywords:
- Edit.FindInFiles command
- find in files command
ms.assetid: 2fc78bfe-b339-4599-97f9-4cafd8a194d9
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 831a67fe567c2e6ae1e288d1bc7ee91026ff2273
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651039"
---
# <a name="find-in-files-command"></a>Befehl "In Dateien suchen"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Durchsucht Dateien mithilfe einer Teilmenge der Optionen, die im Fenster **Suchen und Ersetzen** auf der Registerkarte **In Dateien suchen** verfügbar sind.

## <a name="syntax"></a>Syntax

```
Edit.FindinFiles findwhat [/case] [/ext:extensions]
[/lookin:searchpath] [/names] [/options] [/reset] [/stop] [/sub]
[/text2] [/wild|/regex] [/word]
```

## <a name="arguments"></a>Argumente
 `findwhat` ist erforderlich. Der Text, für den eine Übereinstimmung ermittelt werden soll.

## <a name="switches"></a>Schalter
 /case oder /c ist optional. Übereinstimmungen treten nur auf, wenn die groß und klein geschriebenen Zeichen den im `findwhat`-Argument angegebenen Zeichen entsprechen.

 /ext: `extensions` ist optional. Legt die Dateierweiterungen für die zu suchenden Dateien fest. Wenn keine Erweiterung festgelegt wird und zuvor bereits eine Erweiterung angegeben wurde, wird diese verwendet.

 /lookin: `searchpath` ist optional. Das zu durchsuchende Verzeichnis. Wenn der Pfad Leerzeichen enthält, schließen Sie ihn vollständig in Anführungszeichen ein.

 /names oder /n ist optional. Zeigt eine Liste mit Dateinamen an, die Übereinstimmungen enthalten.

 /options oder /t ist optional. Zeigt eine Liste der aktuellen Optionseinstellungen für die Suche an und führt keine Suche aus.

 /regex oder /r ist optional. Verwendet vordefinierte Sonderzeichen im `findwhat`-Argument als Notationen, die Textmuster anstelle von Literalzeichen darstellen. Eine vollständige Liste von Zeichen für reguläre Ausdrücke finden Sie unter [Reguläre Ausdrücke](../../ide/using-regular-expressions-in-visual-studio.md).

 /reset oder /e ist optional. Legt die Suchoptionen wieder auf die Standardeinstellungen fest und führt keine Suche aus.

 /stop ist optional. Hält den aktuellen Suchvorgang an, wenn ein solcher ausgeführt wird. Bei der Suche werden alle anderen Argumente ignoriert, wenn `/stop` angegeben wurde. Geben Sie Folgendes ein, um z.B. die aktuelle Suche anzuhalten:

```
>Edit.FindinFiles /stop
```

 /sub oder /s ist optional. Durchsucht die Unterordner im Verzeichnis, das im Argument /lookin:`searchpath` angegeben wurde.

 /text2 oder /2 ist optional. Zeigt die Ergebnisse der Suche im Fenster „Suchergebnisse: 2“ an.

 /wild oder /l ist optional. Verwendet vordefinierte Sonderzeichen im `findwhat`-Argument als Notationen, um ein Zeichen oder eine Abfolge von Zeichen darzustellen.

 /word oder /w ist optional. Sucht nur nach ganzen Wörtern

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird nach „btnCancel“ in allen CLS-Dateien gesucht, die sich im Ordner „My Visual Studio Projects“ (Meine Visual Studio-Projekte) befinden. Die Ergebnisse werden im Fenster „Suchergebnisse: 2“ angezeigt.

```
>Edit.FindinFiles btnCancel /lookin:"c:/My Visual Studio Projects" /ext:*.cls /text2
```

## <a name="see-also"></a>Weitere Informationen
 [Suchen in Dateien](../../ide/find-in-files.md) [Befehlsfenster](../../ide/reference/command-window.md) [Suchen/Befehlsfeld](../../ide/find-command-box.md) [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md) Visual Studio- [Befehls Aliase](../../ide/reference/visual-studio-command-aliases.md)
