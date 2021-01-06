---
title: Farbige Syntax in einem Legacy Sprachdienst Microsoft-Dokumentation
description: Erfahren Sie, wie Sie die farbige Syntax Farbgebung in einem Legacy Sprachdienst unterstützen, indem Sie einen Parser oder einen Scanner bereitstellen, der die Typen von lexikalischen Elementen oder Token identifizieren kann.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], syntax highlighting
- colorization, supporting in language services [managed package framework]
- syntax highlighting, supporting in language services [managed package framework]
- language services [managed package framework], colorization
ms.assetid: 1ca1736a-f554-42e4-a9c7-fe8c3c1717df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c51885e593fabffab80d11c930100f3cc719dff8
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877753"
---
# <a name="syntax-colorizing-in-a-legacy-language-service"></a>Einfärben der Syntax in einem Legacysprachdienst
Die farbliche Syntax Farbgebung ist eine Funktion, die bewirkt, dass unterschiedliche Elemente einer Programmiersprache in einer Quelldatei in unterschiedlichen Farben und Stilen angezeigt werden. Zur Unterstützung dieser Funktion müssen Sie einen Parser oder Scanner bereitstellen, der die Typen von lexikalischen Elementen oder Token in der Datei identifizieren kann. Viele Sprachen unterscheiden Schlüsselwörter, Trennzeichen (z. b. Klammern oder geschweifte Klammern) und Kommentare durch farbige Farbgebung.

 Legacy Sprachdienste werden als Teil eines VSPackages implementiert, aber die neuere Methode zum Implementieren von Sprachdienst Funktionen ist die Verwendung von MEF-Erweiterungen. Weitere Informationen finden Sie unter [Erweitern des Editors und der Sprachdienste](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Es wird empfohlen, dass Sie so bald wie möglich mit der Verwendung der neuen Editor-API beginnen. Dadurch wird die Leistung Ihres sprach Dienstanbieter verbessert, und Sie können die neuen Editor-Features nutzen.

## <a name="implementation"></a>Implementierung
 Zur Unterstützung der Farbgebung enthält das Managed Package Framework (MPF) die- <xref:Microsoft.VisualStudio.Package.Colorizer> Klasse, die die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> Schnittstelle implementiert. Diese Klasse interagiert mit einem <xref:Microsoft.VisualStudio.Package.IScanner> , um das Token und die Farben zu bestimmen. Weitere Informationen zu Scannern finden Sie unter [Legacy Sprachdienst Parser und Scanner](../../extensibility/internals/legacy-language-service-parser-and-scanner.md). Die <xref:Microsoft.VisualStudio.Package.Colorizer> -Klasse markiert dann jedes Zeichen des Tokens mit den Farbinformationen und gibt diese Informationen an den Editor zurück, in dem die Quelldatei angezeigt wird.

 Die an den Editor zurückgegebenen Farbinformationen sind ein Index in einer Liste von Kolb baren Elementen. Jedes Kolon-Element gibt einen Farbwert und einen Satz von Schriftart Attributen an, z. b. Fett oder durchgestrichen. Der Editor stellt eine Reihe von standardmäßigen Kolon-Elementen bereit, die von Ihrem Sprachdienst verwendet werden können. Sie müssen lediglich den passenden Farbindex für jeden Tokentyp angeben. Sie können jedoch eine Reihe von benutzerdefinierten Kolon-Elementen und die Indizes bereitstellen, die Sie für Token bereitstellen, und auf eine eigene Liste von kolatable-Elementen anstelle der Standardliste verweisen. Sie müssen auch den `RequestStockColors` Registrierungs Eintrag auf 0 festlegen (oder den `RequestStockColors` Eintrag überhaupt nicht angeben), um benutzerdefinierte Farben zu unterstützen. Sie können diesen Registrierungs Eintrag mit einem benannten Parameter für das <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> benutzerdefinierte Attribut festlegen. Weitere Informationen zum Registrieren eines sprach Dienstanbieter und zum Festlegen der zugehörigen Optionen finden Sie unter [Registrieren eines Legacy sprach Dienstanbieter](../../extensibility/internals/registering-a-legacy-language-service1.md).

## <a name="custom-colorable-items"></a>Benutzerdefinierte einfärbbare Elemente
 Um eigene, benutzerdefinierte Elemente anzugeben, müssen Sie die <xref:Microsoft.VisualStudio.Package.LanguageService.GetItemCount%2A> -Methode und die- <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorableItem%2A> Methode für die-Klasse überschreiben <xref:Microsoft.VisualStudio.Package.LanguageService> . Die erste Methode gibt die Anzahl der benutzerdefinierten Kolon-Elemente zurück, die vom Sprachdienst unterstützt werden, und das zweite Ruft das benutzerdefinierte Kolon-Element nach Index ab. Sie erstellen die Standardliste der benutzerdefinierten Kolon-Elemente. Im Konstruktor Ihres sprach dienstaners müssen Sie lediglich jedes kolamable-Element mit einem Namen angeben. Visual Studio behandelt automatisch den Fall, in dem der Benutzer einen anderen Satz von kolaktivibaren Elementen auswählt. Dieser Name wird im Dialogfeld " **Optionen** " auf der Eigenschaften Seite " **Schriftarten und Farben** " angezeigt (verfügbar über das Visual Studio-Menü " **Tools** "), und dieser Name bestimmt, welche Farbe ein Benutzer überschrieben hat. Die Auswahl des Benutzers wird in einem Cache in der Registrierung gespeichert, und der Zugriff erfolgt über den Farbnamen. Auf der Eigenschaften Seite **Schriftarten und Farben** werden alle Farbnamen in alphabetischer Reihenfolge aufgelistet, sodass Sie Ihre benutzerdefinierten Farben gruppieren können, indem Sie die einzelnen Farbnamen mit Ihrem Sprachnamen vorangestellt haben. Beispiel: "**testlanguage-Comment**" und "**testlanguage-Keywords**". Oder Sie können die färb baren Elemente nach dem Typ "**comment (testlanguage)**" und "**Keyword (testlanguage)**" gruppieren. Die Gruppierung nach sprach Name wird bevorzugt.

> [!CAUTION]
> Es wird dringend empfohlen, dass Sie den Namen der Sprache in den Namen des kolamable-Elements einschließen, um Konflikte mit vorhandenen färb baren Elementnamen zu vermeiden.

> [!NOTE]
> Wenn Sie den Namen einer ihrer Farben während der Entwicklung ändern, müssen Sie den Cache, den Visual Studio beim ersten Zugriff auf Ihre Farben erstellt hat, zurücksetzen. Führen Sie hierzu den Befehl **experimentelle Hive zurücksetzen** im Visual Studio SDK-Programm Menü aus.

 Beachten Sie, dass nie auf das erste Element in der Liste der Kolon-Elemente verwiesen wird. Visual Studio stellt immer die Standardtext Farben und-Attribute für das Element bereit. Die einfachste Möglichkeit, damit umzugehen, besteht darin, einen Platzhalter für das als erstes Element aktivierbare Element anzugeben.

### <a name="high-color-colorable-items"></a>Farbbare Elemente mit hoher Farbe
 Färb Bare Elemente können auch über die-Schnittstelle 24-Bit-oder hohe Farbwerte unterstützen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> . Die MPF <xref:Microsoft.VisualStudio.Package.ColorableItem> -Klasse unterstützt die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> -Schnittstelle, und die 24-Bit-Farben werden im Konstruktor zusammen mit den normalen Farben angegeben. Weitere Informationen finden Sie in den Ausführungen zur <xref:Microsoft.VisualStudio.Package.ColorableItem>-Klasse. Im folgenden Beispiel wird gezeigt, wie die 24-Bit-Farben für Schlüsselwörter und Kommentare festgelegt werden. Die 24-Bit-Farben werden verwendet, wenn die 24-Bit-Farbe auf dem Desktop des Benutzers unterstützt wird. Andernfalls werden die normalen Textfarben verwendet.

 Beachten Sie, dass es sich hierbei um die Standardfarben für Ihre Sprache handelt. der Benutzer kann diese Farben in alle gewünschten Farben ändern.

### <a name="example"></a>Beispiel
 Dieses Beispiel zeigt eine Möglichkeit zum Deklarieren und Auffüllen eines Arrays benutzerdefinierter kolatable-Elemente mithilfe der- <xref:Microsoft.VisualStudio.Package.ColorableItem> Klasse. In diesem Beispiel werden das Schlüsselwort und die Kommentar Farben mit 24-Bit-Farben festgelegt.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        private ColorableItem[] m_colorableItems;

        TestLanguageService() : base()
        {
            m_colorableItems = new ColorableItem[] {
                new ColorableItem("TestLanguage - Text",
                                  "Text",
                                  COLORINDEX.CI_SYSPLAINTEXT_FG,
                                  COLORINDEX.CI_SYSPLAINTEXT_BK,
                                  System.Drawing.Color.Empty,
                                  System.Drawing.Color.Empty,
                                  FONTFLAGS.FF_DEFAULT),
                new ColorableItem("TestLanguage - Keyword",
                                  "Keyword",
                                  COLORINDEX.CI_MAROON,
                                  COLORINDEX.CI_SYSPLAINTEXT_BK,
                                  System.Drawing.Color.FromArgb(192,32,32),
                                  System.Drawing.Color.Empty,
                                  FONTFLAGS.FF_BOLD),
                new ColorableItem("TestLanguage - Comment",
                                  "Comment",
                                  COLORINDEX.CI_DARKGREEN,
                                  COLORINDEX.CI_LIGHTGRAY,
                                  System.Drawing.Color.FromArgb(32,128,32),
                                  System.Drawing.Color.Empty,
                                  FONTFLAGS.FF_DEFAULT)
                // ...
                // Add as many colorable items as you want to support.
            };
        }
    }
}
```

## <a name="the-colorizer-class-and-the-scanner"></a>Die colorzer-Klasse und die Scanner
 Die-Basis <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse verfügt über eine- <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorizer%2A> Methode, die die-Klasse instanziiert <xref:Microsoft.VisualStudio.Package.Colorizer> . Der Scanner, der von der-Methode zurückgegeben wird, <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> wird an den- <xref:Microsoft.VisualStudio.Package.Colorizer> Klassenkonstruktor übergeben.

 Sie müssen die- <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> Methode in ihrer eigenen Version der- <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse implementieren. Die- <xref:Microsoft.VisualStudio.Package.Colorizer> Klasse verwendet den Scanner, um alle tokenfarbinformationen abzurufen.

 Der Scanner muss eine <xref:Microsoft.VisualStudio.Package.TokenInfo> Struktur für jedes Token auffüllen, das er findet. Diese Struktur enthält Informationen, wie z. b. die Spanne, die das Token einnimmt, den zu verwendenden Farb Index, den Typ des Tokens und tokentrigger (siehe <xref:Microsoft.VisualStudio.Package.TokenTriggers> ). Nur der Span-und Color-Index ist für die farbliche Farbgebung durch die- <xref:Microsoft.VisualStudio.Package.Colorizer> Klasse erforderlich.

 Der in der Struktur gespeicherte Farbindex ist in der <xref:Microsoft.VisualStudio.Package.TokenInfo> Regel ein Wert aus der- <xref:Microsoft.VisualStudio.Package.TokenColor> Enumeration, der eine Reihe von benannten Indizes bereitstellt, die verschiedenen Sprachelementen, z. b. Schlüsselwörtern und Operatoren, entsprechen. Wenn die Liste der benutzerdefinierten färb baren Elemente mit den in der-Enumeration dargestellten Elementen übereinstimmt <xref:Microsoft.VisualStudio.Package.TokenColor> , können Sie einfach die-Enumeration als Farbe für jedes Token verwenden. Wenn Sie jedoch über zusätzliche färb Bare Elemente verfügen oder die vorhandenen Werte in dieser Reihenfolge nicht verwenden möchten, können Sie die Liste der benutzerdefinierten Kolon-Elemente Ihren Anforderungen entsprechend anordnen und den entsprechenden Index in diese Liste zurückgeben. Stellen Sie einfach sicher, dass Sie den Index in einen umwandeln, <xref:Microsoft.VisualStudio.Package.TokenColor> Wenn Sie ihn in der Struktur speichern. es wird <xref:Microsoft.VisualStudio.Package.TokenInfo> [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] nur der Index angezeigt.

### <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt, wie der Scanner drei Tokentypen identifizieren kann: Zahlen, Interpunktions Zeichen und Bezeichner (alles, was keine Zahl oder Satzzeichen ist). Dieses Beispiel dient nur zu Illustrations Zwecken und stellt keine umfassende Parser-und Scanner-Implementierung dar. Es wird davon ausgegangen, dass eine- `Lexer` Klasse mit einer-Methode vorhanden ist `GetNextToken()` , die eine Zeichenfolge zurückgibt

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    private Lexer lex;

    public class TestScanner : IScanner
    {
        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,
                                                   ref int state)
        {
            bool foundToken = false;
            string token = lex.GetNextToken();
            if (token != null)
            {
                char firstChar = token[0];
                if (Char.IsPunctuation(firstChar))
                {
                    tokenInfo.Type = TokenType.Operator;
                    tokenInfo.Color = TokenColor.Keyword;
                }
                else if (Char.IsNumber(firstChar))
                {
                    tokenInfo.Type = TokenType.Literal;
                    tokenInfo.Color = TokenColor.Number;
                }
                else
                {
                    tokenInfo.Type = TokenType.Identifier;
                    tokenInfo.Color = TokenColor.Identifier;
                }
            }
            return foundToken;
        }
```

## <a name="see-also"></a>Weitere Informationen
- [Funktionen von Legacysprachdiensten](../../extensibility/internals/legacy-language-service-features1.md)
- [Parser und Scanner von Legacysprachdiensten](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
- [Registrieren eines Legacysprachdiensts](../../extensibility/internals/registering-a-legacy-language-service1.md)
