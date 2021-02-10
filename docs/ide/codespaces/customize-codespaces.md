---
title: Anpassen eines Codespace (Vorschau)
description: Hier erhalten Sie weitere Informationen zum Anpassen eines Codespace.
ms.topic: how-to
ms.date: 09/21/2020
author: gregvanl
ms.author: gregvanl
manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.workload:
- multiple
monikerRange: vs-2019
ms.openlocfilehash: 15efee817e41f928e5ca1162e9ace20276bd20d2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971153"
---
# <a name="how-to-customize-a-codespace-preview"></a>Anpassen eines Codespace (Vorschau)

GitHub Codespaces stellt eine vollständige Entwicklungsumgebung in der Cloud bereit. Für die Windows-basierte Entwicklung mithilfe von Visual Studio 2019 bieten die Standardinstanzen von GitHub Codespaces einen hervorragenden Startpunkt. Sie können die Umgebung jedoch auch für Ihr spezifisches Projekt anpassen.

## <a name="installed-software"></a>Installierte Software

In Windows-Codespaces stehen viele Frameworks und Tools zur Verfügung, die bereits installiert sind, sodass Sie sofort loslegen können. In der Tabelle unten sind die Anwendungen und Features aufgeführt, die in allen Windows-Codespaceumgebungen verfügbar sind.

| App                                         | Pfadalias | Version            |
|---------------------------------------------|------------|--------------------|
| .NET                                        | –        | 4.8                |
| .NET Core Runtime                           | dotnet     | 2.1, 3.1           |
| .NET Core SDK                               | dotnet     | 2.1, 3.1.3, 3.1.4  |
| Azure CLI                                   | az         | 2.5                |
| Chocolatey                                  | choco      | 0.10.15            |
| CMake                                       | cmake      | 3,17               |
| Git                                         | Git        | 2,26               |
| Microsoft Build                             | msbuild    | 16.7               |
| Microsoft SQL Server Express-Version 2019   | –        | 15.0               |
| Ninja                                       | ninja      | 1.8.2              |
| Node.js                                     | Knoten       | 12.16              |
| npm                                         | npm        | 6,14               |
| Python                                      | Python     | 3,7                |
| VC-Paket-Manager                          | vcpkg      | 2020.02            |
| Windows SDK                                 | –        | 10.0.18362         |

Die Liste oben ist nicht vollständig. Viele Tools, die Visual Studio installiert, z. B. IISExpress, sind nicht enthalten. Einzelne Komponenten haben möglicherweise auch eine andere Neben- oder Patchversion als oben aufgeführt.

