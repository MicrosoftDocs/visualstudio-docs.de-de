---
title: Erfahren Sie, wie Sie Ihren Code mit Live Unit Testing testen
description: Hier erfahren Sie, wie Sie Live Unit Testing verwenden, indem Sie eine einfache Klassenbibliothek für .NET Standard erstellen. Des Weiteren erstellen Sie zu Testzwecken ein MSTest-Projekt für .NET Core.
ms.custom: SEO-VS-2020
ms.date: 04/03/2020
ms.topic: how-to
helpviewer_keywords:
- Live Unit Testing
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: ea87135b1f60c7ae65a8bc25399604151ab2fcee
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887808"
---
# <a name="get-started-with-live-unit-testing"></a>Erste Schritte mit Live Unit Testing

Wenn Sie Live Unit Testing in einer Visual Studio-Projektmappe aktivieren, werden Ihre Testabdeckung und der Status Ihrer Tests dargestellt. Live Unit Testing führt außerdem dynamisch Tests durch, wenn Sie den Code ändern, und Sie werden sofort benachrichtigt, wenn Ihre Änderungen dazu führen, dass Tests nicht erfolgreich sind.

Live Unit Testing kann zum Testen von Projektmappen für .NET Framework oder .NET Core verwendet werden. In diesem Tutorial erlernen Sie die Verwendung von Live Unit Testing, indem Sie eine einfache Klassenbibliothek für .NET Standard erstellen. Des Weiteren erstellen Sie zu Testzwecken ein MSTest-Projekt für .NET Core.

Die vollständige C#-Projektmappe kann aus dem Repository [MicrosoftDocs/visualstudio-docs](https://github.com/MicrosoftDocs/visualstudio-docs/tree/master/docs/test/samples/csharp/UtilityLibraries/) auf GitHub heruntergeladen werden.

## <a name="prerequisites"></a>Voraussetzungen

Für dieses Tutorial ist die Installation der Visual Studio Enterprise-Edition mit der Workload für **plattformübergreifende .NET Core-Entwicklung** erforderlich.

## <a name="create-the-solution-and-the-class-library-project"></a>Projektmappe und Klassenbibliotheksprojekt erstellen

Erstellen Sie zunächst eine Visual Studio-Projektmappe mit dem Namen UtilityLibraries, die das einfache .NET-Standard-Klassenbibliotheksprojekt StringLibrary enthält.

Die Projektmappe ist nur ein Container für mindestens ein Projekt. Zum Erstellen einer leeren Projektmappe öffnen Sie Visual Studio und führen die folgenden Schritte aus:

1. Klicken Sie in der Menüleiste von Visual Studio auf **Datei** > **Neu** > **Projekt**.

1. Geben Sie **Projektmappe** in das Vorlagensuchfeld ein, und wählen Sie dann die Vorlage **Leere Projektmappe** aus. Geben Sie dem Projekt den Namen **UtilityLibraries**.

   ::: moniker range="vs-2017"

   ![Das Dialogfeld **Neues Projekt**](./media/lut-start/new-solution.png)

   ::: moniker-end

1. Schließen Sie das Erstellen der Projektmappe ab.

Nach der Erstellung der Projektmappe erstellen Sie eine Klassenbibliothek mit dem Namen StringLibrary, die einige Erweiterungsmethoden für das Arbeiten mit Zeichenfolgen enthält.

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf die Projektmappe UtilityLibraries, und wählen Sie **Hinzufügen** > **Neues Projekt** aus.

::: moniker range="vs-2017"

2. Klicken Sie im Dialogfeld **Neues Projekt hinzufügen** auf den C#-Knoten, und wählen Sie anschließend **.NET Standard** aus.

   > [!NOTE]
   > Da das Ziel unserer Bibliothek die .NET Standard-Implementierung und keine bestimmte .NET-Implementierung ist, kann sie über eine beliebige .NET-Implementierung aufgerufen werden, die diese .NET Standard-Version unterstützt. Weitere Informationen finden Sie unter [.NET Standard](/dotnet/standard/net-standard).

3. Wählen Sie im rechten Bereich die Vorlage **Klassenbibliothek (.NET Standard)** aus, und geben Sie **StringLibrary** wie in der folgenden Abbildung gezeigt in das Textfeld **Name** ein:

   ![Dialogfeld **Neues Projekt hinzufügen**](./media/lut-start/add-project-cs.png)

4. Klicken Sie auf **OK**, um das Projekt zu erstellen.

::: moniker-end

::: moniker range=">=vs-2019"

