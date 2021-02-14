---
title: Aktualisieren von Visual Studio mit einem minimalen Offlinelayout
description: In diesem Artikel erhalten Sie Informationen zum Aktualisieren von Visual Studio mit einem minimalen Offlinelayout.
ms.date: 07/21/2020
ms.custom: seodec18
ms.topic: how-to
ms.assetid: ''
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 199771b1cda2049d6508832d7d2264558104a566
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935702"
---
# <a name="update-visual-studio-using-a-minimal-offline-layout"></a>Aktualisieren von Visual Studio mit einem minimalen Offlinelayout

Für Computer, die nicht mit dem Internet verbunden sind, ist das Erstellen eines minimalen Layouts die einfachste und schnellste Möglichkeit, Ihre Offlineinstanzen in Visual Studio zu aktualisieren.

Das Tool für minimale Layouts erstellt ein perfekt auf die Anforderungen Ihres Teams angepasstes Layout. Unternehmensadministratoren können dieses Tool verwenden, um Aktualisierungslayouts für die meisten Versionen von Visual Studio 2017 und 2019 zu erstellen. Im Gegensatz zu einem vollständigen Visual Studio-Layout enthält ein minimales Layout nur die aktualisierten Pakete. Die Größe ist also immer geringer, und die Generierung und Bereitstellung kann schneller erfolgen. Sie können die Größe des Updatelayouts noch weiter verringern, indem Sie nur die gewünschten Sprachen, Workloads und Komponenten angeben.

## <a name="how-to-generate-a-minimal-layout"></a>Generieren eines minimalen Layouts

> [!IMPORTANT]
> Bei diesen Anweisungen wird vorausgesetzt, dass Sie zuvor bereits Layouts erstellt und verwendet haben. Weitere Informationen hierzu finden Sie unter [Aktualisieren einer netzwerkbasierten Installation von Visual Studio](update-a-network-installation-of-visual-studio.md).
>
> Nähere Informationen zum Visual Studio-Lebenszyklus finden Sie unter [Produktlebenszyklus und Preise in Visual Studio](/visualstudio/releases/2019/servicing).
>

Dieses Tool erstellt Updatelayouts ab Visual Studio 2017 (15.9). Das Layout kann auf Netzwerkcomputern oder Offlinecomputern bereitgestellt werden, um Visual Studio-Instanzen zu aktualisieren. Während der [normalen Layouterstellung](update-a-network-installation-of-visual-studio.md) werden alle Pakete für ein bestimmtes Release heruntergeladen. Die Erstellung von normalen Layouts ist für das Reparieren, Deinstallieren und weitere Standardvorgänge in Visual Studio-Instanzen erforderlich. Beim minimalen Layout werden nur aktualisierte Pakete heruntergeladen, es ist also kleiner und kann einfacher auf Offlinecomputer kopiert werden.

