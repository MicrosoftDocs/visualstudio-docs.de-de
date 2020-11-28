---
title: Anpassen von Fensterlayouts
description: Erfahren Sie, wie die Merkmale von Windows angepasst werden, um Layouts zu erstellen, die für verschiedene Entwicklungsworkflows am besten geeignet sind.
ms.custom: SEO-VS-2020
ms.date: 07/31/2020
ms.topic: conceptual
f1_keywords:
- vs.windows
- vs.environment
helpviewer_keywords:
- windows [Visual Studio], managing
- custom window configurations
- layout [Visual Studio], window management
- document windows [Visual Studio]
- interface modes
- AutoHide windows
- MDI, window interface modes
- multiple monitors
- Tabbed Document mode
- debug mode
- custom layouts
ms.assetid: 7517ff13-76de-4ecf-9c1b-eb9b7ff4d718
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c433a6faf3eab9dd959cc25f26033c74852c0899
ms.sourcegitcommit: 66cda27b63c9b55782b1db223a6dbda9f8cabe13
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2020
ms.locfileid: "95006665"
---
# <a name="customize-window-layouts-in-visual-studio"></a>Anpassen von Fensterlayouts in Visual Studio

In Visual Studio können Sie Position, Größe und Verhalten von Fenstern anpassen, um Fensterlayouts zu erstellen, die für unterschiedliche Entwicklungsworkflows am besten geeignet sind. Wenn Sie das Layout anpassen, wird dies in der IDE gespeichert. Wenn Sie z. B. die Andockposition des **Projektmappen-Explorers** ändern und Visual Studio dann schließen, ist der **Projektmappen-Explorer** nach dem nächsten Öffnen von Visual Studio an derselben Position angedockt, selbst wenn Sie an einem anderen Computer arbeiten.

Sie können ein benutzerdefiniertes Layout auch benennen und speichern und dann mit einem einzelnen Befehl zwischen den Layouts wechseln. Beispielsweise können Sie ein Layout für die Bearbeitung und ein Layout für das Debuggen erstellen und zwischen diesen mithilfe des Menübefehls **Fenster** > **Fensterlayout anwenden** wechseln.

## <a name="tool-and-document-windows"></a>Tool- und Dokumentfenster

Die IDE verfügt über zwei grundlegende Fenstertypen *Toolfenster* und *Dokumentfenster*. Toolfenster sind in **Projektmappen-Explorer**, **Server-Explorer**, **Ausgabefenster**, **Fehlerliste** sowie im Designer, in den Debuggerfenstern usw. enthalten. Dokumentfenster enthalten Quellcodedateien, beliebige Textdateien, Konfigurationsdateien usw. Die Größe der Toolfenster kann angepasst werden, und sie können an der Titelleiste gezogen werden. Dokumentfenster können an der Registerkarte gezogen werden. Klicken Sie zum Festlegen anderer Optionen für das Fenster mit der rechten Maustaste auf die Registerkarte oder die Titelleiste.

Im Menü **Fenster** werden Optionen zum Andocken, Abdocken und Ausblenden von Fenstern in der IDE angezeigt. Klicken Sie mit der rechten Maustaste auf eine Fensterregisterkarte oder Titelleiste, um weitere Optionen für ein bestimmtes Fenster anzuzeigen. Sie können mehrere Instanzen bestimmter Toolfenster gleichzeitig anzeigen. Sie können z. B. mehrere Webbrowserfenster anzeigen und zusätzliche Instanzen bestimmter Toolfenster erstellen, indem Sie **Neues Fenster** im Menü **Fenster** wählen.

### <a name="split-windows"></a>Geteilte Fenster

Wenn Sie zwei Positionen gleichzeitig in einem Dokument anzeigen oder bearbeiten müssen, können Sie die Fenster teilen. Um das Dokument in zwei Abschnitte zu teilen, durch die unabhängig voneinander gescrollt werden kann, klicken Sie auf **Teilen** im Menü **Fenster** . Klicken Sie auf **Teilung aufheben** im Menü **Fenster** , um die ursprüngliche Ansicht wiederherzustellen.

### <a name="tabs"></a>Registerkarten

