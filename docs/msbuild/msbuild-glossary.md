---
title: MSBuild-Glossar
description: MSBuild-Glossarbegriffe zur Beschreibung der Microsoft-Build-Engine und der zugehörigen Komponenten
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: f767d8e4-24d8-4803-80eb-e857202dbe2c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f42d7945656a3f0e3cfbe11f80db26b7e5c124d3
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93046320"
---
# <a name="msbuild-glossary"></a>MSBuild-Glossar

Mit den folgenden Begriffen werden Microsoft Build Engine (MSBuild) und deren Komponenten beschrieben.

## <a name="glossary"></a>Glossar

AssemblyFoldersEx\
Ein Registrierungsspeicherort, an dem Drittanbieter Pfade für jede Version des Frameworks speichern, das sie unterstützen, und die Entwurfszeitauflösung nach Verweisassemblys suchen kann.

batching\
Batchverarbeitung bedeutet, dass Elemente anhand der Elementmetadaten in als *Batches* bezeichnete Kategorien unterteilt werden, über die anschließend jeweils ein Ziel oder eine Aufgabe ausgeführt wird. Die Batchverarbeitung ist die MSBuild-Entsprechung des Schleifenkonstrukts. Weitere Informationen finden Sie unter [MSBuild Batching (Batchverarbeitung)](../msbuild/msbuild-batching.md).

build-scope\
Der Buildumfang beschreibt ein MSBuild-Objekt, z. B. eine globale Eigenschaft, das für ein Projekt und ggf. für dessen in einem Build mit mehreren Projekten erstellte untergeordnete Projekte potenziell sichtbar ist.

child project\
Siehe *Projekt, untergeordnet*.

condition\
Viele MSBuild-Elemente können bedingt definiert werden, das heißt, im Element wird das `Condition`-Attribut angegeben. Sofern wenn die Bedingung nicht `true` ergibt, wird der Inhalt bedingter Elemente ignoriert. Weitere Informationen finden Sie unter [Conditions](../msbuild/msbuild-conditions.md) (MSBuild-Bedingungen).

definition, item\
Siehe *Elementdefinition*.

emit item\
Während der Ausführungsphase eines Builds können Elemente von Aufgaben erstellt oder geändert werden, die untergeordnete `Output`-Elemente mit dem `ItemName`-Attribut aufweisen. Die Aufgabe gibt die neuen Elemente sozusagen aus.

emit property\
Während der Ausführungsphase eines Builds können Eigenschaften von Aufgaben erstellt oder geändert werden, die untergeordnete `Output`-Elemente mit dem `PropertyName`-Attribut aufweisen. Die Aufgabe gibt die neue Eigenschaft sozusagen aus.

evaluation phase\
Als Auswertung wird die erste Phase eines Projektbuilds bezeichnet. Alle Eigenschaften und Elemente werden in der Reihenfolge ausgewertet, in der sie in der Projektdatei angezeigt werden. Importierte Projekte werden ausgewertet, sobald sie im Projekt gefunden wurden. Ziele und Aufgaben werden erst in der Ausführungsphase ausgeführt, und alle Eigenschaften oder Elemente, die sie deklarieren oder ausgeben würden, werden während der Auswertung ignoriert.

execution phase\
Die Ausführung bildet die zweite Phase eines Projektbuilds. Ausgewählte Ziele werden erstellt, und Aufgaben werden ausgeführt. Eigenschaften und Elemente können erstellt oder im Vergleich zu den zugehörigen Auswertungswerten geändert werden.

function, property\
Siehe *Eigenschaftenfunktion*.

function, item\
Siehe Elementfunktion.

item\
Elemente bilden Eingaben für das Buildsystem und werden auf Grundlage ihrer Elementnamen in Elementtypen gruppiert. Elemente stellen in der Regel Dateien dar. Da Elemente anhand des Elementtyps benannt werden, zu dem sie gehören, können die Begriffe *Element* und *Elementwert* synonym verwendet werden. Weitere Informationen finden Sie unter [Elemente](../msbuild/msbuild-items.md).

definition\
Elementdefinitionsgruppen enthalten Elementdefinitionen, durch die jedem Elementtyp Standardmetadaten hinzugefügt werden. Analog zu bekannten Metadaten sind die Standardmetadaten allen Elementen des angegebenen Elementtyps zugeordnet. Standardmetadaten können in einer Elementdefinition explizit überschrieben werden. Weitere Informationen finden Sie unter [Elementdefinitionen](../msbuild/item-definitions.md).

item function\
Elementfunktionen rufen Informationen über die Elemente im Projekt ab. Diese Funktionen vereinfachen das Abrufen von Distinct()-Elementen, und mit ihnen erfolgt der Abruf schneller als beim Durchlaufen der Elemente. Es gibt Funktionen zum Bearbeiten von Elementpfaden und -zeichenfolgen. Weitere Informationen finden Sie unter [Elementfunktionen](../msbuild/item-functions.md).

item metadata\
Siehe *Metadaten, Element*.

