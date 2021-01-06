---
title: Kontexte für Arbeitsbereichs Dateien in Visual Studio | Microsoft-Dokumentation
description: Erfahren Sie mehr über Datei Kontext Anbieter, die die ifilecontextprovider-Schnittstelle implementieren, um Einblicke in geöffnete Ordner Arbeitsbereiche zu unterstützen.
ms.custom: SEO-VS-2020
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 271b05d78123136d47cb618e8ed38cea64b7beac
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877064"
---
# <a name="workspace-file-contexts"></a>Kontexte für Arbeitsbereichs Dateien

Alle Einblicke in Arbeitsbereiche [offener Ordner](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) werden von "Datei Kontext Anbieter" erstellt, die die- <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider> Schnittstelle implementieren. Diese Erweiterungen können nach Mustern in Ordnern oder Dateien suchen, MSBuild-Dateien und Makefiles lesen, Paketabhängigkeiten erkennen usw., um die Einblicke zu sammeln, die Sie benötigen, um einen Datei Kontext zu definieren. Ein Datei Kontext allein führt keine Aktion aus, sondern stellt Daten bereit, auf die eine andere Erweiterung reagieren kann.

Jeder <xref:Microsoft.VisualStudio.Workspace.FileContext> ist ein `Guid` zugeordnet, der den Typ der Daten angibt, die er enthält. Ein Arbeitsbereich verwendet dies `Guid` später, um ihn mit Erweiterungen zu vergleichen, die die Daten über die- <xref:Microsoft.VisualStudio.Workspace.FileContext.Context> Eigenschaft verwenden. Ein Datei Kontext Anbieter wird mit Metadaten exportiert, die den Datei Kontext identifizieren, `Guid` für den er möglicherweise Daten erzeugt.

Nach der Definition kann einem Datei Kontext eine beliebige Anzahl von Dateien oder Ordnern im Arbeitsbereich zugeordnet werden. Einer bestimmten Datei oder einem Ordner kann eine beliebige Anzahl von Datei Kontexten zugeordnet werden. Dabei handelt es sich um eine m:n-Beziehung.

Die häufigsten Szenarien für Datei Kontexte beziehen sich auf die Dienste Build, Debug und Language. Weitere Informationen finden Sie in den anderen Themen im Zusammenhang mit diesen Szenarien.

## <a name="file-context-lifecycle"></a>Datei Kontext Lebenszyklus

Lebenszyklen für einen `FileContext` sind nicht deterministisch. Eine Komponente kann jederzeit eine Reihe von Kontext Typen asynchron anfordern. Anbieter, die eine Teilmenge der Anforderungs Kontext Typen unterstützen, werden abgefragt. Die `IWorkspace` -Instanz fungiert als mittlerer Mann zwischen dem Consumer und den Anbietern durch die- <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> Methode. Consumer könnten einen Kontext anfordern und eine kurzfristige Maßnahme basierend auf dem Kontext ausführen, während andere einen Kontext anfordern und einen lang gelebten Verweis verwalten können.

Möglicherweise treten Änderungen an Dateien auf, die bewirken, dass ein Datei Kontext veraltet ist. Der Anbieter kann ein Ereignis auf dem Auslösen `FileContext` , um Consumer über Updates zu benachrichtigen. Wenn z. b. ein Buildkontext für eine Datei bereitgestellt wird, aber eine Änderung auf dem Datenträger diesen Kontext ungültig macht, kann der ursprüngliche Producer das Ereignis aufrufen. Alle Verbraucher, die noch auf Sie verweisen, `FileContext` können dann für einen neuen anfordert `FileContext` .

>[!NOTE]
>Es gibt kein Push-Modell für Consumer. Consumer werden nach Ihrer Anforderung nicht über den neuen eines Anbieters benachrichtigt `FileContext` .

## <a name="expensive-file-context-computations"></a>Teure Datei Kontext Berechnungen

Das Lesen von Dateiinhalten von einem Datenträger kann teuer sein, insbesondere dann, wenn ein Anbieter die Beziehung zwischen Dateien auflösen muss. Ein Anbieter kann z. b. für den Datei Kontext einer Quelldatei abgefragt werden, aber der Datei Kontext hängt von den Metadaten aus einer Projektdatei ab. Die Projektdatei zu analysieren oder mit MSBuild zu evaluieren, ist aufwendig. Stattdessen kann die Erweiterung einen exportieren `IFileScanner` , um `FileDataValue` während der Arbeitsbereichs Indizierung Daten zu erstellen. Wenn Sie nun nach Datei Kontexten gefragt werden, kann die die `IFileContextProvider` indizierten Daten schnell Abfragen. Weitere Informationen zur Indizierung finden Sie im Thema [Arbeitsbereichs Indizierung](workspace-indexing.md) .

