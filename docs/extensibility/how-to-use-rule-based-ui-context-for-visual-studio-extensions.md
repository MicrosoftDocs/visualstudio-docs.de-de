---
title: Verwenden des regelbasierten UI-Kontexts für Visual Studio-Erweiterungen
titleSuffix: ''
description: Erfahren Sie, wie Sie regelbasierte UI-Kontexte verwenden, die es Erweiterungs Autoren ermöglichen, Bedingungen zu definieren, wenn ein UI-Kontext aktiviert und VSPackages geladen werden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 8dd2cd1d-d8ba-49b9-870a-45acf3a3259d
author: acangialosi
ms.author: anthc
ms.workload:
- vssdk
ms.openlocfilehash: 41b804d3f7697890773b4b6888bcffa108b7a11b
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2020
ms.locfileid: "96993457"
---
# <a name="how-to-use-rule-based-ui-context-for-visual-studio-extensions"></a>Gewusst wie: Verwenden des regelbasierten UI-Kontexts für Visual Studio-Erweiterungen

Visual Studio ermöglicht das Laden von VSPackages, wenn bestimmte bekannte <xref:Microsoft.VisualStudio.Shell.UIContext> en aktiviert sind. Diese UI-Kontexte sind jedoch nicht fein abgeglichen, wodurch Erweiterungs Autoren nicht ausgewählt werden können, sondern ein verfügbarer UI-Kontext ausgewählt wird, der vor dem Punkt aktiviert wird, an dem das VSPackage wirklich geladen werden soll. Eine Liste der bekannten UI-Kontexte finden Sie unter <xref:Microsoft.VisualStudio.Shell.KnownUIContexts> .

Das Laden von Paketen kann sich negativ auf die Leistung auswirken, und das Laden vor Bedarf ist nicht die bewährte Vorgehensweise. In Visual Studio 2015 wurde das Konzept von regelbasierten UI-Kontexten eingeführt, ein Mechanismus, mit dem Erweiterungs Autoren die genauen Bedingungen definieren können, unter denen ein UI-Kontext aktiviert und zugeordnete VSPackages geladen werden.

## <a name="rule-based-ui-context"></a>Regelbasierter UI-Kontext

Eine "Regel" besteht aus einem neuen UI-Kontext (eine GUID) und einem booleschen Ausdruck, der auf ein oder mehrere "Begriffe" in Kombination mit logischen "and"-, "or"-, "Not"-Vorgängen verweist. "Begriffe" werden zur Laufzeit dynamisch ausgewertet, und der Ausdruck wird immer dann neu ausgewertet, wenn sich Ihre Begriffe ändern. Wenn der Ausdruck zu true ausgewertet wird, wird der zugehörige UI-Kontext aktiviert. Andernfalls wird der UI-Kontext deaktiviert.

Der regelbasierte UI-Kontext kann auf verschiedene Arten verwendet werden:

1. Geben Sie Sichtbarkeits Einschränkungen für Befehle und Tool Fenster an. Sie können die Fenster Befehle/Tools ausblenden, bis die UI-Kontext Regel erfüllt ist.

2. Als Einschränkungen für das automatische Laden: Pakete werden nur dann automatisch geladen, wenn die Regel erfüllt ist.

3. Als verzögerter Task: verzögertes Laden, bis ein angegebenes Intervall verstrichen ist und die Regel noch erfüllt ist.

   Der Mechanismus kann von jeder Visual Studio-Erweiterung verwendet werden.

## <a name="create-a-rule-based-ui-context"></a>Erstellen eines regelbasierten UI-Kontexts
 Angenommen, Sie verfügen über eine Erweiterung namens testpackage, die einen Menübefehl enthält, der nur für Dateien mit der Erweiterung *. config* gilt. Vor VS2015 war die beste Option, testpackage beim Aktivieren des <xref:Microsoft.VisualStudio.Shell.KnownUIContexts.SolutionExistsAndFullyLoadedContext%2A> UI-Kontexts zu laden. Das Laden von testpackage auf diese Weise ist nicht effizient, da die geladene Projekt Mappe möglicherweise nicht einmal eine *. config* -Datei enthält. Diese Schritte zeigen, wie Sie mit dem regelbasierten UI-Kontext einen UI-Kontext nur dann aktivieren können, wenn eine Datei mit der Erweiterung *config* ausgewählt ist, und testpackage laden, wenn dieser UI-Kontext aktiviert ist.

