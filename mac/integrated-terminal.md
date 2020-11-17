---
title: Visual Studio für Mac – Integriertes Terminal
description: Arbeiten mit dem integrierten Terminal in Visual Studio für Mac
author: jmatthiesen
ms.author: jomatthi
ms.date: 05/14/2020
ms.assetid: EFD53CE9-8174-4FE4-8863-2984D22FD921
ms.openlocfilehash: f91c2b1c3f06f8f1fbe54e32fde70b9fe88c5f5d
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/11/2020
ms.locfileid: "94492871"
---
# <a name="integrated-terminal"></a>Integriertes Terminal
In Visual Studio für Mac können Sie ein integriertes Terminal öffnen und am Stamm Ihrer Projektmappe beginnen. Das Terminal kann in verschiedenen Situationen nützlich sein: Ausführen von Front-End-Aufgaben (Beispiel.: npm, ng oder vue), Verwalten von Containern, Ausführen erweiterter Git-Befehle, Ausführen von Entity Framework-Befehlen, Anzeigen der Dotnet-CLI-Ausgabe, Hinzufügen von NuGet-Paketen und vieles mehr. 

So öffnen Sie das Terminal:
- Verwenden Sie die Tastenkombination **STRG+'** , um das Terminalfenster anzuzeigen oder auszublenden.
- Verwenden Sie das Menü **Ansicht** \> **Terminal**.
- Verwenden Sie den Befehl **terminal** in der Suchleiste.

![*Das integrierte Terminal von Visual Studio für Mac unmittelbar nach dem Start.*](media/integrated-terminal-intro.png)

Wenn das Terminal gestartet wird, werden standardmäßig folgende Aktionen durchführt:
- Festlegen des Arbeitsverzeichnisses auf den Pfad der aktuellen Projektmappe.
- Laden der Standardsystemshell.

## <a name="search"></a>Suchen
Sie können den Inhalt des Terminalfensters durchsuchen, indem Sie das Menü **Suche > Suchen...** verwenden.

![*Suchbenutzeroberfläche im integrierten Terminal von Visual Studio für Mac*](media/integrated-terminal-search.png)

## <a name="terminal-keyboard-shortcuts"></a>Tastenkombinationen des Terminals
|Befehle|Tastenkombinationen|
|-|-|
|Anzeigen/Ausblenden des Terminalfensters|**STRG+`**|
|Erstellen einer neuen Terminalinstanz|**STRG+'**|
|Bildlauf nach oben für Seite|**BildAuf**|
|Bildlauf nach unten für Seite|**BildAb**|
|Durchlaufen zuvor verwendeter Befehle|**↑**, **↓**|
|Vergrößern des Schriftgrads|**⌘+**|
|Verkleinern des Schriftgrads|**⌘-**|

## <a name="multiple-instances"></a>Mehrfache Instanzen
Mehrere Instanzen des Terminals können jederzeit ausgeführt werden. Sie können eine neue-Instanz erstellen, indem Sie die Tastenkombination **STRG+'** verwenden. Sie können zwischen Instanzen wechseln, indem Sie auf die Registerkarte für jede Instanz klicken oder die Tastenkombination **STRG+TAB** verwenden, um das Dialogfeld „Fensterauswahl“ zu öffnen.

![*Mehrere Terminalinstanzen in Visual Studio für Mac*](media/integrated-terminal-multiple-instances.png) 

## <a name="customizing-the-terminal-window"></a>Anpassen des Terminalfensters
### <a name="configuring-the-terminal-font"></a>Konfigurieren der Schriftart des Terminals
Sie können die Schriftart und die den Schriftgrad im Bereich „Einstellungen > Umgebung > Schriftarten“ ändern, die für Terminalinhalte verwendet werden. Standardmäßig stimmt die Schriftart mit der des Inhalts des Ausgabefensters überein. Es wird Menlo Regular, Schriftgrad 11, verwendet. Sie können eine beliebige Schriftart unabhängig von der Schriftart des Editors festlegen.

![*Anpassen der Schriftarteinstellungen für das integrierte Terminal*](media/integrated-terminal-change-font.png)

### <a name="reusing-system-terminal-customizations"></a>Wiederverwenden von Systemterminalanpassungen
Das integrierte Terminal verwendet dieselben Standardwerte und dieselbe Konfiguration wie das macOS-Systemterminal. Dies bedeutet, dass Ihre Terminalanpassungen (zsh, oh-my-zsh usw.) auch im integrierten Terminal funktionieren.