2. Geben Sie **Klassenbibliothek** in das Vorlagensuchfeld ein, und wählen Sie die Vorlage **Klassenbibliothek (.NET Standard)** aus. Klicken Sie auf **Weiter**.

   > [!NOTE]
   > Da das Ziel unserer Bibliothek die .NET Standard-Implementierung und keine bestimmte .NET-Implementierung ist, kann sie über eine beliebige .NET-Implementierung aufgerufen werden, die diese .NET Standard-Version unterstützt. Weitere Informationen finden Sie unter [.NET Standard](/dotnet/standard/net-standard).

3. Nennen Sie das Projekt **StringLibrary** .

4. Klicken Sie auf **Erstellen**, um das Projekt zu erstellen.

::: moniker-end

5. Ersetzen Sie sämtlichen vorhandenen Code im Code-Editor durch den folgenden Code:

   [!code-csharp[StringLibrary source code](samples/csharp/utilitylibraries/stringlibrary/class1.cs)]

   StringLibrary verfügt über drei statische Methoden:

   - `StartsWithUpper` gibt `true` zurück, wenn eine Zeichenfolge mit einem Großbuchstaben beginnt; andernfalls wird `false` zurückgegeben.

   - `StartsWithLower` gibt `true` zurück, wenn eine Zeichenfolge mit einem Kleinbuchstaben beginnt; andernfalls wird `false` zurückgegeben.

   - `HasEmbeddedSpaces` gibt `true` zurück, wenn eine Zeichenfolge mit einem Leerzeichen beginnt; andernfalls wird `false` zurückgegeben.

6. Klicken Sie im Hauptebenenmenü von Visual Studio auf **Erstellen** > **Projektmappe**. Das Erstellen sollte nun erfolgreich abgeschlossen werden.

## <a name="create-the-test-project"></a>Erstellen des Testprojekts

Im nächsten Schritt wird das Komponententestprojekt zum Testen der StringLibrary-Bibliothek erstellt. Führen Sie die folgenden Schritte aus, um die Komponententests zu erstellen:

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf die Projektmappe UtilityLibraries, und wählen Sie **Hinzufügen** > **Neues Projekt** aus.

::: moniker range="vs-2017"

2. Klicken Sie im Dialogfeld **Neues Projekt hinzufügen** auf den C#-Knoten, und wählen Sie anschließend **.NET Core** aus.

   > [!NOTE]
   > Sie müssen die Komponententests nicht in derselben Sprache wie die Klassenbibliothek schreiben.

3. Wählen Sie im rechten Bereich die Vorlage **Komponententestprojekt (.NET Core)** aus, und geben Sie **StringLibraryTests** wie in der folgenden Abbildung gezeigt in das Textfeld **Name** ein:

   ![Das Dialogfeld **Neues Projekt hinzufügen** für das Komponententestprojekt](./media/lut-start/add-unit-test-cs.png)

4. Klicken Sie auf **OK**, um das Projekt zu erstellen.

::: moniker-end

::: moniker range=">=vs-2019"

2. Geben Sie **Komponententest** in das Vorlagensuchfeld ein, und wählen Sie dann die Vorlage **MSTest-Testprojekt (.NET Core)** aus. Klicken Sie auf **Weiter**.

3. Nennen Sie das Projekt **StringLibraryTests**.

4. Klicken Sie auf **Erstellen**, um das Projekt zu erstellen.

::: moniker-end

   > [!NOTE]
   > In dieser Einführung wird das Live Unit Testing mit dem MSTest-Testframework verwendet. Sie können auch die xUnit- und NUnit-Testframeworks verwenden.

5. Das Komponententestprojekt kann nicht automatisch auf die Klassenbibliothek zugreifen, die getestet wird. Sie erteilen der Testbibliothek Zugriff, indem Sie eine Referenz auf das Klassenbibliotheksprojekt hinzufügen. Klicken Sie hierzu erst mit der rechten Maustaste auf das Projekt `StringLibraryTests` und anschließend mit der Linken auf **Hinzufügen** > **Verweis**. Stellen Sie sicher, dass im Dialogfeld **Verweis-Manager** die Registerkarte **Projektmappe** ausgewählt ist, und wählen Sie wie in der folgenden Abbildung gezeigt das Projekt „StringLibrary“ aus.

   ![Das Dialogfeld **Verweis-Manager**](./media/lut-start/add-reference.png)

6. Ersetzen Sie den in der Vorlage angegebenen Codebaustein für den Komponententest durch den folgenden Code:

   [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest1.cs)]

7. Speichern Sie Ihr Projekt, indem Sie auf das Symbol **Speichern** in der Symbolleiste klicken.

   Da der Komponententestcode einige ASCII-fremde Zeichen enthält, wird das folgende Dialogfeld mit der Warnung angezeigt, dass einige Zeichen verloren gehen, wenn die Datei im ASCII-Standardformat gespeichert wird.

