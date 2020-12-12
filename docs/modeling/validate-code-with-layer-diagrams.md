---
title: Überprüfen von Code mit Abhängigkeitsdiagrammen
description: Um sicherzustellen, dass der Code nicht mit dem Entwurf in Konflikt steht, sollten Sie den Code mit Abhängigkeits Diagrammen in Visual Studio validieren.
ms.custom: SEO-VS-2020
ms.date: 09/28/2018
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, validating
- validation, dependency diagrams
- validation, code
- code exploration, validating
- architecture, validating
- Visual Studio Ultimate, validating code
- validation, architecture
- validation, dependencies
- MSBuild, tasks
- MSBuild, dependency diagrams
- MSBuild, validating code
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bc8b36768cbac4249b964b167988119b5700d5c7
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2020
ms.locfileid: "97362547"
---
# <a name="validate-code-with-dependency-diagrams"></a>Überprüfen von Code mit Abhängigkeitsdiagrammen

## <a name="why-use-dependency-diagrams"></a>Gründe für die Verwendung von Abhängigkeits Diagrammen

Überprüfen Sie den Code mit Abhängigkeits Diagrammen in Visual Studio, um sicherzustellen, dass der Code nicht mit dem Entwurf in Konflikt steht. Dadurch wird Folgendes ermöglicht:

- Findet Konflikte zwischen Abhängigkeiten im Code und Abhängigkeiten im Abhängigkeits Diagramm.

- Ermitteln von Abhängigkeiten, die möglicherweise von vorgeschlagenen Änderungen betroffen sind

   Beispielsweise können Sie das Abhängigkeits Diagramm bearbeiten, um potenzielle Architektur Änderungen anzuzeigen, und dann den Code validieren, um die betroffenen Abhängigkeiten anzuzeigen.

- Umgestalten oder Migrieren von Code in einen anderen Entwurf

   Ermitteln von Code oder Abhängigkeiten, die bei der Umstellung des Codes auf eine andere Architektur noch bearbeitet werden müssen

**Anforderungen**

- Visual Studio

  Um ein Abhängigkeits Diagramm für ein .net Core-Projekt zu erstellen, müssen Sie über Visual Studio 2019 Version 16,2 oder höher verfügen.

- Eine Projekt Mappe mit einem Modellierungsprojekt mit einem Abhängigkeits Diagramm. Dieses Abhängigkeits Diagramm muss mit Artefakten in c# oder Visual Basic Projekten verknüpft werden, die Sie überprüfen möchten. Siehe [Erstellen von Abhängigkeits Diagrammen aus Ihrem Code](../modeling/create-layer-diagrams-from-your-code.md).

