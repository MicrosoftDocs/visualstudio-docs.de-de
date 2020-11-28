---
title: Hinzufügen von Verweisen mit dem Verweis-Manager
description: Erfahren Sie, wie Sie das Dialogfeld „Verweis-Manager“ verwenden, um Verweise auf entwickelte Komponenten hinzuzufügen und zu verwalten.
ms.custom: SEO-VS-2020
ms.date: 08/02/2019
ms.topic: how-to
f1_keywords:
- VS.ReferenceManager
helpviewer_keywords:
- C# projects, references
- references [Visual Studio], adding
- assemblies [Visual Studio], references
- Visual Basic projects, references
- project references, adding
- referencing components, adding references
- project references, removing
- referencing assemblies
- referencing components, removing references
- references [Visual Studio], removing
- referencing components, assemblies not listed
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4884fdc857abd524fa62bb126e7a74af48e9ca88
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/24/2020
ms.locfileid: "95597313"
---
# <a name="how-to-add-or-remove-references-by-using-the-reference-manager"></a>Vorgehensweise: Hinzufügen und Entfernen von Verweisen mit dem Verweis-Manager

Sie können das Dialogfeld „Verweis-Manager“ verwenden, um Verweise auf Komponenten hinzuzufügen und zu verwalten, die von Ihnen, Microsoft oder einem anderen Unternehmen entwickelt wurden. Wenn Sie eine universelle Windows-App entwickeln, verweist das Projekt automatisch auf alle richtigen Windows SDK-DLLs. Wenn Sie eine .NET-Anwendung entwickeln, verweist das Projekt automatisch auf *mscorlib.dll*. Einige .NET-APIs werden in Komponenten verfügbar gemacht, die Sie manuell hinzufügen müssen. Verweise auf COM-Komponenten oder benutzerdefinierte Komponenten müssen manuell hinzugefügt werden.

## <a name="reference-manager-dialog-box"></a>Dialogfeld "Verweis-Manager"

Das Dialogfeld „Verweis-Manager“ zeigt die verschiedenen Kategorien je nach Projekttyp auf der linken Seite an:

- **Assemblys** mit den Untergruppen **Framework** und **Erweiterungen**.

- **COM** listet alle COM-Komponenten auf, die für Verweise verfügbar sind.

- **Projekte**

- **Freigegebene Projekte**

- **Windows** mit den Untergruppen **Core** und **Erweiterungen**. Sie können die Verweise im Windows SDK oder im Erweiterungs-SDK mit dem **Objektkatalog** untersuchen.

- **Durchsuchen** mit der Untergruppe **Aktuell**.
 
    > [!NOTE]
    > Beim Entwickeln von C++-Projekten wird die Option **Durchsuchen** im Dialogfeld „Verweis-Manager“ möglicherweise nicht angezeigt.

## <a name="add-a-reference"></a>Hinzufügen eines Verweises

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Knoten **Verweise** oder den Knoten **Abhängigkeiten**, und klicken Sie dann auf **Verweis hinzufügen**. Klicken Sie mit der rechten Maustaste auf den Projektknoten, und klicken Sie dann auf **Hinzufügen** > **Verweis**.

   Der **Verweis-Manager** wird mit den verfügbaren Verweisen nach Gruppe geöffnet.

2. Geben Sie die hinzuzufügenden Verweise an, und klicken Sie dann auf **OK**.

## <a name="assemblies-tab"></a>Assemblyregisterkarte

Die Registerkarte **Assemblys** führt alle .NET-Assemblys auf, die für Verweise verfügbar sind. Die Registerkarte **Assemblys** führt keine Assemblys aus dem globalen Assemblycache (GAC) auf, da Assemblys im GAC Teil der Laufzeitumgebung sind. Wenn Sie eine Anwendung bereitstellen oder kopieren, die einen Verweis auf eine im globalen Assemblycache registrierte Assembly enthält, wird die Komponente unabhängig von der Einstellung **Lokal kopieren** nicht mit der Anwendung bereitgestellt oder kopiert. Weitere Informationen finden Sie unter [Verwalten von Verweisen in einem Projekt](../ide/managing-references-in-a-project.md).

