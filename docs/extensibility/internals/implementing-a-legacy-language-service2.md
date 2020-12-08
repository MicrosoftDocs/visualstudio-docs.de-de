---
title: Implementieren eines Legacy sprach Service2 | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie mithilfe von Managed Package Framework (MPF) einen Legacy Sprachdienst implementieren, der erweiterte Sprachdienst Features unterstützt. Teil 2 von 2.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], implementing
ms.assetid: 5bcafdc5-f922-48f6-a12e-6c8507a79a05
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1a7da218a9ada593731e6205e017861084e73adc
ms.sourcegitcommit: 2f964946d7044cc7d49b3fc10b413ca06cb2d11b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2020
ms.locfileid: "96761139"
---
# <a name="implementing-a-legacy-language-service-2"></a>Implementieren eines Legacy sprach Dienstanbieter 2
Um einen Sprachdienst mithilfe von Managed Package Framework (MPF) zu implementieren, müssen Sie eine Klasse von der <xref:Microsoft.VisualStudio.Package.LanguageService> -Klasse ableiten und die folgenden abstrakten Methoden und Eigenschaften implementieren:

- Die <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> -Methode

- Die <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> -Methode

- Die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> -Methode

- Die <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A>-Eigenschaft.

  Ausführliche Informationen zur Implementierung dieser Methoden und Eigenschaften finden Sie in den entsprechenden Abschnitten.

  Um zusätzliche Funktionen zu unterstützen, muss Ihr Sprachdienst möglicherweise eine Klasse von einer der MPF-Sprachdienst Klassen ableiten. um z. b. zusätzliche Menübefehle zu unterstützen, müssen Sie eine Klasse von der <xref:Microsoft.VisualStudio.Package.ViewFilter> -Klasse ableiten und mehrere der Befehls Behandlungsmethoden überschreiben (Weitere Informationen finden Sie unter <xref:Microsoft.VisualStudio.Package.ViewFilter> ). Die <xref:Microsoft.VisualStudio.Package.LanguageService> -Klasse stellt eine Reihe von Methoden bereit, die aufgerufen werden, um neue Instanzen verschiedener Klassen zu erstellen, und Sie überschreiben die geeignete Erstellungs Methode, um eine Instanz der Klasse bereitzustellen. Beispielsweise müssen Sie die- <xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A> Methode in der- <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse überschreiben, um eine Instanz Ihrer eigenen-Klasse zurückzugeben <xref:Microsoft.VisualStudio.Package.ViewFilter> . Weitere Informationen finden Sie im Abschnitt "Instanziieren von benutzerdefinierten Klassen".

  Ihr Sprachdienst kann auch eigene Symbole bereitstellen, die an vielen Stellen verwendet werden. Wenn z. b. eine IntelliSense-Vervollständigungsliste angezeigt wird, kann jedem Element in der Liste ein Symbol zugeordnet sein, und das Element wird als Methode, Klasse, Namespace, Eigenschaft oder je nach den für Ihre Sprache erforderlichen Elementen gekennzeichnet. Diese Symbole werden in allen IntelliSense-Listen, in der **Navigationsleiste** und im Aufgaben Fenster **Fehlerliste** verwendet. Weitere Informationen finden Sie im Abschnitt "Sprachdienst Images" weiter unten.

## <a name="getlanguagepreferences-method"></a>GetLanguagePreferences-Methode
 Die- <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> Methode gibt immer die gleiche Instanz einer- <xref:Microsoft.VisualStudio.Package.LanguagePreferences> Klasse zurück. <xref:Microsoft.VisualStudio.Package.LanguagePreferences>Wenn Sie keine weiteren Einstellungen für Ihren Sprachdienst benötigen, können Sie die Basisklasse verwenden. Die MPF-Sprachdienst Klassen nehmen an, dass mindestens die Basis <xref:Microsoft.VisualStudio.Package.LanguagePreferences> Klasse vorhanden ist.

