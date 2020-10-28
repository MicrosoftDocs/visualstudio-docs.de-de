---
title: Seite "Kompilieren", Projekt-Designer (Visual Basic)
description: Hier erfahren Sie, wie Sie Kompilierungsanweisungen in Visual Studio angeben. Sie können auch erweiterte Compileroptionen und Präbuild- oder Postbuildereignisse auf dieser Seite angeben.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesCompile
helpviewer_keywords:
- compilation, Visual Basic projects
- compilation, options [Visual Basic]
- compilers, Visual Basic options
- compilation, instructions [Visual Basic]
- compiler options, Visual Basic
- Project Designer, Compile page
- Compile page in Project Designer
ms.assetid: b2a80230-906e-4e85-b3e0-fcd9c40426e1
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 60172d9e308e38967f5ab5a8d882057e78f083c8
ms.sourcegitcommit: c9a84e6c01e12ccda9ec7072dd524830007e02a3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2020
ms.locfileid: "92136627"
---
# <a name="compile-page-project-designer-visual-basic"></a>Seite "Kompilieren", Projekt-Designer (Visual Basic)

Verwenden Sie die Seite **Kompilieren** des Projekt-Designers, um Kompilieranweisungen festzulegen. Sie können auch erweiterte Compileroptionen und Präbuild- oder Postbuildereignisse auf dieser Seite angeben.

Um auf die Seite **Kompilieren** zuzugreifen, wählen Sie einen Projektknoten (nicht den Knoten **Projektmappe** ) im **Projektmappen-Explorer** . Wählen Sie dann in der Menüleiste die Option **Projekt** und dann **Eigenschaften** aus. Sobald der Projekt-Designer angezeigt wird, klicken Sie auf die Registerkarte **Veröffentlichen** .

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="configuration-and-platform"></a>Konfiguration und Plattform

Die folgenden Eigenschaften ermöglichen es Ihnen, die anzuzeigende bzw. zu ändernde Konfiguration und Plattform auszuwählen.

> [!NOTE]
> Mit vereinfachten Buildkonfigurationen bestimmt das Projektsystem, ob eine Debug- oder eine Releaseversion erstellt werden soll. Deshalb werden die Listen **Konfiguration** und **Plattform** nicht angezeigt.

**Konfiguration**

Gibt an, welche Konfigurationseinstellungen angezeigt oder geändert werden sollen. Die Einstellungen sind **Debuggen** (Standard), **Freigeben** oder **Alle Konfigurationen** . Weitere Informationen finden Sie unter [Grundlagen der Buildkonfiguration](../../ide/understanding-build-configurations.md) und [Gewusst wie: Erstellen und Bearbeiten von Konfigurationen](../../ide/how-to-create-and-edit-configurations.md).

**Plattform**

Gibt an, welche Plattformeinstellungen angezeigt oder geändert werden sollen. Sie können **Beliebige CPU** (Standard), **x64** oder **x86** angeben.

## <a name="compiler-configuration-options"></a>Compilerkonfigurationsoptionen

Mithilfe der folgenden Einstellungen können Sie die Compilerkonfigurationsoptionen festlegen.

**Buildausgabepfad**

Legt den Speicherort der Ausgabedateien für die Konfiguration des Projekts fest. Geben Sie den Pfad der Buildausgabe in dieses Feld ein, oder klicken Sie auf die Schaltfläche **Durchsuchen** , um einen Pfad auszuwählen. Beachten Sie, dass der Pfad relativ ist. Bei der Eingabe eines absoluten Pfads wird dieser als relativer Pfad gespeichert. Der Standardpfad lautet „bin\Debug\ oder bin\Release\\“.

Mit vereinfachten Buildkonfigurationen bestimmt das Projektsystem, ob eine Debug- oder eine Releaseversion erstellt werden soll. Mit dem Befehl **Erstellen** im Menü **Debuggen** (F5) wird der Build unabhängig vom angegebenen **Ausgabepfad** am Debugspeicherort abgelegt. Mit dem Befehl **Erstellen** im Menü **Erstellen** hingegen wird er an dem Speicherort abgelegt, den Sie angeben.

**Option Explicit**

Gibt an, ob implizite Deklaration von Variablen zugelassen werden. Wählen Sie **Ein** , um die explizite Variablendeklaration festzulegen. Dadurch meldet der Compiler Fehler, wenn Variablen nicht deklariert werden, bevor sie verwendet werden. Wählen Sie **Aus** , um implizite Deklaration von Variablen zuzulassen.

Diese Einstellung entspricht der Compileroption [/optionexplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit).

Wenn eine Quellcodedatei eine [Option Explicit-Anweisung](/dotnet/visual-basic/language-reference/statements/option-explicit-statement) enthält, setzt der Wert `On` oder `Off` in der Anweisung die Einstellung **Option Explicit** auf der **Seite „Kompilieren“** außer Kraft.