### <a name="installing-the-minimal-layout-tool"></a>Installieren des Tools für minimale Layouts
 
 1. Laden Sie zunächst das Tool für minimale Layouts [hier](https://aka.ms/vs/installer/minimallayout) herunter. Klicken Sie bei Aufforderung auf die Option **Speichern** und dann auf **Ausführen**.

     ![Speichern des Tools für minimale Layouts](media/save-minimal-layout.png)

 2. Akzeptieren Sie als nächsten Schritt die Aufforderung für die Benutzerkontensteuerung, indem Sie auf **Ja** klicken.

     ![Akzeptieren der Benutzerkontensteuerung](media/accept-user-account-control.png)

 3. Das Tool für minimale Layouts wird unter `C:\Program Files (x86)\Microsoft Visual Studio\MinimalLayout` installiert.

### <a name="how-to-use-the-minimal-layout-tool"></a>Verwenden des Tools für minimale Layouts

`MinimalLayout.exe` verwendet die folgenden Befehle und Optionen, um das Layout zu generieren. Mindestens ein Befehl ist erforderlich, um das Tool auszuführen. So wird das Tool ausgeführt:

```MinimalLayout.exe [command] <options>...```

#### <a name="commands"></a>Befehle
* **Vorschau**: Verwenden Sie diesen Befehl, um als Vorschau zu sehen, wie viele Pakete heruntergeladen werden und wie viel Speicherplatz erforderlich ist, um das Layout zu erstellen. 
* **Generieren**: Verwenden Sie diesen Befehl, um das minimale Layout für das Aktualisieren von Visual Studio zu generieren.
* **regenerate:** Verwenden Sie diesen Befehl, um ein Layout mithilfe einer Antwortdatei für minimale Layouts erneut zu generieren. Jedes minimale Layout erzeugt eine `MinimalLayout.json`-Antwortdatei, die die Eingabeparameter für das ursprüngliche minimale Layout enthält. Sie können den Befehl **regenerate** und eine `MinimalLayout.json`-Antwortdatei verwenden, um das minimale Layout erneut zu generieren. Dies ist dann hilfreich, wenn Sie ein minimales Layout für eine neue Visual Studio-Aktualisierung erstellen möchten, die auf der Antwortdatei des vorherigen minimalen Layouts basieren soll.

   Für diesen Befehl ist ein `MinimalLayout.json`-Dateipfad von einem bereits generierten Layout erforderlich. 

    ```cmd
    MinimalLayout.exe regenerate --filePath C:\MinimalLayout\MinimalLayout.json
    ```

* **verify:** Verwenden Sie diesen Befehl, um zu bestimmen, ob der Layoutordner beschädigt ist.
* **Problemlösung:** Verwenden Sie diesen Befehl, um Fehlerbehebungen für den beschädigten Layoutordner durchzuführen, einschließlich des Ersetzens jeglicher fehlender Pakete aus dem Layoutordner.

::: moniker range="vs-2019"

#### <a name="options"></a>Optionen 

|Optionen    |BESCHREIBUNG    |Erforderlich/Optional |Beispiel |
|:----------|:-----------|:------------|:--------------|
|--targetLocation &lt;Verzeichnis&gt; |Gibt ein Verzeichnis an, in dem ein minimales Offlinelayout erstellt werden soll.       |Erforderlich        |--targetLocation c:\VSLayout\ |
|--baseVersion &lt;Version&gt;|Das minimale Offlinelayout wird ab dieser Version generiert.   |Erforderlich|--baseVersion 16.4.0 |
|--targetVersion &lt;Version&gt;|Das minimale Offlinelayout wird bis zu und einschließlich dieser Version generiert.|Erforderlich|--targetVersion 16.4.4|
|--languages    |Gibt die Sprachen an, die in das minimale Offlinelayout eingeschlossen werden sollen. Es können mehrere Werte angegeben werden, die dann durch Leerzeichen voneinander getrennt werden müssen.    |Erforderlich    |--languages en-US fr-FR |
|--productId &lt;ID&gt;    |Die ID des Produkts, für das das minimale Offlinelayout generiert werden soll. <br> <ul><li>Microsoft.VisualStudio.Product.Enterprise</li><li>Microsoft.VisualStudio.Product.Professional</li><li>Microsoft.VisualStudio.Product.BuildTools</li><li>Microsoft.VisualStudio.Product.TestAgent</li><li>Microsoft.VisualStudio.Product.TestController</li><li>Microsoft.VisualStudio.Product.TeamExplorer</li></ul>|Erforderlich|--productId Microsoft.VisualStudio.Product.Enterprise |
|--filePath    |Der Dateipfad der MinimalLayout.json-Datei eines bereits erstellten Layouts. Diese Option wird nur mit dem regenerate-Befehl verwendet.     |Für den regenerate-Befehl erforderlich    |--filePath C:\VSLayout\minimalLayout.json <br><br> **Beachten Sie, dass der regenerate-Befehl nur --filePath als Option akzeptiert.** |
|--add &lt;mindestens eine Workload- oder Komponenten-ID&gt;    |Gibt mindestens eine Workload- oder Komponenten-ID an, die hinzugefügt werden soll. Zusätzliche Komponenten können global hinzugefügt werden, wenn Sie --includeRecommended und/oder <br> –-includeOptional verwenden. Es können mehrere Workload- oder Komponenten-IDs angegeben werden, die durch ein Leerzeichen voneinander getrennt werden müssen.    |Optional    |--add Microsoft.VisualStudio.Workload.ManagedDesktop Microsoft.VisualStudio.Workload.NetWeb Component.GitHub.VisualStudio |
|--includeRecommended    |Enthält die empfohlenen Komponenten für alle zu installierenden Workloads, aber keine optionalen Komponenten.    |Optional    |Für eine bestimmte Workload: <br> --add Microsoft.VisualStudio.Workload. ManagedDesktop;includeRecommended <br><br> Zur Anwendung aller Workloads: --includeRecommended |
|--includeOptional |Enthält die optionalen Komponenten für alle zu installierenden Workloads, einschließlich der empfohlenen Komponenten.    |Optional    |Für eine bestimmte Workload: <br>--add Microsoft.VisualStudio.Workload. ManagedDesktop;includeOptional <br><br> Zur Anwendung aller Workloads: --includeOptional |

::: moniker-end

::: moniker range="vs-2017"

#### <a name="options"></a>Optionen 

|Optionen    |BESCHREIBUNG    |Erforderlich/Optional |Beispiel |
|:----------|:-----------|:------------|:--------------|
|--targetLocation &lt;Verzeichnis&gt; |Gibt ein Verzeichnis an, in dem ein minimales Offlinelayout erstellt werden soll.       |Erforderlich        |--targetLocation c:\VSLayout\ |
|--baseVersion &lt;Version&gt;|Das minimale Offlinelayout wird ab dieser Version generiert.   |Erforderlich|--baseVersion 15.0.0 |
|--targetVersion &lt;Version&gt;|Das minimale Offlinelayout wird bis zu und einschließlich dieser Version generiert.|Erforderlich|--targetVersion 15.9.31|
|--languages    |Gibt die Sprachen an, die in das minimale Offlinelayout eingeschlossen werden sollen. Es können mehrere Werte angegeben werden, die dann durch Leerzeichen voneinander getrennt werden müssen.    |Erforderlich    |--languages en-US fr-FR |
|--productId &lt;ID&gt;    |Die ID des Produkts, für das das minimale Offlinelayout generiert werden soll. <br> <ul><li>Microsoft.VisualStudio.Product.Enterprise</li><li>Microsoft.VisualStudio.Product.Professional</li><li>Microsoft.VisualStudio.Product.BuildTools</li><li>Microsoft.VisualStudio.Product.TestAgent</li><li>Microsoft.VisualStudio.Product.TestController</li><li>Microsoft.VisualStudio.Product.TeamExplorer</li></ul>|Erforderlich|--productId Microsoft.VisualStudio.Product.Enterprise |
|--filePath    |Der Dateipfad der MinimalLayout.json-Datei eines bereits erstellten Layouts. Diese Option wird nur mit dem regenerate-Befehl verwendet.     |Für den regenerate-Befehl erforderlich    |--filePath C:\VSLayout\minimalLayout.json <br><br> **Beachten Sie, dass der regenerate-Befehl nur --filePath als Option akzeptiert.** |
|--add &lt;mindestens eine Workload- oder Komponenten-ID&gt;    |Gibt mindestens eine Workload- oder Komponenten-ID an, die hinzugefügt werden soll. Zusätzliche Komponenten können global hinzugefügt werden, wenn Sie --includeRecommended und/oder <br> –-includeOptional verwenden. Es können mehrere Workload- oder Komponenten-IDs angegeben werden, die durch ein Leerzeichen voneinander getrennt werden müssen.    |Optional    |--add Microsoft.VisualStudio.Workload.ManagedDesktop Microsoft.VisualStudio.Workload.NetWeb Component.GitHub.VisualStudio |
|--includeRecommended    |Enthält die empfohlenen Komponenten für alle zu installierenden Workloads, aber keine optionalen Komponenten.    |Optional    |Für eine bestimmte Workload: <br> --add Microsoft.VisualStudio.Workload. ManagedDesktop;includeRecommended <br><br> Zur Anwendung aller Workloads: --includeRecommended |
|--includeOptional |Enthält die optionalen Komponenten für alle zu installierenden Workloads, einschließlich der empfohlenen Komponenten.    |Optional    |Für eine bestimmte Workload: <br>--add Microsoft.VisualStudio.Workload. ManagedDesktop;includeOptional <br><br> Zur Anwendung aller Workloads: --includeOptional |

::: moniker-end

### <a name="generating-a-minimal-layout"></a>Generieren eines minimalen Layouts

> [!IMPORTANT]
>  Bei diesen Anweisungen wird vorausgesetzt, dass Sie zuvor ein Layout für die Netzwerkinstallation erstellt haben. Weitere Informationen hierzu finden Sie auf der Seite [Erstellen einer Netzwerkinstallation von Visual Studio](create-a-network-installation-of-visual-studio.md).

Erstellen Sie mithilfe des **generate**-Befehls ein minimales Layout für Ihre speziellen Versionen. Sie müssen dazu außerdem die Produkt-ID, die Sprachen und sämtliche erforderlichen Workloads kennen. Dieses minimale Layout aktualisiert alle Visual Studio-Instanzen von der Basisversion bis zu und einschließlich der Zielversion.

Bevor Sie das Layout erstellen, können Sie sich die Gesamtgröße des Downloads und die Anzahl der darin eingeschlossenen Pakete anzeigen lassen, indem Sie den **preview**-Befehl verwenden. Dieser Befehl akzeptiert dieselben Optionen wie der **generate**-Befehl, und die Details werden in die Konsole geschrieben.

Im Folgenden sehen Sie einige Beispiele, wie eine Vorschau für ein minimales Layout angezeigt werden kann und wie es generiert und erneut generiert werden kann:

::: moniker range="vs-2019"

- Zuerst sehen Sie hier ein Beispiel, wie Sie eine Vorschau für ein Layout für die Visual Studio Enterprise-Versionen 16.4.0 bis 16.4.4 nur für die Sprache Englisch anzeigen können.

    ```cmd
    MinimalLayout.exe preview --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --languages en-US
    ```

- Hier sehen Sie, wie Sie dasselbe Layout mit einer Workload generieren.

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US
    ```

- Hier wiederum sehen Sie, wie Sie ein minimales Offlinelayout mithilfe einer vorhandenen Antwortdatei erneut generieren. 

    ```cmd
    MinimalLayout.exe regenerate -filepath c:\VSLayout\MinimalLayout.json
    ```

Im Folgenden sehen Sie einige Beispiele für die Verwendung des **generate**-Befehls:

- Hier sehen Sie, wie Sie eine zusätzliche Workload hinzufügen und nur die empfohlenen Pakete einschließen. 

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Professional --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop Microsoft.VisualStudio.Workload.NetWeb;includeRecommended --languages en-US
    ```

- Schließlich sehen Sie hier, wie Sie mehrere Sprachen in Ihr minimales Layout einschließen würden. 

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US fr-FR
    ```

::: moniker-end

::: moniker range="vs-2017"

- Zuerst sehen Sie hier ein Beispiel, wie Sie eine Vorschau für ein Layout für die Visual Studio Enterprise-Versionen 15.0.0 bis 15.9.31 anzeigen können (nur für die Sprache Englisch).

    ```cmd
    MinimalLayout.exe preview --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 15.0.0 --targetVersion 15.9.31 --languages en-US
    ```

- Hier sehen Sie, wie Sie dasselbe Layout mit einer Workload generieren.

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 15.0.0 --targetVersion 15.9.31 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US
    ```

- Hier wiederum sehen Sie, wie Sie ein minimales Offlinelayout mithilfe einer vorhandenen Antwortdatei erneut generieren. 

    ```cmd
    MinimalLayout.exe regenerate -filepath c:\VSLayout\MinimalLayout.json
    ```

Im Folgenden sehen Sie einige Beispiele für die Verwendung des **generate**-Befehls:

- Hier sehen Sie, wie Sie eine zusätzliche Workload hinzufügen und nur die empfohlenen Pakete einschließen. 

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Professional --baseVersion 15.0.0 --targetVersion 15.9.31 --add Microsoft.VisualStudio.Workload.ManagedDesktop Microsoft.VisualStudio.Workload.NetWeb;includeRecommended --languages en-US
    ```

- Schließlich sehen Sie hier, wie Sie mehrere Sprachen in Ihr minimales Layout einschließen würden. 

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 15.0.0 --targetVersion 15.9.31 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US fr-FR
    ```

::: moniker-end

### <a name="how-to-maintain-a-minimal-layout"></a>Verwalten eines minimalen Layouts

Verwenden Sie die Befehle **verify** und **fix**, um Ihr minimales Layout nach seiner Erstellung zu verwalten. Der **verify**-Befehl bestimmt, ob es beschädigte oder fehlende Pakete im minimalen Layout gibt. Wenn nach der Ausführung des **verify**-Befehls Probleme auftreten, verwenden Sie den **fix**-Befehl, um diese fehlenden oder beschädigten Pakete zu korrigieren.

- So überprüfen Sie, ob es in einem Layout fehlende oder beschädigte Pakete gibt: 

    ```cmd
    MinimalLayout.exe Verify --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop --includeRecommended --languages en-US
    ```

- So korrigieren Sie ein solches Layout:

    ```cmd
    MinimalLayout.exe fix --targetLocation C:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeRecommended --languages en-US
    ```

>[!NOTE] 
> Dieses Layout kann nicht verwendet werden, um Fehler einer Visual Studio-Installation zu beheben. Weitere Informationen zum Reparieren einer vorhandenen Visual Studio-Instanz finden Sie unter [Reparieren von Visual Studio](repair-visual-studio.md).
>

### <a name="how-to-use-a-minimal-offline-layout-to-update-an-existing-installation-of-visual-studio"></a>Verwenden eines minimalen Offlinelayouts zum Aktualisieren einer vorhandenen Visual Studio-Installation

Nach dem Generieren eines minimalen Layouts können Sie den gesamten Ordner für das minimale Layout auf einen Clientcomputer kopieren. Dies ist erforderlich, wenn der Computer keinen Zugriff auf den Ordner für das minimale Layout am ursprünglichen Speicherort hat.

Navigieren Sie zum Ordner, und identifizieren Sie den Namen der Bootstrapanwendung. Der Name der Bootstrapanwendung hängt vom ProductId-Wert ab, der beim Generieren des minimalen Layouts angegeben wird. In der Tabelle unten finden Sie weitere Beispiele für häufige Werte.

|ProductId-Wert    |Anwendungsname|
|:-----------|:------------|
|Microsoft.VisualStudio.Product.Enterprise    |vs_enterprise.exe|
|Microsoft.VisualStudio.Product.Professional    |vs_professional.exe|
|Microsoft.VisualStudio.Product.BuildTools    |vs_buildtools.exe|

Die Aktualisierung wird auf eine Visual Studio-Instanz in zwei Schritten angewendet. Beginnen Sie damit, den Visual Studio-Installer zu aktualisieren, und aktualisieren Sie dann Visual Studio.

1. **Aktualisieren des Visual Studio-Installers** 

    Führen Sie den folgenden Befehl aus, und ersetzen Sie `vs_enterprise.exe`, wenn erforderlich, durch den korrekten Name der Bootstrapanwendung. 

    ```cmd
    vs_enterprise.exe --quiet --update --offline C:\VSLayout\vs_installer.opc
    ```

2. **Aktualisieren der Visual Studio-Anwendung**

    Zum Aktualisieren von Visual Studio müssen Sie den Installationspfad (installPath) der Visual Studio-Instanz angeben, die Sie aktualisieren möchten. Wenn mehrere Visual Studio-Instanzen installiert sind, muss jede einzeln aktualisiert werden. Es wird empfohlen, die `–noWeb`-Option unbedingt mit dem Befehl zur Aktualisierung anzugeben, um die Installation von Komponenten zu verhindern, die nicht Teil des minimalen Layouts sind. So kann verhindert werden, dass Visual Studio in einen nicht nutzbaren Zustand gerät.

    Führen Sie den folgenden Befehl aus, und ersetzen Sie dabei den installPath-Befehlszeilenparameter entsprechend. Vergewissern Sie sich außerdem, dass der richtige Bootstrapanwendungsname verwendet wird.

    ```cmd
    vs_enterprise.exe update --noWeb --quiet --installpath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise"
    ```

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Siehe auch

* [Installieren von Visual Studio](install-visual-studio.md)
* [Administratorhandbuch für Visual Studio 2017 RC](visual-studio-administrator-guide.md)
* [Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Tools zum Erkennen und Verwalten von Visual Studio-Instanzen](tools-for-managing-visual-studio-instances.md)
* [Gewusst wie: Definieren von Einstellungen in einer Antwortdatei](automated-installation-with-response-file.md)
* [Steuern von Updates für netzwerkbasierte Visual Studio-Bereitstellungen](controlling-updates-to-visual-studio-deployments.md)
* [Projektlebenszyklus und Wartung in Visual Studio](/visualstudio/releases/2019/servicing/)