1. Definieren Sie eine neue UIContext-GUID, und fügen Sie der VSPackage <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> -Klasse und hinzu <xref:Microsoft.VisualStudio.Shell.ProvideUIContextRuleAttribute> .

    Nehmen wir beispielsweise an, dass ein neues UIContext "uicontextguid" hinzugefügt werden muss. Die erstellte GUID (Sie können eine GUID erstellen, indem Sie **auf Extras**  >  **Create GUID** klicken) ist "8b40d5e2-5626-42ae-99ef-3dd1eff46e7b". Fügen Sie dann die folgende Deklaration in der Paket Klasse hinzu:

   ```csharp
   public const string UIContextGuid = "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B";
   ```

    Fügen Sie für die Attribute die folgenden Werte hinzu: (Details zu diesen Attributen werden später erläutert.)

   ```csharp
   [ProvideAutoLoad(TestPackage.UIContextGuid)]
   [ProvideUIContextRule(TestPackage.UIContextGuid,
       name: "Test auto load",
       expression: "DotConfig",
       termNames: new[] { "DotConfig" },
       termValues: new[] { "HierSingleSelectionName:.config$" })]
   ```

    Diese Metadaten definieren die neue UIContext-GUID (8b40d5e2-5626-42ae-99ef-3dd1eff46e7b) und einen Ausdruck, der auf einen einzelnen Begriff ("dotconfig") verweist. Der Begriff "dotconfig" wird als "true" ausgewertet, wenn die aktuelle Auswahl in der aktiven Hierarchie einen Namen aufweist, der mit dem Muster des regulären Ausdrucks " \\ . config $" übereinstimmt (endet mit " *. config*"). Der (standardmäßige) Wert definiert einen optionalen Namen für die Regel, die für das Debuggen nützlich ist.

    Die Werte des-Attributs werden dem während der Buildzeit generierten pkgdef hinzugefügt.

2. Fügen Sie in der vsct-Datei für die Befehle von testpackage dem entsprechenden Befehl das Flag "dynamicvisibility" hinzu:

   ```xml
   <CommandFlag>DynamicVisibility</CommandFlag>
   ```

3. Verknüpfen Sie die entsprechenden Befehle im Abschnitt "visibilitäten" von vsct mit der neuen UIContext-GUID, die in #1 definiert ist:

   ```xml
   <VisibilityConstraints>
       <VisibilityItem guid="guidTestPackageCmdSet" id="TestId"  context="UIContextGuid"/>
   </VisibilityConstraints>
   ```

4. Fügen Sie im Abschnitt "Symbole" die Definition von "UIContext" hinzu:

   ```xml
   <GuidSymbol name="UIContextGuid" value="{8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B}" />
   ```

    Nun werden die Kontextmenü Befehle für *\* config* -Dateien nur angezeigt, wenn das ausgewählte Element im Projektmappen-Explorer eine *. config* -Datei ist und das Paket erst geladen wird, wenn einer dieser Befehle ausgewählt ist.

   Verwenden Sie als nächstes einen Debugger, um zu bestätigen, dass das Paket nur geladen wird, wenn Sie es erwarten. So debuggen Sie testpackage:

5. Legen Sie einen Haltepunkt in der- <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> Methode fest.

6. Erstellen Sie das testpackage, und starten Sie das Debugging.

7. Erstellen Sie ein Projekt, oder öffnen Sie ein Projekt.

8. Wählen Sie eine beliebige Datei mit einer anderen Erweiterung als " *. config*" aus. Der Breakpoint sollte nicht gedrückt werden.

9. Wählen Sie die *App.Config* Datei aus.

   Das testpackage lädt und hält am Haltepunkt an.

## <a name="add-more-rules-for-ui-context"></a>Weitere Regeln für den UI-Kontext hinzufügen
 Da es sich bei den UI-Kontextregeln um boolesche Ausdrücke handelt, können Sie eingeschränktere Regeln für einen UI-Kontext hinzufügen. Im obigen UI-Kontext können Sie z. b. angeben, dass die Regel nur angewendet wird, wenn eine Projekt Mappe mit einem Projekt geladen wird. Auf diese Weise werden die Befehle nicht angezeigt, wenn Sie eine *config* -Datei als eigenständige Datei öffnen, nicht als Teil eines Projekts.

