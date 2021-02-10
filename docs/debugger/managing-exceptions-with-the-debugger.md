---
title: Verwalten von Ausnahmen mit dem Debugger | Microsoft-Dokumentation
description: Es wird beschrieben, wie Sie angeben, bei welchen Ausnahmen der Debugger eine Unterbrechung vornimmt, an welchem Punkt die Unterbrechung durch den Debugger erfolgen soll und wie Unterbrechungen verarbeitet werden.
ms.custom: SEO-VS-2020, seodec18
ms.date: 10/09/2018
ms.topic: how-to
f1_keywords:
- vs.debug.exceptions
- vs.debug.exceptions.find
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- run-time errors
- exception handling, during debugging
- errors [debugger]
- debugger, runtime errors
- On Error-style error handlers
- exceptions, Win32
- run-time errors, debugging
- Win32, exceptions
- run time, exceptions
- error handling
- debugging [Visual Studio], exception handling
- common language runtime, exceptions
- native run-time checks
- exceptions, debugging
ms.assetid: 43a77fa8-37d0-4c98-a334-0134dbca4ece
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b594857b00ee233c186008efc9d0fba7d968a9bc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893164"
---
# <a name="manage-exceptions-with-the-debugger-in-visual-studio"></a>Verwalten von Ausnahmen mit dem Debugger in Visual Studio

Eine Ausnahme ist ein Hinweis auf einen Fehlerstatus, der auftritt, während ein Programm ausgeführt wird. Sie können den Debugger informieren, bei welchen Ausnahmen oder Gruppen von Ausnahmen eine Unterbrechung erforderlich erfolgen soll und an welchem Punkt der Debugger eine Unterbrechung vornehmen soll (d.h. Pause im Debugger). Wenn der Debugger ein Unterbrechung vornimmt, wird angezeigt, wo die Ausnahme ausgelöst wurde. Sie können Ausnahmen auch hinzufügen oder löschen. Wenn eine Projektmappe in Visual Studio geöffnet ist, verwenden Sie **Debuggen > Windows > Ausnahmeeinstellungen**, um das Fenster **Ausnahmeeinstellungen** zu öffnen.

