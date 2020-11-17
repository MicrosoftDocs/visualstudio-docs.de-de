---
title: 'Tutorial: Überprüfung auf'
description: Dieser Artikel enthält eine ausführliche exemplarische Vorgehensweise zum Arbeiten mit Azure Functions in Visual Studio für Mac.
author: jmatthiesen
ms.author: jomatthi
ms.date: 11/06/2020
ms.technology: vs-ide-install
ms.assetid: 38FD2070-5151-482E-B0A9-993715128736
ms.topic: tutorial
ms.openlocfilehash: 3fa653a1acaae0f9b58d17f86d6e2e0feeb027a6
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493022"
---
# <a name="tutorial-getting-started-with-azure-functions"></a>Tutorial: Erste Schritte mit Azure Functions

In diesem Tutorial erfahren Sie mehr über die ersten Schritte beim Erstellen von Azure-Funktionen mithilfe von Visual Studio für Mac. Sie werden ebenfalls Azure-Speichertabellen integrieren, die eine von vielen Arten von Bindungen und Triggern darstellen, die Azure Functions-Entwicklern zur Verfügung stehen.

## <a name="objectives"></a>Ziele

> [!div class="checklist"]
> * Erstellen und Debuggen von lokalen Azure-Funktionen
> * Integrieren mit Webressourcen und Azure-Speicherressourcen
> * Orchestrieren eines Workflows mit mehreren Azure-Funktionen

## <a name="requirements"></a>Anforderungen

