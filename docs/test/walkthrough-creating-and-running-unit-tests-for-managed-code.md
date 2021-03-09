---
title: Tutorial für C#-Komponententest
description: Dieser Artikel führt Sie durch das Erstellen, Ausführen und Anpassen verschiedener Komponententests mithilfe des Microsoft-Komponententestframeworks für verwalteten Code und Visual Studio-Test-Explorer.
ms.custom: SEO-VS-2020
ms.date: 05/14/2019
ms.topic: conceptual
helpviewer_keywords:
- unit tests, walkthrough
- unit tests, creating
- unit tests, generating
- unit tests, running
- unit tests, authoring
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
author: mikejo5000
ms.openlocfilehash: a6ab205b7f651f8bb5954bee4998602c79fd78e7
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/03/2021
ms.locfileid: "101683929"
---
# <a name="walkthrough-create-and-run-unit-tests-for-managed-code"></a>Exemplarische Vorgehensweise: Erstellen und Ausführen von Komponententests für verwalteten Code

Dieser Artikel führt Sie durch das Erstellen, Ausführen und Anpassen verschiedener Komponententests mithilfe des Microsoft-Komponententestframeworks für verwalteten Code und Visual Studio-**Test-Explorer**. Sie beginnen mit einem C#-Projekt in der Entwicklungsphase und erstellen Tests zur Codeüberprüfung. Anschließend führen Sie die Tests aus und überprüfen die Ergebnisse. Dann können Sie den Projektcode ändern und die Tests erneut ausführen.



## <a name="create-a-project-to-test"></a>Erstellen eines zu testenden Projekts

::: moniker range="vs-2017"

1. Öffnen Sie Visual Studio.

2. Wählen Sie im Menü **Datei** die Option **Neues** > **Projekt** aus.

   Das Dialogfeld **Neues Projekt** wird angezeigt.

3. Wählen Sie unter der Kategorie **Visual C#** > **.NET Core** aus, und wählen Sie dann die Projektvorlage **Konsolen-App (.NET Core)** .

4. Benennen Sie das Projekt **Bank**, und klicken Sie auf **OK**.

   Das Projekt „Bank“ wird erstellt und im **Projektmappen-Explorer** angezeigt, und der Code-Editor mit der Datei *Program.cs* wird geöffnet.

   > [!NOTE]
   > Wenn die Datei *Program.cs* nicht im Editor geöffnet wird, doppelklicken Sie im **Projektmappen-Explorer** auf die Datei *Program.cs*, um diese zu öffnen.

::: moniker-end

::: moniker range=">=vs-2019"

1. Öffnen Sie Visual Studio.

2. Wählen Sie im Startfenster **Neues Projekt erstellen** aus.

3. Wählen Sie die C#-Projektvorlage **Konsolen-App** für .NET Core aus, und klicken Sie dann auf **Weiter**.

   > [!NOTE]
   > Wenn die Vorlage **Konsolen-App** nicht angezeigt wird, können Sie sie im Fenster **Neues Projekt erstellen** installieren. Wählen Sie in der Meldung **Sie finden nicht, wonach Sie suchen?** den Link **Weitere Tools und Features installieren** aus. Wählen Sie anschließend im Visual Studio-Installer die Workload **Plattformübergreifende .NET Core-Entwicklung** aus.

4. Geben Sie dem Projekt den Namen **Bank**, und klicken Sie dann auf **Weiter**.

   Wählen Sie entweder das empfohlene Zielframework (.NET Core 3.1) oder .NET 5 aus, und klicken Sie dann auf **Erstellen**.

   Das Projekt „Bank“ wird erstellt und im **Projektmappen-Explorer** angezeigt, und der Code-Editor mit der Datei *Program.cs* wird geöffnet.

   > [!NOTE]
   > Wenn die Datei *Program.cs* nicht im Editor geöffnet wird, doppelklicken Sie im **Projektmappen-Explorer** auf die Datei *Program.cs*, um diese zu öffnen.

::: moniker-end

