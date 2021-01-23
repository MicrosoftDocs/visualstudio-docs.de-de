---
title: Application Lifecycle Management (ALM) mit Unity-Apps | Microsoft-Dokumentation
description: Hier erfahren Sie mehr über das Application Lifecycle Management (ALM) mit Unity-Apps. Informieren Sie sich über Agile-Tools sowie die Modellierung, Code, Builds, Tests sowie das Verbessern der Codequalität.
ms.date: 08/21/2018
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: conceptual
ms.assetid: 2dc61e63-9ba2-4c16-b1ad-f46249e576b6
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 3697ac75eb608f6990cb7f8ca976e103f0df8454
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722983"
---
# <a name="devops-with-unity-apps"></a>DevOps mit Unity-Apps

Das Entwickeln von Apps für moderne Plattformen umfasst viele weitere Aktivitäten neben dem Schreiben von Code. Diese als DevOps (Development + Operations) bezeichneten Aktivitäten decken den gesamten Lebenszyklus der App ab. Dazu gehören das Planen und Nachverfolgen der Arbeit, das Entwickeln und Implementieren von Code, das Verwalten eines Quellcoderepositorys, das Ausführen von Builds, das Verwalten von Continuous Integration und Deployment, das Testen (einschließlich Komponententests und Tests der Benutzeroberfläche), das Durchführen verschiedener Formen der Diagnose in Entwicklungs- und Produktionsumgebungen und das Überwachen der App-Leistung und des Benutzerverhaltens in Echtzeit über Telemetrie und Analysen.

Visual Studio bietet zusammen mit Azure DevOps Services und Team Foundation Server eine Vielzahl von DevOps-Funktionen. Viele dieser Funktionen lassen sich auf plattformübergreifende Projekte anwenden, einschließlich mit Unity erstellter Spiele und immersiver graphischer Apps, insbesondere bei Verwendung von C# als Skriptsprache. Da Unity über eine eigene Entwicklungsumgebung und eine eigene Runtime-Engine verfügt, können viele DevOps-Funktionen allerdings nicht so wie bei anderen Arten von Projekten verwendet werden, die in Visual Studio erstellt wurden.

Die folgenden Tabellen geben an, wie DevOps-Features in Visual Studio bei der Arbeit mit Unity angewendet bzw. nicht angewendet werden können. Ausführliche Informationen über die Funktionen selbst finden Sie in der verknüpften Dokumentation.

## <a name="agile-tools"></a>Agile-Tools

Referenzlink: [About Agile tools and Agile project management (Informationen zu Agile-Tools und zur Agile-Projektverwaltung)](/azure/devops/boards/backlogs/backlogs-overview?view=vsts&preserve-view=true) (mit Azure Boards oder TFS, einschließlich Team Explorer Everywhere)

Allgemeiner Kommentar: alle Planungs- und Nachverfolgungsfunktionen sind vom Projekttyp und den Programmiersprachen unabhängig.

|Feature|Unterstützt von Unity|Zusätzliche Kommentare|
|-------------|--------------------------|-------------------------|
|Verwalten von Rückständen und Sprints|Ja||
|Arbeitsüberwachung|Ja||
|Teamraumzusammenarbeit|Ja||
|Kanban-Boards|Ja||
|Berichte und Visualisierung des Fortschritts|Ja||

## <a name="modeling"></a>Modellierung

Referenzlink: **[Analyze and model architecture (Analysieren und Modellieren der Architektur)](/modeling/analyze-and-model-your-architecture.md)**

Allgemeiner Hinweis: Obwohl diese Entwurfsfunktionen entweder unabhängig von der Programmiersprache sind oder mit .NET-Sprachen wie C# funktionieren, beziehen sie sich auf ein traditionelles Anwendungsparadigma mit Objekthierarchien und Klassenbeziehungen. Für das Entwerfen eines Spiels in Unity ist ein anderes Paradigma erforderlich, nämlich die Beziehungen von grafischen Objekten, Sounds, Shadern, Skripts usw. Aus diesem Grund sind die Modellierungsdiagrammtools von Visual Studio für die Gesamtheit eines Unity-Projekts nicht von besonderer Bedeutung. Sie können möglicherweise zum Verwalten von Beziehungen innerhalb von C#-Skripts verwendet werden, aber das ist nur ein Teil des Ganzen.