```csharp
[ProvideAutoLoad(TestPackage.UIContextGuid)]
[ProvideUIContextRule(TestPackage.UIContextGuid,
    name: "Test auto load",
    expression: "(SingleProject | MultipleProjects) & DotConfig",
    termNames: new[] { "SingleProject", "MultipleProjects","DotConfig" },
    termValues: new[] { VSConstants.UICONTEXT.SolutionHasSingleProject_string , VSConstants.UICONTEXT.SolutionHasMultipleProjects_string , "HierSingleSelectionName:.config$" })]
```

 Nun verweist der Ausdruck auf drei Begriffe. Die ersten beiden Begriffe "singleproject" und "multipleprojects" beziehen sich auf andere bekannte UI-Kontexte (durch Ihre GUIDs). Der dritte Begriff "dotconfig" ist der regelbasierte UI-Kontext, der weiter oben in diesem Artikel definiert wurde.

## <a name="delayed-activation"></a>Verzögerte Aktivierung
 Regeln können eine optionale "Verzögerung" aufweisen. Die Verzögerung wird in Millisekunden angegeben. Falls vorhanden, bewirkt die Verzögerung, dass die Aktivierung oder Deaktivierung des UI-Kontexts einer Regel durch dieses Zeitintervall verzögert wird. Wenn sich die Regel vor dem Verzögerungs Intervall ändert, geschieht nichts. Dieser Mechanismus kann verwendet werden, um Initialisierungs Schritte zu "Staffeln". Dies gilt insbesondere für die einmalige Initialisierung ohne Verwendung von Timern oder die Registrierung für Leerlauf Benachrichtigungen.

 Beispielsweise können Sie für die Test Last Regel eine Verzögerung von 100 Millisekunden angeben:

```csharp
[ProvideAutoLoad(TestPackage.UIContextGuid)]
[ProvideUIContextRule(TestPackage.UIContextGuid,
    name: "Test auto load",
    expression: "DotConfig",
    termNames: new[] { "DotConfig" },
    termValues: new[] { "HierSingleSelectionName:.config$" },
    delay: 100)]
```

## <a name="term-types"></a>Begriffs Typen

Hier sind die verschiedenen Typen von Begriffs, die unterstützt werden:

|Begriff|BESCHREIBUNG|
|-|-|
|{nnnnnnnn-nnnn-nnnn-nnnn-nnnnnnnnnnnn}|Der GUID bezieht sich auf einen UI-Kontext. Der Begriff ist "true", wenn der UI-Kontext aktiv ist, andernfalls "false".|
|Hiersingleselectionname:\<pattern>|Der Begriff ist true, wenn es sich bei der Auswahl in der aktiven Hierarchie um ein einzelnes Element handelt und der Name des ausgewählten Elements mit dem regulären .net-Ausdruck übereinstimmt, der von "Pattern" angegeben wird.|
|Usersettingsstorequery:\<query>|"Query" stellt einen vollständigen Pfad zum Benutzer Einstellungs Speicher dar, der zu einem Wert ungleich 0 (null) ausgewertet werden muss. Die Abfrage wird im letzten Schrägstrich in eine "Collection" und "PropertyName" aufgeteilt.|
|Configsettingsstorequery:\<query>|"Query" stellt einen vollständigen Pfad zum Konfigurations Einstellungs Speicher dar, der zu einem Wert ungleich 0 (null) ausgewertet werden muss. Die Abfrage wird im letzten Schrägstrich in eine "Collection" und "PropertyName" aufgeteilt.|
|Activeprojectflavor:\<projectTypeGuid>|Der Begriff ist "true", wenn das aktuell ausgewählte Projekt (aggregiert) und eine mit der angegebenen Projekttyp-GUID übereinstimmende Konfiguration verwendet wird.|
|Activeeditor ContentType:\<contentType>|Der Begriff ist true, wenn es sich bei dem ausgewählten Dokument um einen Text-Editor mit dem angegebenen Inhaltstyp handelt. Hinweis: Wenn das ausgewählte Dokument umbenannt wird, wird dieser Begriff erst aktualisiert, wenn die Datei geschlossen und wieder geöffnet wurde.|
|Activeprojectcapability:\<Expression>|Der Begriff ist "true", wenn aktive Projektfunktionen dem bereitgestellten Ausdruck entsprechen. Ein Ausdruck kann in etwa vb &#124; CSharp sein.|
|Solutionhasprojectcapability:\<Expression>|Ähnlich wie oben, aber Term ist true, wenn die Projekt Mappe über ein geladenes Projekt verfügt, das mit dem Ausdruck übereinstimmt.|
|Solutionhasprojectflavor:\<projectTypeGuid>|Der Begriff ist "true", wenn eine Projekt Mappe über ein Projekt verfügt, das mit dem angegebenen Projekttyp-GUID übereinstimmt.|
|Projectaddeditem:\<pattern>| Der Begriff ist "true", wenn eine Datei, die mit "Pattern" übereinstimmt, einem Projekt in der geöffneten projektmappenlösung hinzugefügt wird.|
|Activeprojectoutputtype:\<outputType>|Der Begriff ist true, wenn der Ausgabetyp für das aktive Projekt genau übereinstimmt.  Der OutputType kann eine ganze Zahl oder ein- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROJOUTPUTTYPE> Typ sein.|
|Activeprojectbuildproperty:\<buildProperty>=\<regex>|Der Begriff ist "true", wenn das aktive Projekt die angegebene Buildeigenschaft und den Eigenschafts Wert mit dem angegebenen Regex-Filter übereinstimmt. Weitere Informationen zu Buildeigenschaften finden Sie unter [persistente Daten in MSBuild-Projektdateien](internals/persisting-data-in-the-msbuild-project-file.md) .|
|Solutionhasprojectbuildproperty:\<buildProperty>=\<regex>|Der Begriff ist true, wenn die Projekt Mappe ein geladenes Projekt mit der angegebenen Buildeigenschaft und dem angegebenen Eigenschafts Wert mit dem angegebenen Regex-Filter aufweist.|

