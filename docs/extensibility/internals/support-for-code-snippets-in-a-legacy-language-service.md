---
title: Unterstützung für Code Ausschnitte in einem Legacy Sprachdienst | Microsoft-Dokumentation
description: Erfahren Sie, wie ein Legacy Sprachdienst Code Ausschnitte unterstützt. Ein Code Ausschnitt ist ein Code Ausschnitt, der in die Quelldatei eingefügt wird.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- snippets, supporting in language services
- code snippets, supporting in language services [managed package framework]
- language services [managed package framework], supporting code snippets
ms.assetid: 7490325b-acee-4c2d-ac56-1cd5db1a1083
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 16f0df8a21621b93655935b3cfa27a4b62df63ce
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888146"
---
# <a name="support-for-code-snippets-in-a-legacy-language-service"></a>Unterstützen von Codeausschnitten in einem Legacysprachdienst
Ein Code Ausschnitt ist ein Code Ausschnitt, der in die Quelldatei eingefügt wird. Der Code Ausschnitt selbst ist eine XML-basierte Vorlage mit einem Satz von Feldern. Diese Felder werden hervorgehoben, nachdem der Ausschnitt eingefügt wurde, und können je nach Kontext, in dem der Ausschnitt eingefügt wird, unterschiedliche Werte aufweisen. Unmittelbar nachdem der Ausschnitt eingefügt wurde, kann der Sprachdienst den Ausschnitt formatieren.

 Der Code Ausschnitt wird in einem speziellen Bearbeitungsmodus eingefügt, der die Navigation der Felder des Code Ausschnitts mithilfe der Tab-Taste ermöglicht. Die Felder können Dropdown Menüs im IntelliSense-Stil unterstützen. Der Benutzer führt einen Commit für den Ausschnitt zur Quelldatei aus, indem er entweder die EINGABETASTE oder die ESC-Taste eingegeben hat. Weitere Informationen zu Code Ausschnitten finden Sie unter [Code Ausschnitte](../../ide/code-snippets.md).

 Legacy Sprachdienste werden als Teil eines VSPackages implementiert, aber die neuere Methode zum Implementieren von Sprachdienst Funktionen ist die Verwendung von MEF-Erweiterungen. Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Implementieren von Code Ausschnitten](../../extensibility/walkthrough-implementing-code-snippets.md).

> [!NOTE]
> Es wird empfohlen, dass Sie so bald wie möglich mit der Verwendung der neuen Editor-API beginnen. Dadurch wird die Leistung Ihres sprach Dienstanbieter verbessert, und Sie können die neuen Editor-Features nutzen.

## <a name="managed-package-framework-support-for-code-snippets"></a>Unterstützung von Managed Package Framework für Code Ausschnitte
 Das Managed Package Framework (MPF) unterstützt die meisten ausschnittsfunktionen, das Lesen der Vorlage, das Einfügen des Code Ausschnitts und das Aktivieren des speziellen Bearbeitungsmodus. Die Unterstützung wird durch die- <xref:Microsoft.VisualStudio.Package.ExpansionProvider> Klasse verwaltet.

 Wenn die- <xref:Microsoft.VisualStudio.Package.Source> Klasse instanziiert wird, <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A> wird die-Methode in der- <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse aufgerufen, um ein- <xref:Microsoft.VisualStudio.Package.ExpansionProvider> Objekt abzurufen (Beachten Sie, dass die Basis <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse immer ein neues- <xref:Microsoft.VisualStudio.Package.ExpansionProvider> Objekt für jedes-Objekt zurückgibt <xref:Microsoft.VisualStudio.Package.Source> ).

 Der MPF unterstützt keine Erweiterungsfunktionen. Eine Erweiterungs Funktion ist eine benannte Funktion, die in eine Ausschnitt Vorlage eingebettet ist und einen oder mehrere Werte zurückgibt, die in ein Feld eingefügt werden sollen. Die Werte werden vom Sprachdienst selbst durch ein-Objekt zurückgegeben <xref:Microsoft.VisualStudio.Package.ExpansionFunction> . Das <xref:Microsoft.VisualStudio.Package.ExpansionFunction> Objekt muss vom Sprachdienst implementiert werden, um Erweiterungsfunktionen zu unterstützen.