### <a name="example"></a>Beispiel
 Dieses Beispiel zeigt eine typische Implementierung der- <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> Methode. In diesem Beispiel wird die-Basis <xref:Microsoft.VisualStudio.Package.LanguagePreferences> Klasse verwendet.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        private LanguagePreferences m_preferences;

        public override LanguagePreferences GetLanguagePreferences()
        {
            if (m_preferences == null)
            {
                m_preferences = new LanguagePreferences(this.Site,
                                                        typeof(TestLanguageService).GUID,
                                                        this.Name );
                m_preferences.Init();
            }
            return m_preferences;
        }
    }
}
```

## <a name="getscanner-method"></a>GetScanner-Methode
 Diese Methode gibt eine Instanz eines <xref:Microsoft.VisualStudio.Package.IScanner> Objekts zurück, das einen zeilenorientierten Parser oder Scanner implementiert, der zum Abrufen von Token und ihrer Typen und Trigger verwendet wird. Dieser Scanner wird in der- <xref:Microsoft.VisualStudio.Package.Colorizer> Klasse für die farbliche Kennzeichnung verwendet, obwohl der Scanner auch zum Abrufen von Tokentypen und Triggern als Auftakt für einen komplexeren Verarbeitungsvorgang verwendet werden kann. Sie müssen die Klasse angeben, die die <xref:Microsoft.VisualStudio.Package.IScanner> -Schnittstelle implementiert, und Sie müssen alle Methoden für die- <xref:Microsoft.VisualStudio.Package.IScanner> Schnittstelle implementieren.

### <a name="example"></a>Beispiel
 Dieses Beispiel zeigt eine typische Implementierung der- <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> Methode. Die- `TestScanner` Klasse implementiert die- <xref:Microsoft.VisualStudio.Package.IScanner> Schnittstelle (nicht angezeigt).

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        private TestScanner m_scanner;

        public override IScanner GetScanner(IVsTextLines buffer)
        {
            if (m_scanner == null)
            {
                m_scanner = new TestScanner(buffer);
            }
            return m_scanner;
        }
    }
}
    internal class TestScanner : IScanner
    {
        private IVsTextBuffer m_buffer;
        string m_source;

        public TestScanner(IVsTextBuffer buffer)
        {
            m_buffer = buffer;
        }

        bool IScanner.ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo, ref int state)
        {
            tokenInfo.Type = TokenType.Unknown;
            tokenInfo.Color = TokenColor.Text;
            return true;
        }

        void IScanner.SetSource(string source, int offset)
        {
            m_source = source.Substring(offset);
        }
    }

```

## <a name="parsesource-method"></a>Methode "paramesesource"
 Analysiert die Quelldatei basierend auf einer Reihe von verschiedenen Gründen. Diese Methode erhält ein- <xref:Microsoft.VisualStudio.Package.ParseRequest> Objekt, das beschreibt, was von einem bestimmten Verarbeitungsvorgang erwartet wird. Die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> -Methode ruft einen komplexeren Parser auf, der die Tokenfunktionalität und den Bereich bestimmt. Die- <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode wird für die Unterstützung von IntelliSense-Vorgängen sowie für übereinstimmende Klammern verwendet. Auch wenn Sie solche erweiterten Vorgänge nicht unterstützen, müssen Sie immer noch ein gültiges <xref:Microsoft.VisualStudio.Package.AuthoringScope> -Objekt zurückgeben, das erfordert, dass Sie eine Klasse erstellen, die die <xref:Microsoft.VisualStudio.Package.AuthoringScope> -Schnittstelle implementiert und alle Methoden für diese Schnittstelle implementiert. Sie können NULL-Werte von allen Methoden zurückgeben, aber das <xref:Microsoft.VisualStudio.Package.AuthoringScope> Objekt selbst darf kein NULL-Wert sein.

