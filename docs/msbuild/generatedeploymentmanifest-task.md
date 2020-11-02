---
title: GenerateDeploymentManifest-Aufgabe | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie die MSBuild-Aufgabe „GenerateDeploymentManifest“ verwenden, um ein ClickOnce-Bereitstellungsmanifest zu generieren.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GenerateDeploymentManifest
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateDeploymentManifest task
- GenerateDeploymentManifest task [MSBuild]
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 68a35804a1523b3387061b4666cd483a9c3b0476
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436460"
---
# <a name="generatedeploymentmanifest-task"></a>GenerateDeploymentManifest-Aufgabe

Generiert ein ClickOnce-Bereitstellungsmanifest. Ein ClickOnce-Bereitstellungsmanifest beschreibt die Bereitstellung einer Anwendung, indem eine eindeutige Identität für die Bereitstellung definiert wird, Merkmale der Bereitstellung wie Installations- oder Onlinemodus angegeben werden, Einstellungen für Anwendungsupdates und Updatepfade festgelegt werden und das entsprechende ClickOnce-Anwendungsmanifest angegeben wird.

## <a name="parameters"></a>Parameter

In der folgenden Tabelle werden die Parameter für die `GenerateDeploymentManifest`-Aufgabe beschrieben.

| Parameter | Beschreibung |
|--------------------------| - |
| `AssemblyName` | Optionaler `String`-Parameter.<br /><br /> Gibt das `Name`-Feld der Assemblyidentität für das generierte Manifest an. Wenn dieser Parameter nicht angegeben wird, wird der Name vom `EntryPoint`-Parameter oder `InputManifest`-Parameter abgeleitet. Wenn der Name nicht abgeleitet werden kann, löst die Aufgabe einen Fehler aus. |
| `AssemblyVersion` | Optionaler `String`-Parameter.<br /><br /> Gibt das `Version`-Feld der Assemblyidentität für das generierte Manifest an. Wenn dieser Parameter nicht angegeben wird, verwendet die Aufgabe den Wert „1.0.0.0“. |
| `CreateDesktopShortcut` | Optionaler `Boolean`-Parameter.<br /><br /> Wenn "true", wird während der Installation der ClickOnce-Anwendung ein Symbol auf dem Desktop erstellt. |
| `DeploymentUrl` | Optionaler `String`-Parameter.<br /><br /> Gibt den Updatepfad der Anwendung an. Wenn dieser Parameter nicht angegeben wird, wird kein Updatepfad für die Anwendung definiert. Weist der `UpdateEnabled`-Parameter jedoch den Wert `true` auf, muss der Updatepfad angegeben werden. Der angegebene Wert muss eine vollqualifizierte URL oder ein UNC-Pfad sein. |
| `Description` | Optionaler `String`-Parameter.<br /><br /> Gibt eine optionale Beschreibung der Anwendung an. |
| `DisallowUrlActivation` | Optionaler `Boolean`-Parameter.<br /><br /> Gibt an, ob die Anwendung automatisch ausgeführt werden soll, wenn sie über eine URL geöffnet wird. Wenn dieser Parameter den Wert `true` aufweist, kann die Anwendung nur über das **Startmenü** gestartet werden. Der Standardwert dieses Parameters ist `false`. Diese Eingabe ist nur gültig, wenn der Wert des `Install`-Parameters `true` ist. |
| `EntryPoint` | Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Gibt den Einstiegspunkt für die generierte Manifestassembly an. Bei einem ClickOnce-Bereitstellungsmanifest gibt diese Eingabe das ClickOnce-Anwendungsmanifest an.<br /><br />Wenn der Taskparameter `EntryPoint` nicht angegeben ist, wird das `<customHostSpecified>`-Tag als untergeordnetes Element des `<entryPoint>`-Tags eingefügt. Beispiel:<br /><br /> `<entryPoint xmlns="urn:schemas-microsoft-com:asm.v2">`<br /><br /> `<co.v1:customHostSpecified />`<br /><br /> `</entryPoint>`<br /><br /> Sie können dem Anwendungsmanifest DLL-Abhängigkeiten hinzufügen, indem Sie die folgenden Schritte ausführen:<br /><br /> 1.  Lösen Sie die Verweise der Assembly mit einem Aufruf von <xref:Microsoft.Build.Tasks.ResolveAssemblyReference> auf.<br />2.  Übergeben Sie die Ausgabe der vorherigen Aufgabe und die Assembly selbst an <xref:Microsoft.Build.Tasks.ResolveManifestFiles>.<br />3.  Übergeben Sie die Abhängigkeiten über den `Dependencies`-Parameter an <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>. |
| `ErrorReportUrl` | Optionaler <xref:System.String?displayProperty=fullName>-Parameter.<br /><br /> Gibt die URL der Webseite an, die während der ClickOnce-Installationen in den Dialogfeldern angezeigt wird. |
| `InputManifest` | Optionaler <xref:Microsoft.Build.Framework.ITaskItem>-Parameter.<br /><br /> Gibt ein Eingabe-XML-Dokument an, das als Basis für den Manifestgenerator dienen soll. Dadurch können strukturierte Daten im Ausgabemanifest dargestellt werden, beispielsweise benutzerdefinierte Manifestdefinitionen. Das Stammelement im XML-Dokument muss ein Assemblyknoten im "asmv1"-Namespace sein. |
| `Install` | Optionaler `Boolean`-Parameter.<br /><br /> Gibt an, ob die Anwendung eine installierte Anwendung oder eine reine Onlineanwendung ist. Wenn dieser Parameter den Wert `true` aufweist, wird die Anwendung im **Startmenü** des Benutzers installiert und kann über das Dialogfeld **Software** entfernt werden. Weist dieser Parameter den Wert `false` auf, ist die Anwendung zur Onlineverwendung von einer Webseite bestimmt. Der Standardwert dieses Parameters ist `true`. |
| `MapFileExtensions` | Optionaler `Boolean`-Parameter.<br /><br /> Gibt an, ob die Zuordnung für die Erweiterung *.deploy* verwendet wird. Wenn dieser Parameter den Wert `true` aufweist, wird jede Programmdatei mit der Erweiterung *.deploy* veröffentlicht. Diese Option verbessert die Webserversicherheit, weil mit ihr die Anzahl von Dateinamenerweiterungen begrenzt werden kann, deren Blockierung aufgehoben werden muss, um die ClickOnce-Anwendungsbereitstellung zu aktivieren. Der Standardwert dieses Parameters ist `false`. |
| `MaxTargetPath` | Optionaler `String`-Parameter.<br /><br /> Gibt die maximal zulässige Länge eines Dateipfads in einer ClickOnce-Anwendungsbereitstellung an. Wenn dieser Parameter angegeben wird, wird die Länge jedes Dateipfads in der Anwendung mit dem Grenzwert verglichen. Alle Elemente, die den Grenzwert übersteigen, lösen eine Buildwarnung aus. Wenn dieser Parameter nicht angegeben wird oder den Wert 0 (Null) hat, wird keine Prüfung ausgeführt. |
| `MinimumRequiredVersion` | Optionaler `String`-Parameter.<br /><br /> Gibt an, ob der Benutzer das Update überspringen kann. Wenn der Benutzer nicht mindestens über die erforderliche Version verfügt, steht die Option zum Überspringen des Updates nicht zur Verfügung. Diese Eingabe ist nur gültig, wenn der Wert des `Install`-Parameters `true` ist. |
| `OutputManifest` | Optionaler <xref:Microsoft.Build.Framework.ITaskItem>-Parameter.<br /><br /> Gibt den Namen der generierten Ausgabemanifestdatei an. Wenn dieser Parameter nicht angegeben wird, wird der Name der Ausgabedatei von der Identität des generierten Manifests abgeleitet. |
| `Platform` | Optionaler `String`-Parameter.<br /><br /> Gibt die Zielplattform für die Anwendung an. Dieser Parameter kann die folgenden Werte aufweisen:<br /><br /> -   `AnyCPU`<br />-   `x86`<br />-   `x64`<br />-   `Itanium`<br /><br /> Der Standardwert ist `AnyCPU`. |
| `Product` | Optionaler `String`-Parameter.<br /><br /> Gibt den Namen der Anwendung an. Wenn dieser Parameter nicht angegeben wird, wird der Name von der Identität des generierten Manifests abgeleitet. Dieser Name wird für die Verknüpfung im **Startmenü** verwendet und ist Teil des Namens, der im Dialogfeld **Software** angezeigt wird. |
| `Publisher` | Optionaler `String`-Parameter.<br /><br /> Gibt den Herausgeber der Anwendung an. Wenn dieser Parameter nicht angegeben ist, wird der Name vom registrierten Benutzer oder von der Identität des generierten Manifests abgeleitet. Dieser Name wird für den Ordnernamen im **Startmenü** verwendet und ist Teil des Namens, der im Dialogfeld **Software** angezeigt wird. |
| `SuiteNamel` | Optionaler `String`-Parameter.<br /><br /> Gibt den Namen des Ordners im **Startmenü** an, in dem sich die Anwendung nach der ClickOnce-Bereitstellung befindet. |
| `SupportUrl` | Optionaler `String`-Parameter.<br /><br /> Gibt den Link an, der im Dialogfeld **Software** für die Anwendung angezeigt wird. Der angegebene Wert muss eine vollqualifizierte URL oder ein UNC-Pfad sein. |
| `TargetCulture` | Optionaler `String`-Parameter.<br /><br /> Identifiziert die Kultur der Anwendung und gibt das `Language`-Feld der Assemblyidentität für das generierte Manifest an. Wenn dieser Parameter nicht angegeben ist, wird davon ausgegangen, dass die Anwendung kulturinvariant ist. |
| `TrustUrlParameters` | Optionaler `Boolean`-Parameter.<br /><br /> Gibt an, ob URL-Abfragezeichenfolgen-Parameter für die Anwendung verfügbar gemacht werden sollen. Der Standardwert dieses Parameters ist `false`, was bedeutet, dass der Anwendung keine Parameter zur Verfügung stehen. |
| `UpdateEnabled` | Optionaler `Boolean`-Parameter.<br /><br /> Gibt an, ob die Anwendung für Updates aktiviert wird. Der Standardwert dieses Parameters ist `false`. Dieser Parameter ist nur gültig, wenn der Wert des `Install`-Parameters `true` ist. |
| `UpdateInterval` | Optionaler `Int32`-Parameter.<br /><br /> Gibt das Updateintervall für die Anwendung an. Der Standardwert dieses Parameters ist 0 (Null). Dieser Parameter ist nur gültig, wenn sowohl der `Install`-Parameter als auch der `UpdateEnabled`-Parameter den Wert `true` aufweisen. |
| `UpdateMode` | Optionaler `String`-Parameter.<br /><br /> Gibt an, ob vor dem Start der Anwendung im Vordergrund oder nach dem Start der Anwendung im Hintergrund nach Updates gesucht werden soll. Dieser Parameter kann die folgenden Werte aufweisen:<br /><br /> -   `Foreground`<br />-   `Background`<br /><br /> Der Standardwert dieses Parameters ist `Background`. Dieser Parameter ist nur gültig, wenn sowohl der `Install`-Parameter als auch der `UpdateEnabled`-Parameter den Wert `true` aufweisen. |
| `UpdateUnit` | Optionaler `String`-Parameter.<br /><br /> Gibt die Einheiten für den `UpdateInterval`-Parameter an. Dieser Parameter kann die folgenden Werte aufweisen:<br /><br /> -   `Hours`<br />-   `Days`<br />-   `Weeks`<br /><br /> Dieser Parameter ist nur gültig, wenn sowohl der `Install`-Parameter als auch der `UpdateEnabled`-Parameter den Wert `true` aufweisen. |

## <a name="remarks"></a>Hinweise

Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.GenerateManifestBase>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste der Parameter der Aufgabenklasse finden Sie unter [Task-Basisklasse](../msbuild/task-base-class.md).

## <a name="see-also"></a>Weitere Informationen

- [Aufgaben](../msbuild/msbuild-tasks.md)
- [GenerateApplicationManifest-Aufgabe](../msbuild/generateapplicationmanifest-task.md)
- [SignFile-Aufgabe](../msbuild/signfile-task.md)
- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
