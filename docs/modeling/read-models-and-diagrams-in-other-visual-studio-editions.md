---
title: Lesen von Modellen und Diagrammen in anderen Versionen von Visual Studio
description: Erfahren Sie mehr über das Lesen von Modellen und Diagrammen in Visual Studio sowie das schreibgeschützte Verhalten, wenn Sie eine Version von Visual Studio verwenden, die keine Modell Erstellung unterstützt.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- models, versions of Visual Studio
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ffbf39421f507338d14a6b05a667ec4301375067
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2020
ms.locfileid: "97360688"
---
# <a name="read-models-and-diagrams-in-other-visual-studio-editions"></a>Lesen von Modellen und Diagrammen in anderen Versionen von Visual Studio

Wenn Sie ein Model in einer Version von Visual Studio öffnen, die keine Modellerstellung unterstützt, wird das Modell im schreibgeschützten Modus geöffnet. In diesem Modus können Sie das Layout der Diagramme ändern, aber nicht das Modell.

Welche Versionen von Visual Studio die Modell Erstellung unterstützen, erfahren Sie unter [Versions Unterstützung für Architektur-und Modellierungstools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="obtaining-access-to-a-model-and-diagrams"></a>Erhalten von Zugriff auf ein Modell und Diagramme

Zum Lesen eines Abhängigkeits Diagramms müssen Sie zunächst Visual Studio verwenden, um das Modellierungsprojekt zu öffnen, und dann das Diagramm darin öffnen.

Wenn Sie ein Abhängigkeits Diagramm lesen möchten, müssen Sie aus diesem Grund auch Zugriff auf das Modellierungsprojekt haben, in dem es erstellt wurde. Dazu können Sie entweder über die Quell Code Verwaltung auf das Projekt zugreifen oder eine Kopie der Projektdateien abrufen.

> [!NOTE]
> Dies gilt nicht für Codezuordnungen und .NET-Klassendiagramme, die aus Code generiert wurden. Diese Diagramme können unabhängig von einem Modellierungsprojekt angezeigt werden.

Wenn Sie ein Abhängigkeits Diagramm lesen möchten, benötigen Sie mindestens die folgenden Dateien:

- Die beiden Diagramm Dateien für das Diagramm, das Sie lesen möchten, z. b. " **mydiagram. classdiagram" und "mydiagram. classdiagram. Layout**".

    > [!NOTE]
    > Für Abhängigkeits Diagramme sollten Sie auch über die Datei mit dem Namen " _mydiagram_**. layerdiagram. Suppression**" verfügen.

- Die Modellierungsprojekt Datei (**MyModel. modelproj**)

- Die Stamm Modelldatei (**ModelDefinition\MyModel.UML**)

- Die Paketdateien für ein beliebiges Paket, auf das im Diagramm verwiesen wird (**ModelDefinition\MyPackage.UML**).

## <a name="changes-that-you-can-make-in-read-only-mode"></a>Änderungen, die Sie im schreibgeschützten Modus vornehmen können

Wenn Sie ein Modell und seine Diagramme in einer Version von Visual Studio öffnen, die keine Modellerstellung unterstützt, können Sie das Modell nicht ändern. Das heißt, dass Sie nicht die Elemente und Beziehungen ändern können, die in den Diagrammen oder im Modell-Explorer angezeigt werden. Sie können jedoch einige Änderungen am Layout der Diagramme vornehmen:

- Anordnen von Formen und Konnektoren im Diagramm.

- Erweitern und Reduzieren von Formen.

Sie können diese Änderungen speichern. Wenn Sie die Änderungen für andere Benutzer sichtbar machen möchten, müssen Sie mindestens die aktualisierten **Layoutdateien** senden.

## <a name="see-also"></a>Siehe auch

- [Abhängigkeitsdiagramme: Referenz](../modeling/layer-diagrams-reference.md)
- [Erstellen von Modellen für Ihre App](../modeling/create-models-for-your-app.md)
