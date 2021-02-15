---
title: Einschließen eines NuGet-Pakets in Ihr Projekt
description: In diesem Dokument wird beschrieben, wie ein NuGet-Paket in ein Xamarin-Projekt eingeschlossen wird. Es veranschaulicht das Suchen und Herunterladen von Paketen und bietet eine Einführung in die IDE-Integrationsfunktionen.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 04/14/2017
ms.assetid: 5C800815-0B13-4B27-B017-95FCEF1A0EA2
ms.custom: video
ms.topic: how-to
ms.openlocfilehash: 274e8defe25fa78c30aee72834e486b302a9af4e
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2020
ms.locfileid: "97729430"
---
# <a name="include-a-nuget-package-in-your-project"></a>Einschließen eines NuGet-Pakets in Ihr Projekt

NuGet ist der beliebteste Paket-Manager für die .NET-Entwicklung und ist in Visual Studio für Mac und Visual Studio für Windows integriert. Sie können nach Paketen suchen und diese zu Ihren Xamarin-Projekten für iOS und Android mithilfe beider IDEs hinzufügen.

Dieser Artikel befasst sich mit dem Einschließen eines NuGet-Pakets in ein Projekt und veranschaulicht die Toolkette, durch die der Prozess nahtlos abläuft.

## <a name="nuget-in-visual-studio-for-mac"></a>NuGet in Visual Studio für Mac

Zum Veranschaulichen der NuGet-Paketfunktionen erläutern wir zunächst das Erstellen einer neuen Anwendung und das Hinzufügen eines Pakets zu dieser. Anschließend behandeln wir die IDE-Features, die Sie beim Verwalten von Paketen unterstützen.

## <a name="create-a-new-project"></a>Erstellt ein neues Projekt

Erstellen Sie zunächst ein Projekt namens `HelloNuget`, wie unten gezeigt. Dieses Beispiel zeigt die Vorlage für eine Single-View-Anwendung unter iOS, allerdings funktioniert jeder unterstützte Projekttyp:

![Erstellen eines neuen iOS-Projekts](media/nuget-walkthrough-NewProject.png)

## <a name="adding-a-package"></a>Hinzufügen eines Pakets

Wenn das Projekt in Visual Studio für Mac geöffnet ist, klicken Sie mit der rechten Maustaste auf den Ordner **Pakete** im **Projektmappenpad**, und klicken Sie dann auf **Pakete hinzufügen**:

![Kontextaktion für das Hinzufügen eines neuen NuGet-Pakets](media/nuget-walkthrough-PackagesMenu.png)

Dadurch wird das Fenster **Pakete hinzufügen** geöffnet. Versichern Sie sich, dass das Dropdownmenü für die Quelle auf `nuget.org` festgelegt ist:

![Dropdownmenü für die Datenquellenliste](media/nuget-walkthrough-Source.png)

Wenn das Fenster geöffnet ist, wird eine Liste von Paketen aus der Standardpaketquelle (nuget.org) geladen. Die ersten Ergebnisse sehen wie folgt aus:

![Liste von NuGet-Paketen](media/nuget-walkthrough-AddPackages1.png)

Verwenden Sie das Suchfeld in der oberen rechten Ecke, um ein bestimmtes Paket, zum Beispiel `azure`, zu finden. Wenn Sie ein Paket gefunden haben, das Sie verwenden möchten, wählen Sie es aus, und klicken Sie auf die Schaltfläche **Paket hinzufügen**, um die Installation zu starten.

[Add Azure NuGet Package (Hinzufügen eines Azure-NuGet-Pakets)](media/nuget-walkthrough-AddPackages2.png)

Sobald das Paket heruntergeladen wurde, wird es Ihrem Projekt hinzugefügt. Die Projektmappe wird sich wie folgt ändern:

* Der Knoten **Referenzen** wird eine Liste aller Assemblys enthalten, die Teil eines NuGet-Pakets sind.
* Der Knoten **Pakete** zeigt alle NuGet-Pakete an, die Sie heruntergeladen haben. Sie können Pakete aus dieser Liste aktualisieren oder entfernen.
* Die Datei **packages.config** wird Ihrem Projekt hinzugefügt. Diese XML-Datei wird von der IDE verwendet, um nachzuverfolgen, auf welche Paketversionen in diesem Projekt verwiesen wird. Diese Datei sollte nicht manuell bearbeitet werden, aber Sie sollten sie in der Versionskontrolle behalten. Beachten Sie, dass die Datei „project.json“ statt der Datei „packages.config“ verwendet werden kann. Bei der Datei „project.json“ handelt es sich um ein neues Dateiformat für Pakete, das mit NuGet 3 eingeführt wurde und die transitive Wiederherstellung unterstützt. Weitere Informationen zu „project.json“ finden Sie in der [NuGet documentation (NuGet-Dokumentation)](/NuGet/Schema/Project-Json). Die Datei „project.json“ muss manuell hinzugefügt und das Projekt geschlossen und erneut geöffnet werden, bevor diese in Visual Studio für Mac verwendet werden kann.

## <a name="using-nuget-packages"></a>Verwenden von NuGet-Paketen

Sobald das NuGet-Paket hinzugefügt und die Projektverweise aktualisiert wurden, können Sie so mit der API programmieren, wie Sie es mit jedem anderen Projektverweis tun würden.

Versichern Sie sich, dass sie alle erforderlichen `using`-Anweisungen zum Anfang Ihrer Datei hinzufügen:

```csharp
using Newtonsoft.Json;
```