8. Klicken Sie auf die Schaltfläche **Mit anderer Codierung speichern**.

   ![Wählen Sie eine Dateicodierung aus](media/lut-start/ascii-encoding.png)

9. Wählen Sie wie in der folgenden Abbildung gezeigt in der Dropdownliste **Codierung** des Dialogfelds **Erweiterte Speicheroptionen** die Option **Unicode (UTF-8 ohne Signatur) – Codepage 65001** aus:

   ![Auswählen der UTF-8-Codierung](media/lut-start/utf8-encoding.png)

10. Kompilieren Sie das Komponententestprojekt, indem Sie im Hauptebenenmenü von Visual Studio auf **Erstellen** > **Projektmappe neu erstellen** klicken.

Sie haben eine Klassenbibliothek und einige Komponententests dafür erstellt. Sie haben nun die Vorbereitungen abgeschlossen, die für die Verwendung von Live Unit Testing erforderlich sind.

## <a name="enable-live-unit-testing"></a>Aktivieren von Live Unit Testing

Bisher haben Sie die Tests für die StringLibrary-Klassenbibliothek zwar geschrieben, jedoch nicht ausgeführt. Live Unit Testing macht dies automatisch, nachdem es aktiviert wurde. Führen Sie hierzu die folgenden Schritte aus:

1. Wählen Sie optional das Code-Editor-Fenster aus, das den Code für StringLibrary enthält. Dies ist entweder *Class1.cs* für ein C#-Projekt oder *Class1.vb* für ein Visual Basic-Projekt. (In diesem Schritt können Sie nach der Aktivierung von Live Unit Testing das Ergebnis Ihrer Tests und die Reichweite Ihrer Code Coverage prüfen.)

1. Klicken Sie im Hauptebenenmenü von Visual Studio auf **Test** > **Live Unit Testing** > **Starten**.

1. Visual Studio startet Live Unit Testing, das automatisch alle Ihre Tests ausführt.

::: moniker range="vs-2017"
Nach Abschluss der Testausführung zeigt der **Test-Explorer** die Gesamtergebnisse und das Ergebnis der einzelnen Tests an. Darüber hinaus werden sowohl die Code Coverage als auch die Ergebnisse Ihrer Tests im Code-Editor-Fenster angezeigt. Alle drei Tests wurden wie in der folgenden Abbildung gezeigt erfolgreich ausgeführt. Zudem ist zu sehen, dass die Tests alle Codepfade in der Methode `StartsWithUpper` abgedeckt haben, und dass diese Tests alle erfolgreich ausgeführt wurden (durch das grüne Häkchen „✓“ gekennzeichnet). Schließlich ist zu sehen, dass keine der anderen Methoden in StringLibrary über eine Code Coverage verfügt (dies wird durch eine blaue Linie „➖“ gekennzeichnet).

![Test-Explorer- und Code-Editor-Fenster nach Start von Live Unit Testing](media/lut-start/lut-results-cs.png)
::: moniker-end
::: moniker range=">=vs-2019"
Nach Abschluss der Testausführung zeigt **Live Unit Testing** die Gesamtergebnisse und die Ergebnisse der einzelnen Tests an. Darüber hinaus werden sowohl die Code Coverage als auch die Ergebnisse Ihrer Tests im Code-Editor-Fenster angezeigt. Alle drei Tests wurden wie in der folgenden Abbildung gezeigt erfolgreich ausgeführt. Zudem ist zu sehen, dass die Tests alle Codepfade in der Methode `StartsWithUpper` abgedeckt haben, und dass diese Tests alle erfolgreich ausgeführt wurden (durch das grüne Häkchen „✓“ gekennzeichnet). Schließlich ist zu sehen, dass keine der anderen Methoden in StringLibrary über eine Code Coverage verfügt (dies wird durch eine blaue Linie „➖“ gekennzeichnet).

![Live Test-Explorer- und Code-Editor-Fenster nach Start von Live Unit Testing](media/lut-start/vs-2019/lut-results-cs.png)
::: moniker-end

Ausführlichere Informationen zu Testabdeckung und Testergebnissen erhalten Sie, indem Sie im Code-Editor-Fenster ein bestimmtes Code Coverage-Symbol auswählen. Gehen Sie wie folgt vor, um diese Details zu prüfen:

