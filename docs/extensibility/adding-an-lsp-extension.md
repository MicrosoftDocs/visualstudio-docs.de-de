---
title: Hinzufügen einer sprach Server-Protokollerweiterung | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie eine Visual Studio-Erweiterung erstellen, die einen Sprachserver auf Grundlage des Language Server-Protokolls (LSP) integriert.
ms.custom: SEO-VS-2020
ms.date: 11/14/2017
ms.topic: conceptual
ms.assetid: 52f12785-1c51-4c2c-8228-c8e10316cd83
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 26f78be8708e61370be3256c8cde481d5c61c89d
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/24/2020
ms.locfileid: "95598145"
---
# <a name="add-a-language-server-protocol-extension"></a>Hinzufügen der Sprachserverprotokollerweiterung

Das Language Server-Protokoll (LSP) ist ein gängiges Protokoll in Form von JSON RPC v 2.0, das zum Bereitstellen von Sprachdienst Funktionen für verschiedene Code-Editoren verwendet wird. Mithilfe des-Protokolls können Entwickler einen einzelnen Sprachserver schreiben, um Sprachdienst Features wie IntelliSense, Fehlerdiagnose, alle Verweise suchen usw. zu unterschiedlichen Code-Editoren, die den LSP unterstützen, bereitzustellen. Traditionell können Sprachdienste in Visual Studio mithilfe von TextMate-Grammatik Dateien hinzugefügt werden, um grundlegende Funktionen wie Syntax Hervorhebung oder benutzerdefinierte Sprachdienste zu erstellen, die den vollständigen Satz von Visual Studio-Erweiterbarkeits-APIs verwenden, um umfangreichere Daten bereitzustellen. Mit der Visual Studio-Unterstützung für LSP steht eine dritte Option zur Verfügung.

![Sprachserver-Protokolldienst in Visual Studio](media/lsp-service-in-VS.png)

## <a name="language-server-protocol"></a>Sprachserverprotokoll

![Sprachserver-Protokoll Implementierung](media/lsp-implementation.png)

In diesem Artikel wird beschrieben, wie Sie eine Visual Studio-Erweiterung erstellen, die einen LSP-basierten Sprachserver verwendet. Dabei wird davon ausgegangen, dass Sie bereits einen LSP-basierten Sprachserver entwickelt haben und ihn nur in Visual Studio integrieren möchten.

Zur Unterstützung in Visual Studio können Sprachserver mit dem Client (Visual Studio) über einen beliebigen streambasierten Übertragungsmechanismus kommunizieren, z. b.:

* Standard Eingabe-/Ausgabestreams
* Named Pipes
* Sockets (nur TCP)

