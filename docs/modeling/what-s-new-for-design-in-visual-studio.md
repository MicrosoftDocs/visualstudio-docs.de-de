---
title: Neuerungen beim Entwurf in Visual Studio 2017
description: Erfahren Sie mehr über die neuen Features für den Code Entwurf, wie die Live-Abhängigkeits Überprüfung, die in Visual Studio 2017 verfügbar sind.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio], architecture and modeling
- architecture [Visual Studio], modeling
- modeling software [Visual Studio], What's New
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: bf622d9762e86bcb75a08c60085a15abb6fdca91
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2020
ms.locfileid: "97360974"
---
# <a name="whats-new-for-design-in-visual-studio-2017"></a>Neuerungen beim Entwurf in Visual Studio 2017

## <a name="live-dependency-validation"></a>Live-Abhängigkeits Überprüfung

Das Entfernen unerwünschter Abhängigkeiten ist ein wichtiger Bestandteil der Verwaltung ihrer technischen Schulden. Visual Studio bietet eine Live Validierung der Abhängigkeiten, einschließlich präziser Informationen zu Problemen, z. b. wo Sie sich befinden. Die Live-Abhängigkeits Überprüfung bietet vollständige Vorteile der neuen Features im Fehlerliste und im Editor.

![Live-Abhängigkeits Validierung in Aktion](media/dep-validation-whatsnew-01.png)

Die Erstellungs Funktion wurde geändert, damit die Abhängigkeits Überprüfung leichter erkennbar und leichter zugänglich ist. Die Terminologie wurde von "ebenendiagramm" in "Abhängigkeits Diagramm" geändert.

Das Menü **Architektur** enthält jetzt einen Befehl, mit dem Sie direkt ein Abhängigkeits Diagramm erstellen können:

![Live-Abhängigkeits Element im Menü "Architektur"](media/dep-validation-whatsnew-02.png)

Ebeneneigenschaftennamen und Beschreibungen wurden geändert, um Sie aussagekräftiger zu machen:

![Aktualisieren von Eigenschaftsnamen für Live Abhängigkeiten](media/dep-validation-whatsnew-03.png)

Wenn Sie das Diagramm speichern, sehen Sie sofort die Auswirkung Ihrer Änderungen in den Analyseergebnissen auf den aktuellen Code in der Projekt Mappe. Sie müssen nicht auf den Abschluss des Befehls " **Abhängigkeiten** überprüfen" warten.

Weitere Informationen finden Sie in [diesem Blogbeitrag](https://devblogs.microsoft.com/devops/live-architecture-dependency-validation-in-visual-studio-15-preview-5/).

## <a name="uml-designers-have-been-removed"></a>UML-Designer wurden entfernt.

Die UML-Designer wurden aus Visual Studio entfernt.

* UML-Diagramme werden nun als XML-Dateien dargestellt.
* Der UML-Modell-Explorer ist nicht mehr vorhanden.
* Modellierungsprojekt Verweise werden nicht mehr für die Abhängigkeits Validierung verwendet
* Der Knoten "ebenenverweise" in Projektmappen-Explorer wird nicht mehr angezeigt.
* Die Buildaktion "Validate" (überprüfen) auf einem Abhängigkeits Diagramm (Schicht Diagramm) wird nicht mehr verwendet, und die Buildaufgabe wurde entfernt.
* Die Projektstruktur wird für das Roundtrip Zwischenversionen beibehalten.
* Sie können ein Abhängigkeits Diagramm (Schicht Diagramm) weiterhin im XML-Format öffnen, erstellen, bearbeiten und speichern.
* TFS-Arbeitselemente, die mit einem Abhängigkeits Diagramm (Schicht) verknüpft sind, sind auf der Entwurfs Oberfläche nicht zugänglich.
* Das Verknüpfen von mit DSL oder einer Ebene wird nicht mehr unterstützt.
* Die UML-Erweiterbarkeit im Modellierungs-SDK wird nicht mehr unterstützt.

Unterstützung für die Visualisierung der Architektur von .net-und C++-Code ist über [Code Maps](map-dependencies-across-your-solutions.md)verfügbar.

Wenn Sie ein bedeutender Benutzer der UML-Designer sind, können Sie Visual Studio 2015 oder frühere Versionen weiterhin verwenden, während Sie sich für ein alternatives Tool für Ihre UML-Anforderungen entscheiden.

Weitere Informationen finden Sie in [diesem Blogbeitrag](https://devblogs.microsoft.com/devops/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/).

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="edition-support-for-architecture-and-modeling-tools"></a><a name="VersionSupport" />Editions Unterstützung für Architektur-und Modellierungstools

Visual Studio ist in verschiedenen Editionen verfügbar. Nicht alle diese bieten Unterstützung für die Architektur-und Modellierungstools. Die folgende Tabelle zeigt die Verfügbarkeit jedes Tools.

|**Feature**|**Enterprise Edition**|**Professional Edition**|**Community-Edition**|
|-|-|-|-|
|**Codezuordnungen**|Ja|Unterstützt nur das Lesen von Code Maps, das Filtern von Code Maps, das Hinzufügen neuer generischer Knoten und das Erstellen eines neuen gerichteten Diagramms aus einer Auswahl.|-|
|**Abhängigkeitsdiagramme**|Ja|Unterstützt nur das Lesen von Abhängigkeits Diagrammen.|Unterstützt nur das Lesen von Abhängigkeits Diagrammen.|
|**Gesteuerte Diagramme** (dgml-Diagramme)|Ja|Ja|Ja|
|**Codeklon**|Ja|-|-|
