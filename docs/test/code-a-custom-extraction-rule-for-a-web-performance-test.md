---
title: Programmieren einer benutzerdefinierten Extraktionsregel (Webleistungstest)
description: Lernen Sie, eigene Extraktionsregeln zu erstellen, die von der Extraktionsregelklasse ExtractionRule abgeleitet werden.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- extraction rules
- Web performance tests, creating custom extraction rules
- extraction rules, creating custom
ms.assetid: 6bcc5712-6cc6-4f59-8933-6e8078318c45
dev_langs:
- CSharp
- VB
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 09038afd3b8f359ed90639d7f35cb92c04241324
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99964601"
---
# <a name="code-a-custom-extraction-rule-for-a-web-performance-test"></a>Kodieren einer benutzerdefinierten Extraktionsregel für einen Webleistungstest

Sie können eigene Extraktionsregeln erstellen. Leiten Sie hierzu Ihre Regeln von einer bereits vorhandenen Klasse für Extraktionsregeln ab. Extraktionsregeln werden von der <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule>-Basisklasse abgeleitet.

> [!NOTE]
> Sie können auch benutzerdefinierte Validierungsregeln erstellen. Weitere Informationen finden Sie unter [Erstellen von benutzerdefiniertem Code und benutzerdefinierten Plug-Ins für Auslastungstests](../test/create-custom-code-and-plug-ins-for-load-tests.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-create-a-custom-extraction-rule"></a>So erstellen Sie eine benutzerdefinierte Extraktionsregel

1. Öffnen Sie ein Testprojekt, das einen Webleistungstest enthält.

2. (Optional) Erstellen Sie ein separates Klassenbibliotheksprojekt zum Speichern der Extraktionsregel.

    > [!IMPORTANT]
    > Die Klasse kann im selben Projekt erstellt werden, in dem sich die Tests befinden. Wenn die Regel erneut verwendet werden soll, wird jedoch empfohlen, ein separates Klassenbibliotheksprojekt zu erstellen, in dem die Regel gespeichert wird. Wenn Sie ein separates Projekt erstellen, müssen Sie die optionalen Schritte in dieser Prozedur ausführen.

3. (Optional) Fügen Sie im Klassenbibliotheksprojekt einen Verweis auf Microsoft.VisualStudio.QualityTools.WebTestFramework dll hinzu.

4. Erstellen Sie eine von der <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule>-Klasse abgeleitete Klasse. Implementieren Sie den <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule.Extract*>-Member und den <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule.RuleName*>-Member.

5. (Optional) Erstellen Sie das neue Klassenbibliotheksprojekt.

6. (Optional) Fügen Sie im Testprojekt einen Verweis auf das Klassenbibliotheksprojekt mit der benutzerdefinierten Extraktionsregel hinzu.

7. Öffnen Sie im Testprojekt einen Webleistungstest im **Webleistungstest-Editor**.

8. Um die benutzerdefinierte Extraktionsregel hinzuzufügen, klicken Sie mit der rechten Maustaste auf eine Webleistungstest-Anforderung, und wählen Sie **Extraktionsregel hinzufügen** aus.

     Das Dialogfeld **Extraktionsregel hinzufügen** wird angezeigt. Die benutzerdefinierte Validierungsregel wird in der Liste **Regel auswählen** zusammen mit den vordefinierten Validierungsregeln angezeigt. Wählen Sie die benutzerdefinierte Extraktionsregel aus, und klicken Sie auf **OK**.

9. Führen Sie den Webleistungstest aus.

## <a name="example"></a>Beispiel

Im folgenden Code wird eine Implementierung einer benutzerdefinierten Extraktionsregel dargestellt. Diese Extraktionsregel extrahiert den Wert eines angegebenen Eingabefelds. Verwenden Sie dieses Beispiel als Ausgangspunkt für eigene benutzerdefinierte Extraktionsregeln.

```csharp
using System;
using System.Collections.Generic;
using Microsoft.VisualStudio.TestTools.WebTesting;
using System.Globalization;

namespace ClassLibrary2
{
    //-------------------------------------------------------------------------
    // This class creates a custom extraction rule named "Custom Extract Input"
    // The user of the rule specifies the name of an input field, and the
    // rule attempts to extract the value of that input field.
    //-------------------------------------------------------------------------
    public class CustomExtractInput : ExtractionRule
    {
        /// Specify a name for use in the user interface.
        /// The user sees this name in the Add Extraction dialog box.
        //---------------------------------------------------------------------
        public override string RuleName
        {
            get { return "Custom Extract Input"; }
        }

        /// Specify a description for use in the user interface.
        /// The user sees this description in the Add Extraction dialog box.
        //---------------------------------------------------------------------
        public override string RuleDescription
        {
            get { return "Extracts the value from a specified input field"; }
        }

        // The name of the desired input field
        private string NameValue;
        public string Name
        {
            get { return NameValue; }
            set { NameValue = value; }
        }

        // The Extract method.  The parameter e contains the web performance test context.
        //---------------------------------------------------------------------
        public override void Extract(object sender, ExtractionEventArgs e)
        {
            if (e.Response.HtmlDocument != null)
            {
                foreach (HtmlTag tag in e.Response.HtmlDocument.GetFilteredHtmlTags(new string[] { "input" }))
                {
                    if (String.Equals(tag.GetAttributeValueAsString("name"), Name, StringComparison.InvariantCultureIgnoreCase))
                    {
                        string formFieldValue = tag.GetAttributeValueAsString("value");
                        if (formFieldValue == null)
                        {
                            formFieldValue = String.Empty;
                        }

                        // add the extracted value to the web performance test context
                        e.WebTest.Context.Add(this.ContextParameterName, formFieldValue);
                        e.Success = true;
                        return;
                    }
                }
            }
            // If the extraction fails, set the error text that the user sees
            e.Success = false;
            e.Message = String.Format(CultureInfo.CurrentCulture, "Not Found: {0}", Name);
        }
    }
}
```

```vb
Imports System
Imports System.Collections.Generic
Imports Microsoft.VisualStudio.TestTools.WebTesting
Imports System.Globalization

Namespace ClassLibrary2

    '-------------------------------------------------------------------------
    ' This class creates a custom extraction rule named "Custom Extract Input"
    ' The user of the rule specifies the name of an input field, and the
    ' rule attempts to extract the value of that input field.
    '-------------------------------------------------------------------------
    Public Class CustomExtractInput
        Inherits ExtractionRule

        ' Specify a name for use in the user interface.
        ' The user sees this name in the Add Extraction dialog box.
        '---------------------------------------------------------------------
        Public Overrides ReadOnly Property RuleName() As String
            Get
                Return "Custom Extract Input"
            End Get
        End Property

        ' Specify a description for use in the user interface.
        ' The user sees this description in the Add Extraction dialog box.
        '---------------------------------------------------------------------
        Public Overrides ReadOnly Property RuleDescription() As String
            Get
                Return "Extracts the value from a specified input field"
            End Get
        End Property

        ' The name of the desired input field
        Private NameValue As String
        Public Property Name() As String
            Get
                Return NameValue
            End Get
            Set(ByVal value As String)
                NameValue = value
            End Set
        End Property

        ' The Extract method.  The parameter e contains the web performance test context.
        '---------------------------------------------------------------------
        Public Overrides Sub Extract(ByVal sender As Object, ByVal e As ExtractionEventArgs)

            If Not e.Response.HtmlDocument Is Nothing Then

                For Each tag As HtmlTag In e.Response.HtmlDocument.GetFilteredHtmlTags(New String() {"input"})

                    If String.Equals(tag.GetAttributeValueAsString("name"), Name, StringComparison.InvariantCultureIgnoreCase) Then

                        Dim formFieldValue As String = tag.GetAttributeValueAsString("value")
                        If formFieldValue Is Nothing Then

                            formFieldValue = String.Empty
                        End If

                        ' add the extracted value to the web performance test context
                        e.WebTest.Context.Add(Me.ContextParameterName, formFieldValue)
                        e.Success = True
                        Return
                    End If
                Next
            End If
            ' If the extraction fails, set the error text that the user sees
            e.Success = False
            e.Message = String.Format(CultureInfo.CurrentCulture, "Not Found: {0}", Name)
        End Sub
    End Class
End Namespace
```

Die <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule.Extract*>-Methode enthält die Basisfunktionalität einer Extraktionsregel. An die <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule.Extract*>-Methode im vorherigen Beispiel wird <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionEventArgs> übergeben, worin die Antwort der Anforderung zurückgegeben wird, auf die diese Extraktionsregel angewendet wird. Die Antwort beinhaltet ein <xref:Microsoft.VisualStudio.TestTools.WebTesting.HtmlDocument>, das alle Tags aus der Antwort enthält. Eingabetags werden dabei aus dem <xref:Microsoft.VisualStudio.TestTools.WebTesting.HtmlDocument> herausgefiltert. Jedes Eingabetag wird auf ein `name`-Attribut geprüft, dessen Wert mit der vom Benutzer bereitgestellten `Name`-Eigenschaft übereinstimmt. Wenn ein Tag mit diesem übereinstimmenden Attribut gefunden wird, wird versucht, einen im `value`-Attribut enthaltenen Wert zu extrahieren, sofern ein value-Attribut vorhanden ist. Ist dieses Attribut ebenfalls vorhanden, werden Name und Wert des Tags extrahiert und dem Webleistungstestkontext hinzugefügt. Die Extraktionsregel wurde damit erfolgreich ausgeführt.

## <a name="see-also"></a>Weitere Informationen

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractAttributeValue>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractFormField>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractHttpHeader>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractRegularExpression>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractText>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractHiddenFields>
- [Kodieren einer benutzerdefinierten Validierungsregel für einen Webleistungstest](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
