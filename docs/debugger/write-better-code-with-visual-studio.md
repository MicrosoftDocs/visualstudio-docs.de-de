---
title: Debugverfahren und -tools
description: Schreiben Sie mithilfe von Visual Studio besseren Code mit weniger Fehlern, um Ausnahmen zu beseitigen, Fehler zu beheben und den Code zu verbessern.
ms.custom:
- debug-experiment
- seodec18
ms.date: 02/14/2020
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c69fe13821f595a137c07d545a4ccfb10fc89b34
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99904946"
---
# <a name="debugging-techniques-and-tools-to-help-you-write-better-code"></a>Debugverfahren und -tools zum Schreiben von besserem Code

Das Beheben von Fehlern im Code kann zeitaufwändig und manchmal frustrierend sein. Es dauert lange, bis man herausgefunden hat, wie man effektiv Fehler beheben kann. Eine integrierte Entwicklungsumgebung (IDE) wie Visual Studio kann Ihnen diese Aufgabe um einiges leichter machen. Eine IDE kann Ihnen helfen, Fehler zu beheben und den Code schneller zu debuggen. Außerdem bietet sie Unterstützung beim Schreiben von besserem Code mit weniger Fehlern. Ziel dieses Artikels ist es, Ihnen einen ganzheitlichen Überblick über den Fehlerbehebungsprozess zu geben, damit Sie wissen, wann Sie das Codeanalysetool bzw. den Debugger verwenden, wie Sie Ausnahmen beseitigen und wie Sie beim Programmieren klare Absichten verfolgen. Wenn Sie bereits wissen, dass Sie den Debugger verwenden müssen, finden Sie weitere Informationen unter [Ein erster Blick auf den Visual Studio-Debugger](../debugger/debugger-feature-tour.md).

In diesem Artikel wird die Nutzung der IDE erläutert, um Ihre Programmierungsvorgänge produktiver zu machen. Es werden unter anderem folgende Aufgaben erläutert:

* Vorbereiten des Codes für das Debuggen mithilfe des Codeanalysetools der IDE

* Beseitigen von Ausnahmen (Laufzeitfehler)

* Minimieren von Fehlern durch Programmieren mit klarer Absicht (mithilfe von Assert)

* Verwendung des Debuggers

Zur Veranschaulichung dieser Aufgaben zeigen wir einige der gängigsten Arten von Fehlern, die beim Debuggen Ihrer Apps auftreten. Obwohl der Beispielcode in C# geschrieben wurde, sind die konzeptionellen Informationen in der Regel auf C++, Visual Basic, JavaScript und andere von Visual Studio unterstützte Sprachen anwendbar (sofern nicht anders angegeben). Die Screenshots wurden in C# erstellt.

## <a name="create-a-sample-app-with-some-bugs-and-errors-in-it"></a>Erstellen einer Beispiel-App mit Fehlern

Der folgende Code enthält einige Fehler, die Sie mithilfe der Visual Studio-IDE beheben können. Bei der App handelt es sich um eine einfache App, die das Abrufen von JSON-Daten aus einem Vorgang simuliert, die Daten in ein Objekt deserialisiert und eine einfache Liste mit den neuen Daten aktualisiert.

So erstellen Sie die App:

1. Auf Ihrem Computer muss Visual Studio installiert sein, und in Visual Studio muss, je nachdem, welchen Typ von App Sie erstellen möchten, entweder die Workload **Plattformübergreifende .NET Core-Entwicklung** oder die Workload **.NET-Desktopentwicklung** installiert sein.

    Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads/) kostenlos herunterladen.

    Wenn Sie die Workload installieren müssen und Visual Studio bereits installiert ist, klicken Sie auf **Extras** > **Tools und Features abrufen...** . Der Visual Studio-Installer wird gestartet. Wählen Sie die Workload **Plattformübergreifende .NET Core-Entwicklung** oder die Workload **.NET-Desktopentwicklung** aus, und klicken Sie auf **Anpassen**.

