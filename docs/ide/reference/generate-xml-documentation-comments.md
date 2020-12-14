---
title: Einfügen von XML-Dokumentationskommentaren
description: Hier erfahren Sie, wie Sie XML-Dokumentationskommentare in den Code einfügen, mit dem Sie eine compilergenerierte XML-Datei erstellen können, die zusammen mit der .NET-Assembly verteilt wird.
ms.custom: SEO-VS-2020
ms.date: 01/22/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 250e07994b04e03b015bf3893633ebce0f36a90d
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2020
ms.locfileid: "96617473"
---
# <a name="how-to-insert-xml-comments-for-documentation-generation"></a>Vorgehensweise: Einfügen von XML-Kommentaren für die Generierung der Dokumentation

Visual Studio unterstützt Sie dabei, Codeelemente wie z.B. Klassen und Methoden zu dokumentieren, indem es automatisch die Standardstruktur für XML-Dokumentationskommentare generiert. Sie können eine XML-Datei zur Kompilierzeit erstellen, die die Dokumentationskommentare enthält.

> [!TIP]
> Informationen zum Konfigurieren des Namens und des Speicherorts der erzeugten XML-Datei finden Sie unter [Dokumentieren von Code mit XML-Kommentaren (C# Guide)](/dotnet/csharp/codedoc).

Die vom Compiler generierte XML-Datei kann zusammen mit Ihrer .NET-Assembly verteilt werden, damit Visual Studio und andere IDEs mit IntelliSense QuickInfos über Typen und Member anzeigen können. Darüber hinaus kann die XML-Datei mithilfe von Tools wie [DocFX](https://dotnet.github.io/docfx/) und [Sandcastle](https://www.microsoft.com/download/details.aspx?id=10526) ausgeführt werden, um API-Verweiswebsites zu generieren.

> [!NOTE]
> Der Befehl **Kommentar einfügen**, der automatisch XML-Dokumentationskommentare einfügt, ist in [C#](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments) und [Visual Basic](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation) verfügbar. Dennoch können Sie [XML-Dokumentationskommentare in C++-Dateien](/cpp/build/reference/xml-documentation-visual-cpp) manuell einfügen, und weiterhin XML-Dokumentationskommentare zur Kompilierzeit generieren.

## <a name="to-insert-xml-comments-for-a-code-element"></a>Einfügen von XML-Kommentaren für ein Codeelement

1. Platzieren Sie den Textcursor oberhalb des zu dokumentierenden Elements, z.B. einer Methode.

2. Führen Sie eines der folgenden Verfahren aus:

   - Geben Sie `///` in C# oder `'''` in Visual Basic ein

   - Wählen Sie im Menü **Bearbeiten** **IntelliSense** > **Kommentar einfügen** aus.

   - Führen Sie einen Rechtsklick aus, bzw. nutzen Sie das Kontextmenü, und klicken dann auf **Ausschnitt** > **Kommentar einfügen**.

   Die XML-Vorlage wird sofort über dem Codeelement generiert. Wenn Sie zum Beispiel eine Methode kommentieren, wird ein **\<summary\>** -Element, ein **\<param\>** -Element für jeden Parameter und ein **\<returns\>** -Element generiert, um den Rückgabewert zu dokumentieren.

   ![XML-Kommentarvorlage – C#](media/doc-preview-cs.png)

   ![XML-Kommentarvorlage – Visual Basic](media/doc-preview-vb.png)

3. Geben Sie Beschreibungen für jedes XML-Element an, um das Codeelement vollständig zu dokumentieren.

   ![Screenshot: Abgeschlossener Kommentar](media/doc-result-cs.png)

Sie können in XML-Kommentaren Stile verwenden, die beim Zeigen auf das Element in der QuickInfo gerendert werden. Zu diesen Stilen zählen z. B. die Kursiv- oder Fettformatierung, Aufzählungslisten und klickbare Links.

   ![Screenshot: Abgeschlossener Kommentar mit Stiltags für „Kursiv“, „Fett“, Aufzählungszeichen und einen klickbaren Link](media/doc-style-cs.png) 

> [!NOTE]
> Es gibt eine [Option](../../ide/reference/options-text-editor-csharp-advanced.md) zum Ein- und Ausblenden von XML-Dokumentationskommentaren nach der Eingabe von `///` in C# oder `'''` in Visual Basic. Wählen Sie in der Menüleiste **Extras** > **Optionen** aus, um das Dialogfeld **Optionen** zu öffnen. Navigieren Sie dann zu **Text-Editor** > **C#** oder **Basic** > **Advanced** (Basic > Erweitert). Suchen Sie im Abschnitt **Editor-Hilfe** nach der Option **XML-Dokumentationskommentare generieren**.

## <a name="see-also"></a>Weitere Informationen

- [XML-Dokumentationskommentare (C#-Programmierhandbuch)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
- [Documenting your code with XML comments (C# Guide) (Dokumentieren von Code mit XML-Kommentaren (C#-Handbuch))](/dotnet/csharp/codedoc)
- [How to: Create XML documentation (Visual Basic) (Vorgehensweise: Erstellen von XML-Dokumentation (Visual Basic))](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation)
- [C++-Kommentare](/cpp/cpp/comments-cpp)
- [XML-Dokumentation (C++)](/cpp/build/reference/xml-documentation-visual-cpp)
- [Codegenerierung](../code-generation-in-visual-studio.md)