item type\
Elementtypen sind benannte Listen von Elementen, die als Parameter für Aufgaben verwendet werden können. In den Aufgaben werden die Schritte des Buildprozesses mithilfe der Elementwerte ausgeführt. Weitere Informationen finden Sie unter [Elemente](../msbuild/msbuild-items.md).

metadata, item\
Elementmetadaten sind Auflistungen von Name-Wert-Paaren, die einem Element zugeordnet sind. Metadaten enthalten beschreibende Informationen zum Element und sind, außer bei bekannten Metadaten, optional. Weitere Informationen finden Sie unter [Elemente](../msbuild/msbuild-items.md).

metadata, well-known\
Als bekannte Metadaten werden schreibgeschützte Elementmetadaten bezeichnet, die mit einem vordefinierten Wert initialisiert werden. Bekannte Metadaten enthalten beschreibende Informationen zu einem Element, das auf eine Datei verweist. Beispielsweise wird als Wert des bekannten Metadatenelements `FullPath` der vollständige Pfad der Datei verwendet, auf die verwiesen wird. Weitere Informationen finden Sie unter [Elemente](../msbuild/msbuild-items.md).

multitargeting\
Die Fähigkeit eines Anwendungs- oder Assemblyprojekts, auf viele verschiedene CLRs und Frameworks von MSBuild und Visual Studio abzuzielen.

profile\
Eine Teilmenge des vollständigen Frameworks. Dies wird verwendet, um die Menge zu verringern, die auf einen Computer heruntergeladen werden muss.

project file\
Eine Projektdatei enthält das MSBuild-Skript, das den Build steuert. Projektdateien weisen meist eine Erweiterung auf, die mit *proj* endet, z.B. *.csproj* oder *.vbproj*. Von Projektdateien können Eigenschaftendateien und Zieldateien importiert werden.

property\
Eine Eigenschaft besteht aus einem Schlüssel-Wert-Paar, das zum Steuern des Buildprozesses verwendet wird. Weitere Informationen finden Sie unter [MSBuild-Eigenschaften](../msbuild/msbuild-properties.md).

property, environment\
Umgebungseigenschaft wird eine Eigenschaft genannt, die automatisch mit dem Wert einer Systemumgebungsvariable mit demselben Namen initialisiert wird. Weitere Informationen finden Sie unter [MSBuild-Eigenschaften](../msbuild/msbuild-properties.md).

property file\
Als Eigenschaftendatei wird eine Projektdatei bezeichnet, die vor allem Eigenschaftengruppen und Elementgruppen zur Steuerung des Builds enthält. Konventionsgemäß besitzen solche Dateien die Erweiterung *.props*. Eigenschaftendateien werden meist am Anfang zugeordneter Projektdateien importiert.

property, function\
Als Eigenschaftenfunktion wird eine Systemeigenschaft oder -methode bezeichnet, die zum Auswerten von MSBuild-Skripts verwendet werden kann. Mit Eigenschaftenmethoden ist es möglich, die Systemzeit zu lesen, Zeichenfolgen zu vergleichen, nach regulären Ausdrücke zu suchen und weitere Aktionen auszuführen. Weitere Informationen finden Sie unter [Eigenschaftenfunktionen](../msbuild/property-functions.md).

property function, nested\
Eigenschaftenfunktionen können zu komplexeren Funktionen kombiniert werden. Beispiel:

 `$([MSBuild]::BitwiseAnd(32,   $([System.IO.File]::GetAttributes(tempFile))))`

Weitere Informationen finden Sie unter [Eigenschaftenfunktionen](../msbuild/property-functions.md).

property, global\
Eine globale Eigenschaft besteht aus einem Schlüssel-Wert-Paar, das zum Steuern des Buildprozesses verwendet wird. Globale Eigenschaften werden an einer Eingabeaufforderung oder über das `Properties`-Attribut einer [MSBuild-Aufgabe](../msbuild/msbuild-task.md) festgelegt und können während der Auswertungsphase eines Builds nicht geändert werden. Weitere Informationen finden Sie unter [MSBuild-Eigenschaften](../msbuild/msbuild-properties.md).

property, local\
Eine lokale Eigenschaft besteht aus einem Schlüssel-Wert-Paar, das zum Steuern des Buildprozesses verwendet wird. Dieser Begriff wird nur verwendet, um explizit eine Eigenschaft zu bezeichnen, bei der es sich um keine globale Eigenschaft handelt.

property, registry\
Registrierungseigenschaften besitzen einen Wert, der mit einer besonderen Syntax festgelegt wird, die den Wert eines Systemregistrierungsunterschlüssels liest. Weitere Informationen finden Sie unter [MSBuild-Eigenschaften](../msbuild/msbuild-properties.md).

property, reserved\
Eine reservierte Eigenschaft besteht aus einem Schlüssel-Wert-Paar, das zum Steuern des Buildprozesses verwendet wird. Reservierte Eigenschaften werden automatisch mit vordefinierten Werten initialisiert. Weitere Informationen finden Sie unter [MSBuild-Eigenschaften](../msbuild/msbuild-properties.md).

