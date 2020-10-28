---
title: Debuggen von XAML in Blend | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie die Tools in Blend für Visual Studio verwenden, um XAML-Fehler in Ihrer APP zu erkennen, zu Debuggen und aufzulösen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 29a37182-2a2c-47e4-a4a9-2d5412738fed
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 91d1df06d991669b023ede60b8b384ea75af651a
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796718"
---
# <a name="debug-xaml-in-blend"></a>Debuggen von XAML in Blend

Sie können die Tools in Blend für Visual Studio verwenden, um den XAML-Code in Ihrer APP zu debuggen. Beim Erstellen eines Projekts werden alle Fehler im Bereich **Ergebnisse** angezeigt. Doppelklicken Sie auf einen Fehler, um das dazugehörige Markup zu suchen. Wenn Sie mehr Platz benötigen, können Sie das **Ergebnis** Panel durch Drücken von **F12** ausblenden.

## <a name="syntax-errors"></a>Syntaxfehler

Syntaxfehler treten auf, wenn die Formatierungsregeln der Sprache im XAML-Code oder in Code-Behind-Dateien nicht befolgt werden. Die Beschreibung des Fehlers kann bei seiner Behebung hilfreich sein. In der Liste wird auch der Name der Datei und die Nummer der Zeile angegeben, in der der Fehler auftritt. Die XAML-Fehler werden auch auf der Registerkarte **Markup** im Bereich **Ergebnisse** angezeigt.

> [!TIP]
> XAML ist eine XML-basierte Markupsprache, die XML-Syntaxregeln befolgt.

Es folgen einige häufige Ursachen für XAML-Syntaxfehler:

- Ein Schlüsselwort wurde falsch geschrieben, oder die Groß-/Kleinschreibung ist falsch.

- Um Attribute oder um Textzeichenfolgen fehlen Anführungszeichen.

- Für ein XAML-Element fehlt ein Endtag.

- Ein XAML-Element ist an einer Position vorhanden, an der es nicht zulässig ist.

Weitere Informationen über die allgemeine XAML-Syntax finden Sie in der [Anleitung zur grundlegenden XAML-Syntax](/windows/uwp/xaml-platform/xaml-syntax-guide).

Sie können auch einfache Code-Behind-Syntax Fehler, Kompilierungsfehler und Laufzeitfehler in Blend identifizieren und beheben. Für Code-Behind-Fehler können Sie dies allerdings möglicherweise in Visual Studio einfacher durchführen.

### <a name="debugging-sample-xaml-code"></a>Debuggen von XAML-Beispielcode

Das folgende Beispiel führt Sie durch eine einfache XAML-Debuggingsitzung in Blend.

#### <a name="to-create-a-project"></a>So erstellen Sie ein Projekt

1. Öffnen Sie in Blend das Menü **Datei** , und klicken Sie dann auf **Neues Projekt** .

    Auf der linken Seite des Dialogfelds **Neues Projekt** wird eine Liste der Projekttypen angezeigt. Wenn Sie auf einen Projekttyp klicken, werden die Projektvorlagen, die diesem Typ zugeordnet sind, auf der rechten Seite angezeigt.

2. Klicken Sie in der Liste der Projekttypen auf **Windows Universal** .

3. Klicken Sie in der Liste der Projektvorlagen auf **leere app (universelle Windows-APP)** .

4. Geben Sie im Textfeld **Name den Namen** ein `DebuggingSample` .

5. Überprüfen Sie im Textfeld **Speicherort** den Projektspeicherort.

6. Klicken Sie im Listenfeld **Sprache** auf **Visual C#** , und klicken Sie dann auf **OK** , um das Projekt zu erstellen.

7. Klicken Sie mit der rechten Maustaste auf die Entwurfsoberfläche, und klicken Sie dann auf **Quelle anzeigen** , um zur Ansicht **Geteilt** zu wechseln.

8. Kopieren Sie den folgenden Code, indem Sie auf den Link **Kopieren** in der rechten oberen Ecke des Codes klicken.

   ```xml
   <Grid HorizontalAlignment="Left" Height="222" VerticalAlignment="Top>
        <Button content="Button" x:Mame="Home" HorizontalAlignment="Left" VerticalAlignment="Top"/>
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,38,0,0">
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,75,0,0"/>
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,112,0,0"/>
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top Margin="0,149,0,0"/>
   </Grid>
   ```

9. Suchen Sie das standardmäßige **Raster** , und fügen Sie den Code zwischen den **Grid** -Start- und Endtags ein. Anschließend sollte der Code ungefähr wie folgt aussehen:

    ```xml
    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
         <Grid HorizontalAlignment="Left" Height="222" VerticalAlignment="Top>
              <Button content="Button" x:Mame="Home" HorizontalAlignment="Left" VerticalAlignment="Top"/>
              <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,38,0,0">
              <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,75,0,0"/>
              <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,112,0,0"/>
              <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top Margin="0,149,0,0"/>
         </Grid>
    </Grid>
    ```

10. Drücken Sie **STRG** + **UMSCHALT** + **B** , um das Projekt zu erstellen.

    Eine Fehlermeldung wird angezeigt, dass das Projekt nicht erstellt werden kann. Im unteren Bereich der App wird zudem der Bereich **Ergebnisse** mit der Liste der Fehler angezeigt.

    ![Debuggen von XAML in Blend für Visual Studio](../debugger/media/blend_debugxaml_xaml.png "blend_debugXAML_XAML")