5. Ersetzen Sie den Inhalt der Datei *Program.cs* durch den folgenden C#-Code, der die Klasse *BankAccount* definiert:

   ```csharp
   using System;

   namespace BankAccountNS
   {
       /// <summary>
       /// Bank account demo class.
       /// </summary>
       public class BankAccount
       {
           private readonly string m_customerName;
           private double m_balance;

           private BankAccount() { }

           public BankAccount(string customerName, double balance)
           {
               m_customerName = customerName;
               m_balance = balance;
           }

           public string CustomerName
           {
               get { return m_customerName; }
           }

           public double Balance
           {
               get { return m_balance; }
           }

           public void Debit(double amount)
           {
               if (amount > m_balance)
               {
                   throw new ArgumentOutOfRangeException("amount");
               }

               if (amount < 0)
               {
                   throw new ArgumentOutOfRangeException("amount");
               }

               m_balance += amount; // intentionally incorrect code
           }

           public void Credit(double amount)
           {
               if (amount < 0)
               {
                   throw new ArgumentOutOfRangeException("amount");
               }

               m_balance += amount;
           }

           public static void Main()
           {
               BankAccount ba = new BankAccount("Mr. Bryan Walton", 11.99);

               ba.Credit(5.77);
               ba.Debit(11.22);
               Console.WriteLine("Current balance is ${0}", ba.Balance);
           }
       }
   }
   ```

6. Ändern Sie den Dateinamen per Rechtsklick zu *BankAccount.cs* und wählen Sie **Umbenennen** in **Projektmappen-Explorer**.

7. Wählen Sie im Menü **Erstellen** die Option **Projektmappe erstellen** aus, oder drücken Sie **STRG** + **UMSCHALT** + **B**.

Sie haben nun ein Projekt mit Methoden, die Sie testen können. Die Tests in diesem Artikel beziehen sich auf die `Debit`-Methode. Die `Debit`-Methode wird aufgerufen, wenn von einem Konto Geld abgehoben wird.

## <a name="create-a-unit-test-project"></a>Ein Komponententestprojekt erstellen

1. Klicken Sie im Menü **Datei** auf **Hinzufügen** > **Neues Projekt**.

   > [!TIP]
   > Alternativ können Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf die Projektmappe klicken und anschließend **Hinzufügen** > **Neues Projekt** auswählen.

::: moniker range="vs-2017"

2. Erweitern Sie im Dialogfeld **Neues Projekt** erst die Option **Installiert** und dann die Option **Visual C#** , und klicken Sie anschließend auf **Test**.

3. Wählen Sie in der Liste der Vorlagen **MSTest Test Project (.NET Core)** aus.

4. Geben Sie im Feld **Name**`BankTests` ein, und klicken Sie dann auf die Schaltfläche **OK**.

   Das Projekt **BankTests** wird der Projektmappe **Bank** hinzugefügt.

::: moniker-end

::: moniker range=">=vs-2019"

2. Geben Sie im Suchfeld **Komponententest** ein, wählen Sie als Sprache **C#** und dann die C#-Vorlage **Komponententestprojekt** für .NET Core aus, und klicken Sie anschließend auf **Weiter**.

   > [!NOTE]
   > In Visual Studio 2019, Version 16.9 wurde der Name der MSTest-Projektvorlage von **MSTest-Komponententestprojekt (.NET Core)** in **Komponententestprojekt** geändert.

3. Geben Sie dem Projekt den Namen **BankTests**, und klicken Sie auf **Weiter**.

4. Wählen Sie entweder das empfohlene Zielframework (.NET Core 3.1) oder .NET 5 aus, und klicken Sie dann auf **Erstellen**.

   Das Projekt **BankTests** wird der Projektmappe **Bank** hinzugefügt.

::: moniker-end

5. Fügen Sie im Projekt **BankTests** einen Verweis auf die Projektmappe **Bank** ein.

   Wählen Sie im **Projektmappen-Explorer** im Projekt **BankTests** erst **Abhängigkeiten** und dann im Kontextmenü **Verweis hinzufügen** aus.

6. Erweitern Sie im Dialogfeld **Verweis-Manager** die Option **Projekte**, wählen Sie **Lösung** aus, und überprüfen Sie das Element **Bank**.

