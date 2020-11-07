---
title: Verwenden von Visual Studio Tools für Unity | Microsoft-Dokumentation
description: Hier erfahren Sie, wie Sie die Integrations- und Produktivitätsfeatures der Visual Studio-Tools für Unity verwenden. Verwenden Sie auch den Visual Studio-Debugger für die Unity-Entwicklung.
ms.custom: ''
ms.date: 07/03/2018
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: how-to
ms.assetid: e67ec9a2-a449-413e-8930-9a471bd43a06
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
zone_pivot_groups: platform
ms.openlocfilehash: 9a89f83ecaa4545eb6151c7a92e76a08708c3855
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2020
ms.locfileid: "94341204"
---
# <a name="use-visual-studio-tools-for-unity"></a>Verwenden von Visual Studio-Tools für Unity

In diesem Abschnitt erfahren Sie, wie Sie die Integrations- und Produktivitätsfunktionen von Visual Studio-Tools für Unity und den Visual Studio-Debugger für die Unity-Entwicklung einsetzen.

## <a name="open-unity-scripts-in-visual-studio"></a>Öffnen von Unity-Skripts in Visual Studio

Sobald Visual Studio [als externer Editor für Unity festgelegt](getting-started-with-visual-studio-tools-for-unity.md#configure-unity-to-use-visual-studio)ist, wird durch Doppelklicken auf ein Skript aus dem Unity-Editor automatisch auf Visual Studio gestartet oder gewechselt, und das ausgewählte Skript wird geöffnet.

Alternativ können Sie Visual Studio öffnen, ohne dass im Quellen-Editor ein Skript geöffnet ist, indem Sie das Menü **Objekte > öffnen des c#-Projekts** in Unity auswählen.

:::zone pivot="windows"
![Öffnen eines c#-Projekts in Visual Studio](../media/vs/vstu-open-csharp-project.png)
:::zone-end
:::zone pivot="macos"
![Öffnen Sie das c#-Projekt in Visual Studio für Mac](../media/vsm/vstu-open-csharp-project.png)
:::zone-end

## <a name="unity-documentation-access"></a>Zugriff auf die Unity-Dokumentation

Sie können in Visual Studio schnell auf die Dokumentation zur Erstellung von Unity-Skripts zugreifen. Wenn Visual Studio-Tools für Unity die API-Dokumentation lokal nicht finden kann, wird versucht, sie online zu finden.

:::zone pivot="windows"
- Platzieren Sie in Visual Studio den Cursor über der Unity-API, zu der Sie Informationen wünschen, oder markieren Sie sie, und drücken Sie dann **STRG**+**ALT**+**M** > **STRG**+**H**.
- Sie können auch das **Hilfe > Unity-API-Verweis** Menü anstelle der KeyBinding verwenden.
![Das Unity-API-Referenz Menü in Visual Studio](../media/vs/help-unity-documentation.png)
:::zone-end
:::zone pivot="macos"
- Markieren Sie in Visual Studio für Mac den Cursor über der Unity-API, über die Sie weitere Informationen erhalten möchten, und drücken Sie dann **cmd** + **"** .
- Sie können auch das **Hilfe > Unity-API-Verweis** Menü anstelle der KeyBinding verwenden.
![Das Unity-API-Verweis Menü in Visual Studio für Mac](../media/vsm/help-unity-documentation.png)
:::zone-end

## <a name="intellisense-for-unity-api-messages"></a>API-Nachrichten von IntelliSense für Unity

Die Codevervollständigung von IntelliSense erleichtert das Implementieren von Unity-API-Nachrichten in MonoBehaviour-Skripts und das Erlernen des Umgangs mit der Unity-API. So verwenden Sie IntelliSense für Unity-Nachrichten:

1. Platzieren Sie den Cursor in einer neuen Zeile innerhalb des Texts einer Klasse, die von `MonoBehaviour` abgeleitet wird.

2. Geben Sie den Namens einer Unity-Nachricht ein, z.B. `OnTriggerEnter`.

3. Sobald Sie die Buchstaben **ontri** eingegeben haben, wird eine Liste von IntelliSense-Vorschlägen angezeigt.

:::zone pivot="windows"

![Verwenden von IntelliSense in Visual Studio](../media/vs/intellisense-example.png)  

:::zone-end

4. Die Auswahl in der Liste kann auf drei verschiedene Arten geändert werden:

    - Mit den Pfeiltasten **Nach oben** und **Nach unten**

    - Indem Sie mit der Maus auf das gewünschte Element klicken

    - Indem Sie den Namen des gewünschten Elements weiter eingeben

5. IntelliSense kann die ausgewählte Unity-Nachricht einfügen, einschließlich aller erforderlichen Parameter:

    - Durch Drücken der **TAB-TASTE**

    - Durch Drücken der **EINGABETASTE**.

    - Durch Doppelklicken auf das ausgewählte Element

:::zone pivot="windows"

![Einfügen von Unity-Nachrichten aus IntelliSense in Visual Studio](../media/vs/vstu-intellisense2.png)

:::zone-end

## <a name="unity-monobehavior-scripting-wizard"></a>Unity MonoBehavior-Assistent für das Erstellen von Skripts

Sie können den MonoBehavior-Assistenten verwenden, um eine Liste aller Unity-API-Methoden anzuzeigen und schnell eine leere Definition zu implementieren. Diese Funktion ist hilfreich – insbesondere, wenn die Option **Methodenkommentare generieren** aktiviert ist – wenn Sie noch lernen, was in der Unity-API verfügbar ist.

So erstellen Sie mit dem MonoBehavior-Assistenten leere MonoBehavior-Methodendefinitionen:

1. Positionieren Sie den Cursor in Visual Studio an der Stelle, an der die Methoden eingefügt werden sollen, und drücken Sie **STRG**+**UMSCHALT**+**M** , um den MonoBehavior-Assistenten zu starten. Drücken Sie in Visual Studio für Mac **cmd** + **UMSCHALT** + **M**.

2. Aktivieren Sie im Fenster **Create script methods** (Skriptmethoden erstellen) die Kontrollkästchen neben den Namen der einzelnen Methoden, die Sie hinzufügen möchten.

3. Wählen Sie in der Dropdownliste **Framework version** Ihre gewünschte Version aus.

4. Standardmäßig werden die Methoden an der Position des Cursors eingefügt. Alternativ können Sie sie nach jeder Methode, die bereits in Ihrer Klasse implementiert ist, durch Ändern des Werts der Dropdownliste **Insertion point** (Einfügemarke) an der gewünschten Stelle einfügen.

5. Wenn Sie möchten, dass der Assistent Kommentare für die Methoden generiert, die Sie ausgewählt haben, markieren Sie das Kontrollkästchen **Methodenkommentare generieren**. Diese Kommentare sollen Ihnen helfen zu verstehen, wann die Methode aufgerufen wird und was ihre allgemeinen Aufgaben sind.

6. Klicken Sie auf die Schaltfläche **OK** , um den Assistenten zu beenden und die Methoden in Ihren Code einzufügen.

:::zone pivot="windows"

![Der monobehavior-Assistent-Dialogfeld in Visual Studio.](../media/vs/vstu-monobehavior-wizard.png)
:::zone-end
:::zone pivot="macos"

![Das Dialogfeld monobehavior-Assistent in Visual Studio für Mac.](../media/vsm/vstu-monobehavior-wizard.png)
:::zone-end   

## <a name="unity-project-explorer"></a>Unity-Projekt-Explorer
Der Unity-Projekt-Explorer zeigt alle Ihre Unity-Projektdateien und -Verzeichnisse in der gleichen Weise wie der Unity-Editor an. Dies unterscheidet sich vom Navigieren durch Ihre Unity-Skripts mit dem normalen Visual Studio-Projektmappen-Explorer, der sie in Projekten und einer von Visual Studio generierten Projektmappe organisiert.

:::zone pivot="windows"
- Wählen Sie in Visual Studio im Hauptmenü **Ansicht > Unity-Projektexplorer** aus. Tastenkombination: **alt** + **UMSCHALT** Taste + **E** zeigt 
 ![ das Fenster Unity-Projekt-Explorer an.](../media/vs/unity-project-explorer.png)
:::zone-end
:::zone pivot="macos"
- In Visual Studio für Mac verhält sich der Lösungspad automatisch wie diese, wenn ein Unity-Projekt geöffnet wird.
:::zone-end
## <a name="unity-debugging"></a>Debuggen von Unity

Mit Visual Studio-Tools für Unity können Sie Editor- und Spielskripts für Ihr Unity-Projekt mit dem leistungsfähigen Debugger von Visual Studio debuggen.

### <a name="debug-in-the-unity-editor"></a>Debuggen im Unity-Editor

#### <a name="start-debugging"></a>Debugging starten
:::zone pivot="windows"

1. Stellen Sie eine Verbindung von Visual Studio mit Unity her, indem Sie auf die **Wiedergabeschaltfläche** mit der Bezeichnung **An Unity anfügen** klicken, oder verwenden Sie die Taste **F5**.
![In Visual Studio auf „Wiedergeben“ klicken](../media/vs/vstu-play-button.png)

:::zone-end
:::zone pivot="macos"

1. Verbinden Sie Visual Studio mit Unity, indem Sie auf die Schaltfläche **Play** (Wiedergeben) klicken, oder drücken Sie **⌘ (cmd)+EINGABETASTE** oder **F5** ein.
![Klicken Sie auf wiedergeben in Visual Studio für Mac](../media/vsm/using-vsmac-tools-unity-image5.png)

:::zone-end

2. Wechseln Sie zu Unity, und klicken Sie auf **Play** , um das Spiel im Editor auszuführen.
:::zone pivot="windows"
![Klicken Sie in Unity unter Windows auf wiedergeben.](../media/vs/vstu-unity-play-button.png)
:::zone-end
:::zone pivot="macos"
![Klicken Sie in Unity unter macOS auf wiedergeben.](../media/vsm/using-vsmac-tools-unity-image6.png)
:::zone-end

3. Wenn das Spiel in Unity-Editor ausgeführt wird und gleichzeitig eine Verbindung mit Visual Studio besteht, pausieren alle vorgefundenen Breakpoints die Ausführung des Spiels und bringen die Codezeile hervor, in der das Spiel den Breakpoint in Visual Studio erreicht hat.

#### <a name="stop-debugging"></a>Beenden des Debuggens

:::zone pivot="windows"

Klicken Sie in Visual Studio auf die Schaltfläche **Beenden** , oder verwenden Sie die Tastenkombination **UMSCHALT + F5**.
![In Visual Studio auf „Beenden“ klicken](../media/vs/vstu-stop-debugger.png)

:::zone-end
:::zone pivot="macos"

Klicken Sie in Visual Studio für Mac auf **Stop** (Beenden), oder drücken Sie **UMSCHALTTASTE+CMD+EINGABETASTE**.
![Klicken Sie in Visual Studio für Mac](../media/vsm/using-vsmac-tools-unity-image7.png)

:::zone-end

Weitere Informationen zum Debuggen in Visual Studio finden Sie unter [Ein erster Blick auf die Visual Studio-Debugger](/debugger/debugger-feature-tour.md).

#### <a name="attach-to-unity-and-play"></a>An Unity anfügen und wiedergeben

Der Einfachheit halber können Sie die Schaltfläche **An Unity anfügen** in den Modus **An Unity anfügen und wiedergeben** ändern.

:::zone pivot="windows"

1. Klicken Sie auf den kleinen **Pfeil nach unten** neben der Schaltfläche **An Unity anfügen**.
2. Wählen Sie **An Unity anfügen und wiedergeben** aus dem Dropdownmenü aus.
   ![Anfügen und Abspielen in Visual Studio](../media/vs/vstu-attach-and-play.png)

Die Wiedergabeschaltfläche erhält die Bezeichnung **An Unity anfügen und wiedergeben**. Wenn Sie auf diese Schaltfläche klicken oder die Taste **F5** verwenden, erfolgt zusätzlich zum Anfügen des Visual Studio-Debuggers automatisch der Wechsel zum Unity-Editor und wird das Spiel im Editor ausgeführt.

:::zone-end
:::zone pivot="macos"
Das Debuggen zu starten und den Unity-Editor wiederzugeben kann als einzelner Schritt direkt in Visual Studio für Mac ausgeführt werden, indem Sie die Konfiguration **An Unity anfügen und wiedergeben** auswählen.

![Wählen Sie an Unity anfügen und wiedergeben in Visual Studio für Mac](../media/vsm/using-vsmac-tools-unity-image8.png)
:::zone-end

> [!NOTE]
> Wenn Sie das Debuggen mit der Funktion " **an Unity anfügen" und** "wiedergeben" gestartet haben, wird auch die Schaltfläche " **Abbrechen** " beendet

### <a name="debug-unity-player-builds"></a>Debuggen von Unity-Playerbuilds

Sie können Entwicklungs Builds von Unity-Playern mit Visual Studio debuggen.

#### <a name="enable-script-debugging-in-a-unity-player"></a>Aktivieren des Skriptdebuggens in einem Unity-Player

1. Öffnen Sie in Unity die Buildeinstellungen durch Auswahl von **File > Build Settings (Datei > Buildeinstellungen)** .
2. Aktivieren Sie im Fenster „Build Settings“ (Buildeinstellungen) Ihres Unity-Projekts die Kontrollkästchen **Development Build** (Entwicklungsbuild) und **Script Debugging** (Skriptdebuggen).

   ![Konfigurieren der Unity-Buildeinstellungen für das Debuggen](../media/vs/vstu-debugging-build-settings.png "vstu_debugging_build_settings")

#### <a name="select-a-unity-instance-to-attach-the-debugger-to"></a>Auswählen einer Unity-Instanz zum Anfügen des Debuggers

:::zone pivot="windows"

- Wählen Sie in Visual Studio im Hauptmenü **Debuggen > Unity-Debugger anfügen** aus.

   ![Unity-Debugger anhängen](../media/vs/vstu-debugging-attach-unity-debugger.png "vstu_debugging_attach_unity_debugger")

   Das Dialogfeld **Unity-Instanz auswählen** zeigt Informationen zu jeder Unity-Instanz, mit der Sie eine Verbindung herstellen können.

   ![Unity-Instanz auswählen, zu der eine Verbindung hergestellt werden soll](../media/vs/vstu-attach-debugger.png "vstu_connection_to_unity")

   **Projekt**

   Der Name des Unity-Projekts, das in dieser Instanz von Unity ausgeführt wird.

   **Computer** Der Name des Computers oder Geräts, auf dem diese Unity-Instanz ausgeführt wird.

   **Typ** - **Editor** , wenn diese Unity-Instanz als Teil des Unity-Editors ausgeführt wird; **Player** , wenn diese Unity-Instanz ein eigenständiger Player ist.

   **Port** Die Portnummer für den UDP-Socket, über den diese Instanz von Unity kommuniziert.

> [!IMPORTANT]
> Da Visual Studio-Tools für Unity und die Unity-Instanz über einen UDP-Netzwerk Socket kommunizieren, benötigt Ihre Firewall möglicherweise eine Regel, um Sie zuzulassen. Bei Bedarf wird möglicherweise eine Eingabeaufforderung angezeigt. Sie müssen die Verbindung autorisieren, damit vstu und Unity kommunizieren können.

:::zone-end
:::zone pivot="macos"

- Wählen Sie in Visual Studio für Mac im oberen Menü die Option **Ausführen > an den Prozess anhängen** aus. 
- Wählen Sie im Dialogfeld **an den Prozess anhängen** im Dropdown Menü Debugger unten im Dropdown Menü Debugger die Option **Unity-Debugger** aus.
- Wählen Sie eine Unity-Instanz aus der Liste aus, und klicken Sie auf die Schaltfläche **Anhängen**

:::zone-end

### <a name="debug-a-dll-in-your-unity-project"></a>Debuggen einer DLL im Unity-Projekt

Viele Unity-Entwickler schreiben Codekomponenten als externe DLLs, damit die Funktionalität, die sie entwickeln, einfach mit anderen Projekten gemeinsam genutzt werden kann. Durch Visual Studio-Tools für Unity wird das reibungslose Debuggen von Code in diese DLLs mit anderem Code in Ihrem Unity-Projekt erleichtert.

> [!NOTE]
> Derzeit unterstützt Visual Studio-Tools für Unity nur verwaltete DLLs. Das Debuggen von DLLs mit systemeigenem Code, z. B. mit C++-Code, wird nicht unterstützt.

Beachten Sie, dass bei dem hier beschriebenen Szenario davon ausgegangen wird, dass Sie den Quellcode haben, d. h. dass Sie eigenen Code aus erster Hand entwickeln oder wiederverwenden oder über Quellcode für eine Drittanbieterbibliothek verfügen und dessen Bereitstellung in Ihrem Unity-Projekt als DLL planen. Dieses Szenario beschreibt nicht das Debuggen einer DLL, für die Sie nicht über den Quellcode verfügen.

#### <a name="to-debug-a-managed-dll-project-used-in-your-unity-project"></a>So debuggen Sie ein in Ihrem Unity-Projekt verwendetes verwaltetes DLL-Projekt

1. Fügen Sie Ihr vorhandenes DLL-Projekt der Visual Studio-Projektmappe hinzu, die von Visual Studio-Tools für Unity generiert wurde. Möglicherweise starten Sie auch, was weniger üblich ist, mit einem neuen verwalteten DLL-Projekt als Container für die Codekomponenten Ihres Unity-Projekts. Ist dies der Fall, können Sie stattdessen der Visual Studio-Projektmappe ein neues verwaltetes DLL-Projekt hinzufügen.

   ![Vorhandenes DLL-Projekt zur Projektmappe hinzufügen](../media/vs/vstu-debugging-dll-add-existing.png "vstu_debugging_dll_add_existing")

   In beiden Fällen verwaltet Visual Studio-Tools für Unity den Projektverweis, selbst wenn die Projekt- und Projektmappendateien neu generiert werden müssen. Daher müssen Sie diese Schritte nur einmal ausführen.

2. Verweisen Sie im DLL-Projekt auf das richtige Unity-Frameworkprofil. Legen Sie in Visual Studio in den Eigenschaften des DLL-Projekts die Eigenschaft **Zielframework** auf das von Ihnen verwendete Unity-Framework fest. Dies ist die Unity-Basisklassenbibliothek, die der gewünschten API-Kompatibilität Ihres Projekts entspricht, wie z. B. die Unity-Klassenbibliothek "full", "micro" oder "web". Dies verhindert, dass Ihre DLL Frameworkmethoden aufruft, die in anderen Frameworks oder auf anderen Kompatibilitätsstufen, aber nicht in der Unity-Frameworkversion vorhanden sind, die Sie verwenden.

> [!NOTE]
> Folgendes ist nur erforderlich, wenn Sie eine ältere Unity-Runtime verwenden. Wenn Sie die neue Unity-Runtime verwenden, müssen Sie diese speziellen 3.5-Profile nicht mehr verwenden. Verwenden Sie ein .NET 4.x-Profil, die mit Ihrer Unity-Version kompatibel ist.

   ![Unity-Framework als Zielframework der DLL festlegen](../media/vs/vstu-debugging-dll-target-framework.png "vstu_debugging_dll_target_framework")

3. Kopieren Sie die DLL in den Ordner "Assets" Ihres Unity-Projekts. In Unity sind "Assets" Dateien, die in Paketen zusammen mit Ihrer Unity-App so bereitgestellt werden, dass sie zur Laufzeit geladen werden können. Da DLLs zur Laufzeit verknüpft werden, müssen die DLLs als Assets bereitgestellt werden. Um als Asset bereitgestellt zu werden, verlangt der Unity-Editor, dass die DLLs dem Ordner "Assets" in Ihrem Unity-Projekt hinzugefügt werden. Dazu stehen zwei Möglichkeiten zur Verfügung:

   - Ändern Sie die Buildeinstellungen Ihres DLL-Projekts so, dass eine im Anschluss an den Build erfolgende Aufgabe hinzugefügt wird, die die DLL- und PDB-Ausgabedateien aus ihrem Ausgabeordner in den Ordner **Assets** Ihres Unity-Projekts kopiert.

   - Ändern Sie die Buildeinstellungen Ihres DLL-Projekts so, dass der Ausgabeordner auf den Ordner **Assets** Ihres Unity-Projekts festgelegt wird. Sowohl DLL- als auch PDB-Dateien werden im Ordner **Assets** abgelegt.

   Die PDB-Dateien sind für das Debuggen erforderlich, da sie Debugsymbole der DLL enthalten und den DLL-Code seiner Quellcodeform zuordnen. Wenn Sie auf die ältere Runtime Visual abzielen, verwendet Visual Studio-Tools für Unity Informationen aus der DLL- und PDB-Datei, um eine DLL.MDB-Datei zu erstellen. Dies ist das Debugsymbolformat, das von der älteren Unity-Skript-Engine verwendet wird. Wenn Sie auf die neue Runtime zielen und Portable-PDB verwenden, werden die Visual Studio-Tools für Unity nicht versuchen, eine Symbolkonvertierung durchzuführen, da die neue Unity-Runtime Portable-PDBs nativ verarbeiten kann.

   Weitere Informationen zur PDB-Generierung finden [hier](/debugger/how-to-set-debug-and-release-configurations.md). Wenn Sie auf die neue Runtime abzielen, stellen Sie bitte sicher, dass „Debuginformationen“ auf „Portable“ gesetzt ist, um Portable-PDB korrekt zu generieren. Wenn Sie auf die ältere Runtime abzielen, müssen Sie „Full“ verwenden.

4. Debuggen Sie Ihren Code. Sie können jetzt Ihren DLL-Quellcode zusammen mit dem Quellcode Ihres Unity-Projekts debuggen und alle vertrauten Debuggingfunktionen nutzen, d. h. Haltepunkte setzen und Code schrittweise durchlaufen.

## <a name="keyboard-shortcuts"></a>Tastenkombinationen

Über Tastenkombinationen können Sie schnell auf die Unity-Tools für Visual Studio-Funktionalität zugreifen. Hier eine Übersicht über die verfügbaren Tastenkombinationen.

:::zone pivot="windows"

|Befehl|Verknüpfung|Name des Kontextmenübefehls|
|-------------|--------------|---------------------------|
|Den MonoBehavior-Assistenten öffnen|**STRG**+**UMSCHALT**+**M**|**EditorContextMenus.CodeWindow.ImplementMonoBehaviours**|
|Den Unity-Projekt-Explorer öffnen|**ALT**+**UMSCHALT**+**E**|**View.UnityProjectExplorer**|
|Auf Unity-Dokumentation zugreifen|**STRG**+**ALT**+**M > STRG**+**H**|**Help.UnityAPIReference**|
|An Unity-Debugger (Player oder Editor) anfügen|**_Kein Standard_**|**Debug.AttachUnityDebugger**|

Sie können die Tastenkombinationen ändern, wenn Ihnen die Standardeinstellung nicht gefällt. Weitere Informationen finden Sie unter [Identifizieren und Anpassen von Tastenkombinationen in Visual Studio](/docs/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

:::zone-end
:::zone pivot="macos"

|Befehl|Verknüpfung|Name des Kontextmenübefehls|
|-------------|--------------|---------------------------|
|Den MonoBehavior-Assistenten öffnen|**Cmd** + **UMSCHALT** + **M**|**EditorContextMenus.CodeWindow.ImplementMonoBehaviours**|
|Auf Unity-Dokumentation zugreifen|**Cmd + '**|**Help.UnityAPIReference**|

Sie können die Tastenkombinationen ändern, wenn Ihnen die Standardeinstellung nicht gefällt. Weitere Informationen zum Ändern der IDE finden Sie unter [Anpassen der IDE](/mac/customizing-the-ide#key-bingings).

:::zone-end
