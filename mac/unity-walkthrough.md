---
title: Erste Schritte beim Erstellen von Spielen mit Unity
description: Erste Schritte mit Unity und Visual Studio für Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/09/2020
ms.technology: vs-ide-general
ms.assetid: D07FA43B-9D18-4DFA-8343-CD538FAD84DB
ms.topic: how-to
ms.openlocfilehash: cae68b54623564028ea85dd1aa319fad5ceaec48
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493581"
---
# <a name="getting-started-building-games-with-unity-in-visual-studio-for-mac"></a>Erste Schritte beim Erstellen von Spielen mit Unity in Visual Studio für Mac

Unity ist eine Spiele-Engine, mit der Sie Spiele in C# entwickeln können. Diese exemplarische Vorgehensweise zeigt, wie Sie mit der Entwicklung und dem Debuggen von Unity-Spielen mit Visual Studio für Mac und den Visual Studio für Mac-Tools für die Unity-Erweiterung in Verbindung mit der Unity-Umgebung beginnen können.

Visual Studio für Mac-Tools für Unity ist eine kostenlose Erweiterung, die mit Visual Studio für Mac installiert wird. Damit können Unity-Entwickler die Produktivitätsfunktionen von Visual Studio für Mac nutzen, einschließlich hervorragender IntelliSense-Unterstützung, Debugfunktionen und mehr.

## <a name="objectives"></a>Ziele

> [!div class="checklist"]
> * Erfahren Sie mehr über die Unity-Entwicklung mit Visual Studio für Mac.

## <a name="prerequisites"></a>Voraussetzungen

