---
title: Festlegen mehrerer Startprojekte
description: In diesem Artikel wird beschrieben, wie Sie festlegen, dass mehrere Projekte beim Ausführen oder Debuggen gestartet werden.
author: jmatthiesen
ms.author: jomatthi
ms.date: 11/09/2020
ms.topic: how-to
ms.prod: visual-studio-mac
ms.assetid: fd354fff-ce6b-4505-a815-84a2311e39ba
ms.openlocfilehash: df1e088a5e2d0f65d8b72dad0895f1edb1740f1f
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493568"
---
# <a name="set-multiple-startup-projects"></a>Festlegen mehrerer Startprojekte

In Visual Studio für Mac können Sie angeben, dass mehrere Projekte gestartet werden sollen, wenn Sie Ihre Projektmappe debuggen oder ausführen.

## <a name="to-set-multiple-startup-projects"></a>So legen Sie mehrere Startprojekte fest

1. Wählen Sie im Projektmappenfenster die Projektmappe aus (den obersten Knoten).

2. Klicken Sie mit der rechten Maustaste auf den Knoten der Projektmappe, und wählen Sie **Startprojekte festlegen** aus:

   ![Auswählen von „Startprojekte festlegen“](media/startup-proj-ctx-menu.png)

3. Das Dialogfeld **Laufzeitkonfiguration für Projektmappe erstellen** wird geöffnet. In diesem Dialogfeld können Sie eine neue Laufzeitkonfiguration für die Projektmappe erstellen. Sie können einen beliebigen Namen verwenden. Der Standardname ist `Multiple Projects`.

   ![Dialogfeld „Laufzeitkonfiguration für Projektmappe erstellen“](media/create-sln-run-config.png)

4. Klicken Sie auf **Laufzeitkonfiguration erstellen**. Das Dialogfeld **Projektmappenoptionen** wird geöffnet. Hierbei ist die neue Laufzeitkonfiguration für die Projektmappe ausgewählt:

   ![Dialogfeld „Projektmappenoptionen“](media/sln-options-run-config-multi-projects.png)

5. Wählen Sie die Projekte aus, die Sie beim Debuggen oder Ausführen Ihrer App in Visual Studio für Mac starten möchten:

   ![Dialogfeld „Projektmappenoptionen“ mit ausgewählten Projekten](media/sln-options-run-config-multi-projects-configured.png)

6. Klicken Sie auf **OK**. Die neue Laufzeitkonfiguration für die Projektmappe wird als aktive Laufzeitkonfiguration festgelegt:

   ![Projektmappe mit mehreren Projekten, die so konfiguriert sind, dass sie beim Debuggen gestartet oder ausgeführt werden](media/startup-project-configured.png)

   Nun werden die beiden Projekte für den Start konfiguriert, was durch die **Fettformatierung** beider Projekte im Projektmappenfenster angezeigt wird. Auf der Symbolleiste wurde die neue Laufzeitkonfiguration als aktuelle Laufzeitkonfiguration für die Projektmappe festgelegt.

## <a name="next-steps"></a>Nächste Schritte

- [Kompilieren und Generieren in Visual Studio für Mac](compiling-and-building.md)
- [Grundlagen der Buildkonfiguration](configurations.md)
