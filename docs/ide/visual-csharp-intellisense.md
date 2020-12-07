---
title: C#-IntelliSense
description: Hier erhalten Sie Informationen zu IntelliSense-Features, die Sie beim Programmieren Ihres C#-Projekts verwenden können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- C#, IntelliSense
- IntelliSense [C#]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: e725a06a2bc90c91cff11b05ad32b20a0db8e4fc
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2020
ms.locfileid: "96479783"
---
# <a name="c-intellisense"></a>C#-IntelliSense

C#-IntelliSense ist beim Codieren im Editor und beim Debuggen im Befehlsfenster [Unmittelbarer Modus](../ide/reference/immediate-window.md) verfügbar.

## <a name="completion-lists"></a>Vervollständigungslisten

Die IntelliSense-Vervollständigungslisten in C# enthalten u.a. Token von „Member auflisten“ und „Wort vervollständigen“. Die Listen ermöglichen schnellen Zugriff auf:

- Member eines Typs oder Namespaces

- Variablen-, Befehls- und Funktionsnamen

- Codeausschnitte

- Sprachschlüsselwörter

- Erweiterungsmethoden

Die Vervollständigungsliste in C# ist darüber hinaus intelligent genug, irrelevante Token herauszufiltern und auf der Grundlage des Kontexts eine Vorauswahl unter den Token zu treffen. Weitere Informationen finden Sie unter [Gefilterte Vervollständigungslisten](#filtered-completion-lists).

### <a name="code-snippets-in-completion-lists"></a>Codeausschnitte in Vervollständigungslisten

In C# enthält die Vervollständigungsliste Codeausschnitte, um Ihnen das einfache Einfügen vordefinierter Codetexte in das Programm zu ermöglichen. Codeausschnitte werden in der Vervollständigungsliste als [Verknüpfungstext](../ide/code-snippets-schema-reference.md#shortcut-element) des Ausschnitts angezeigt. Weitere Informationen über standardmäßig in C# verfügbare Codeausschnitte finden Sie unter [C#-Codeausschnitte](../ide/visual-csharp-code-snippets.md).

### <a name="language-keywords-in-completion-lists"></a>Sprachschlüsselwörter in Vervollständigungslisten

In C# umfasst die Vervollständigungsliste zusätzlich Programmiersprachen-Schlüsselwörter. Weitere Informationen über Sprachschlüsselwörter in C# finden Sie unter [C#-Schlüsselwörter](/dotnet/csharp/language-reference/keywords/index).

### <a name="extension-methods-in-completion-lists"></a>Erweiterungsmethoden in Vervollständigungslisten

In C# enthält die Vervollständigungsliste Erweiterungsmethoden innerhalb des jeweiligen Gültigkeitsbereichs.

> [!NOTE]
> Von der Vervollständigungsliste werden nicht alle Erweiterungsmethoden für <xref:System.String>-Objekte angezeigt.

Für Erweiterungsmethoden wird ein anderes Symbol als für Instanzenmethoden verwendet. Einen Leitfaden zur Symbolreferenz finden Sie unter [Symbole in der Klassenansicht und im Objektkatalog](../ide/class-view-and-object-browser-icons.md). Wenn sich eine Instanzenmethode und eine Erweiterungsmethode mit identischem Namen im selben Bereich befinden, zeigt die Vervollständigungsliste das Symbol für die Erweiterungsmethode an.

### <a name="filtered-completion-lists"></a>Gefilterte Vervollständigungslisten

Unnötige Member werden von IntelliSense mithilfe von Filtern aus der Vervollständigungsliste entfernt. In C# werden die Vervollständigungslisten für folgende Elemente gefiltert:

- **Schnittstellen und Basisklassen**: IntelliSense entfernt automatisch Elemente aus den Vervollständigungslisten für Schnittstellen und Basisklassen, und zwar sowohl aus Basisklassen- und Schnittstellenlisten für die Klassendeklaration als auch aus Einschränkungslisten. So werden Enumerationen in der Vervollständigungsliste für Basisklassen beispielsweise nicht angezeigt, da Enumerationen für Basisklassen nicht verwendet werden können. Die Vervollständigungsliste für Basisklassen enthält nur Schnittstellen und Namespaces.  Wenn Sie in der Liste ein Element auswählen und anschließend ein Komma eingeben, entfernt IntelliSense Basisklassen aus der Vervollständigungsliste, da C# eine Mehrfachvererbung nicht unterstützt. Das gleiche Verhalten gilt auch für Einschränkungsklauseln.

- **Attribute:** Beim Anwenden eines Attributs auf einen Typ wird die Vervollständigungsliste gefiltert, sodass sie nur die Typen enthält, die von den Namespaces abgeleitet werden, in denen diese Typen enthalten sind, z.B. <xref:System.Attribute>.

- **Catch-Klauseln**

- **Objektinitialisierer:** Nur Members, die initialisiert werden können, werden in der Vervollständigungsliste angezeigt.

- **Neues Schlüsselwort:** Wenn Sie `new` eingeben und dann die **Leertaste** drücken, wird eine Vervollständigungsliste angezeigt. Auf der Grundlage des Kontexts im Code wird in der Liste automatisch ein Element ausgewählt. Beispielsweise werden in den Vervollständigungslisten automatisch Elemente für Deklarationen und return-Anweisungen in Methoden ausgewählt.

- **enum-Schlüsselwort**: Wenn Sie nach einem Gleichheitszeichen für eine enum-Zuweisung die **Leertaste** drücken, wird eine Vervollständigungsliste angezeigt. Auf der Grundlage des Kontexts im Code wird in der Liste automatisch ein Element ausgewählt. Beispielsweise werden automatisch Elemente in der Vervollständigungsliste ausgewählt, nachdem Sie das return-Schlüsselwort eingegeben oder eine Deklaration erstellt haben.

- **as- und is-Operatoren:** Eine gefilterte Vervollständigungsliste wird automatisch eingeblendet, wenn Sie nach Eingabe des Schlüsselworts `as` oder `is` die **Leertaste** drücken.

- **Ereignisse:** Wenn Sie das Schlüsselwort `event` eingeben, sind in der Vervollständigungsliste nur Delegattypen enthalten.

- Mit **Parametern** kann automatisch nach der ersten Methodenüberladung gefiltert werden, die den Parametern während der Eingabe entspricht. Falls mehrere Methodenüberladungen verfügbar sind, können Sie die NACH-OBEN- bzw. NACH-UNTEN-TASTE verwenden, um in der Liste zur nächsten möglichen Überladung zu navigieren.

### <a name="most-recently-used-members"></a>Zuletzt verwendete Member

IntelliSense speichert, welche Member Sie in der Popupliste [Member auflisten](../ide/using-intellisense.md) zuletzt ausgewählt haben, um die automatische Vervollständigung von Objektnamen zu ermöglichen. Bei der nächsten Verwendung der **Memberliste** werden die zuletzt verwendeten Member oben angezeigt. Der Verlauf der zuletzt verwendeten Member wird nach jeder Sitzung in Visual Studio gelöscht.

### <a name="override"></a>override

Beim Eingeben von [override](/dotnet/csharp/language-reference/keywords/override) und Drücken der **Leertaste** zeigt IntelliSense alle zulässigen Basisklassenmember an, die Sie in einem Popuplistenfeld überschreiben können. Durch die Eingabe des Rückgabetyps der Methode nach `override` wird IntelliSense angewiesen, nur Methoden anzuzeigen, die denselben Typ zurückgeben. Wenn IntelliSense keine Übereinstimmung findet, werden alle Basisklassenmember angezeigt.

### <a name="ai-enhanced-intellisense"></a>IntelliSense mit KI-Erweiterung

[Visual Studio IntelliCode](/visualstudio/intellicode/intellicode-visual-studio) bietet KI-basierte IntelliSense-Vervollständigungslisten. IntelliCode trifft eine Vorhersage hinsichtlich der höchstwahrscheinlich korrekten zu verwendenden API statt einfach nur eine alphabetische Memberliste anzuzeigen. Sie verwendet Ihren aktuellen Codekontext und die aktuellen Muster, um die dynamische Liste bereitzustellen.

## <a name="automatic-code-generation"></a>Automatische Codegenerierung

### <a name="add-using"></a>Hinzufügen mit

Der IntelliSense-Vorgang **Hinzufügen mit** fügt automatisch die erforderliche `using`-Anweisung zu Ihrer Codedatei hinzu. Durch diese Funktion können Sie den Schwerpunkt auf den zu schreibenden Code statt auf einen anderen Teil des Codes legen.

Um den Vorgang **Hinzufügen mit** zu initiieren, positionieren Sie den Cursor auf einem Typverweis, der nicht aufgelöst werden kann. Wenn Sie beispielsweise eine Konsolenanwendung erstellen und anschließend `XmlReader` zum Text der `Main`-Methode hinzufügen, wird eine rote Wellenlinie in dieser Codezeile angezeigt, da der Typverweis nicht aufgelöst werden kann. Sie können dann **Hinzufügen mit** über die **Schnellaktionen** aufrufen. Die Option **Schnellaktionen** ist nur sichtbar, wenn sich der Cursor auf dem ungebundenen Typ befindet.

![Darstellung vom Hinzufügen der using-Anweisung über eine schnelle Aktion](../ide/media/addusing-quickaction.png)

Klicken Sie auf das Fehlerglühbirnensymbol und dann auf **using System.Xml;**, um die using-Anweisung automatisch hinzuzufügen.

### <a name="remove-and-sort-usings"></a>Using-Direktiven entfernen und sortieren

Mit der Option **Using-Direktiven entfernen und sortieren** können Sie `using`- und `extern`-Deklarationen sortieren und entfernen, ohne das Verhalten des Quellcodes zu ändern. Im Laufe der Zeit können Quelldateien aufgrund von nicht benötigten und unorganisierten `using`-Direktiven sehr groß werden und schwer zu lesen sein. Die Option **Using-Direktiven entfernen und sortieren** komprimiert Quellcode, in dem sie nicht verwendete `using`-Direktiven entfernt, und verbessert die Lesbarkeit durch Sortierung. Klicken Sie im Menü **Bearbeiten** auf die Option **IntelliSense** und dann auf **Ausschnitt einfügen**.

### <a name="implement-interface"></a>Implementieren einer Schnittstelle

IntelliSense bietet die Möglichkeit, eine [Schnittstelle](/dotnet/csharp/language-reference/keywords/interface) bei der Arbeit im Code-Editor zu implementieren. Um eine Schnittstelle ordnungsgemäß zu implementieren, müssen Sie normalerweise eine Methodendeklaration für jeden Schnittstellenmember in der Klasse erstellen. Nachdem Sie den Namen einer Schnittstelle unter Verwendung von IntelliSense in einer Klassendeklaration eingegeben haben, wird eine Glühbirne für **Schnellaktionen** angezeigt. Mithilfe der Glühbirne können Sie die Schnittstelle mit expliziten oder impliziten Namen automatisch implementieren. Bei expliziter Benennung tragen die Methodendeklarationen den Namen der Schnittstelle. Bei impliziter Benennung fehlt bei den Methodendeklarationen ein Hinweis auf die zugehörige Schnittstelle. Auf eine explizit benannte Schnittstellenmethode kann nur über eine Schnittstelleninstanz zugegriffen werden, und nicht über eine Klasseninstanz. Weitere Informationen finden Sie unter [Explizite Schnittstellenimplementierung](/dotnet/csharp/programming-guide/interfaces/explicit-interface-implementation).

Bei der Schnittstellenimplementierung wird die Mindestanzahl von Methodenstubs generiert, die für die Schnittstelle benötigt werden. Wenn eine Basisklasse Teile der Schnittstelle implementiert, werden diese Stubs nicht neu generiert.

### <a name="implement-abstract-base-class"></a>Implementieren abstrakter Basisklassen

IntelliSense bietet eine Option zum automatischen Implementieren von Membern einer abstrakten Basisklasse während der Arbeit im Code-Editor. Normalerweise erfordert das Implementieren von Membern einer abstrakten Basisklasse das Erstellen einer neuen Methodendefinition für jede Methode der abstrakten Basisklasse in der abgeleiteten Klasse. Nachdem Sie den Namen einer abstrakten Basisklasse mithilfe von IntelliSense in einer Klassendeklaration eingegeben haben, wird eine Glühbirne für **Schnellaktionen** angezeigt. Durch die Glühbirne können Sie Basisklassenmethoden automatisch implementieren.

Die durch das Feature **Abstrakte Basisklasse implementieren** generierten MethodStubs werden durch den in der Datei *MethodStub.snippet* definierten Codeausschnitt modelliert. Codeausschnitte können geändert werden. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines Codeausschnitts](../ide/walkthrough-creating-a-code-snippet.md).