1. Öffnen Sie Visual Studio.

    ::: moniker range=">=vs-2019"
    Wählen Sie im Startfenster **Neues Projekt erstellen** aus. Geben Sie im Suchfeld den Begriff **Konsole** ein, und wählen Sie dann entweder **Konsolen-App (.NET Core)** oder **Konsolen-App (.NET Framework)** aus. Wählen Sie **Weiter** aus. Geben Sie einen Projektnamen wie **Console_Parse_JSON** ein, und klicken Sie dann auf **Erstellen**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Klicken Sie oben in der Menüleiste auf **Datei** > **Neu** > **Projekt**. Klicken Sie im linken Bereich des Dialogfelds **Neues Projekt** unter **Visual C#** auf die Option **Konsolen-App** und dann im mittleren Bereich entweder auf **Konsolen-App (.NET Core)** oder auf **Konsolen-App (.NET Framework)** . Geben Sie einen Namen wie **Console_Parse_JSON** ein, und klicken Sie auf **OK**.
    ::: moniker-end

    Wenn die Projektvorlage **Konsolen-App (.NET Core)** oder **Konsolen-App (.NET Framework)** nicht angezeigt wird, navigieren Sie zu **Tools** > **Get Tools and Features** (Tools und Features abrufen), wodurch der Visual Studio-Installer geöffnet wird. Wählen Sie entweder die Workload **Plattformübergreifende .NET Core-Entwicklung** oder die Workload **.NET-Desktopentwicklung** aus, und klicken Sie dann auf **Anpassen**.

    Visual Studio erstellt das Konsolenprojekt, das im Projektmappen-Explorer (rechter Bereich) angezeigt wird.

1. Ersetzen Sie den Standardcode in der *Program.cs*-Datei des Projekts durch den unten stehenden Beispielcode.

```csharp
using System;
using System.Collections.Generic;
using System.Runtime.Serialization.Json;
using System.Runtime.Serialization;
using System.IO;

namespace Console_Parse_JSON
{
    class Program
    {
        static void Main(string[] args)
        {
            var localDB = LoadRecords();
            string data = GetJsonData();

            User[] users = ReadToObject(data);

            UpdateRecords(localDB, users);

            for (int i = 0; i < users.Length; i++)
            {
                List<User> result = localDB.FindAll(delegate (User u) {
                    return u.lastname == users[i].lastname;
                    });
                foreach (var item in result)
                {
                    Console.WriteLine($"Matching Record, got name={item.firstname}, lastname={item.lastname}, age={item.totalpoints}");
                }
            }

            Console.ReadKey();
        }

        // Deserialize a JSON stream to a User object.
        public static User[] ReadToObject(string json)
        {
            User deserializedUser = new User();
            User[] users = { };
            MemoryStream ms = new MemoryStream(Encoding.UTF8.GetBytes(json));
            DataContractJsonSerializer ser = new DataContractJsonSerializer(users.GetType());

            users = ser.ReadObject(ms) as User[];

            ms.Close();
            return users;
        }

        // Simulated operation that returns JSON data.
        public static string GetJsonData()
        {
            string str = "[{ \"points\":4o,\"firstname\":\"Fred\",\"lastname\":\"Smith\"},{\"lastName\":\"Jackson\"}]";
            return str;
        }

        public static List<User> LoadRecords()
        {
            var db = new List<User> { };
            User user1 = new User();
            user1.firstname = "Joe";
            user1.lastname = "Smith";
            user1.totalpoints = 41;

            db.Add(user1);

            User user2 = new User();
            user2.firstname = "Pete";
            user2.lastname = "Peterson";
            user2.totalpoints = 30;

            db.Add(user2);

            return db;
        }
        public static void UpdateRecords(List<User> db, User[] users)
        {
            bool existingUser = false;

            for (int i = 0; i < users.Length; i++)
            {
                foreach (var item in db)
                {
                    if (item.lastname == users[i].lastname && item.firstname == users[i].firstname)
                    {
                        existingUser = true;
                        item.totalpoints += users[i].points;

                    }
                }
                if (existingUser == false)
                {
                    User user = new User();
                    user.firstname = users[i].firstname;
                    user.lastname = users[i].lastname;
                    user.totalpoints = users[i].points;

                    db.Add(user);
                }
            }
        }
    }

    [DataContract]
    internal class User
    {
        [DataMember]
        internal string firstname;

        [DataMember]
        internal string lastname;

        [DataMember]
        // internal double points;
        internal string points;

        [DataMember]
        internal int totalpoints;
    }
}
```