- Visual Studio für Mac ([https://www.visualstudio.com/vs/mac](https://www.visualstudio.com/vs/visual-studio-mac))
- Unity 5.6.1 Personal Edition oder höher ([https://store.unity.com](https://store.unity.com/), erfordert für die Ausführung ein unity.com-Konto)

## <a name="intended-audience"></a>Zielgruppe

Dieses Lab ist für Entwickler gedacht, die mit C# vertraut sind, tiefgreifende Kenntnisse sind jedoch nicht erforderlich.

## <a name="task-1-creating-a-basic-unity-project"></a>Aufgabe 1: Erstellen eines einfachen Unity-Projekts

1. Starten Sie **Unity**. Melden Sie sich an, falls Sie dazu aufgefordert werden.

2. Klicken Sie auf **New** (Neu).

    ![Schaltfläche „New“ (Neu) in Unity](media/unity-image1.png)

3. Legen Sie für **Project name** (Projektname) **UnityLab** fest, und wählen Sie **3D** aus. Klicken Sie auf **Create Project** (Projekt erstellen).

    ![Bildschirm „Create new project“ (Neues Projekt erstellen)](media/unity-image2.png)

4. Sie sehen jetzt die standardmäßige Unity-Benutzeroberfläche. Sie enthält die Szenenhierarchie mit Spielobjekten auf der linken Seite, eine 3D-Ansicht der leeren Szene in der Mitte, einen Projektdateibereich im unteren Bereich und den Inspector und Dienste auf der rechten Seite. Natürlich gibt es noch viel mehr Komponenten, aber das sind erst einmal einige der wichtigsten.

    ![Leere Unity-Benutzeroberfläche](media/unity-image3.png)

5. Für Entwickler, die noch nicht mit Unity vertraut sind: alles, was in Ihrer App ausgeführt wird, steht im Kontext einer **Szene**. Eine Szenendatei ist eine einzelne Datei, die alle Sorten der Metadaten über die Ressourcen enthält, die im Projekt für die aktuelle Szene und die zugehörigen Eigenschaften verwendet werden. Wenn Sie Ihre App für eine Plattform zusammenstellen, wird aus der resultierenden App eine Sammlung aus einer oder mehreren Szenen und jedem plattformabhängigen Code, den Sie hinzufügen. Ein Projekt kann beliebig viele Szenen enthalten.

6. Die neue Szene enthält nur eine Kamera und ein diffuses Licht. Eine Szene erfordert eine **Kamera**, damit alle Elemente sichtbar sind, und einen **Audio Listener**, damit alle entsprechenden Elemente hörbar sind. Diese Komponenten werden an ein **GameObject** angefügt.

7. Wählen Sie das Objekt **Main Camera** (Hauptkamera) im Bereich **Hierarchy** (Hierarchie) aus.

    ![Objekt „Main Camera“ (Hauptkamera) im Bereich „Hierarchy“ (Hierarchie) hervorgehoben](media/unity-image4.png)

8. Wählen Sie den Bereich **Inspector** auf der rechten Seite des Fensters, um seine Eigenschaften anzuzeigen. Zu den Kameraeigenschaften gehören „transform“ (Transformation), „Background“ (Hintergrund), „Projection“ (Projektionsart), „Field of View“ (Sichtfeld) und so weiter. Standardmäßig wurde auch eine Audio Listener-Komponente hinzugefügt, die im Wesentlichen Szenen-Audio von einem an der Kamera angeschlossenen virtuellen Mikrofon rendert.

    ![Bereich „Inspector“](media/unity-image5.png)

9. Wählen Sie das Objekt **Directional Light** (Diffuses Licht) aus. Dadurch wird die Szene beleuchtet, sodass Komponenten wie die Shader wissen, wie Objekte gerendert werden.

    ![Objekt „Directional Light“ (Diffuses Licht) hervorgehoben](media/unity-image6.png)

10. Verwenden Sie den **Inspector**, um zu sehen, dass allgemeine Beleuchtungseigenschaften enthalten sind, wie z.B. Typ, Farbe, Intensität, Schattentyp und so weiter.

    ![Anzeige der Eigenschaften im Bereich „Inspector“](media/unity-image7.png)

11. Es ist wichtig, zu beachten, dass sich Projekte in Unity ein wenig von ihren Pendants in Visual Studio für Mac unterscheiden. Klicken Sie auf der Registerkarte **Project** (Projekt) unten mit der rechten Maustaste auf den Ordner **Assets** (Objekte), und wählen Sie **Reveal in Finder** (Im Finder anzeigen) aus.

    ![Kontextaktion „Reveal in Finder“ (Im Finder anzeigen)](media/unity-image8.png)

12. Die Projekte enthalten die Ordner **Assets** (Objekte), **Library** (Bibliothek), **ProjectSettings** und **Temp**. In der Benutzeroberfläche wird jedoch nur der Ordner **Assets** (Objekte) angezeigt. Der Ordner **Library** (Bibliothek) ist der lokale Zwischenspeicher für importierte Objekte, er enthält alle Metadaten für die Objekte. Im Ordner **ProjectSettings** werden die Einstellungen gespeichert, die Sie konfigurieren. Der Ordner **Temp** wird während des Buildvorgangs für temporäre Dateien aus Mono und Unity verwendet. Es gibt auch eine Projektmappendatei, die Sie in Visual Studio für Mac öffnen können (hier **UnityLab.sln**).

    ![Objekte im Finder](media/unity-image9.png)

13. Schließen Sie das Fenster **Finder**, und kehren Sie zu **Unity** zurück.

14. Die **Assets** Ordner enthält alle Ihre Assets-Grafiken, Code, Audio usw. Er ist jetzt leer, aber jede Datei, die Sie in Ihr Projekt laden, wird hier abgelegt. Dieser ist immer der Ordner auf oberster Ebene im **Unity-Editor**. Dateien müssen immer über die Unity-Benutzeroberfläche (oder Visual Studio für Mac) hinzugefügt und entfernt werden, die direkt über das Dateisystem.

    ![Ordner „Assets“ (Objekte) in Unity](media/unity-image10.png)

15. Das **GameObject** ist von zentraler Bedeutung für die Entwicklung in Unity, da fast alles aus diesem Typ abgeleitet ist, einschließlich Modellen, Beleuchtung, Partikelsystemen und so weiter. Fügen Sie über das Menü **GameObject > 3D Object > Cube** (GameObject > 3D-Objekt > Würfel) ein neues Objekt **Cube** hinzu.

    ![Objekt „Cube“ in der Szene](media/unity-image11.png)

16. Werfen Sie einen kurzen Blick auf die Eigenschaften des neuen **GameObject**. Sehen Sie, dass es einen Namen, ein Tag, eine Ebene und eine Transformation enthält. Diese Eigenschaften hat jedes der **GameObjects**. Darüber hinaus wurden mehrere Komponenten an den **Würfel** angehängt, um die erforderliche Funktionalität wie Netzfilter, Boxcollider und Renderer bereitzustellen.

    ![Eigenschaften des Spieleobjekts](media/unity-image12.png)

17. Benennen Sie das Objekt **Cube**, das standardmäßig den Namen **Cube** hat, in **Enemy** um. Drücken Sie auf die **EINGABETASTE**, um die Änderung zu speichern. Das ist der Würfel „Enemy“ in unserem einfachen Spiel.

    ![Eigenschaft zum Umbenennen des Objekts „Cube“](media/unity-image13.png)

18. Fügen Sie mit dem gleichen Verfahren wie oben ein weiteres Objekt **Cube** zur Szene hinzu, und nennen Sie dieses **Player**.

    ![Umbenennen des zweiten Objekts „Cube“](media/unity-image14.png)

19. Markieren Sie das Player-Objekt **Player** (siehe Dropdownsteuerung **Tag** direkt unter dem Namensfeld). Wir verwenden es im Skript „Enemy“, um das Spielobjekt „Player“ zu suchen.

    ![Markieren des Player-Objekts](media/unity-image15.png)

20. Bewegen Sie das Objekt „Player“ in der Ansicht **Scene** (Szene) mit der Maus entlang der Z-Achse vom Objekt „Enemy“ weg. Sie können sich entlang der Z-Achse bewegen, indem Sie den Würfel mit seinem **roten** Feld auswählen und in Richtung der **blauen** Linie ziehen. Da sich der Würfel im 3D-Raum befindet, aber jeweils nur in 2D gezogen werden kann, ist die Achse, auf der Sie das Objekt ziehen, besonders wichtig.

    ![Szenenansicht mit Würfel](media/unity-image16.png)

21. Bewegen Sie den Würfel nach unten und nach rechts entlang der Achse. Dadurch wird die Eigenschaft **Transform.Position** im **Inspector** aktualisiert. Achten Sie darauf, dass Sie das Objekt an eine ähnliche Position ziehen wie hier gezeigt, um spätere Schritte im Lab zu erleichtern.

    ![Verschieben eines Würfels auf der Achse](media/unity-image17.png)

22. Jetzt können Sie etwas Code hinzufügen, um die Logik des Würfels „Enemy“ so zu steuern, dass er den Würfel „Player“ verfolgt. Klicken Sie mit der rechten Maustaste auf den Ordner **Ressourcen** im Fenster **Projekt** und dann mit der linken auf **Erstellen > C#-Skript**.

    ![Kontextaktion „C# Script “ (C#-Skript)](media/unity-image18.png)

23. Benennen Sie das neue C#-Skript **EnemyAI**.

    ![C#-Skript](media/unity-image19.png)

24. Um Skripte an Spielobjekte anzufügen, ziehen Sie das neu erstellte Skript auf das Objekt **Enemy** im Bereich **Hierarchy** (Hierarchie). Dieses Objekt verwendet jetzt Verhaltensweisen dieses Skripts.

    ![Hervorhebung zeigt das Hinzufügen des Skripts zum Spielobjekt](media/unity-image20.png)

25. Wählen Sie **File > Save Scenes** (Datei > Szene speichern) aus, um die aktuelle Szene zu speichern. Nennen Sie sie **MyScene**.

## <a name="task-2-working-with-visual-studio-for-mac-tools-for-unity"></a>Aufgabe 2: Arbeiten mit Visual Studio für Mac-Tools für Unity

1. Die beste Möglichkeit zum Bearbeiten von C#-Code ist die Verwendung von Visual Studio für Mac. Sie können Unity so konfigurieren, dass Visual Studio für Mac als der Standardhandler verwendet wird. Wählen Sie **Unity > Preferences** (Unity > Einstellungen) aus.

2. Wählen Sie die Registerkarte **External Tools** (Externe Tools) aus. Wählen Sie in der Dropdownliste **External Script Editor** (Externer Skripteditor) die Option **Browse** (Durchsuchen) und anschließend **Applications/Visual Studio.app** aus. Wenn bereits eine Option **Visual Studio** vorhanden ist, wählen Sie diese aus.

    ![Registerkarte „External Tools“ (Externe Tools) in den Einstellungen](media/unity-image21.png)

3. Unity ist jetzt so konfiguriert, dass **Visual Studio für Mac** zur Skriptbearbeitung verwendet wird. Schließen Sie das Dialogfeld **Unity Preferences** (Unity-Einstellungen).

    ![Visual Studio in den Einstellungen ausgewählt](media/unity-image22.png)

4. Doppelklicken Sie auf die Datei **EnemyAI.cs**, um Sie in **Visual Studio für Mac** zu öffnen.

    ![Objekt „Enemy“ in Unity ausgewählt](media/unity-image23.png)

5. Die Visual Studio-Projektmappe ist sehr einfach. Sie enthält den Ordner **Assets** (Objekte) (der gleiche wie in **Finder**) und das zuvor erstellte Skript **EnemyAI.cs**. In komplexeren Projekten wird die Hierarchie wahrscheinlich anders aussehen als das, was Sie in Unity sehen.

    ![Projektmappenfenster in Visual Studio für Mac](media/unity-image24.png)

6. **EnemyAI.cs** wird im Editor geöffnet. Das erste Skript enthält nur die Stubs für die Methoden **Start** und **Update**.

7. Ersetzen Sie den ursprünglichen Code für „Enemy“ durch den folgenden Code.

    ```csharp
    public class EnemyAI : MonoBehaviour
    {
        public float Speed = 50;
        private Transform _playerTransform;
        private Transform _myTransform;

        void Start()
        {
            var player = GameObject.FindGameObjectWithTag("Player");
            if (!player)
            {
                Debug.LogError(
                    "Could not find the main player. Ensure it has the player tag set.");
            }
            else
            {
                _playerTransform = player.transform;
            }
            _myTransform = this.transform;
        }

        void Update()
        {
            var moveAmount = Speed * Time.deltaTime;
            _myTransform.position = Vector3.MoveTowards(_myTransform.position,
                _playerTransform.position, moveAmount);

            if (_myTransform.position == _playerTransform.position)
            {
                _myTransform.position = Vector3.back * 10;
            }
        }
    }
    ```

8. Werfen Sie einen kurzen Blick auf das einfache Verhalten von „Enemy“, das hier definiert ist. In der Methode **Start** erhalten wir einen Verweis auf das Objekt „Player“ (durch dessen Tag) und auf die Eigenschaft **transform**. In der Methode **Update**, die in jedem Frame aufgerufen wird, bewegt sich das Objekt „Enemy“ auf das Objekt „Player“ zu. Die Schlüsselwörter und Namen verwenden eine Farbkodierung, damit Sie die Codebasis in Visual Studio für Mac besser verstehen können.

9. Speichern Sie die Änderungen im Skript „Enemy“ in **Visual Studio für Mac**.

## <a name="task-3-debugging-the-unity-project"></a>Aufgabe 3: Debuggen des Unity-Projekts

1. Legen Sie in der ersten Codezeile der Methode **Start** einen Breakpoint fest. Sie können entweder in den Editorrand an der Zielzeile klicken oder den Cursor auf der Zeile positionieren und **F9** drücken.

    ![Festlegen eines Breakpoints in Visual Studio für Mac](media/unity-image25.png)

2. Klicken Sie auf die **Start Debugging** (Debuggen starten), oder drücken Sie die **F5**. Damit wird das Projekt erstellt und zum Debuggen an Unity angefügt.

    ![Startschaltfläche in Visual Studio für Mac](media/unity-image26.png)

3. Kehren Sie zu **Unity** zurück, und klicken Sie auf **Run** (Ausführen), um das Spiel zu starten.

    ![Schaltfläche „Run“ (Ausführen) in Unity](media/unity-image27.png)

4. Der Breakpoint sollte erreicht werden, und Sie können nun die Debugging-Tools von Visual Studio für Mac verwenden.

    ![Breakpoint in Visual Studio für Mac erreicht](media/unity-image28.png)

5. Suchen Sie im Fenster **Lokale Versionen** den Zeiger **this**, der auf ein **EnemyAI**-Objekt verweist. Erweitern Sie den Verweis und schauen Sie sich an, dass Sie die zugehörigen Member wie **Speed** (Geschwindigkeit) durchsuchen können.

    ![Das Fenster „Lokale Versionen“ in Visual Studio für Mac](media/unity-image29.png)

6. Entfernen Sie den Breakpoint aus der Methode **Start** auf die gleiche Weise, wie sie Ihn hinzugefügt haben, indem Sie entweder auf dessen Rand klicken oder die Zeile auswählen und **F9** drücken.

    ![Entfernen eines Breakpoints in Visual Studio für Mac durch Klicken darauf](media/unity-image30.png)

7. Drücken Sie **F10**, um die erste Codezeile zu überspringen, die das Spielobjekt **Player** mit einem Tag als Parameter findet.

8. Bewegen Sie den Mauszeiger innerhalb des Code-Editor-Fensters über die Variable **player**, um die zugehörigen Member anzuzeigen. Sie können auch die Überlagerung erweitern, um untergeordnete Eigenschaften anzuzeigen.

    ![Debugfenster im Visual Studio für Mac-Editor](media/unity-image31.png)

9. Drücken Sie auf **F5** oder die Schaltfläche **Run** (Ausführen), um die Ausführung fortzusetzen. Kehren Sie zu Unity zurück, um zu sehen, wie sich der Würfel „Enemy“ wiederholt dem Würfel „Player“ nähert. Möglicherweise müssen Sie die Kamera anpassen, wenn Sie das nicht sehen.

    ![Abspielen einer Szene in Unity](media/unity-image32.png)

10. Wechseln Sie zurück zu **Visual Studio für Mac** und legen Sie einen Breakpoint in der ersten Zeile der Methode **Update** fest. Dieser sollte sofort erreicht werden.

    ![Entfernen eines Breakpoints in Visual Studio für Mac](media/unity-image33.png)

11. Angenommen, die Geschwindigkeit ist zu hoch, und wir wollen die Auswirkungen der Änderung testen, ohne die App neu zu starten. Suchen Sie die Variable **Speed** innerhalb des Fensters **Autos** oder **Locals** (Gebietsschemas), ändern Sie sie dann in **10**, und drücken Sie die **EINGABETASTE**.

    ![Anpassen von Variablen im Fenster „Locals“ (Gebietsschema)](media/unity-image34.png)

12. Entfernen Sie den Breakpoint, und drücken Sie **F5**, um die Ausführung fortzusetzen.

13. Kehren Sie zu **Unity** zurück, um die ausgeführte Anwendung anzuzeigen. Der Würfel „Enemy“ bewegt sich nun mit einem Fünftel der ursprünglichen Geschwindigkeit.

    ![Unity-Fenster mit der ausgeführten Anwendung](media/unity-image35.png)

14. Beenden Sie die Unity-App an, indem Sie erneut auf die Schaltfläche **Play** (Wiedergabe) klicken.

    ![Beenden der Unity-App](media/unity-image36.png)

15. Kehren Sie zu **Visual Studio für Mac** zurück. Beenden Sie die Debugsitzung, indem Sie auf die Schaltfläche **Stop** (Beenden) klicken.

    ![Beenden der Debugsitzung in Visual Studio für Mac](media/unity-image37.png)

## <a name="task-4-exploring-unity-features-in-visual-studio-for-mac"></a>Aufgabe 4: Erkunden der Unity-Features in Visual Studio für Mac

1. Visual Studio für Mac bietet im Code-Editor schnellen Zugriff auf die Unity-Dokumentation. Positionieren Sie den Cursor an einer beliebigen Stelle auf dem Symbol **Vector3** innerhalb der Methode **Update**, und drücken Sie auf **⌘ Command + '** .

    ![Auswählen der Methode im Visual Studio für Mac-Editor](media/unity-image38.png)

2. Die Dokumentation zu **Vector3** wird in einem neuen Browserfenster geöffnet. Schließen Sie das Browserfenster, wenn Sie mit dem Ergebnis zufrieden sind.

    ![Browserfenster mit geöffneter Dokumentation](media/unity-image39.png)

3. Visual Studio für Mac bietet auch einige Hilfsprogramme zum schnellen Erstellen von Unity-Verhaltensklassen. Klicken Sie im **Solution Explorer** (Projektmappen-Explorer) mit der rechten Maustaste auf **Assets** (Objekte), und wählen Sie **Add > New MonoBehaviour** (Hinzufügen > Neues MonoBehaviour) aus.

    ![Kontextaktion „New MonoBehaviour“ (Neues MonoBehaviour)](media/unity-image40.png)

4. Die neu erstellte Klasse bietet Stubs für die Methoden **Start** und **Update**. Beginnen Sie nach der schließenden Klammer der Methode **Update** mit der Eingabe von **onmouseup**. Beachten Sie beim Tippen, dass die IntelliSense-Funktion von Visual Studio die Methode, die Sie implementieren möchten, schnell anzeigt. Wählen Sie sie aus der AutoVervollständigen-Liste aus. Damit wird ein Methodenstub für Sie ausgefüllt, einschließlich aller Parameter.

    ![IntelliSense in Visual Studio für Mac](media/unity-image41.png)

5. Geben Sie in der Methode **OnMouseUp** **base.** ein, um alle Basismethoden anzuzeigen, die aufgerufen werden können. Sie können sich auch mit der Paging-Funktion in der rechten oberen Ecke des IntelliSense-Flyouts die verschiedenen Überladungen der einzelnen Funktionen ansehen.

    ![Untersuchen der Überladungen in Visual Studio für Mac](media/unity-image42.png)

6. Mit Visual Studio für Mac können Sie auch problemlos neue Shader definieren. Klicken Sie im **Solution Explorer** (Projektmappen-Explorer) mit der rechten Maustaste auf **Assets** (Objekte), und wählen Sie **Add > New Shader** (Hinzufügen > Neuer Shader) aus.

    ![Aktion „Neuer Shader“ in Visual Studio für Mac](media/unity-image43.png)

7. Das Shader-Dateiformat wird hinsichtlich Vollfarbe und Schriftarten optimiert, um das Lesen und Verstehen zu erleichtern.

    ![Syntaxhervorhebung](media/unity-image44.png)

8. Kehren Sie zu **Unity** zurück. Sie werden sehen, dass Änderungen auf beiden Seiten automatisch miteinander synchronisiert werden, da Visual Studio für Mac mit dem gleichen Projektsystem arbeitet. Jetzt können Sie ganz einfach immer das beste Tool für die Aufgabe verwenden.

    ![Objektbereich in Unity](media/unity-image45.png)

## <a name="summary"></a>Zusammenfassung

In diesem Tutorial haben Sie mehr über die ersten Schritte beim Erstellen eines Spiels mithilfe von Unity und Visual Studio für Mac erfahren. Weitere Informationen zu Unity finden Sie unter [https://unity3d.com/learn](https://unity3d.com/learn).
