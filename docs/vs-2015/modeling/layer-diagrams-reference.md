---
title: 'Ebenendiagramme: Referenz | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.layerdiagram.layerexplorer.artifactlink
- vs.teamarch.layerdiagram.layerexplorer.artifactlink.properties
- vs.teamarch.layerdiagram.diagram
- vs.teamarch.UMLModelExplorer.layerdiagram
- vs.teamarch.layerdiagram.layerexplorer
- vs.teamarch.layerdiagram.shapes.properties
- vs.teamarch.layerdiagram.toolbox
helpviewer_keywords:
- architecture, layer diagrams
- layer diagrams
- diagrams - modeling, layer
- constraints, architectural
ms.assetid: f26c986c-1e79-420e-b29a-a283e6d8a71d
caps.latest.revision: 35
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 448a74b739bbb339d5f3b3e56c0ba59072994109
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850615"
---
# <a name="layer-diagrams-reference"></a>Ebenendiagramme: Referenz
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio können Sie ein *ebenendiagramm* verwenden, um die logische Architektur des Systems auf hoher Ebene visuell darzustellen. Ein ebenendiagramm organisiert die physischen Artefakte in Ihrem System in logische, abstrakte Gruppen, die als *Ebenen*bezeichnet werden. Diese Ebenen beschreiben die Hauptaufgaben, die von diesen Artefakten ausgeführt werden, oder die Hauptkomponenten des Systems. Jede Ebene kann außerdem geschachtelte Ebenen enthalten, die ausführlichere Aufgaben beschreiben.

 Welche Versionen von Visual Studio dieses Feature unterstützen, erfahren Sie unter [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Sie können die vorgesehenen oder vorhandenen Abhängigkeiten zwischen Ebenen angeben. Diese als Pfeile dargestellten Abhängigkeiten geben an, welche Ebenen die Funktionen verwenden können bzw. welche Ebenen die Funktionen derzeit verwenden, die durch andere Ebenen dargestellt werden. Indem es das System in Ebenen organisiert, die eindeutige Rollen und Funktionen beschreiben, kann ein Ebenendiagramm das Verstehen, Wiederverwenden und Verwalten von Code vereinfachen.

 Verwenden Sie ein Ebenendiagramm als Unterstützung bei folgenden Aufgaben:

- Kommunizieren der vorhandenen oder vorgesehenen logischen Architektur des Systems

- Ermitteln von Konflikten zwischen dem vorhandenen Code und der vorgesehenen Architektur

- Visualisieren der Auswirkungen von Änderungen auf die vorgesehene Architektur beim Umgestalten, Aktualisieren oder Entwickeln des Systems

- Untermauern der vorgesehenen Architektur während der Entwicklung und Wartung des Codes durch Einschließen von Validierung in Eincheck- und Buildvorgänge

  In diesem Thema werden die Elemente beschrieben, die Sie in Ebenendiagrammen verwenden können. Ausführlichere Informationen zum Erstellen und Zeichnen von ebenendiagrammen finden Sie unter [ebenendiagramme: Richtlinien](../modeling/layer-diagrams-guidelines.md). Weitere Informationen zu ebenenmustern finden Sie auf der [Seite Patterns & Practices](https://apparch.codeplex.com/Wiki/View.aspx?title=Application Patterns&referringTitle=Home).

## <a name="reading-layer-diagrams"></a>Lesen von Ebenendiagrammen
 ![Elemente in Ebenendiagrammen](../modeling/media/uml-layerrefreading.png "UML_LayerRefReading")

 In der folgenden Tabelle werden die Elemente beschrieben, die in einem Ebenendiagramm verwendet werden können.

|**Form**|**Element**|**Beschreibung**|
|---------------|-----------------|---------------------|
|1|**Ebene**|Eine logische Gruppe von physischen Artefakten im System. Diese Artefakte können Namespaces, Projekte, Klassen, Methoden usw. sein.<br /><br /> Um die mit einer Ebene verknüpften Artefakte anzuzeigen, öffnen Sie das Kontextmenü für die Ebene, und klicken Sie dann auf **Links anzeigen** , um den **Ebenen-Explorer**zu öffnen.<br /><br /> Weitere Informationen finden Sie unter [Ebenen-Explorer](#Explorer).<br /><br /> -   Unzulässige **Namespace Abhängigkeiten** : gibt an, dass die dieser Ebene zugeordneten Artefakte nicht von den angegebenen Namespaces abhängen können.<br />-   Unzulässige **Namespaces** : gibt an, dass die dieser Ebene zugeordneten Artefakte nicht zu den angegebenen Namespaces gehören dürfen.<br />-   **Erforderliche Namespaces** : gibt an, dass die dieser Ebene zugeordneten Artefakte zu einem der angegebenen Namespaces gehören müssen.|
|2|**Abhängigkeit**|Gibt an, dass eine Ebene die Funktionen in einer anderen Ebene verwenden darf, jedoch nicht umgekehrt.<br /><br /> -   **Direction** : gibt die Richtung der Abhängigkeit an.|
|3|**Bidirektionale Abhängigkeit**|Gibt an, dass eine Ebene die Funktionen in einer anderen Ebene verwenden darf und umgekehrt.<br /><br /> -   **Direction** : gibt die Richtung der Abhängigkeit an.|
|4|**Comment**|Verwenden Sie einen Kommentar, um dem Diagramm oder Elementen im Diagramm allgemeine Hinweise hinzuzufügen.|
|5|**Kommentarverknüpfung**|Verwenden Sie dieses Feature, um Kommentare mit Elementen im Diagramm zu verknüpfen.|

## <a name="layer-explorer"></a><a name="Explorer"></a> Ebenenexplorer
 Sie können jede Ebene mit Artefakten in der Projektmappe verknüpfen, z. B. Projekte, Klassen, Namespaces, Projektdateien und andere Teile der Software. Die Zahl auf einer Ebene zeigt die Anzahl von Artefakten an, die mit der Ebene verknüpft sind. Beachten Sie jedoch beim Lesen der Anzahl der Artefakte in einer Ebene Folgendes:

- Wenn eine Ebene mit einem Artefakt verknüpft ist, das andere Artefakte enthält, die Ebene jedoch nicht direkt mit den anderen Artefakten verknüpft ist, umfasst die Zahl nur das verknüpfte Artefakt. Die anderen Artefakte werden jedoch während der Ebenenvalidierung für die Analyse berücksichtigt.

   Ist z. B. eine Ebene mit einem einzelnen Namespace verknüpft, ist die Anzahl der verknüpften Artefakte 1, auch wenn der Namespace Klassen enthält. Wenn die Ebene auch mit den einzelnen Klassen im Namespace verknüpft ist, umfasst die Zahl die verknüpften Klassen.

- Wenn eine Ebene andere Ebenen enthält, die mit Artefakten verknüpft sind, ist die Containerebene ebenfalls mit diesen Artefakten verknüpft, obwohl in der Zahl auf der Containerebene diese Artefakte nicht berücksichtigt sind.

  Weitere Informationen zum Verknüpfen von Ebenen und Artefakten finden Sie unter:

- [Ebenendiagramme: Richtlinien](../modeling/layer-diagrams-guidelines.md)

- [Erstellen von Ebenendiagrammen aus Ihrem Code](../modeling/create-layer-diagrams-from-your-code.md)

#### <a name="to-examine-the-linked-artifacts"></a>So untersuchen Sie die verknüpften Artefakte

- Öffnen Sie im ebenendiagramm das Kontextmenü für eine oder mehrere Ebenen, und wählen Sie dann **Verknüpfungen anzeigen**aus.

     Der **Ebenen-Explorer** wird geöffnet und zeigt die Artefakte an, die mit den ausgewählten Ebenen verknüpft sind. Der **ebenenexplorer** verfügt über eine Spalte, in der die einzelnen Eigenschaften der artefaktlinks angezeigt werden.

    > [!NOTE]
    > Wenn nicht alle diese Eigenschaften angezeigt werden, erweitern Sie das Fenster **Ebenen-Explorer** .

    |**Spalte im Ebenen-Explorer**|**Beschreibung**|
    |----------------------------------|---------------------|
    |**Kategorien**|Die Art des Artefakts, z. B. Klasse, Namespace, Quelldatei usw.|
    |**Ebene**|Die Ebene, die mit dem Artefakt verknüpft ist.|
    |**Unterstützt die Validierung**|Wenn **true**, kann der ebenenvalidierungsprozess überprüfen, ob das Projekt Abhängigkeiten zu oder von diesem Element entspricht.<br /><br /> Wenn der Wert **false**ist, wird der Link nicht an dem ebenenvalidierungsprozess beteiligt.<br /><br /> Weitere Informationen finden Sie unter [ebenendiagramme: Richtlinien](../modeling/layer-diagrams-guidelines.md).|
    |**Bezeichner**|Der Verweis auf das verknüpfte Artefakt|

## <a name="see-also"></a>Weitere Informationen
 [Erstellen von Modellen für Ihre App](../modeling/create-models-for-your-app.md)