7. Klicken Sie auf **OK**.

## <a name="create-the-test-class"></a>Die Testklasse erstellen

Erstellen Sie eine Testklasse, um die `BankAccount`-Klasse zu überprüfen. Sie können die Datei *UnitTest1.cs* verwenden, die von der Projektvorlage generiert wurde; Datei und Klasse sollten jedoch einen aussagekräftigeren Namen erhalten.

### <a name="rename-a-file-and-class"></a>Umbenennen einer Datei und Klasse

1. Wählen Sie zum Umbenennen der Datei im **Projektmappen-Explorer** im BankTests-Projekt die Datei *UnitTest1.cs* aus. Wählen Sie im Kontextmenü die Option **Umbenennen** aus, oder drücken Sie **F2**, und benennen Sie dann die Datei in *BankAccountTests.cs* um.

::: moniker range="vs-2017"

2. Zum Umbenennen der Klasse wählen Sie **Ja** in dem Dialogfeld, in dem Sie gefragt werden, ob Sie auch Verweise auf das Codeelement umbenennen möchten.

::: moniker-end

::: moniker range=">=vs-2019"

2. Zeigen Sie im Code-Editor mit dem Cursor auf `UnitTest1`, klicken Sie mit der rechten Maustaste, und wählen Sie dann **Umbenennen** aus (oder drücken Sie **F2**), um die Klasse umzubenennen. Geben Sie **BankAccountTests** ein, und drücken Sie dann die **EINGABETASTE**.

::: moniker-end

Die Datei *BankAccountTests.cs* enthält nun den folgenden Code:

```csharp
using Microsoft.VisualStudio.TestTools.UnitTesting;

namespace BankTests
{
    [TestClass]
    public class BankAccountTests
    {
        [TestMethod]
        public void TestMethod1()
        {
        }
    }
}
```

### <a name="add-a-using-statement"></a>Hinzufügen einer Using-Anweisung

Fügen Sie der Testklasse eine [`using`-Anweisung](/dotnet/csharp/language-reference/keywords/using-statement) hinzu, damit Sie das Testprojekt ohne vollqualifizierte Namen aufrufen können. Fügen Sie am Anfang der Klassendatei Folgendes hinzu:

```csharp
using BankAccountNS;
```

### <a name="test-class-requirements"></a>Testklassenanforderungen

Die Mindestanforderungen für eine Testklasse lauten wie folgt:

- Das `[TestClass]`-Attribut ist für jede Klasse erforderlich, die in Test-Explorer auszuführende Komponententestmethoden enthält.

- Jede Testmethode, die vom Test-Explorer erkannt werden soll, muss über das `[TestMethod]`-Attribut verfügen.

Ein Komponententestprojekt kann auch über andere Klassen ohne das `[TestClass]` -Attribut verfügen, und Testklassen können andere Methoden ohne das `[TestMethod]` -Attribut aufweisen. Sie können diese anderen Klassen und Methoden in den Testmethoden aufrufen.

## <a name="create-the-first-test-method"></a>Die erste Testmethode erstellen

In dieser Vorgehensweise schreiben Sie Komponententestmethoden, um das Verhalten der `Debit`-Methode der `BankAccount`-Klasse zu überprüfen.

Es müssen mindestens drei Verhalten überprüft werden:

- Die Methode löst eine <xref:System.ArgumentOutOfRangeException> aus, wenn der Abbuchungsbetrag größer ist als das Guthaben.

- Außerdem löst sie eine <xref:System.ArgumentOutOfRangeException> aus, wenn der Abbuchungsbetrag kleiner als 0 (null) ist.

- Wenn der Abbuchungsbetrag gültig ist, zieht die Methode diesen vom Kontoguthaben ab.

> [!TIP]
> Sie können die Standardmethode `TestMethod1` löschen, da Sie sie für diese exemplarische Vorgehensweise nicht benötigen.

### <a name="to-create-a-test-method"></a>So erstellen Sie eine Testmethode