1. Klicken Sie in der Zeile, in der `if (String.IsNullOrWhiteSpace(s))` bei der Methode `StartsWithUpper` steht, auf das grüne Häkchen. Live Unit Testing gibt wie in der folgenden Abbildung gezeigt an, dass drei Tests die Codezeile abdecken, und dass alle erfolgreich ausgeführt wurden.

   ![Code Coverage für die Bedingungsanweisung „if“](media/lut-start/code-coverage-cs1.png)

1. Klicken Sie in der Zeile, in der `return Char.IsUpper(s[0])` bei der Methode `StartsWithUpper` steht, auf das grüne Häkchen. Live Unit Testing gibt wie in der folgenden Abbildung gezeigt an, dass nur zwei Tests die Codezeile abdecken, und dass alle erfolgreich ausgeführt wurden.

   ![Code Coverage für die return-Anweisung](media/lut-start/code-coverage-cs2.png)

Das größte, von Live Unit Testing ermittelte Problem ist die unvollständige Code Coverage. Dieses Problem wird im nächsten Abschnitt behandelt.

## <a name="expand-test-coverage"></a>Erweitern der Testabdeckung

In diesem Abschnitt erweitern Sie die Komponententests um die Methode `StartsWithLower`. Während Sie dies tun, testet Live Unit Testing Ihren Code weiterhin dynamisch.

Gehen Sie wie folgt vor, um die Code Coverage um die Methode `StartsWithLower` zu erweitern:

