---
title: Debuggen von Benutzercode mit nur eigenem Code | Microsoft-Dokumentation
description: „Nur eigenen Code“ ist ein Debugfeature, das automatisch Aufrufe von Nichtbenutzercode überspringt. Hier erfahren Sie, wie Sie dieses Feature aktivieren, deaktivieren und verwenden.
ms.custom: SEO-VS-2020
ms.date: 02/13/2019
ms.topic: how-to
ms.assetid: 0f0df097-bbaf-46ad-9ad1-ef5f40435079
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2c902147bd1b7761bb6fdab1bc577af6a1990bed
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903882"
---
# <a name="debug-only-user-code-with-just-my-code"></a>Debuggen von Benutzercode mit nur eigenem Code

*Nur eigenen Code* ist ein Visual Studio-Debugfeature, das automatisch Aufrufe von System-, Framework- und anderem Nichtbenutzercode überspringt. Im Fenster **Aufrufstapel** werden diese Aufrufe von „Nur eigenen Code“ in Frames mit **[externem Code]** reduziert.

„Nur eigenen Code“ funktioniert in .NET-, C++- und JavaScript-Projekten unterschiedlich.

## <a name="enable-or-disable-just-my-code"></a><a name="BKMK_Enable_or_disable_Just_My_Code"></a> Aktivieren oder Deaktivieren von „Nur eigenen Code“

Für die meisten Programmiersprachen ist „Nur eigenen Code“ standardmäßig aktiviert.

- Um „Nur eigenen Code“ in Visual Studio zu aktivieren bzw. zu deaktivieren, aktivieren bzw. deaktivieren Sie unter **Extras** > **Optionen** (oder **Debuggen** > **Optionen**) > **Debugging** > **Allgemein** die Option **Nur meinen Code aktivieren**.

![„Nur meinen Code aktivieren“ im Dialogfeld „Optionen“](../debugger/media/dbg_justmycode_options.png "Nur meinen Code aktivieren")

> [!NOTE]
> **Nur meinen Code aktivieren** ist eine globale Einstellung, die auf alle Visual Studio-Projekte in allen Sprachen angewendet wird.

## <a name="just-my-code-debugging"></a>Nur mein Code (Debugoption)

