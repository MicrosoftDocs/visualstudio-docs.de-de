---
title: Arbeitsbereiche in Visual Studio | Microsoft-Dokumentation
description: Erfahren Sie, wie Visual Studio einen Arbeitsbereich verwendet, um eine Sammlung von Dateien in einem geöffneten Ordner darzustellen, einschließlich der Arbeitsbereichs Anbieter und-Dienste.
ms.custom: SEO-VS-2020
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 1ed660a5f52aba548d087b28f7caea4d1966fe45
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97876947"
---
# <a name="workspaces"></a>Arbeitsbereiche

In einem Arbeitsbereich stellt Visual Studio eine beliebige Sammlung von Dateien im [geöffneten Ordner](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)dar und wird durch den- <xref:Microsoft.VisualStudio.Workspace.IWorkspace> Typ dargestellt. Der Arbeitsbereich kennt nicht den Inhalt oder die Funktionen im Zusammenhang mit Dateien innerhalb des Ordners. Vielmehr stellt Sie einen allgemeinen Satz von APIs für Features und Erweiterungen bereit, um Daten zu erzeugen und zu nutzen, auf die andere Benutzer reagieren können. Die Producer werden über die [Managed Extensibility Framework](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (MEF) mithilfe verschiedener Export Attribute zusammengesetzt.

## <a name="workspace-providers-and-services"></a>Arbeitsbereichs Anbieter und-Dienste

Arbeitsbereichs Anbieter und-Dienste stellen die Daten und Funktionen bereit, die auf den Inhalt eines Arbeitsbereichs reagieren sollen. Sie können kontextabhängige Dateiinformationen, Symbole in Quelldateien oder Buildfunktionen bereitstellen.

Beide Konzepte verwenden ein [Factorymuster](https://en.wikipedia.org/wiki/Factory_method_pattern) und werden durch MEF durch den Arbeitsbereich importiert. Alle Export Attribute implementieren `IProviderMetadataBase` oder `IWorkspaceServiceFactoryMetadata` . es gibt jedoch konkrete Typen, die Erweiterungen für exportierte Typen verwenden sollten.

Ein Unterschied zwischen Anbietern und Diensten ist die Beziehung zum Arbeitsbereich. Ein Arbeitsbereich kann viele Anbieter eines bestimmten Typs aufweisen, es wird jedoch nur ein Dienst eines bestimmten Typs pro Arbeitsbereich erstellt. Ein Arbeitsbereich verfügt beispielsweise über viele Dateiscanner-Anbieter, aber der Arbeitsbereich verfügt über nur einen Indizierungs Dienst pro Arbeitsbereich.

Ein weiterer wichtiger Unterschied ist die Nutzung von Daten von Anbietern und Diensten. Der Arbeitsbereich ist der Einstiegspunkt zum erhalten von Daten von Anbietern aus mehreren Gründen. Zunächst verfügen Anbieter in der Regel über einen schmalen Satz von Daten, die Sie erstellen. Bei den Daten kann es sich um Symbole für eine c#-Quelldatei oder um builddateikontexte für eine _CMakeLists.txt_ Datei handeln. Der Arbeitsbereich entspricht der Anforderung eines Consumers an die Anbieter, deren Metadaten mit der Anforderung übereinstimmen. Zweitens ermöglichen einige Szenarien vielen Anbietern, an einer Anforderung mitzuwirken, während andere Szenarien den Anbieter mit der höchsten Priorität verwenden.

Im Gegensatz dazu können Erweiterungen Instanzen von erhalten und direkt mit den Arbeitsbereichs Diensten interagieren. Erweiterungs Methoden für `IWorkspace` sind für die Dienste verfügbar, die von Visual Studio bereitgestellt werden, z <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A> . b.. Ihre Erweiterung bietet möglicherweise einen Arbeitsbereichs Dienst für Komponenten innerhalb ihrer Erweiterung oder für andere Erweiterungen. Consumer sollten <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetServiceAsync%2A> oder eine Erweiterungsmethode verwenden, die Sie für den `IWorkspace` Typ angeben.

>[!WARNING]
> Erstellen Sie keine Dienste, die mit Visual Studio in Konflikt stehen. Dies kann zu unerwarteten Problemen führen.

## <a name="disposal-on-workspace-closure"></a>Entsorgung bei der Schließung des Arbeitsbereichs

Wenn ein Arbeitsbereich geschlossen wird, müssen Extender ggf. den asynchronen Code verwerfen, aber abrufen. Die- <xref:Microsoft.VisualStudio.Threading.IAsyncDisposable> Schnittstelle ist verfügbar, damit Sie diesen Code leicht schreiben können.

## <a name="related-types"></a>Verwandte Typen

- <xref:Microsoft.VisualStudio.Workspace.IWorkspace> ist die zentrale Entität für einen geöffneten Arbeitsbereich wie einen geöffneten Ordner.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspaceProviderFactory`1> erstellt einen Anbieter pro Arbeitsbereich, der instanziiert wird.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspaceServiceFactory> erstellt einen Dienst pro Arbeitsbereich, der instanziiert wird.
- <xref:Microsoft.VisualStudio.Threading.IAsyncDisposable> sollte für Anbieter und Dienste implementiert werden, die asynchronen Code während der Beseitigung ausführen müssen.
- <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper> stellt Hilfsmethoden für den Zugriff auf bekannte Dienste oder beliebige Dienste bereit.

## <a name="workspace-settings"></a>Arbeitsbereichseinstellungen

Arbeitsbereiche verfügen <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager> über einen Dienst mit einfacher, aber leistungsfähiger Kontrolle über einen Arbeitsbereich. Eine grundlegende Übersicht über die Einstellungen finden Sie unter [Anpassen von Build-und debugtasks](../ide/customize-build-and-debug-tasks-in-visual-studio.md).

Einstellungen für die meisten `SettingsType` Typen sind _JSON_ -Dateien, z. b. _VSWorkspaceSettings.json_ und _tasks.vs.json_.

Die Leistungsfähigkeit der Arbeitsbereichs Einstellungen liegt bei "Bereichen", bei denen es sich einfach um Pfade innerhalb des Arbeitsbereichs handelt. Wenn ein Consumer aufruft <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager.GetAggregatedSettings%2A> , werden alle Bereiche, die den angeforderten Pfad und den Typ der Einstellung enthalten, aggregiert. Die Bereichs Aggregations Priorität lautet wie folgt:

1. "Lokale Einstellungen", bei denen es sich in der Regel um das Stammverzeichnis des Arbeitsbereichs handelt `.vs`
1. Der angeforderte Pfad selbst.
1. Das übergeordnete Verzeichnis des angeforderten Pfads.
1. Alle weiteren übergeordneten Verzeichnisse bis einschließlich des Arbeitsbereichs Stamms.
1. "Globale Einstellungen", die sich in einem Benutzerverzeichnis befinden.

Das Ergebnis ist eine Instanz von <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings> . Dieses Objekt enthält die Einstellungen für einen bestimmten Typ und kann zum Festlegen von Schlüsselnamen, die als gespeichert werden, abgefragt werden `string` . Die <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings.GetProperty%2A> Methoden und <xref:Microsoft.VisualStudio.Workspace.Settings.WorkspaceSettingsExtensions> Erweiterungs Methoden erwarten, dass der Aufrufer den Typ des angeforderten Einstellungs Werts kennt. Da die meisten Einstellungsdateien als _JSON_ -Dateien beibehalten werden, verwenden viele Aufrufe `string` , `bool` , `int` und Arrays dieser Typen. Objekttypen werden ebenfalls unterstützt. In diesen Fällen können Sie `IWorkspaceSettings` sich selbst als Typargument verwenden. Zum Beispiel:

```json
{
  "intValue": 1,
  "stringValue": "s",
  "boolValue": true,
  "stringArray": [
    "s1",
    "s2"
  ],
  "nestedIWorkspaceSettings": {
    "nestedString": "ns"
  }
}
```

Angenommen, diese Einstellungen befinden sich imVSWorkspaceSettings.jseines Benutzers _auf, auf_ die Daten wie folgt zugegriffen werden kann:

```csharp
using System.Collections.Generic;
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Settings;

private static void ReadSettings(IWorkspace workspace)
{
    IWorkspaceSettingsManager settingsManager = workspace.GetSettingsManager();
    IWorkspaceSettings settings = settingsManager.GetAggregatedSettings(SettingsTypes.Generic);

    // result == WorkspaceSettingsResult.Success
    WorkspaceSettingsResult result = settings.GetProperty("intValue", out int intValue);
    result = settings.GetProperty("stringValue", out string stringValue);
    result = settings.GetProperty("boolValue", out bool boolValue);
    result = settings.GetProperty("stringArray", out string[] stringArray);
    result = settings.GetProperty("nestedIWorkspaceSettings", out IWorkspaceSettings nestedIWorkspaceSettings);
    result = nestedIWorkspaceSettings.GetProperty("nestedString", out string nestedString);

    // Extension method alternative using default values.
    int intValueOrDefault = settings.Property("intValue", /* default */ 42);

    // Missing key. result == WorkspaceSettingsResult.Undefined
    result = settings.GetProperty("missing", out string missing);

    // Wrong type for a key. result == WorkspaceSettingsResult.Error
    result = settings.GetProperty("intValue", out IWorkspaceSettings notSettings);

    // Special ability to union "stringArray" across all scopes.
    IEnumerable<string> allStringArray = settings.UnionPropertyArray<string>("stringArray");
}
```

>[!NOTE]
>Diese Einstellungs-APIs stehen nicht im Zusammenhang mit den im-Namespace verfügbaren APIs `Microsoft.VisualStudio.Settings` . Die Arbeitsbereichs Einstellungen sind agnostisch des Hosts und verwenden Arbeitsbereichs spezifische Einstellungsdateien oder dynamische Einstellungs Anbieter.

### <a name="providing-dynamic-settings"></a>Bereitstellen dynamischer Einstellungen

Erweiterungen können s bereitstellen <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsProvider> . Mit diesen in-Memory-Anbietern können Erweiterungen Einstellungen hinzufügen oder andere außer Kraft setzen.

Der Export eines `IWorkspaceSettingsProvider` unterscheidet sich von anderen Arbeitsbereichs Anbietern. Die Factory ist nicht, `IWorkspaceProviderFactory` und es gibt keinen speziellen Attributtyp. Implementieren Sie stattdessen, <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsProviderFactory> und verwenden Sie `[Export(typeof(IWorkspaceSettingsProviderFactory))]` .

```csharp
// Common workspace provider factory pattern
[ExportFeatureProvider(some, args, to, export)]
internal class MyProviderFactory : IWorkspaceProviderFactory<IFeatureProvider>
{
     IFeatureProvider CreateProvider(IWorkspace workspace) => new Provider(workspace);
}

// IWorkspaceSettingsProvider pattern
[Export(typeof(IWorkspaceSettingsProviderFactory))]
internal class MySettingsProviderFactory : IWorkspaceSettingsProviderFactory
{
    // 100 is typically the value used by built-in settings providers. Lower value is higher priority.
    int Priority => 100;

    IWorkspaceSettingsProvider CreateSettingsProvider(IWorkspace workspace) => new MySettingsProvider(workspace);
}
```

>[!TIP]
>Gibt beim Implementieren von Methoden, die zurückgeben `IWorkspaceSettingsSource` (wie `IWorkspaceSettingsProvider.GetSingleSettings` ), eine Instanz von anstelle von zurück `IWorkspaceSettings` `IWorkspaceSettingsSource` . `IWorkspaceSettings` bietet weitere Informationen, die bei einigen Einstellungs Aggregationen nützlich sein können.

### <a name="settings-related-apis"></a>Einstellungs bezogene APIs

- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager> Hiermit werden Einstellungen für den Arbeitsbereich gelesen und aggregiert.
- <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetSettingsManager%2A> Ruft den `IWorkspaceSettingsManager` für einen Arbeitsbereich ab.
- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager.GetAggregatedSettings%2A> Ruft Einstellungen für einen angegebenen Bereich ab, der über alle überlappenden Bereiche aggregiert wird.
- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings> enthält Einstellungen für einen bestimmten Bereich.

## <a name="workspace-suggested-practices"></a>Empfohlene Vorgehensweisen

- Rückgabe von Objekten von `IWorkspaceProviderFactory.CreateProvider` oder ähnlichen APIs, die Ihren `Workspace` Kontext bei der Erstellung merken. Anbieter Schnittstellen werden geschrieben, erwartet, dass dieses Objekt bei der Erstellung beibehalten wird.
- Speichern Sie Arbeitsbereichs spezifische Caches oder Einstellungen im Pfad "lokale Einstellungen" des Arbeitsbereichs. Erstellen Sie einen Pfad für die Datei, indem Sie `Microsoft.VisualStudio.Workspace.WorkspaceHelper.MakeRootedUnderWorkingFolder` in Visual Studio 2017, Version 15,6 oder höher, verwenden. Verwenden Sie für Versionen vor Version 15,6 den folgenden Code Ausschnitt:

```csharp
using System.IO;
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Settings;

private static string MakeRootedUnderWorkingFolder(IWorkspace workspace, string relativePath)
{
    string workingFolder = workspace.GetSettingsManager().GetAggregatedSettings(SettingsTypes.WorkspaceControlSettings).Property<string>("WorkingFolder");
    return Path.Combine(workingFolder, relativePath);
}
```

## <a name="solution-events-and-package-auto-load"></a>Projektmappenereignisse und Automatisches Laden von Paketen

Geladene Pakete können implementieren `IVsSolutionEvents7` und aufrufen `IVsSolution.AdviseSolutionEvents` . Dies schließt Ereignisse beim Öffnen und Schließen eines Ordners in Visual Studio ein.

Ein Benutzeroberflächen Kontext kann verwendet werden, um das Paket automatisch zu laden. Der Wert ist `4646B819-1AE0-4E79-97F4-8A8176FDD664`.

## <a name="troubleshooting"></a>Problembehandlung

### <a name="the-sourceexplorerpackage-package-did-not-load-correctly"></a>Das sourceexplorerpackage-Paket wurde nicht ordnungsgemäß geladen.

Die Erweiterbarkeit von Arbeitsbereichen ist hochgradig MEF-basiert, und Kompositions Fehler bewirken, dass das Paket, das den geöffneten Ordner gehostet, nicht geladen wird. Wenn eine Erweiterung z. b. einen Typ mit exportiert `ExportFileContextProviderAttribute` , der Typ jedoch nur implementiert `IWorkspaceProviderFactory<IFileContextActionProvider>` , tritt ein Fehler auf, wenn versucht wird, einen Ordner in Visual Studio zu öffnen.

::: moniker range="vs-2017"

Fehlerdetails finden Sie unter " _%LocalAppData%\microsoft\visualstudio\ 15.0_id \componentmodelcache\microsoft.VisualStudio.default.err_". Beheben Sie alle Fehler für Typen, die von ihrer Erweiterung implementiert werden.

::: moniker-end

::: moniker range=">=vs-2019"

Fehlerdetails finden Sie unter " _%LocalAppData%\microsoft\visualstudio\ 16.0_id \componentmodelcache\microsoft.VisualStudio.default.err_". Beheben Sie alle Fehler für Typen, die von ihrer Erweiterung implementiert werden.

::: moniker-end

## <a name="next-steps"></a>Nächste Schritte

* [Datei Kontexte](workspace-file-contexts.md) : Datei Kontext Anbieter bringen Code Intelligenz für geöffnete Ordner Arbeitsbereiche.
* [Indizierung](workspace-indexing.md) : die Arbeitsbereichs Indizierung sammelt und speichert Informationen über den Arbeitsbereich.