Welche Visual Studio-Editionen dieses Feature unterstützen, erfahren Sie unter [Edition-Unterstützung für Architektur- und Modellierungstools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

Sie können Code manuell über ein offenes Abhängigkeits Diagramm in Visual Studio oder über eine Eingabeaufforderung validieren. Sie können Code auch automatisch validieren, wenn Sie lokale Builds oder Azure Pipelines Builds ausführen. Siehe [Channel 9-Video: Entwerfen und validieren ihrer Architektur mithilfe von Abhängigkeits Diagrammen](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Using-layer-diagrams-to-design-and-validate-your-architecture).

> [!IMPORTANT]
> Wenn Sie die ebenenvalidierung mit Team Foundation Server (TFS) ausführen möchten, müssen Sie auch die gleiche Version von Visual Studio auf dem Buildserver installieren.

## <a name="live-dependency-validation"></a>Live-Abhängigkeits Überprüfung

Die Überprüfung der Abhängigkeit erfolgt in Echtzeit, und Fehler werden sofort im **Fehlerliste** angezeigt.

* Die Live Validierung wird für c# und Visual Basic unterstützt.

* Um die vollständige projektmappenanalyse bei Verwendung der Live-Abhängigkeits Überprüfung zu aktivieren, öffnen Sie die Options Einstellungen in der Goldene Leiste, die im **Fehlerliste** angezeigt wird

  - Sie können den Gold-Balken endgültig verwerfen, wenn Sie nicht alle architektonischen Probleme in Ihrer Lösung sehen möchten.
  - Wenn Sie die vollständige projektmappenanalyse nicht aktivieren, wird die Analyse nur für die bearbeiteten Dateien durchgeführt.

* Wenn Sie Projekte aktualisieren, um die Live Validierung zu aktivieren, wird in einem Dialogfeld der Fortschritt der Konvertierung angezeigt.

* Wenn Sie ein Projekt für die Live-Abhängigkeits Validierung aktualisieren, wird die Version des nuget-Pakets auf das gleiche für alle Projekte aktualisiert und ist die höchste verwendete Version.

* Durch das Hinzufügen eines neuen Abhängigkeits Validierungs Projekts wird ein Projekt Update ausgelöst.

## <a name="see-if-an-item-supports-validation"></a>Sehen, ob ein Element die Validierung unterstützt

Sie können Ebenen mit Websites, Office-Dokumenten, nur-Text-Dateien und Dateien in Projekten verknüpfen, die für mehrere apps freigegeben sind. der Überprüfungsprozess enthält diese jedoch nicht. Für Verweise auf Projekte oder Assemblys, die mit separaten Ebenen verknüpft sind, treten keine Validierungsfehler auf, wenn keine Abhängigkeiten zwischen diesen Ebenen angezeigt werden. Solche Verweise werden nur dann als Abhängigkeiten betrachtet, wenn sie im Code verwendet werden.

1. Wählen Sie im Abhängigkeits Diagramm eine oder mehrere Ebenen aus, klicken Sie mit der rechten Maustaste auf Ihre Auswahl, und klicken Sie dann auf **Links anzeigen**.

2. Sehen Sie sich im **ebenenexplorer** die Spalte **unterstützt Validierung** an. Wenn der Wert "false" ist, wird die Überprüfung vom Element nicht unterstützt.

## <a name="include-other-net-assemblies-and-projects-for-validation"></a>Andere .NET-Assemblys und Projekte zur Validierung einschließen

Wenn Sie Elemente in das Abhängigkeits Diagramm ziehen, werden die Verweise auf die entsprechenden .NET-Assemblys oder-Projekte automatisch dem Ordner für **ebenenverweise** im Modellierungsprojekt hinzugefügt. Dieser Ordner enthält Verweise auf die Assemblys und Projekte, die bei der Validierung analysiert werden. Sie können andere .NET-Assemblys und-Projekte zur Validierung hinzufügen, ohne Sie manuell in das Abhängigkeits Diagramm zu ziehen.

1. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf das Modellierungsprojekt oder den Ordner **ebenenverweise** , und klicken Sie dann auf **Verweis hinzufügen**.

2. Wählen Sie im Dialogfeld **Verweis hinzufügen** die Assemblys oder Projekte aus, und klicken Sie dann auf **OK**.

## <a name="validate-code-manually"></a>Code manuell überprüfen

Wenn Sie über ein offenes Abhängigkeits Diagramm verfügen, das mit Projektmappenelementen verknüpft ist, können Sie den Befehl **"Verknüpfung über** prüfen" aus dem Diagramm ausführen. Sie können auch die Eingabeaufforderung verwenden, um den **MSBuild** -Befehl auszuführen, bei dem die benutzerdefinierte Eigenschaft **/p: ValidateArchitecture** auf **true** festgelegt ist. Bei Codeänderungen sollten Sie beispielsweise regelmäßig eine Ebenenvalidierung durchführen, um Abhängigkeitskonflikte frühzeitig lösen zu können.

### <a name="validate-code-from-an-open-dependency-diagram"></a>Überprüfen von Code aus einem geöffneten Abhängigkeits Diagramm

1. Klicken Sie mit der rechten Maustaste auf die Diagramm Oberfläche, und klicken Sie auf **Architektur** überprüfen.

    > [!NOTE]
    > Standardmäßig ist die **Eigenschaft** Buildvorgang für die Abhängigkeits Diagramm Datei (. layerdiagram) auf **Validate** festgelegt, sodass das Diagramm in den Überprüfungsprozess eingeschlossen wird.

     Das **Fehlerliste** Fenster meldet alle auftretenden Fehler. Weitere Informationen zu Validierungs Fehlern finden Sie unter [Beheben von ebenenvalidierungsproblemen](#troubleshoot-layer-validation-issues).

2. Wenn Sie die Quelle der einzelnen Fehler anzeigen möchten, doppelklicken Sie im Fenster **Fehlerliste** auf den Fehler.

    > [!NOTE]
    > Visual Studio zeigt möglicherweise eine Code Map anstelle der Quelle des Fehlers an. Dies tritt auf, wenn der Code eine Abhängigkeit von einer Assembly aufweist, die nicht vom Abhängigkeits Diagramm angegeben wird, oder wenn im Code eine vom Abhängigkeits Diagramm angegebene Abhängigkeit fehlt. Überprüfen Sie die Code Map oder den Code, um festzustellen, ob die Abhängigkeit vorhanden sein sollte. Weitere Informationen zu Code Maps finden Sie unterzuordnen von [Abhängigkeiten in ihren Lösungen](../modeling/map-dependencies-across-your-solutions.md).

3. Informationen zum Verwalten von Fehlern finden Sie unter [Beheben von ebenenvalidierungs-Fehlern](#resolve-layer-validation-errors)

### <a name="validate-code-at-the-command-prompt"></a>Überprüfen von Code an der Eingabeaufforderung

1. Öffnen Sie die Visual Studio-Eingabeaufforderung.

2. Wählen Sie eine der folgenden Optionen aus:

   - Wenn Sie Code für ein bestimmtes Modellierungsprojekt in der Projekt Mappe überprüfen möchten, führen Sie MSBuild mit der folgenden benutzerdefinierten Eigenschaft aus.

       ```
       msbuild <FilePath+ModelProjectFileName>.modelproj /p:ValidateArchitecture=true
       ```

     - ODER

       Navigieren Sie zu dem Ordner, der die Modellierungsprojekt Datei (. modelproj) und das Abhängigkeits Diagramm enthält, und führen Sie dann MSBuild mit der folgenden benutzerdefinierten Eigenschaft aus:

       ```
       msbuild /p:ValidateArchitecture=true
       ```

   - Wenn Sie Code für alle Modellierungs Projekte in der Projekt Mappe überprüfen möchten, führen Sie MSBuild mit der folgenden benutzerdefinierten Eigenschaft aus:

       ```
       msbuild <FilePath+SolutionName>.sln /p:ValidateArchitecture=true
       ```

     - ODER

       Navigieren Sie zum Projektmappenordner, der ein Modellierungsprojekt enthalten muss, das ein Abhängigkeits Diagramm enthält, und führen Sie dann MSBuild mit der folgenden benutzerdefinierten Eigenschaft aus:

       ```
       msbuild /p:ValidateArchitecture=true
       ```

     Alle aufgetretenen Fehler werden aufgelistet. Weitere Informationen zu MSBuild finden Sie unter [MSBuild](../msbuild/msbuild.md) und [MSBuild-Aufgabe](../msbuild/msbuild-task.md).

   Weitere Informationen zu Validierungs Fehlern finden Sie unter [Beheben von ebenenvalidierungsproblemen](#troubleshoot-layer-validation-issues).

### <a name="manage-validation-errors"></a>Validierungsfehler verwalten

Während des Entwicklungsprozesses können Sie ggf. einige der Konflikte unterdrücken, die während der Validierung gemeldet werden. Beispielsweise können Sie Fehler unterdrücken, die Sie bereits behandeln oder die für das spezifische Szenario nicht relevant sind. Wenn Sie einen Fehler unterdrücken, empfiehlt es sich, ein Arbeits Element in Team Foundation zu protokollieren.

> [!WARNING]
> Sie müssen bereits mit der TFS-Quellcodeverwaltung verbunden sein, um ein Arbeitselement zu erstellen oder zu verknüpfen. Wenn Sie versuchen, eine Verbindung mit einer anderen TFS-Quellcodeverwaltung herzustellen, schließt Visual Studio automatisch die aktuelle Projektmappe. Stellen Sie sicher, dass Sie bereits mit der richtigen Quellcodeverwaltung verbunden sind, bevor Sie versuchen, ein Arbeitselement zu erstellen oder zu verknüpfen. In höheren Versionen von Visual Studio stehen die Menübefehle nicht zur Verfügung, wenn Sie mit keiner Quellcodeverwaltung verbunden sind.

#### <a name="create-a-work-item-for-a-validation-error"></a>Erstellen eines Arbeits Elements für einen Validierungs Fehler

- Klicken Sie im **Fehlerliste** Fenster mit der rechten Maustaste auf den Fehler, zeigen Sie auf **Arbeits Element erstellen**, und klicken Sie dann auf den Typ des Arbeits Elements, das Sie erstellen möchten.

Verwenden Sie diese Tasks, um Validierungs Fehler im Fenster **Fehlerliste** zu verwalten:

|**An**|Führen Sie **diese Schritte** aus.|
|-|-|
|Unterdrücken von ausgewählten Fehlern während der Validierung|Klicken Sie mit der rechten Maustaste auf einen oder mehrere ausgewählte Fehler, zeigen Sie auf **Validierungs Fehler verwalten**, und klicken Sie dann auf **Fehler unterdrücken**.<br /><br /> Die unterdrückten Fehler werden durchgestrichen dargestellt. Beim nächsten Ausführen der Validierung werden diese Fehler nicht mehr angezeigt.<br /><br /> Unterdrückte Fehler werden in einer Unterdrückungen-Datei für die entsprechende Abhängigkeits Diagramm Datei nachverfolgt.|
|Beenden der Unterdrückung von ausgewählten Fehlern|Klicken Sie mit der rechten Maustaste auf den ausgewählten Fehler oder Fehler, zeigen Sie auf **Validierungs Fehler verwalten**, und klicken Sie dann auf **Fehler nicht mehr unterdrücken**.<br /><br /> Beim nächsten Ausführen der Validierung werden die ausgewählten unterdrückten Fehler wieder angezeigt.|
|Alle unterdrückten Fehler im Fenster " **Fehlerliste** " Wiederherstellen|Klicken Sie mit der rechten Maustaste auf eine beliebige Stelle im **Fehlerliste** Fenster, zeigen Sie auf **Validierungs Fehler verwalten**, und klicken Sie dann auf **alle unterdrückten Fehler anzeigen**.|
|Alle unterdrückten Fehler im Fenster " **Fehlerliste** " ausblenden|Klicken Sie mit der rechten Maustaste auf eine beliebige Stelle im **Fehlerliste** Fenster, zeigen Sie auf **Validierungs Fehler verwalten**, und klicken Sie dann auf **alle unterdrückten Fehler ausblenden**.|

## <a name="validate-code-automatically"></a>Code automatisch überprüfen

Sie können eine Ebenenvalidierung bei jeder Ausführung eines lokalen Builds durchführen. Wenn das Team Azure devops verwendet, können Sie eine ebenenvalidierung mit abgegrenzten Eincheck Vorgängen durchführen, die Sie angeben können, indem Sie eine benutzerdefinierte MSBuild-Aufgabe erstellen und Validierungs Fehler mithilfe von Buildberichten sammeln. Informationen zum Erstellen von Gated-Check-in-Builds finden Sie unter [tfvc Gated Check-in](/azure/devops/pipelines/build/triggers).

### <a name="to-validate-code-automatically-during-a-local-build"></a>So überprüfen Sie Code automatisch während eines lokalen Builds

Öffnen Sie die Modellierungsprojektdatei (.modelproj) mithilfe eines Text-Editors, und fügen Sie dann die folgende Eigenschaft ein:

```xml
<ValidateArchitecture>true</ValidateArchitecture>
```

\- oder -

1. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf das Modellierungsprojekt, das das Abhängigkeits Diagramm oder die Diagramme enthält, und klicken Sie dann auf **Eigenschaften**.

2. Legen Sie im Fenster **Eigenschaften** die Eigenschaft **Architektur validieren** des Modellierungs Projekts auf **true** fest.

    Dadurch wird das Modellierungsprojekt in den Validierungsprozess eingeschlossen.

3. Klicken Sie in **Projektmappen-Explorer** auf die Abhängigkeits Diagramm Datei (. layerdiagram), die Sie für die Validierung verwenden möchten.

4. Stellen Sie im **Eigenschaften** Fenster sicher, dass **die Eigenschaft Buildvorgang des** Diagramms auf **überprüfen** festgelegt ist.

    Dies schließt das Abhängigkeits Diagramm im Validierungsprozess ein.

Informationen zum Verwalten von Fehlern im Fenster Fehlerliste finden Sie unter [Auflösen von ebenenvalidierungsfehlern](#resolve-layer-validation-errors).

## <a name="troubleshoot-layer-validation-issues"></a>Ebenenvalidierungsprobleme beheben

In der folgenden Tabelle sind Ebenenvalidierungsprobleme und entsprechende Auflösungen aufgeführt. Diese Probleme unterscheiden sich von Fehlern, die das Ergebnis von Konflikten zwischen Code und Entwurf sind. Weitere Informationen zu diesen Fehlern finden Sie unter [Beheben von ebenenvalidierungsproblemen](#troubleshoot-layer-validation-issues).

|**Problem**|**Mögliche Ursache**|**Lösung**|
|-|-|-|
|Validierungsfehler treten nicht wie erwartet auf.|Die Validierung funktioniert nicht in Abhängigkeits Diagrammen, die aus anderen Abhängigkeits Diagrammen in Projektmappen-Explorer kopiert werden und sich im gleichen Modellierungsprojekt befinden. Abhängigkeits Diagramme, die auf diese Weise kopiert werden, enthalten die gleichen Verweise wie das ursprüngliche Abhängigkeits Diagramm.|Fügen Sie dem Modellierungsprojekt ein neues Abhängigkeits Diagramm hinzu.<br /><br /> Kopieren Sie die Elemente aus dem Quell Abhängigkeits Diagramm in das neue Diagramm.|

## <a name="resolve-layer-validation-errors"></a>Auflösen von ebenenvalidierungs-Fehlern

Wenn Sie Code anhand eines Abhängigkeits Diagramms validieren, treten Validierungs Fehler auf, wenn der Code mit dem Entwurf in Konflikt steht. Validierungsfehler können beispielsweise unter folgenden Bedingungen auftreten:

- Ein Artefakt wurde der falschen Ebene zugewiesen. Verschieben Sie in diesem Fall das Artefakt.

- Von einem Artefakt (beispielsweise einer Klasse) wird eine andere Klasse auf eine Weise verwendet, die einen Konflikt mit der Architektur zur Folge hat. Gestalten Sie in diesem Fall den Code um, um die Abhängigkeit zu entfernen.

Aktualisieren Sie zum Beheben dieser Fehler den Code, bis bei der Validierung keine Fehler mehr angezeigt werden. Diese Aufgabe kann iterativ ausgeführt werden.

Im folgenden Abschnitt wird die Syntax beschrieben, die in diesen Fehlern verwendet wird. Außerdem wird die Bedeutung dieser Fehler erläutert, und es werden Vorschläge zur deren Behebung bzw. Verwaltung gegeben.

|**Syntax**|**Beschreibung**|
|-|-|
|*Artifaktn*(*artifakttypen*)|*Artifacetten TN* ist ein Artefakt, das einer Ebene im Abhängigkeits Diagramm zugeordnet ist.<br /><br /> *Artifacttypen* ist der Typ von *artifactn*, z. b. eine **Klasse** oder **Methode**, z. b.:<br /><br /> MySolution.MyProject.MyClass.MyMethod(Method)|
|*NamespaceNameN*|Der Name eines Namespace.|
|*LayerNameN*|Der Name einer Ebene im Abhängigkeits Diagramm.|
|*DependencyType*|Der Typ der Abhängigkeitsbeziehung zwischen *Element1* und *Artifact2*. Beispielsweise hat *Element1* eine Beziehung zum **aufrufen** von *Artifact2*.|

| **Fehlersyntax** | **Fehlerbeschreibung** |
|-|-|
| DV0001: **ungültige Abhängigkeit** | Dieses Problem wird gemeldet, wenn ein Code Element (Namespace, Typ, Member), das einer Ebene zugeordnet ist, auf ein Code Element verweist, das einer anderen Ebene zugeordnet ist. es gibt jedoch keinen Abhängigkeits Pfeil zwischen diesen Ebenen im Abhängigkeits Validierungs Diagramm, das diese Ebenen enthält. Dies ist eine Verletzung der Abhängigkeits Einschränkung. |
| DV1001: **ungültiger Namespace Name** | Dieses Problem wird in einem Code Element gemeldet, das einer Ebene zugeordnet ist, die die Eigenschaft "zulässige Namespace-Namen" nicht den Namespace enthält, in dem dieses Code Element definiert ist. Dies ist eine Verletzung der Benennungs Einschränkung. Beachten Sie, dass die Syntax "zulässige Namespace Namen" eine Semikolons Liste von Namespaces sein muss, in denen Code Elemente, die zugeordnet sind, eine Ebene definiert werden dürfen. |
| DV1002: **Abhängigkeit von nicht referenzierbarem Namespace** | Dieses Problem wird in einem Code Element gemeldet, das einer Ebene zugeordnet ist, und verweist auf ein anderes Code Element, das in einem Namespace definiert ist, der in der Eigenschaft "nicht referenzierbare Namespace" der Ebene definiert ist. Dies ist eine Verletzung der Benennungs Einschränkung. Beachten Sie, dass die Eigenschaft "nicht referenzierbare Namespaces" als eine durch Semikolons getrennte Liste von Namespaces definiert ist, auf die in Code Elementen, die dieser Ebene zugeordnet sind, nicht verwiesen werden soll. |
| DV1003: **unzulässiger Namespace Name** | Dieses Problem wird in einem Code Element gemeldet, das einer Ebene zugeordnet ist, die die Eigenschaft "unzulässige Namespace Namen" enthält den Namespace, in dem dieses Code Element definiert ist. Dies ist eine Verletzung der Benennungs Einschränkung. Beachten Sie, dass die Eigenschaft "unzulässiger Namespace Name" als eine durch Semikolons getrennte Liste von Namespaces definiert ist, in denen Code Elemente, die dieser Ebene zugeordnet sind, nicht definiert werden dürfen. |
| DV2001: **Darstellung des ebenendiagramms** | Dieses Problem wird in einem Projekt gemeldet, das keine Abhängigkeits Diagramm Datei enthält, sondern verweist auf die Analyzers für die Abhängigkeits Überprüfung. Wenn keine Abhängigkeits Validierung verwendet wurde, können Sie "Microsoft. dependencyvalidation. Analyzers" direkt aus Projektmappen-Explorer entfernen oder diese Warnung unterdrücken. Weitere Informationen zum Hinzufügen eines Abhängigkeits Diagramms finden Sie unter [Erstellen von Abhängigkeits Diagrammen aus](../modeling/create-layer-diagrams-from-your-code.md) |
| DV2002: **nicht zugeordnete Typen Basis** | Dieses Problem wird gemeldet, wenn ein Code Element keiner Ebene zugeordnet ist. |
| DV3001: **fehlender Link** | Schicht '*Layername*' ist mit '*artefakt'* verknüpft, das nicht gefunden werden kann. Möglicherweise fehlt ein Assemblyverweis. |
| DV9001: es **wurden interne Fehler bei der Architekturanalyse gefunden** . | Die Ergebnisse sind möglicherweise nicht vollständig. Weitere Informationen finden Sie im ausführlichen Buildereignisprotokoll oder im Ausgabefenster. |

## <a name="see-also"></a>Siehe auch

- [Live-Abhängigkeits Validierung in Visual Studio](https://devblogs.microsoft.com/devops/live-dependency-validation-in-visual-studio-2017/)
- [Überprüfen des Systems während der Entwicklung](../modeling/validate-your-system-during-development.md)
- [Video: Überprüfen der Architekturabhängigkeiten in Echtzeit](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)