>[!WARNING]
>Seien Sie vorsichtig bei anderen Möglichkeiten `FileContext` , um Ihre computekapazität zu berechnen. Einige Interaktionen mit der Benutzeroberfläche sind synchron und basieren auf einer hohen Anzahl von `FileContext` Anforderungen. Beispiele hierfür sind das Öffnen einer Editor-Registerkarte und das Öffnen eines **Projektmappen-Explorer** Kontextmenüs. Durch diese Aktionen werden viele buildkontexttyp Anforderungen erstellt.

## <a name="file-context-related-apis"></a>Mit dem Datei Kontext verbundene APIs

- <xref:Microsoft.VisualStudio.Workspace.FileContext> enthält Daten und Metadaten.
- <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider> und <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider`1> Erstellen Sie den Datei Kontext.
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextProviderAttribute> exportiert einen Datei Kontext Anbieter.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> wird verwendet, damit Consumer Datei Kontexte erhalten.
- <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes> definiert buildkontexttypen, die vom geöffneten Ordner verwendet werden.

## <a name="file-context-actions"></a>Datei Kontext Aktionen

Ein `FileContext` selbst ist nur Daten über einige Dateien, eine <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> Möglichkeit, diese Daten auszudrücken und darauf zu reagieren. `IFileContextAction` ist in seiner Verwendung flexibel. Zwei der häufigsten Fälle sind das entwickeln und Debuggen.

## <a name="reporting-progress"></a>Melden des Status

Die <xref:Microsoft.VisualStudio.Workspace.IFileContextActionBase.ExecuteAsync%2A> Methode wird erfolgreich durchgeführt `IProgress<IFileContextActionProgressUpdate>` , aber das Argument sollte nicht als dieser Typ verwendet werden. `IFileContextActionProgressUpdate` ist eine leere Schnittstelle, und der Aufruf von löst `IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)` möglicherweise aus `NotImplementedException` . Stattdessen muss das- `IFileContextAction` Argument in einen anderen Typ umwandeln, wenn dies für das Szenario notwendig ist.

Informationen zu den Typen, die von Visual Studio bereitgestellt werden, finden Sie in der Dokumentation des jeweiligen Szenarios.

## <a name="file-context-action-related-apis"></a>Mit Datei Kontext Aktionen verbundene APIs

- <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> führt ein gewisses Verhalten auf Grundlage eines aus `FileContext` .
- <xref:Microsoft.VisualStudio.Workspace.IFileContextActionProvider> erstellt Instanzen von `IFileContextAction` .
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextActionProviderAttribute> exportiert den Typ `IWorkspaceProviderFactory<IFileContextActionProvider>` .

## <a name="file-watching"></a>Dateiüberwachung

Ein Arbeitsbereich lauscht auf Datei Änderungs Benachrichtigungen und stellt die <xref:Microsoft.VisualStudio.Workspace.IFileWatcherService> via bereit <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A> . Dateien, die mit der Einstellung "ExcludedItems" übereinstimmen, führen keine Datei Benachrichtigungs Ereignisse aus. Ein Schwellenwert zwischen Ereignissen wird für Benachrichtigungs Vereinfachung und doppelte Reduzierung verwendet. Wenn Sie auf eine Datei Änderung reagieren müssen, sollten Sie diesen Dienst abonnieren.

>[!TIP]
>Der [Indizierungs Dienst](workspace-indexing.md) eines Arbeitsbereichs abonniert Datei Ereignisse standardmäßig. Datei Ergänzungen und-Änderungen bewirken, `IFileScanner` dass relevante s-Ereignisse für neue Daten für diese Datei aufgerufen werden. Durch Datei Löschungen werden indizierte Daten entfernt. Sie müssen `IFileScanner` den Datei-watcherdienst nicht abonnieren.

## <a name="next-steps"></a>Nächste Schritte

* [Indizierung](workspace-indexing.md) : die Arbeitsbereichs Indizierung sammelt und speichert Informationen über den Arbeitsbereich.
* [Arbeitsbereiche](workspaces.md) : Überprüfen Sie die Arbeitsbereichs Konzepte und die Einstellungs Speicherung.