### <a name="example"></a>Beispiel
 Dieses Beispiel zeigt eine minimale Implementierung der <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> -Methode und der- <xref:Microsoft.VisualStudio.Package.AuthoringScope> Klasse, die ausreicht, damit der Sprachdienst kompiliert und funktioniert, ohne dass die erweiterten Funktionen tatsächlich unterstützt werden.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        public override AuthoringScope ParseSource(ParseRequest req)
        {
            return new TestAuthoringScope();
        }
    }

    internal class TestAuthoringScope : AuthoringScope
    {
        public override string GetDataTipText(int line, int col, out TextSpan span)
        {
            span = new TextSpan();
            return null;
        }

        public override Declarations GetDeclarations(IVsTextView view,
                                                     int line,
                                                     int col,
                                                     TokenInfo info,
                                                     ParseReason reason)
        {
            return null;
        }

        public override string Goto(VSConstants.VSStd97CmdID cmd, IVsTextView textView, int line, int col, out TextSpan span)
        {
            span = new TextSpan();
            return null;
        }

        public override Methods GetMethods(int line, int col, string name)
        {
            return null;
        }
}
```

## <a name="name-property"></a>Name-Eigenschaft
 Diese Eigenschaft gibt den Namen des sprach Dienstanbieter zurück. Dies muss der gleiche Name sein, der beim Registrieren des sprach Dienstanbieter angegeben wurde. Dieser Name wird an mehreren Stellen verwendet, die wichtigste davon ist die Klasse, in der <xref:Microsoft.VisualStudio.Package.LanguagePreferences> der Name verwendet wird, um auf die Registrierung zuzugreifen. Der von dieser Eigenschaft zurückgegebene Name darf nicht lokalisiert werden, da er in der Registrierung für Registrierungs Eintrag und Schlüsselnamen verwendet wird.

### <a name="example"></a>Beispiel
 Dieses Beispiel zeigt eine mögliche Implementierung der- <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A> Eigenschaft. Beachten Sie, dass der Name hier hart codiert ist: der tatsächliche Name sollte aus einer Ressourcen Datei abgerufen werden, damit er beim Registrieren eines sprach Dienstanbieter (siehe [Registrieren eines Legacy sprach Dienstanbieter](../../extensibility/internals/registering-a-legacy-language-service1.md)) verwendet werden kann.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        public override string Name
        {
            get { return "Test Language"; }
        }
    }
}
```

## <a name="instantiating-custom-classes"></a>Instanziieren von benutzerdefinierten Klassen
 Die folgenden Methoden in den angegebenen Klassen können überschrieben werden, um Instanzen Ihrer eigenen Versionen der einzelnen Klassen bereitzustellen.

### <a name="in-the-languageservice-class"></a>In der LanguageService-Klasse

|Methode|Zurückgegebene Klasse|BESCHREIBUNG|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateCodeWindowManager%2A>|<xref:Microsoft.VisualStudio.Package.CodeWindowManager>|Zur Unterstützung benutzerdefinierter Ergänzungen für die Textansicht.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A>|<xref:Microsoft.VisualStudio.Package.DocumentProperties>|, Um benutzerdefinierte Dokumenteigenschaften zu unterstützen.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>|<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>|Zur Unterstützung der **Navigationsleiste**.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionFunction>|Zur Unterstützung von Funktionen in Code Ausschnitt Vorlagen.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionProvider>|Zur Unterstützung von Code Ausschnitten (diese Methode wird in der Regel nicht überschrieben).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateParseRequest%2A>|<xref:Microsoft.VisualStudio.Package.ParseRequest>|Zur Unterstützung der Anpassung der <xref:Microsoft.VisualStudio.Package.ParseRequest> Struktur (diese Methode wird in der Regel nicht überschrieben).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateSource%2A>|<xref:Microsoft.VisualStudio.Package.Source>|, Um das Formatieren von Quellcode, das Angeben von Kommentarzeichen und das Anpassen von Methoden Signaturen zu unterstützen.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A>|<xref:Microsoft.VisualStudio.Package.ViewFilter>|, Um zusätzliche Menübefehle zu unterstützen.|
|<xref:Microsoft.VisualStudio.Package.Source.GetColorizer%2A>|<xref:Microsoft.VisualStudio.Package.Colorizer>|Zur Unterstützung der Syntax Hervorhebung (diese Methode wird in der Regel nicht überschrieben).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>|<xref:Microsoft.VisualStudio.Package.LanguagePreferences>|, Um den Zugriff auf Spracheinstellungen zu unterstützen. Diese Methode muss implementiert werden, kann jedoch eine Instanz der Basisklasse zurückgeben.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>|<xref:Microsoft.VisualStudio.Package.IScanner>|Zum Bereitstellen eines Parsers für die Identifizierung von Tokentypen in einer Zeile. Diese Methode muss implementiert werden und <xref:Microsoft.VisualStudio.Package.IScanner> muss von abgeleitet werden.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringScope>|Zum Bereitstellen eines Parsers, der zur Identifizierung von Funktionalität und Gültigkeitsbereich in der gesamten Quelldatei verwendet wird Diese Methode muss implementiert werden, und es muss eine Instanz Ihrer Version der-Klasse zurückgegeben werden <xref:Microsoft.VisualStudio.Package.AuthoringScope> . Wenn Sie nur die Syntax Hervorhebung unterstützen möchten (was den <xref:Microsoft.VisualStudio.Package.IScanner> Parser erfordert, der von der-Methode zurückgegeben wird <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> ), können Sie in dieser Methode nichts tun, als eine Version der Klasse zurückzugeben, <xref:Microsoft.VisualStudio.Package.AuthoringScope> deren Methoden alle NULL-Werte zurückgeben.|

