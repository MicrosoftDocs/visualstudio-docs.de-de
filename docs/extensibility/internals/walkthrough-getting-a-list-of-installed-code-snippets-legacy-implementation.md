---
title: Eine Liste der installierten Code Ausschnitte (Legacy) Microsoft-Dokumentation
description: Erfahren Sie, wie Sie alle Code Ausschnitte für eine bestimmte sprach-GUID erhalten. Die Tastenkombinationen für diese Code Ausschnitte können in eine IntelliSense-Vervollständigungsliste eingefügt werden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- snippets, retrieving list
- code snippets, retrieving list
- GetSnippets method
ms.assetid: 7d142f8b-35b1-44c4-a13e-f89f6460c906
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 390f8e7030d0e758eb27fce4e83a30e30fbf64af
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97487893"
---
# <a name="walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation"></a>Exemplarische Vorgehensweise: Abrufen einer Liste der installierten Codeausschnitte (Legacyimplementierung)
Ein Code Ausschnitt ist ein Code Ausschnitt, der in den Quell Puffer eingefügt werden kann, entweder mit einem Menübefehl (der die Auswahl zwischen einer Liste installierter Code Ausschnitte ermöglicht) oder durch Auswahl einer Ausschnitt Verknüpfung aus einer IntelliSense-Vervollständigungsliste.

 Die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.EnumerateExpansions%2A> Methode ruft alle Code Ausschnitte für eine bestimmte sprach-GUID ab. Die Tastenkombinationen für diese Code Ausschnitte können in eine IntelliSense-Vervollständigungsliste eingefügt werden.

 Ausführliche Informationen zum Implementieren von Code Ausschnitten in einem MPF-Sprachdienst (Managed Package Framework) finden Sie [unter Unterstützung für Code Ausschnitte in einem Legacy Sprachdienst](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md) .

### <a name="to-retrieve-a-list-of-code-snippets"></a>So rufen Sie eine Liste von Code Ausschnitten ab

1. Der folgende Code zeigt, wie Sie eine Liste von Code Ausschnitten für eine bestimmte Sprache erhalten. Die Ergebnisse werden in einem Array von <xref:Microsoft.VisualStudio.TextManager.Interop.VsExpansion> Strukturen gespeichert. Diese Methode verwendet die statische- <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> Methode, um die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> Schnittstelle aus dem Dienst zu erhalten <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> . Sie können jedoch auch den Dienstanbieter verwenden, der für Ihr VSPackage angegeben ist, und die-Methode aufzurufen <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> .

    ```csharp
    using System;
    using System.Collections;
    using System.Runtime.InteropServices;
    using Microsoft.VisualStudio.Package;
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.TextManager.Interop;

    [Guid("00000000-0000-0000-0000-000000000000")] //create a new GUID for the language service
    namespace TestLanguage
    {
        class TestLanguageService : LanguageService
        {
            private void GetSnippets(Guid languageGuid,
                                     ref ArrayList expansionsList)
            {
                IVsTextManager textManager = (IVsTextManager)Package.GetGlobalService(typeof(SVsTextManager));
                if (textManager != null)
                {
                    IVsTextManager2 textManager2 = (IVsTextManager2)textManager;
                    if (textManager2 != null)
                    {
                        IVsExpansionManager expansionManager = null;
                        textManager2.GetExpansionManager(out expansionManager);
                        if (expansionManager != null)
                        {
                            // Tell the environment to fetch all of our snippets.
                            IVsExpansionEnumeration expansionEnumerator = null;
                            expansionManager.EnumerateExpansions(languageGuid,
                            0,     // return all info
                            null,    // return all types
                            0,     // return all types
                            1,     // include snippets without types
                            0,     // do not include duplicates
                            out expansionEnumerator);
                            if (expansionEnumerator != null)
                            {
                                // Cache our expansions in a VsExpansion array
                                uint count   = 0;
                                uint fetched = 0;
                                VsExpansion expansionInfo = new VsExpansion();
                                IntPtr[] pExpansionInfo   = new IntPtr[1];

                                // Allocate enough memory for one VSExpansion structure. This memory is filled in by the Next method.
                                pExpansionInfo[0] = Marshal.AllocCoTaskMem(Marshal.SizeOf(expansionInfo));

                                expansionEnumerator.GetCount(out count);
                                for (uint i = 0; i < count; i++)
                                {
                                    expansionEnumerator.Next(1, pExpansionInfo, out fetched);
                                    if (fetched > 0)
                                    {
                                        // Convert the returned blob of data into a structure that can be read in managed code.
                                        expansionInfo = (VsExpansion)Marshal.PtrToStructure(pExpansionInfo[0], typeof(VsExpansion));

                                        if (!String.IsNullOrEmpty(expansionInfo.shortcut))
                                        {
                                            expansionsList.Add(expansionInfo);
                                        }
                                    }
                                }
                                Marshal.FreeCoTaskMem(pExpansionInfo[0]);
                            }
                        }
                    }
                }
            }
        }
    }
    ```