Wenn Sie einem der EnvDTE-Namespaces (<xref:EnvDTE>, <xref:EnvDTE80>, <xref:EnvDTE90>, <xref:EnvDTE90a> oder <xref:EnvDTE100>) manuell einen Verweis hinzufügen, legen Sie im Fenster **Eigenschaften** die Eigenschaft **Interoptypen einbetten** des Verweises auf **FALSE** fest. Wird diese Eigenschaft auf **TRUE** festgelegt wird, können aufgrund bestimmter EnvDTE-Eigenschaften, die nicht eingebettet werden können, Buildprobleme auftreten.

Alle Desktopprojekte enthalten einen impliziten Verweis auf **mscorlib**. Visual Basic-Projekte enthalten einen impliziten Verweis auf <xref:Microsoft.VisualBasic>. Alle Projekte enthalten einen impliziten Verweis auf **System.Core**. Dies gilt auch, wenn der Eintrag aus der Liste der Verweise entfernt wird.

Wenn ein Projekttyp keine Assemblys unterstützt, wird die Registerkarte nicht im Dialogfeld „Verweis-Manager“ angezeigt.

Die Registerkarte **Assemblys** besteht aus zwei untergeordneten Registerkarten:

1. In **Framework** werden alle Assemblys aufgelistet, die das Zielframework darstellen.

   Für Projekte, die nicht auf .NET Core oder die universelle Windows-Plattform abzielen, listet die Registerkarte **Framework** Assemblys aus dem Zielframework auf. Der Benutzer muss alle Verweise hinzufügen, die für die Anwendung erforderlich sind.

   Universelle Windows-Projekte enthalten standardmäßig Verweise auf alle Assemblys im Zielframework. In verwalteten Projekten gibt ein schreibgeschützter Knoten unter dem Ordner **Verweise** im **Projektmappen-Explorer** den Verweis auf das gesamte Framework an. Entsprechend listet die Registerkarte **Framework** keine der Assemblys aus dem Framework auf und zeigt stattdessen die folgende Meldung an: „All of the Framework assemblies are already referenced. Please use the Object Browser to explore the references in the Framework. (Es wird bereits auf alle Frameworkassemblys verwiesen. Verwenden Sie den Objektkatalog, um Verweise im Framework zu durchsuchen“.

2. Unter **Erweiterungen** werden alle Assemblys aufgelistet, die externe Anbieter von Komponenten und Steuerelementen selbst entwickelt haben, um das Zielframework zu erweitern. Abhängig vom Zweck der Benutzeranwendung sind diese Assemblys gegebenenfalls erforderlich.

   **Erweiterungen** werden ausgefüllt, indem die Assemblys aufgelistet werden, die unter den folgenden Speicherorten registriert sind:

   32-Bit-Computer:
   - `HKEY_CURRENT_USER\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`
   - `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`

   64-Bit-Computer:
   - `HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`
   - `HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`

   Und ältere Versionen des [Zielframeworkbezeichners]

   Wenn ein Projekt .NET Framework 4 als Ziel auf einem 32-Bit-Computer verwendet, listen die **Erweiterungen** Assemblys auf, die unter *\Microsoft\.NETFramework\v4.0\AssemblyFoldersEx*, *\Microsoft\.NETFramework\v3.5\AssemblyFoldersEx*, *\Microsoft\.NETFramework\v3.0\AssemblyFoldersEx* und *\Microsoft\.NETFramework\v2.0\AssemblyFoldersEx* registriert sind.

Einige Komponenten in der Liste werden möglicherweise nicht angezeigt. Dies hängt von der Frameworkversion des Projekts ab. Dieser Fall kann unter den folgenden Bedingungen eintreten:

- Eine Komponente, für die eine aktuelle Frameworkversion verwendet wird, ist nicht kompatibel mit einem Projekt, für das eine frühere Version als Zielversion festgelegt wurde.

   Informationen zum Ändern der Zielversion von Framework für ein Projekt finden Sie unter [Übersicht über Frameworkziele](visual-studio-multi-targeting-overview.md).

- Eine Komponente, für die .NET Framework 4 verwendet wird, ist nicht kompatibel mit einem Projekt, für das als Zielversion .NET Framework 4.5 festgelegt wurde.

Sie sollten keine Dateiverweise auf Ausgaben eines anderen Projekts in derselben Projektmappe hinzufügen, da dies zu Kompilierungsfehlern führen kann. Erstellen Sie Verweise zwischen Projekten stattdessen im Dialogfeld **Verweis hinzufügen** auf der Registerkarte **Projekte**. Dies erleichtert die Entwicklung im Team, da die in den Projekten erstellten Klassenbibliotheken besser verwaltet werden können. Weitere Informationen finden Sie unter [Problembehandlung bei fehlerhaften Verweisen](../ide/troubleshooting-broken-references.md).

> [!NOTE]
> In Visual Studio 2015 oder höher wird anstelle eines Projektverweises ein Dateiverweis erstellt, wenn die Zielversion von Framework eines Projekts .NET Framework 4.5 oder höher ist und die Zielversion des anderen Projekts .NET Framework 2, 3, 3.5 oder 4.0 ist.

### <a name="to-display-an-assembly-in-the-add-reference-dialog-box"></a>So zeigen Sie eine Assembly im Dialogfeld "Verweis hinzufügen" an

- Verschieben oder kopieren Sie die Assembly in einen der folgenden Speicherorte:

  - Das aktuelle Projektverzeichnis. (Sie können die Assemblys über die Registerkarte **Durchsuchen** suchen.)

  - Andere Projektverzeichnisse in der gleichen Projektmappe. (Sie können die Assemblys über die Registerkarte **Projekte** suchen.)

  \- oder -

- Legen Sie einen Registrierungsschlüssel fest, der den Speicherort der anzuzeigenden Assemblys angibt:

  Fügen Sie für ein 32-Bit-Betriebssystem einen der folgenden Registrierungsschlüssel hinzu:

  - `[HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

  - `[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

  Fügen Sie für ein 64-Bit-Betriebssystem einen der folgenden Registrierungsschlüssel in einer 32-Bit-Registrierungsstruktur hinzu:

  - `[HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

  - `[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

  *\<VersionMinimum\>* ist die niedrigste in Frage kommende .NET Framework-Version. Wenn *\<VersionMinimum\>* v3.0 ist, gelten in *AssemblyFoldersEx* angegebene Ordner für Projekte mit der Zielversion .NET Framework 3.0 und höher.

  *\<AssemblyLocation\>* ist das Verzeichnis der Assemblys, die Sie im Dialogfeld **Verweis hinzufügen** anzeigen möchten, z. B. *C:\MyAssemblies*.

  Indem der Registrierungsschlüssel unter dem `HKEY_LOCAL_MACHINE`-Knoten erstellt wird, können die Assemblys am angegebenen Speicherort für alle Benutzer im Dialogfeld **Verweis hinzufügen** angezeigt werden. Wenn der Registrierungsschlüssel unter dem `HKEY_CURRENT_USER`-Knoten erstellt wird, hat dies nur Einfluss auf die Einstellung für den aktuellen Benutzer.

  Öffnen Sie das Dialogfeld **Verweis hinzufügen** erneut. Die Assemblys sollten auf der Registerkarte **.NET** angezeigt werden. Stellen Sie andernfalls sicher, dass sich die Assemblys im angegebenen Verzeichnis *AssemblyLocation* befinden, starten Sie Visual Studio neu, und versuchen Sie es noch einmal.

## <a name="projects-tab"></a>Registerkarte „Projekte“

Die Registerkarte **Projekte** listet alle kompatiblen Projekte innerhalb der aktuellen Projektmappe auf der Unterregisterkarte **Projektmappe** auf.

Ein Projekt kann auf ein anderes Projekt verweisen, das eine andere Frameworkversion als Ziel verwendet. Beispielsweise können Sie ein Projekt erstellen, das .NET Framework 4 als Ziel verwendet, jedoch auf eine Assembly verweist, die für .NET Framework 2 erstellt wurde. Das .NET Framework 2-Projekt kann jedoch nicht auf ein .NET Framework 4-Projekt verweisen. Weitere Informationen finden Sie unter [Übersicht über Frameworkziele](../ide/visual-studio-multi-targeting-overview.md).

> [!NOTE]
> Ein Projekt, das auf .NET Framework 4 abzielt, ist nicht kompatibel mit einem Projekt, das auf das Clientprofil von .NET Framework 4 abzielt.

## <a name="shared-projects-tab"></a>Registerkarte „Freigegebene Projekte“

Fügen Sie auf der **Registerkarte Freigegebene Projekte** im Dialogfeld „Verweis-Manager“ einen Verweis auf ein freigegebenes Projekt hinzu. [Mit freigegebenen Projekten](/xamarin/cross-platform/app-fundamentals/shared-projects?tabs=windows) können Sie allgemeinen Code schreiben, auf den von einer Reihe verschiedener Anwendungsprojekte verwiesen wird.

## <a name="universal-windows-tab"></a>Registerkarte „Universelles Windows“

Die Registerkarte **Universelles Windows** führt alle SDKs auf, die für Plattformen gelten, auf denen Windows-Betriebssysteme ausgeführt werden.
Diese Registerkarte enthält zwei Untergruppen: **Core** und **Erweiterungen**.

### <a name="core-subgroup"></a>Untergruppe „Kernspeicher“

Universelle Windows-App-Projekte verweisen standardmäßig auf das Universelles Windows SDK. Entsprechend werden in der Untergruppe **Core** im **Verweis-Manager** keine der Assemblys aus dem Universelles Windows SDK aufgelistet.

### <a name="extensions-subgroup"></a>Untergruppe „Erweiterungen“

**Erweiterungen** listen die Benutzer-SDKs auf, die die als Ziel verwendete Windows-Plattform erweitern.

Ein SDK ist eine Auflistung von Dateien, die Visual Studio als einzelne Komponente behandelt. Auf der Registerkarte **Erweiterungen** werden SDKs, die sich auf das Projekt beziehen, über das das Dialogfeld „Verweis-Manager“ aufgerufen wurde, als einzelne Einträge aufgeführt. Wenn er einem Projekt hinzugefügt wird, wird der gesamte SDK-Inhalt von Visual Studio so verwendet, dass der Benutzer keine weiteren Aktionen ausführen muss, um den SDK-Inhalt in IntelliSense, in der Toolbox, in Designern, im Objektkatalog, im Build, bei der Bereitstellung, beim Debuggen und beim Packen zu nutzen.

Informationen über das Anzeigen Ihres SDKs auf der Registerkarte **Erweiterungen** finden Sie unter [Creating a Software Development Kit (Erstellen eines Software Development Kits)](../extensibility/creating-a-software-development-kit.md).

> [!NOTE]
> Wenn ein Projekt auf ein SDK verweist, das von einem anderen SKD abhängt, verwendet Visual Studio das zweite SDK nur, wenn Sie manuell einen Verweis auf das zweite SDK hinzufügen. Wenn ein Benutzer ein SDK auf der Registerkarte **Erweiterungen** auswählt, unterstützt Sie das Dialogfeld „Verweis-Manager“ beim Erkennen von SDK-Abhängigkeiten, indem es alle Abhängigkeiten im Detailbereich auflistet.

Wenn ein Projekttyp Erweiterungen nicht unterstützt, wird diese Registerkarte nicht im Dialogfeld „Verweis-Manager“ angezeigt.

## <a name="com-tab"></a>COM-Registerkarte

Die Registerkarte **COM** listet alle COM-Komponenten auf, die für Verweise verfügbar sind. Wenn Sie einer registrierten COM DLL mit einem internen Manifest eine Referenz hinzufügen möchten, müssen Sie die Registrierung der DLL zunächst aufheben. Andernfalls fügt Visual Studio den Assemblyverweis nicht als native DLL, sondern als ActiveX-Steuerelement hinzu.

Wenn ein Projekttyp COM nicht unterstützt, wird die Registerkarte nicht im Dialogfeld „Verweis-Manager“ angezeigt.

## <a name="browse"></a>Durchsuchen

Mit der Schaltfläche **Durchsuchen** können Sie nach einer Komponente im Dateisystem suchen.

Ein Projekt kann auf eine andere Komponente verweisen, die eine andere Frameworkversion als Ziel verwendet. Sie können z.B. eine Anwendung für .NET Framework 4.7 erstellen, die auf eine Komponente verweist, die wiederum auf .NET Framework 4 abzielt. Weitere Informationen finden Sie unter [Übersicht über Frameworkziele](../ide/visual-studio-multi-targeting-overview.md).

Sie sollten keine Dateiverweise auf Ausgaben eines anderen Projekts in derselben Projektmappe hinzufügen, da dies zu Kompilierungsfehlern führen kann. Erstellen Sie Verweise zwischen Projekten stattdessen im Dialogfeld „Verweis-Manager“ auf der Registerkarte **Projektmappe**. Dies erleichtert die Entwicklung im Team, da die in den Projekten erstellten Klassenbibliotheken besser verwaltet werden können. Weitere Informationen finden Sie unter [Problembehandlung bei fehlerhaften Verweisen](../ide/troubleshooting-broken-references.md).

Sie können nicht zu einem SDK navigieren und es dem Projekt hinzufügen. Sie können nur zu einer Datei navigieren (beispielsweise zu einer Assembly oder einer *WINMD*-Datei) und sie dem Projekt hinzufügen.

Beim Erstellen eines Dateiverweises auf eine WinMD-Datei wird als Layout erwartet, dass die Dateien mit den Erweiterungen *\<FileName>.winmd*, *\<FileName>.dll* und *\<FileName>.pri* alle nebeneinander platziert werden. Wenn Sie in den folgenden Szenarien auf ein WinMD verweisen, wird ein unvollständiger Satz von Dateien in das Projektausgabeverzeichnis kopiert und es treten infolgedessen Build- und Laufzeitfehler auf.

- **Native Komponente**: Ein natives Projekt erstellt ein WinMD für jeden unzusammenhängenden Satz von Namespaces und eine DLL, die aus der Implementierung besteht. Die WinMDs haben unterschiedliche Namen. Wenn auf diese native Komponentendatei verwiesen wird, erkennt MSBuild nicht, dass die ungleich benannten WinMDs eine Komponente darstellen. Folglich werden nur die Dateien mit den Erweiterungen *\<FileName>.dll* und *\<FileName>.winmd* mit identischem Namen kopiert, und es treten Laufzeitfehler auf. Erstellen Sie ein Erweiterungs-SDK, um dieses Problem zu umgehen. Weitere Informationen finden Sie unter [Create a Software Development Kit (Erstellen eines Software Development Kits)](../extensibility/creating-a-software-development-kit.md).

- **Verarbeiten von Steuerelementen**: Ein XAML-Steuerelement besteht mindestens aus den folgenden Dateien: *\<FileName>.winmd*, *\<FileName>.dll*, *\<FileName>.pri*, *\<XamlName>.xaml* und *\<ImageName>.jpg*. Bei der Projekterstellung werden die Ressourcendateien, die mit dem Dateiverweis verknüpft sind, nicht in das Ausgabeverzeichnis des Projekts kopiert. Es werden nur die Dateien mit den Erweiterungen *\<FileName>.winmd*, *\<FileName>.dll* und *\<FileName>.pri* kopiert. Ein Buildfehler wird protokolliert, um den Benutzer zu informieren, dass die Ressourcen *\<XamlName>.xaml* und *\<ImageName>.jpg* fehlen. Damit der Vorgang erfolgreich abgeschlossen wird, muss der Benutzer diese Ressourcendateien manuell in das Projektausgabeverzeichnis für Build und Debuggen/Laufzeit kopieren. Erstellen Sie zur Umgehung des Problems entweder ein Erweiterungs-SDK, indem Sie die Schritte unter [Create a Software Development Kit (Erstellen eines Software Development Kits)](../extensibility/creating-a-software-development-kit.md) ausführen, oder bearbeiten Sie die Projektdatei, und fügen Sie folgende Eigenschaft hinzu:

    ```xml
    <PropertyGroup>
       <GenerateLibraryOutput>True</GenerateLibraryOutput>
    </PropertyGroup>
    ```

    > [!NOTE]
    > Wenn Sie die Eigenschaft hinzufügen, wird der Build ggf. langsamer ausgeführt.

## <a name="recent"></a>Zuletzt

**Assemblys**, **COM**, **Windows** und **Durchsuchen** unterstützen jeweils eine Registerkarte **Aktuell**, auf der die Liste der Komponenten aufgeführt werden, die Projekten kürzlich hinzugefügt wurden.

## <a name="search"></a>Suchen

Die Suchleiste im Dialogfeld „Verweis-Manager“ funktioniert über die Registerkarte, die sich im Fokus befindet. Wenn beispielsweise ein Benutzer „System“ in der Suchleiste eingibt, während die Registerkarte **Projektmappe** im Fokus ist, gibt die Suche keine Ergebnisse zurück, es sei denn, die Projektmappe umfasst einen Projektnamen, der das Wort „System“ enthält.

## <a name="see-also"></a>Siehe auch

- [Verwalten von Verweisen in einem Projekt](../ide/managing-references-in-a-project.md)