Wenn Sie ein neues Projekt erstellen, wird die **Option Explicit** -Einstellung in der Seite **Kompilieren** auf den Wert der **Option Explicit** -Einstellung im Dialogfeld **Optionen** festgelegt. Um die Einstellung in diesem Dialogfeld anzuzeigen oder zu ändern, klicken Sie im Menü **Extras** auf **Optionen** . Erweitern Sie im Dialogfeld **Optionen****Projekte und Lösungen** , und klicken Sie dann auf **VB Defaults** . Die ursprüngliche Standardeinstellung **Option Explicit** in **VB Defaults** ist **Ein** .

Das Festlegen der **Option Explicit** auf `Off` ist eine bewährte Methode. Sie könnten den Namen einer Variable an einem oder mehreren Orten falsch buchstabieren, wodurch unerwartete Ergebnisse auftreten würden, wenn das Programm ausgeführt wird.

**Option Strict**

Gibt an, ob die strikte Typsemantik erzwungen werden soll. Wenn die **Option Strict****Ein** ist, führen die folgenden Bedingungen zu einem Kompilierzeitfehler:

- Implizite Eingrenzungskonvertierungen

- Spätes Binden

- Implizites Typisierung der Ergebnisse in einem `Object`-Typ

Implizite Eingrenzungskonvertierungsfehler treten auf, wenn eine implizite Datentypkonvertierung vorhanden ist, die eine Eingrenzungskonvertierung ist. Weitere Informationen finden Sie unter [Option Strict-Anweisung](/dotnet/visual-basic/language-reference/statements/option-strict-statement), [Implizite und explizite Konvertierungen](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions) und [Erweiternde und eingrenzende Konvertierungen](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions).

Ein Objekt wird spät gebunden, wenn es einer Eigenschaft oder Methode einer Variable zugeordnet wird, für die der Typ `Object` deklariert wurde. Weitere Informationen finden Sie unter [Option Strict-Anweisung](/dotnet/visual-basic/language-reference/statements/option-strict-statement) und [Frühes und spätes Binden](/dotnet/visual-basic/programming-guide/language-features/early-late-binding).

Implizite Objekttypfehler treten auf, wenn ein entsprechender Typ nicht für eine deklarierte Variable hergeleitet werden kann, also wir ein Typ von `Object` hergeleitet. Dies tritt vorwiegend auf, wenn Sie eine `Dim`-Anweisung verwenden, um eine Variable ohne die Verwendung einer `As`-Klausel deklarieren und `Option Infer` deaktiviert ist. Weitere Informationen finden Sie unter [Option Strict-Anweisung](/dotnet/visual-basic/language-reference/statements/option-strict-statement), [Option Infer-Anweisung](/dotnet/visual-basic/language-reference/statements/option-infer-statement) und in der [Visual Basic-Sprachspezifikation](/dotnet/visual-basic/reference/language-specification).

Die **Option Strict** -Einstellung entspricht der [/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict)-Compileroption.

Wenn eine Quellcodedatei eine [Option Strict-Anweisung](/dotnet/visual-basic/language-reference/statements/option-strict-statement) enthält, setzt der Wert `On` oder `Off` in der Anweisung die Einstellung **Option Strict** auf der **Seite „Kompilieren“** außer Kraft.

Wenn Sie ein Projekt erstellen, wird die **Option Strict** -Einstellung in der Seite **Kompilieren** auf den Wert der **Option Strict** -Einstellung im Dialogfeld **Optionen** festgelegt. Um die Einstellung in diesem Dialogfeld anzuzeigen oder zu ändern, klicken Sie im Menü **Extras** auf **Optionen** . Erweitern Sie im Dialogfeld **Optionen****Projekte und Lösungen** , und klicken Sie dann auf **VB Defaults** . Die ursprüngliche Standardeinstellung **Option Strict** in **VB Defaults** ist **Ein** .

**Einzelne Option Strict-Warnungen**

Der Abschnitt **Warnungskonfigurationen** auf der Seite **Kompilieren** verfügt über Einstellungen, die mit den drei Bedingungen übereinstimmen, die einen Kompilierzeitfehler auslösen, wenn `Option Strict` aktiviert ist. Die drei Einstellungen sind die folgenden:

- **Implizite Konvertierung**

- **Späte Bindung; Aufruf könnte zur Laufzeit einen Fehler verursachen**

- **Impliziter Typ; Objekt wird angenommen**

Wenn Sie **Option Strict** auf **Ein** festlegen, werden alle drei Warnungskonfigurationseinstellungen auf **Fehler** festgelegt. Wenn Sie **Option Strict** auf **Aus** festlegen werden alle drei Einstellungen auf **Keine** festgelegt.