Mithilfe von Registerkarten können Sie Ihr Layout auf unterschiedliche Weise anordnen. Sie können beispielsweise eine Vorschau einer Datei im Editor anzeigen, ohne die Datei zu öffnen. Sie können Ihre Registerkarten gruppieren und viele weitere Anpassungen vornehmen.

#### <a name="preview-tab-document-windows"></a>Registerkarte „Vorschau“ (Dokumentfenster)

Auf der Registerkarte **Vorschau** können Sie Dateien im Editor anzeigen, ohne sie zu öffnen. Sie können die Vorschau für Dateien anzeigen, indem Sie diese im **Projektmappen-Explorer** auswählen, während des Debuggens die einzelnen Dateien durchlaufen, mit der Option **Gehe zu Definition** oder beim Durchsuchen der Suchergebnisse. Vorschaudateien werden auch in einer Registerkarte auf der rechten Seite der Dokumentregisterkarte angezeigt. Die Datei wird zum Bearbeiten geöffnet, wenn Sie sie ändern oder auf **Öffnen** klicken.

::: moniker range="vs-2019"

#### <a name="vertical-document-tabs"></a>Vertikale Registerkarten für Dokumente

**[Neu in Version 16.4](/visualstudio/releases/2019/release-notes-v16.4/)** : Wir haben eine der häufigsten Featureanfragen in die Visual Studio 2019-Version 16.4 eingebaut: [vertikale Registerkarten für Dokumente](https://developercommunity.visualstudio.com/idea/467369/vertical-group-tab.html). Jetzt können Sie Ihre Dokumentregisterkarten in einer vertikalen Liste auf der linken oder rechten Seite des Editors verwalten.

Sie können vertikale Registerkarten für Dokumente auf folgende Weise anwenden:

- Wählen Sie in der Menüleiste die Optionen **Extras** > **Optionen** > **Umgebung** > **Registerkarten und Fenster** aus. Wählen Sie dann im Steuerelement **Registerkartenlayout festlegen** aus der Dropdownliste **Oben**, **Links** oder **Rechts** aus.

- Klicken Sie mit der rechten Maustaste auf eine Registerkarte, wählen Sie **Registerkartenlayout festlegen** aus, und wählen Sie dann **Links** oder **Rechts** aus. (Um die Registerkarten auf ihre Standardposition zurückzusetzen, wählen Sie **Oben** aus.)

    :::image type="content" source="./media/vs-2019/vertical-tabs.gif" alt-text="Eine Animation, die vertikale Dokumentregisterkarten in Aktion zeigt":::

::: moniker-end

#### <a name="tab-groups"></a>Registerkartengruppen

Mit Registerkartengruppen können Sie den begrenzten Platz im Arbeitsbereich besser verwalten, wenn Sie mit zwei oder mehr offenen Dokumenten in der IDE arbeiten. Sie können mehrere Dokument- und Toolfenster in vertikalen oder horizontalen Registerkartengruppen anordnen und Dokumente zwischen den Registerkartengruppen verschieben.

### <a name="toolbars"></a>Symbolleisten

Sie können Symbolleisten anordnen, indem Sie sie per Drag & Drop an die gewünschte Position ziehen oder indem Sie die Positionen im Dialogfeld **Anpassen** festlegen. Weitere Informationen zur Anordnung und Anpassung von Symbolleisten finden Sie unter [Vorgehensweise: Anpassen von Menüs und Symbolleisten](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md).

## <a name="arrange-and-dock-windows"></a>Anordnen und Andocken von Fenstern

Dokumentfenster und Toolfenster können *angedockt* werden, sodass sie innerhalb des Rahmens des IDE-Fensters eine bestimmte Position und Größe haben. Sie können die Fenster auch als abgedockte Fenster außerhalb der IDE positionieren.

Ein Toolfenster kann an jeder Stelle innerhalb des IDE-Rahmens angedockt werden. Einige Toolfenster lassen sich auch als Fenster mit Registerkarten im Editor-Rahmen andocken. Sie können Dokumentfenster innerhalb des Editor-Rahmens andocken und an ihrer aktuellen Position in der Registerkartenreihe anheften.

Sie können auch mehrere Fenster per *Rafting* außerhalb der IDE andocken. Toolfenster können ausgeblendet oder minimiert werden.

Fenster können auf die folgenden Weisen angeordnet werden:

- Heftet Dokumentfenster auf der linken Seite der Registerkartenreihe an.

- Andocken von Fenstern am Bearbeitungsrahmen

- Andocken von Toolfenstern am Rand eines Frames in der IDE.

- Verschieben von Dokument- oder Toolfenstern über die IDE bzw. außerhalb der IDE.

- Verbergen von Toolfenstern am Rand der IDE.

- Anzeigen von Fenstern auf verschiedenen Bildschirmen.

- Zurücksetzen der Fensteranordnung auf das Standardlayout oder ein gespeichertes benutzerdefiniertes Layout.

Um Tool- und Dokumentfenster anzuordnen, können Sie den Cursor auf die Titelleiste eines Fensters platzieren und ihn dann dahin ziehen, wo Sie das Fenster positionieren möchten. Alternativ dazu können Sie mit der rechten Maustaste auf die Titelleiste des Fensters klicken und das Kontextmenü verwenden, oder Sie können die Befehle im Menü **Fenster** verwenden.

### <a name="dock-windows"></a>Andocken von Fenstern

Beim Klicken und Ziehen der Titelleiste eines Toolfensters oder der Registerkarte im Dokumentfenster wird ein Diamant-Führungssymbol angezeigt. Während des Ziehvorgangs wird, wenn sich der Mauszeiger über einem der Pfeile im Diamanten befindet, ein schattierter Bereich angezeigt, der anzeigt, wo das Fenster angedockt wird, wenn Sie die Maustaste loslassen.

Halten Sie beim Ziehen eines Fensters die **STRG-TASTE** gedrückt, um ein andockbares Fenster ohne Einrasten zu verschieben.

Drücken Sie zum Zurückkehren an die letzte Andockposition eines Tool- oder Dokumentfensters **STRG**, während Sie auf die Titelleiste oder die Registerkarte des Fensters doppelklicken.

Die folgende Abbildung veranschaulicht das Diamant-Führungssymbol für Dokumentfenster, das nur im Bearbeitungsrahmen angedockt werden kann:

![Rastersymbol im Dokumentfenster](../ide/media/documentwindowguidediamonds.png)

Toolfenster können an einer Seite eines Frames in der IDE oder innerhalb des Bearbeitungsrahmens angebunden werden. Ein Rauten-Führungssymbol wird angezeigt, wenn Sie ein Toolfenster an eine andere Position ziehen, damit Sie das Fenster problemlos neu andocken können.

![Diamant-Führungssymbole im Toolfenster](../ide/media/vs10guidediamond.png)

In der folgenden Abbildung ist der **Projektmappen-Explorer** an einer neuen Position angedockt, die durch den blau schattierten Bereich angegeben wird:

![Andocken des Projektmappen-Explorers an einer neuen Position](../ide/media/vs2015_dock_diamond.png)

### <a name="close-and-auto-hide-tool-windows"></a>Schließen und automatisches Ausblenden von Toolfenstern

Sie können ein Toolfenster schließen, indem Sie auf das **X** oben rechts in der Titelleiste klicken. Um das Fenster wieder zu öffnen, verwenden Sie seine Tastenkombination oder seinen Menübefehl. Toolfenster unterstützen das Feature *Automatisch im Hintergrund*, mit der ein Fenster bei Verwendung eines anderen Fensters in den Hintergrund versetzt wird und ist somit nicht mehr sichtbar ist. Wenn ein Fenster automatisch ausgeblendet wird, wird sein Name auf einer Registerkarte am Rand der IDE angezeigt. Um das Fenster wieder zu verwenden, zeigen Sie auf die Registerkarte, damit das Fenster wieder angezeigt wird.

![Automatisch im Hintergrund](../ide/media/vs2015_auto_hide.png)

> [!NOTE]
> Legen Sie fest, ob die Funktion „Automatisch im Hintergrund“ in Toolfenstern einzeln oder als angedockte Gruppe ausgeführt wird, indem Sie im Dialogfeld **Optionen** das Kontrollkästchen **Schaltfläche „Automatisch ausblenden“ bezieht sich nur auf aktives Toolfenster** aktivieren oder deaktivieren. Weitere Informationen finden Sie im Artikel zu den Dialogfeldern [Allgemein, Umgebung und Optionen](../ide/reference/general-environment-options-dialog-box.md).

> [!NOTE]
> Toolfenster, für die die Option „Automatisch im Hintergrund“ aktiviert ist, werden möglicherweise kurz eingeblendet, sobald das Fenster den Fokus erhält. Zum Ausblenden des Fensters wählen Sie ein Element außerhalb des aktuellen Fensters aus. Wenn das Fenster den Fokus verliert, wird es ausgeblendet.

### <a name="use-a-second-monitor"></a>Verwenden eines zweiten Monitors

Wenn Sie einen zweiten Bildschirm besitzen und dieser vom Betriebssystem unterstützt wird, können Sie angeben, auf welchem Bildschirm ein Fenster angezeigt werden soll. Sie können mehrere Fenster sogar in *Rafts* auf anderen Bildschirmen gruppieren.

> [!TIP]
> Sie können auch mehrere Instanzen von **Projektmappen-Explorer** erstellen und auf einen anderen Bildschirm verschieben. Klicken Sie mit der rechten Maustaste in das Fenster und wählen Sie **Neue Projektmappen-Explorer-Ansicht** aus. Sie können alle Fenster wieder zum ursprüngliche Bildschirm zurückkehren lassen, indem Sie auf **STRG** drücken und gleichzeitig doppelklicken.

### <a name="reset-name-and-switch-between-window-layouts"></a>Zurücksetzen, Benennen und Wechseln zwischen Fensterlayouts

Sie können die IDE mit dem Befehl **Fensterlayout zurücksetzen** auf das ursprüngliche Fensterlayout für Ihre Einstellungsauflistung zurücksetzen. Beim Ausführen dieses Befehls geschieht Folgendes:

- Alle Fenster werden an ihre Standardpositionen verschoben.

- Fenster, die im Standardfensterlayout geschlossen sind, werden geschlossen.

- Fenster, die im Standardfensterlayout geöffnet sind, werden geöffnet.

### <a name="create-and-save-custom-layouts"></a>Erstellen und Speichern von benutzerdefinierten Layouts

Mit Visual Studio können Sie bis zu 10 benutzerdefinierte Fensterlayouts speichern und schnell zwischen diesen wechseln. Die folgenden Schritte zeigen Ihnen, wie Sie benutzerdefinierte Layouts, mit denen Sie die Vorteile mehrerer Monitore mit angedockten Fenstern und unverankerten Toolfenstern nutzen können, erstellen, speichern, aufrufen und verwalten.

Erstellen Sie zunächst eine Testprojektmappe mit zwei Projekten, die jeweils über ein optimales Layout verfügen.

#### <a name="create-a-ui-project-and-customize-the-layout"></a>Erstellen eines Benutzeroberflächenprojekts und individuelles Anpassen des Layouts

1. Erstellen Sie ein neues C# **WPF-App** Projekt. Stellen Sie sich vor, dass Sie in diesem Projekt eine Benutzeroberfläche entwickeln werden. Sie möchten den Platz für das Designerfenster maximieren und andere Toolfenster aus dem Weg räumen.

2. Wenn Sie über mehrere Monitore verfügen, ziehen Sie das Fenster **Projektmappen-Explorer** und das Fenster **Eigenschaften** auf den zweiten Monitor. Versuchen Sie, wenn Ihnen nur ein Monitor zur Verfügung steht, alle Fenster außer dem Designerfenster zu schließen.

3. Drücken Sie **STRG**+**ALT**+**X**, um das **Toolboxfenster** anzuzeigen. Ist das Fenster angedockt, ziehen Sie es so, dass es sich freischwebend dort befindet, wo Sie es platzieren möchten.

4. Drücken Sie **F5**, um Visual Studio in den Debugmodus zu versetzen. Passen Sie die Position der Debugfenster **Auto**, **Aufrufliste** und **Ausgabe** an Ihre Anforderungen an. Das Layout, das Sie erstellen, ist sowohl für den Bearbeitungsmodus als auch den Debugmous geeignet.

5. Wenn Sie die Layouts sowohl im Debugmodus als auch im Bearbeitungsmodus Ihren Anforderungen angepasst haben, klicken Sie auf **Fenster** > **Fensterlayout speichern**. Nennen Sie dieses Layout „Designer“.

     Beachten Sie, dass das neue Layout der nächsten Tastenkombination aus der reservierten Liste mit **STRG**+**ALT**+**1...0** zugewiesen wird.

#### <a name="create-a-database-project-and-layout"></a>Erstellen eines Datenbankprojekts und eines Layouts

1. Fügen Sie der Projektmappe ein neues **SQL Server-Datenbankprojekt** hinzu.

2. Rechtsklicken Sie im **Projektmappen-Explorer** auf das neue Projekt, und klicken Sie auf **In Objekt-Explorer anzeigen**. Dadurch wird das Fenster **SQL Server-Objekt-Explorer** angezeigt, mit dem Sie auf Tabellen, Ansichten und andere Objekte in der Datenbank zugreifen können. Dieses Fenster kann entweder schwebend sein oder angedockt bleiben. Passen Sie die anderen Toolfenster wie gewünscht an. Um das Beispiel realistischer zu gestalten, können Sie eine tatsächliche Datenbank hinzufügen. Für diese exemplarische Vorgehensweise ist das jedoch nicht notwendig.

3. Wenn das Layout Ihren Vorstellungen entspricht, klicken Sie im Hauptmenü auf **Fenster** > **Fensterlayout speichern**. Nennen Sie dieses Layout „DB Project“. (Für dieses Projekt ist kein Layout für den Debugmodus erforderlich.)

#### <a name="switch-between-the-layouts"></a>Wechseln zwischen Layouts

Sie können mit Tastenkombinationen zwischen Layouts wechseln, oder klicken Sie im Hauptmenü auf **Fenster** > **Fensterlayout anwenden**.

![Menü „Apply window layout“](../ide/media/vs2015_applywindowlayout.png)

Nachdem Sie das Benutzeroberflächenlayout angewendet haben, beachten Sie, wie das Layout im Bearbeitungs- und im Debugmodus beibehalten wird.

Wenn Sie an Ihrem Arbeitsplatz mehrere Monitore und zuhause einen Laptop mit nur einem Monitor nutzen, können Sie Layouts erstellen, die für den jeweiligen Computer optimiert sind.

> [!NOTE]
> Wenn Sie ein für mehrere Monitore konzipiertes Layout mit einem einzelnen Monitor nutzen, werden die frei schwebenden Fenster, die Sie auf dem zweiten Monitor platziert haben, durch das Visual Studio-Fenster verdeckt. Sie können diese Fenster in den Vordergrund bewegen, indem Sie **ALT+TAB** drücken. Wenn Sie später Visual Studio mit mehreren Monitoren öffnen, können Sie die Fenster wieder auf die festgelegten Positionen verschieben, indem Sie das Layout erneut anwenden.

#### <a name="manage-and-roam-your-layouts"></a>Verwalten der Layouts und Ausführen von Roamings

Sie können benutzerdefinierte Layouts entfernen, umbenennen oder neu arrangieren, indem Sie auf **Fenster** > **Fensterlayouts verwalten** klicken. Wenn Sie ein Layout verschieben, wird die Schlüsselbindung automatisch so angepasst, dass die neue Position in der Liste wiedergegeben wird. Die Bindung kann nicht auf andere Weise geändert werden. Daher können Sie maximal 10 Layouts gleichzeitig speichern.

![Fensterlayouts verwalten](../ide/media/managewindowlayouts.png)

Klicken Sie auf **Fenster** > **Fensterlayout anwenden**, um nachzusehen, welche Tastenkombination welchem Layout zugeordnet ist.

Für diese Layouts wird automatisch Roaming zwischen Visual Studio-Editionen ausgeführt, ebenso zwischen Blend-Instanzen auf unterschiedlichen Computern sowie zwischen einer Express-Edition und jeder beliebigen anderen Express-Organisation. Die Layouts können jedoch nicht zwischen Visual Studio, Blend und Express wandern.

## <a name="see-also"></a>Siehe auch

- [How to: Navigieren in der IDE](../ide/how-to-move-around-in-the-visual-studio-ide.md)