Stellen Sie Handler bereit, die auf die wichtigsten Ausnahmen reagieren. Wenn Sie wissen möchten, wie Handler für Ausnahmen hinzugefügt werden, finden Sie weitere Informationen unter [Korrigieren von Fehlern durch das Schreiben von besserem C#-Code](../debugger/write-better-code-with-visual-studio.md). Erfahren Sie außerdem, wie Sie den Debugger so konfigurieren, dass die Ausführung für einige Ausnahmen immer unterbricht.

Wenn eine Ausnahme ausgelöst wird, schreibt der Debugger eine Ausnahmemeldung an das Fenster **Ausgabe**. In den folgenden Fällen kann die Ausführung unterbrochen werden:

- Es wird eine Ausnahme ausgelöst, die nicht behandelt wird.
- Der Debugger wird so konfiguriert, dass die Ausführung abgebrochen wird, bevor ein Handler aufgerufen wird.
- Wenn Sie [Nur eigenen Code](../debugger/just-my-code.md) festgelegt haben und der Debugger so konfiguriert ist, dass eine Unterbrechung bei jeder Ausnahme veranlasst wird, die nicht im Benutzercode behandelt wird.

> [!NOTE]
> ASP.NET verfügt über einen Ausnahmehandler der obersten Ebene, der Fehlerseiten in einem Browser anzeigt. Die Ausführung wird nicht unterbrochen, es sei denn, **Nur eigenen Code** ist aktiviert. Ein Beispiel finden Sie weiter unten unter [Einstellen des Debuggers zum Fortfahren bei nicht vom Benutzercode behandelten Ausnahmen](#BKMK_UserUnhandled).

<!-- Two consecutive notes are intentional here...-->

> [!NOTE]
> In Visual Basic-Anwendungen werden alle Fehler vom Debugger als Ausnahmen behandelt. Dies ist auch dann der Fall, wenn Sie Fehlerhandler des Typs On Error verwenden.

## <a name="tell-the-debugger-to-break-when-an-exception-is-thrown"></a>Festlegen, dass der Debugger die Ausführung bei ausgelöster Ausnahme unterbricht

Der Debugger kann die Ausführung beim Auftreten einer Ausnahme sofort unterbrechen. Dadurch haben Sie die Möglichkeit, die Ausnahme zu untersuchen, bevor ein Handler aufgerufen wird.

Erweitern Sie im Fenster **Ausnahmeeinstellungen** (**Debuggen > Windows > Ausnahmeeinstellungen**) den Knoten für eine Kategorie von Ausnahmen, z. B. **CLR-Ausnahmen**. Aktivieren Sie dann das Kontrollkästchen für eine bestimmte Ausnahme innerhalb dieser Kategorie, z. B. **System.AccessViolationException**. Sie können auch eine ganze Kategorie von Ausnahmen auswählen.

![AccessViolationException ist aktiviert](../debugger/media/exceptionsettingscheckaccess.png "ExceptionSettingsCheckAccess")

> [!TIP]
> Nach spezifischen Ausnahmen können Sie mithilfe des Fensters **Suche** in der Symbolleiste **Ausnahmeeinstellungen** suchen. Sie können die Suchergebnisse auch nach bestimmten Namespaces filtern (z. B. **System.IO**).

Wenn Sie eine Ausnahme im Fenster **Ausnahmeeinstellungen** auswählen, wird die Ausführung des Debuggers bei jeder Auslösung der Ausnahme unterbrochen, und zwar unabhängig davon, ob die Ausnahme behandelt wird. Die Ausnahme wird nun als „erste Chance“ bezeichnet. Im Folgenden einige Szenarios:

- In der folgenden C#-Konsolenanwendung löst die Main-Methode eine **AccessViolationException** in einem `try/catch`-Block aus.

  ```csharp
  static void Main(string[] args)
  {
      try
      {
          throw new AccessViolationException();
          Console.WriteLine("here");
      }
      catch (Exception e)
      {
          Console.WriteLine("caught exception");
      }
      Console.WriteLine("goodbye");
  }
  ```

  Wenn Sie **AccessViolationException** in den **Ausnahmeeinstellungen** aktiviert haben, wird die Ausführung an der `throw`-Zeile unterbrochen, wenn Sie diesen Code im Debugger ausführen. Danach können Sie die Ausführung fortsetzen. In der Konsole sollten beide Zeilen angezeigt werden:

  ```cmd
  caught exception
  goodbye
  ```

  Die `here`-Zeile wird jedoch nicht angezeigt.

- Eine C#-Konsolenanwendung verweist auf eine Klassenbibliothek mit einer Klasse, die über zwei Methoden verfügt. Eine Methode löst eine Ausnahme aus und behandelt sie, während eine zweite Methode die gleiche Ausnahme auslöst, sie aber nicht behandelt.

  ```csharp
  public class Class1
  {
      public void ThrowHandledException()
      {
          try
          {
              throw new AccessViolationException();
          }
          catch (AccessViolationException ave)
          {
              Console.WriteLine("caught exception" + ave.Message);
          }
      }

      public void ThrowUnhandledException()
      {
          throw new AccessViolationException();
      }
  }
  ```

  Dies ist die Hauptmethode der Konsolenanwendung:

  ```csharp
  static void Main(string[] args)
  {
      Class1 class1 = new Class1();
      class1.ThrowHandledException();
      class1.ThrowUnhandledException();
  }
  ```

  Wenn Sie **AccessViolationException** in den **Ausnahmeeinstellungen** aktiviert haben, wird die Ausführung an der `throw`-Zeile sowohl in **ThrowHandledException()** als auch in **ThrowUnhandledException()** unterbrochen, wenn Sie diesen Code im Debugger ausführen.

Um die Ausnahmeeinstellungen mit den Standardeinstellungen wiederherzustellen, wählen Sie die Schaltfläche **Liste der Standardeinstellungen wiederherstellen** aus:

![Wiederherstellen der Standardeinstellungen in den Ausnahmeeinstellungen](../debugger/media/restoredefaultexceptions.png "RestoreDefaultExceptions")

## <a name="tell-the-debugger-to-continue-on-user-unhandled-exceptions"></a><a name="BKMK_UserUnhandled"></a>Einstellen des Debuggers zum Fortfahren bei nicht vom Benutzercode behandelten Ausnahmen

Wenn Sie .NET- oder JavaScript-Code mit [Nur eigenen Code](../debugger/just-my-code.md) debuggen, können Sie den Debugger so einstellen, dass er bei Ausnahmen, die an anderer Stelle als im Benutzercode behandelt werden, die Ausführung nicht unterbricht.

1. Öffnen Sie im Fenster **Ausnahmeeinstellungen** das Kontextmenü, indem Sie mit der rechten Maustaste auf eine Spaltenbezeichnung klicken, und wählen Sie dann **Spalten anzeigen > Weitere Aktionen** aus. (Wenn Sie **Nur eigenen Code** deaktiviert haben, wird dieser Befehl nicht angezeigt.) Eine dritte Spalte mit dem Namen **Zusätzliche Aktionen** wird angezeigt.

   ![Spalte „Zusätzliche Aktionen“](../debugger/media/additionalactionscolumn.png "AdditionalActionsColumn")

   Für eine Ausnahme, die **Fortfahren, wenn in Benutzercode nicht behandelt** in dieser Spalte anzeigt, wird der Debugger fortgesetzt, wenn diese Ausnahme nicht im Benutzercode, sondern extern behandelt wird.

2. Wenn Sie diese Einstellung für eine bestimmte Ausnahme ändern möchten, wählen Sie die Ausnahme aus, klicken Sie mit der rechten Maustaste, um das Kontextmenü anzuzeigen, und wählen Sie dann **Fortfahren, wenn in Benutzercode nicht behandelt** aus. Sie können auch die Einstellung für eine ganze Kategorie von Ausnahmen ändern, z. B. die gesamten CLR-Ausnahmen).

   ![Einstellung „Fortfahren, wenn in Benutzercode nicht behandelt“](../debugger/media/continuewhenunhandledinusercodesetting.png "ContinueWhenUnhandledInUserCodeSetting")

Beispielsweise behandeln ASP.NET-Webanwendungen Ausnahmen dadurch, dass sie diese in einen HTTP 500-Statuscode konvertieren ([Ausnahmebehandlung in der ASP.NET-Web-API](/aspnet/web-api/overview/error-handling/exception-handling)), wodurch es möglicherweise unmöglich wird, die Quelle der Ausnahme zu bestimmen. Im folgenden Beispiel wird durch den Benutzercode `String.Format()` aufgerufen, wodurch eine <xref:System.FormatException>ausgelöst wird. Die Ausführung wird folgendermaßen unterbrochen:

![Unterbrechen bei vom Benutzer nicht behandelter Ausnahme](../debugger/media/exceptionunhandledbyuser.png "ExceptionUnhandledByUser")

## <a name="add-and-delete-exceptions"></a>Hinzufügen und Löschen von Ausnahmen

Sie können Ausnahmen hinzufügen und löschen. Wenn Sie einen Ausnahmetyp aus einer Kategorie löschen möchten, wählen Sie die Ausnahme aus, und klicken Sie auf die Schaltfläche **Ausgewählte Ausnahme aus der Liste löschen** (das Minuszeichen) auf der Symbolleiste **Ausnahmeeinstellungen**. Sie können auch mit der rechten Maustaste auf die Ausnahme klicken und dann im Kontextmenü **Löschen** auswählen. Das Löschen einer Ausnahme hat dieselbe Wirkung wie das Deaktivieren, d. h. der Debugger wird nicht unterbrochen, wenn die Ausnahme ausgelöst wird.

So fügen Sie eine Ausnahme hinzu:

1. Wählen Sie im Fenster **Ausnahmeeinstellungen** eine der Ausnahmekategorien (z. B. **CLR**) aus.

2. Wählen Sie die Schaltfläche **Der ausgewählten Kategorie eine Ausnahme hinzufügen** (das Pluszeichen) aus.

   ![Schaltfläche „Der ausgewählten Kategorie eine Ausnahme hinzufügen“](../debugger/media/addanexceptiontotheselectedcategorybutton.png "AddAnExceptionToTheSelectedCategoryButton")

3. Geben Sie den Namen der Ausnahme ein (z. B. **System.UriTemplateMatchException**).

   ![Eingeben des Ausnahmenamens](../debugger/media/typetheexceptionname.png "TypeTheExceptionName")

   Die Ausnahme wird der Liste hinzugefügt (in alphabetischer Reihenfolge) und automatisch aktiviert.

Wenn Sie eine Ausnahme zu den Ausnahmen für GPU-Speicherzugriff, JavaScript-Laufzeitausnahmen oder Win32-Ausnahmekategorien hinzufügen möchten, binden Sie den Fehlercode und die Beschreibung ein.

> [!TIP]
> Überprüfen Sie die Rechtschreibung! Das Fenster **Ausnahmeeinstellungen** prüft nicht, ob eine hinzugefügte Ausnahme vorhanden ist. Bei Eingabe von **Sytem.UriTemplateMatchException** erhalten Sie daher einen Eintrag für diese Ausnahme und nicht für **System.UriTemplateMatchException**.

Ausnahmeeinstellungen werden in der SUO-Datei der Projektmappe beibehalten, sie gelten also für eine bestimmte Projektmappe. Sie können spezifische Ausnahmeeinstellungen nicht für andere Projektmappen wiederverwenden. Nun werden nur hinzugefügte Ausnahmen beibehalten, gelöschte Ausnahmen nicht. Die hinzugefügte Ausnahme ist weiterhin vorhanden, wenn Sie die Projektmappe schließen und erneut öffnen. Wenn Sie eine Ausnahme dagegen löschen und die Projektmappe anschließend schließen und wieder öffnen, wird die Ausnahme nicht mehr angezeigt.

Das Fenster **Ausnahmeeinstellungen** unterstützt generische Ausnahmetypen in C#, aber nicht in Visual Basic. Um bei Ausnahmen wie `MyNamespace.GenericException<T>`eine Unterbrechung vorzunehmen, müssen Sie die Ausnahme als **MyNamespace.GenericException`1** hinzufügen. Wenn Sie eine Ausnahme wie den folgenden Code erstellt haben:

```csharp
public class GenericException<T> : Exception
{
    public GenericException() : base("This is a generic exception.")
    {
    }
}
```

Sie können die Ausnahme den **Ausnahmeeinstellungen** mit dem oben beschriebenen Verfahren hinzufügen:

![Hinzufügen einer generischen Ausnahme](../debugger/media/addgenericexception.png "AddGenericException")

## <a name="add-conditions-to-an-exception"></a>Hinzufügen von Bedingungen zu einer Ausnahme

Verwenden Sie das Fenster **Ausnahmeeinstellungen**, um Bedingungen für Ausnahmen festzulegen. Zu den derzeit unterstützten Bedingungen gehören die Modulnamen, die für die Ausnahme eingeschlossen oder ausgeschlossen werden sollen. Durch Festlegen von Modulnamen als Bedingungen können Sie eine Unterbrechung für die Ausnahme nur für bestimmte Codemodule auswählen. Sie können eine Unterbrechung für bestimmte Module auch vermeiden.

> [!NOTE]
> Das Hinzufügen von Bedingungen zu einer Ausnahme wird ab [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] unterstützt.

So fügen Sie bedingte Ausnahmen hinzu:

1. Wählen Sie im Fenster „Ausnahmeeinstellungen“ die Schaltfläche **Bedingungen bearbeiten** aus, oder klicken Sie mit der rechten Maustaste auf die Ausnahme, und wählen Sie dann **Bedingungen bearbeiten** aus.

   ![Bedingungen für eine Ausnahme](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

2. Wenn Sie der Ausnahme zusätzliche erforderliche Bedingungen hinzufügen möchten, wählen Sie **Bedingung hinzufügen** für jede neue Bedingung aus. Weitere Bedingungszeilen werden angezeigt.

   ![Zusätzliche Bedingungen für eine Ausnahme](../debugger/media/extraconditionsforanexception.png "ExtraConditionsForAnException")

3. Geben Sie für jede Bedingungszeile den Namen des Moduls ein, und ändern Sie die Liste der Vergleichsoperatoren in **Equals** (gleich) oder **Not equals** (nicht gleich). Sie können Platzhalter ( **\\\*** ) im Namen angeben, um mehrere Module anzugeben.

4. Wenn Sie eine Bedingung löschen müssen, wählen Sie das **X** am Ende der Bedingungszeile aus.

## <a name="see-also"></a>Siehe auch

- [Fortfahren mit der Ausführung nach einer Ausnahme](../debugger/continuing-execution-after-an-exception.md)<br/>
- [How to: Untersuchen von Systemcode nach einer Ausnahme](../debugger/how-to-examine-system-code-after-an-exception.md)<br/>
- [How to: Use native run-time checks (Vorgehensweise: Verwenden von nativen Laufzeitüberprüfungen)](../debugger/how-to-use-native-run-time-checks.md)<br/>
- [Erster Einblick in den Debugger](../debugger/debugger-feature-tour.md)