Sie können individuell jede Warnungskonfigurationseinstellung auf **Keine** , **Warnung** oder **Fehler** festlegen. Wenn alle drei Warnungskonfigurationseinstellungen auf **Fehler** festgelegt sind, erscheint `On` im `Option strict`-Feld. Wenn alle drei Einstellungen auf **Keine** festgelegt sind, erscheint `Off` im Feld. Für jede andere Kombination dieser Einstellungen erscheint **(benutzerdefiniert)** .

**Option Compare**

Gibt den Typ des Zeichenfolgenvergleichs an, der verwendet werden soll. Wählen Sie **Binär** aus, um den Compiler anzuweisen, binäre Zeichenfolgenvergleiche mit Unterscheidung zwischen Groß- und Kleinschreibung zu verwenden. Wählen Sie **Text** aus, um gebietsschemaspezifische Textzeichenfolgenvergleiche ohne Berücksichtigung der Groß- und Kleinschreibung zu verwenden.

Diese Einstellung entspricht der Compileroption [/optioncompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare).

Wenn eine Quellcodedatei eine [Option Compare-Anweisung](/dotnet/visual-basic/language-reference/statements/option-compare-statement) enthält, setzt der Wert `Binary` oder `Text` in der Anweisung die Einstellung **Option Compare** auf der **Seite „Kompilieren“** außer Kraft.

Wenn Sie ein Projekt erstellen, wird die **Option Compare** -Einstellung in der Seite **Kompilieren** auf den Wert der **Option Compare** -Einstellung im Dialogfeld **Optionen** festgelegt. Um die Einstellung in diesem Dialogfeld anzuzeigen oder zu ändern, klicken Sie im Menü **Extras** auf **Optionen** . Erweitern Sie im Dialogfeld **Optionen****Projekte und Lösungen** , und klicken Sie dann auf **VB Defaults** . Die ursprüngliche Standardeinstellung **Option Compare** in **VB Defaults** ist **Binär** .

**Option Infer**

Gibt an, ob die Verwendung von lokalem Typrückschluss in Variablendeklarationen zulässig ist. Wählen Sie **Ein** aus, um die Verwendung des lokalen Typrückschlusses zuzulassen. Wählen Sie **Aus** aus, um den lokalen Typrückschluss zu blockieren.

Diese Einstellung entspricht der Compileroption [/optioninfer](/dotnet/visual-basic/reference/command-line-compiler/optioninfer).

Wenn eine Quellcodedatei eine [Option Infer-Anweisung](/dotnet/visual-basic/language-reference/statements/option-infer-statement) enthält, setzt der Wert `On` oder `Off` in der Anweisung die Einstellung **Option Infer** auf der **Seite „Kompilieren“** außer Kraft.

Wenn Sie ein neues Projekt erstellen, ist die Einstellung **Option Infer** auf der Registerkarte **Kompilieren** auf die Einstellung **Option Infer** im Textfeld **Optionen** festgelegt. Um die Einstellung in diesem Dialogfeld anzuzeigen oder zu ändern, klicken Sie im Menü **Extras** auf **Optionen** . Erweitern Sie im Dialogfeld **Optionen****Projekte und Lösungen** , und klicken Sie dann auf **VB Defaults** . Die ursprüngliche Standardeinstellung **Option Infer** in **VB Defaults** ist **Ein** .

**Ziel-CPU**

Gibt den Prozessor an, für den die Ausgabedatei konfiguriert ist. Geben Sie für jeden Intel-kompatiblen 32-Bit-Prozessor **x86** , für jeden Intel-kompatiblen 64-Bit-Prozessor **x64** und für ARM-Prozessoren **ARM** oder **Any CPU** ein, um anzugeben, dass jeder Prozessor zulässig ist. **Any CPU** (Beliebige CPU) ist der Standardwert für neue Projekte, da die Anwendung hiermit auf der größten Anzahl von Hardwaretypen ausgeführt werden kann.