## <a name="compatibility-with-cross-version-extension"></a>Kompatibilität mit Versions übergreifenden Erweiterungen

Regelbasierte UI-Kontexte sind ein neues Feature in Visual Studio 2015 und werden nicht in frühere Versionen portiert. Wenn Sie nicht auf frühere Versionen portieren, wird ein Problem mit Erweiterungen/Paketen verursacht, die mehrere Versionen von Visual Studio als Ziel haben. Diese Versionen müssten in Visual Studio 2013 und früher automatisch geladen werden, können jedoch von regelbasierten UI-Kontexten profitieren, um zu verhindern, dass Sie automatisch in Visual Studio 2015 geladen werden.

Um solche Pakete zu unterstützen, können die autoloadpackages-Einträge in der Registrierung nun ein Flag in Ihrem Wertfeld bereitstellen, um anzugeben, dass der Eintrag in Visual Studio 2015 und höher ausgelassen werden soll. Hierzu können Sie eine Flags-Option hinzufügen <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags> . VSPackages können jetzt die Option **skip\uicontextrulesactive** zu Ihrem <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> Attribut hinzufügen, um anzugeben, dass der Eintrag in Visual Studio 2015 und höher ignoriert werden soll.
## <a name="extensible-ui-context-rules"></a>Erweiterbare UI-Kontextregeln

Manchmal können Pakete keine statischen UI-Kontextregeln verwenden. Angenommen, Sie haben ein Paket, das Erweiterbarkeit unterstützt, sodass der Befehls Zustand auf Editor-Typen basiert, die von importierten MEF-Anbietern unterstützt werden. Der Befehl ist aktiviert, wenn eine Erweiterung vorhanden ist, die den aktuellen Typ der Bearbeitung unterstützt. In solchen Fällen kann das Paket selbst keine statische UI-Kontext Regel verwenden, da sich die Bedingungen abhängig davon ändern, welche MEF-Erweiterungen verfügbar sind.

Um solche Pakete zu unterstützen, unterstützen regelbasierte UI-Kontexte einen hart codierten Ausdruck "*", der angibt, dass alle unten aufgeführten Begriffe mit oder verknüpft werden. Dadurch kann das Master Paket einen bekannten, regelbasierten UI-Kontext definieren und dessen Befehls Zustand mit diesem Kontext verknüpfen. Anschließend kann jede MEF-Erweiterung, die für das Master Paket vorgesehen ist, ihre Begriffe für Editoren hinzufügen, die Sie unterstützt, ohne dass andere Begriffe oder der Master Ausdruck beeinträchtigt

Die <xref:Microsoft.VisualStudio.Shell.ProvideExtensibleUIContextRuleAttribute.%23ctor%2A> konstruktordokumentation zeigt die Syntax für erweiterbare UI-Kontextregeln.