1. Fügen Sie die folgenden Methoden `TestStartsWithLower` und `TestDoesNotStartWithLower` zur Testquellcodedatei Ihres Projekts hinzu:

    [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest2.cs#1)]

1. Ändern Sie die Methode `DirectCallWithNullOrEmpty`, indem Sie den folgenden Code direkt nach dem Aufruf zur Methode [`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.isfalse) hinzufügen.

    [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest2.cs#2)]

1. Wenn Sie Ihren Quellcode ändern, führt Live Unit Testing automatisch neue und geänderte Tests aus. Alle Tests, einschließlich der zwei, die Sie hinzugefügt haben, und dem einen, den Sie geändert haben, wurden wie in der folgenden Abbildung gezeigt erfolgreich ausgeführt.

   ::: moniker range="vs-2017"
   ![Der Test-Explorer nach der Erweiterung der Testabdeckung](media/lut-start/test-dynamic.png)
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![Der Live Test-Explorer nach der Erweiterung der Testabdeckung](media/lut-start/vs-2019/test-dynamic.png)
   ::: moniker-end

1. Wechseln Sie zu dem Fenster mit dem Quellcode für die Klasse StringLibrary. Live Unit Testing zeigt jetzt an, dass Ihre Code Coverage um die Methode `StartsWithLower` erweitert wurde.

    ![Code Coverage für die Methode StartsWithLower](media/lut-start/lut-extended-cs.png)

In einigen Fällen sind erfolgreich ausgeführte Tests im **Test-Explorer** grau unterlegt. Dies deutet darauf hin, dass gerade ein Test ausgeführt wird oder dass der Test nicht erneut ausgeführt wurde, da keine Codeänderungen vorgenommen wurden, die seit seiner letzten Ausführung Auswirkungen auf den Test haben würden.

Bisher wurden alle Tests erfolgreich abgeschlossen. Im nächsten Abschnitt untersuchen wir, wie Sie Testfehler behandeln können.

## <a name="handle-a-test-failure"></a>Behandeln eines Testfehlers

In diesem Abschnitt lernen Sie, wie Sie mithilfe von Live Unit Testing Testfehler ermitteln, behandeln und beheben können. Hierzu müssen Sie die Testabdeckung um die Methode `HasEmbeddedSpaces` erweitern.

1. Fügen Sie die folgende Methode zu Ihrer Testdatei hinzu:

    [!code-csharp[The TestHasEmbeddedSpaces test method](samples/snippets/csharp/lut-start/unittest2.cs#3)]

1. Wenn der Test ausgeführt wird, gibt Live Unit Testing wie in der folgenden Abbildung gezeigt an, dass die `TestHasEmbeddedSpaces`-Methode fehlgeschlagen ist:

   ::: moniker range="vs-2017"
   ![Der Test-Explorer meldet einen nicht erfolgreichen Test](media/lut-start/test-failure.png)
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![Der Live Test-Explorer meldet einen nicht erfolgreichen Test](media/lut-start/vs-2019/test-failure.png)
   ::: moniker-end

1. Wählen Sie das Fenster aus, in dem der Bibliothekscode angezeigt wird. Live Unit Testing hat die Code Coverage um die `HasEmbeddedSpaces`-Methode erweitert. Der Testfehler wird zudem durch Hinzufügen eines roten „🞩“ in Zeilen, die von fehlerhaften Tests abgedeckt werden, angegeben.

1. Zeigen Sie auf die Zeile mit der `HasEmbeddedSpaces`-Methodensignatur. Live Unit Testing zeigt wie in der folgenden Abbildung gezeigt eine QuickInfo an, die angibt, dass die Methode von einem Test abgedeckt wird:

   ![Live Unit Testing-Informationen zu einem nicht erfolgreichen Test](media/lut-start/test-failure-info-cs.png)

1. Wählen Sie den fehlerhaften Test **TestHasEmbeddedSpaces** aus. Live Unit Testing bietet Ihnen wie in der folgenden Abbildung gezeigt einige Optionen wie das Ausführen aller Tests und das Debuggen aller Tests:

   ::: moniker range="vs-2017"
   ![Live Unit Testing-Optionen für einen nicht erfolgreichen Test](media/lut-start/test-failure-options.png)
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![Live Unit Testing-Optionen für einen nicht erfolgreichen Test](media/lut-start/vs-2019/test-failure-options.png)
   ::: moniker-end

1. Klicken Sie auf **Alle debuggen**, um den fehlgeschlagenen Test zu debuggen.

1. Visual Studio führt den Test im Debugmodus aus.

   Der Test weist jede Zeichenfolge in einem Array einer Variablen mit dem Namen `phrase` zu und übergibt sie an die `HasEmbeddedSpaces`-Methode. Die Ausführung des Programms wird angehalten, und wenn der Assert-Ausdruck erstmalig `false` lautet, wird der Debugger abgerufen. Das Ausnahmedialogfeld, das aus dem unerwarteten Wert im Aufruf der Methode [`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.istrue) resultiert, wird in der folgenden Abbildung gezeigt.

   ![Ausnahmedialogfeld in Live Unit Testing](media/lut-start/exception-dialog-cs.png)

   Darüber hinaus sind alle von Visual Studio bereitgestellten Debugtools verfügbar, um die Fehlerbehebung bei nicht erfolgreichen Tests zu unterstützen. Dies wird in der folgenden Abbildung veranschaulicht:

   ![Debugtools von Visual Studio](media/lut-start/debugging-tools-cs.png)

   Beachten Sie im Fenster **Auto**, dass der Wert der Variable `phrase` „Name\tDescription“ lautet und damit dem zweiten Element des Arrays entspricht. Von der Testmethode wird erwartet, dass die Methode `HasEmbeddedSpaces` bei der Übergabe dieser Zeichenfolge den Wert `true` zurückgibt; stattdessen wird der Wert `false` zurückgegeben. Offenbar erkennt die Methode das Tabstoppzeichen „\t“ nicht als eingebettetes Leerzeichen.

1. Klicken Sie auf **Debuggen** > **Fortfahren**, drücken Sie **F5**, oder klicken Sie in der Symbolleiste auf die Schaltfläche **Fortfahren**, um mit der Ausführung des Testprogramms fortzufahren. Der Test wird aufgrund eines Ausnahmefehlers beendet.
Die gelieferten Informationen sind für eine vorläufige Untersuchung des Fehlers ausreichend. Sämtliche eingebettete Leerzeichen werden entweder dadurch, dass `TestHasEmbeddedSpaces` (die Testroutine) von falschen Voraussetzungen ausgeht, oder von `HasEmbeddedSpaces` nicht ordnungsgemäß erkannt.

1. Starten Sie mit der `StringLibrary.HasEmbeddedSpaces`-Methode, um das Problem zu diagnostizieren und zu beheben. Sehen Sie sich den Vergleich in der `HasEmbeddedSpaces`-Methode an. Darin wird angenommen, dass U+0020 für ein eingebettetes Leerzeichen steht. Der Unicode-Standard enthält jedoch mehrere andere Leerzeichen. Dies deutet darauf hin, dass der Bibliothekscode nicht ordnungsgemäß auf ein Leerzeichen getestet wurde.

1. Ersetzen Sie den Übereinstimmungsvergleich durch einen Aufruf der <xref:System.Char.IsWhiteSpace%2A?displayProperty=fullName>-Methode:

    [!code-csharp[The TestHasEmbeddedSpaces test method](samples/snippets/csharp/lut-start/program2.cs#1)]

1. Live Unit Testing führt die fehlgeschlagene Testmethode automatisch wieder aus.

   Live Unit Testing zeigt die aktualisierten Ergebnisse an, die auch im Code-Editor angezeigt werden.

## <a name="see-also"></a>Siehe auch

- [Live Unit Testing in Visual Studio](live-unit-testing.md)
- [Live Unit Testing – FAQ (Häufig gestellte Fragen)](live-unit-testing-faq.md)