### <a name="generate-from-usage"></a>Aus Verwendung generieren

Mit der Funktion **Aus Verwendung generieren** können Sie Klassen und Member verwenden, bevor Sie sie definieren. Sie können ein Stub für alle Klassen, Konstruktoren, Methoden, Eigenschaften, Felder oder Enumerationen generieren, die Sie verwenden möchten, aber noch nicht definiert haben. Sie können neue Typen und Member generieren, ohne Ihre aktuelle Position im Code zu verlassen. Dies verringert die Unterbrechung des Workflows.

Unter jedem nicht definierten Bezeichner wird eine rote, wellenförmige Unterstreichung angezeigt. Wenn Sie den Mauszeiger auf den Bezeichner bewegen, wird eine Fehlermeldung als QuickInfo angezeigt. Sie können eines der folgenden Verfahren verwenden, um die entsprechenden Optionen anzuzeigen:

- Klicken Sie auf den nicht definierten Bezeichner. Unter dem Bezeichner wird ein Fehlerglühbirnensymbol für **Schnellaktionen** angezeigt. Klicken Sie auf das Fehlerglühbirnensymbol.

- Klicken Sie auf den nicht definierten Bezeichner, und drücken Sie **STRG**+ **.** (**STRG**+Punkt).

- Klicken Sie mit der rechten Maustaste auf den nicht definierten Bezeichner, und klicken Sie auf **Schnellaktionen und Refactorings**.

