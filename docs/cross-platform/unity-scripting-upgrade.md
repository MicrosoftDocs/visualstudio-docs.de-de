---
title: Verwenden von .NET 4.x in Unity
description: Hier erfahren Sie, wie Sie .NET 4.x in Unity verwenden. Aktivieren Sie die .NET 4.x-Skripterstellungsruntime. Nutzen Sie die .NET-Kompatibilität. Überprüfen Sie neue Syntax- und Sprachenfeatures.
author: therealjohn
ms.author: johmil
ms.date: 08/29/2018
ms.topic: how-to
ms.assetid: E2C9420F-A5D5-4472-9020-2B63FB27A133
ms.technology: vs-unity-tools
ms.workload:
- unity
ms.openlocfilehash: 06efbe9d346cbbe8b9e81d95be257742b659cf8f
ms.sourcegitcommit: 01c1b040b12d9d43e3e8ccadee20d6282154faad
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/14/2020
ms.locfileid: "92039845"
---
# <a name="using-net-4x-in-unity"></a>Verwenden von .NET 4.x in Unity

Die der Unity-Skripterstellung zugrunde liegenden Technologien C# und .NET wurden seit der Veröffentlichung durch Microsoft im Jahr 2002 fortlaufend aktualisiert. Viele Unity-Entwickler sind sich jedoch nicht bewusst, dass die C#-Sprache und das .NET Framework ständig mit neuen Features erweitert werden. Das liegt daran, dass für Unity vor Unity 2017.1 eine .NET 3.5 entsprechende Skriptlaufzeit verwendet wurde, für die es jahrelang keine Updates gab.

Mit dem Release von Unity 2017.1 stellte Unity eine experimentelle Version der Skriptlaufzeit vor, für die ein Upgrade durchgeführt wurde, dass sie mit der C#-Version 6 für .NET 4.6 kompatibel ist. In Unity 2018.1 wird die .NET 4.x entsprechende Laufzeit nicht mehr als experimentell angesehen, während die ältere .NET 3.5 entsprechende Laufzeit nun als veraltete Version betrachtet wird. Zudem ist mit dem Release von Unity 2018.3 geplant, die aktualisierte Skriptlaufzeit zur Standardauswahl zu machen und sogar ein weiteres Update auf C#-Version 7 zu ermöglichen. Weitere Informationen und die neuesten Updates zu dieser Roadmap finden Sie im [Blogbeitrag](https://blogs.unity3d.com/2018/07/11/scripting-runtime-improvements-in-unity-2018-2/) von Unity oder im [Forum für Vorschauversionen zu experimentellen Skripts](https://forum.unity.com/forums/experimental-scripting-previews.107/). In der Zwischenzeit lesen Sie die folgenden Abschnitte, um mehr über die neuen Features zu erfahren, die ab sofort mit der .NET 4.x-Skriptlaufzeit verfügbar sind.

## <a name="prerequisites"></a>Voraussetzungen

* [Unity 2017.1 oder höher](https://unity3d.com/) (2018.2 empfohlen)
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)

## <a name="enabling-the-net-4x-scripting-runtime-in-unity"></a>Aktivieren der .NET 4.x-Skriptlaufzeit in Unity

Um die .NET 4.x-Skriptlaufzeit zu aktivieren, führen Sie die folgenden Schritte aus:

1. Öffnen Sie „PlayerSettings“ im Unity Inspector, indem Sie **Edit > Project Settings > Player** (Bearbeiten > Projekteinstellungen > Player) auswählen.

1. Klicken Sie unter der Überschrift **Configuration** (Konfiguration) auf die Dropdownliste **Scripting Runtime Version** (Version der Skriptlaufzeit), und wählen Sie **.NET 4.x Equivalent** (.NET 4.x-Entsprechung) aus. Sie werden aufgefordert, Unity neu zu starten.

![Auswahl der .NET 4.x-Entsprechung](media/vstu_scripting-runtime-version.png)