|Feature|Unterstützt von Unity|Zusätzliche Kommentare|
|-------------|--------------------------|-------------------------|
|Sequenzdiagramme|Nein||
|Abhängigkeitsdiagramme|Nein||
|Aufrufhierarchie|Nein||
|Klassen-Designer|Nein||
|Architektur-Explorer|Nein||
|UML-Diagramme (Anwendungsfall, Aktivität, Klasse, Komponente, Sequenz und DSL)|Nein||
|Ebenendiagramme|Nein||
|Ebenenüberprüfung|Nein||

## <a name="code"></a>Code

|Feature|Unterstützt von Unity|Zusätzliche Kommentare|
|-------------|--------------------------|-------------------------|
|[Verwenden der Team Foundation-Versionskontrolle (TFVC)](/azure/devops/repos/tfvc/overview?view=vsts&preserve-view=true) oder Azure Repos|Ja|Unity-Projekte sind einfach eine Sammlung von Dateien, die wie jedes andere Projekt in Versionskontrollsysteme eingefügt werden können, jedoch gibt es einige spezielle Überlegungen, die nach dieser Tabelle aufgeführt sind.|
|[Erste Schritte mit Git in Azure Repos](/azure/devops/repos/git/gitquickstart?view=vsts&preserve-view=true&tabs=visual-studio)|Ja|Siehe Hinweise nach der Tabelle.|
|[Verbessern der Codequalität](/test/improve-code-quality.md)|Ja||
|[Ermitteln von Änderungen am Code und andere Verläufe](/ide/find-code-changes-and-other-history-with-codelens.md)|Ja||
|[Verwenden von Code Maps zum Debuggen von Anwendungen](/modeling/use-code-maps-to-debug-your-applications.md)|Ja||

Besondere Überlegungen für die Versionskontrolle mit Unity:

1. Unity überwacht Metadaten über Spielressourcen in einer einzelnen, nicht transparenten Bibliothek, die standardmäßig ausgeblendet ist. Damit Dateien und Metadaten synchron bleiben, müssen die Metadaten sichtbar gemacht und in besser verwaltbaren Blöcken gespeichert werden. Weiter Informationen finden Sie unter [Using Version Control System with Unity (Verwenden von Versionskontrollsystemen mit Unity)](https://docs.unity3d.com/Manual/ExternalVersionControlSystemSupport.html) (Unity-Dokumentation).

2. Nicht alle Dateien und Ordner in einem Unity-Projekt eignen sich für die Quellcodeverwaltung, wie auch im obenstehenden Link beschrieben wird. Die Assets- und ProjectSettings-Ordner sollten hinzugefügt werden, nicht aber die Library- und Temp-Ordner. Eine zusätzliche Liste generierter Dateien, die nicht in die Quellcodeverwaltung aufgenommen werden würden, finden Sie unter [How to use Git for Unity3D source control? (So verwenden Sie Git für die Quellcodeverwaltung von Unity3D)](https://stackoverflow.com/questions/18225126/how-to-use-git-for-unity3d-source-control) auf StackOverflow. Viele Entwickler haben zu diesem Thema auch unabhängig Blog-Einträge geschrieben.

3. Binäre Objekte in einem Unity-Projekt, z. B. Texturen oder Audiodateien, können eine große Menge an Speicherplatz belegen. Verschiedene Quellcodeverwaltungssysteme wie Git speichern eine Kopie einer Datei für jede vorgenommene Änderung, auch wenn die Änderung nur einen kleinen Teil der Datei betrifft. Dadurch kann das Git-Repository sehr groß werden. Um dies zu vermeiden, entscheiden sich Unity-Entwickler häufig dafür, nur finale Objekte zu ihrem Repository hinzufügen und den Arbeitsverlauf der Objekte anderweitig zu speichern, etwa mit OneDrive, DropBox oder git-annex. Dieser Ansatz funktioniert, da solche Objekte in der Regel nicht zusammen mit Änderungen am Quellcode mit einer Versionsangabe versehen müssen. Entwickler legen in der Regel auch den Objektserialisierungsmodus des Projekteditors auf das Erzwingen von Text fest, um Szenendateien als Text und nicht im Binärformat zu speichern, wodurch Zusammenführungen in der Quellcodeverwaltung ermöglicht werden. Weitere Informationen finden Sie unter [Editoreinstellungen](https://docs.unity3d.com/Manual/class-EditorManager.html) (Unity-Dokumentation).

## <a name="build"></a>Build

Referenzlink: **[Azure Pipelines](/azure/devops/pipelines/index?view=vsts&preserve-view=true)**

|Feature|Unterstützt von Unity|Zusätzliche Kommentare|
|-------------|--------------------------|-------------------------|
|Lokaler Team Foundation Server (TFS)|Möglich|Unity-Projekte werden über die Unity-Umgebung und nicht über das Visual Studio-Buildsystem erstellt (durch das Erstellen innerhalb der Visual Studio-Tools für Unity kompilieren Sie die Skripts, jedoch wird keine ausführbare Datei erzeugt). Es ist möglich, Unity-Projekte über die Befehlszeile  zu [erstellen (Unity-Dokumentation)](https://docs.unity3d.com/Manual/CommandLineArguments.html). Damit ist es möglich, einen MSBuild-Prozess auf einem TFS-Server zum Ausführen der entsprechenden Unity-Befehle zu konfigurieren, sofern Unity selbst auf diesem Computer installiert ist.<br /><br /> Unity bietet darüber hinaus [Unity Cloud Build](https://build.cloud.unity3d.com/landing/), welches ein Git- oder SVN-Repository überwacht und regelmäßige Builds ausführt. Zurzeit kann dieser Dienst nicht mit TFVC oder Azure DevOps Services verwendet werden.|
|Lokaler Buildserver mit Verbindung zu Azure DevOps Services|Möglich|Unter den obigen Bedingungen ist es zudem möglich, über Azure DevOps Services ausgelöste Builds einen lokalen TFS-Computer verwenden zu lassen. Anweisungen finden Sie unter [Build and release agents (Build- und Release-Agents)](/azure/devops/pipelines/agents/agents?view=vsts&preserve-view=true).|
|Gehosteter Controllerdienst von Azure DevOps Services|Nein|Builds von Unity werden derzeit nicht unterstützt.|
|Builddefinitionen mit Vor- und Nachskripts|Ja|Eine benutzerdefinierte Builddefinition, die einen Build über die Unity-Befehlszeile ausführt, kann ebenfalls für Prä- und Postbuildskripts konfiguriert werden.|
|Fortlaufende Integration einschließlich abgegrenzter Eincheckvorgänge|Ja|Abgegrenzte Eincheckvorgänge für TFVC, nur wenn Git auf einem Pull-Request-Modell statt mit Eincheckvorgängen arbeitet.|

## <a name="test"></a>Test

|Feature|Unterstützt von Unity|Zusätzliche Kommentare|
|-------------|--------------------------|-------------------------|
|Planen von Tests, Erstellen von Testfällen und Organisieren von Testauflistungen|Ja||
|Manuelle Tests|Ja||
|Test-Manager (Aufzeichnung und Wiedergabe von Tests)|Nur Windows-Geräte und Android-Emulatoren||
|Codeabdeckung|n/v|Nicht zutreffend, da Komponententests in Unity und nicht in Visual Studio erfolgen (siehe unten).|
|[Ausführen von Komponententests für Code](/test/unit-test-your-code.md)|In Unity, nicht in Visual Studio|Unity bietet ein eigenes Komponententest-Framework als Teil der [Unity-Testtools](https://assetstore.unity.com/packages/tools/utilities/unity-test-tools-13802) (Unity Asset Store). Unit-Testergebnisse werden in Unity gemeldet und nicht in Visual Studio angezeigt.|
|[Verwenden der Benutzeroberflächenautomatisierung zum Testen des Codes](/test/use-ui-automation-to-test-your-code.md)|Nein|Tests der programmieren UI basieren auf lesbaren Steuerelementen in der App-Benutzeroberfläche. Unity-Apps sind grafischer Art, sodass Inhalte nicht von den Tools für Tests der programmierten UI gelesen werden können.|

## <a name="improve-code-quality"></a>Verbessern der Codequalität

Referenzlink: **[Improve code quality (Verbessern der Codequalität)](/test/improve-code-quality.md)**

|Feature|Unterstützt von Unity|Zusätzliche Kommentare|
|-------------|--------------------------|-------------------------|
|[Analysieren der Qualität von verwaltetem Code](/code-quality/code-analysis-for-managed-code-overview.md)|Ja|Kann den C#-Skriptcode in Visual Studio analysieren.|
|[Suchen von doppeltem Code mit der Codeklonerkennung](https://msdn.microsoft.com/library/hh205279.aspx)|Ja|Kann den C#-Skriptcode in Visual Studio analysieren.|
|[Messen von Komplexität und Verwaltbarkeit verwalteten Codes](/code-quality/code-metrics-values.md)|Ja|Kann den C#-Skriptcode in Visual Studio analysieren.|
|[Leistungstools](/profiling/performance-explorer.md)|Nein|Verwenden des [Unity Profiler](https://docs.unity3d.com/Manual/Profiler.html) (Unity-Website).|
|[Analysieren von .NET Framework-Arbeitsspeicherproblemen](https://msdn.microsoft.com/library/dn342825.aspx)|Nein|Visual Studio-Tools haben keinen Zugriff auf das Mono-Framework (wie von Unity verwendet) für die Profilerstellung. Verwenden des [Unity Profiler](http://docs.unity3d.com/Manual/Profiler.html) (Unity-Dokumentation).|

## <a name="release-management"></a>Release Management:

Referenzlink: [Build and release in Azure Pipelines and TFS (Build und Release in Azure Pipelines und TFS)](/azure/devops/pipelines/overview?view=vsts&preserve-view=true)

|Feature|Unterstützt von Unity|Zusätzliche Kommentare|
|-------------|--------------------------|-------------------------|
|Verwalten von Releaseprozessen|Ja||
|Bereitstellen auf Servern für das Sideloading über Skripts|Ja||
|Hochladen in den App Store|Partial|Es stehen Erweiterungen zur Verfügung, die diesen Prozess für manche App-Stores automatisieren können. Ein Übersicht finden Sie unter [Extensions for Azure DevOps Services (Erweiterungen für Azure DevOps Services)](https://marketplace.visualstudio.com/VSTS). Dort ist beispielsweise die [Erweiterung für Google Play](https://marketplace.visualstudio.com/items?itemName=ms-vsclient.google-play) erhältlich.|

## <a name="monitor-with-hockeyapp"></a>Überwachen mit HockeyApp

Referenzlink: **[Monitor with HockeyApp (Überwachen mit HockeyApp)](https://www.hockeyapp.net/features/)**

|Feature|Unterstützt von Unity|Zusätzliche Kommentare|
|-------------|--------------------------|-------------------------|
|Absturzanalysen, Telemetrie und Betaverteilung|Ja|HockeyApp wird hauptsächlich für das Verarbeiten und Abrufen Absturzberichte verwendet.<br /><br /> Für die Telemetrie von C#-Skripts kann ein Analytics-Framework verwendet werden, vorausgesetzt, dass es auf der von Unity verwendeten Version von .NET ausgeführt wird. Dies ermöglicht allerdings lediglich Analysen in Spieleskripts und nicht tiefer in der Unity-Engine. Im Moment gibt es kein Plug-In für Application Insights; es stehen jedoch Plug-Ins für andere Analyselösungen wie etwa [Unity Analytics](https://assetstore.unity.com/packages/add-ons/services/analytics/unity-analytics-28120) und [Google Analytics](https://github.com/googleanalytics/google-analytics-plugin-for-unity) zur Verfügung. Dienste wie Unity Analytics, die die Art eines Unity-Projekts verstehen, liefern natürlich deutlich aussagekräftigere Analysen als generische Frameworks.|