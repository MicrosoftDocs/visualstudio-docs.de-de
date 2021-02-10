---
title: Erstellen einer benutzerdefinierten Validierungsregel für einen Webleistungstest
description: Lernen Sie, eigene Validierungsregeln zu erstellen, die von der Validierungsregelklasse ValidationRule abgeleitet werden.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- custom validation rules
- validation rules, creating
- web performance tests, creating custom validation rules
- rules, validation
- validation rules
ms.assetid: 989124bc-1a86-41f7-b37d-8f9e54dd4f0b
dev_langs:
- CSharp
- VB
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: ae5228c4da9abef9b5bee417d5d3d71bb28d416d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99964588"
---
# <a name="code-a-custom-validation-rule-for-a-web-performance-test"></a>Kodieren einer benutzerdefinierten Validierungsregel für einen Webleistungstest

Sie können eigene Validierungsregeln erstellen. Dazu leiten Sie Ihre eigene Regelklasse von einer Validierungsregelklasse ab. Validierungsregeln werden von der <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule>-Basisklasse abgeleitet.

> [!NOTE]
> Sie können auch benutzerdefinierte Extraktionsregeln erstellen. Weitere Informationen finden Sie unter [Erstellen von benutzerdefiniertem Code und benutzerdefinierten Plug-Ins für Auslastungstests](../test/create-custom-code-and-plug-ins-for-load-tests.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-create-custom-validation-rules"></a>So erstellen Sie benutzerdefinierte Validierungsregeln

1. Öffnen Sie ein Testprojekt, das einen Webleistungstest enthält.

2. (Optional) Erstellen Sie ein separates Klassenbibliotheksprojekt, in dem die Validierungsregel gespeichert wird.

    > [!IMPORTANT]
    > Die Klasse kann im selben Projekt erstellt werden, in dem sich die Tests befinden. Wenn die Regel erneut verwendet werden soll, wird jedoch empfohlen, ein separates Klassenbibliotheksprojekt zu erstellen, in dem die Regel gespeichert wird. Wenn Sie ein separates Projekt erstellen, müssen Sie die optionalen Schritte in dieser Prozedur ausführen.

3. (Optional) Fügen Sie im Klassenbibliotheksprojekt einen Verweis auf Microsoft.VisualStudio.QualityTools.WebTestFramework DLL ein.

4. Erstellen Sie eine von der <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule>-Klasse abgeleitete Klasse. Implementieren Sie den <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule.Validate*>-Member und den <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule.RuleName*>-Member.

5. (Optional) Erstellen Sie das neue Klassenbibliotheksprojekt.

6. (Optional) Fügen Sie im Testprojekt einen Verweis auf das Klassenbibliotheksprojekt mit der benutzerdefinierten Validierungsregel hinzu.

7. Öffnen Sie im Testprojekt einen Webleistungstest im **Webleistungstest-Editor**.

8. Klicken Sie mit der rechten Maustaste auf eine Anforderung, und wählen Sie **Validierungsregel hinzufügen** aus, um die benutzerdefinierte Validierungsregel einer Webleistungstestanforderung hinzuzufügen.

     Das Dialogfeld **Validierungsregel hinzufügen** wird angezeigt. Die benutzerdefinierte Validierungsregel wird in der Liste **Regel auswählen** zusammen mit den vordefinierten Validierungsregeln angezeigt. Wählen Sie die benutzerdefinierte Validierungsregel aus, und klicken Sie dann auf **OK**.

9. Führen Sie den Webleistungstest aus.

## <a name="example"></a>Beispiel

Im folgenden Code wird eine Implementierung einer benutzerdefinierten Validierungsregel dargestellt. Diese Validierungsregel simuliert das Verhalten einer vordefinierten Validierungsregel Erforderliches Tag. Verwenden Sie dieses Beispiel als Ausgangspunkt für eigene benutzerdefinierte Validierungsregeln.

> [!WARNING]
> Öffentliche Eigenschaften im Code für eine benutzerdefinierte Bestätigung kann keine "null"-Werte aufweisen.

```csharp
using System;
using System.Diagnostics;
using System.Globalization;
using Microsoft.VisualStudio.TestTools.WebTesting;

namespace SampleWebTestRules
{
    //-------------------------------------------------------------------------
    // This class creates a custom validation rule named "Custom Validate Tag"
    // The custom validation rule is used to check that an HTML tag with a
    // particular name is found one or more times in the HTML response.
    // The user of the rule can specify the HTML tag to look for, and the
    // number of times that it must appear in the response.
    //-------------------------------------------------------------------------
    public class CustomValidateTag : ValidationRule
    {
        /// Specify a name for use in the user interface.
        /// The user sees this name in the Add Validation dialog box.
        //---------------------------------------------------------------------
        public override string RuleName
        {
            get { return "Custom Validate Tag"; }
        }

        /// Specify a description for use in the user interface.
        /// The user sees this description in the Add Validation dialog box.
        //---------------------------------------------------------------------
        public override string RuleDescription
        {
            get { return "Validates that the specified tag exists on the page."; }
        }

        // The name of the required tag
        private string RequiredTagNameValue;
        public string RequiredTagName
        {
            get { return RequiredTagNameValue; }
            set { RequiredTagNameValue = value; }
        }

        // The minimum number of times the tag must appear in the response
        private int MinOccurrencesValue;
        public int MinOccurrences
        {
            get { return MinOccurrencesValue; }
            set { MinOccurrencesValue = value; }
        }

        // Validate is called with the test case Context and the request context.
        // These allow the rule to examine both the request and the response.
        //---------------------------------------------------------------------
        public override void Validate(object sender, ValidationEventArgs e)
        {
            bool validated = false;
            int numTagsFound = 0;

            foreach (HtmlTag tag in e.Response.HtmlDocument.GetFilteredHtmlTags(RequiredTagName))
            {
                Debug.Assert(string.Equals(tag.Name, RequiredTagName, StringComparison.InvariantCultureIgnoreCase));

                if (++numTagsFound >= MinOccurrences)
                {
                    validated = true;
                    break;
                }
            }

            e.IsValid = validated;

            // If the validation fails, set the error text that the user sees
            if (!validated)
            {
                if (numTagsFound > 0)
                {
                    e.Message = String.Format("Only found {0} occurrences of the tag", numTagsFound);
                }
                else
                {
                    e.Message = String.Format("Did not find any occurrences of tag '{0}'", RequiredTagName);
                }
            }
        }
    }
}
```

```vb
Imports System
Imports System.Diagnostics
Imports System.Globalization
Imports Microsoft.VisualStudio.TestTools.WebTesting

Namespace SampleWebTestRules

    '-------------------------------------------------------------------------
    ' This class creates a custom validation rule named "Custom Validate Tag"
    ' The custom validation rule is used to check that an HTML tag with a
    ' particular name is found one or more times in the HTML response.
    ' The user of the rule can specify the HTML tag to look for, and the
    ' number of times that it must appear in the response.
    '-------------------------------------------------------------------------
    Public Class CustomValidateTag
        Inherits Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule

        ' Specify a name for use in the user interface.
        ' The user sees this name in the Add Validation dialog box.
        '---------------------------------------------------------------------
        Public Overrides ReadOnly Property RuleName() As String
            Get
                Return "Custom Validate Tag"
            End Get
        End Property

        ' Specify a description for use in the user interface.
        ' The user sees this description in the Add Validation dialog box.
        '---------------------------------------------------------------------
        Public Overrides ReadOnly Property RuleDescription() As String
            Get
                Return "Validates that the specified tag exists on the page."
            End Get
        End Property

        ' The name of the required tag
        Private RequiredTagNameValue As String
        Public Property RequiredTagName() As String
            Get
                Return RequiredTagNameValue
            End Get
            Set(ByVal value As String)
                RequiredTagNameValue = value
            End Set
        End Property

        ' The minimum number of times the tag must appear in the response
        Private MinOccurrencesValue As Integer
        Public Property MinOccurrences() As Integer
            Get
                Return MinOccurrencesValue
            End Get
            Set(ByVal value As Integer)
                MinOccurrencesValue = value
            End Set
        End Property

        ' Validate is called with the test case Context and the request context.
        ' These allow the rule to examine both the request and the response.
        '---------------------------------------------------------------------
        Public Overrides Sub Validate(ByVal sender As Object, ByVal e As ValidationEventArgs)

            Dim validated As Boolean = False
            Dim numTagsFound As Integer = 0

            For Each tag As HtmlTag In e.Response.HtmlDocument.GetFilteredHtmlTags(RequiredTagName)

                Debug.Assert(String.Equals(tag.Name, RequiredTagName, StringComparison.InvariantCultureIgnoreCase))

                numTagsFound += 1
                If numTagsFound >= MinOccurrences Then

                    validated = True
                    Exit For
                End If
            Next

            e.IsValid = validated

            ' If the validation fails, set the error text that the user sees
            If Not (validated) Then
                If numTagsFound > 0 Then
                    e.Message = String.Format("Only found {0} occurrences of the tag", numTagsFound)
                Else
                    e.Message = String.Format("Did not find any occurrences of tag '{0}'", RequiredTagName)
                End If
            End If
        End Sub
    End Class
End Namespace
```

## <a name="see-also"></a>Weitere Informationen

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ValidateFormField>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ValidationRuleFindText>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ValidationRuleRequestTime>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ValidationRuleRequiredAttributeValue>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ValidationRuleRequiredTag>
- [Kodieren einer benutzerdefinierten Extraktionsregel für einen Webleistungstest](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