## <a name="choosing-between-net-4x-and-net-standard-20-profiles"></a>Auswahl zwischen .NET 4.x- und .NET Standard 2.0-Profilen

Nachdem Sie zur .NET 4.x entsprechenden Skriptlaufzeit gewechselt haben, können Sie den **Api Compatibility Level** (API-Kompatibilitätsgrad) in den PlayerSettings über das Dropdownmenü ( **Edit > Project Settings > Player** (Bearbeiten > Projekteinstellungen > Player)) festlegen. Es gibt zwei Optionen:

* **.NET Standard 2.0** . Dieses Profil entspricht dem von der .NET Foundation veröffentlichten [.NET Standard 2.0-Profil](https://github.com/dotnet/standard/blob/master/docs/versions/netstandard2.0.md). Für neue Projekte empfiehlt Unity die Verwendung von .NET Standard 2.0. Das Profil hat einen kleineren Umfang als .NET 4.x, was für Plattformen mit Größenbeschränkungen von Vorteil ist. Darüber hinaus hat sich Unity verpflichtet, dieses Profil auf allen von Unity unterstützten Plattformen zu unterstützen.

* **.NET 4.x** . Dieses Profil bietet Zugriff auf die neueste .NET 4-API. Es enthält den gesamten Code, der in den .NET Framework-Klassenbibliotheken verfügbar ist, und unterstützt zudem .NET Standard 2.0-Profile. Verwenden Sie das .NET 4.x-Profil, wenn es für Ihr Projekt erforderlich ist, dass ein Teil der API nicht im .NET Standard 2.0-Profil enthalten ist. Es kann jedoch sein, dass einige Teile dieser API nicht auf allen Plattformen von Unity unterstützt werden.

Weitere Informationen zu diesen Optionen finden Sie im [Blogbeitrag](https://blogs.unity3d.com/2018/03/28/updated-scripting-runtime-in-unity-2018-1-what-does-the-future-hold/) von Unity.

### <a name="adding-assembly-references-when-using-the-net-4x-api-compatibility-level"></a>Hinzufügen von Assemblyverweisen bei Verwendung des .NET 4.x-API-Kompatibilitätsgrads

Wenn Sie in der Dropdownliste **Api Compatibility Level** (API-Kompatibilitätsgrad) die .NET Standard 2.0-Einstellung auswählen, werden alle Assemblys im API-Profil referenziert und können verwendet werden. Wenn Sie jedoch das größere .NET 4.x-Profil verwenden, werden einige der von Unity mitgelieferten Assemblys standardmäßig nicht referenziert. Um diese APIs zu verwenden, müssen Sie manuell einen Assemblyverweis hinzufügen. Sie können die von Unity bereitgestellten Assemblys im Verzeichnis **MonoBleedingEdge/lib/mono** Ihrer Unity-Editor-Installation anzeigen:

![Verzeichnis „MonoBleedingEdge“](media/vstu_monobleedingedge.png)

Wenn Sie beispielsweise das .NET 4.x-Profil nutzen und `HttpClient` verwenden möchten, müssen Sie für System.Net.Http.dll einen Assemblyverweis hinzufügen. Andernfalls wird der Compiler eine Meldung ausgeben, dass ein Assemblyverweis fehlt:

![Hinweis auf fehlenden Assemblyverweis](media/vstu_missing-reference.png)

Jedes Mal, wenn Sie Unity-Projekte öffnen, werden in Visual Studio .csproj- und .sln-Dateien generiert. Folglich können Sie Assemblyverweise nicht direkt in Visual Studio hinzufügen, da sie beim erneuten Öffnen des Projekts verloren gehen. Stattdessen muss eine spezielle Textdatei namens **mcs.rsp** verwendet werden:

1. Erstellen Sie im Stammverzeichnis **Assets** Ihres Unity-Projekts eine neue Textdatei namens **mcs.rsp** .

1. Geben Sie in der ersten Zeile der leeren Textdatei Folgendes ein: `-r:System.Net.Http.dll`. Speichern Sie anschließend die Datei. Sie können „System.Net.Http.dll“ durch jede enthaltene Assembly ersetzen, der möglicherweise ein Verweis fehlt.

1. Starten Sie den Unity-Editor neu.

## <a name="taking-advantage-of-net-compatibility"></a>Vorteile der .NET-Kompatibilität

Zusätzlich zu den neuen C#-Syntax- und Sprachfunktionen bietet die .NET 4.x-Skriptlaufzeit Unity-Benutzern Zugriff auf eine sehr umfangreiche Bibliothek von .NET-Paketen, die mit der veralteten .NET 3.5-Skriptlaufzeit nicht kompatibel sind.

### <a name="add-packages-from-nuget-to-a-unity-project"></a>Hinzufügen von Paketen aus NuGet zu einem Unity-Projekt

[NuGet](https://www.nuget.org/) ist der Paket-Manager für .NET. NuGet ist in Visual Studio integriert. Unity-Projekte erfordern jedoch einen speziellen Prozess, um NuGet-Pakete hinzuzufügen. Dies liegt daran, dass beim Öffnen eines Projekts in Unity seine Visual Studio-Projektdateien neu generiert werden, wobei notwendige Konfigurationen rückgängig gemacht werden. Um ein Paket aus NuGet zu Ihrem Unity-Projekt hinzuzufügen, gehen Sie wie folgt vor:

1. Durchsuchen Sie NuGet nach einem kompatiblen Paket, das Sie hinzufügen möchten (.NET Standard 2.0 oder .NET 4.x). Dieses Beispiel zeigt das Hinzufügen von [Json.NET](https://www.nuget.org/packages/Newtonsoft.Json/), einem beliebten Paket für die Arbeit mit JSON, zu einem .NET Standard 2.0-Projekt.

1. Klicken Sie auf die Schaltfläche **Herunterladen** :

    ![Schaltfläche zum Herunterladen](media/vstu_nuget-download.png)

1. Suchen Sie die heruntergeladene Datei, und ändern Sie die Erweiterung von **.nupkg** in **.zip** .

1. Navigieren Sie innerhalb der ZIP-Datei zum Verzeichnis **lib/netstandard2.0** , und kopieren Sie die Datei **Newtonsoft.Json.dll** .

1. Erstellen Sie im Stammordner **Assets** Ihres Unity-Projekts einen neuen Ordner mit dem Namen **Plugins** . In Unity ist „Plugins“ ein spezieller Ordnername. Weitere Informationen finden Sie in der [Unity-Dokumentation](https://docs.unity3d.com/Manual/Plugins.html).

1. Fügen Sie die Datei **Newtonsoft.Json.dll** in das Verzeichnis **Plugins** Ihres Unity-Projekts ein.

1. Erstellen Sie im Verzeichnis **Assets** Ihres Unity-Projekts eine Datei namens **link.xml** , und fügen Sie folgenden XML-Code hinzu.  Dadurch wird sichergestellt, dass der Unity-Prozess zum Entfernen von Bytecode beim Export auf eine IL2CPP-Plattform nicht die benötigten Daten entfernt.  Obwohl dieser Schritt nur für diese Bibliothek gilt, können auch Probleme mit anderen Bibliotheken auftreten, die auf ähnliche Weise eine Reflektion verwenden.  Weitere Informationen finden Sie in den [Unity-Dokumenten](https://docs.unity3d.com/Manual/IL2CPP-BytecodeStripping.html) zu diesem Thema.

    ```xml
    <linker>
      <assembly fullname="System.Core">
        <type fullname="System.Linq.Expressions.Interpreter.LightLambda" preserve="all" />
      </assembly>
    </linker>
    ```

Nachdem alles vorbereitet ist, können Sie nun das Json.NET-Paket verwenden.

```csharp
using Newtonsoft.Json;
using UnityEngine;

public class JSONTest : MonoBehaviour
{
    class Enemy
    {
        public string Name { get; set; }
        public int AttackDamage { get; set; }
        public int MaxHealth { get; set; }
    }
    private void Start()
    {
        string json = @"{
            'Name': 'Ninja',
            'AttackDamage': '40'
            }";

        var enemy = JsonConvert.DeserializeObject<Enemy>(json);

        Debug.Log($"{enemy.Name} deals {enemy.AttackDamage} damage.");
        // Output:
        // Ninja deals 40 damage.
    }
}
```

Dies ist ein einfaches Beispiel für die Verwendung einer Bibliothek, die keine Abhängigkeiten aufweist. Wenn NuGet-Pakete auf andere NuGet-Pakete angewiesen sind, müssen Sie diese Abhängigkeiten manuell herunterladen und auf die gleiche Weise dem Projekt hinzufügen.

## <a name="new-syntax-and-language-features"></a>Neue Syntax- und Sprachfunktionen

Die Verwendung der aktualisierten Skriptlaufzeit gibt Unity-Entwicklern Zugriff auf C# 6 und eine Vielzahl neuer Sprachfunktionen und Syntaxelemente.

### <a name="auto-property-initializers"></a>Auto-Eigenschaft-Initialisierer

In der .NET 3.5-Skriptlaufzeit von Unity ist es mit der Auto-Eigenschaft-Syntax einfach, schnell nicht initialisierte Eigenschaften zu definieren. Dabei erfolgt die Initialisierung jedoch an anderer Stelle in Ihrem Skript. Mit der .NET 4.x-Laufzeit ist es nun möglich, Auto-Eigenschaften in derselben Zeile zu initialisieren:

```csharp
// .NET 3.5
public int Health { get; set; } // Health has to be initialized somewhere else, like Start()

// .NET 4.x
public int Health { get; set; } = 100;
```

### <a name="string-interpolation"></a>Zeichenfolgeninterpolierung

Mit der älteren .NET 3.5-Laufzeit erforderte die Zeichenfolgenverkettung eine umständliche Syntax. Jetzt mit der .NET 4.x-Laufzeit lassen sich dank des Features für die [`$`-Zeichenfolgeninterpolation](/dotnet/csharp/language-reference/tokens/interpolated) Ausdrücke in Zeichenfolgen in einer direkteren und besser lesbaren Syntax einfügen:

```csharp
// .NET 3.5
Debug.Log(String.Format("Player health: {0}", Health)); // or
Debug.Log("Player health: " + Health);

// .NET 4.x
Debug.Log($"Player health: {Health}");
```

### <a name="expression-bodied-members"></a>Ausdruckskörpermember

Mit der neueren C#-Syntax, die in der .NET 4.x-Laufzeit verfügbar ist, können [lambda](/dotnet/csharp/programming-guide/statements-expressions-operators/lambda-expressions)-Ausdrücke den Funktionskörper ersetzen, um ihn prägnanter zu gestalten:

```csharp
// .NET 3.5
private int TakeDamage(int amount)
{
    return Health -= amount;
}

// .NET 4.x
private int TakeDamage(int amount) => Health -= amount;
```

Sie können auch Ausdruckskörpermember in schreibgeschützten Eigenschaften verwenden:

```csharp
// .NET 4.x
public string PlayerHealthUiText => $"Player health: {Health}";
```

### <a name="task-based-asynchronous-pattern-tap"></a>Aufgabenbasiertes asynchrones Muster (TAP, Task-based Asynchronous Pattern)

Die [asynchrone Programmierung](/dotnet/csharp/async) erlaubt zeitaufwändige Vorgänge, ohne dass dadurch Ihre Anwendung nicht mehr reagiert. Zudem ermöglicht diese Funktionalität, dass auf das Ende zeitaufwendiger Vorgänge gewartet wird, bevor nachfolgender Code ausgeführt wird, der von den Ergebnissen dieser Vorgänge abhängt. Sie können beispielsweise warten, bis eine Datei geladen oder ein Netzwerkvorgang abgeschlossen ist.

In Unity wird die asynchrone Programmierung typischerweise mit [Coroutinen](https://docs.unity3d.com/Manual/Coroutines.html) durchgeführt. Seit C# 5 ist die bevorzugte Methode der asynchronen Programmierung in der .NET-Entwicklung jedoch das [Task-based Asynchronous Pattern (TAP)](/dotnet/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap), oder aufgabenbasiertes asynchrones Muster, das `async`- und `await`-Schlüsselwörter mit [System.Threading.Task](/dotnet/api/system.threading.tasks.task) verwendet. Kurz gesagt: In einer `async`-Funktion kann `await` genutzt werden, um auf die Fertigstellung eines Tasks zu warten, ohne dass der Rest Ihrer Anwendung an einer Aktualisierung gehindert wird:

```csharp
// Unity coroutine
using UnityEngine;
public class UnityCoroutineExample : MonoBehaviour
{
    private void Start()
    {
        StartCoroutine(WaitOneSecond());
        DoMoreStuff(); // This executes without waiting for WaitOneSecond
    }
    private IEnumerator WaitOneSecond()
    {
        yield return new WaitForSeconds(1.0f);
        Debug.Log("Finished waiting.");
    }
}
```

```csharp
// .NET 4.x async-await
using UnityEngine;
using System.Threading.Tasks;
public class AsyncAwaitExample : MonoBehaviour
{
    private async void Start()
    {
        Debug.Log("Wait.");
        await WaitOneSecondAsync();
        DoMoreStuff(); // Will not execute until WaitOneSecond has completed
    }
    private async Task WaitOneSecondAsync()
    {
        await Task.Delay(TimeSpan.FromSeconds(1));
        Debug.Log("Finished waiting.");
    }
}
```

TAP ist ein komplexes Thema mit Unity-spezifischen Details, die Entwickler berücksichtigen sollten. Aus diesem Grund ist TAP kein universeller Ersatz für Coroutinen in Unity, aber es ist ein weiteres Werkzeug, das Entwickler nutzen können. Die Beschreibung aller Featuredetails würde den Rahmen dieses Artikels sprengen, daher sind nachfolgend lediglich einige allgemeinen Best Practices und Tipps aufgeführt.

#### <a name="getting-started-reference-for-tap-with-unity"></a>Erste Schritte mit TAP in Unity

Diese Tipps können Ihnen bei den ersten Schritten mit TAP in Unity helfen:

* Asynchrone Funktionen, auf die gewartet werden soll, sollten den Rückgabetyp [`Task`](/dotnet/api/system.threading.tasks.task) oder [`Task<TResult>`](/dotnet/api/system.threading.tasks.task-1) aufweisen.
* Asynchrone Funktionen, die einen Task zurückgeben, sollten das Suffix **„Async“** an ihren Namen angehängt haben. Das Suffix „Async“ weist darauf hin, dass auf eine Funktion immer gewartet werden sollte.
* Verwenden Sie den Rückgabetyp `async void` nur für Funktionen, die asynchrone Funktionen aus traditionellem synchronem Code auslösen. Solche Funktionen können selbst nicht erwartet werden und sollten das Suffix „Async“ nicht im Namen haben.
* Unity stellt mit UnitySynchronizationContext sicher, dass asynchrone Funktionen standardmäßig im Hauptthread ausgeführt werden. Auf die Unity-API kann außerhalb des Hauptthreads nicht zugegriffen werden.
* Mit Methoden wie [`Task.Run`](/dotnet/api/system.threading.tasks.task.run) und [`Task.ConfigureAwait(false)`](/dotnet/api/system.threading.tasks.task.configureawait) ist es möglich, Tasks in Hintergrundthreads auszuführen. Diese Technik ist nützlich, um teure Vorgänge vom Hauptthread zu verlagern, um so die Leistung zu verbessern. Die Verwendung von Hintergrundthreads kann jedoch zu Problemen führen, die schwer zu debuggen sind, wie z.B. [Racebedingungen](https://wikipedia.org/wiki/Race_condition).
* Auf die Unity-API kann außerhalb des Hauptthreads nicht zugegriffen werden.
* Tasks, die Threads verwenden, werden in Unity-WebGL-Builds nicht unterstützt.

#### <a name="differences-between-coroutines-and-tap"></a>Unterschiede zwischen Coroutinen und TAP

Es gibt einige wichtige Unterschiede zwischen Coroutinen und TAP bzw. dem Warten auf eine asynchrone Funktion:

* Coroutinen können keine Werte zurückgeben, `Task<TResult>` jedoch schon.
* Sie können ein `yield`-Element nicht in eine try-catch-Anweisung einfügen, was die Fehlerbehandlung bei Coroutinen erschwert. Eine try-catch-Anweisung funktioniert jedoch mit TAP.
* Die Coroutinefunktion von Unity ist nicht in Klassen verfügbar, die nicht aus MonoBehaviour abgeleitet sind. TAP eignet sich hervorragend für die asynchrone Programmierung in solchen Klassen.
* An dieser Stelle wird TAP von Unity nicht als umfassender Ersatz für Coroutinen empfohlen. Eine Profilerstellung ist der einzige Weg, um die spezifischen Ergebnisse eines Ansatzes im Vergleich zum anderen für ein bestimmtes Projekt zu ermitteln.

> [!NOTE]
> Durch Unity 2018.2 wird das Debuggen von asynchronen Methoden mit Haltepunkten noch nicht vollständig unterstützt; [diese Funktionalität wird jedoch in Unity 2018.3 erwartet](https://twitter.com/jbevain/status/900043560665235456).

### <a name="nameof-operator"></a>nameof-Operator

Der `nameof`-Operator ruft den Zeichenfolgenamen einer Variablen, eines Typs oder eines Members ab. Beispielsweise ist `nameof` bei Protokollierungsfehlern nützlich, oder um den Zeichenfolgenamen einer Enumeration abzurufen:

```csharp
// Get the string name of an enum:
enum Difficulty {Easy, Medium, Hard};
private void Start()
{
    Debug.Log(nameof(Difficulty.Easy));
    RecordHighScore("John");
    // Output:
    // Easy
    // playerName
}
// Validate parameter:
private void RecordHighScore(string playerName)
{
    Debug.Log(nameof(playerName));
    if (playerName == null) throw new ArgumentNullException(nameof(playerName));
}
```

### <a name="caller-info-attributes"></a>Aufruferinformationsattribute

[Aufruferinformationsattribute](/dotnet/csharp/programming-guide/concepts/caller-information) liefern Informationen über den Aufrufer einer Methode. Sie müssen für jeden Parameter, den Sie mit einem Aufruferinformationsattribut verwenden möchten, einen Standardwert angeben:

```csharp
private void Start ()
{
    ShowCallerInfo("Something happened.");
}
public void ShowCallerInfo(string message,
        [System.Runtime.CompilerServices.CallerMemberName] string memberName = "",
        [System.Runtime.CompilerServices.CallerFilePath] string sourceFilePath = "",
        [System.Runtime.CompilerServices.CallerLineNumber] int sourceLineNumber = 0)
{
    Debug.Log($"message: {message}");
    Debug.Log($"member name: {memberName}");
    Debug.Log($"source file path: {sourceFilePath}");
    Debug.Log($"source line number: {sourceLineNumber}");
}
// Output:
// Something happened
// member name: Start
// source file path: D:\Documents\unity-scripting-upgrade\Unity Project\Assets\CallerInfoTest.cs
// source line number: 10
```

### <a name="using-static"></a>using static-Anweisung

Mithilfe von [using static](/dotnet/csharp/language-reference/keywords/using-static)-Anweisungen können Sie statische Funktionen verwenden, ohne deren Klassennamen einzugeben. Durch using static-Anweisungen sparen Sie zudem Platz und Zeit, wenn Sie mehrere statische Funktionen derselben Klasse verwenden müssen:

```csharp
// .NET 3.5
using UnityEngine;
public class Example : MonoBehaviour
{
    private void Start ()
    {
        Debug.Log(Mathf.RoundToInt(Mathf.PI));
        // Output:
        // 3
    }
}
```

```csharp
// .NET 4.x
using UnityEngine;
using static UnityEngine.Mathf;
public class UsingStaticExample: MonoBehaviour
{
    private void Start ()
    {
        Debug.Log(RoundToInt(PI));
        // Output:
        // 3
    }
}
```

## <a name="il2cpp-considerations"></a>Überlegungen zu IL2CPP

Beim Export Ihres Spiels auf Plattformen wie iOS verwendet Unity seine IL2CPP-Engine, um IL- in C++-Code zu „transpilieren“, der dann mit dem nativen Compiler der Zielplattform kompiliert wird. In diesem Szenario gibt es mehrere .NET-Features, die nicht unterstützt werden, wie z.B. Teile einer Reflektion und die Verwendung des Schlüsselworts `dynamic`. Während sich die Verwendung dieser Features in Ihrem eigenen Code steuern lässt, können Sie auf Probleme mit DLLs und SDKs von Drittanbietern stoßen, die nicht mit Blick auf Unity und IL2CPP geschrieben wurden. Weitere Informationen zu diesem Thema finden Sie auf der Unity-Website in der Dokumentation zu [Einschränkungen bei der Skripterstellung](https://docs.unity3d.com/Manual/ScriptingRestrictions.html).

Darüber hinaus wird Unity versuchen, wie im obigen Beispiel zu Json.NET erwähnt, ungenutzten Code während des IL2CPP-Exportprozesses zu entfernen.  Dies ist zwar in der Regel kein Problem, aber bei Bibliotheken, die Reflektion verwenden, kann es vorkommen, dass zur Laufzeit aufgerufene Eigenschaften oder Methoden versehentlich entfernt werden, wenn diese zum Zeitpunkt des Exports nicht bestimmt werden konnten.  Um diese Probleme zu beheben, fügen Sie Ihrem Projekt eine Datei **link.xml** hinzu, die eine Liste von Assemblys und Namespaces enthält, die während des Prozesses nicht entfernt werden können.  Ausführliche Informationen finden Sie in der [Unity-Dokumentation zum Entfernen von Bytecode](https://docs.unity3d.com/Manual/IL2CPP-BytecodeStripping.html).

## <a name="net-4x-sample-unity-project"></a>Beispiel für .NET 4.x-Unity-Projekt

Dieser Beispielcode enthält Beispiele für verschiedene .NET 4.x-Features. Auf [GitHub](https://github.com/Microsoft/unity-scripting-upgrade) können Sie das Projekt herunterladen oder den Quellcode anzeigen.

## <a name="additional-resources"></a>Zusätzliche Ressourcen

* [Unity Blog - Scripting Runtime Improvements in Unity 2018.2](https://blogs.unity3d.com/2018/07/11/scripting-runtime-improvements-in-unity-2018-2/) (Unity-Blog: Verbesserungen der Skriptlaufzeit in Unity 2018.2)
* [Die Geschichte von C#](/dotnet/csharp/whats-new/csharp-version-history)
* [Neues in C# 6](/dotnet/csharp/whats-new/csharp-6)
* [Asynchronous programming in Unity, Using Coroutine and TAP](/archive/blogs/appconsult/unity-coroutine-tap-en-us) (Asynchrone Programmierung in Unity unter Verwendung von Coroutine und TAP)
* [Async-Await Instead of Coroutines in Unity 2017](http://www.stevevermeulen.com/index.php/2017/09/using-async-await-in-unity3d-2017/) (Warten auf asynchrone Funktionen anstelle von Coroutinen in Unity 2017)
* [Unity Forum - Experimental Scripting Previews](https://forum.unity.com/forums/experimental-scripting-previews.107/) (Unity-Forum: Vorschauversionen zu experimentellen Skripts)