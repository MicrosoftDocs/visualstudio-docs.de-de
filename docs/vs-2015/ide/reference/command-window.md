---
title: Befehlsfenster | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.CommandWindow
helpviewer_keywords:
- IDE, Command window
- Mark mode in Command window
- Command window
- Command mode in Command window
- IDE Command window
ms.assetid: 48711628-1909-4713-a73e-d7b714c77f8a
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0c3bcac9f320840faaed32d0622f30e4cbd288ea
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660846"
---
# <a name="command-window"></a>Befehlsfenster
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Das Fenster **Befehl** wird verwendet, um Befehle oder Aliase direkt in der integrierten Entwicklungsumgebung (IDE) von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] auszuführen. Sie können sowohl Menübefehle als auch Befehle ausführen, die in keinem Menü angezeigt werden. Wählen Sie zum Anzeigen des Fensters **Befehl** im Menü **Ansicht** den Befehl **Weitere Fenster** aus, und klicken Sie dann auf **Befehlsfenster**.

## <a name="displaying-the-values-of-variables"></a>Anzeigen der Werte von Variablen
 Verwenden Sie den [Befehl „Drucken“](../../ide/reference/print-command.md), um den Wert einer Variablen `varA` zu überprüfen:

```
>Debug.Print varA
```

 Das Fragezeichen (?) ist ein Alias für `Debug.Print`, sodass dieser Befehl auch wie folgt eingegeben werden kann:

```
>? varA
```

 Beide Versionen dieses Befehls geben den Wert der Variablen `varA` zurück.

## <a name="entering-commands"></a>Eingeben von Befehlen
 Am linken Rand des Befehlsfensters wird das Größer-als-Zeichen (`>`) als Eingabeaufforderung für neue Zeilen angezeigt. Verwenden Sie die NACH-OBEN- und NACH UNTEN-TASTEN, um einen Bildlauf durch bereits ausgegebene Befehle durchzuführen.

|Aufgabe|Lösung|Beispiel|
|----------|--------------|-------------|
|Auswerten eines Ausdrucks.|Stellen Sie dem Ausdruck ein Fragezeichen (`?`) voran.|`? myvar`|
|Wechseln Sie zu einem Direktfenster.|Geben Sie in das Fenster `immed` ohne das Größer-als-Zeichen (>) ein.|`immed`|
|Wechseln Sie wieder vom Direktfenster zum Befehlsfenster.|Geben Sie `cmd` in das Fenster ein.|`>cmd`|

 Die folgenden Tastenkombinationen erleichtern Ihnen die Navigation im Befehlsmodus.

|Aktion|Cursorplatzierung|Schlüsselbindung|
|------------|---------------------|----------------|
|Der Reihe nach durch die Liste der zuvor eingegebenen Befehle wechseln|Eingabezeile|NACH-OBEN- & NACH-UNTEN-TASTE|
|Im Fenster einen Bildlauf nach oben durchführen|Inhalt im Befehlsfenster|STRG+NACH-OBEN|
|Im Fenster einen Bildlauf nach unten durchführen|Inhalt im Befehlsfenster|NACH-UNTEN oder STRG+NACH-UNTEN|

> [!TIP]
> Sie können den zuvor ausgegebenen Befehl ganz oder teilweise in die Eingabezeile kopieren, indem Sie einen Bildlauf dorthin durchführen, den Befehl ganz oder teilweise hervorheben und dann die EINGABETASTE drücken.

## <a name="mark-mode"></a>Markierungsmodus
 Wenn Sie im Fenster **Befehl** auf eine zuvor ausgegebene Zeile klicken, schalten Sie automatisch in den Markierungsmodus um. Auf diese Weise können Sie den Text vorheriger Befehle wie in einem beliebigen anderen Text-Editor markieren, bearbeiten, kopieren und in die aktuelle Zeile einfügen.

## <a name="the-equals--sign"></a>Gleichheitszeichen (=)
 Abhängig vom Fenster, das zur Eingabe des `EvaluateStatement`-Befehls verwendet wird, wird ein Gleichheitszeichen (=) als Vergleichsoperator oder als Zuweisungsoperator interpretiert.

 Im Fenster **Befehl** wird ein Gleichheitszeichen (=) als Vergleichsoperator interpretiert. Sie können keine Zuweisungsoperatoren im Fenster **Befehl** verwenden. Wenn die Werte der Variablen `varA` und `varB` beispielsweise unterschiedlich sind, gibt der Befehl

