---
title: Seite "Erstellen", Projekt-Designer (C#)
description: Hier erfahren Sie, wie Sie die Seite „Erstellen“ des Projekt-Designers in Visual Studio verwenden, um die Buildkonfigurationseigenschaften des Projekts anzugeben.
ms.custom: SEO-VS-2020
ms.date: 06/20/2017
ms.technology: vs-ide-compile
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesBuild
helpviewer_keywords:
- Build options [C#]
- Project Designer, Build page
ms.assetid: 77ff1bfc-d633-4634-ba29-9afdb6d7e362
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: f8c3409c7ba62f1deb628645b624a40de4cbeaff
ms.sourcegitcommit: c9a84e6c01e12ccda9ec7072dd524830007e02a3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2020
ms.locfileid: "92136874"
---
# <a name="build-page-project-designer-c"></a>Seite "Erstellen", Projekt-Designer (C#)

Verwenden Sie die Seite **Erstellen** des **Projekt-Designers** , um die Buildkonfigurationseigenschaften des Projekts anzugeben. Diese Seite bezieht sich nur auf [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]-Projekte.

Um auf die Seite **Erstellen** zuzugreifen, wählen Sie einen Projektknoten (nicht den Knoten **Projektmappe** ) im **Projektmappen-Explorer** . Wählen Sie anschließend im Menü **Ansicht** , **Eigenschaftenseiten** aus. Sobald der Projekt-Designer angezeigt wird, wählen Sie die Registerkarte **Erstellen** aus.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="configuration-and-platform"></a>Konfiguration und Plattform

Die folgenden Optionen ermöglichen es Ihnen, die anzuzeigende bzw. zu ändernde Konfiguration und Plattform auszuwählen.

> [!NOTE]
> Mit vereinfachten Buildkonfigurationen bestimmt das Projektsystem, ob eine Debug- oder eine Releaseversion erstellt werden soll. Deshalb werden diese Optionen nicht angezeigt. Weitere Informationen finden Sie unter [Vorgehensweise: Festlegen von Debug- und Releasekonfigurationen](../../debugger/how-to-set-debug-and-release-configurations.md).

**Konfiguration**

Gibt an, welche Konfigurationseinstellungen angezeigt oder geändert werden sollen. Es stehen die Einstellungen **Aktiv (Debuggen)** (Standard), **Debuggen** , **Release** oder **Alle Konfigurationen** zur Verfügung.

**Plattform**

Gibt an, welche Plattformeinstellungen angezeigt oder geändert werden sollen. Die Standardeinstellung ist **Aktiv (Any CPU)** . Sie können die aktive Plattform mit dem **Konfigurations-Manager** ändern. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen und Bearbeiten von Konfigurationen](../../ide/how-to-create-and-edit-configurations.md).

## <a name="general"></a>Allgemein

Die folgenden Optionen ermöglichen es Ihnen, einige C#-Compilereinstellungen zu konfigurieren.

**Symbole für bedingte Kompilierung**

Gibt Symbole an, für die eine bedingte Kompilierung durchgeführt werden soll. Trennen Sie Symbole mit einem Semikolon („;“). Weitere Informationen finden Sie unter [/define (C# Compiler Options)](/dotnet/csharp/language-reference/compiler-options/define-compiler-option).

**DEBUG-Konstante definieren**

Definiert DEBUGGEN als Symbol in allen Quellcodedateien Ihrer App. Die Auswahl dieser Option entspricht der Verwendung der Befehlszeilenoption `/define:DEBUG`.

**TRACE-Konstante definieren**

Definiert TRACE als Symbol in allen Quellcodedateien Ihrer App. Die Auswahl dieser Option entspricht der Verwendung der Befehlszeilenoption `/define:TRACE`.

**Zielplattform**

Gibt den Prozessor an, für den die Ausgabedatei konfiguriert ist. Wählen Sie für jeden Intel-kompatiblen 32-Bit-Prozessor **x86** , für jeden Intel-kompatiblen 64-Bit-Prozessor **x64** und für ARM-Prozessoren **ARM** aus, oder wählen Sie **Any CPU** , um anzugeben, dass jeder Prozessor zulässig ist. **Any CPU** (Beliebige CPU) ist der Standardwert für Projekte, da die Anwendung hiermit auf möglichst vielen Geräten ausgeführt werden kann.

Weitere Informationen finden Sie unter [/platform (C# Compiler Options)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option).

**NULL zulassen**

Gibt projektübergreifend den C#-Nullable-Kontext an. Diese UI-Option wurde in Visual Studio 16.5 eingeführt und ist nur in Projekten verfügbar, die C# 8.0 oder höher verwenden.

Weitere Informationen finden Sie unter [Nullwerte zulassende Verweistypen – Nullable-Kontexte](/dotnet/csharp/nullable-references#nullable-contexts).

**32-Bit bevorzugen**

Wenn das Kontrollkästchen **32-Bit bevorzugen** ausgewählt wird, wird die Anwendung auf den 32-Bit- und 64-Bit-Versionen von Windows als 32-Bit-Anwendung ausgeführt. Wenn das Kontrollkästchen deaktiviert ist, wird die Anwendung auf 32-Bit-Versionen von Windows als 32-Bit-Anwendung und auf 64-Bit-Versionen von Windows als 64-Bit-Anwendung ausgeführt.

Wenn Sie eine Anwendung als 64-Bit-Anwendung ausführen, wird die Zeigergröße verdoppelt und es können Kompatibilitätsprobleme mit anderen Bibliotheken auftreten, die ausschließlich 32-Bit verwenden. Es ist sinnvoll, eine 64-Bit-Anwendung nur auszuführen, wenn sie mehr als 4 GB Arbeitsspeicher erfordert oder 64-Bit-Anweisungen eine beträchtliche Leistungssteigerung darstellen.

Dieses Kontrollkästchen ist nur verfügbar, wenn die folgenden Bedingungen zutreffen:

- Auf der Seite **Erstellen** ist die Liste **Plattformziel** auf **Any CPU** festgelegt.

- Auf der Seite **Anwendung** wird in der Liste **Ausgabetyp** angegeben, dass das Projekt eine Anwendung ist.

- Auf der Seite **Anwendung** ist in der Liste **Zielframework** „.NET Framework 4.5“ angegeben.

**Unsicheren Code zulassen**

Ermöglicht das Kompilieren von Code, der das [unsafe](/dotnet/csharp/language-reference/keywords/unsafe)-Schlüsselwort verwendet. Weitere Informationen finden Sie unter [/unsafe (C# Compiler Options](/dotnet/csharp/language-reference/compiler-options/unsafe-compiler-option).

**Code optimieren**

Aktiviert oder deaktiviert die vom Compiler durchgeführten Optimierungen, damit Ihre Ausgabedatei kleiner, schneller und effizienter wird. Weitere Informationen finden Sie unter [/optimize (C# Compiler Options)](/dotnet/csharp/language-reference/compiler-options/optimize-compiler-option).

## <a name="errors-and-warnings"></a>Fehler und Warnungen

Die folgenden Einstellungen werden verwendet, um Optionen zu Fehlern und Warnungen für den Buildvorgang zu konfigurieren.

**Warnstufe**

Gibt die anzuzeigende Stufe für Compiler-Warnungen an. Weitere Informationen finden Sie unter [/warn (C# Compiler Options)](/dotnet/csharp/language-reference/compiler-options/warn-compiler-option).

**Unterdrücken von Warnungen**

Unterdrückt die Compilerfunktion zum Generieren einer oder mehrerer Warnungen. Trennen Sie mehrere Warnungsnummern jeweils durch ein Komma oder Semikolon voneinander. Weitere Informationen finden Sie unter [/nowarn (C# Compiler Options)](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option).

## <a name="treat-warnings-as-errors"></a>Warnungen als Fehler behandeln

Die folgenden Einstellungen werden verwendet, um anzugeben, welche Warnungen als Fehler behandelt werden. Wählen Sie eine der folgenden Optionen aus, um die Bedingungen anzugeben, unter denen beim Auftreten einer Warnung im Buildvorgang ein Fehler zurückgegeben wird. Weitere Informationen finden Sie unter [/warnaserror (C# Compiler Options)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).

**Keine:** Warnungen werden nicht als Fehler behandelt.

**Alle:** Alle Warnungen werden als Fehler behandelt.

**Bestimmte Warnungen:** Die angegebenen Warnungen werden als Fehler behandelt. Trennen Sie mehrere Warnungsnummern jeweils durch ein Komma oder Semikolon voneinander.

> [!TIP]
> Wenn keine Warnungen der Codeanalyse als Fehler behandelt werden sollen, sehen Sie sich die [Häufig gestellten Fragen zur Codeanalyse](../../code-quality/analyzers-faq.md#treat-warnings-as-errors) an.

## <a name="output"></a>Output

Die folgenden Einstellungen werden verwendet, um die Ausgabeoptionen für den Buildvorgang zu konfigurieren.

**Ausgabepfad**

Legt den Speicherort der Ausgabedateien für die Konfiguration des Projekts fest. Geben Sie den Pfad der Buildausgabe in dieses Feld ein, oder wählen Sie die Schaltfläche **Durchsuchen** , um einen Pfad anzugeben. Der Pfad ist relativ. Wenn Sie einen absoluten Pfad eingeben, wird dieser als relativer Pfad gespeichert. Der Standardpfad lautet bin\Debug\ oder bin\Release\\.

Mit vereinfachten Buildkonfigurationen bestimmt das Projektsystem, ob eine Debug- oder eine Releaseversion erstellt werden soll. Mit dem Befehl **Erstellen** im Menü **Debuggen** (F5) wird der Build unabhängig vom angegebenen **Ausgabepfad** am Debugspeicherort abgelegt. Mit dem Befehl **Erstellen** im Menü **Erstellen** hingegen wird er an dem Speicherort abgelegt, den Sie angeben. Weitere Informationen finden Sie unter [Grundlagen der Buildkonfiguration](../../ide/understanding-build-configurations.md).

**XML-Dokumentationsdatei**

Gibt den Namen der Datei an, in der die Dokumentationskommentare verarbeitet werden. Weitere Informationen finden Sie unter [/doc (C# Compiler Options)](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option).

**Für COM-Interop registrieren**

Legt fest, dass die verwaltete Anwendung ein COM-Objekt (einen COM Callable Wrapper) verfügbar macht, der einem COM-Objekt die Interaktion mit der verwalteten Anwendung ermöglicht. Die Eigenschaft **Ausgabetyp** auf der Seite [Anwendung](../../ide/reference/application-page-project-designer-visual-basic.md) des **Projekt-Designers** muss für diese Anwendung auf **Klassenbibliothek** festgelegt werden, damit die Eigenschaft **Für COM-Interop registrieren** verfügbar ist. Eine Beispielklasse, die Sie in die [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]-Anwendung aufnehmen und als COM-Objekt verfügbar machen können, finden Sie unter [COM-Beispielklasse](/dotnet/csharp/programming-guide/interop/example-com-class).

**Serialisierungsassembly generieren**

Gibt an, ob der Compiler das XML Serializer Generator-Tool (Sgen.exe) verwendet, um XML-Serialisierungsassemblys zu erstellen. Serialisierungsassemblys können die Startleistung von <xref:System.Xml.Serialization.XmlSerializer> verbessern, sofern Sie diese Klasse zum Serialisieren von Typen im Code verwendet haben. Standardmäßig ist diese Option auf **Auto** festgelegt, d.h., es werden nur dann Serialisierungsassemblys generiert, wenn Sie <xref:System.Xml.Serialization.XmlSerializer> verwendet haben, um Typen im Code in XML zu codieren. **Aus** gibt an, dass grundsätzlich keine Serialisierungsassemblys generiert werden, unabhängig davon, ob im Code <xref:System.Xml.Serialization.XmlSerializer> verwendet wird. **Ein** gibt an, dass immer Serialisierungsassemblys generiert werden. Serialisierungsassemblys tragen den Namen `TypeName`.XmlSerializers.dll. Weitere Informationen finden Sie unter [XML Serializer Generator-Tool (Sgen.exe)](/dotnet/framework/serialization/xml-serializer-generator-tool-sgen-exe).

**Erweitert**

Klicken Sie darauf, um das [Dialogfeld „Erweiterte Buildeinstellungen“ (C#)](../../ide/reference/advanced-build-settings-dialog-box-csharp.md) anzuzeigen.

## <a name="see-also"></a>Siehe auch

- [Projekteigenschaftenverweise](../../ide/reference/project-properties-reference.md)
- [C#-Compileroptionen](/dotnet/csharp/language-reference/compiler-options/index)