Genauere Informationen zu vorinstallierten Frameworks und Tools finden Sie im Abschnitt [Informationen zu installierter Software](#installed-software-specifics) unten.

## <a name="modifications-to-a-codespace"></a>Änderungen an einem Codespace
 
Sobald Sie einen Codespace erstellt haben, werden alle Änderungen an diesem spezifischen Codespace übernommen, während die Codespaceinstanz auf GitHub Codespaces verfügbar ist. Sie können weitere Repositorys klonen, Tools und Anwendungsgeneratoren installieren und weitere Entwicklungsressourcen hinzufügen. Diese Änderungen werden beibehalten, selbst wenn der Codespace ersetzt wird. Wenn Sie jedoch einen Codespace löschen, gehen alle Änderungen verloren.

> [!NOTE]
> Wenn Sie einen Codespace löschen, gehen alle Änderungen an einem lokalen Repository (ausstehend oder committet) im Codespace verloren. Sorgen Sie dafür, dass Repositoryänderungen an einen Remotespeicherort gepusht werden, bevor ein Codespace gelöscht wird.

Während eine Verbindung zu einem Codespace in Visual Studio besteht, können Sie das Visual Studio-Terminal verwenden, um Befehlszeilentools auszuführen. Sie können entweder PowerShell oder die Eingabeaufforderung von Windows verwenden, die beide über erhöhte Rechte unter dem lokalen Administratorkonto verfügen. Weitere Informationen zum Visual Studio-Terminal finden Sie im [Ankündigungsblog zum Visual Studio-Terminal](https://devblogs.microsoft.com/visualstudio/say-hello-to-the-new-visual-studio-terminal/).

## <a name="customize-a-codespace"></a>Anpassen eines Codespaces

Der wahre Wert von GitHub Codespaces tritt zutage, wenn Sie eindeutige, wiederholbare Entwicklungsumgebungen in der Cloud erstellen können, die auf Ihre eigene Arbeit sowie auf die Ihres Teams zugeschnitten sind. Indem Sie in einer Standardinstanz von GitHub Codespaces entwickeln, können Sie anpassen, was installiert und konfiguriert wird, wenn Sie einen neuen Codespace erstellen.

In den nächsten Abschnitten werden zwei Codespacekonfigurationsmethoden mit den Dateien *.devcontainer.json* und *.devinit.json* beschrieben. In diesen Dateien können Sie die Installationsframeworks und Tools für einen Codespace konfigurieren. Wenn diese Ihrem Repository hinzugefügt werden, kann außerdem jeder, der einen Codespace basierend auf Ihrem Repository erstellt, dieselbe Remoteentwicklungsumgebung nutzen.

## <a name="customize-with-devcontainerjson"></a>Anpassen mit devcontainer.json

Bei Erstellung eines Codespace sucht GitHub Codespaces nach einer [*devcontainers.json*](https://code.visualstudio.com/docs/remote/devcontainerjson-reference)-Datei im Stammverzeichnis Ihres Repository und verwendet die Einstellungen darin, um den Codespace oder die Clientinstanzen, die eine Verbindung dazu herstellen, anzupassen (browserbasierter Editor, Visual Studio oder Visual Studio Code). Die meisten *devcontainer.json*-Einstellungen gelten für Linux-basierte Codespaces oder die zwei anderen Clients, manche sind jedoch für Windows-Codespaces und Visual Studio verfügbar.

Die *devcontainer.json*-Datei kann in einem Repository an einem von zwei Orten gespeichert werden:

1. *{repository-root}/.devcontainer.json*
2. *{repository-root}/.devcontainer/devcontainer.json*

GitHub Codespaces-Instanzen unterstützen die folgenden *devcontainer.json*-Eigenschaften. Visual Studio Code-spezifische Einstellungen festzulegen, ist hilfreich, wenn Sie zusätzlich zu Visual Studio eine Verbindung zu Ihrem Codespace mit den anderen Clients herstellen möchten. 

* `extensions`: Ein Array von [Marketplace-Erweiterungen von Visual Studio Code](https://marketplace.visualstudio.com/vscode), die installiert werden sollten.
* `settings`: [Visual Studio Code-Einstellungen](https://code.visualstudio.com/docs/getstarted/settings), die angewendet werden sollen.
* `forwardPorts`: Ein Port oder ein Array aus Ports, die lokal automatisch weitergeleitet werden sollten, wenn der Codespace ausgeführt wird.
* `postCreateCommand`: Eine Befehlszeichenfolge oder eine Liste von Befehlsargumenten, die nach Erstellung des Codespace ausgeführt werden sollen.

> [!NOTE]
> **devcontainer.json**-Dateien werden auch genutzt, um die [Remoteentwicklung](https://code.visualstudio.com/docs/remote/remote-overview) in Visual Studio Code zu unterstützen. Sie verfügen über weitere Eigenschaften, die in diesem Artikel allerdings nicht thematisiert werden. Diese zusätzlichen Eigenschaften können der Datei sicher hinzugefügt werden, werden von Codespaces jedoch ignoriert. Weitere Informationen finden Sie in der [Referenz zu devcontainer.json](https://code.visualstudio.com/docs/remote/devcontainerjson-reference) unter code.visualstudio.com.

## <a name="customize-with-devinit"></a>Anpassen mit devinit

[devinit](../../devinit/getting-started-with-devinit.md) ist ein Befehlszeilentool in Windows-Codespaces, mit dem Sie Frameworks und Tools in Ihrer Umgebung installieren können. Das Tool kann über eine Eingabeaufforderung (`devinit run -t require-dotnetcoresdk`) manuell ausgeführt werden, aber die vollen Kapazitäten können erst dann genutzt werden, wenn eine benutzerdefinierte [ *.devinit.json*-](../../devinit/devinit-json.md)-Datei erstellt wird, mit der Codespaces bei jedem Erstellvorgang einheitlich konfiguriert werden.

`devinit` beinhaltet mehrere Tools für das Installieren bestimmter Elemente, z. B. SQL Server und die Azure CLI. Außerdem können allgemeine Paket-Manager ausgeführt werden, z. B. chocolatey, npm und vcpkg. Die vollständige Liste der `devinit`-Tools finden Sie in der Dokumentation [Verfügbare Tools](../../devinit/devinit-tool-list.md).

### <a name="devinitjson"></a>devinit.json

Während Sie die `devinit`-Befehlszeile direkt ausführen können, wird empfohlen, die [*devinit.json*](../../devinit/devinit-json.md)-Konfigurationsdateien zu erstellen, in denen die `devinit`-Tools beschrieben werden, die ausgeführt werden sollen. 

Für die Installation des [.NET Core SDK](/dotnet/core/sdk) würde eine *.devinit.json*-Datei beispielsweise folgendermaßen aussehen:

```json
{
    "run": [
        {
            "comments": "We need the .NET Core SDK."
            "tool": "require-dotnetcoresdk"
        }
    ]
}
```

Wenn Sie eine *.devinit.json*-Datei im Stammverzeichnis Ihres Projekts erstellen, wird sie verwendet, wenn Sie `devinit init` ausführen. Standardmäßig sucht `devinit.exe` nach der Datei an folgenden Speicherorten:

1. *{current-directory}\\.devinit.json*
2. *{current-directory}\\.devinit\devinit.json*

### <a name="running-devinit-when-creating-a-codespace"></a>Ausführen von devinit beim Erstellen eines Codespace

Sie können GitHub Codespaces anweisen, `devinit` nach Erstellung eines Codespace auszuführen, indem die `postCreateCommand`-Eigenschaft in einer *devcontainers.json*-Datei verwendet wird. Wie bereits erwähnt sucht GitHub Codespaces nach einer *devcontainer.json*-Datei in Ihrem geklonten Repository, um den Codespace oder die Clientinstanz anzupassen. Außerdem werden in der `postCreateCommand`-Eigenschaft beschriebene Befehle ausgeführt.

Indem `devinit init` angegeben wird, wird `devinit` mithilfe Ihrer *devinit.json*-Konfiguration ausgeführt.

```json
{
  "postCreateCommand": "devinit init"
}
```

### <a name="an-example"></a>Beispiel

Hier finden Sie ein einfaches Beispiel für die Installation des Befehlszeilentools für .NET Core Entity Framework: `dotnet-ef`.

**devcontainer.json**

Inhalte der *.devcontainer.json*-Datei im Repositorystamm. 

```json
{
  "postCreateCommand": "devinit init"
}
```

**devinit.json**

Inhalte der *.devinit.json*-Datei. Diese Datei muss sich im selben Ordner wie *.devcontainer.json* befinden.

```json
{
    "run": [
        {
            "comments": "Install the Entity Framework tools",
            "tool": "dotnet-toolinstall",
            "input": "dotnet-ef",
        }
     ]
}
```

Weitere `devinit`-Beispiele finden Sie in der `devinit`-[Beispielliste](../../devinit/sample-readme.md).

## <a name="port-forwarding"></a>Portweiterleitung

GitHub Codespaces bietet Zugriff auf die Anwendungen und Dienste, die in Remoteumgebungen ausgeführt werden, indem Portweiterleitung verwendet wird. Standardmäßig werden aus Sicherheitsgründen keine Ports weitergeleitet. Sie können jedoch bestimmte Ports angeben, die in einem Codespace geöffnet werden sollen.

### <a name="configure-port-forwarding"></a>Konfigurieren der Portweiterleitung

Wenn es einen oder mehrere Ports gibt, die für ein bestimmtes Repository standardmäßig weitergeleitet werden sollten, kann dies mit der `forwardPorts`-Eigenschaft in der *devcontainer.json*-Datei konfiguriert werden.

* `forwardPorts`: Ein Port oder ein Array aus Ports, die lokal automatisch weitergeleitet werden sollten, wenn die Umgebung ausgeführt wird.

## <a name="installed-software-specifics"></a>Informationen zu installierter Software

### <a name="microsoft-sql-server"></a>Microsoft SQL Server

Die Express-Version von Microsoft SQL Server 2019 ist verfügbar und wird als lokaler Dienst (localdb) in der Windows-Codespaceumgebung ausgeführt. Der aktuelle Benutzer, als der Ihre App und das Visual Studio-Terminal ausgeführt werden, verfügt über SQL-Administratorrechte für die SQL Server-Instanz. Zur Verwaltung des Servers müssen Sie PowerShell im Visual Studio-Terminal oder andere Befehlszeilentools wie `dotnet-ef` verwenden. Aktuell sind SQL Server Management Studio und andere Remoteverwaltungstools nicht verfügbar.

#### <a name="example-connection-string"></a>Exemplarische Verbindungszeichenfolge

Unten finden Sie ein Beispiel für eine Verbindungszeichenfolge, mit der eine Verbindung zur lokalen Microsoft SQL Server-Instanz hergestellt wird.

```csharp
"Server=(LocalDB);Integrated Security=true;"
```

### <a name="azure-cli"></a>Azure CLI

Die Azure CLI ist in allen Windows-Codespaceumgebungen installiert und unter Pfaden als `az` verfügbar.

#### <a name="using-azure-resources"></a>Verwenden von Azure-Ressourcen

Wenn Sie eine Azure Active Directory-Identität nutzen, um Ihre Anwendung für Azure-Ressourcen zu authentifizieren, müssen Sie sich zunächst über das Visual Studio-Terminal bei Azure anmelden. Verwenden Sie zur Anmeldung den `login`-Befehl in der Azure CLI mit dem Geräteanmeldungsflow (siehe Beispiel unten). Nach der Anmeldung sollten Ihre Anwendung und die Terminalsitzung diese Identität verwenden können.

```powershell
> az login --use-device-code
```

Weitere Informationen zum `az login`-Befehl finden Sie in der [Dokumentation](/cli/azure/reference-index#az_login) zur Azure CLI.

## <a name="see-also"></a>Weitere Informationen

- [Was ist GitHub Codespaces?](codespaces-overview.md)
- [Verwenden von Visual Studio mit einem Codespace](use-visual-studio-with-codespaces.md)