```
>Debug.EvaluateStatement(varA=varB)
```

 den Wert `False` zurück.

 Im Fenster **Direkt** wird ein Gleichheitszeichen (=) dagegen als Zuweisungsoperator interpretiert. Daher wird mit dem Befehl

```
>Debug.EvaluateStatement(varA=varB)
```

 der Variablen `varA` der Wert von Variable `varB` zugewiesen.

## <a name="parameters-switches-and-values"></a>Parameter, Schalter und Werte
 Einige [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]-Befehle verfügen über erforderliche und optionale Argumente, Schalter und Werte. Für die Verwendung dieser Befehle gelten bestimmte Regeln. Im folgenden Beispiel wird ein umfangreicher Befehl gezeigt, um die Terminologie zu verdeutlichen.

```
Edit.ReplaceInFiles /case /pattern:regex var[1-3]+ oldpar
```

 In diesem Beispiel

- `Edit.ReplaceInFiles` der Befehl,

- `/case` und `/pattern:regex` sind Schalter (eingeleitet mit dem Schrägstrich [/]),

- `regex` der Wert des `/pattern`-Schalters (der `/case`-Schalter weist keinen Wert auf), und

- `var[1-3]+` sowie `oldpar` sind Parameter.

  > [!NOTE]
  > Jeder Befehl, Parameter, Schalter oder Wert, der Leerzeichen enthält, muss in doppelte Anführungszeichen eingeschlossen werden.

  Die Position von Schaltern und Parametern kann im Allgemeinen frei auf der Befehlszeile kombiniert werden, mit Ausnahme des [Shell](../../ide/reference/shell-command.md)-Befehls, für den eine bestimmte Reihenfolge der Schalter und Parameter erforderlich ist.

  Nahezu jeder von einem Befehl unterstützte Schalter verfügt über zwei Formen: eine kurze Form, bestehend aus einem Buchstaben, und eine lange Form. Mehrere Schalter in kurzer Form können zu einer Gruppe zusammengefasst werden. Beispielsweise kann `/p /g /m` alternativ auch als `/pgm` ausgedrückt werden.

  Wenn Schalter in Kurzform zu einer Gruppe zusammengefasst und mit einem Wert versehen werden, bezieht sich dieser Wert auf jeden der Schalter. Beispielsweise ist `/pgm:123` gleichbedeutend mit `/p:123 /g:123 /m:123`. Es tritt ein Fehler auf, wenn einer der Schalter in der Gruppe keinen Wert annimmt.

## <a name="escape-characters"></a>Escapezeichen
 Ein Caretzeichen (^) in einer Befehlszeile bedeutet, dass das unmittelbar darauf folgende Zeichen literal und nicht als Steuerzeichen interpretiert wird. Dies ermöglicht das Einbetten von geraden Anführungszeichen ("), Leerzeichen, vorangestellten Schrägstrichen, Caretzeichen oder beliebigen anderen Literalzeichen in einen Parameter- oder Schalterwert, mit Ausnahme von Schalternamen. Beispiel:

```
>Edit.Find ^^t /regex
```

 Die Funktionsweise des Caretzeichens ist unabhängig davon, ob es in Anführungszeichen eingeschlossen ist oder nicht. Wenn ein Caretzeichen das letzte Zeichen in einer Zeile ist, wird es ignoriert. Im hier gezeigten Beispiel wird die Suche nach dem Muster "^t" veranschaulicht.

## <a name="use-quotes-for-path-names-with-spaces"></a>Verwenden von Anführungszeichen für Pfadnamen mit Leerzeichen
 Wenn Sie beispielsweise eine Datei öffnen möchten, die über einen Pfad mit Leerzeichen verfügt, müssen Sie den Pfad oder das Pfadsegment, das Leerzeichen enthält, in doppelte Anführungszeichen einschließen: **C:\\"Eigene Dateien"** oder **"C:\Eigene Dateien"**.

## <a name="see-also"></a>Weitere Informationen
 [Visual Studio-Befehls Aliase](../../ide/reference/visual-studio-command-aliases.md) [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