Im ersten Test überprüfen Sie, ob durch einen gültigen Betrag (kleiner als das Kontoguthaben und größer als null) der richtige Betrag vom Konto abgebucht wird. Fügen Sie dieser `BankAccountTests` -Klasse die folgende Methode hinzu.

```csharp
[TestMethod]
public void Debit_WithValidAmount_UpdatesBalance()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = 4.55;
    double expected = 7.44;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act
    account.Debit(debitAmount);

    // Assert
    double actual = account.Balance;
    Assert.AreEqual(expected, actual, 0.001, "Account not debited correctly");
}
```

Die Methode ist ganz einfach: Sie richtet ein neues `BankAccount`-Objekt mit einem Startguthaben ein und bucht dann einen gültigen Betrag ab. Sie verwendet die <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=nameWithType>-Methode, um zu überprüfen, ob das Guthaben zum Schluss den Erwartungen entspricht.

### <a name="test-method-requirements"></a>Testmethodenanforderungen

Eine Testmethode muss die folgenden Anforderungen erfüllen:

- Sie ist mit dem `[TestMethod]`-Attribut ausgestattet.

- Er gibt `void` zurück.

- Die darf keine Parameter aufweisen.

## <a name="build-and-run-the-test"></a>Den Test erstellen und ausführen

1. Wählen Sie im Menü **Erstellen** die Option **Projektmappe erstellen** aus, oder drücken Sie **STRG** + **UMSCHALT** + **B**.

2. Wenn der **Test-Explorer** nicht geöffnet ist, öffnen Sie ihn, indem Sie in der oberen Menüleiste **Testen** > **Windows** > **Test-Explorer** auswählen oder **STRG** + **E**, **T** drücken.

3. Wählen Sie **Alle ausführen** aus, oder drücken Sie **STRG** + **R**, **V**, um den Test auszuführen.

   Während der Test ausgeführt wird, gibt die Statusleiste am oberen Rand des Fensters **Test-Explorer** den aktuellen Status an. Am Ende des Testlaufs wird die Leiste grün, wenn alle Tests erfolgreich sind, oder rot, sofern bei einem der Tests ein Fehler auftritt.

   In diesem Fall schlägt der Test fehl.

4. Wählen Sie die Methode im **Test-Explorer** aus, um die Details unten im Fenster anzuzeigen.

## <a name="fix-your-code-and-rerun-your-tests"></a>Den Code korrigieren und die Tests erneut ausführen

Das Testergebnis enthält eine Meldung mit der Fehlerbeschreibung. Bei der `AreEqual`-Methode zeigt die Meldung an, was erwartet und was tatsächlich empfangen wurde. Es wurde davon ausgegangen, dass sich das Guthaben verringern würde. Stattdessen hat es sich aber um den Betrag der Abhebung erhöht.

Beim Komponententest wurde ein Fehler festgestellt: Der Abbuchungsbetrag wird dem Kontoguthaben *hinzugerechnet*, anstatt davon *abgezogen* zu werden.

### <a name="correct-the-bug"></a>Korrigieren des Fehlers

Um den Fehler zu beheben, ersetzten Sie in der Datei *BankAccount.cs* die Zeile:

```csharp
m_balance += amount;
```

Durch:

```csharp
m_balance -= amount;
```

### <a name="rerun-the-test"></a>Erneutes Ausführen des Tests

Wählen Sie im **Test-Explorer** die Option **Alle ausführen** aus, oder drücken Sie **STRG** + **R**, **V**, um den Test erneut auszuführen. Wenn die rote oder grüne Statusleiste grün wird, war der Test erfolgreich.

![Test-Explorer in Visual Studio 2019, der erfolgreiche Tests anzeigt](media/test-explorer-banktests-passed.png)

## <a name="use-unit-tests-to-improve-your-code"></a>Den Code mit Komponententests verbessern

In diesem Abschnitt wird beschrieben, wie ein iterativer Prozess bestehend aus Analyse, Komponententestentwicklung und Umgestaltung helfen kann, die Robustheit und Effektivität des Produktionscodes zu verbessern.

### <a name="analyze-the-issues"></a>Analysieren der Probleme