## <a name="providing-support-for-code-snippets"></a>Bereitstellen von Unterstützung für Code Ausschnitte
 Um die Unterstützung für Code Ausschnitte zu aktivieren, müssen Sie die Code Ausschnitte bereitstellen oder installieren, und Sie müssen dem Benutzer die Möglichkeit geben, diese Ausschnitte einzufügen. Es gibt drei Schritte, um die Unterstützung für Code Ausschnitte zu aktivieren:

1. Die Ausschnitt Dateien werden installiert.

2. Aktivieren von Code Ausschnitten für Ihren Sprachdienst.

3. Aufrufen des- <xref:Microsoft.VisualStudio.Package.ExpansionProvider> Objekts.

### <a name="installing-the-snippet-files"></a>Installieren der Ausschnitt Dateien
 Alle Ausschnitte für eine Sprache werden als Vorlagen in XML-Dateien gespeichert, in der Regel eine Ausschnitt Vorlage pro Datei. Ausführliche Informationen zum XML-Schema, das für Code Ausschnitt Vorlagen verwendet wird, finden Sie unter [Schema Referenz für Code Ausschnitte](../../ide/code-snippets-schema-reference.md). Jede Ausschnitt Vorlage wird mit einer Sprach-ID identifiziert. Diese Sprach-ID wird in der Registrierung angegeben und in das- `Language` Attribut des- \<Code> Tags in der Vorlage eingefügt.

 Es gibt in der Regel zwei Orte, an denen die Code Ausschnitt Vorlagen Dateien gespeichert werden: 1), in denen Ihre Sprache installiert wurde, und 2) im Ordner des Benutzers. Diese Speicherorte werden der Registrierung hinzugefügt, sodass der Code Ausschnitt-Manager von Visual Studio die **Code** Ausschnitte finden kann. Im Ordner des Benutzers werden Ausschnitte gespeichert, die vom Benutzer erstellt wurden.

 Das typische Ordner Layout für die installierten Ausschnitt Vorlagen Dateien sieht wie folgt aus: *[InstallRoot]* \\ *[testlanguage]* \Snippets \\ *[LCID]* \snippe.

 *[InstallRoot]* ist der Ordner, in dem Ihre Sprache installiert ist.

 *[Testlanguage]* ist der Name der Sprache als Ordnername.

 *[LCID]* ist die Gebiets Schema-ID. Auf diese Weise werden lokalisierte Versionen der Code Ausschnitte gespeichert. Die Gebiets Schema-ID für Englisch lautet z. b. 1033, d. h., *[LCID]* wird durch 1033 ersetzt.

 Es muss eine zusätzliche Datei angegeben werden, die eine Indexdatei ist, die in der Regel als SnippetsIndex.xml oder ExpansionsIndex.xml bezeichnet wird. (Sie können einen beliebigen gültigen Dateinamen verwenden, der in. XML endet. Diese Datei wird in der Regel im Ordner *[InstallRoot]* \\ *[testlanguage]* gespeichert und gibt den genauen Speicherort des Ordner Snippets sowie die Sprach-ID und GUID des sprach Dienstanbieter an, der die Ausschnitte verwendet. Der exakte Pfad der Indexdatei wird in der Registrierung abgelegt, wie weiter unten unter "Installieren der Registrierungseinträge" beschrieben. Im folgenden finden Sie ein Beispiel für eine SnippetsIndex.xml-Datei:

```
<?xml version="1.0" encoding="utf-8" ?>
<SnippetCollection>
    <Language Lang="Testlanguage" Guid="{b614a40a-80d9-4fac-a6ad-fc2868fff7cd}">
        <SnippetDir>
            <OnOff>On</OnOff>
            <Installed>true</Installed>
            <Locale>1033</Locale>
            <DirPath>%InstallRoot%\TestLanguage\Snippets\%LCID%\Snippets\</DirPath>
            <LocalizedName>Snippets</LocalizedName>
        </SnippetDir>
    </Language>
</SnippetCollection>
```

 Das \<Language> -Tag gibt die Sprach-ID (das `Lang` -Attribut) und die Sprachdienst-GUID an.

 In diesem Beispiel wird davon ausgegangen, dass Sie Ihren Sprachdienst im Visual Studio-Installationsordner installiert haben. % LCID% wird durch die aktuelle Gebiets Schema-ID des Benutzers ersetzt. Es \<SnippetDir> können mehrere Tags hinzugefügt werden, eine für jedes andere Verzeichnis und jedes beliebige Gebiets Schema. Außerdem kann ein Ausschnitt Ordner Unterordner enthalten, die jeweils in der Indexdatei mit dem-Tag identifiziert werden, \<SnippetSubDir> das in ein-Tag eingebettet ist \<SnippetDir> .

 Benutzer können auch eigene Ausschnitte für Ihre Sprache erstellen. Diese werden in der Regel im Ordner "Einstellungen" des Benutzers gespeichert, z. b. *[testdocs]* \code Ausschnitte \\ *[testlanguage]* \testcode Ausschnitte, wobei *[testdocs]* der Speicherort des Ordners für die Benutzereinstellungen für Visual Studio ist.

 Die folgenden Ersetzungs Elemente können im Pfad abgelegt werden, der im- \<DirPath> Tag in der Indexdatei gespeichert ist.

|Element|Beschreibung|
|-------------|-----------------|
|LCID|Gebiets Schema-ID.|
|InstallRoot|Der Stamm Installationsordner für Visual Studio, z. b. c:\Programme\Microsoft Visual Studio 8.|
|% Projdir%|Ordner, der das aktuelle Projekt enthält.|
|%ProjItem%|Ordner, der das aktuelle Projekt Element enthält.|
|% Testdocs%|Ordner im Ordner "Einstellungen" des Benutzers, z. b. c:\Dokumente und Einstellungen \\ *[username]* \Eigene Dateien\Visual Studio\8.|

### <a name="enabling-code-snippets-for-your-language-service"></a>Aktivieren von Code Ausschnitten für Ihren Sprachdienst
 Sie können Code Ausschnitte für Ihren Sprachdienst aktivieren, indem Sie das- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> Attribut zu Ihrem VSPackage hinzufügen (Weitere Informationen finden Sie unter [Registrieren eines Legacy sprach Dienstanbieter](../../extensibility/internals/registering-a-legacy-language-service1.md) ). Der <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.ShowRoots%2A> -Parameter und der- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.SearchPaths%2A> Parameter sind optional, Sie sollten jedoch den benannten Parameter einschließen, um `SearchPaths` den Code Ausschnitt- **Manager** über den Speicherort der Code Ausschnitte zu informieren.

 Im folgenden finden Sie ein Beispiel für die Verwendung dieses Attributs:

```
[ProvideLanguageCodeExpansion(
         typeof(TestSnippetLanguageService),
         "Test Snippet Language",          // Name of language used as registry key
         0,                               // Resource ID of localized name of language service
         "Test Snippet Language",        // Name of Language attribute in snippet template
         @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\SnippetsIndex.xml",  // Path to snippets index
         SearchPaths = @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\")]    // Path to snippets
```

### <a name="calling-the-expansion-provider"></a>Aufrufen des Erweiterungs Anbieters
 Der Sprachdienst steuert das Einfügen eines beliebigen Code Ausschnitts sowie die Art und Weise, in der Einfügevorgänge aufgerufen werden.

## <a name="calling-the-expansion-provider-for-code-snippets"></a>Aufrufen des Erweiterungs Anbieters für Code Ausschnitte
 Es gibt zwei Möglichkeiten, den Erweiterungs Anbieter aufzurufen: mithilfe eines Menübefehls oder mithilfe einer Verknüpfung aus einer Vervollständigungsliste.

### <a name="inserting-a-code-snippet-by-using-a-menu-command"></a>Einfügen eines Code Ausschnitts mithilfe eines Menübefehls
 Wenn Sie einen Menübefehl verwenden möchten, um den Ausschnitt Browser anzuzeigen, fügen Sie einen Menübefehl hinzu, und nennen Sie dann die- <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> Methode in der- <xref:Microsoft.VisualStudio.Package.ExpansionProvider> Schnittstelle als Reaktion auf den Menübefehl.

1. Fügen Sie der vsct-Datei einen Befehl und eine Schaltfläche hinzu. Anweisungen dazu finden Sie unter [Erstellen einer Erweiterung mit einem Menübefehl](../../extensibility/creating-an-extension-with-a-menu-command.md).

2. Leiten Sie eine Klasse von der <xref:Microsoft.VisualStudio.Package.ViewFilter> -Klasse ab <xref:Microsoft.VisualStudio.Package.ViewFilter.QueryCommandStatus%2A> , und überschreiben Sie die-Methode, um Unterstützung für den neuen Menübefehl anzugeben In diesem Beispiel wird immer der Menübefehl aktiviert.

    ```csharp
    using Microsoft.VisualStudio.Package;

    namespace TestLanguagePackage
    {
        class TestViewFilter : ViewFilter
        {
            public TestViewFilter(CodeWindowManager mgr, IVsTextView view)
                : base(mgr, view)
            {
            }

            protected override int QueryCommandStatus(ref Guid guidCmdGroup,
                                                      uint nCmdId)
            {
                int hr = base.QueryCommandStatus(ref guidCmdGroup, nCmdId);
                // If the base class did not recognize the command then
                // see if we can handle the command.
                if (hr == (int)Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_UNKNOWNGROUP)
                {
                    if (guidCmdGroup == GuidList.guidTestLanguagePackageCmdSet)
                    {
                        if (nCmdId == PkgCmdIDList.InvokeCodeSnippetsBrowser)
                        {
                            hr = (int)(OLECMDF.OLECMDF_SUPPORTED | OLECMDF.OLECMDF_ENABLED);
                        }
                    }
                }
                return hr;
            }
        }
    }
    ```

3. Überschreiben <xref:Microsoft.VisualStudio.Package.ViewFilter.HandlePreExec%2A> Sie die-Methode in der- <xref:Microsoft.VisualStudio.Package.ViewFilter> Klasse, um das <xref:Microsoft.VisualStudio.Package.ExpansionProvider> Objekt abzurufen und die- <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> Methode für dieses Objekt aufzurufen.

    ```csharp
    using Microsoft.VisualStudio.Package;

    namespace TestLanguagePackage
    {
        class TestViewFilter : ViewFilter
        {
            public override bool HandlePreExec(ref Guid guidCmdGroup,
                                               uint nCmdId,
                                               uint nCmdexecopt,
                                               IntPtr pvaIn,
                                               IntPtr pvaOut)
            {
                if (base.HandlePreExec(ref guidCmdGroup,
                                       nCmdId,
                                       nCmdexecopt,
                                       pvaIn,
                                       pvaOut))
                {
                    // Base class handled the command.  Do nothing more here.
                    return true;
                }

                if (guidCmdGroup == GuidList.guidTestLanguagePackageCmdSet)
                {
                    if (nCmdId == PkgCmdIDList.InvokeCodeSnippetsBrowser)
                    {
                        ExpansionProvider ep = this.GetExpansionProvider();
                        if (this.TextView != null && ep != null)
                        {
                            bool bDisplayed = ep.DisplayExpansionBrowser(
                                this.TextView,
                                "TestLanguagePackage Snippet:",
                                null,
                                false,
                                null,
                                false);
                        }
                        return true;   // Handled the command.
                    }
                }
                return false;   // Did not handle the command.
            }
        }
    }

    ```

     Die folgenden Methoden in der- <xref:Microsoft.VisualStudio.Package.ExpansionProvider> Klasse werden von Visual Studio in der angegebenen Reihenfolge aufgerufen, während der Ausschnitt eingefügt wird:

4. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnItemChosen%2A>

5. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>

6. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>

7. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>

8. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>

     Nachdem die- <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A> Methode aufgerufen wurde, wurde der Ausschnitt eingefügt, und das <xref:Microsoft.VisualStudio.Package.ExpansionProvider> Objekt befindet sich in einem speziellen Bearbeitungsmodus, der zum Ändern eines soeben eingefügten Code Ausschnitts verwendet wird.

### <a name="inserting-a-code-snippet-by-using-a-shortcut"></a>Einfügen eines Code Ausschnitts mithilfe einer Verknüpfung
 Die Implementierung einer Verknüpfung aus einer Vervollständigungsliste ist weitaus komplizierter als die Implementierung eines Menübefehls. Sie müssen der IntelliSense-Wort Vervollständigungsliste zuerst Ausschnitt Verknüpfungen hinzufügen. Anschließend müssen Sie erkennen, wenn ein Ausschnitt Verknüpfungs Name als Ergebnis der Vervollständigung eingefügt wurde. Schließlich müssen Sie den Ausschnitt Titel und-Pfad mit dem Verknüpfungs Namen abrufen und diese Informationen an die- <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> Methode der- <xref:Microsoft.VisualStudio.Package.ExpansionProvider> Methode übergeben.

 Um Ausschnitt Verknüpfungen zur Wort Vervollständigungsliste hinzuzufügen, fügen Sie Sie dem- <xref:Microsoft.VisualStudio.Package.Declarations> Objekt in der- <xref:Microsoft.VisualStudio.Package.AuthoringScope> Klasse hinzu. Sie müssen sicherstellen, dass Sie die Verknüpfung als Ausschnitt Namen identifizieren können. Ein Beispiel finden Sie unter Exemplarische Vorgehensweise [: erhalten einer Liste installierter Code Ausschnitte (Legacy Implementierung)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).

 Sie können das Einfügen der Verknüpfung mit dem Code Ausschnitt in der- <xref:Microsoft.VisualStudio.Package.Declarations.OnAutoComplete%2A> Methode der- <xref:Microsoft.VisualStudio.Package.Declarations> Klasse erkennen. Da der Name des Code Ausschnitts bereits in die Quelldatei eingefügt wurde, muss dieser beim Einfügen der Erweiterung entfernt werden. Die- <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> Methode nimmt eine Spanne an, die den Einfügepunkt für den Ausschnitt beschreibt. wenn die Spanne den gesamten Ausschnitt Namen in der Quelldatei enthält, wird dieser Name durch den Ausschnitt ersetzt.

 Hier ist eine Version einer <xref:Microsoft.VisualStudio.Package.Declarations> Klasse, die das Einfügen von Ausschnitten behandelt, wenn ein Verknüpfungs Name angegeben ist. Andere Methoden in der- <xref:Microsoft.VisualStudio.Package.Declarations> Klasse wurden aus Gründen der Übersichtlichkeit ausgelassen. Beachten Sie, dass der Konstruktor dieser Klasse ein- <xref:Microsoft.VisualStudio.Package.LanguageService> Objekt annimmt. Dies kann aus der-Version des-Objekts übergeben werden <xref:Microsoft.VisualStudio.Package.AuthoringScope> (z. b. kann die Implementierung der- <xref:Microsoft.VisualStudio.Package.AuthoringScope> Klasse das <xref:Microsoft.VisualStudio.Package.LanguageService> -Objekt in seinem Konstruktor annehmen und dieses Objekt an den `TestDeclarations` Klassenkonstruktor übergeben).

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    internal class TestDeclarations : Declarations
    {
        private ArrayList       declarations;
        private LanguageService languageService;
        private TextSpan        commitSpan;

        public TestDeclarations(LanguageService langService)
            : base()
        {
            languageService = langService;
            declarations = new ArrayList();
        }

        // This method is used to add declarations to the internal list.
        public void AddDeclaration(TestDeclaration declaration)
        {
            declarations.Add(declaration);
        }

        // This method is called to get the string to commit to the source buffer.
        // Note that the initial extent is only what the user has typed so far.
        public override string OnCommit(IVsTextView textView,
                                        string textSoFar,
                                        char commitCharacter,
                                        int index,
                                        ref TextSpan initialExtent)
        {
            // We intercept this call only to get the initial extent
            // of what was committed to the source buffer.
            commitSpan = initialExtent;

            return base.OnCommit(textView,
                                 textSoFar,
                                 commitCharacter,
                                 index,
                                 ref initialExtent);
        }

        // This method is called after the string has been committed to the source buffer.
        public override char OnAutoComplete(IVsTextView textView,
                                            string committedText,
                                            char commitCharacter,
                                            int index)
        {
            TestDeclaration item = declarations[index] as TestDeclaration;
            if (item != null)
            {
                // In this example, TestDeclaration identifies types with a string.
                // You can choose a different approach.
                if (item.Type == "snippet")
                {
                    Source src = languageService.GetSource(textView);
                    if (src != null)
                    {
                        ExpansionProvider ep = src.GetExpansionProvider();
                        if (ep != null)
                        {
                            string title;
                            string path;
                            int commitLength = commitSpan.iEndIndex - commitSpan.iStartIndex;
                            if (commitLength < committedText.Length)
                            {
                                // Replace everything that was inserted
                                // so calculate the span of the full
                                // insertion, taking into account what
                                // was inserted when the commitSpan
                                // was obtained in the first place.
                                commitSpan.iEndIndex += (committedText.Length - commitLength);
                            }

                            if (ep.FindExpansionByShortcut(textView,
                                                           committedText,
                                                           commitSpan,
                                                           true,
                                                           out title,
                                                           out path))
                            {
                                ep.InsertNamedExpansion(textView,
                                                        title,
                                                        path,
                                                        commitSpan,
                                                        false);
                            }
                        }
                    }
                }
            }
            return '\0';
        }
    }
}
```

 Wenn der Sprachdienst den Verknüpfungs Namen erhält, ruft er die <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FindExpansionByShortcut%2A> -Methode auf, um den Dateinamen und den Code Ausschnitt Titel abzurufen. Der Sprachdienst ruft dann die- <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> Methode in der- <xref:Microsoft.VisualStudio.Package.ExpansionProvider> Klasse auf, um den Code Ausschnitt einzufügen. Die folgenden Methoden werden von Visual Studio in der angegebenen Reihenfolge in der-Klasse aufgerufen, <xref:Microsoft.VisualStudio.Package.ExpansionProvider> während der Ausschnitt eingefügt wird:

1. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>

2. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>

3. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>

4. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>

   Weitere Informationen zum erhalten einer Liste installierter Code Ausschnitte für Ihren Sprachdienst finden Sie unter Exemplarische Vorgehensweise [: erhalten einer Liste installierter Code Ausschnitte (Legacy Implementierung)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).

## <a name="implementing-the-expansionfunction-class"></a>Implementieren der Expansions Function-Klasse
 Eine Erweiterungs Funktion ist eine benannte Funktion, die in eine Ausschnitt Vorlage eingebettet ist und einen oder mehrere Werte zurückgibt, die in ein Feld eingefügt werden sollen. Um Erweiterungsfunktionen in Ihrem Sprachdienst zu unterstützen, müssen Sie eine Klasse von der <xref:Microsoft.VisualStudio.Package.ExpansionFunction> -Klasse ableiten und die- <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetCurrentValue%2A> Methode implementieren. Anschließend müssen Sie die- <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A> Methode in der- <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse überschreiben, um eine neue Instanziierung Ihrer Version der- <xref:Microsoft.VisualStudio.Package.ExpansionFunction> Klasse für jede von Ihnen unterstützte Erweiterungs Funktion zurückzugeben. Wenn Sie eine Liste möglicher Werte aus einer Erweiterungs Funktion unterstützen, müssen Sie auch die- <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetIntellisenseList%2A> Methode in der- <xref:Microsoft.VisualStudio.Package.ExpansionFunction> Klasse überschreiben, um eine Liste dieser Werte zurückzugeben.

 Eine Erweiterungs Funktion, die Argumente annimmt oder auf andere Felder zugreifen muss, sollte nicht mit einem bearbeitbaren Feld verknüpft werden, da der Erweiterungs Anbieter möglicherweise nicht vollständig von dem Zeitpunkt, zu dem die Erweiterungs Funktion aufgerufen wird, vollständig initialisiert wurde. Folglich kann die Erweiterungs Funktion nicht den Wert ihrer Argumente oder eines anderen Felds abrufen.

### <a name="example"></a>Beispiel
 Im folgenden finden Sie ein Beispiel dafür, wie eine einfache Erweiterungs Funktion mit dem Namen `GetName` implementiert werden kann. Diese Erweiterungs Funktion fügt eine Zahl an einen Basisklassen Namen an, wenn die Erweiterungs Funktion instanziiert wird (was jedem Zeitpunkt entspricht, an dem der zugehörige Code Ausschnitt eingefügt wird).

```csharp
using Microsoft.VisualStudio.Package;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        private int classNameCounter = 0;

        public override ExpansionFunction CreateExpansionFunction(
            ExpansionProvider provider,
            string functionName)
        {
            ExpansionFunction function = null;
            if (functionName == "GetName")
            {
                ++classNameCounter;
                function = new TestGetNameExpansionFunction(provider, classNameCounter);
            }
            return function;
        }
    }

    internal class TestGetNameExpansionFunction : ExpansionFunction
    {
        private int nameCount;

        TestGetNameExpansionFunction(ExpansionProvider provider, int counter)
            : base(provider)
        {
            nameCount = counter;
        }

        public override string GetCurrentValue()
        {
            string name = "TestClass";
            name += nameCount.ToString();
            return name;
        }
    }
}
```

## <a name="see-also"></a>Weitere Informationen
- [Funktionen von Legacysprachdiensten](../../extensibility/internals/legacy-language-service-features1.md)
- [Registrieren eines Legacysprachdiensts](../../extensibility/internals/registering-a-legacy-language-service1.md)
- [Codeausschnitte](../../ide/code-snippets.md)
- [Exemplarische Vorgehensweise: Abrufen einer Liste der installierten Codeausschnitte (Legacyimplementierung)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)
