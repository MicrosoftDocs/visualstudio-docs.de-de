---
title: Parameter Informationen in einer Legacy Sprache Service2 | Microsoft-Dokumentation
description: Erfahren Sie, wie der IntelliSense-Parameter Info-Vorgang zum Anzeigen einer Methoden Signatur unterstützt wird, wenn die-Methode in einem Legacy Sprachdienst eingegeben wird.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense, Parameter Info tool tip
- language services [managed package framework], IntelliSense Parameter Info
- Parameter Info (IntelliSense), supporting in language services [managed package framework]
ms.assetid: a117365d-320d-4bb5-b61d-3e6457b8f6bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fc239d5b0d580d420683c6940ac2bbd5198335d7
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97875946"
---
# <a name="parameter-info-in-a-legacy-language-service-2"></a>Parameter Informationen in einem Legacy Sprachdienst 2
IntelliSense-Parameter Info ist eine QuickInfo, die die Signatur einer Methode anzeigt, wenn der Benutzer das Parameter Listen-Startzeichen (in der Regel eine öffnende Klammer) für die Methoden Parameter Liste eingibt. Wenn jeder Parameter eingegeben und das Parameter Trennzeichen (in der Regel ein Komma) eingegeben wird, wird die QuickInfo aktualisiert, um den nächsten Parameter fett anzuzeigen.

 Die MPF-Klassen (Managed Package Framework) unterstützen die Verwaltung der QuickInfo-Parameter info. Der Parser muss Parameter Start-, Parameter-Next-und Parameter Endzeichen erkennen, und er muss eine Liste der Methoden Signaturen und der zugehörigen Parameter angeben.

 Legacy Sprachdienste werden als Teil eines VSPackages implementiert, aber die neuere Methode zum Implementieren von Sprachdienst Funktionen ist die Verwendung von MEF-Erweiterungen. Weitere Informationen finden Sie unter [Erweitern des Editors und der Sprachdienste](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Es wird empfohlen, dass Sie so bald wie möglich mit der Verwendung der neuen Editor-API beginnen. Dadurch wird die Leistung Ihres sprach Dienstanbieter verbessert, und Sie können die neuen Editor-Features nutzen.

## <a name="implementation"></a>Implementierung
 Der Parser sollte festlegen, dass der Wert des Auslösers <xref:Microsoft.VisualStudio.Package.TokenTriggers> festgelegt wird, wenn er ein Startzeichen für eine Parameterliste findet (häufig eine öffnende Klammer). Sie sollte einen- <xref:Microsoft.VisualStudio.Package.TokenTriggers> Parameter festlegen, wenn ein Parameter Trennzeichen (häufig ein Komma) gefunden wird. Dies bewirkt, dass die QuickInfo für die Parameter Info aktualisiert und der nächste Parameter fett angezeigt wird. Der Parser sollte den Wert des Auslösers festlegen, wenn <xref:Microsoft.VisualStudio.Package.TokenTriggers> der das Parameterlisten-Endzeichen findet (häufig eine schließende Klammer).

 Der <xref:Microsoft.VisualStudio.Package.TokenTriggers> Triggerwert initiiert einen Aufruf der- <xref:Microsoft.VisualStudio.Package.Source.MethodTip%2A> Methode, die wiederum den <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methoden Parser mit einer analysieren-Ursache von aufruft <xref:Microsoft.VisualStudio.Package.ParseReason> . Wenn der Parser feststellt, dass der Bezeichner vor dem Startzeichen der Parameterliste ein bekannter Methodenname ist, wird eine Liste der übereinstimmenden Methoden Signaturen im-Objekt zurückgegeben <xref:Microsoft.VisualStudio.Package.AuthoringScope> . Wenn Methoden Signaturen gefunden wurden, wird die QuickInfo für die Parameter Info mit der ersten Signatur in der Liste angezeigt. Diese QuickInfo wird dann aktualisiert, sobald mehr Signatur eingegeben wurde. Wenn das Parameterlisten-Endzeichen eingegeben wird, wird die QuickInfo für die Parameter Info aus der Ansicht entfernt.

> [!NOTE]
> Um sicherzustellen, dass die QuickInfo für die QuickInfo ordnungsgemäß formatiert ist, müssen Sie die Eigenschaften der Klasse überschreiben, <xref:Microsoft.VisualStudio.Package.Methods> um die entsprechenden Zeichen bereitzustellen. Die Basis <xref:Microsoft.VisualStudio.Package.Methods> Klasse geht von einer Methoden Signatur im c#-Stil aus. Ausführliche Informationen zur Vorgehensweise finden Sie in der- <xref:Microsoft.VisualStudio.Package.Methods> Klasse.

## <a name="enabling-support-for-the-parameter-info"></a>Aktivieren der Unterstützung für die Parameter Informationen
 Um Quick Infos für Parameter Info zu unterstützen, müssen Sie den `ShowCompletion` benannten Parameter von <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> auf festlegen `true` . Der Sprachdienst liest den Wert dieses Registrierungs Eintrags aus der- <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> Eigenschaft.

 Außerdem muss die- <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ParameterInformation%2A> Eigenschaft auf festgelegt werden, `true` damit die QuickInfo für die Parameter angezeigt wird.

### <a name="example"></a>Beispiel
 Im folgenden finden Sie ein vereinfachtes Beispiel für das Erkennen der Parameterlisten Zeichen und das Festlegen der entsprechenden Trigger. Dieses Beispiel dient nur zu Illustrations Zwecken. Dabei wird davon ausgegangen, dass der Scanner eine Methode enthält `GetNextToken` , die Token aus einer Textzeile identifiziert und zurückgibt. Der Beispielcode legt die Trigger einfach fest, wenn Sie die richtige Art von Zeichen sehen.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestScanner : IScanner
    {
        private Lexer lex;
        private const char parameterListStartChar = '(';
        private const char parameterListEndChar   = ')';
        private const char parameterNextChar      = ',';

        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,
                                                   ref int state)
        {
            bool foundToken = false
            string token = lex.GetNextToken();
            if (token != null)
            {
                foundToken = true;
                char c = token[0];
                if (Char.IsPunctuation(c))
                {
                    tokenInfo.Type = TokenType.Operator;
                    tokenInfo.Color = TokenColor.Keyword;
                    tokenInfo.EndIndex = index;

                    if (c == parameterListStartChar)
                    {
                        tokenInfo.Trigger |= TokenTriggers.ParameterStart;
                    }
                    else if (c == parameterListNextChar)
                    {
                        tokenInfo.Trigger |= TokenTriggers.ParameterNext;
                    else if (c == parameterListEndChar)
                    {
                        tokenInfo.Trigger |= TokenTriggers.ParameterEnd;
                    }
                }
            return foundToken;
        }
    }
}
```

## <a name="supporting-the-parameter-info-tooltip-in-the-parser"></a>Unterstützen der QuickInfo-Parameter Info im Parser
 Die <xref:Microsoft.VisualStudio.Package.Source> -Klasse macht einige Annahmen über den Inhalt der <xref:Microsoft.VisualStudio.Package.AuthoringScope> -Klasse und der-Klasse, <xref:Microsoft.VisualStudio.Package.AuthoringSink> Wenn die QuickInfo für die Parameter Info angezeigt und aktualisiert wird.

- Der Parser wird angegeben, <xref:Microsoft.VisualStudio.Package.ParseReason> Wenn das Parameterlisten-Startzeichen eingegeben wird.

- Der im-Objekt angegebene Speicherort <xref:Microsoft.VisualStudio.Package.ParseRequest> ist unmittelbar nach dem Startzeichen der Parameterliste. Der Parser muss die Signaturen aller Methoden Deklarationen erfassen, die an dieser Position verfügbar sind, und Sie in einer Liste in Ihrer Version des <xref:Microsoft.VisualStudio.Package.AuthoringScope> Objekts speichern. Diese Liste enthält den Methodennamen, den Methodentyp (oder Rückgabetyp) und eine Liste möglicher Parameter. Diese Liste wird später nach der Methoden Signatur oder den Signaturen durchsucht, die in der QuickInfo für die Parameter Info angezeigt werden sollen.

  Der Parser muss dann die durch das-Objekt angegebene Zeile analysieren <xref:Microsoft.VisualStudio.Package.ParseRequest> , um den Namen der eingegebenen Methode zu erfassen und zu erfahren, wie weit der Benutzer in der Eingabe von Parametern ist. Dies wird erreicht, indem der Name der Methode an die <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> -Methode des <xref:Microsoft.VisualStudio.Package.AuthoringSink> -Objekts übergeben und dann die- <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A> Methode aufgerufen wird, wenn das Startzeichen der Parameterliste analysiert wird. dabei wird die-Methode aufgerufen, <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A> Wenn das nächste Zeichen in der Parameterliste analysiert wird, und schließlich wird die-Methode aufgerufen, <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A> Wenn das Endzeichen der Parameterliste analysiert wird. Die Ergebnisse dieser Methodenaufrufe werden von der- <xref:Microsoft.VisualStudio.Package.Source> Klasse verwendet, um die QuickInfo für die Parameter Informationen entsprechend zu aktualisieren.

### <a name="example"></a>Beispiel
 Hier ist eine Textzeile, die der Benutzer eingeben kann. Die Zahlen unterhalb der Zeile geben an, welcher Schritt vom Parser an dieser Position in der Zeile durchgeführt wird (vorausgesetzt, die Analyse wird von links nach rechts verschoben). Die Annahme besteht darin, dass alles, was vor der Zeile bereits für Methoden Signaturen, einschließlich der Methoden Signatur "testfunc", analysiert wurde.

```
testfunc("a string",3);
     ^^          ^ ^
     12          3 4
```

 Die Schritte, die der Parser durchführt, werden im folgenden beschrieben:

1. Der Parser ruft <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> mit dem Text "testfunc" auf.

2. Der Parser Ruft auf <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A> .

3. Der Parser Ruft auf <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A> .

4. Der Parser Ruft auf <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A> .