Das Ziel des LSP und die Unterstützung in Visual Studio besteht darin, Sprachdienste zu integrieren, die nicht Teil von Visual Studio sind. Es ist nicht vorgesehen, vorhandene Sprachdienste (z. b. c#) in Visual Studio zu erweitern. Weitere Informationen zum Erweitern vorhandener Sprachen finden Sie im Erweiterbarkeits Handbuch des sprach Diensts (z. b. ["Roslyn" .NET Compiler Platform](../extensibility/dotnet-compiler-platform-roslyn-extensibility.md)) oder unter [Erweitern des Editors und der Sprachdienste](../extensibility/extending-the-editor-and-language-services.md).

Weitere Informationen zum eigentlichen [Protokoll finden Sie in der Dokumentation.](https://github.com/Microsoft/language-server-protocol)

Weitere Informationen zum Erstellen eines Beispiel sprach Servers oder zum Integrieren eines vorhandenen sprach Servers in [Visual Studio Code finden Sie in der Dokumentation.](https://code.visualstudio.com/docs/extensions/example-language-server)

## <a name="language-server-protocol-supported-features"></a>Vom sprach Server Protokoll unterstützte Funktionen

Die folgenden Tabellen zeigen, welche LSP-Funktionen in Visual Studio unterstützt werden:

Nachricht | Bietet Unterstützung in Visual Studio
--- | ---
initialisieren | ja
initialisiert | ja
shutdown | ja
exit | ja
$/cancelRequest | ja
Fenster/ShowMessage | ja
Fenster/showmessagerequest | ja
Fenster/Protokollmeldung | ja
Telemetrie/Ereignis |
Client/registercapability |
Client/unregistercapability |
Arbeitsbereich/didchangeconfiguration | ja
Workspace/didchangewatchedfiles | ja
Arbeitsbereich/Symbol | ja
Workspace/ExecuteCommand | ja
Arbeitsbereich/applyedit | ja
TextDocument/publishdiagnostics | ja
TextDocument/didopen | ja
TextDocument/didchange | ja
TextDocument/willsave |
TextDocument/willsavewaituntil |
TextDocument/didsave | ja
TextDocument/didclose | ja
TextDocument/Vervollständigung | ja
Abschluss/auflösen | ja
TextDocument/Hover | ja
TextDocument/signaturehelp | ja
TextDocument/Verweise | ja
TextDocument/documentHighlight | ja
TextDocument/documentsymbol | ja
TextDocument/Formatierung | ja
TextDocument/rangeformatierung | ja
TextDocument/ontypeformatierung |
TextDocument/Definition | ja
TextDocument/codeaction | ja
TextDocument/codelta ens |
codelta ens/auflösen |
TextDocument/documentlink |
documentlink/auflösen |
TextDocument/umbenennen | ja

## <a name="get-started"></a>Erste Schritte

> [!NOTE]
> Ab Visual Studio 2017, Version 15,8, ist die Unterstützung für das Common Language Server-Protokoll in Visual Studio integriert. Wenn Sie LSP-Erweiterungen mithilfe der Preview [Language Server-Client-VSIX](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview) -Version erstellt haben, funktionieren Sie nicht mehr, sobald Sie ein Upgrade auf Version 15,8 oder höher durchführen. Sie müssen die folgenden Schritte ausführen, um die LSP-Erweiterungen erneut zu funktionieren:
>
> 1. Deinstallieren Sie die VSIX-Vorschauversion des Microsoft Visual Studio Language Server-Protokolls
>
>    Ab Version 15,8 wird jedes Mal, wenn Sie ein Upgrade in Visual Studio durchführen, die VSIX-Vorschau automatisch erkannt und entfernt.
>
> 2. Aktualisieren Sie den nuget-Verweis auf die neueste Version, die nicht der Vorschauversion für [LSP-Pakete](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client)entspricht.
>
> 3. Entfernen Sie die Abhängigkeit zur VSIX-Vorschauversion des Microsoft Visual Studio Language Server-Protokolls in Ihrem VSIX-Manifest.
>
> 4. Stellen Sie sicher, dass Ihre VSIX Visual Studio 2017, Version 15,8 Preview 3, als die untere Grenze für das Installationsziel angibt.
>
> 5. Führen Sie die Neuerstellung und dann die erneute Bereitstellung durch.

### <a name="create-a-vsix-project"></a>Erstellen eines VSIX-Projekts

Um eine Sprachdienst Erweiterung mithilfe eines LSP-basierten sprach Servers zu erstellen, müssen Sie zunächst sicherstellen, dass die **Visual Studio-extensionentwicklungs** -Arbeitsauslastung für Ihre Instanz von vs installiert ist.

Erstellen Sie als nächstes ein neues VSIX-Projekt, indem Sie zu **Datei**  >  **New Project**  >  **Visual c#**  >  **Extensibility**  >  **VSIX Project** navigieren:

![VSIX-Projekt erstellen](media/lsp-vsix-project.png)

### <a name="language-server-and-runtime-installation"></a>Sprachserver-und Lauf Zeit Installation

Standardmäßig enthalten die Erweiterungen, die zur Unterstützung von LSP-basierten Sprach Servern in Visual Studio erstellt wurden, nicht die Sprachserver selbst oder die Laufzeiten, die für die Ausführung benötigt werden. Erweiterungs Entwickler sind dafür verantwortlich, die Sprachserver und die benötigten Laufzeiten zu verteilen. Hierfür gibt es mehrere Möglichkeiten:

* Sprachserver können in die VSIX als Inhalts Dateien eingebettet werden.
* Erstellen Sie eine MSI-Datei, um den Sprachserver und/oder erforderliche Laufzeiten zu installieren.
* Bereitstellen von Anweisungen zum Marketplace, um Benutzer zu informieren, wie Laufzeiten und Sprachserver abgerufen werden.

### <a name="textmate-grammar-files"></a>TextMate-Grammatik Dateien

Der LSP umfasst keine Angabe, wie die farbliche Farbgebung von Text für Sprachen bereitgestellt wird. Um benutzerdefinierte Farbgebung für Sprachen in Visual Studio bereitzustellen, können Erweiterungs Entwickler eine TextMate-Grammatik Datei verwenden. Führen Sie die folgenden Schritte aus, um benutzerdefinierte TextMate-Grammatik oder Designdateien hinzuzufügen:

1. Erstellen Sie in ihrer Erweiterung einen Ordner mit dem Namen "Grammatiken" (oder einen beliebigen Namen, den Sie auswählen).

2. Fügen Sie im *Grammatiken* -Ordner beliebige *\* tmlanguage*-, *\* plist*-, *\* tmtheme*-oder *\* JSON* -Dateien ein, die benutzerdefinierte Farbgebung bereitstellen möchten.

   > [!TIP]
   > Eine *tmtheme* -Datei definiert, wie die Bereiche Visual Studio-Klassifizierungen (benannte Farbtasten) zugeordnet werden. Anweisungen dazu finden Sie im Verzeichnis *% Program Files (x86)% \ Microsoft Visual Studio \\ \<version> \\ \<SKU> \common7\ide\commonextensions\microsoft\textmate\starterkit\themesg)* *.*

3. Erstellen Sie eine *pkgdef* -Datei, und fügen Sie eine Zeile hinzu, die der folgenden ähnelt:

    ```
    [$RootKey$\TextMate\Repositories]
    "MyLang"="$PackageFolder$\Grammars"
    ```

4. Klicken Sie mit der rechten Maustaste auf die Dateien, und wählen Sie **Eigenschaften**. Ändern Sie die Buildaktion in **Content** , und ändern **Sie die Eigenschaft** **in VSIX einschließen in** **true**.

Nachdem Sie die vorherigen Schritte abgeschlossen haben, wird dem Installationsverzeichnis des Pakets als Repository-Quelle mit dem Namen "mylang" ein *grammaticordner* hinzugefügt ("mylang" ist nur ein Name für die Mehrdeutigkeit und kann eine beliebige eindeutige Zeichenfolge sein). Alle Grammatiken (*tmlanguage* -Dateien) und Designdateien (*tmtheme* -Dateien) in diesem Verzeichnis werden als Potenzierung übernommen und ersetzen die integrierten Grammatiken, die mit Textmate bereitgestellt werden. Wenn die deklarierten Erweiterungen der Grammatik Datei der Erweiterung der Datei entsprechen, die geöffnet wird, führt TextMate einen Schritt aus.

## <a name="create-a-simple-language-client"></a>Erstellen eines einfachen sprach Clients

### <a name="main-interface---ilanguageclient"></a>Hauptschnittstelle- [ilanguageclient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017&preserve-view=true)

Nachdem Sie das VSIX-Projekt erstellt haben, fügen Sie dem Projekt die folgenden nuget-Pakete hinzu:

* [Microsoft. VisualStudio. languageserver. Client](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client)

> [!NOTE]
> Wenn Sie nach Abschluss der vorherigen Schritte eine Abhängigkeit von dem nuget-Paket nehmen, werden die Newtonsoft.Json-und streamjsonrpc-Paketen ebenfalls dem Projekt hinzugefügt. **Aktualisieren Sie diese Pakete nur dann, wenn Sie sicher sind, dass diese neuen Versionen auf der Version von Visual Studio installiert werden, auf die die Erweiterung abzielt**. Die Assemblys sind nicht in der VSIX enthalten. Stattdessen werden Sie aus dem Visual Studio-Installationsverzeichnis abgerufen. Wenn Sie auf eine neuere Version der Assemblys verweisen, als auf dem Computer eines Benutzers installiert ist, funktioniert die Erweiterung nicht.

Anschließend können Sie eine neue Klasse erstellen, die die [ilanguageclient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017&preserve-view=true) -Schnittstelle implementiert. Dies ist die Hauptschnittstelle, die für sprach Clients erforderlich ist, die eine Verbindung mit einem LSP-basierten Sprachserver herstellen.

Beispiel:

```csharp
namespace MockLanguageExtension
{
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
        public string Name => "Bar Language Extension";

        public IEnumerable<string> ConfigurationSections => null;

        public object InitializationOptions => null;

        public IEnumerable<string> FilesToWatch => null;

        public event AsyncEventHandler<EventArgs> StartAsync;
        public event AsyncEventHandler<EventArgs> StopAsync;

        public async Task<Connection> ActivateAsync(CancellationToken token)
        {
            await Task.Yield();

            ProcessStartInfo info = new ProcessStartInfo();
            info.FileName = Path.Combine(Path.GetDirectoryName(Assembly.GetExecutingAssembly().Location), "Server", @"MockLanguageServer.exe");
            info.Arguments = "bar";
            info.RedirectStandardInput = true;
            info.RedirectStandardOutput = true;
            info.UseShellExecute = false;
            info.CreateNoWindow = true;

            Process process = new Process();
            process.StartInfo = info;

            if (process.Start())
            {
                return new Connection(process.StandardOutput.BaseStream, process.StandardInput.BaseStream);
            }

            return null;
        }

        public async Task OnLoadedAsync()
        {
            await StartAsync.InvokeAsync(this, EventArgs.Empty);
        }

        public Task OnServerInitializeFailedAsync(Exception e)
        {
            return Task.CompletedTask;
        }

        public Task OnServerInitializedAsync()
        {
            return Task.CompletedTask;
        }
    }
}
```

Die wichtigsten Methoden, die implementiert werden müssen, sind [onloadedasync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017&preserve-view=true) und [activateasync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017&preserve-view=true). " [Onloadedasync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017&preserve-view=true) " wird aufgerufen, wenn Visual Studio Ihre Erweiterung geladen hat und Ihr Sprachserver bereit ist, gestartet zu werden. Bei dieser Methode können Sie den [startasync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017&preserve-view=true) -Delegaten sofort aufrufen, um zu signalisieren, dass der Sprachserver gestartet werden soll, oder Sie können zusätzliche Logik ausführen und [startasync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017&preserve-view=true) später aufrufen. **Um Ihren Sprachserver zu aktivieren, müssen Sie startasync zu einem bestimmten Zeitpunkt aufrufen.**

[Activateasync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017&preserve-view=true) ist die Methode, die schließlich aufgerufen wird, indem der [startasync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017&preserve-view=true) -Delegat aufgerufen wird. Sie enthält die Logik, mit der der Sprachserver gestartet und eine Verbindung mit dem Server hergestellt werden kann. Ein Verbindungs Objekt, das Datenströme zum Schreiben auf den Server und zum Lesen vom Server enthält, muss zurückgegeben werden. Alle hier ausgelösten Ausnahmen werden abgefangen und für den Benutzer über eine Infobar-Nachricht in Visual Studio angezeigt.

### <a name="activation"></a>Aktivierung

Sobald Ihre Sprachclient Klasse implementiert ist, müssen Sie zwei Attribute definieren, um zu definieren, wie Sie in Visual Studio geladen und aktiviert werden:

```csharp
  [Export(typeof(ILanguageClient))]
  [ContentType("bar")]
```

### <a name="mef"></a>MEF

Visual Studio verwendet [MEF](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (Managed Extensibility Framework) zum Verwalten der Erweiterungs Punkte. Das [Export](/dotnet/api/system.componentmodel.composition.exportattribute) Attribut gibt Visual Studio an, dass diese Klasse als Erweiterungs Punkt übernommen und zum richtigen Zeitpunkt geladen werden soll.

Um MEF verwenden zu können, müssen Sie auch MEF als Medienobjekt im VSIX-Manifest definieren.

Öffnen Sie den VSIX-Manifest-Designer, und navigieren Sie zur Registerkarte " **Assets** ":

![MEF-Medienobjekt hinzufügen](media/lsp-add-asset.png)

Klicken Sie auf **neu** , um ein neues Asset zu erstellen:

![MEF-Asset definieren](media/lsp-define-asset.png)

* **Typ**: Microsoft. VisualStudio. MEFComponent
* **Quelle**: ein Projekt in der aktuellen Projekt Mappe
* **Projekt**: [Ihr Projekt]

### <a name="content-type-definition"></a>Inhaltstyp Definition

Derzeit ist die einzige Möglichkeit zum Laden Ihrer LSP-basierten Sprachserver Erweiterung der dateiinhaltstyp. Das heißt, wenn Sie die Sprachclient Klasse definieren (die " [ilanguageclient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017&preserve-view=true)" implementiert), müssen Sie die Typen von Dateien definieren, die nach dem Öffnen die Erweiterung laden. Wenn keine Dateien geöffnet werden, die dem definierten Inhaltstyp entsprechen, wird die Erweiterung nicht geladen.

Dies erfolgt durch Definieren einer oder mehrerer `ContentTypeDefinition` Klassen:

```csharp
namespace MockLanguageExtension
{
    public class BarContentDefinition
    {
        [Export]
        [Name("bar")]
        [BaseDefinition(CodeRemoteContentDefinition.CodeRemoteContentTypeName)]
        internal static ContentTypeDefinition BarContentTypeDefinition;

        [Export]
        [FileExtension(".bar")]
        [ContentType("bar")]
        internal static FileExtensionToContentTypeDefinition BarFileExtensionDefinition;
    }
}
```

Im vorherigen Beispiel wird eine Inhaltstyp Definition für Dateien erstellt, die mit der Dateierweiterung " *. Bar* " enden. Der Inhaltstyp Definition wird der Name "Bar" zugewiesen, und Sie muss von " [coderemotecontenttykename](/dotnet/api/microsoft.visualstudio.languageserver.client.coderemotecontentdefinition.coderemotecontenttypename?view=visualstudiosdk-2017&preserve-view=true)" abgeleitet werden.

Nachdem Sie eine Inhaltstyp Definition hinzugefügt haben, können Sie definieren, wann die Sprachclient Erweiterung in der Sprachclient Klasse geladen werden soll:

```csharp
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
    }
```

Wenn Sie Unterstützung für LSP-Sprachserver hinzufügen, müssen Sie kein eigenes Projekt System in Visual Studio implementieren. Kunden können eine einzelne Datei oder einen Ordner in Visual Studio öffnen, um mit der Verwendung Ihres sprach Dienstanbieter zu beginnen. Tatsächlich ist die Unterstützung für LSP-Sprachserver so konzipiert, dass Sie nur in Open Folder-/dateiszenarios funktioniert. Wenn ein benutzerdefiniertes Projekt System implementiert ist, funktionieren einige Funktionen (z. b. Einstellungen) nicht.

## <a name="advanced-features"></a>Erweiterte Funktionen

### <a name="settings"></a>Einstellungen

Die Unterstützung für benutzerdefinierte sprachspezifische Einstellungen ist zwar verfügbar, wird jedoch gerade noch verbessert. Die Einstellungen sind spezifisch für das, was der Sprachserver unterstützt, und Steuern in der Regel, wie der Sprachserver Daten ausgibt. Ein Sprachserver kann z. b. eine Einstellung für die maximale Anzahl von gemeldeten Fehlern aufweisen. Erweiterungs Autoren definieren einen Standardwert, der von Benutzern für bestimmte Projekte geändert werden kann.

Führen Sie die folgenden Schritte aus, um ihrer LSP-Sprachdienst Erweiterung Unterstützung für Einstellungen hinzuzufügen:

1. Fügen Sie dem Projekt eine JSON-Datei (z. b. *MockLanguageExtensionSettings.js*) hinzu, die die Einstellungen und deren Standardwerte enthält. Beispiel:

    ```json
    {
        "foo.maxNumberOfProblems": -1
    }
    ```

2. Klicken Sie mit der rechten Maustaste auf die JSON-Datei, und wählen Sie **Eigenschaften**. Ändern Sie die Buildaktion in "Content" **und die Eigenschaft** "include in VSIX" in " **true**".

3. Implementieren Sie ConfigurationSettings, und geben Sie die Liste der Präfixe für die Einstellungen zurück, die in der JSON-Datei definiert sind (in Visual Studio Code wird dies dem Konfigurations Abschnittsnamen in package.jsauf zugeordnet):

    ```csharp
    public IEnumerable<string> ConfigurationSections
    {
        get
        {
            yield return "foo";
        }
    }
    ```

4. Fügen Sie dem Projekt eine pkgdef-Datei hinzu (fügen Sie eine neue Textdatei hinzu, und ändern Sie die Dateierweiterung in pkgdef). Die pkgdef-Datei sollte diese Informationen enthalten:

    ```
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\[settings-name]]
    @="$PackageFolder$\[settings-file-name].json"
    ```

    Beispiel:

    ```
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\MockLanguageExtension]
    @="$PackageFolder$\MockLanguageExtensionSettings.json"
    ```

5. Klicken Sie mit der rechten Maustaste auf die pkgdef-Datei, und wählen Sie **Eigenschaften**. Ändern Sie die Buildaktion in **Content** **und die** **include in VSIX** -Eigenschaft in **true**.

6. Öffnen Sie die Datei " *Source. Extension. vsixmanifest* ", und fügen Sie ein Asset auf der Registerkarte " **Asset** " hinzu:

   ![VSPackage-Asset bearbeiten](media/lsp-add-vspackage-asset.png)

   * **Typ**: Microsoft. VisualStudio. VSPackage
   * **Quelle**: Datei im Dateisystem
   * **Pfad**: [Pfad zu Ihrer *pkgdef* -Datei]

### <a name="user-editing-of-settings-for-a-workspace"></a>Benutzer Bearbeitung von Einstellungen für einen Arbeitsbereich

1. Der Benutzer öffnet einen Arbeitsbereich mit Dateien, die Ihr Server besitzt.
2. Der Benutzer fügt eine Datei im *vs* -Ordner mit dem Namen *VSWorkspaceSettings.jsauf* hinzu.
3. Der Benutzer fügt der Datei *VSWorkspaceSettings.js* eine Zeile für eine Einstellung hinzu, die der Server bereitstellt. Beispiel:

    ```json
    {
        "foo.maxNumberOfProblems": 10
    }
    ```

### <a name="enable-diagnostics-tracing"></a>Diagnose Ablauf Verfolgung aktivieren

Die Diagnose Ablauf Verfolgung kann aktiviert werden, um alle Nachrichten zwischen dem Client und dem Server auszugeben, was beim Debuggen von Problemen hilfreich sein kann. Gehen Sie folgendermaßen vor, um die Diagnose Ablauf Verfolgung zu aktivieren:

1. Öffnen oder erstellen Sie die Datei mit den Arbeitsbereichs Einstellungen *VSWorkspaceSettings.jsauf* (siehe "Benutzer Bearbeitung von Einstellungen für einen Arbeitsbereich").
2. Fügen Sie die folgende Zeile in die JSON-Einstellungsdatei ein:

```json
{
    "foo.trace.server": "Off"
}
```

Es gibt drei mögliche Werte für die Ablauf Verfolgungs Ausführlichkeit:

* "Off": Ablauf Verfolgung vollständig ausgeschaltet
* "Messages": die Ablauf Verfolgung ist aktiviert, aber nur der Methodenname und die Antwort-ID werden nachverfolgt.
* "Verbose": Ablauf Verfolgung aktiviert; die gesamte RPC-Nachricht wird nachverfolgt.

Wenn die Ablauf Verfolgung aktiviert ist, wird der Inhalt in eine Datei im Verzeichnis *%Temp%\visualstudio\lsp* geschrieben. Das Protokoll folgt dem Namensformat *[languageclientname]-[DateTime Stamp]. log*. Die Ablauf Verfolgung kann derzeit nur für Szenarien mit geöffneten Ordnern aktiviert werden. Beim Öffnen einer einzelnen Datei zum Aktivieren eines sprach Servers ist keine Unterstützung für die Diagnose Ablauf Verfolgung vorhanden.

### <a name="custom-messages"></a>Benutzerdefinierte Meldungen

Es gibt APIs, um das Übergeben von Nachrichten an den und das Empfangen von Nachrichten vom Sprachserver zu vereinfachen, die nicht Teil des Standard Sprachserver Protokolls sind. Um benutzerdefinierte Nachrichten zu verarbeiten, implementieren Sie die [ilanguageclientcustommessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017&preserve-view=true) -Schnittstelle in ihrer Sprachclient Klasse. Die [vs-streamjsonrpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) -Bibliothek wird verwendet, um benutzerdefinierte Nachrichten zwischen dem Sprachclient und dem Sprachserver zu übertragen. Da die Client Erweiterung der LSP-Sprache genau wie jede andere Visual Studio-Erweiterung aussieht, können Sie in der Erweiterung über benutzerdefinierte Nachrichten zusätzliche Features hinzufügen (die nicht vom LSP unterstützt werden).

#### <a name="receive-custom-messages"></a>Empfangen benutzerdefinierter Nachrichten

Um benutzerdefinierte Nachrichten vom Sprachserver zu empfangen, implementieren Sie die [custommessagetarget](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.custommessagetarget?view=visualstudiosdk-2017&preserve-view=true) -Eigenschaft für [ilanguageclientcustommessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017&preserve-view=true) und geben ein Objekt zurück, das die Handhabung Ihrer benutzerdefinierten Nachrichten kennt. Das folgende Beispiel zeigt dies:

```csharp
internal class MockCustomLanguageClient : MockLanguageClient, ILanguageClientCustomMessage
{
    private JsonRpc customMessageRpc;

    public MockCustomLanguageClient() : base()
    {
        CustomMessageTarget = new CustomTarget();
    }

    public object CustomMessageTarget
    {
        get;
        set;
    }

    public class CustomTarget
    {
        public void OnCustomNotification(JToken arg)
        {
            // Provide logic on what happens OnCustomNotification is called from the language server
        }

        public string OnCustomRequest(string test)
        {
            // Provide logic on what happens OnCustomRequest is called from the language server
        }
    }
}
```

#### <a name="send-custom-messages"></a>Senden benutzerdefinierter Nachrichten

Um benutzerdefinierte Nachrichten an den Sprachserver zu senden, implementieren Sie die [attachforcustommessageasync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.attachforcustommessageasync?view=visualstudiosdk-2017&preserve-view=true) -Methode für [ilanguageclientcustommessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017&preserve-view=true). Diese Methode wird aufgerufen, wenn Ihr Sprachserver gestartet wird und bereit ist, Nachrichten zu empfangen. Ein [JsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/src/StreamJsonRpc/JsonRpc.cs) -Objekt wird als Parameter übergeben, das Sie dann zum Senden von Nachrichten an den Sprachserver mithilfe von [vs-streamjsonrpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) -APIs weiter verwenden können. Das folgende Beispiel zeigt dies:

```csharp
internal class MockCustomLanguageClient : MockLanguageClient, ILanguageClientCustomMessage
{
    private JsonRpc customMessageRpc;

    public MockCustomLanguageClient() : base()
    {
        CustomMessageTarget = new CustomTarget();
    }

    public async Task AttachForCustomMessageAsync(JsonRpc rpc)
    {
        await Task.Yield();

        this.customMessageRpc = rpc;
    }

    public async Task SendServerCustomNotification(object arg)
    {
        await this.customMessageRpc.NotifyWithParameterObjectAsync("OnCustomNotification", arg);
    }

    public async Task<string> SendServerCustomMessage(string test)
    {
        return await this.customMessageRpc.InvokeAsync<string>("OnCustomRequest", test);
    }
}
```

### <a name="middle-layer"></a>Mittlere Ebene

Manchmal kann ein Erweiterungs Entwickler LSP-Nachrichten abfangen, die an den Sprachserver gesendet und von diesem empfangen werden. Beispielsweise kann ein Erweiterungs Entwickler den Nachrichten Parameter ändern, der für eine bestimmte LSP-Nachricht gesendet wurde, oder die vom Sprachserver zurückgegebenen Ergebnisse für eine LSP-Funktion ändern (z. b. Vervollständigungen). Wenn dies erforderlich ist, können Erweiterungs Entwickler LSP-Nachrichten mithilfe der-API von "Mittel dlelayer" abfangen.

Jede LSP-Nachricht verfügt über eine eigene mittlere ebenenschnittstelle für die Abfang Funktion. Um eine bestimmte Nachricht abzufangen, erstellen Sie eine Klasse, die die Schnittstelle der mittleren Ebene für diese Nachricht implementiert. Implementieren Sie dann die [ilanguageclientcustommessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017&preserve-view=true) -Schnittstelle in der Sprachclient Klasse, und geben Sie eine Instanz des Objekts in der Eigenschaft " [Mittel dlelayer](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.middlelayer?view=visualstudiosdk-2017&preserve-view=true) " zurück. Das folgende Beispiel zeigt dies:

```csharp
public class MockLanguageClient: ILanguageClient, ILanguageClientCustomMessage
{
    public object MiddleLayer => MiddleLayerProvider.Instance;

    private class MiddleLayerProvider : ILanguageClientWorkspaceSymbolProvider
    {
        internal readonly static MiddleLayerProvider Instance = new MiddleLayerProvider();

        private MiddleLayerProvider()
        {
        }

        public async Task<SymbolInformation[]> RequestWorkspaceSymbols(WorkspaceSymbolParams param, Func<WorkspaceSymbolParams, Task<SymbolInformation[]>> sendRequest)
        {
            // Send along the request as given
            SymbolInformation[] symbols = await sendRequest(param);

            // Only return symbols that are "files"
            return symbols.Where(sym => string.Equals(new Uri(sym.Location.Uri).Scheme, "file", StringComparison.OrdinalIgnoreCase)).ToArray();
        }
    }
}
```

Die Funktion der mittleren Ebene befindet sich noch in der Entwicklung und ist noch nicht vollständig.

## <a name="sample-lsp-language-server-extension"></a>Beispiel-LSP-Sprachserver Erweiterung

Informationen zum Anzeigen des Quellcodes einer Beispiel Erweiterung mithilfe der LSP-Client-API in Visual Studio finden Sie unter VSSDK-Extensibility-Samples [LSP Sample](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/LanguageServerProtocol).

## <a name="faq"></a>Häufig gestellte Fragen

**Ich möchte ein benutzerdefiniertes Projekt System erstellen, mit dem mein LSP-Sprachserver ergänzt werden kann, um die Unterstützung von Funktionen in Visual Studio bereitzustellen. wie gehe ich dazu vor?**

Die Unterstützung für LSP-basierte Sprachserver in Visual Studio basiert auf der [Funktion "Ordner öffnen](https://devblogs.microsoft.com/visualstudio/open-any-folder-with-visual-studio-15-preview/) " und ist so konzipiert, dass kein benutzerdefiniertes Projekt System erforderlich ist. Sie können ein [eigenes, Benutzer](https://github.com/Microsoft/VSProjectSystem)definiertes Projekt System nachfolgend beschrieben erstellen, aber einige Features, z. b. Einstellungen, funktionieren möglicherweise nicht. Die standardmäßige Initialisierungs Logik für LSP-Sprachserver besteht darin, den Stamm Ordner Speicherort des Ordners zu übergeben, der gerade geöffnet wird. Wenn Sie also ein benutzerdefiniertes Projekt System verwenden, müssen Sie möglicherweise während der Initialisierung benutzerdefinierte Logik bereitstellen, um sicherzustellen, dass Ihr Sprachserver ordnungsgemäß gestartet

**Gewusst wie Unterstützung für Debugger hinzufügen?**

Wir werden in einer zukünftigen Version Unterstützung für das [gängige Debugprotokoll](https://code.visualstudio.com/docs/extensionAPI/api-debugging) bereitstellen.

**Wenn bereits ein von vs unterstützter Sprachdienst installiert ist (z. b. JavaScript), kann ich trotzdem eine LSP-Sprachserver Erweiterung installieren, die zusätzliche Features bietet (z. b. linting)?**

Ja, aber nicht alle Features funktionieren ordnungsgemäß. Das ultimative Ziel für LSP-Sprachserver Erweiterungen besteht darin, Sprachdienste zu aktivieren, die von Visual Studio nicht nativ unterstützt werden. Sie können Erweiterungen erstellen, die zusätzliche Unterstützung bei der Verwendung von LSP-Sprach Servern bieten, aber einige Features (z. b. IntelliSense) werden nicht reibungslos eingesetzt. Im Allgemeinen wird empfohlen, dass LSP-Sprachserver Erweiterungen verwendet werden, um neue sprach Umgebungen bereitzustellen und vorhandene zu erweitern.

**Wo kann ich meinen abgeschlossenen LSP Language Server VSIX veröffentlichen?**

Weitere Informationen finden Sie [hier](walkthrough-publishing-a-visual-studio-extension.md).

## <a name="see-also"></a>Siehe auch

- [Hinzufügen von Visual Studio-Editor-Unterstützung für andere Sprachen](../ide/adding-visual-studio-editor-support-for-other-languages.md)