### <a name="to-call-the-getsnippets-method"></a>So wenden Sie die geznippets-Methode an

1. Die folgende Methode zeigt, wie die- `GetSnippets` Methode beim Abschluss eines-Vorgangs aufgerufen wird. Die- <xref:Microsoft.VisualStudio.Package.LanguageService.OnParseComplete%2A> Methode wird nach einem mit dem Grund gestarteten Verarbeitungsvorgang aufgerufen <xref:Microsoft.VisualStudio.Package.ParseReason> .

> [!NOTE]
> Die `expansionsList` Liste der Arrays wird aus Leistungsgründen zwischengespeichert. Änderungen an den Code Ausschnitten werden erst dann in der Liste wiedergegeben, wenn der Sprachdienst beendet und erneut geladen wurde (z. b. durch beenden und Neustarten [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ).

```csharp
class TestLanguageService : LanguageService
{
    private ArrayList expansionsList;

    public override void OnParseComplete(ParseRequest req)
    {
        if (this.expansionsList == null)
        {
            this.expansionsList = new ArrayList();
            GetSnippets(this.GetLanguageServiceGuid(),
                ref this.expansionsList);
        }
    }
}
```

### <a name="to-use-the-snippet-information"></a>So verwenden Sie die Ausschnitt Informationen

1. Der folgende Code zeigt, wie die von der-Methode zurückgegebenen Ausschnitt Informationen verwendet werden `GetSnippets` . Die- `AddSnippets` Methode wird vom Parser als Reaktion auf einen beliebigen Analyse Grund aufgerufen, der verwendet wird, um eine Liste von Code Ausschnitten aufzufüllen. Dies sollte erfolgen, nachdem die vollständige Analyse zum ersten Mal ausgeführt wurde.

     Die- `AddDeclaration` Methode erstellt eine Liste von Deklarationen, die später in einer Vervollständigungsliste angezeigt wird.

     Die- `TestDeclaration` Klasse enthält alle Informationen, die in einer Vervollständigungsliste angezeigt werden können, sowie den Typ der Deklaration.

    ```csharp
    class TestAuthoringScope : AuthoringScope
    {
        public void AddDeclarations(TestDeclaration declaration)
        {
            if (m_declarations == null)
                m_declarations = new List<TestDeclaration>();
            m_declarations.Add(declaration);
         }
    }
    class TestDeclaration
    {
        private string m_name;
        private string m_description;
        private string m_type;

        public TestDeclaration(string name, string desc, string type)
        {
            m_name = name;
            m_description = desc;
            m_type = type;
        }

    class TestLanguageService : LanguageService
    {
        internal void AddSnippets(ref TestAuthoringScope scope)
        {
            if (this.expansionsList != null && this.expansionsList.Count > 0)
            {
                int count = this.expansionsList.Count;
                for (int i = 0; i < count; i++)
                {
                    VsExpansion expansionInfo = (VsExpansion)this.expansionsList[i];
                    scope.AddDeclaration(new TestDeclaration(expansionInfo.title,
                         expansionInfo.description,
                         "snippet"));
                }
            }
        }
    }

    ```

## <a name="see-also"></a>Weitere Informationen
- [Unterstützen von Codeausschnitten in einem Legacysprachdienst](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)