### <a name="in-the-source-class"></a>In der Source-Klasse

|Methode|Zurückgegebene Klasse|BESCHREIBUNG|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A>|<xref:Microsoft.VisualStudio.Package.CompletionSet>|Zum Anpassen der Anzeige von IntelliSense-Vervollständigungs Listen (diese Methode wird in der Regel nicht überschrieben).|
|<xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A>|<xref:Microsoft.VisualStudio.Package.DocumentTask>|Zur Unterstützung von Markern in der Fehlerliste Aufgabenliste insbesondere Unterstützung für Features, die über das Öffnen der Datei hinausgehen und in die Zeile springen, die den Fehler verursacht hat.|
|<xref:Microsoft.VisualStudio.Package.Source.CreateMethodData%2A>|<xref:Microsoft.VisualStudio.Package.MethodData>|Zum Anpassen der Anzeige von Quick Infos für IntelliSense-Parameter info.|
|<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>|<xref:Microsoft.VisualStudio.Package.CommentInfo>|Zur Unterstützung von Kommentar Code.|
|<xref:Microsoft.VisualStudio.Package.Source.CreateAuthoringSink%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringSink>|Zum Sammeln von Informationen während des Analyse Vorgangs.|

### <a name="in-the-authoringscope-class"></a>In der AuthoringScope-Klasse

|Methode|Zurückgegebene Klasse|BESCHREIBUNG|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>|<xref:Microsoft.VisualStudio.Package.Declarations>|Stellt eine Liste von Deklarationen bereit, z. b. Member oder Typen. Diese Methode muss implementiert werden, kann jedoch einen NULL-Wert zurückgeben. Wenn diese Methode ein gültiges-Objekt zurückgibt, muss das-Objekt eine Instanz Ihrer Version der- <xref:Microsoft.VisualStudio.Package.Declarations> Klasse sein.|
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetMethods%2A>|<xref:Microsoft.VisualStudio.Package.Methods>|Stellt eine Liste von Methoden Signaturen für einen angegebenen Kontext bereit. Diese Methode muss implementiert werden, kann jedoch einen NULL-Wert zurückgeben. Wenn diese Methode ein gültiges-Objekt zurückgibt, muss das-Objekt eine Instanz Ihrer Version der- <xref:Microsoft.VisualStudio.Package.Methods> Klasse sein.|

## <a name="language-service-images"></a>Sprachdienst Images
 Zum Bereitstellen einer Liste von Symbolen, die im gesamten Sprachdienst verwendet werden sollen, überschreiben Sie die <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> -Methode in der <xref:Microsoft.VisualStudio.Package.LanguageService> -Klasse, und geben Sie <xref:System.Windows.Forms.ImageList> mit den Symbolen zurück. Die Basis <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse lädt einen Standardsatz von Symbolen. Da Sie den exakten Abbild Index an den Orten angeben, die Symbole benötigen, ist das Anordnen Ihrer eigenen Bildliste vollständig.