Die angezeigten Optionen können Folgendes umfassen:

- **Eigenschaft generieren**

- **Feld generieren**

- **Generieren einer Methode**

- **Klasse generieren**

- **Neuen Typ generieren** (für Klasse, Struktur, Schnittstelle oder Enumeration)

## <a name="generate-event-handlers"></a>Ereignishandler generieren

Im Code-Editor kann IntelliSense Sie beim Verknüpfen von Methoden (Ereignishandlern) mit Ereignisfeldern unterstützen.

Wenn Sie den `+=`-Operator nach einem Ereignisfeld in einer *CS*-Datei eingeben, fordert IntelliSense Sie dazu auf, die **Tab**-Taste zu drücken. Hierbei wird eine neue Instanz eines Delegaten eingefügt, der auf die Methode zum Behandeln des Ereignisses zeigt.

![Button automatisch verknüpfen](../ide/media/vxautohookup.gif)

Wenn Sie die **Tab**-Taste drücken, schließt IntelliSense die Anweisung automatisch für Sie ab und zeigt den Ereignishandlerverweis als ausgewählten Text im Code-Editor an. Um die automatische Ereigniseinbindung abzuschließen, fordert IntelliSense Sie erneut zum Drücken der **TAB-TASTE** auf, um einen leeren Stub für den Ereignishandler zu erstellen.

![Ereignishandler generieren](../ide/media/vxgenerateeventhandler.gif)

> [!NOTE]
> Wenn ein neuer Delegat, der von IntelliSense erstellt wird, auf einen vorhandenen Ereignishandler verweist, vermittelt IntelliSense diese Informationen über die QuickInfo. Sie können diesen Verweis dann ändern. Der Text ist im Code-Editor bereits ausgewählt. Andernfalls ist die automatische Ereigniseinbindung an diesem Punkt abgeschlossen.

Wenn Sie die **TAB-TASTE** drücken, versieht IntelliSense eine Methode per Stub mit der richtigen Signatur und fügt den Cursor in den Text Ihres Ereignishandlers ein.

> [!NOTE]
> Verwenden Sie im Menü **Ansicht** (**STRG**+**-**) den Befehl **Rückwärts navigieren**, um zurück zur Anweisung für die Ereigniseinbindung zu wechseln.

## <a name="see-also"></a>Siehe auch

- [Verwendung von IntelliSense](../ide/using-intellisense.md)
- [Visual Studio-IDE](../get-started/visual-studio-ide.md)