Sie haben eine Testmethode erstellt, um zu bestätigen, dass zum jeweiligen Zeitpunkt in der `Debit`-Methode ein gültiger Betrag abgezogen wird. Überprüfen Sie jetzt, ob die Methode eine <xref:System.ArgumentOutOfRangeException> auslöst, wenn der Abbuchungsbetrag

- entweder höher als das Guthaben ist
- oder unter 0 liegt.

### <a name="create-and-run-new-test-methods"></a>Erstellen und Ausführen neuer Testmethoden

Erstellen Sie eine Testmethode, um die Richtigkeit zu bestätigen, wenn der Abbuchungsbetrag unter 0 liegt:

```csharp
[TestMethod]
public void Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = -100.00;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act and assert
    Assert.ThrowsException<System.ArgumentOutOfRangeException>(() => account.Debit(debitAmount));
}
```

Verwenden Sie die <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A>-Methode, um zu bestätigen, dass die richtige Ausnahme ausgelöst wurde. Diese Methode führt zu einem Fehler des Tests, es sei denn, eine <xref:System.ArgumentOutOfRangeException> wird ausgelöst. Wenn Sie die zu testende Methode kurzzeitig ändern, um eine generischere <xref:System.ApplicationException> auszulösen, wenn der Abbuchungsbetrag unter 0 liegt, wird der Test richtig ausgeführt und schlägt fehl.

Gehen Sie folgendermaßen vor, um das Verhalten zu testen, wenn der abzubuchende Betrag höher ist als das Guthaben:

1. Erstellen Sie eine neue Testmethode mit dem Namen `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange`.

2. Kopieren Sie den Methodentext aus `Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange` in die neue Methode.

3. Legen Sie `debitAmount` auf eine Zahl größer als das Guthaben fest.

Führen Sie die zwei Tests aus, und stellen Sie sicher, dass sie erfolgreich abgeschlossen werden.

### <a name="continue-the-analysis"></a>Fortführen der Analyse

Die zu testende Methode kann weiter verbessert werden. In der aktuellen Implementierung gibt es keine Möglichkeit, zu erfahren, welche Bedingung (`amount > m_balance` oder `amount < 0`) zu der Ausnahme geführt hat, die während des Tests ausgelöst wurde. Wir wissen nur, dass irgendwo in der Methode eine `ArgumentOutOfRangeException` ausgelöst wurde. Es wäre wünschenswert zu wissen, welche Bedingung in `BankAccount.Debit` das Auslösen der Ausnahme verursacht hat (`amount > m_balance` oder `amount < 0`), sodass wir sicher sein können, dass die Methode die Integrität ihrer Argumente ordnungsgemäß überprüft.

Wenn Sie sich die zu testende Methode (`BankAccount.Debit`) noch einmal ansehen, werden Sie feststellen, dass beide Bedingungsanweisungen einen `ArgumentOutOfRangeException`-Konstruktor verwenden, der einfach den Namen des Arguments als Parameter übernimmt:

```csharp
throw new ArgumentOutOfRangeException("amount");
```

Sie können einen Konstruktor verwenden, der weitaus ausführlichere Informationen übermittelt: <xref:System.ArgumentOutOfRangeException.%23ctor(System.String,System.Object,System.String)> umfasst den Namen des Arguments, den Argumentwert und eine benutzerdefinierte Meldung. Sie können die zu testende Methode so umgestalten, dass sie diesen Konstruktor verwendet. Besser noch, Sie können öffentlich verfügbare Typmitglieder verwenden, um die Fehler anzugeben.

### <a name="refactor-the-code-under-test"></a>Umgestalten des zu testenden Codes

Definieren Sie zunächst zwei Konstanten für die Fehlermeldungen im Klassengültigkeitsbereich. Übertragen Sie diese in die getestete Klasse `BankAccount`:

```csharp
public const string DebitAmountExceedsBalanceMessage = "Debit amount exceeds balance";
public const string DebitAmountLessThanZeroMessage = "Debit amount is less than zero";
```

Ändern Sie dann die beiden Bedingungsanweisungen in der `Debit`-Methode:

