---
title: Hallo Welt-Erweiterungstutorial | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie einen neuen Befehl als Erweiterung zu Visual Studio hinzufügen. Dazu gehört das Erstellen eines Projekts, das Hinzufügen eines Befehls und das Ändern des Quellcodes.
ms.custom: SEO-VS-2020
ms.date: 03/14/2019
ms.topic: tutorial
ms.assetid: f74e1ad1-1ee5-4360-9bd5-d82467b884ca
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7e943da6745832cbe59cfe94013650a503265636
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903293"
---
# <a name="tutorial---create-your-first-extension-hello-world"></a>Tutorial – Erstellen Ihrer ersten Erweiterung: Hello World

Dieses Hallo Welt-Beispiel führt Sie durch die Erstellung Ihrer ersten Erweiterung für Visual Studio. In diesem Tutorial wird gezeigt, wie Sie in Visual Studio einen neuen Befehl hinzufügen.

In diesem Prozess lernen Sie Folgendes:

* **[Erstellen eines Erweiterbarkeitsprojekts](#create-an-extensibility-project)**
* **[Hinzufügen eines benutzerdefinierten Befehls](#add-a-custom-command)**
* **[Ändern des Quellcodes](#modify-the-source-code)**
* **[Führen Sie das Skript aus.](#run-it)**

In diesem Beispiel verwenden Sie Visual C#, um eine benutzerdefinierte Menüschaltfläche namens „Sag Hallo Welt!“ hinzuzufügen. Diese sieht folgendermaßen aus:

![Hallo Welt-Befehl](media/hello-world-say-hello-world.png)

> [!NOTE]
> Dieser Artikel gilt für Visual Studio unter Windows. Informationen zu Visual Studio für Mac finden Sie unter [Exemplarische Vorgehensweise: Erweitern von Visual Studio für Mac](/visualstudio/mac/extending-visual-studio-mac-walkthrough).

## <a name="prerequisites"></a>Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie die Workload **Visual Studio-Extensionentwicklung** installiert haben, die die benötigte VSIX-Vorlage und Beispielcode enthält.

> [!NOTE]
> Sie können eine beliebige Edition von Visual Studio (Community, Professional oder Enterprise) verwenden, um ein Visual Studio-Erweiterbarkeitsprojekt zu erstellen.

## <a name="create-an-extensibility-project"></a>Erstellen eines Erweiterbarkeitsprojekts

::: moniker range="vs-2017"

Schritt 1: Klicken Sie im Menü **Datei** auf **Neu** > **Projekt**.

Schritt 2: Geben Sie im Suchfeld in der oberen rechten Ecke „vsix“ ein, und klicken Sie auf das Visual C#-**VSIX-Projekt**. Geben Sie unten im Dialogfeld „HelloWorld“ als **Name** ein, und klicken Sie auf **OK**.

![Neues Projekt](media/hello-world-new-project.png)

Nun sollten die Seite „Erste Schritte“ und einige Beispielressourcen angezeigt werden.

Wenn Sie dieses Tutorial verlassen müssen und dann wieder zurückkommen, finden Sie Ihr neues „HelloWorld“-Projekt auf der **Startseite** im Abschnitt **Zuletzt verwendet**.

::: moniker-end

::: moniker range=">=vs-2019"

Schritt 1: Klicken Sie im Menü **Datei** auf **Neu** > **Projekt**. Suchen Sie nach „vsix“, klicken Sie auf das Visual C#-**VSIX-Projekt** und dann auf **Weiter**.

Schritt 2: Geben Sie für **Projektname** „HelloWorld“ ein, und klicken Sie auf **Erstellen**.

![Neues Projekt](media/hello-world-new-project-2019.png)

Nun sollte das „HelloWorld“-Projekt im **Projektmappen-Explorer** angezeigt werden.

::: moniker-end

## <a name="add-a-custom-command"></a>Hinzufügen eines benutzerdefinierten Befehls

Schritt 1: Wenn Sie die Manifestdatei *.vsixmanifest* auswählen, können Sie sehen, welche Optionen geändert werden können (z. B. Beschreibung, Autor und Version).

Schritt 2: Klicken Sie mit der rechten Maustaste auf das Projekt (nicht auf die Projektmappe). Klicken Sie im Kontextmenü auf **Hinzufügen** und dann auf **Neues Element**.

Schritt 3: Klicken Sie auf den Abschnitt **Erweiterbarkeit** und dann auf **Befehl**.

Schritt 4. Geben Sie unten im Feld **Name** einen Dateinamen wie beispielsweise *Command.cs* ein.

![Benutzerdefinierter Befehl](media/hello-world-vsix-command.png)

Die neue Befehlsdatei wird im **Projektmappen-Explorer** angezeigt. Unter dem Knoten **Ressourcen** finden Sie weitere Dateien, die sich auf den Befehl beziehen. Wenn Sie beispielsweise das Bild ändern möchten, befindet sich hier die PNG-Datei.

## <a name="modify-the-source-code"></a>Ändern des Quellcodes

An diesem Punkt werden der Befehl und der Schaltflächentext automatisch generiert, sodass dies für diese Vorgänge nicht sehr interessant ist. Sie können die VSCT- und CS-Datei ändern, wenn Sie Änderungen vornehmen möchten.

* In der VSCT-Datei können Sie die Befehle umbenennen und definieren, wo diese im Visual Studio-Befehlssystem platziert werden. Beim Durchsuchen der VSCT-Datei werden Kommentare angezeigt, die erläutern, was mit den einzelnen Abschnitten des VSCT-Codes gesteuert wird.

* In der CS-Datei können Sie Aktionen definieren (z. B. den Klickhandler).

::: moniker range="vs-2017"

Schritt 1: Im **Projektmappen-Explorer** finden Sie die VSCT-Datei für Ihren neuen Befehl. In diesem Fall heißt die Datei *CommandPackage.vsct*.

![CommandPackage.vsct](media/hello-world-command-package-vsct.png)

::: moniker-end

::: moniker range=">=vs-2019"

Schritt 1: Im **Projektmappen-Explorer** finden Sie die VSCT-Datei für das VS-Erweiterungspaket. In diesem Fall heißt die Datei *HelloWorldPackage.vsct*.

::: moniker-end

Schritt 2: Ändern Sie den Parameter `ButtonText` in `Say Hello World!`.

```xml
  ...
  <Button guid="guidCommandPackageCmdSet" id="CommandId" priority="0x0100" type="Button">
     <Parent guid="guidCommandPackageCmdSet" id="MyMenuGroup" />
     <Icon guid="guidImages" id="bmpPic1" />
     <Strings>
        <ButtonText>Say Hello World!</ButtonText>
     </Strings>
  </Button>
  ...
```

Schritt 3: Navigieren Sie zurück zum **Projektmappen-Explorer**, und suchen Sie die Datei *Command.cs*. Ändern Sie in der `Execute`-Methode die Zeichenfolge `message` von `string.Format(..)` in `Hello World!`.

```csharp
  ...
  private void Execute(object sender, EventArgs e)
  {
    ThreadHelper.ThrowIfNotOnUIThread();
    string message = "Hello World!";
    string title = "Command";

    // Show a message box to prove we were here
    VsShellUtilities.ShowMessageBox(
        this.ServiceProvider,
        message,
        title,
        OLEMSGICON.OLEMSGICON_INFO,
        OLEMSGBUTTON.OLEMSGBUTTON_OK,
        OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST);
  }
  ...
```

Stellen Sie sich, dass Sie alle Änderungen an den Dateien speichern.

## <a name="run-it"></a>Führen Sie das Skript aus.

Sie können nun den Quellcode in der experimentellen Instanz von Visual Studio ausführen.

Schritt 1: Drücken Sie **F5**, um den Befehl **Debuggen starten** auszuführen. Mit diesem Befehl wird das Projekt erstellt und der Debugger gestartet. Eine neue Instanz von Visual Studio wird gestartet, die als **experimentelle Instanz** bezeichnet wird.

::: moniker range="vs-2017"

Die Bezeichnung **Experimentelle Instanz** wird in der Titelleiste von Visual Studio angezeigt.

![„Experimentelle Instanz“ in der Titelleiste](media/hello-world-exp-instance.png)

::: moniker-end

Schritt 2: Klicken Sie im Menü **Extras** der **experimentellen Instanz** auf **Sag Hallo Welt!** .

![Endergebnis](media/hello-world-final-result.png)

Die Ausgabe des neuen benutzerdefinierten Befehls, nämlich **Hallo Welt**, sollte in diesem Fall im Dialogfeld in der Mitte des Bildschirms angezeigt werden. Meldung.

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie nun mit den Grundlagen der Visual Studio-Erweiterbarkeit vertraut sind, finden Sie hier weitere Informationen:

* [Beginnen mit dem Entwickeln von Visual Studio-Erweiterungen:](starting-to-develop-visual-studio-extensions.md) Beispiele, Tutorials und Veröffentlichen der Erweiterung
* [Neuigkeiten im Visual Studio 2017-SDK:](what-s-new-in-the-visual-studio-2017-sdk.md) Neue Erweiterbarkeitsfeatures in Visual Studio 2017
* [Neuigkeiten im Visual Studio 2019-SDK:](whats-new-visual-studio-2019-sdk.md) Neue Erweiterbarkeitsfeatures in Visual Studio 2019
* [Informationen zum Visual Studio-SDK:](internals/inside-the-visual-studio-sdk.md) Details im Zusammenhang mit der Visual Studio-Erweiterbarkeit