project-scope\
Der Projektumfang beschreibt ein MSBuild-Objekt, z. B. eine lokale Eigenschaft, das nur in der enthaltenden Projektdatei und in allen Projekten sichtbar ist, die von dieser importiert wurden.

project, child\
Ein untergeordnetes Projekt wird während eines Projektbuilds von der MSBuild-Aufgabe erstellt. Dieses neue Projekt ist dem Projekt untergeordnet, das das Ziel mit der MSBuild-Aufgabe enthält oder importiert. Das untergeordnete Projekt erbt die globalen Eigenschaften des übergeordneten Projekts, sofern diese nicht vom `Properties`-Attribut geändert werden.

redist list\
Neuverteilungsliste: die Liste der Assemblys, die einem angegebenen Framework entsprechen.

reference assembly\
Eine Assembly, mit der während der Entwurfszeit eine Anwendung erstellt wird. Von einer Verweisassembly können der tatsächliche Code und die privaten Schnittstellen entfernt und nur die Metadaten und die öffentlichen Schnittstellen beibehalten werden.

registry property\
Siehe *Eigenschaft, Registrierung*.

target\
In einem Ziel werden Aufgaben in einer bestimmten Reihenfolge gruppiert und Abschnitte der Projektdatei als Einstiegspunkte in den Buildprozess verfügbar gemacht. Weitere Informationen finden Sie unter [Ziele](../msbuild/msbuild-targets.md).

target, building\
Siehe Ziel, Ausführen.

target, evaluating\
Aufgrund der inkrementellen Kompilierung müssen Ziele auf potenzielle Änderungen an Eigenschaften und Elementen analysiert werden. Diese Änderungen müssen auch vorgenommen werden, wenn das Ziel übersprungen wurde. Ein Ziel auszuwerten bedeutet, diese Analyse auszuführen und die genannten Änderungen vorzunehmen. Weitere Informationen finden Sie unter [Incremental Builds (Inkrementelle Builds)](../msbuild/incremental-builds.md).

target, executing\
Ein Ziel auszuführen bedeutet, dieses auszuwerten und alle Aufgaben auszuführen, die keine Bedingungen aufweisen oder deren Bedingungen zu true ausgewertet werden. Während der inkrementellen Kompilierung können Ziele übersprungen oder ausgeführt werden, jedoch werden sie werden in jedem Fall ausgewertet. Weitere Informationen finden Sie unter Ziel, Auswerten.

target, running\
Ein Ziel, das eine Bedingung aufweist, die false ergibt, wird nicht ausgeführt (Run) und besitzt daher keine Auswirkungen auf den Build. Ziele, die ausgeführt (Run) werden, werden ausgeführt (Execute) oder aber übersprungen. In jedem Fall wird das Ziel ausgewertet. Weitere Informationen finden Sie unter Ziel, Auswerten.

target, skipping\
Wenn bei der inkrementellen Kompilierung ermittelt wird, dass alle Ausgabedateien aktuell sind, wird das Ziel übersprungen, das heißt, das Ziel wird ausgewertet, jedoch werden die Aufgaben im Ziel nicht ausgeführt. Weitere Informationen finden Sie unter Ziel, Auswerten.

target framework moniker\
Ein Name, der das Framework (z.B. .NET Framework, Silverlight usw.), die Version und das Profil (z.B. Client, Server usw.) beschreibt, die das Ziel darstellen sollen.

targeting pack\
Die Liste der Assemblys, die mit einem angegebenen Framework und dem Satz von Verweisassemblys für dieses Framework verteilt werden sollen.

targets file\
Eine TARGETS-Datei ist eine Projektdatei, die vor allem Ziele und Aufgaben zur Steuerung des Builds enthält. Konventionsgemäß besitzen solche Dateien die Erweiterung *.targets*. TARGETS-Dateien werden meist am Ende zugeordneter Projektdateien importiert.

task\
Aufgaben sind Einheiten ausführbaren Codes, die in MSBuild-Projekten zum Ausführen von Buildvorgängen verwendet werden. Eine Aufgabe kann beispielsweise Eingabedateien kompilieren oder ein externes Tool ausführen. Weitere Informationen finden Sie unter [MSBuild-Aufgaben](../msbuild/msbuild-tasks.md).

transform\
Eine Transformation ist eine 1:1-Konvertierung von einer Elementauflistung in eine andere. Über Transformationen können nicht nur Elementauflistungen in einem Projekt transformiert werden, sondern auch direkte Zuordnungen zwischen Eingaben und Ausgaben eines Ziels identifiziert werden. Weitere Informationen finden Sie unter [Transformationen](../msbuild/msbuild-transforms.md).

well-known metadata\
Siehe *Metadaten, bekannt*.

## <a name="see-also"></a>Weitere Informationen

- [MSBuild](../msbuild/msbuild.md)
