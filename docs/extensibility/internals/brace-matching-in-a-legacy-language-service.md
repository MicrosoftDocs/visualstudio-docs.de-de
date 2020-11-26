---
title: Übereinstimmung von Klammern in einem Legacy Sprachdienst | Microsoft-Dokumentation
description: Erfahren Sie mehr über das Abgleichen von Klammern in einem Legacy Sprachdienst, mit dem Sie Sprachelemente nachverfolgen können, die in der Regel auftreten müssen, z. b. Klammern und geschweifte Klammern.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- brace matching
- language services [managed package framework], brace matching
ms.assetid: 4e3d0a70-f22f-49dd-92d8-edf48ab62b52
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7d9f93f0081d45e986ab6845cdaee53209b84e13
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2020
ms.locfileid: "96190004"
---
# <a name="brace-matching-in-a-legacy-language-service"></a>Übereinstimmung von Klammern in einem Legacy Sprachdienst
Mit der Übereinstimmung mit geschweiften Klammern können Entwickler Sprachelemente nachverfolgen, die gleichzeitig auftreten müssen, z. b. Klammern und geschweifte Klammern. Wenn ein Entwickler eine schließende geschweifte Klammer eingibt, wird die öffnende geschweifte Klammer hervorgehoben.

 Sie können zwei oder drei zusammen vorkommende Elemente, die als Paare und Paare bezeichnet werden, vergleichen. Dreipel sind Sätze von drei nebeneinander vorkommenden Elementen. In c# `foreach` bildet die-Anweisung z. b. ein Triple: `foreach()` , `{` und `}` . Alle drei Elemente werden hervorgehoben, wenn die schließende geschweifte Klammer eingegeben wird.

 Legacy Sprachdienste werden als Teil eines VSPackages implementiert, aber die neuere Methode zum Implementieren von Sprachdienst Funktionen ist die Verwendung von MEF-Erweiterungen. Weitere Informationen zur neuen Methode zum Implementieren der geschweiften Klammer finden Sie unter Exemplarische Vorgehensweise [: anzeigen übereinstimmender](../../extensibility/walkthrough-displaying-matching-braces.md)geschweifter Klammern.

> [!NOTE]
> Es wird empfohlen, dass Sie so bald wie möglich mit der Verwendung der neuen Editor-API beginnen. Dadurch wird die Leistung Ihres sprach Dienstanbieter verbessert, und Sie können die neuen Editor-Features nutzen.

 Die <xref:Microsoft.VisualStudio.Package.AuthoringSink> -Klasse unterstützt sowohl Paare als auch mit der <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchPair%2A> -Methode und der- <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchTriple%2A> Methode.

## <a name="implementation"></a>Implementierung
 Der Sprachdienst muss alle übereinstimmenden Elemente in der Sprache identifizieren und dann alle übereinstimmenden Paare finden. Dies wird in der Regel durch Implementieren von <xref:Microsoft.VisualStudio.Package.IScanner> zum Erkennen einer übereinstimmenden Sprache und anschließendes Verwenden der- <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode zum Abgleichen der Elemente erreicht.

 Die <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> -Methode ruft den Scanner auf, um die Zeile zu tokenten und das Token direkt vor der Einfügemarke zurückzugeben. Der Scanner gibt an, dass ein sprach Element paar gefunden wurde, indem ein tokenauslöserwert von <xref:Microsoft.VisualStudio.Package.TokenTriggers> für das aktuelle Token festgelegt wurde. Die- <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Methode ruft die- <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> Methode auf, die wiederum die- <xref:Microsoft.VisualStudio.Package.LanguageService.BeginParse%2A> Methode mit dem Wert der Analyse Ursache von aufruft <xref:Microsoft.VisualStudio.Package.ParseReason> , um das entsprechende sprach Element zu suchen. Wenn das übereinstimmende sprach Element gefunden wird, werden beide Elemente hervorgehoben.

 Eine umfassende Beschreibung der Art und Weise, wie die Eingabe einer geschweifter Klammer die geschweifter Klammer auslöst, finden Sie im Abschnitt *analysieren Operation (Beispiel Analyse Vorgang* ) im Artikel [Legacy-Sprachdienst Parser und Scanner](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).

## <a name="enable-support-for-brace-matching"></a>Unterstützung für übereinstimmende Klammern aktivieren
 Mit dem <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> -Attribut können die Registrierungseinträge **matchgeschweiften**, **matchbracesatcaret** und **showmatchingbrace** festgelegt werden, mit denen die entsprechenden Eigenschaften der-Klasse festgelegt werden <xref:Microsoft.VisualStudio.Package.LanguagePreferences> . Die Eigenschaften der Spracheinstellungen können auch vom Benutzer festgelegt werden.

