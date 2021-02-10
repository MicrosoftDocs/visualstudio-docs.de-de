---
title: 'Workflow-Designer: Tastenkombinationen'
description: Erlernen Sie die verschiedenen Befehle, die Sie auf der Tastatur eingeben können, um die Workflow-Designer in Visual Studio zu navigieren.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- WFDKeyboardShortcuts.UI
ms.assetid: 9be75438-a4a3-4781-94e5-45b7ec082358
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1d276711e07dfe08b0efda0142089b7807a5509c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931226"
---
# <a name="keyboard-shortcuts-in-the-workflow-designer"></a>Tastenkombinationen im Workflow-Designer

Auf die gesamte Kernfunktionalität des Workflow-Designer kann über die Tastatur zugegriffen werden.

## <a name="navigating-the-workflow-designer-using-the-keyboard"></a>Bedienen des Workflow-Designers mithilfe der Tastatur

In Visual Studio gelten die globalen Verknüpfungen und debugkombinationen für das Workflow-Designer. Außerdem wurde eine Reihe Workflow-Designer spezifischer Tastenkombinationen erstellt. In Visual Studio können alle Tastenkombinationen neu zugeordnet werden. In einer neu gehosteten Anwendung sind diese Tastenkombinationen jedoch hartcodiert.

### <a name="workflow-designer-keyboard-shortcuts"></a>Tastenkombinationen des Workflow-Designers

In der folgenden Tabelle werden die Standard Tastenkombinationen zusammengefasst, die Workflow-Designer Befehlen zugewiesen sind.

|Verknüpfung|Zweck|
|-|-------------|
|STRG+E, A|Argument-Designer anzeigen oder ausblenden.|
|STRG+E, C|Die ausgewählte Aktivität direkt reduzieren.|
|STRG+E, E|Die ausgewählte Aktivität direkt erweitern.|
|STRG+E, F|Die ausgewählten Aktivitäten in einem Flussdiagramm verbinden.|
|CTRL+E+I|Imports-Designer anzeigen oder ausblenden.|
|STRG+E, M|Der Tastaturfokus wechselt zum nächsten Element in der Aktivierreihenfolge.|
|STRG+E, N|Eine neue Variable im Bereich der ausgewählten Aktivität (oder der nächsten Aktivität) erstellen.|
|STRG+E, O|Die Übersichtskarte anzeigen oder ausblenden.|
|STRG+E, P|Zum übergeordneten Element der ausgewählten Aktivität wechseln. In der Brotkrümelnavigation eine Ebene nach oben gehen und die Stammaktivität auf der Designeroberfläche ändern.|
|STRG+E, S|Das Element der aktuellen Auswahl mit dem Tastaturfokus hinzufügen.|
|STRG+E, V|Variablen-Designer anzeigen oder ausblenden.|
|STRG+E, X|Alle Aktivitäten im Workflow erweitern.|
|STRG+ALT+F6|Den Tastaturfokus im aktuellen Benutzeroberflächenbereich auf den nächsten Bereich der Folge verschieben. Die Reihenfolge ist die Folgende:<br /><br /> 1. Breadcrumb-Navigationsleiste<br />2. Designer Oberfläche<br />3. Argumente/Variablen/Import-Designer, wenn Sie geöffnet sind<br />4. Shell|

### <a name="flowchart"></a>Flussdiagramm

In der folgenden Liste sind die Gesten aufgeführt, mit denen ein Flussdiagramm mithilfe der Tastatur erstellt wurde. Wie im restlichen Workflow-Designer werden Aktivitäten mithilfe der globalen Toolbox Verknüpfungen, die mit Visual Studio bereitgestellt werden, der Designer Oberfläche hinzugefügt.

- Um eine Aktivität zu verschieben, markieren Sie die Aktivität, und ordnen Sie sie mithilfe der PFEILTASTEN neu an.

- Um die Größe eines Flussdiagramms zu ändern, schieben Sie eine Aktivität mit den PFEILTASTEN über den aktuellen Rahmen des Flussdiagramms hinaus. Die Größe des Flussdiagramms wird automatisch geändert.

- Um eine Aktivität als Startknoten festzulegen, verwenden Sie den Befehl **als startNode festlegen** im Kontextmenü.

- So verbinden Sie Aktivitäten:

    1. Wählen Sie die Quellaktivität durch Drücken der TAB-TASTE aus.

    2. Drücken Sie STRG+E, M so oft wie erforderlich, um den Tastaturfokus auf die Zielaktivität zu verschieben.

    3. Drücken Sie STRG+E, S, um die Zielaktivität der Auswahl hinzuzufügen.

    4. Drücken Sie STRG+E, F, um den Connector von der Quelle zum Ziel hinzuzufügen.

Hinweise zum Verbinden von Aktivitäten mithilfe der Tastatur:

- Sie können gleichzeitig mehrere Verbindungen herstellen, indem Sie der Auswahl mehrere Aktivitäten hinzufügen, bevor Sie STRG+E, F drücken. Die Verbindungen werden in der Reihenfolge hergestellt, in der die Aktivitäten der Auswahl hinzugefügt wurden.

- Selbst wenn ein Aktivitätenpaar nicht verbunden werden kann, z. B. wenn die Quellaktivität bereits über eine ausgehende Verbindung verfügt, werden die anderen Verbindungen zwischen Aktivitäten in der Auswahl noch hergestellt, sofern dies möglich ist.

- Wenn eine **FlowDecision** in der Auswahl enthalten ist und die **FlowDecision** keine ausgehenden Connectors aufweist, wird der Connector in der **true** -Verzweigung platziert.

### <a name="expression-editing"></a>Ausdrucksbearbeitung

Standardmäßig gelten die Standard Tastenkombinationen für die Visual Basic Textbearbeitung innerhalb des Ausdrucks-Editors in Workflow-Designer, wobei die folgenden Einschränkungen gelten:

- Eine Neuzuordnung der Tastenkombinationen für die folgenden Befehle ist wirkungslos. Beim Bearbeiten eines Ausdrucks können Sie nur über die Standardtastenkombinationen auf diese Befehle zugreifen.

  - Ausschneiden
  - Kopieren
  - Einfügen
  - Alles auswählen
  - Rückgängig
  - Wiederholen

- Um die Tastenkombinationen für Befehle zur Ausdrucks Bearbeitung innerhalb Workflow-Designer in Visual Studio neu zuzuordnen, bearbeiten Sie die Verknüpfungen im Workflow-Designer Bereich. Im Text-Editor-Bereich vorgenommene Änderungen gelten nicht automatisch für Workflow-Designer. Wenn Sie Verknüpfungen an beiden Stellen neu zuordnen möchten, müssen Sie die Änderungen zweimal (einmal für jeden Bereich) vornehmen.
