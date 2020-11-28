---
title: Codeausschnittfunktionen
description: Erfahren Sie mehr über die Funktionen GenerateSwitchCases(EnumerationLiteral), ClassName() und SimpleTypeNam(TypeName), die mit C#-Codeausschnitten verwendet werden können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- code snippets [Visual Studio], functions
- snippets [Visual Studio], functions
- IntelliSense code snippets, functions
ms.assetid: c0a2bf21-8fa5-4457-9281-f599beb53e7d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e6529f4f82f7a8a6862ae85adbf170d2fb6f8706
ms.sourcegitcommit: 66cda27b63c9b55782b1db223a6dbda9f8cabe13
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2020
ms.locfileid: "95006509"
---
# <a name="code-snippet-functions"></a>Codeausschnittfunktionen

Es stehen drei Funktionen zur Verfügung, die mit C#-Codeausschnitten verwendet werden können. Funktionen werden im Element [Function](../ide/code-snippets-schema-reference.md#function-element) (Funktion) des Codeausschnitts angegeben. Informationen zum Erstellen von Codeausschnitten finden Sie unter [Codeausschnitte](../ide/code-snippets.md).

## <a name="functions"></a>Functions

In der folgenden Tabelle werden die verfügbaren Funktionen für die Verwendung mit dem `Function`-Element in Codeausschnitten beschrieben.

|Funktion|Beschreibung|Sprache|
|--------------|-----------------|--------------|
|`GenerateSwitchCases(EnumerationLiteral)`|Es werden eine switch-Anweisung sowie mehrere case-Anweisungen für die vom `EnumerationLiteral`-Parameter angegebenen Member der Enumeration generiert. Der `EnumerationLiteral`-Parameter muss entweder ein Verweis auf ein Enumerationsliteral oder auf einen Enumerationstyp sein.|C#|
|`ClassName()`|Gibt den Namen der Klasse zurück, die den eingefügten Ausschnitt enthält.|C#|
|`SimpleTypeName(TypeName)`|Reduziert den *TypeName*-Parameter auf seine einfachste Form im Kontext, in dem der Ausschnitt aufgerufen wurde.|C#|

## <a name="generateswitchcases-example"></a>Beispiel für GenerateSwitchCases

Das folgende Beispiel zeigt die Verwendung der Funktion `GenerateSwitchCases`. Wenn dieser Ausschnitt eingefügt wird und eine Enumeration in das `$switch_on$`-Literal eingefügt wird, generiert das `$cases$`-Literal eine `case`-Anweisung für jeden Wert in der Enumeration.

```xml
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
    <CodeSnippet Format="1.0.0">
        <Header>
            <Title>switch</Title>
            <Shortcut>switch</Shortcut>
            <Description>Code snippet for switch statement</Description>
            <Author>Microsoft Corporation</Author>
            <SnippetTypes>
                <SnippetType>Expansion</SnippetType>
            </SnippetTypes>
        </Header>
        <Snippet>
            <Declarations>
                <Literal>
                    <ID>expression</ID>
                    <ToolTip>Expression to switch on</ToolTip>
                    <Default>switch_on</Default>
                </Literal>
                <Literal Editable="false">
                    <ID>cases</ID>
                    <Function>GenerateSwitchCases($expression$)</Function>
                    <Default>default:</Default>
                </Literal>
            </Declarations>
            <Code Language="csharp">
                <![CDATA[
                    switch ($expression$)
                    {
                        $cases$
                    }
                ]]>
            </Code>
        </Snippet>
    </CodeSnippet>
</CodeSnippets>
```

## <a name="classname-example"></a>Beispiel für ClassName

Das folgende Beispiel zeigt die Verwendung der Funktion `ClassName`. Wenn dieser Ausschnitt eingefügt wird, wird das `$classname$`-Literal mit dem Namen der einschließenden Klasse an diesem Speicherort in der Codedatei ersetzt.

```xml
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
    <CodeSnippet Format="1.0.0">
        <Header>
            <Title>Common constructor pattern</Title>
            <Shortcut>ctor</Shortcut>
            <Description>Code Snippet for a constructor</Description>
            <Author>Microsoft Corporation</Author>
            <SnippetTypes>
                <SnippetType>Expansion</SnippetType>
            </SnippetTypes>
        </Header>
        <Snippet>
            <Declarations>
                <Literal>
                    <ID>type</ID>
                    <Default>int</Default>
                </Literal>
                <Literal>
                    <ID>name</ID>
                    <Default>field</Default>
                </Literal>
                <Literal default="true" Editable="false">
                    <ID>classname</ID>
                    <ToolTip>Class name</ToolTip>
                    <Function>ClassName()</Function>
                    <Default>ClassNamePlaceholder</Default>
                </Literal>
            </Declarations>
            <Code Language="csharp" Format="CData">
                <![CDATA[
                    public $classname$ ($type$ $name$)
                    {
                        this._$name$ = $name$;
                    }
                    private $type$ _$name$;
                ]]>
            </Code>
        </Snippet>
    </CodeSnippet>
</CodeSnippets>
```

## <a name="simpletypename-example"></a>Beispiel für SimpleTypeName

In diesem Beispiel wird die Verwendung der `SimpleTypeName`-Funktion veranschaulicht. Wenn dieser Codeausschnitt in eine Codedatei eingefügt wird, wir das `$SystemConsole$`-Literal mit der einfachsten Form des Typs <xref:System.Console> im Kontext ersetzt, in dem der Ausschnitt aufgerufen wurde.

```xml
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
    <CodeSnippet Format="1.0.0">
        <Header>
            <Title>Console_WriteLine</Title>
            <Shortcut>cw</Shortcut>
            <Description>Code snippet for Console.WriteLine</Description>
            <Author>Microsoft Corporation</Author>
            <SnippetTypes>
                <SnippetType>Expansion</SnippetType>
            </SnippetTypes>
        </Header>
        <Snippet>
            <Declarations>
                <Literal Editable="false">
                    <ID>SystemConsole</ID>
                    <Function>SimpleTypeName(global::System.Console)</Function>
                </Literal>
            </Declarations>
            <Code Language="csharp">
                <![CDATA[
                    $SystemConsole$.WriteLine();
                ]]>
            </Code>
        </Snippet>
    </CodeSnippet>
</CodeSnippets>
```

## <a name="see-also"></a>Weitere Informationen

- [Function-Element](../ide/code-snippets-schema-reference.md#function-element)
- [Schemareferenz für Codeausschnitte](../ide/code-snippets-schema-reference.md)
