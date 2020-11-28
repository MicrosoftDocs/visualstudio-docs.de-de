---
title: Suchen der Aufrufe einer Methode
description: Erfahren Sie, wie Sie mit dem Fenster „Aufrufhierarchie“ alle Aufrufe einer ausgewählten Methode, Eigenschaft oder eines ausgewählten Konstruktors und manchmal von ihnen ausgehende Aufrufe verfolgen können.
ms.custom: SEO-VS-2020
ms.date: 05/18/2018
ms.topic: reference
f1_keywords:
- VS.CallHierarchy
helpviewer_keywords:
- Call Hierarchy
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 75c330855d3fca1187f88171adb893c3f77c4ccd
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/25/2020
ms.locfileid: "95871404"
---
# <a name="view-call-hierarchy"></a>Anzeigen der Aufrufhierarchie

Durch Anzeigen der Aufrufhierarchie für Ihren Code können Sie in allen Aufrufen an und manchmal aus einer ausgewählten Methode, einer ausgewählten Eigenschaft oder einem ausgewählten Konstruktor navigieren. So verstehen Sie, wie der Code funktioniert und können die Auswirkungen von Codeänderungen besser bewerten. Sie können mehrere Codeebenen überprüfen, um komplexe Methodenaufrufketten und zusätzliche Einstiegspunkte in den Code anzuzeigen. So können Sie sämtliche möglichen Ausführungswege erkunden.

In Visual Studio können Sie eine Aufrufhierarchie zur Entwurfszeit anzeigen. Sie müssen also keinen Haltepunkt setzen und den Debugger starten, um die Laufzeit-Aufrufliste anzuzeigen.

## <a name="use-the-call-hierarchy-window"></a>Verwenden des Fensters „Aufrufhierarchie“

Klicken Sie mit der rechten Maustaste im Code-Editor auf den Namen einer Methode, Eigenschaft oder eines Konstruktoraufrufs, damit das Fenster **Aufrufhierarchie** angezeigt wird. Klicken Sie anschließend auf **Aufrufhierarchie anzeigen**.

Der Membername erscheint in einem Strukturansichtsbereich im Fenster **Aufrufhierarchie**. Wenn Sie den Memberknoten erweitern, werden die Unterknoten **Calls To (Aufrufe an)** *Membername* und in C++ **Calls From (Aufrufe von)** *Membername* angezeigt.

In C++-Code können Sie Aufrufe sowohl an als auch von einem Member anzeigen:

![Aufrufhierarchie für C++-Code in Visual Studio](media/call-hierarchy-cpp.png)

In C#- und Visual Basic-Code können Sie Aufrufe an einen Member sehen, aber keine Aufrufe von diesem:

![Aufrufhierarchie für C#-Code in Visual Studio](media/call-hierarchy-csharp.png)

- Wenn Sie den **Calls To**-Knoten erweitern, werden alle Members angezeigt, die den ausgewählten Member aufrufen.

- Wenn Sie in C++ den **Calls From**-Knoten erweitern, werden alle Member angezeigt, die den ausgewählten Member aufrufen.

Sie können jeden aufrufenden Member erweitern, um die **Calls To**-Knoten sowie in C++ die **Call From**-Knoten anzeigen zu lassen. Dadurch können Sie, wie in der folgenden Abbildung dargestellt, in den Aufruferstapel navigieren:

![Fenster Aufrufhierarchie mit mehreren erweiterten Ebenen](media/call-hierarchy-csharp-expanded.png)

Für Members, die als virtuell oder abstrakt definiert sind, wird ein **Overrides method name**-Knoten (Knoten zur Außerkraftsetzung des Methodennamens) angezeigt. Für Schnittstellenmember wird ein Knoten zum **Implementieren des Methodennamens** angezeigt. Diese erweiterbaren Knoten erscheinen auf derselben Ebene wie **Calls To**- und **Calls From**-Knoten.

Das Feld **Suchbereich** in der Symbolleiste enthält verschiedene Auswahlmöglichkeiten für **My Solution** („Meine Projektmappe“), **Aktuelles Projekt** und **Aktuelles Dokument**.

Wenn Sie im Strukturansichtsbereich **Aufrufhierarchie** einen untergeordneten Member auswählen:

- Im Detailbereich **Aufrufhierarchie** werden alle Codezeilen angezeigt, in denen dieser untergeordnete Member von dem übergeordneten Member aufgerufen wird.

- Wenn das **Codedefinitionsfenster** geöffnet ist, zeigt es den Code für den ausgewählten Member an (nur C++). Weitere Informationen zu diesem Fenster finden Sie unter [Anzeigen der Codestruktur](../../ide/viewing-the-structure-of-code.md).

> [!NOTE]
> Die **Aufrufhierarchie** findet keine Methodengruppenverweise, die Stellen enthalten, an denen eine Methode als Ereignishandler hinzugefügt oder einem Delegaten zugewiesen wird. Verwenden Sie den Befehl **Alle Verweise suchen**, um alle Verweise auf eine Methode zu suchen.

## <a name="shortcut-menu-items"></a>Kontextmenüelemente

In der folgenden Tabelle werden einige Kontextmenüoptionen beschrieben, auf die Sie zugreifen können, wenn Sie mit der rechten Maustaste auf einen Knoten im Strukturansichtsbereich klicken.

|Kontextmenüelement|BESCHREIBUNG|
| - |-----------------|
|**Als neuen Stamm hinzufügen**|Fügt dem Strukturansichtsbereich den ausgewählten Knoten als neuen Stammknoten hinzu. Dadurch können Sie sich auf eine bestimmte Unterstruktur konzentrieren.|
|**Stamm entfernen**|Entfernt den ausgewählten Stammknoten aus dem Strukturansichtsbereich. Diese Option ist nur in einem Stammknoten verfügbar.<br /><br /> Sie können außerdem die Symbolleistenschaltfläche **Stamm entfernen** verwenden, um den ausgewählten Stammknoten zu entfernen.|
|**Gehe zu Definition**|Führt den Befehl „Gehe zu Definition“ für den ausgewählten Knoten aus. Dadurch wird zu der ursprünglichen Definition für einen Memberaufruf oder eine Variablendefinition navigiert.<br /><br /> Sie können auch auf den ausgewählten Knoten doppelklicken, oder drücken Sie für den ausgewählten Knoten auf F12, um den Befehl „Gehe zu Definition“ auszuführen.|
|**Alle Verweise suchen**|Führt den Befehl „Alle Verweise suchen“ für den ausgewählten Knoten aus. So finden Sie alle Codezeilen in Ihrem Projekt, die auf eine Klasse oder einen Member verweisen.<br /><br /> Sie können auch auf UMSCHALT+F12 drücken, um den Befehl „Alle Verweise suchen“ für den ausgewählten Knoten auszuführen.|
|**Copy**|Kopiert die Inhalte des ausgewählten Knotens (aber nicht dessen Unterknoten).|
|**Aktualisieren**|Reduziert die ausgewählten Knoten, sodass bei der erneuten Erweiterung aktuelle Informationen angezeigt werden.|