```csharp
if (amount > m_balance)
{
    throw new System.ArgumentOutOfRangeException("amount", amount, DebitAmountExceedsBalanceMessage);
}

if (amount < 0)
{
    throw new System.ArgumentOutOfRangeException("amount", amount, DebitAmountLessThanZeroMessage);
}
```

### <a name="refactor-the-test-methods"></a>Umgestalten der Testmethoden

Gestalten Sie die Testmethoden um, indem Sie den Aufruf von <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> entfernen. Umschließen Sie den Aufruf von `Debit()` in einem `try/catch`-Block, fangen Sie die spezifische erwartete Ausnahme ab, und verifizieren Sie die zugehörige Meldung. Mithilfe der <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Contains%2A?displayProperty=fullName>-Methode können Sie zwei Zeichenfolgen miteinander vergleichen.

`Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` wird wie folgt formuliert:

```csharp
[TestMethod]
public void Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = 20.0;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act
    try
    {
        account.Debit(debitAmount);
    }
    catch (System.ArgumentOutOfRangeException e)
    {
        // Assert
        StringAssert.Contains(e.Message, BankAccount.DebitAmountExceedsBalanceMessage);
    }
}
```

### <a name="retest-rewrite-and-reanalyze"></a>Erneut testen, umschreiben und neu analysieren

Derzeit verarbeitet die Testmethode nicht alle Fälle, die sie verarbeiten sollte. Wenn die zu testende Methode, die `Debit`-Methode, keine <xref:System.ArgumentOutOfRangeException>-Ausnahme auslöst, wenn der `debitAmount`-Wert größer als der Saldo (oder unter null (0)) liegt, wird die Testmethode erfolgreich ausgeführt. Dies ist nicht gut, da bei der Testmethode ein Fehler auftreten soll, wenn keine Ausnahme ausgelöst wird.

Dabei handelt es sich um einen Fehler der Testmethode. Um das Problem zu beheben, fügen Sie eine <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A>-Assertion am Ende der Testmethode hinzu, um den Fall abzudecken, in dem keine Ausnahme ausgelöst wird.

Ein erneuter Test zeigt, dass der Test jetzt *fehlschlägt*, wenn die richtige Ausnahme erfasst wird. Der `catch`-Block fängt die Ausnahme zwar ab, aber die Methode wird weiterhin ausgeführt und schlägt bei der neuen <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A>-Assertion fehl. Um dieses Problem zu beheben, fügen Sie nach `return` eine `StringAssert`-Anweisung zum Block `catch` hinzu. Wenn Sie den Test erneut ausführen, bestätigen Sie, dass Sie dieses Problem behoben haben. Die fertige Version von `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` sieht wie folgt aus:

```csharp
[TestMethod]
public void Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = 20.0;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act
    try
    {
        account.Debit(debitAmount);
    }
    catch (System.ArgumentOutOfRangeException e)
    {
        // Assert
        StringAssert.Contains(e.Message, BankAccount.DebitAmountExceedsBalanceMessage);
        return;
    }

    Assert.Fail("The expected exception was not thrown.");
}
```

### <a name="conclusion"></a>Schlussbemerkung

Aufgrund der Verbesserungen des Testcodes wurden stabilere und informationsreichere Testmethoden erstellt. Aber noch wichtiger: es wurde auch der Code verbessert, der getestet werden soll.

> [!TIP]
> In dieser exemplarischen Vorgehensweise wird das Microsoft-Komponententest-Framework für verwalteten Code verwendet. Der **Test-Explorer** kann außerdem Tests von Komponententestframeworks von Drittanbietern ausführen, die über Adapter für den **Test-Explorer** verfügen. Weitere Informationen finden Sie unter [Installieren von Frameworks für Komponententests von Drittanbietern](../test/install-third-party-unit-test-frameworks.md).

## <a name="see-also"></a>Siehe auch

Informationen zum Ausführen von Tests über die Befehlszeile finden Sie unter [Exemplarische Vorgehensweise: Befehlszeilenoptionen für VSTest.Console.exe](vstest-console-options.md).