Weitere Informationen finden Sie unter [/platform (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/platform).

**32-Bit bevorzugen**

Wenn das Kontrollkästchen **32-Bit bevorzugen** ausgewählt wird, wird die Anwendung auf den 32-Bit- und 64-Bit-Versionen von Windows als 32-Bit-Anwendung ausgeführt. Die Anwendung wird andernfalls auf 32-Bit-Versionen von Windows als 32-Bit-Anwendung und auf 64-Bit-Versionen von Windows als 64-Bit-Anwendung ausgeführt.

Die Ausführung als 64-Bit-Anwendung verdoppelt die Zeigergröße und kann zu Kompatibilitätsproblemen mit Bibliotheken führen, die ausschließlich eine 32-Bit-Version sind. Es macht Sinn, eine Anwendung nur als 64-Bit auszuführen, wenn die Anwendung erheblich schneller ist oder mehr als 4 GB Speicherplatz benötigt.

Dieses Kontrollkästchen ist nur verfügbar, wenn die folgenden Bedingungen zutreffen:

- Auf der Seite **Kompilieren** ist die Liste **Ziel-CPU** auf **Beliebige CPU** festgelegt.

- Auf der Seite **Anwendung** wird in der Liste **Anwendungstyp** angegeben, dass das Projekt eine Anwendung ist.

- Auf der Seite **Anwendung** ist in der Liste **Zielframework** „.NET Framework 4.5“ angegeben.

**Warnungskonfigurationen**

In dieser Tabelle sind Buildbedingungen und die jeweils entsprechenden Benachrichtigungsstufen **Keine** , **Warnung** oder **Fehler** aufgeführt.

Während der Kompilierung werden standardmäßig alle Compilerwarnungen der Aufgabenliste hinzugefügt. Wählen Sie **Alle Warnungen deaktivieren** aus, um den Compiler anzuweisen, keine Warnungen oder Fehler auszugeben. Wählen Sie **Alle Warnungen als Fehler behandeln** , wenn Sie möchten, dass der Compiler Warnungen als Fehler behandelt, die behoben werden müssen.

**Alle Warnungen deaktivieren**

Gibt an, ob der Compiler Benachrichtigungen ausgeben darf, sowie in der vorher in diesem Dokument beschriebenen Tabelle **Bedingung und Benachrichtigung** angegeben. Standardmäßig ist dieses Kontrollkästchen deaktiviert. Aktivieren Sie dieses Kontrollkästchen, um den Compiler anzuweisen, keine Warnungen oder Fehler auszugeben.

Diese Einstellung entspricht der Compileroption [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn).

**Alle Warnungen als Fehler behandeln.**

Gibt an, wie Warnungen behandelt werden müssen. In der Standardeinstellung ist dieses Kontrollkästchen deaktiviert, damit alle Warnungsbenachrichtigungen auf **Warnung** festgelegt bleiben. Aktivieren Sie dieses Kontrollkästchen, um alle Warnungsbenachrichtigungen in **Fehler** zu ändern.

Diese Option ist nur verfügbar, wenn **Alle Warnungen deaktivieren** deaktiviert ist.

**XML-Dokumentationsdatei generieren**

Gibt an, ob Dokumentationsiformationen generiert werden sollen. Standardmäßig ist dieses Kontrollkästchen ausgewählt und weist den Compiler an, Dokumentationsinformationen zu generieren und diese in einer XML-Datei einzuschließen. Deaktivieren Sie dieses Kontrollkästchen, um den Compiler anzuweisen, keine Dokumentation zu erstellen.

Diese Einstellung entspricht der Compileroption [/doc](/dotnet/visual-basic/reference/command-line-compiler/doc).

**Für COM-Interop registrieren**

Gibt an, ob Ihre verwaltete Anwendung ein COM-Objekt (einen COM Callable Wrapper) verfügbar macht, der einem COM-Objekt die Interaktion mit der verwalteten Anwendung ermöglicht.

Dieses Kontrollkästchen ist standardmäßig deaktiviert, was angibt, dass die Anwendung COM-Interop nicht zulässt. Aktivieren Sie dieses Kontrollkästchen, um COM-Interop zuzulassen.

Diese Option ist nicht für Windows-Anwendungs- und Konsolenanwendungsprojekte verfügbar.

**Buildereignisse**

Klicken Sie auf diese Schaltfläche, um auf das Dialogfeld **Buildereignisse** zuzugreifen. Verwenden Sie dieses Dialogfeld, um die Präbuild- und Postbuild-Konfigurationsanweisungen für das Projekt anzugeben. Dieses Dialogfeld gilt nur für Visual Basic-Projekte. Weitere Informationen finden Sie unter [Dialogfeld „Buildereignisse“ (Visual Basic)](../../ide/reference/build-events-dialog-box-visual-basic.md).

**Erweiterte Kompilierungsoptionen**

Klicken Sie auf diese Schaltfläche, um auf das Dialogfeld **Erweiterte Compileroptionen** zuzugreifen. Verwenden Sie das Dialogfeld **Erweiterte Compilereinstellungen** , um die erweiterten Buildkonfigurationseigenschaften des Projekts anzugeben. Dieses Dialogfeld gilt nur für Visual Basic-Projekte. Weitere Informationen finden Sie im [Dialogfeld „Erweiterte Compilereinstellungen“ (Visual Basic)](../../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md).

## <a name="see-also"></a>Siehe auch

- [Gewusst wie: Festlegen von Buildereignissen (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)
- [Visual Basic-Befehlszeilencompiler](/dotnet/visual-basic/reference/command-line-compiler/index)
- [How to: Erstellen und Bearbeiten von Konfigurationen](../../ide/how-to-create-and-edit-configurations.md)