### <a name="resolve-xaml-errors"></a>Auflösen von XAML-Fehlern

Wenn XAML-Fehler ermittelt werden, zeigt die Entwurfsoberfläche eine Warnung an, dass das Projekt ungültiges Markup enthält. Während Sie die Fehler beheben, wird die Fehlerliste im Bereich **Ergebnisse** aktualisiert. Wenn Sie alle Fehler behoben haben, wird die Entwurfsoberfläche aktiviert und die App wird darin angezeigt.

#### <a name="to-resolve-the-xaml-errors"></a>So beheben Sie die XAML-Fehler

1. Doppelklicken Sie auf den ersten Fehler in der Fehlerliste. Die Beschreibung lautet: "The value '<' is not valid in an attribute." (Der Wert „<“ ist in Attributen ungültig). Wenn Sie auf den Fehler doppelklicken, ermittelt der Zeiger die entsprechende Position im Code. `<` vor `Button` ist gültig und kein Attribut, wie in der Fehlermeldung beschrieben. Wenn Sie die vorhergehende Codezeile prüfen, stellen Sie fest, dass die schließenden Anführungszeichen für das `Top`-Attribut fehlen. Geben Sie die schließenden Anführungszeichen ein. Die Fehlerliste im Bereich **Ergebnisse** wird aktualisiert, um die Änderung zu reflektieren.

2. Doppelklicken Sie auf die Beschreibung "0" ist am Anfang eines Namens ungültig. " `Margin="0,149,0,0"` scheint wohl geformt zu sein. Allerdings stimmt der Farbcode für `Margin` nicht mit den anderen Instanzen von `Margin` im Code überein. Da für das vorangehende Name-Wert-Paar die schließenden Anführungszeichen fehlen (`VerticalAlignment="Top`), wird `Margin="` als Teil des Werts des vorangehenden Attributs gelesen, und 0 wird als Anfang von einem Name-Wert-Paar gelesen. Geben Sie die schließenden Anführungszeichen für `Top` ein. Die Fehlerliste im Bereich **Ergebnisse** wird aktualisiert, um die Änderung zu reflektieren.

3. Doppelklicken Sie auf den verbleibenden Fehler: "Das schließende XML-Tag 'Button' ist falsch zugeordnet." Der Zeiger befindet sich beim **Grid** -Endtag (`</Grid>`), um anzugeben, dass der Fehler mutmaßlich im `Grid`-Objekt ist. Beachten Sie, dass das Endtag für das `Button`-Objekt fehlt. Nachdem Sie das `/`-Endtag hinzugefügt haben, wird die Liste im Bereich **Ergebnisse** aktualisiert. Nach dem Beheben dieser Anfangsfehler wurden zwei weitere Fehler identifiziert.

4. Doppelklicken Sie auf: "Das Element 'content' wurde nicht erkannt, oder es kann nicht auf das Element zugegriffen werden." Das `c` in `content` muss groß geschrieben sein. Ersetzen Sie das klein geschriebene "c" durch ein groß geschriebenes "C".

5. Doppelklicken Sie auf "die Mame-Eigenschaft ist im- `http://schemas.microsoft.com/winfx/2006/xaml` Namespace nicht vorhanden." Das "M" in "Mame" muss ein "N" sein. Ersetzen Sie das "M" durch ein "N". Da der XAML-Code jetzt verarbeitet werden kann, wird die App auf der Entwurfsoberfläche angezeigt.

    ![Debuggen von XAML in Blend für Visual Studio](../debugger/media/blend_debugartboard_xaml.png "blend_debugArtboard_XAML")

    Drücken Sie **STRG** + **UMSCHALT** + **B** , um das Projekt zu erstellen, und vergewissern Sie sich, dass keine weiteren Fehler vorhanden sind.

## <a name="debug-in-visual-studio"></a>Debuggen in Visual Studio

Sie können Blend-Projekte in Visual Studio öffnen, um den Code in Ihrer APP leichter zu debuggen. Um ein Blend-Projekt in Visual Studio zu öffnen, klicken Sie im **Projekt Panel mit der rechten** Maustaste auf das Projekt, und klicken Sie dann auf **in Visual Studio bearbeiten** . Nachdem Sie die Debugsitzung in Visual Studio abgeschlossen haben, drücken Sie STRG + UMSCHALT + S, um alle Änderungen zu speichern, und wechseln Sie dann zurück zu Blend. Sie werden aufgefordert, das Projekt erneut zu laden. Klicken Sie **auf Ja, um** die Arbeit in Blend fortzusetzen.

Weitere Informationen zum Debuggen Ihrer App finden Sie unter [Debuggen von UWP-apps in Visual Studio](../debugger/debugging-windows-store-and-windows-universal-apps.md).

## <a name="get-help"></a>Hilfe erhalten

Wenn Sie weitere Hilfe beim Debuggen Ihrer Blend-App benötigen, können Sie im [UWP-App-Communityforum](https://social.msdn.microsoft.com/Forums/windowsapps/home?category=windowsapps) nach Beiträgen suchen, die Ihr Problem betreffen, oder eine Frage stellen.