Während einer Debugsitzung wird im Fenster **Module** zusammen mit dem jeweiligen Symbolladestatus angezeigt, welche Codemodule vom Debugger als eigener Code (Benutzercode) behandelt werden. Weitere Informationen erhalten Sie unter [Informieren Sie sich darüber, wie der Debugger an Ihre App angefügt wird](../debugger/debugger-tips-and-tricks.md#modules_window).

![Benutzercode im Fenster „Module“](../debugger/media/dbg_justmycode_module.png "Benutzercode im Fenster „Module“")

Im Fenster **Aufrufstapel** oder **Tasks** wird Nichtbenutzercode von „Nur eigenen Code“ in einen grauen, kommentierten Codeframe mit der Bezeichnung `[External Code]` reduziert.

![Externer Codeframe im Fenster „Aufrufstapel“](../debugger/media/dbg_justmycode_externalcode.png "Frame mit externem Code")

>[!TIP]
>Zum Öffnen von **Module**, **Aufrufstapel**, **Tasks** oder der meisten anderen Debugfenster müssen Sie sich in einer Debugsitzung befinden. Wählen Sie während des Debuggens unter **Debuggen** > **Fenster** die Fenster aus, die Sie öffnen möchten.

<a name="BKMK_Override_call_stack_filtering"></a> Um den Code in einem reduzierten Frame mit **[externem Code]** anzuzeigen, klicken Sie mit der rechten Maustaste in das Fenster **Aufrufstapel** oder **Tasks** und wählen Sie im Kontextmenü **Externen Code anzeigen** aus. Die erweiterten externen Codezeilen ersetzen den Frame mit **[externem Code]** .

![Anzeigen von externem Code im Fenster „Aufrufstapel“](../debugger/media/dbg_justmycode_showexternalcode.png "Externen Code anzeigen")

> [!NOTE]
> **Externen Code anzeigen** ist eine aktuelle Benutzerprofileinstellung, die für alle Projekte in allen Sprachen gilt, die vom Benutzer geöffnet werden.

Durch Doppelklicken auf eine erweiterte externe Codezeile im Fenster **Aufrufstapel** wird die aufrufende Codezeile im Quellcode in Grün hervorgehoben. Bei DLLs oder anderen Modulen, die nicht gefunden oder geladen wurden, kann sich eine Seite „Symbol oder Quelle nicht gefunden“ öffnen.

## <a name="net-just-my-code"></a><a name="BKMK__NET_Framework_Just_My_Code"></a>„Nur eigenen Code“ in .NET

In .NET-Projekten werden von „Nur eigenen Code“ Symboldateien ( *. pdb*) und Programmoptimierungen verwendet, um Benutzer- und Nichtbenutzercode zu klassifizieren. Der .NET-Debugger betrachtet optimierte Binärdateien und nicht geladene *.pdb*-Dateien als Nichtbenutzercode.

Drei Compilerattribute beeinflussen außerdem, was der .NET-Debugger als Benutzercode ansieht:

- <xref:System.Diagnostics.DebuggerNonUserCodeAttribute> teilt dem Debugger mit, dass der Code, auf den er angewendet wird, kein Benutzercode ist.
- <xref:System.Diagnostics.DebuggerHiddenAttribute> blendet den Code für den Debugger aus, auch wenn Nur mein Code deaktiviert wird.
- <xref:System.Diagnostics.DebuggerStepThroughAttribute> veranlasst den Debugger, den vorliegenden Code nicht in Einzelschritten, sondern in Prozedurschritten zu durchlaufen.

Der .NET-Debugger betrachtet den gesamten anderen Code als Benutzercode.

Beim .NET-Debuggen:

- **Debuggen** > **Einzelschritt** (oder **F11**) in Nichtbenutzercode überspringt den Code bis zur nächsten Zeile des Benutzercodes.
- **Debuggen** > **Rücksprung** (oder **UMSCHALT**+**F11**) in Nichtbenutzercode springt zurück zur nächsten Zeile des Benutzercodes.

Wenn kein Benutzercode mehr vorhanden ist, wird das Debuggen bis zum Ende fortgesetzt, es wird ein weiterer Haltepunkt erreicht oder ein Fehler ausgelöst.

<a name="BKMK_NET_Breakpoint_behavior"></a> Wenn der Debugger Nichtbenutzercode unterbricht (z. B., wenn Sie **Debuggen** > **Alle unterbrechen** verwenden und Nichtbenutzercode anhalten), wird das Fenster **Keine Quelle** angezeigt. Sie können dann über den Befehl **Debuggen** > **Schritt** zur nächsten Zeile des Benutzercodes wechseln.

Wenn ein Ausnahmefehler im Nichtbenutzercode auftritt, unterbricht der Debugger an der Benutzercodezeile, in der die Ausnahme generiert wurde.

Wenn Ausnahmen (erste Chance) für die Ausnahme aktiviert sind, wird die aufrufende Benutzercodezeile im Quellcode grün hervorgehoben. Im Fenster **Aufrufstapel** wird ein mit Anmerkungen versehener Frame mit der Bezeichnung **[Externer Code]** angezeigt.

## <a name="c-just-my-code"></a><a name="BKMK_C___Just_My_Code"></a> „Nur eigenen Code“ in C++

Ab Visual Studio 2017, Version 15.8, wird „Nur eigenen Code“ für die Codeausführung unterstützt. Diese Funktion erfordert auch die Verwendung des Compilerschalters [/JMC (Debuggen von „Nur eigenen Code“)](/cpp/build/reference/jmc). Der Schalter ist in C++-Projekten standardmäßig aktiviert. Für das Fenster **Aufrufstapel** und die Unterstützung des Aufrufstapels in „Nur eigenen Code“ ist der /JMC-Schalter nicht erforderlich.

<a name="BKMK_CPP_User_and_non_user_code"></a> Für die Klassifizierung als Benutzercode muss die PDB für die Binärdatei, die den Benutzercode enthält, vom Debugger geladen werden (über das Fenster **Module** können Sie dies überprüfen).

Für das Verhalten von Aufrufstapeln, wie z. B. im Fenster **Aufrufstapel**, betrachtet „Nur eigenen Code“ in C++ nur diese Funktionen als *Nichtbenutzercode*:

- Funktionen mit entfernten Quellinformationen in ihrer Symboldatei.
- Funktionen, bei denen die Symboldateien angeben, dass keine Quelldatei vorhanden ist, die dem Stapelrahmen entspricht.
- Funktionen, die in *\*.natjmc*-Dateien im Ordner *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers* angegeben werden.

Für das Verhalten bei der Codeausführung betrachtet „Nur eigenen Code“ in C++ nur diese Funktionen als *Nichtbenutzercode*:

- Funktionen, für die die entsprechende PDB-Datei nicht in den Debugger geladen wurde.
- Funktionen, die in *\*.natjmc*-Dateien im Ordner *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers* angegeben werden.

> [!NOTE]
> Für die Unterstützung von Codeschritten in „Nur eigenen Code“ muss C++-Code mit den MSVC-Compilern in Visual Studio 15.8 Vorschauversion 3 oder höher kompiliert werden, und der /JMC-Compilerschalter muss aktiviert sein (er ist standardmäßig aktiviert). Weitere Informationen finden Sie unter [Customize C++ call stack and code stepping behavior](#BKMK_CPP_Customize_call_stack_behavior) (Anpassen des Verhaltens für C++-Aufrufsstapel und -Codeschritte) und dieses [Blogbeitrags](https://devblogs.microsoft.com/cppblog/announcing-jmc-stepping-in-visual-studio/). Für Code, der mit einem älteren Compiler kompiliert wurde, sind *.natstepfilter*-Dateien die einzige Möglichkeit, das Codeschrittverhalten unabhängig von „Nur eigenen Code“ anzupassen. Weitere Informationen finden Sie unter [Anpassen C++-Schrittverhaltens unabhängig von den Einstellungen für „Nur eigenen Code“](#BKMK_CPP_Customize_stepping_behavior)

<a name="BKMK_CPP_Stepping_behavior"></a> Beim C++-Debuggen:

- **Debuggen** > **Einzelschritt** (oder **F11**) in Nichtbenutzercode überspringt den Code bis zur nächsten Zeile des Benutzercodes.
- **Debuggen** > **Rücksprung** (oder **UMSCHALT**+**F11**) in Nichtbenutzercode springt zurück zur nächsten Zeile des Benutzercodes.

Wenn kein Benutzercode mehr vorhanden ist, wird das Debuggen bis zum Ende fortgesetzt, es wird ein weiterer Haltepunkt erreicht oder ein Fehler ausgelöst.

Wenn der Debugger den Nichtbenutzercode unterbricht (zum Beispiel, wenn Sie **Debuggen** > **Alle unterbrechen** verwenden und Nichtbenutzercode anhalten), wird die schrittweise Ausführung im Nichtbenutzercode weitergeführt.

Wenn der Debugger auf eine Ausnahme trifft, hält er bei der Ausnahme an, unabhängig davon, ob sie im Benutzer- oder Nichtbenutzercode auftritt. Die Optionen **Vom Benutzercode unbehandelt** im Dialogfeld **Ausnahmeeinstellungen** werden ignoriert.

### <a name="customize-c-call-stack-and-code-stepping-behavior"></a><a name="BKMK_CPP_Customize_call_stack_behavior"></a> Anpassen des Verhaltens von C++-Aufrufsstapel und -Codeschritten

Für C++-Projekte können Sie die Module, Quelldateien und Funktionen angeben, die das Fenster **Aufrufstapel** als Nichtbenutzercode behandelt, indem Sie sie in *\*.natjmc*-Dateien festlegen. Diese Anpassung gilt auch für Codeschritte, wenn Sie den neuesten Compiler verwenden (siehe [„Nur eigenen Code“ in C++](#BKMK_CPP_User_and_non_user_code)).

- Fügen Sie dem Ordner *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers* die *NATJMC*-Datei hinzu, um Nichtbenutzercode aller Benutzer des Visual Studio-Computers anzugeben.
- Fügen Sie dem Ordner *%USERPROFILE%\Eigene Dokumente\\<Visual Studio-Version\>\Visualizers* die *.natjmc*-Datei hinzu, um Nichtbenutzercode für einen einzelnen Benutzer anzugeben.

Eine *.natjmc*-Datei ist eine XML-Datei mit der folgenden Syntax:

```xml
<?xml version="1.0" encoding="utf-8"?>
<NonUserCode xmlns="http://schemas.microsoft.com/vstudio/debugger/jmc/2015">

  <!-- Modules -->
  <Module Name="ModuleSpec" />
  <Module Name="ModuleSpec" Company="CompanyName" />

  <!-- Files -->
  <File Name="FileSpec"/>

  <!-- Functions -->
  <Function Name="FunctionSpec" />
  <Function Name="FunctionSpec" Module ="ModuleSpec" />
  <Function Name="FunctionSpec" Module ="ModuleSpec" ExceptionImplementation="true" />

</NonUserCode>

```

 **Modulelementattribute**

|Attribut|BESCHREIBUNG|
|---------------|-----------------|
|`Name`|Erforderlich. Der vollständige Pfad des Moduls oder der Module. Sie können die Windows-Platzhalterzeichen `?` (null oder ein Zeichen) und `*` (null oder mehr Zeichen) verwenden. Ein auf ein Objekt angewendeter<br /><br /> `<Module Name="?:\3rdParty\UtilLibs\*" />`<br /><br /> weist den Debugger an, alle Module in *\3rdParty\UtilLibs* auf einem Laufwerk als externen Code zu behandeln.|
|`Company`|Dies ist optional. Der Name des Unternehmens, das das Modul veröffentlicht, das in die ausführbare Datei eingebettet ist. Sie können dieses Attribut verwenden, um die Module zu unterscheiden.|

 **Dateielementattribute**

|Attribut|BESCHREIBUNG|
|---------------|-----------------|
|`Name`|Erforderlich. Der vollständige Pfad der Quelldatei oder -dateien, die als externer Code behandelt werden sollen. Sie können die Windows-Platzhalterzeichen `?` und `*` verwenden, wenn Sie den Pfad angeben.|

 **Funktionselementattribute**

|Attribut|BESCHREIBUNG|
|---------------|-----------------|
|`Name`|Erforderlich. Der vollqualifizierte Name der Funktion, die als externer Code behandelt werden soll.|
|`Module`|Dies ist optional. Der Name oder der vollständige Pfad zu dem Modul, das die Funktion enthält. Sie können dieses Attribut verwenden, um Funktionen mit demselben Namen zu unterscheiden.|
|`ExceptionImplementation`|Bei Festlegung auf `true` zeigt die Aufrufliste die Funktion an, die die Ausnahme und nicht diese Funktion ausgelöst hat.|

### <a name="customize-c-stepping-behavior-independent-of-just-my-code-settings"></a><a name="BKMK_CPP_Customize_stepping_behavior"></a> Anpassen C++-Schrittverhaltens unabhängig von den Einstellungen für „Nur eigenen Code“

In C++-Projekten können Sie Funktionen angeben, die zu überspringen sind, indem Sie sie als Nichtbenutzercode in *\*.natstepfilter*-Dateien auflisten. Die in *\*.natstepfilter*-Dateien aufgeführten Funktionen sind nicht von Einstellungen für „Nur eigenen Code“ abhängig.

- Um Nichtbenutzercode für alle lokalen Visual Studio-Benutzer anzugeben, fügen Sie dem Ordner *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers* die *.natstepfilter*-Datei hinzu.
- Fügen Sie dem Ordner *%USERPROFILE%\Eigene Dokumente\\<Visual Studio-Version\>\Visualizers* die *.natstepfilter*-Datei hinzu, um Nichtbenutzercode für einen einzelnen Benutzer anzugeben.

Eine *.natstepfilter*-Datei ist eine XML-Datei mit der folgenden Syntax:

```xml
<?xml version="1.0" encoding="utf-8"?>
<StepFilter xmlns="http://schemas.microsoft.com/vstudio/debugger/natstepfilter/2010">
    <Function>
        <Name>FunctionSpec</Name>
        <Action>StepAction</Action>
    </Function>
    <Function>
        <Name>FunctionSpec</Name>
        <Module>ModuleSpec</Module>
        <Action>StepAction</Action>
    </Function>
</StepFilter>

```

|Element|BESCHREIBUNG|
|-------------|-----------------|
|`Function`|Erforderlich. Gibt eine oder mehreren Funktionen als Nichtbenutzerfunktionen an.|
|`Name`|Erforderlich. Ein ECMA-262-formatierter regulärer Ausdruck, der den vollständigen Funktionsnamen angibt, der übereinstimmen muss. Zum Beispiel:<br /><br /> `<Name>MyNS::MyClass.*</Name>`<br /><br /> teilt dem Debugger mit, dass alle Methoden in `MyNS::MyClass` als Nichtbenutzercode behandelt werden sollen. Bei der Übereinstimmung muss die Groß-/Kleinschreibung beachtet werden.|
|`Module`|Dies ist optional. Ein ECMA-262-formatierter regulärer Ausdruck, der den vollständigen Pfad zu dem Modul angibt, das die Funktion enthält. Die Groß- und Kleinschreibung wird bei der Übereinstimmung nicht berücksichtigt.|
|`Action`|Erforderlich. Einer dieser Werte, bei denen die Groß-/Kleinschreibung beachtet werden muss.<br /><br /> `NoStepInto` – weist den Debugger an, die Funktion zu überspringen.<br /> `StepInto` – weist den Debugger an, die Funktion schrittweise auszuführen, wobei alle anderen `NoStepInto` für die übereinstimmende Funktion überschrieben werden.|

## <a name="javascript-just-my-code"></a><a name="BKMK_JavaScript_Just_My_Code"></a> „Nur eigenen Code“ in JavaScript

<a name="BKMK_JS_User_and_non_user_code"></a> „Nur eigenen Code“ in JavaScript steuert die Einzelschrittausführung und die Aufruflistenanzeige durch Kategorisieren von Code in einer dieser Klassifizierungen:

|Klassifizierung|Beschreibung|
|-|-|
|**MyCode**|Benutzercode, den Sie besitzen und steuern.|
|**LibraryCode**|Nichtbenutzercode aus Bibliotheken, den Sie regelmäßig verwenden und die für das ordnungsgemäße Funktionieren Ihrer Anwendung erforderlich sind (z. B. WinJS oder jQuery).|
|**UnrelatedCode**|Nichtbenutzercode in Ihrer Anwendung, den Sie nicht besitzen und auf den Ihre Anwendung nicht zurückgreift, um korrekt zu funktionieren. Beispielsweise könnte ein SDK für Werbung, das Anzeigen anzeigt, UnrelatedCode sein. In UWP-Projekten gilt jeder Code, der von einem HTTP- oder HTTPS-URI in Ihre Anwendung geladen wird, als UnrelatedCode.|

Der JavaScript-Debugger klassifiziert Code als Benutzer- oder Nichtbenutzercode in dieser Reihenfolge:

1. Die Standardklassifizierungen.
   - Skript, das ausgeführt wird, indem eine Zeichenfolge an die vom Host bereitgestellte `eval`-Funktion übergeben wird, lautet **MyCode**.
   - Skript, das ausgeführt wird, indem eine Zeichenfolge an den `Function`-Konstruktor übergeben wird, lautet **LibraryCode**.
   - Skript, das in einem Frameworkverweis, wie etwa WinJS oder dem Azure SDK, enthalten ist, wird als **LibraryCode** klassifiziert.
   - Skript, das ausgeführt wird, indem eine Zeichenfolge an die Funktionen `setTimeout`, `setImmediate` oder `setInterval` übergeben wird, ist **UnrelatedCode**.

2. Klassifikationen, die für alle JavaScript-Projekte in Visual Studio in der Datei *%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json* angegeben sind.

3. Klassifizierungen in der *mycode.json*-Datei des aktuellen Projekts.

Jeder Klassifizierungsschritt überschreibt die vorherigen Schritte.

Der restliche Code wird als **MyCode** klassifiziert.

Sie können die Standardklassifizierungen ändern und bestimmte Dateien und URLs als Benutzer- oder Nichtbenutzercode klassifizieren, indem Sie eine *.json*-Datei namens *mycode.json* zum Stammordner eines JavaScript-Projekts hinzufügen. Weitere Informationen finden Sie unter [Anpassen von „Nur eigenen Code“ in JavaScript](#BKMK_JS_Customize_Just_My_Code).

<a name="BKMK_JS_Stepping_behavior"></a> Beim JavaScript-Debuggen:

- Wenn es sich bei einer Funktion um Nichtbenutzercode handelt, entspricht das Verhalten von **Debuggen** > **Einzelschritt** (oder **F11**) dem Verhalten von **Debuggen** > **Rücksprung** (oder **F10**).
- Wenn ein Schritt im Nichtbenutzercode (**LibraryCode** oder **UnrelatedCode**) beginnt, dann verhält sich die schrittweise Ausführung kurzfristig so, als wäre „Nur eigenen Code“ nicht aktiviert. Sobald Sie zurück zum Benutzercode wechseln, wird die schrittweise Ausführung für „Nur eigenen Code“ erneut aktiviert.
- Wenn ein Benutzercodeschritt dazu führt, dass der aktuelle Ausführungskontext verlassen wird, hält der Debugger bei der nächsten ausgeführten Benutzercodezeile an. Wenn beispielsweise ein Rückruf in **LibraryCode**-Code ausgeführt wird, fährt der Debugger fort, bis die nächste Zeile des Benutzercodes ausgeführt wird.
- **Rücksprung** (oder **UMSCHALT**+**F11**) hält in der nächsten Zeile des Benutzercodes an.

Wenn kein Benutzercode mehr vorhanden ist, wird das Debuggen bis zum Ende fortgesetzt, es wird ein weiterer Haltepunkt erreicht oder ein Fehler ausgelöst.

Im Code gesetzte Haltepunkte werden immer getroffen, jedoch ist der Code klassifiziert.

- Wenn das `debugger`-Schlüsselwort in **LibraryCode** vorkommt, unterbricht der Debugger immer die Ausführung.
- Wenn das `debugger`-Schlüsselwort in **UnrelatedCode** vorkommt, stoppt der Debugger nicht.

<a name="BKMK_JS_Exception_behavior"></a> Wenn eine nicht behandelte Ausnahme in **MyCode** oder **LibraryCode**-Code auftritt, unterbricht der Debugger immer die Ausführung.

Wenn eine nicht behandelte Ausnahme in **UnrelatedCode** auftritt und sich **MyCode** oder **LibraryCode** im Aufrufstapel befindet, unterbricht der Debugger die Ausführung.

Wenn Ausnahmen (erste Chance) für die Ausnahme aktiviert sind und die Ausnahme in **LibraryCode** oder **UnrelatedCode** ausgelöst wird:

- Wenn die Ausnahme behandelt wird, unterbricht der Debugger nicht.
- Wenn die Ausnahme nicht behandelt wird, unterbricht der Debugger.

### <a name="customize-javascript-just-my-code"></a><a name="BKMK_JS_Customize_Just_My_Code"></a> Anpassen von „Nur eigenen Code“ in JavaScript

Um Benutzer- und Nichtbenutzercode für ein einzelnes JavaScript-Projekt zu kategorisieren, können Sie dem Stammordner des Projekts eine *.json*-Datei mit dem Namen *mycode.json* hinzufügen.

Die Spezifikationen in dieser Datei setzen die Standardklassifizierungen und die Datei *mycode.default.wwa.json* außer Kraft. Die *mycode.json*-Datei muss nicht alle Schlüssel-Wert-Paare auflisten. Die Werte **MyCode**, **Libraries** und **Unrelated** können leere Arrays sein.

*Mycode.json*-Dateien verwenden folgende Syntax:

```json
{
    "Eval" : "Classification",
    "Function" : "Classification",
    "ScriptBlock" : "Classification",
    "MyCode" : [
        "UrlOrFileSpec",
        . . .
        "UrlOrFileSpec"
    ],
    "Libraries" : [
        "UrlOrFileSpec",
        . .
        "UrlOrFileSpec"
    ],
    "Unrelated" : [
        "UrlOrFileSpec",
        . . .
        "UrlOrFileSpec"
    ]
}

```

**Eval, Function und ScriptBlock**

Die Schlüsselwertpaare **Eval**, **Function** und **ScriptBlock** bestimmen, wie dynamisch erzeugter Code klassifiziert wird:

|name|Beschreibung|
|-|-|
|**Eval**|Skript, das ausgeführt wird, indem eine Zeichenfolge an die vom Host bereitgestellte `eval`-Funktion übergeben wird. Standardmäßig wird ein Eval-Skript als **MyCode** klassifiziert.|
|**Function**|Skript, das ausgeführt wird, indem eine Zeichenfolge an den `Function`-Konstruktor übergeben wird. Standardmäßig wird ein Function-Skript als **LibraryCode** klassifiziert.|
|**ScriptBlock**|Skript, das ausgeführt wird, indem eine Zeichenfolge an die Funktionen `setTimeout`, `setImmediate` oder `setInterval` übergeben wird. Standardmäßig wird ein ScriptBlock-Skript als **UnrelatedCode** klassifiziert.|

Sie können den Wert auf eines dieser Schlüsselwörter ändern:

- `MyCode` klassifiziert das Skript als **MyCode**.
- `Library` klassifiziert das Skript als **LibraryCode**.
- `Unrelated` klassifiziert das Skript als **UnrelatedCode**.

**MyCode, Libraries und Unrelated**

Die Schlüsselwertpaare **MyCode**, **Libraries** und **Unrelated** geben die URLs oder Dateien an, die Sie in eine Klassifikation einschließen möchten:

|name|Beschreibung|
|-|-|
|**MyCode**|Ein Array von URLs oder Dateien, die als **MyCode** klassifiziert werden.|
|**Libraries**|Ein Array von URLs oder Dateien, die als **LibraryCode** klassifiziert werden.|
|**Unrelated**|Ein Array von URLs oder Dateien, die als **UnrelatedCode** klassifiziert werden.|

Die URL-Zeichenfolge oder Dateizeichenfolge kann eine oder mehrere `*`-Zeichen enthalten, die mit null oder mehr Zeichen übereinstimmen. `*` entspricht dem regulären Ausdruck `.*`.