### <a name="images-used-in-intellisense-completion-lists"></a>In IntelliSense-Vervollständigungs Listen verwendete Bilder
 Für IntelliSense-Vervollständigungs Listen wird der Bildindex für jedes Element in der- <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> Methode der- <xref:Microsoft.VisualStudio.Package.Declarations> Klasse angegeben, die Sie überschreiben müssen, wenn Sie einen Bildindex bereitstellen möchten. Der von der-Methode zurückgegebene Wert <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> ist ein Index in der Bildliste, die für den <xref:Microsoft.VisualStudio.Package.CompletionSet> -Klassenkonstruktor bereitgestellt wird, und der dieselbe Bildliste ist, die von der- <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> Methode in der-Klasse zurückgegeben wird <xref:Microsoft.VisualStudio.Package.LanguageService> . (Sie können die Bildliste ändern, die für das verwendet werden soll, <xref:Microsoft.VisualStudio.Package.CompletionSet> Wenn Sie die- <xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A> Methode in der- <xref:Microsoft.VisualStudio.Package.Source> Klasse überschreiben,

### <a name="images-used-in-the-navigation-bar"></a>In der Navigationsleiste verwendete Bilder
 In der **Navigationsleiste** werden Listen von Typen und Membern angezeigt, und für die schnelle Navigation können Symbole angezeigt werden. Diese Symbole werden von der <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> -Methode in der <xref:Microsoft.VisualStudio.Package.LanguageService> -Klasse abgerufen und können nicht speziell für die **Navigationsleiste** überschrieben werden. Die Indizes, die für jedes Element in den Kombinations Feldern verwendet werden, werden angegeben, wenn die Listen, die die Kombinations Felder darstellen, in der-Methode der-Klasse ausgefüllt werden <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> (siehe [Unterstützung für die Navigationsleiste in einem Legacy Sprachdienst](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)). Diese Bild Indizes werden in der Regel über die-Version der-Klasse vom Parser abgerufen <xref:Microsoft.VisualStudio.Package.Declarations> . Die Art und Weise, wie die Indizes abgerufen werden, ist vollständig.

### <a name="images-used-in-the-error-list-task-window"></a>Im Aufgaben Fenster Fehlerliste verwendete Bilder
 Wenn der <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methoden Parser (siehe [Legacy-Sprachdienst Parser und Scanner](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)) einen Fehler feststellt und diesen Fehler an die- <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> Methode in der- <xref:Microsoft.VisualStudio.Package.AuthoringSink> Klasse übergibt, wird der Fehler im Aufgaben Fenster **Fehlerliste** angezeigt. Jedem Element, das im Aufgaben Fenster angezeigt wird, kann ein Symbol zugeordnet werden, und dieses Symbol stammt aus derselben Bildliste, die von der- <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> Methode in der-Klasse zurückgegeben wird <xref:Microsoft.VisualStudio.Package.LanguageService> . Das Standardverhalten der MPF-Klassen besteht darin, kein Bild mit der Fehlermeldung anzuzeigen. Sie können dieses Verhalten jedoch überschreiben, indem Sie eine Klasse von der <xref:Microsoft.VisualStudio.Package.Source> -Klasse ableiten und die-Methode überschreiben <xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A> . In dieser Methode erstellen Sie ein neues- <xref:Microsoft.VisualStudio.Package.DocumentTask> Objekt. Vor der Rückgabe dieses Objekts können Sie die-Eigenschaft des-Objekts verwenden, <xref:Microsoft.VisualStudio.Shell.Task.ImageIndex%2A> <xref:Microsoft.VisualStudio.Package.DocumentTask> um den Bildindex festzulegen. Dies sieht in etwa wie im folgenden Beispiel aus. Beachten Sie, dass `TestIconImageIndex` eine Enumeration ist, die alle Symbole auflistet und für dieses Beispiel spezifisch ist. Sie haben möglicherweise eine andere Möglichkeit zum Identifizieren von Symbolen in Ihrem Sprachdienst.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    class TestSource : Source
    {
        public override DocumentTask CreateErrorTaskItem(
            TextSpan          span,
            string            filename,
            string            message,
            TaskPriority      priority,
            TaskCategory      category,
            MARKERTYPE        markerType,
            TaskErrorCategory errorCategory)
        {
            DocumentTask taskItem = base.CreateErrorTaskItem(
                                           span,
                                           filename,
                                           message,
                                           priority,
                                           category,
                                           markerType,
                                           errorCategory);
            if (errorCategory == TaskErrorCategory.Error)
            {
                taskItem.ImageIndex = TestIconImageIndex.Error;
            }
            return taskItem;
        }
    }
}
```

## <a name="the-default-image-list-for-a-language-service"></a>Die Standard Bildliste für einen Sprachdienst
 Die Standard Bildliste, die mit den grundlegenden MPF-Sprachdienst Klassen bereitgestellt wird, enthält eine Reihe von Symbolen, die den allgemeineren Sprachelementen zugeordnet sind. Die meisten dieser Symbole werden in Sätzen von sechs Variationen angeordnet, die den Zugriffs Konzepten Public, Internal, Friend, protected, private und Shortcut entsprechen. Beispielsweise können Sie verschiedene Symbole für eine Methode haben, je nachdem, ob Sie öffentlich, geschützt oder privat ist.

 Die folgende Enumeration gibt typische Namen für jeden Symbolsatz an und gibt den zugeordneten Index an. Basierend auf der-Enumeration können Sie z. b. den Image Index für eine geschützte Methode als angeben `(int)IconImageIndex.Method + (int)IconImageIndex.AccessProtected` . Sie können die Namen in dieser Enumeration wie gewünscht ändern.

```csharp
public enum IconImageIndex
        {
            // access types
            AccessPublic = 0,
            AccessInternal = 1,
            AccessFriend = 2,
            AccessProtected = 3,
            AccessPrivate = 4,
            AccessShortcut = 5,

            Base = 6,
            // Each of the following icon type has 6 versions,
            //corresponding to the access types
            Class = Base + 0,
            Constant = Base + 1,
            Delegate = Base + 2,
            Enumeration = Base + 3,
            EnumMember = Base + 4,
            Event = Base + 5,
            Exception = Base + 6,
            Field = Base + 7,
            Interface = Base + 8,
            Macro = Base + 9,
            Map = Base + 10,
            MapItem = Base + 11,
            Method = Base + 12,
            OverloadedMethod = Base + 13,
            Module = Base + 14,
            Namespace = Base + 15,
            Operator = Base + 16,
            Property = Base + 17,
            Struct = Base + 18,
            Template = Base + 19,
            Typedef = Base + 20,
            Type = Base + 21,
            Union = Base + 22,
            Variable = Base + 23,
            ValueType = Base + 24,
            Intrinsic = Base + 25,
            JavaMethod = Base + 26,
            JavaField = Base + 27,
            JavaClass = Base + 28,
            JavaNamespace = Base + 29,
            JavaInterface = Base + 30,
            // Miscellaneous icons with one icon for each type.
            Error = 187,
            GreyedClass = 188,
            GreyedPrivateMethod = 189,
            GreyedProtectedMethod = 190,
            GreyedPublicMethod = 191,
            BrowseResourceFile = 192,
            Reference = 193,
            Library = 194,
            VBProject = 195,
            VBWebProject = 196,
            CSProject = 197,
            CSWebProject = 198,
            VB6Project = 199,
            CPlusProject = 200,
            Form = 201,
            OpenFolder = 202,
            ClosedFolder = 203,
            Arrow = 204,
            CSClass = 205,
            Snippet = 206,
            Keyword = 207,
            Info = 208,
            CallBrowserCall = 209,
            CallBrowserCallRecursive = 210,
            XMLEditor = 211,
            VJProject = 212,
            VJClass = 213,
            ForwardedType = 214,
            CallsTo = 215,
            CallsFrom = 216,
            Warning = 217,
        }
```

## <a name="see-also"></a>Weitere Informationen
- [Implementieren eines Legacysprachdiensts](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [Übersicht über Legacysprachdienste](../../extensibility/internals/legacy-language-service-overview.md)
- [Registrieren eines Legacysprachdiensts](../../extensibility/internals/registering-a-legacy-language-service1.md)
- [Parser und Scanner von Legacysprachdiensten](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
