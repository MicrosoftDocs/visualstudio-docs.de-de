---
title: Benutzerdefinierte Dokumenteigenschaften in Legacy Sprachdiensten
description: Erfahren Sie, wie Sie benutzerdefinierte Dokumenteigenschaften erstellen, die im Visual Studio-Eigenschaftenfenster als Teil eines Legacy sprach Dienstanbieter angezeigt werden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- custom document properties, language services [managed package framework]
- document properties, custom
- language services [managed package framework], custom document properties
ms.assetid: cc714a67-b33e-4440-9203-3c90f648bd9c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d5fa24f3d052ab9122776967607b2c197fb102bf
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2020
ms.locfileid: "96329899"
---
# <a name="custom-document-properties-in-a-legacy-language-service"></a>Benutzerdefinierte Dokumenteigenschaften in einem Legacy Sprachdienst
Dokumenteigenschaften können im [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **Eigenschaften** Fenster angezeigt werden. Programmiersprachen sind im Allgemeinen keine Eigenschaften zugeordnet, die einzelnen Quelldateien zugeordnet sind. XML unterstützt jedoch Dokumenteigenschaften, die die Codierung, das Schema und das Stylesheet beeinflussen.

## <a name="discussion"></a>Diskussion
 Wenn Ihre Sprache benutzerdefinierte Dokumenteigenschaften benötigt, müssen Sie eine Klasse von der <xref:Microsoft.VisualStudio.Package.DocumentProperties> -Klasse ableiten und die erforderlichen Eigenschaften für die abgeleitete Klasse implementieren.

 Außerdem werden Dokumenteigenschaften in der Regel in der Quelldatei gespeichert. Dies erfordert, dass der Sprachdienst die Eigenschaften Informationen aus der Quelldatei analysiert, die im **Eigenschaften** Fenster angezeigt werden sollen, und die Quelldatei aktualisieren, wenn an den Dokumenteigenschaften im **Eigenschaften** Fenster eine Änderung vorgenommen wird.

## <a name="customize-the-documentproperties-class"></a>Anpassen der DocumentProperties-Klasse
 Um benutzerdefinierte Dokumenteigenschaften zu unterstützen, müssen Sie eine Klasse von der <xref:Microsoft.VisualStudio.Package.DocumentProperties> -Klasse ableiten und beliebig viele Eigenschaften hinzufügen. Sie sollten auch Benutzerattribute angeben, um Sie im **Eigenschaften** Fenster anzuzeigen. Wenn eine Eigenschaft nur über einen- `get` Accessor verfügt, wird Sie im **Eigenschaften** Fenster als schreibgeschützt angezeigt. Wenn eine Eigenschaft über `get` -und- `set` Accessoren verfügt, kann die-Eigenschaft auch im **Eigenschaften** Fenster aktualisiert werden.

### <a name="example"></a>Beispiel
 Im folgenden finden Sie eine Beispiel Klasse, die von abgeleitet wird <xref:Microsoft.VisualStudio.Package.DocumentProperties> und die zwei Eigenschaften anzeigt: `Filename` und `Description` . Wenn eine-Eigenschaft aktualisiert wird, wird eine benutzerdefinierte-Methode für die- <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse aufgerufen, um die-Eigenschaft in die Quelldatei zu schreiben.

```csharp
using System.ComponentModel;
using Microsoft.VisualStudio.Package;

namespace TestLanguagePackage
{
    class TestDocumentProperties : DocumentProperties
    {
        private string m_filename;
        private string m_description;

        public TestDocumentProperties(CodeWindowManager mgr)
            : base(mgr)
        {
        }

        // Helper function to initialize this property without
        // going through the FileName property (which does a lot
        // more than we need when the filename is set).
        public void SetFileName(string filename)
        {
            m_filename = filename;
        }

        // Helper function to initialize this property without
        // going through the Description property (which does a lot
        // more than we need when the description is set).
        public void SetDescription(string description)
        {
            m_description = description;
        }

        ////////////////////////////////////////////////////////////
        // The document properties

        [CategoryAttribute("General")]
        [DescriptionAttribute("Name of the file")]
        [DisplayNameAttribute("Filename")]
        public string FileName
        {
            get { return m_filename; }
            set
            {
               if (value != m_filename)
               {
                    m_filename = value;
                    SetPropertyValue("Filename", m_filename);
               }
            }
        }

        [CategoryAttribute("General")]
        [DescriptionAttribute("Description of the file")]
        [DisplayNameAttribute("Description")]
        public string Description
        {
            get { return m_description; }
            set
            {
                if (value != m_description)
                {
                    m_description = value;
                    SetPropertyValue("Description", m_description);
                }
            }
        }

        ///////////////////////////////////////////////////////////
        // Private methods.

        private void SetPropertyValue(string propertyName, string propertyValue)
        {
            Source src = this.GetSource();
            if (src != null)
            {
                TestLanguageService service = src.LanguageService as TestLanguageService;
                if (service != null)
                {
                    // Set the property in to the source file.
                    service.SetPropertyValue(src, propertyName, propertyValue);
                }
            }
        }
    }
}
```

## <a name="instantiate-the-custom-documentproperties-class"></a>Instanziieren der benutzerdefinierten DocumentProperties-Klasse
 Um die benutzerdefinierte Dokumenteigenschaften Klasse zu instanziieren, müssen Sie die- <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A> Methode in Ihrer Version der- <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse überschreiben, um eine einzelne Instanz der-Klasse zurückzugeben <xref:Microsoft.VisualStudio.Package.DocumentProperties> .

### <a name="example"></a>Beispiel

```csharp
using System.ComponentModel;
using Microsoft.VisualStudio.Package;

namespace TestLanguagePackage
{
    class TestLanguageService : LanguageService
    {
        private TestDocumentProperties m_documentProperties;

        public override DocumentProperties CreateDocumentProperties(CodeWindowManager mgr)
        {
            if (m_documentProperties == null)
            {
                m_documentProperties = new TestDocumentProperties(mgr);
            }
            return m_documentProperties;
        }
    }
}
```

## <a name="properties-in-the-source-file"></a>Eigenschaften in der Quelldatei
 Da Dokumenteigenschaften in der Regel für die Quelldatei spezifisch sind, werden die Werte in der Quelldatei selbst gespeichert. Dies erfordert die Unterstützung durch den sprach Parser oder Scanner, um diese Eigenschaften zu definieren. Beispielsweise werden die Eigenschaften eines XML-Dokuments auf dem Stamm Knoten gespeichert. Die Werte auf dem Stamm Knoten werden geändert, wenn die **Eigenschaften** Fenster Werte geändert werden und der Stamm Knoten im Editor aktualisiert wird.

### <a name="example"></a>Beispiel
 In diesem Beispiel werden die Eigenschaften `Filename` und `Description` in den ersten beiden Zeilen der Quelldatei, die in einen speziellen Kommentar Header eingebettet sind, wie folgt gespeichert:

```
//!Filename = file.testext
//!Description = A sample file
```

 Dieses Beispiel zeigt die zwei Methoden, die erforderlich sind, um die Dokumenteigenschaften aus den ersten beiden Zeilen der Quelldatei zu erhalten und festzulegen. Außerdem wird erläutert, wie die Eigenschaften aktualisiert werden, wenn der Benutzer die Quelldatei direkt ändert. Die- `SetPropertyValue` Methode im hier gezeigten Beispiel ist dieselbe, die von der-Klasse aufgerufen wird, `TestDocumentProperties` wie im Abschnitt *Anpassen der DocumentProperties-Klasse* gezeigt.

 In diesem Beispiel wird der Scanner verwendet, um den Typ der Token in den ersten beiden Zeilen zu bestimmen. Dieses Beispiel dient nur zu Illustrations Zwecken. Ein typischer Ansatz für diese Situation besteht darin, die Quelldatei in eine Analyse Struktur zu analysieren, in der jeder Knoten der Strukturinformationen zu einem bestimmten Token enthält. Der Stamm Knoten enthält die Dokumenteigenschaften.

```csharp
using System.ComponentModel;
using Microsoft.VisualStudio.Package;

namespace TestLanguagePackage
{
    // TokenType.Comment is the last item in that enumeration.
    public enum TestTokenTypes
    {
        DocPropertyLine = TokenType.Comment + 1,
        DocPropertyName,
        DocPropertyAssign,
        DocPropertyValue
    }

    class TestLanguageService : LanguageService
    {
        // Search this many lines from the beginning for properties.
        private static int maxLinesToSearch = 2;

        private TestDocumentProperties m_documentProperties;

        // Called whenever a full parsing operation has completed.
        public override void OnParseComplete(ParseRequest req)
        {
            if (m_documentProperties != null)
            {
                Source src = GetSource(req.View);
                if (src != null)
                {
                    string value = GetPropertyValue(src, "Filename");
                    m_documentProperties.SetFileName(value);

                    value = GetPropertyValue(src, "Description");
                    m_documentProperties.SetDescription(value);

                    // Update the Properties Window.
                    m_documentProperties.Refresh();
                }
            }
        }

        // Retrieves the specified property value from the given source.
        public string GetPropertyValue(Source src, string propertyName)
        {
            string propertyValue = "";

            if (src != null)
            {
                IVsTextColorState colorState = src.ColorState;
                if (colorState != null)
                {
                    string      line;
                    TokenInfo[] lineInfo = null;
                    int         i;

                    for (i = 0; i < maxLinesToSearch; i++)
                    {
                        line     = src.GetLine(i);
                        lineInfo = src.GetColorizer().GetLineInfo(
                                                        src.GetTextLines(),
                                                        i,
                                                        colorState);
                        if (lineInfo == null)
                        {
                            continue;
                        }
                        if (lineInfo[0].Type != (TokenType)TestTokenTypes.DocPropertyLine)
                        {
                            // Not a property line.
                            continue;
                        }
                        TokenInfo valueInfo = new TokenInfo();
                        int tokenIndex = -1;
                        for (tokenIndex = 0;
                             tokenIndex < lineInfo.Length;
                             tokenIndex++)
                        {
                            if (lineInfo[tokenIndex].Type == (TokenType)TestTokenTypes.DocPropertyName)
                            {
                                break;
                            }
                        }
                        if (tokenIndex >= lineInfo.Length)
                        {
                            // No property name on the line.
                            continue;
                        }
                        string name = src.GetText(i,
                                                  lineInfo[tokenIndex].StartIndex,
                                                  i,
                                                  lineInfo[tokenIndex].EndIndex + 1);
                        if (name != null)
                        {
                            if (String.Compare(name, propertyName, true) == 0)
                            {
                                for ( ;
                                     tokenIndex < lineInfo.Length;
                                     tokenIndex++)
                                {
                                    if (lineInfo[tokenIndex].Type == (TokenType)TestTokenTypes.DocPropertyValue)
                                    {
                                        break;
                                    }
                                }
                                if (tokenIndex < lineInfo.Length)
                                {
                                    propertyValue = src.GetText(i,
                                                          lineInfo[tokenIndex].StartIndex,
                                                          i,
                                                          lineInfo[tokenIndex].EndIndex + 1);
                                }
                                break;
                            }
                        }
                    }
                }
            }
            return propertyValue;
        }

        // Sets the specified property into the given source file.
        // Called from the TestDocumentProperties class.
        public void SetPropertyValue(Source src, string propertyName, string propertyValue)
        {
            string newLine;

            if (propertyName == null || propertyName == "")
            {
                // No property name, so nothing to do
                return;
            }
            if (propertyValue == null)
            {
                propertyValue = "";
            }
            // This is the line to be inserted.
            newLine = String.Format("//!{0} = {1}", propertyName, propertyValue);

            // First, find the line on which the property belongs.
            // If line is found, replace it.
            // Otherwise, insert the line at the beginning of the file.
            if (src != null)
            {
                IVsTextColorState colorState = src.ColorState;
                if (colorState != null)
                {
                    int         lineNumber = -1;
                    string      line;
                    TokenInfo[] lineInfo   = null;
                    int         i;

                    for (i = 0; i < maxLinesToSearch; i++)
                    {
                        line     = src.GetLine(i);
                        lineInfo = src.GetColorizer().GetLineInfo(
                                                        src.GetTextLines(),
                                                        i,
                                                        colorState);
                        if (lineInfo == null)
                        {
                            continue;
                        }
                        if (lineInfo[0].Type != (TokenType)TestTokenTypes.DocPropertyLine)
                        {
                            // Not a property line
                            continue;
                        }
                        TokenInfo valueInfo = new TokenInfo();
                        int tokenIndex = -1;
                        for (tokenIndex = 0;
                             tokenIndex < lineInfo.Length;
                             tokenIndex++)
                        {
                            if (lineInfo[tokenIndex].Type == (TokenType)TestTokenTypes.DocPropertyName)
                            {
                                break;
                            }
                        }
                        if (tokenIndex >= lineInfo.Length)
                        {
                            // No property name on the line.
                            continue;
                        }
                        string name = src.GetText(i,
                                                  lineInfo[tokenIndex].StartIndex,
                                                  i,
                                                  lineInfo[tokenIndex].EndIndex + 1);
                        if (name != null)
                        {
                            if (String.Compare(name, propertyName, true) == 0)
                            {
                                lineNumber = i;
                                break;
                            }
                        }
                    }

                    // Set up an undo context that also handles the insert/replace.
                    EditArray editArray = new EditArray(src,
                                                        true,
                                                        "Update Property");
                    if (editArray != null)
                    {
                        TextSpan span = new TextSpan();
                        if (lineNumber != -1)
                        {
                            // Replace line.
                            int lineLength = 0;
                            src.GetTextLines().GetLengthOfLine(lineNumber,
                                                               out lineLength);
                            span.iStartLine  = lineNumber;
                            span.iStartIndex = 0;
                            span.iEndLine    = lineNumber;
                            span.iEndIndex   = lineLength;
                        }
                        else
                        {
                            // Insert new line.
                            span.iStartLine  = 0;
                            span.iStartIndex = 0;
                            span.iEndLine    = 0;
                            span.iEndIndex   = 0;
                            newLine += "\n";
                        }
                        editArray.Add(new EditSpan(span, newLine));
                        editArray.ApplyEdits();
                    }
                }
            }
        }
    }
}
```

## <a name="see-also"></a>Siehe auch
- [Funktionen von Legacy Sprachdiensten](../../extensibility/internals/legacy-language-service-features1.md)