## <a name="find-the-red-and-green-squiggles"></a>Suche nach roten und grünen Wellenlinien

Überprüfen Sie den Code im Code-Editor auf die roten und grünen Wellenlinien, bevor Sie versuchen, die Beispiel-App zu starten und den Debugger auszuführen. Diese stellen Fehler und Warnungen dar, die vom Codeanalysetool der IDE identifiziert werden. Die roten Wellenlinien sind Kompilierzeitfehler, die Sie beheben müssen, bevor Sie den Code ausführen können. Bei den grünen Wellenlinien handelt es sich um Warnungen. Obwohl Sie Ihre App häufig ausführen können, ohne die Warnungen zu beseitigen, können diese eine Fehlerquelle sein, und Sie sparen sich häufig Zeit und Nerven bei deren Überprüfung. Diese Warnungen und Fehler werden auch im Fenster **Fehlerliste** angezeigt, wenn Sie eine Listenansicht bevorzugen.

In der Beispiel-App werden mehrere rote Wellenlinien und eine grüne Wellenlinie angezeigt, die Sie beseitigen müssen. Hier ist der erste Fehler.

![Fehler, der mit roter Wellenlinie angezeigt wird](../debugger/media/write-better-code-red-squiggle.png)

Sie nutzen zum Beheben des Fehlers eine weitere Funktion der IDE, die durch das Glühbirnensymbol dargestellt wird.

## <a name="check-the-light-bulb"></a>Glühbirne als Hinweis

Die erste rote Wellenlinie stellt einen Kompilierzeitfehler dar. Bewegen Sie den Mauszeiger darüber, und die Meldung ```The name `Encoding` does not exist in the current context``` wird angezeigt.

Beachten Sie, dass für diesen Fehler ein Glühbirnensymbol unten links anzeigt wird. Neben dem Schraubendrehersymbol ![Schraubendrehersymbol](../ide/media/screwdriver-icon.png) stellt das Glühbirnensymbol ![Glühbirnensymbol](../ide/media/light-bulb-icon.png) schnelle Aktionen dar, mit denen Sie Code inline korrigieren oder umgestalten können. Die Glühbirne stellt Probleme dar, die Sie beheben *sollten*. Der Schraubendreher steht für Probleme, die Sie beheben können. Verwenden Sie die erste vorgeschlagene Korrektur, um diesen Fehler zu beheben, indem Sie auf der linken Seite auf **using System.Text** klicken.

![Verwenden der Glühbirne zum Korrigieren von Code](../debugger/media/write-better-code-missing-include.png)

Wenn Sie auf dieses Element klicken, fügt Visual Studio die `using System.Text`-Anweisung am Anfang der Datei *Program.cs* ein, und die rote Wellenlinie verschwindet. (Wenn Sie nicht sicher sind, was eine vorgeschlagene Korrektur bewirkt, können Sie vor deren Anwendung auf der rechten Seite auf den Link **Vorschau der Änderungen anzeigen** klicken.)