Die meisten NuGet-Pakete enthalten zusätzliche Informationen, zum Beispiel eine Infodatei oder einen Projektseitenlink zur NuGet-Quelle. Sie können diesen Link normalerweise in den Paketinformationen auf der Seite „Pakete hinzufügen“ finden:

[View Project Page link (Anzeigen des Projektseitenlinks)](media/nuget-walkthrough-project-page.png)

<a name="Package_Updates" class="injected"></a>

## <a name="package-updates"></a>Paketaktualisierungen

Paketupdates können entweder alle auf einmal durchgeführt werden, indem Sie mit der rechten Maustaste auf den Knoten **Pakete** klicken, oder einzeln, indem Sie auf jede Komponente klicken.

Klicken Sie mit der rechten Maustaste auf **Pakete**, um auf das Kontextmenü zuzugreifen:

![Screenshot mit dem ausgewählten Paketknoten und dem Kontextmenü, das mit Rechtsklick ausgewählt wurde, mit den Befehlen für „Pakete hinzufügen“, „Update“, „Wiederherstellen“, „Aktualisieren“](media/nuget-walkthrough-PackagesMenu.png)

* **Pakete hinzufügen**: Öffnet das Fenster, um dem Projekt weitere Pakete hinzuzufügen.
* **Aktualisieren**: Überprüft den Quellserver auf jedes Paket und lädt neuere Versionen herunter.
* **Wiederherstellen**: Lädt fehlende Pakete herunter (ohne bestehende Pakete auf neuere Versionen zu aktualisieren).

Die Optionen „Aktualisieren“ und „Wiederherstellen“ sind auch auf Projektmappenebene verfügbar und wirken sich auf alle Projekte in der Projektmappe aus.

Sie können auch mit der rechten Maustaste auf die einzelnen Pakete klicken, um auf das Kontextmenü zuzugreifen:

![Screenshot mit ausgewähltem eindeutigem Paket und das Kontextmenü, das mit Rechtsklick ausgewählt wurde, mit Befehlen für „Update“, „Entfernen“ und „Aktualisieren“](media/nuget-walkthrough-PackageMenu.png)

* **Versionsnummer**: Die Versionsnummer ist ein deaktiviertes Menüelement, das nur zu Informationszwecken dient.
* **Aktualisieren**: Überprüft den Quellserver und lädt eine neuere Version herunter (falls vorhanden).
* **Entfernen**: Entfernt das Paket aus diesem Projekt und die relevanten Assemblys aus den Projektverweisen.

## <a name="adding-package-sources"></a>Hinzufügen von Paketquellen

Pakete, die für die Installation verfügbar sind, werden ursprünglich von nuget.org abgerufen. Sie können jedoch andere Paketspeicherorte zu Visual Studio für Mac hinzufügen. Das kann hilfreich sein, um Ihre NuGet-Pakete in der Entwicklung zu testen oder um einen privaten NuGet-Server innerhalb Ihres Unternehmens oder Ihrer Organisation zu verwenden.

Navigieren Sie in Visual Studio für Mac zu **Visual Studio > Einstellungen > NuGet > Quellen**, um die Liste der Paketquellen anzuzeigen und zu bearbeiten. Beachten Sie, dass es sich bei den Quellen um einen Remoteserver (angegeben durch eine URL) oder ein lokales Verzeichnis handeln kann.

![Paketquellen](media/nuget-walkthrough-PackageSource.png)

Klicken Sie auf **Hinzufügen**, um eine neue Quelle festzulegen. Geben Sie einen Anzeigenamen und die URL (oder den Dateipfad) zur Paketquelle an. Wenn es sich bei der Quelle um einen sicheren Webserver handelt, geben Sie auch einen Benutzernamen und ein Kennwort an, andernfalls lassen Sie diese Einträge leer:

![Screenshot des Dialogfelds „Paketquelle hinzufügen“ mit den Feldern für Name, Speicherort, Benutzername und Kennwort.](media/nuget-walkthrough-PackageSource2.png)

Verschiedene Quellen können bei der Suche nach Paketen angegeben werden:

![Screenshot des Bildschirms „Pakete hinzufügen“, auf dem eine Dropdownliste der Quellen angezeigt wird, die bei der Suche nach Paketen ausgewählt werden können](media/nuget-walkthrough-PackageSource3.png)

## <a name="version-control"></a>Quellcodeverwaltung

Die NuGet-Dokumentation erläutert [das Verwenden von NuGet ohne das Übernehmen von Paketen in die Quellcodeverwaltung](/nuget/consume-packages/packages-and-source-control). Wenn Sie keine Binärdateien und nicht verwendeten Informationen in der Quellcodeverwaltung speichern möchten, können Sie Visual Studio für Mac für das automatische Wiederherstellen vom Server konfigurieren. Wenn ein Entwickler das Projekt zum ersten Mal aus der Quellcodeverwaltung abruft, lädt Visual Studio für Mac dadurch die erforderlichen Pakete automatisch herunter und installiert diese.

![Automatisches Wiederherstellen von Paketen](media/nuget-walkthrough-AutoRestore.png)

Weitere Informationen zum Ausschließen der Verfolgung des Verzeichnisses `packages` finden Sie in der Dokumentation zu Ihrer speziellen Quellcodeverwaltung.

## <a name="related-video"></a>Zugehörige Videos

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Using-NuGet/player]

## <a name="see-also"></a>Siehe auch

* [Installieren und Verwenden eines Pakets in Visual Studio (unter Windows)](/nuget/quickstart/install-and-use-a-package-in-visual-studio)
