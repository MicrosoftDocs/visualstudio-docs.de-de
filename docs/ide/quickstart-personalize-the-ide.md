---
title: Festlegen des dunklen Visual Studio-Designs und Ändern von Textfarben
description: Erfahren Sie, wie Sie das Standardfarbdesign von Visual Studio in den dunklen Modus und die Schriftfarben im Code-Editor ändern.
ms.date: 08/20/2020
ms.topic: how-to
ms.custom: contperf-fy21q1
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: eb7c9bf04e5f38e5138eae6cf6254bb77bbd6230
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99916063"
---
# <a name="how-to-personalize-the-visual-studio-ide-and-the-editor"></a>Vorgehensweise: Personalisieren von Visual Studio-IDE und Editor

In diesem Artikel zur Vorgehensweise wird das standardmäßige blaue Design des Visual Studio-Farbschemas in das dunkle Design geändert. Außerdem passen wir die Farben für zwei verschiedene Texttypen im Code-Editor an.

::: moniker range="vs-2017"

Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) kostenlos herunterladen.

::: moniker-end

::: moniker range=">=vs-2019"

Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads) kostenlos herunterladen.

::: moniker-end

## <a name="set-the-color-theme-for-the-ide"></a>Festlegen des Farbdesigns für die IDE

Das Standardfarbdesign für die Benutzeroberfläche von Visual Studio heißt **Blau**. Ändern Sie es in **Dunkel**.

1. Klicken Sie in der Menüleiste (die Zeile, die Menüs wie **Datei** und **Bearbeiten** enthält) auf **Extras** > **Optionen**.

1. Ändern Sie auf der Optionsseite **Umgebung** > **Allgemein** die Auswahl für **Farbdesign** in **Dunkel**, und klicken Sie dann auf **OK**.

   Das Farbdesign für die gesamte integrierten Entwicklungsumgebung in Visual Studio (Integrated Development Environment, IDE) wird in **Dunkel** geändert.

   ::: moniker range="vs-2017"

   ![Visual Studio 2017 im Design „Dunkel“](media/quickstart-personalize-dark-theme.png)

   ::: moniker-end

   ::: moniker range="vs-2019"

   ![Visual Studio 2019 im Design „Dunkel“](media/vs-2019/dark-theme.png)

   ::: moniker-end

::: moniker range="vs-2017"

> [!TIP]
> Sie können weitere vordefinierte Designs installieren, indem Sie den **Visual Studio Color Theme Editor** aus [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor) installieren. Nachdem Sie dieses Tool installiert haben, werden zusätzliche Farbdesigns in der **Farbdesign**-Dropdownliste angezeigt.

::: moniker-end

::: moniker range="vs-2019"

> [!TIP]
> Sie können Ihre eigenen Designs erstellen, indem Sie **Visual Studio Color Theme Designer** aus dem [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-madsk.ColorThemeDesigner) installieren.

::: moniker-end

## <a name="change-text-colors-in-the-editor"></a>Ändern der Textfarben im Editor

Nun passen Sie einige Textfarben für den Editor an. Erstellen Sie zunächst eine XML-Datei, um die Standardfarben anzuzeigen.

1. Klicken Sie in der Menüleiste auf **Datei** > **Neu** > **Datei**.

1. Wählen Sie im Dialogfeld **Neue Datei** unter der Kategorie **Allgemein** die Option **XML-Datei** aus, und wählen Sie dann **Öffnen** aus.

1. Fügen Sie den folgenden XML-Code unter der Zeile mit `<?xml version="1.0" encoding="utf-8"?>` ein.

   ```xml
   <Catalog>
     <Book id="bk101">
     <Author>Garghentini, Davide</Author>
     <Title>XML Developer's Guide</Title>
     <Genre>Computer</Genre>
     <Price>44.95</Price>
     <PublishDate>2000-10-01</PublishDate>
     <Description>
       An in-depth look at creating applications with XML.
     </Description>
   </Book>
   <Book id="bk102">
     <Author>Garcia, Debra</Author>
     <Title>Midnight Rain</Title>
     <Genre>Fantasy</Genre>
     <Price>5.95</Price>
     <PublishDate>2000-12-16</PublishDate>
     <Description>
       A former architect battles corporate zombies, an evil
       sorceress, and her own childhood to become queen of the world.
     </Description>
   </Book>
   </Catalog>
   ```

   Beachten Sie, dass die Zeilennummern türkisblau und die XML-Attribute (z.B. `id="bk101"`) hellblau sind. Sie ändern nun die Textfarbe für diese Elemente.

   ![Schriftfarben der XML-Datei](media/quickstart-personalize-xml-file.png)

1. Wählen Sie in der Menüleiste **Extras** > **Optionen** aus, um das Dialogfeld **Optionen** zu öffnen.

1. Wählen Sie unter **Umgebung** die Kategorie **Schriftarten und Farben** aus.

   Beachten Sie, dass der Text unter **Einstellungen anzeigen für** die Angabe **Text-Editor** enthält – dies ist so gewünscht. Erweitern Sie die Dropdownliste, um eine umfassende Liste mit Optionen anzuzeigen, die zum Ändern der Schriftarten und Farben für Text verfügbar sind.

1. Wählen Sie zum Ändern der Farbe des Zeilennummerntexts in der Liste **Elemente anzeigen** die Option **Zeilennummer** aus. Wählen Sie im Feld **Elementvordergrund** die Option **Oliv** aus.

   ![Dialogfeld „Optionen“, Kategorie „Schriftarten und Farben“](media/quickstart-personalize-line-number-color.png)

   Einige Sprachen verfügen über spezielle Einstellungen für Schriftarten und Farben. Wenn Sie ein C++-Entwickler sind, möchten Sie möglicherweise die für die Funktionen verwendete Farbe ändern. Sie können dafür z.B. nach **C++-Funktionen** in der Liste **Elemente anzeigen** suchen.

1. Bevor Sie das Dialogfeld schließen, ändern Sie noch die Farbe der XML-Attribute. Scrollen Sie in der Liste **Elemente anzeigen** nach unten bis zu **XML-Attribut**, und wählen Sie diese Option aus. Wählen Sie im Feld **Elementvordergrund** die Option **Gelbgrün** aus. Wählen Sie **OK** aus, um Ihre Auswahl zu speichern und das Dialogfeld zu schließen.

   Die Zeilennummern weisen nun die Farbe oliv auf, und die XML-Attribute leuchten in gelbgrün. Wenn Sie einen anderen Dateityp öffnen, z.B. eine C++- oder C#-Codedatei, erkennen Sie, dass die Zeilennummern auch in der Farbe oliv angezeigt werden.

   ![XML-Datei mit neuen Schriftfarben](media/quickstart-personalize-xml-file-new-colors.png)

Wir haben nur ein paar Methoden zum Anpassen der Farben in Visual Studio untersucht. Wir hoffen, dass Sie die anderen Anpassungsoptionen im Dialogfeld [**Optionen**](../ide/reference/fonts-and-colors-environment-options-dialog-box.md) ebenfalls nutzen, um Visual Studio ganz Ihren Vorstellungen anzupassen.

## <a name="see-also"></a>Weitere Informationen

- [How to: Ändern von Schriftarten, Farben und Designs in Visual Studio](../ide/how-to-change-fonts-and-colors-in-visual-studio.md)
- [Vorgehensweise: Ändern der Groß-/Kleinschreibung von Text im Editor](../ide/how-to-change-text-case-in-the-editor.md)
- [Übersicht über die Visual Studio-IDE](../get-started/visual-studio-ide.md)