- Visual Studio für Mac 7.5 oder höher
- Ein Azure-Abonnement (kostenlos unter [https://azure.com/free](https://azure.com/free?ref=visualstudio) verfügbar)

## <a name="exercise-1-creating-an-azure-functions-project"></a>Übung 1: Erstellen eines Azure Functions-Projekts

1. Starten Sie **Visual Studio für Mac**.

2. Klicken Sie auf **Datei > Neue Projektmappe**.

3. Wählen Sie aus der Kategorie **Cloud > Allgemein** die Vorlage **Azure Functions** aus. Sie verwenden C#, um eine .NET-Klassenbibliothek zu erstellen, die Azure Functions hostet. Klicken Sie auf **Weiter**.

    ![Auswahl der Azure Functions-Vorlage](media/azure-functions-lab-image1.png)

4. Legen Sie den **Projektnamen** auf **"AzureFunctionsLab"** fest, und klicken Sie auf **Erstellen**.

    ![Benennen und Erstellen des Azure Functions-Projekts](media/azure-functions-lab-image2.png)

5. Erweitern Sie die Knoten im **Projektmappenfenster**. Die Standardvorlage für Projekte enthält NuGet-Verweise auf eine Vielzahl von Azure WebJobs-Paketen sowie das Paket „Newtonsoft.Json“.

     Es sind ebenfalls zwei Dateien enthalten: **host.json** für das Beschreiben von globalen Konfigurationsoptionen für den Host und **local.settings.json** für das Konfigurieren von Diensteinstellungen.
        Die Projektvorlage erstellt ebenfalls eine HttpTrigger-Standarddatei. Für dieses Tutorial sollten Sie die Datei **HttpTrigger.cs** aus dem Projekt löschen.

    Öffnen Sie **local.settings.json**. Diese Datei weist standardmäßig zwei leere Einstellungen für Verbindungszeichenfolgen auf.

    ![Projektmappenfenster, das die Datei „local.settings.json“ anzeigt](media/azure-functions-lab-image3.png)

## <a name="exercise-2-creating-an-azure-storage-account"></a>Übung 2: Erstellen eines Azure-Speicherkontos

1. Melden Sie sich unter [https://portal.azure.com](https://portal.azure.com) bei Ihrem Azure-Konto an.

1. Klicken Sie im Abschnitt **Favoriten** auf der linken Seite des Bildschirms auf **Speicherkonten**:

    ![Abschnitt „Favoriten“ des Azure-Portals, der die Elemente von Speicherkonten anzeigt](media/azure-functions-lab-image4.png)

1. Klicken Sie auf **Hinzufügen**, um ein neues Speicherkonto zu erstellen:

    ![Schaltfläche zum Hinzufügen eines neuen Speicherkontos](media/azure-functions-lab-image5.png)

1. Geben Sie einen global eindeutigen **Namen** ein, und verwenden Sie diesen für die **Ressourcengruppe** erneut. Für alle anderen Elemente können Sie die Standardeinstellungen beibehalten.

    ![Details zum neuen Speicherkonto](media/azure-functions-lab-image6.png)

1. Klicken Sie auf **Erstellen**. Es dauert möglicherweise einige Minuten, bis das Speicherkonto erstellt wurde. Sie erhalten eine Benachrichtigung, sobald es erfolgreich erstellt wurde.

    ![Benachrichtigung „Bereitstellung erfolgreich“](media/azure-functions-lab-image7.png)

1. Klicken Sie in der Benachrichtigung auf die Schaltfläche **Zu Ressource wechseln**.

1. Klicken Sie auf die Registerkarte **Zugriffsschlüssel**.

    ![Einstellung für Zugriffsschlüssel](media/azure-functions-lab-image8.png)

1. Kopieren Sie die erste **Verbindungszeichenfolge**. Diese Zeichenfolge wird verwendet, um den Azure-Speicher später in Azure-Funktionen zu integrieren.

    ![Informationen für Schlüssel 1](media/azure-functions-lab-image9.png)

1. Kehren Sie zu **Visual Studio für Mac** zurück, und fügen Sie die vollständige Verbindungszeichenfolge als Einstellung für **AzureWebJobsStorage** in der Datei **local.settings.json** ein. Sie können auf den Namen der Einstellungen nun in Attributen für Funktionen verweisen, die Zugriff auf diese Ressourcen benötigen.

    ![Lokale Einstellungsdatei mit eingegebenem Verbindungsschlüssel](media/azure-functions-lab-image10.png)

## <a name="example-3-creating-and-debugging-an-azure-function"></a>Beispiel 3: Erstellen und Debuggen von Azure-Funktionen

1. Sie können nun mit dem Hinzufügen von Code beginnen. Wenn Sie mit einer .NET-Klassenbibliothek arbeiten, werden Azure-Funktionen als statische Methoden hinzugefügt. Klicken Sie im **Projektmappenfenster** mit der rechten Maustaste auf den Projektknoten **AzureFunctions** und dann mit der linken auf **Hinzufügen > Funktion hinzufügen**:

    ![Option „Funktion hinzufügen“](media/azure-functions-lab-image11.png)

1. Wählen Sie im Dialogfeld „New Azure Functions“ (Neue Azure-Funktionen) die Vorlage für generische Webhooks aus. Legen Sie den **Namen** auf **Add** (Hinzufügen) fest, und klicken Sie auf **OK**, um Ihre Funktion zu erstellen:

    ![Dialogfeld „Neue Azure-Funktionen“](media/azure-functions-lab-image12.png)

1. Fügen Sie am Anfang der neuen Datei folgende **using**-Anweisungen hinzu:

    ```csharp
    using Microsoft.Azure.WebJobs.Extensions.Http;
    using System.Web;
    using Microsoft.WindowsAzure.Storage.Table;
    ```

1. Entfernen Sie die vorhandene `Run`-Methode, und fügen Sie folgende Methode als Azure-Funktion zur Klasse hinzu:

    ```csharp
    [FunctionName("Add")]
    public static int Run(
    [HttpTrigger(AuthorizationLevel.Function, "get", Route = null)]
    HttpRequestMessage req,
    TraceWriter log)
    {
        int x = 1;
        int y = 2;

        return x + y;
    }
    ```

1. Im Folgenden werden die einzelnen Schritte der Methodendefinition durchlaufen.

    Zunächst sehen Sie ein **FunctionName**-Attribut, das diese Methode als Azure-Funktion markiert. Dieses Attribut kennzeichnet den öffentlichen Namen der Funktion. Der Attributname muss nicht dem tatsächlichen Methodennamen entsprechen.

    ![Neue Run-Methode mit dem hervorgehobenen FunctionName-Attribut](media/azure-functions-lab-image13.png)

1. Anschließend wird die Methode als **public static**-Methode markiert. Dieser Schritt ist erforderlich. Sie werden feststellen, dass der Rückgabewert den Typ **int** aufweist. Sofern dies nicht durch Methodenattribute anders angegeben wurde, werden alle nicht leeren Rückgabewerte einer Azure-Funktion als Text an den Client zurückgegeben. Standardmäßig werden diese als **XML** zurückgegeben. Dies kann und wird im Verlauf dieses Tutorials jedoch in **JSON** geändert werden.

    ![Neue Run-Methode mit hervorgehobener Methodeninitialisierung](media/azure-functions-lab-image14.png)

1. Der erste Parameter ist mit dem Attribut **HttpTrigger** markiert, das angibt, dass die Methode über eine HTTP-Anforderung aufgerufen wird. Das Attribut gibt ebenfalls die Autorisierungsebene der Methode sowie die unterstützten Verben (in diesem Fall lediglich **"GET"** ) an. Sie können optional eine **Route** definieren, die den Pfad zur Methode überschreibt und automatisch Variablen aus dem Pfad extrahieren kann. Da der Wert der **Route** in diesem Fall NULL ist, wird der Pfad dieser Methode standardmäßig auf **/api/Add** festgelegt.

    ![Neue Run-Methode mit hervorgehobenem Parameter](media/azure-functions-lab-image15.png)

1. Der letzte Parameter der Methode ist **TraceWriter** und kann verwendet werden, um Diagnose- und Fehlermeldungen zu protokollieren.

    ![Neue Run-Methode mit hervorgehobenem TraceWriter-Parameter](media/azure-functions-lab-image16.png)

1. Legen Sie in der **return**-Zeile der Methode einen Breakpoint fest, indem Sie auf den Rand der Zeile klicken:

    ![In der return-Zeile festgelegter Breakpoint](media/azure-functions-lab-image17.png)

1. Erstellen Sie das Projekt, und führen Sie es in einer Debugsitzung aus, indem Sie **F5** drücken oder auf **Debuggen > Debuggen starten** klicken: Sie können alternativ auf die Schaltfläche **Ausführen** klicken. Diese Optionen führen die gleiche Aufgabe aus. Im restlichen Tutorial wird **F5** verwendet. Sie können jedoch die Methode verwenden, die Sie bevorzugen.

    ![Erstellen und Ausführen des Projekts](media/azure-functions-lab-image18.png)

1. Durch das Ausführen des Projekts wird automatisch die Terminal-Anwendung geöffnet.

1. Das Projekt durchläuft einen Prozess, in dem Azure-Funktionen basierend auf den Methodenattributen und einer Dateikonvention ermittelt werden, die im Verlauf dieses Artikels erläutert wird. In diesem Fall wird eine einzige Azure-Funktion erkannt und eine Auftragsfunktion generiert.

    ![Ausgabe der Azure-Funktion im Terminal](media/azure-functions-lab-image19.png)

1. Im unteren Bereich der Startmeldung gibt der Azure Functions-Host die URLs aller HTTP-Trigger-APIs aus. Dort sollte nur eine URL vorhanden sein. Kopieren Sie diese, und fügen Sie sie in eine neue Registerkarte Ihres Browsers ein.

    ![URL der Azure Functions-API](media/azure-functions-lab-image20.png)

1. Der Breakpoint sollte sofort ausgelöst werden. Die Webanforderungen wurde an die Funktion weitergeleitet und kann nun gedebuggt werden. Zeigen Sie mit der Maus auf die Variable **x**, um deren Wert anzuzeigen.

    ![Ausgelöster Breakpoint](media/azure-functions-lab-image21.png)

1. Entfernen Sie den Breakpoint mit der Methode, mit der Sie ihn zuvor hinzugefügt haben (klicken Sie auf den Rand, oder wählen Sie die Zeile aus, und drücken Sie **F9**).

1. Drücken Sie **F5**, um die Ausführung fortzusetzen.

1. Im Browser wird das XML-Ergebnis der Methode gerendert. Der hartcodierte Additionsvorgang erzeugt wie erwartet eine plausible Summe. Wenn in Safari nur „3“ angezeigt wird, navigieren Sie zu **Safari > Einstellungen > Erweitert**, und aktivieren Sie das Kontrollkästchen **Show Develop menu in menu bar** (Menü „Entwickeln“ in der Menüleiste anzeigen), um die Seite neu zu laden.

1. Klicken Sie in **Visual Studio für Mac** auf die Schaltfläche **Beenden**, um die Debugsitzung zu beenden. Denken Sie daran, die Debugsitzung neu zu starten, indem Sie diese beenden und erneut ausführen, um sicherzustellen, dass die Änderungen übernommen werden.

    ![Option „Debuggen beenden“](media/azure-functions-lab-image22.png)

1. Ersetzen Sie in der **Run**-Methode die Definitionen von **x** und **y** mit folgendem Code. Dieser Code extrahiert Werte aus der Abfragezeichenfolge der URL, sodass der Additionsvorgang auf den angegebenen Parametern basierend dynamisch ausgeführt werden kann.

    ```csharp
    var query = HttpUtility.ParseQueryString(req.RequestUri.Query);

    int x = int.Parse(query["x"]);

    int y = int.Parse(query["y"]);

    return x + y;
    ```

1. Führen Sie die Anwendung aus.

1. Kehren Sie in das Browserfenster zurück, und fügen Sie die Zeichenfolge `/?x=2&y=3` an die URL an. Die vollständige URL sollte nun `http://localhost:7071/api/Add?x=2&y=3` lauten. Navigieren Sie zur neuen URL.

1. Dieses Mal sollte das Ergebnis den neuen Parametern entsprechen. Sie können das Projekt mit unterschiedlichen Werten ausführen. Beachten Sie, dass keine Fehlerprüfung durchgeführt wird. Ungültige oder nicht vorhandene Parameter lösen also Fehler aus.

1. Beenden Sie die Debugsitzung.

## <a name="exercise-4-working-with-functionjson"></a>Übung 4: Arbeiten mit function.json

1. In einer vorherigen Übung wurde bereits erwähnt, dass Visual Studio für Mac eine Auftragsfunktion für die in der Bibliothek definierte Azure-Funktion generiert hat. Dies ist darin begründet, dass Azure Functions die Methodenattribute nicht zur Laufzeit verwendet, sondern eine Dateisystemkonvention zur Kompilierzeit, um zu konfigurieren, wo und wie Azure-Funktionen zur Verfügung gestellt werden. Klicken Sie im **Projektmappenfenster** mit der rechten Maustaste auf den Projektknoten und dann mit der linken auf **Im Finder anzeigen**.

     ![Option „Im Finder anzeigen“](media/azure-functions-lab-image23.png)

1. Navigieren Sie im Dateisystem nach unten, bis Sie **bin/Debug/netstandard2.0** erreichen. Dort sollte ein Ordner namens **Add** (Hinzufügen) vorhanden sein. Dieser Ordner wurde erstellt, um mit dem Namensattribut der Funktion im C#-Code zu kommunizieren. Erweitern Sie den Ordner „Add“, damit eine einzelne **function.json**-Datei angezeigt wird. Diese Datei wird von der Runtime verwendet, um die Azure-Funktion zu hosten und zu verwalten. Bei anderen Sprachmodellen ohne Unterstützung zur Kompilierzeit (z.B. C#-Skripts oder JavaScript) müssen diese Ordner manuell erstellt und verwaltet werden. Für C#-Entwickler werden diese beim Build automatisch durch die Metadaten der Attribute generiert. Klicken Sie mit der rechten Maustaste auf **function.json**, und öffnen Sie die Datei in Visual Studio.

    ![function.json im Dateiverzeichnis](media/azure-functions-lab-image24.png)

1. Durch die bisherigen Schritte dieses Tutorials sollten Sie nun ein grundlegendes Verständnis für C#-Attribute besitzen. Deshalb sollte Ihnen dieser JSON-Code bekannt vorkommen. Es gibt jedoch eine Elemente, die in den vorherigen Übungen nicht behandelt wurden. Für jede **Bindung** muss beispielsweise eine **Richtung** festgelegt werden. Daraus können Sie ableiten, dass es sich bei **"in"** um einen Eingabeparameter und bei **"out"** um einen Rückgabewert (über **$return**) oder um einen **out**-Parameter der Methode handelt. Sie müssen ebenfalls die **scriptFile**- (in Bezug auf den endgültigen Speicherort) und die **entryPoint**-Methode (public static) innerhalb der Assembly angeben. In den nächsten Schritten fügen Sie mithilfe dieses Modells einen benutzerdefinierten Funktionspfad hinzu, also kopieren Sie die Inhalte dieser Datei in die Zwischenablage.

    ![Geöffnete function.json-Datei in Visual Studio für Mac](media/azure-functions-lab-image25.png)

1. Klicken Sie im **Projektmappenfenster** mit der rechten Maustaste auf den Projektknoten **AzureFunctionsLab** und dann mit der linken auf **Hinzufügen > Neuer Ordner**. Nennen Sie diesen Ordner **Adder**. Der Name dieses Ordners definiert standardmäßig den Pfad zur API, z.B. **api/Adder**.

    ![Option „Neuer Ordner“](media/azure-functions-lab-image26.png)

1. Klicken Sie mit der rechten Maustaste auf den Ordner **Adder**, und wählen Sie **Hinzufügen > Neue Datei** aus.

    ![Option „Neue Datei“](media/azure-functions-lab-image27.png)

1. Wählen Sie die Kategorie **Web** und die Vorlage **Leere JSON-Datei** aus. Legen Sie den **Namen** auf **function** fest, und klicken Sie auf **Neu**.

    ![Option „Leere JSON-Datei“](media/azure-functions-lab-image28.png)

1. Fügen Sie die Inhalte der anderen **function.json**-Datei (aus Schritt 3) ein, um die Standardinhalte der neu erstellten Datei zu ersetzen.

1. Entfernen Sie am Anfang der JSON-Datei folgende Zeilen:

    ```json
    "configurationSource":"attributes",
    "generatedBy":"Microsoft.NET.Sdk.Functions-1.0.13",
    ```

1. Fügen Sie am Ende der ersten Bindung (nach der Zeile **"name": "req"** ) folgende Eigenschaften hinzu: Denken Sie daran, in der vorherigen Zeile ein Komma einzufügen. Diese Eigenschaft überschreibt das Standardstammverzeichnis, sodass nun **int**-Parameter aus dem Pfad extrahiert und in den Methodenparametern namens **x** und **y** platziert werden.

    ```json
    "direction": "in",
    "route": "Adder/{x:int?}/{y:int?}"
    ```

1. Fügen Sie unterhalb zunächst eine weitere Bindung hinzu. Diese Bindung verarbeitet den Rückgabewert der Funktion. Denken Sie daran, in der vorherigen Zeile ein Komma einzufügen.

    ```json
    {
    "name": "$return",
    "type": "http",
    "direction": "out"
    }
    ```

1. Aktualisieren Sie ebenfalls die Eigenschaft **entryPoint** am Ende der Datei, damit wie im Folgenden dargestellt eine Methode namens **"Add2"** verwendet wird. Dadurch soll veranschaulicht werden, dass der Pfad **api/Adder...** einer geeigneten Methode mit einem beliebigen Namen (in diesem Fall **Add2**) zugeordnet werden kann.

    ```json
    "entryPoint": "<project-name>.<function-class-name>.Add2"
    ```

1. Die fertige **function.json**-Datei sollte folgender JSON-Datei ähneln:

    ```json
    {
    "bindings": [
        {
        "type": "httpTrigger",
        "methods": [
            "get"
        ],
        "authLevel": "function",
        "direction": "in",
        "name": "req",
        "route": "Adder/{x:int?}/{y:int?}"
        },
        {
        "name": "$return",
        "type": "http",
        "direction": "out"
        }
    ],
    "disabled": false,
    "scriptFile": "../bin/AzureFunctionsProject.dll",
    "entryPoint": "AzureFunctionsProject.Add.Add2"
    }
    ```

1. Damit alles funktioniert, was Sie bisher erstellt haben, müssen Sie Visual Studio für Mac in einem letzten Schritt anweisen, diese Datei bei jeder Änderung in denselben relativen Pfad im Ausgabeverzeichnis zu kopieren. Wählen Sie die Datei aus, und klicken Sie auf die Registerkarte „Eigenschaften“ auf dem rechten Balken, und wählen Sie **Kopieren, wenn neuer** für **In Ausgabeverzeichnis kopieren** aus:

    ![Optionen für die JSON-Datei auf der Registerkarte „Eigenschaften“](media/azure-functions-lab-image30.png)

1. Ersetzen Sie in **Add.cs** die Methode `Run` (einschließlich des Attributs) durch folgende Methode, um die erwartete Funktion zu erfüllen. Diese ähnelt `Run`, verwendet jedoch keine Attribute und besitzt explizite Parameter für **x** und **y**.

    ```csharp
    public static int Add2(
        HttpRequestMessage req,
        int x,
        int y,
        TraceWriter log)
    {
        return x + y;
    }
    ```

1. Drücken Sie **F5**, um das Projekt zu erstellen und auszuführen.

1. Wenn der Build abgeschlossen ist und die Plattform gestartet wurde, wird nun angezeigt, dass eine zweite Route für Anforderungen verfügbar ist, die der neu hinzugefügten Methode zugeordnet ist:

    ![URL für HTTP-Funktionen](media/azure-functions-lab-image31.png)

1. Kehren Sie zum Browserfenster zurück, und navigieren Sie zu **http://localhost:7071/api/Adder/3/5** .

1. Auch dieses Mal funktioniert die Methode. Sie extrahiert Parameter aus dem Pfad und erzeugt eine Summe.

1. Kehren Sie zu **Visual Studio für Mac** zurück, und beenden Sie die Debugsitzung.

## <a name="exercise-5-working-with-azure-storage-tables"></a>Übung 5: Arbeiten mit Azure-Speichertabellen

Häufig ist der Dienst, den Sie erstellen, wesentlich komplexer als das, was in diesem Tutorial bisher erstellt wurde, und die Ausführung erfordert viel Zeit und/oder eine große Menge an Infrastruktur. In diesem Fall ist es effektiv, Anforderungen zu akzeptieren, die sich für die Verarbeitung in der Warteschlange befinden, wenn die Ressourcen verfügbar werden. Dies wird von Azure Functions unterstützt. In anderen Fällen sollten Sie Ihre Daten zentral speichern. Dies können Sie mit Azure Storage-Tabellen schnell erledigen.

1. Fügen Sie die untenstehende Klasse zu **Add.cs** hinzu. Sie sollte sich innerhalb des Namespaces, aber außerhalb der vorhandenen Klasse befinden.

    ```csharp
    public class TableRow : TableEntity
    {
        public int X { get; set; }
        public int Y { get; set; }
        public int Sum { get; set; }
    }
    ```

1. Fügen Sie innerhalb der **Add**-Klasse folgenden Code hinzu, um eine weitere Funktion einzuführen. Beachten Sie, dass diese bisher einzigartig ist, da keine HTTP-Antwort enthalten ist. Die letzte Zeile gibt ein neues **TableRow**-Element zurück, das mit einigen wichtigen Informationen (**PartitionKey** und **RowKey**) aufgefüllt wird, damit es und seine Parameter und Summen später leichter abgerufen werden können. Der Code innerhalb der Mode verwendet ebenfalls **TraceWriter**, damit einfacher nachzuvollziehen ist, wann Funktionen ausgeführt werden.

    ```csharp
    [FunctionName("Process")]
    [return: Table("Results")]
    public static TableRow Process(
        [HttpTrigger(AuthorizationLevel.Function, "get",
            Route = "Process/{x:int}/{y:int}")]
        HttpRequestMessage req,
        int x,
        int y,
        TraceWriter log)
    {
        log.Info($"Processing {x} + {y}");

        return new TableRow()
        {
            PartitionKey = "sums",
            RowKey = $"{x}_{y}",
            X = x,
            Y = y,
            Sum = x + y
        };
    }
    ```

1. Drücken Sie **F5**, um das Projekt zu erstellen und auszuführen.

1. Navigieren Sie in der Registerkarte des Browsers zu **http://localhost:7071/api/Process/4/6** . Dadurch wird eine weitere Meldung der Warteschlange hinzugefügt, die schließlich dazu führen soll, dass der Tabelle eine weitere Zeile hinzugefügt wird.

1. Kehren Sie zum **Terminal** zurück, und suchen Sie die eingehende Anforderung für **4 + 6**.

    ![Ausgabe des Terminals, die die Additionsanforderung anzeigt](media/azure-functions-lab-image32.png)

1. Kehren Sie zum Browser zurück, um die Anforderung erneut an dieselbe URL zu senden. Dieses Mal wird Ihnen nach der **Process**-Methode ein Fehler angezeigt. Das liegt daran, dass der Code versucht, eine Zeile mit einer bereits vorhandenen Kombination aus einer Partition und einem Zeilenschlüssel zur Azure Table Storage-Tabelle hinzuzufügen.

    ```
    System.Private.CoreLib: Exception while executing function: Process. Microsoft.Azure.WebJobs.Host: Error while handling parameter $return after function returned:. Microsoft.Azure.WebJobs.Host: The specified entity already exists.
    ```

1. Beenden Sie die Debugsitzung.

1. Fügen Sie folgenden Parameter direkt vor dem Parameter **TraceWriter** zur Methodendefinition hinzu, um den Fehler zu beheben. Dieser Parameter weist die Azure Functions-Plattform an, ein **TableRow**-Element aus der **Results**-Tabelle mit dem **PartitionKey** abzurufen, der bisher für das Speichern von Ergebnissen verwendet wurde. Sie werden feststellen, dass das **RowKey**-Element basierend auf den anderen **x**- und **y**-Parametern für dieselbe Methode dynamisch generiert wird. Wenn diese Zeile bereits vorhanden ist, kann **TableRow** diese am Anfang der Methode verwenden. Für den Entwickler fällt keine zusätzliche Arbeit an. Wenn die Zeile nicht vorhanden ist, ist der Wert NULL. Durch diese Effizienz können Entwickler sich auf die wichtige Geschäftslogik statt auf die Infrastruktur konzentrieren.

    ```csharp
    [Table("Results", "sums", "{x}_{y}")]
    TableRow tableRow,
    ```

1. Fügen Sie folgenden Code am Anfang der Methode hinzu. Wenn **TableRow** nicht NULL ist, ist das Ergebnis für den angeforderten Vorgang bereits vorhanden und kann sofort zurückgegeben werden. Andernfalls wird die Funktion wie bisher fortgesetzt. Dies ist zwar nicht die zuverlässigste Methode, um Daten zurückzugeben, aber sie veranschaulicht, dass Sie komplexe Vorgänge mit wenig Code auf mehreren skalierbaren Ebenen orchestrieren können.

    ```csharp
    if (tableRow != null)
    {
        log.Info($"{x} + {y} already exists");
        return null;
    }
    ```

1. Drücken Sie **F5**, um das Projekt zu erstellen und auszuführen.

1. Aktualisieren Sie in der Registerkarte des Browsers die URL unter **http://localhost:7071/api/Process/4/6** . Da die Tabellenzeile für diesen Datensatz vorhanden ist, sollte die Rückgabe sofort und ohne Fehler erfolgen. Da es keine HTTP-Ausgabe gibt, wird die Ausgabe im Terminal angezeigt.

    ![Terminal-Ausgabe, die die bereits vorhandene Tabellenzeile anzeigt](media/azure-functions-lab-image33.png)

1. Aktualisieren Sie die URL, damit diese eine bisher nicht getestete Kombination wie **http://localhost:7071/api/Process/5/7** enthält. Beachten Sie die Meldung im Terminal, die angibt, dass die Tabellenzeile (wie erwartet) nicht gefunden wurde.

    ![Ausgabe des Terminals, die den neuen Vorgang anzeigt](media/azure-functions-lab-image34.png)

1. Kehren Sie zu **Visual Studio für Mac** zurück, und beenden Sie die Debugsitzung.

<!--
1. Finally, let's take a look at what it's like to work with multiple input records. Rather than specify a specific **TableRow**, you can request an **IQueryable<TableRow>** using the same attributes, and the runtime will fill it with the appropriate resource you need. Add the code below to create a **List** function that lists all items that currently exist in the Azure table we've been working with. Also note that we're specifying that the MIME type of the response is **application/json**, so the runtime will automatically render as JSON.

    ```csharp
    [FunctionName("List")]
    public static HttpResponseMessage List(
        [HttpTrigger(AuthorizationLevel.Function, "get", Route = null)]
        HttpRequestMessage req,
        [Table("Results", "sums")]
        IQueryable<TableRow> table,
        TraceWriter log)
    {
        return req.CreateResponse(HttpStatusCode.OK, table, "application/json");
    }
    ```
1. Press **F5** to build and run the project.

1. In the browser tab, navigate to **http://localhost:7071/api/List**. This should pull down the list of all items in the Azure table and render it as JSON.

    ![](https://user-images.githubusercontent.com/3944468/29033725-be9d5a5e-7b4a-11e7-8b55-df0a200b6320.png)
-->

## <a name="summary"></a>Zusammenfassung

In diesem Tutorial haben Sie mehr über die ersten Schritte beim Erstellen von Azure Functions mithilfe von Visual Studio für Mac erfahren.