|Registrierungseintrag|Eigenschaft|BESCHREIBUNG|
|--------------------|--------------|-----------------|
|Matchgeschweifte Klammern|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBraces%2A>|Aktiviert die Übereinstimmung mit Klammern.|
|Matchbracesatcaret|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBracesAtCaret%2A>|Aktiviert die geschweifter Klammer, wenn die Einfügemarke verschoben wird.|
|Showmatchingbrace|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>|Hebt die zugehörige Klammer hervor.|

## <a name="match-conditional-statements"></a>Abgleichen von Bedingungs Anweisungen
 Sie können Bedingungs Anweisungen, wie z `if` . b `else if` .,, und `else` oder `#if` , `#elif` ,, `#else` `#endif` auf die gleiche Weise wie übereinstimmende Trennzeichen vergleichen. Sie können die <xref:Microsoft.VisualStudio.Package.AuthoringSink> -Klasse Unterklassen und eine Methode bereitstellen, mit der Text Spannen und Trennzeichen dem internen Array von übereinstimmenden Elementen hinzugefügt werden können.

## <a name="set-the-trigger"></a>Festlegen des Auslösers
 Im folgenden Beispiel wird gezeigt, wie Sie übereinstimmende Klammern, geschweifte Klammern und eckige Klammern erkennen und den Trigger dafür im Scanner festlegen. Die <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> -Methode für die <xref:Microsoft.VisualStudio.Package.Source> -Klasse erkennt den-Aufruf und ruft den Parser auf, um das passende paar zu finden (Weitere Informationen finden Sie im Abschnitt Suchen *der Übereinstimmung* in diesem Artikel). Dieses Beispiel dient nur zu Illustrations Zwecken. Dabei wird davon ausgegangen, dass der Scanner eine Methode enthält `GetNextToken` , die Token aus einer Textzeile identifiziert und zurückgibt.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestScanner : IScanner
    {
        private const string braces = "()[]{}";
        private Lexer lex;

        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,
                                                   ref int state)
        {
            bool foundToken = false;
            string token = lex.GetNextToken();
            if (token != null)
            {
                foundToken = true;
                char firstChar = token[0];
                if (Char.IsPunctuation(firstChar) && token.Length > 0)
                {
                    if (braces.IndexOf(firstChar) != -1)
                    {
                        tokenInfo.Trigger = TokenTriggers.MatchBraces;
                    }
                }
            }
            return foundToken;
        }
```

## <a name="match-the-braces"></a>Mit geschweiften Klammern vergleichen
 Im folgenden finden Sie ein vereinfachtes Beispiel für das Abgleichen der Sprachelemente `{ }` , `( )` und `[ ]` und das Hinzufügen Ihrer spannen zum- <xref:Microsoft.VisualStudio.Package.AuthoringSink> Objekt. Diese Vorgehensweise wird nicht empfohlen, um Quellcode zu übernehmen. Sie dient nur zu Illustrations Zwecken.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class Parser
    {
         private IList<TextSpan[]> m_braces;
         public IList<TextSpan[]> Braces
         {
             get { return m_braces; }
         }
         private void AddMatchingBraces(TextSpan braceSpan1, TextSpan braceSpan2)
         {
             if IsMatch(braceSpan1, braceSpan2)
                 m_braces.Add(new TextSpan[] { braceSpan1, braceSpan2 });
         }

         private bool IsMatch(TextSpan braceSpan1, TextSpan braceSpan2)
         {
             //definition for matching here
          }
    }

    public class TestLanguageService : LanguageService
    {
         Parser parser = new Parser();
         Source source = (Source) this.GetSource(req.FileName);

         private AuthoringScope ParseSource(ParseRequest req)
         {
             if (req.Sink.BraceMatching)
             {
                 if (req.Reason==ParseReason.MatchBraces)
                 {
                     foreach (TextSpan[] brace in parser.Braces)
                     {
                         req.Sink.MatchPair(brace[0], brace[1], 1);
                     }
                 }
             }
             return new TestAuthoringScope();
         }
    }
}
```

## <a name="see-also"></a>Weitere Informationen
- [Funktionen von Legacy Sprachdiensten](../../extensibility/internals/legacy-language-service-features1.md)
- [Parser und Scanner des Legacy sprach Dienstanbieter](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