Der vorherige Fehler ist ein häufiger Fehler, den Sie normalerweise beheben, indem Sie dem Code eine neue `using`-Anweisung hinzufügen. Es gibt mehrere häufige, ähnliche Fehler (z. B. ```The type or namespace `Name` cannot be found.```). Diese Arten von Fehlern können auf einen fehlenden Assemblyverweis (mit der rechten Maustaste auf das Projekt und dann auf **Hinzufügen** > **Verweis** klicken), einen falsch geschriebenen Namen oder eine fehlende Bibliothek hindeuten, die Sie hinzufügen müssen (für C# mit der rechten Maustaste auf das Projekt und dann auf **NuGet-Pakete verwalten** klicken).

## <a name="fix-the-remaining-errors-and-warnings"></a>Beheben der restlichen Fehler und Warnungen

In diesem Code sind einige weitere Wellenlinien zu sehen. Hier sehen Sie einen häufigen Typkonvertierungsfehler. Wenn Sie mit dem Mauszeiger auf die Wellenlinie zeigen, sehen Sie, dass der Code versucht, eine Zeichenfolge in eine ganze Zahl zu konvertieren. Dies wird nicht unterstützt, es sei denn, Sie fügen expliziten Code hinzu, um die Konvertierung vorzunehmen.

![Typkonvertierungsfehler](../debugger/media/write-better-code-conversion-error.png)

Da das Codeanalysetool Ihre Absicht nicht erraten kann, sind in diesem Fall keine Glühbirnen zu sehen, um Ihnen Unterstützung zu bieten. Sie müssen die Absicht des Codes kennen, um diesen Fehler zu beheben. In diesem Beispiel ist es nicht allzu schwer zu erkennen, dass `points` ein numerischer Wert (Integer) sein sollte, da Sie versuchen, `points` zu `totalpoints` hinzuzufügen.

Ändern Sie zum Beheben des Fehlers den `points`-Member der `User`-Klasse von:

```csharp
[DataMember]
internal string points;
```

in:

```csharp
[DataMember]
internal int points;
```

Die roten Wellenlinien im Code-Editor verschwinden.

Zeigen Sie dann auf die grüne Wellenlinie in der Deklaration des `points`-Datenmembers. Das Codeanalysetool zeigt Ihnen an, dass der Variablen nie ein Wert zugewiesen wird.

![Warnmeldung für nicht zugewiesene Variable](../debugger/media/write-better-code-warning-message.png)

In der Regel ist dies ein Problem, das behoben werden muss. Allerdings speichern Sie in der Beispiel-App während des Deserialisierungsprozesses tatsächlich Daten in der `points`-Variable und fügen diesen Wert dann dem `totalpoints`-Datenmember hinzu. In diesem Beispiel kennen Sie die Absicht des Codes und können die Warnung gefahrlos ignorieren. Wenn Sie die Warnung jedoch vermeiden möchten, können Sie den folgenden Code ersetzen:

```csharp
item.totalpoints = users[i].points;
```

durch diesen:

```csharp
item.points = users[i].points;
item.totalpoints += users[i].points;
```

Die grüne Wellenlinie verschwindet.

## <a name="fix-an-exception"></a>Beseitigen einer Ausnahme

Wenn Sie alle roten Wellenlinien behoben und korrigiert oder zumindest alle grünen Wellenlinien untersucht haben, können Sie den Debugger starten und die App ausführen.

Drücken Sie **F5** (**Debuggen > Debuggen starten**), oder klicken Sie auf der Symbolleiste „Debuggen“ auf die Schaltfläche **Debuggen starten** ![Debuggen starten](../debugger/media/dbg-tour-start-debugging.png "Debugging starten").

An diesem Punkt löst die Beispiel-App eine `SerializationException`-Ausnahme aus (ein Laufzeitfehler). Das heißt, die App wählt die Daten aus, die Sie serialisieren möchten. Da Sie die App im Debugmodus (Debugger angefügt) gestartet haben, führt Sie die Ausnahmen-Hilfe des Debuggers direkt zu dem Code, der die Ausnahme ausgelöst hat, und gibt Ihnen eine hilfreiche Fehlermeldung.

![SerializationException tritt auf](../debugger/media/write-better-code-serialization-exception.png)

Die Fehlermeldung weist Sie darauf hin, dass der Wert `4o` nicht als ganze Zahl analysiert werden kann. Sie wissen, dass die Daten in diesem Beispiel schlecht sind: `4o` sollte `40` sein. Was tun Sie aber damit, wenn Sie in einem realen Szenario nicht die Kontrolle über die Daten haben (wenn Sie diese beispielsweise von einem Webdienst erhalten)? Wie lösen Sie dieses Problem?

Wenn eine Ausnahme auftritt, müssen Sie eine Reihe von Fragen stellen (und beantworten):

* Handelt es sich bei dieser Ausnahme um einen Fehler, den Sie beheben können? Oder:

* Tritt die Ausnahme auch bei Ihren Benutzern auf?

Ist ersteres der Fall, beheben Sie den Fehler. (In der Beispiel-App bedeutet dies, dass die fehlerhaften Daten korrigiert werden.) Wenn zweiteres der Fall ist, müssen Sie möglicherweise die Ausnahme in Ihrem Code mit einem `try/catch`-Block behandeln (im nächsten Abschnitt sehen wir uns andere mögliche Strategien an). Ersetzen Sie in der Beispiel-App folgenden Code:

```csharp
users = ser.ReadObject(ms) as User[];
```

durch den folgenden:

```csharp
try
{
    users = ser.ReadObject(ms) as User[];
}
catch (SerializationException)
{
    Console.WriteLine("Give user some info or instructions, if necessary");
    // Take appropriate action for your app
}
```

Ein `try/catch`-Block hat einige Leistungseinbußen zur Folge, sodass Sie ihn nur verwenden sollten, wenn Sie ihn wirklich benötigen. Dies ist der Fall, wenn (a) sie in der Releaseversion der App vorkommen und (b) die Dokumentation für die Methode anzeigt, dass Sie die Ausnahme überprüfen sollten (vorausgesetzt die Dokumentation ist vollständig). In vielen Fällen können Sie eine Ausnahme ordnungsgemäß behandeln, und der Benutzer bekommt davon nichts mit.

Im Folgenden finden Sie einige wichtige Tipps für die Behandlung von Ausnahmen:

* Vermeiden Sie die Verwendung eines leeren catch-Blocks (z. B. `catch (Exception) {}`), der keine geeignete Aktion zum Aufdecken oder Behandeln eines Fehlers ausführt. Ein leerer oder nicht informativer catch-Block kann Ausnahmen ausblenden und das Debuggen des Codes erschweren anstatt zu erleichtern.

* Verwenden Sie den `try/catch`-Block für die bestimmte Funktion, die die Ausnahme auslöst (`ReadObject` in der Beispiel-App). Wenn Sie ihn für einen größeren Codeblock verwenden, blenden Sie die Position des Fehlers aus. Verwenden Sie beispielsweise den `try/catch`-Block nicht für den Aufruf der hier gezeigten übergeordneten Funktion `ReadToObject`, da Sie sonst nicht genau wissen, wo die Ausnahme aufgetreten ist.

    ```csharp
    // Don't do this
    try
    {
        User[] users = ReadToObject(data);
    }
    catch (SerializationException)
    {
    }
    ```

* Überprüfen Sie für unbekannte Funktionen, die Sie in Ihre App einschließen, und insbesondere für die Interaktion mit externen Daten (wie z. B. eine Webanforderung), die Dokumentation, um zu sehen, welche Ausnahmen die Funktion wahrscheinlich auslöst. Dies können wichtige Informationen für die ordnungsgemäße Fehlerbehandlung und das Debuggen Ihrer App sein.

Korrigieren Sie für die Beispiel-App `SerializationException` in der `GetJsonData`-Methode, indem Sie `4o` in `40`ändern.

## <a name="clarify-your-code-intent-by-using-assert"></a>Verdeutlichen der Absicht von Code mithilfe von Assert

Klicken Sie auf der Symbolleiste „Debuggen“ auf die Schaltfläche **Neu starten** ![App neu starten](../debugger/media/dbg-tour-restart.png "RestartApp") (**STRG** + **UMSCHALT** + **F5**). Dadurch wird die App in weniger Schritten neu gestartet. Im Konsolenfenster wird die folgende Aus angezeigt:

![NULL-Wert in der Ausgabe](../debugger/media/write-better-code-using-assert-null-output.png)

Sie sehen in dieser Ausgabe etwas, das nicht ganz richtig ist. **name** und **lastname** für den dritten Datensatz sind leer.

Dies ist ein guter Zeitpunkt, um über einen nicht allzu häufig verwendeten aber dennoch hilfreichen Programmierstil zu sprechen: die Verwendung von `assert`-Anweisungen in Ihren Funktionen. Durch Hinzufügen des folgenden Codes schließen Sie eine Laufzeitüberprüfung ein, um sicherzustellen, dass `firstname` und `lastname` nicht `null` entsprechen. Ersetzen Sie den folgenden Code in der `UpdateRecords`-Methode:

```csharp
if (existingUser == false)
{
    User user = new User();
    user.firstname = users[i].firstname;
    user.lastname = users[i].lastname;
```

durch diesen:

```csharp
// Also, add a using statement for System.Diagnostics at the start of the file.
Debug.Assert(users[i].firstname != null);
Debug.Assert(users[i].lastname != null);
if (existingUser == false)
{
    User user = new User();
    user.firstname = users[i].firstname;
    user.lastname = users[i].lastname;
```

Wenn Sie den Funktionen während des Entwicklungsprozesses `assert`-Anweisungen wie diese hinzufügen, können Sie die Absicht Ihres Codes angeben. Im vorherigen Beispiel geben wir Folgendes an:

* Für den Vornamen ist eine gültige Zeichenfolge erforderlich.
* Für den Nachnamen ist eine gültige Zeichenfolge erforderlich.

Durch die Angabe der Absicht auf diese Weise erfüllen Sie Ihre Anforderungen. Dies ist eine einfache und praktische Methode, die Sie verwenden können, um während der Entwicklung Fehler zu beheben. (`assert`-Anweisungen werden auch als Hauptelement in Komponententests verwendet.)

Klicken Sie auf der Symbolleiste „Debuggen“ auf die Schaltfläche **Neu starten** ![App neu starten](../debugger/media/dbg-tour-restart.png "RestartApp") (**STRG** + **UMSCHALT** + **F5**).

> [!NOTE]
> Der `assert`-Code ist nur in einem Debugbuild aktiv.

Wenn Sie neu starten, hält der Debugger an der `assert`-Anweisung an, da der Ausdruck `users[i].firstname != null` als `false` anstelle von `true` ausgewertet wird.

![Für Assert wird „false“ ausgegeben](../debugger/media/write-better-code-using-assert.png)

Der `assert`-Fehler weist darauf hin, dass ein Problem vorliegt, das Sie untersuchen müssen. `assert` kann viele Szenarios abdecken, in denen nicht notwendigerweise eine Ausnahme auftritt. In diesem Beispiel wird dem Benutzer keine Ausnahme angezeigt, und ein `null`-Wert wird als `firstname` in der Liste der Datensätze hinzugefügt. Dies kann später zu Problemen führen (siehe Konsolenausgabe) und das Debuggen möglicherweise erschweren.

> [!NOTE]
> In Szenarios, in denen eine Methode für den `null`-Wert aufgerufen wird, wird `NullReferenceException` ausgegeben. Normalerweise möchten Sie die Verwendung eines `try/catch`-Blocks für eine allgemeine Ausnahme vermeiden (d. h. eine Ausnahme, die nicht an die jeweilige Bibliotheksfunktion gebunden ist). Jedes Objekt kann `NullReferenceException` auslösen. Lesen Sie die Dokumentation für die Bibliotheksfunktion, wenn Sie sich nicht sicher sind.

Während des Debuggens ist es ratsam, eine bestimmte `assert`-Anweisung beizubehalten, bis Sie wissen, dass Sie diese durch eine tatsächliche Codekorrektur ersetzen müssen. Nehmen wir an, Sie entscheiden sich dazu, dass die Ausnahme für den Benutzer in einem Releasebuild der App auftritt. In diesem Fall müssen Sie Code umgestalten, um sicherzustellen, dass Ihre App keine schwerwiegende Ausnahme auslöst oder zu einem anderen Fehler führt. Ersetzen Sie den folgenden Code, um diesen Code zu korrigieren:

```csharp
if (existingUser == false)
{
    User user = new User();
```

durch den folgenden:

```csharp
if (existingUser == false && users[i].firstname != null && users[i].lastname != null)
{
    User user = new User();
```

Wenn Sie diesen Code verwenden, erfüllen Sie die Codeanforderungen und stellen sicher, dass den Daten kein Datensatz mit `null` für die Werte `firstname` und `lastname` hinzugefügt wird.

In diesem Beispiel haben wir die beiden `assert`-Anweisungen in einer Schleife hinzugefügt. Wenn Sie `assert` verwenden, sollten Sie in der Regel `assert`-Anweisungen am Einstiegspunkt (Anfang) einer Funktion oder Methode hinzufügen. Sie sehen sich derzeit die `UpdateRecords`-Methode in der Beispiel-App an. Sie wissen, dass bei dieser Methode Probleme auftreten, wenn eines der Methodenargumente `null` ist. Überprüfen Sie daher beide mit einer `assert`-Anweisung am Einstiegspunkt der Funktion.

```csharp
public static void UpdateRecords(List<User> db, User[] users)
{
    Debug.Assert(db != null);
    Debug.Assert(users != null);
```

Bei den vorangehenden Anweisungen haben Sie die Absicht, vorhandene Daten (`db`) zu laden und neue Daten (`users`) abzurufen, bevor Sie etwas aktualisieren.

Sie können `assert` mit allen Arten von Ausdrücken verwenden, für die `true` oder `false` ausgegeben wird. Sie können z. B. eine `assert`-Anweisung wie die folgende hinzufügen.

```csharp
Debug.Assert(users[0].points > 0);
```

Der vorangehende Code ist nützlich, wenn Sie die folgende Absicht angeben möchten: Es ist ein neuer Punktwert erforderlich, der größer als Null (0) ist, um den Datensatz des Benutzers zu aktualisieren.

## <a name="inspect-your-code-in-the-debugger"></a>Überprüfen des Codes im Debugger

Da Sie nun alle wesentlichen Probleme in Zusammenhang mit Ihrer Beispiel-App behoben haben, können Sie sich auf andere Dinge konzentrieren.

Wir haben Ihnen die Ausnahme-Hilfe des Debuggers gezeigt, aber der Debugger ist ein viel leistungsfähigeres Tool, das Sie auch für andere Aufgaben wie das zeilenweise Durchgehen von Code und das Überprüfen von Variablen verwenden können. Die leistungsfähigeren Funktionen sind besonders in den folgenden Szenarios nützlich:

* Sie versuchen, einen Laufzeitfehler im Code zu isolieren, können dies jedoch nicht mithilfe der zuvor beschriebenen Methoden und Tools machen.

* Sie möchten den Code während der Ausführung überprüfen, um sicherzustellen, dass er sich erwartungsgemäß verhält.

    Es ist aufschlussreich, den Code während der Ausführung zu überwachen. Sie können auf diese Weise mehr über Ihren Code erfahren und häufig Fehler identifizieren, bevor diese offensichtliche Symptome manifestieren.

Informationen zur Verwendung der wesentlichen Features des Debuggers finden Sie unter [Debuggen für Einsteiger](../debugger/debugging-absolute-beginners.md).

## <a name="fix-performance-issues"></a>Beheben der Leistungsprobleme

Zu Fehlern einer anderen Art gehört ineffizienter Code, der bewirkt, dass Ihre App langsam ausgeführt wird oder zu viel Speicherplatz beansprucht. Im Allgemeinen ist die Optimierung der Leistung etwas, das Sie später in der App-Entwicklung angehen. Leistungsprobleme können jedoch frühzeitig auftreten (z. B. wenn Sie erkennen, dass ein Teil Ihrer App langsam läuft), und Sie müssen Ihre App möglicherweise frühzeitig mit den Profilerstellungstools testen. Weitere Informationen über Profilerstellungstools wie das CPU-Auslastungstool und des Arbeitsspeicheranalyzer finden Sie in der [Einführung in Profilerstellungstools](../profiling/profiling-feature-tour.md).

## <a name="next-steps"></a>Nächste Schritte

In diesem Artikel haben Sie gelernt, wie Sie viele gängige Fehler in Ihrem Code vermeiden und beheben können, und wann der Debugger verwendet werden soll. Als nächstes erfahren Sie mehr über die Verwendung des Visual Studio-Debuggers zum Beheben von Fehlern.

> [!div class="nextstepaction"]
> [Debuggen für Einsteiger](../debugger/debugging-absolute-beginners.md)
