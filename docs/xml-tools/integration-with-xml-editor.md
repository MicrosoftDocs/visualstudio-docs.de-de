---
title: Integration des XML-Schema-Designers in XML-Editor
description: In diesem Artikel erfahren Sie mehr über die Integration zwischen dem XML-Schema-Designer und dem XML-Editor sowie darüber, wie Änderungen in diesen dargestellt werden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 43d7a8e6-bd94-4407-a800-15a145c74223
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9fe1bfcd422dbfc5f010ae7819e2fccbeafb8227
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934623"
---
# <a name="integration-with-xml-editor"></a>Integration in den XML-Editor

Der XML-Schema-Designer ist in den XML-Editor integriert. Wenn Sie eine XSD-Datei im XML-Editor ändern, wird die Änderung im [XML-Schema-Editor](../xml-tools/xml-schema-explorer.md) widergespiegelt. Falls die [Diagrammansicht](../xml-tools/graph-view.md) oder [Inhaltsmodellansicht](../xml-tools/content-model-view.md) geöffnet ist, wird die Änderung dort ebenfalls wiedergegeben. Sie können wie folgt zwischen dem XML-Schema-Designer und dem XML-Editor navigieren:

- Klicken Sie im XML-Editor mit der rechten Maustaste auf einen Knoten, und wählen Sie **In XML-Schema-Explorer anzeigen** aus.

- Doppelklicken Sie in der Diagrammansicht und im **XML-Schema-Explorer** auf einen Knoten, oder klicken Sie mit der rechten Maustaste auf einen Knoten, und wählen Sie **Code anzeigen** aus. Klicken Sie in der Inhaltsmodellansicht mit der rechten Maustaste auf einen Knoten, und wählen Sie **Code anzeigen** aus.

Die folgende Bildschirmabbildung zeigt ein im **XML-Schema-Explorer** geöffnetes XML-Schema. Der **XML-Schema-Explorer** zeigt das Schemaset in einer Strukturansicht an. Der XML-Editor zeigt die Textansicht des aktuell im **XML-Schema-Explorer** aktiven Knotens an.

![Screenshot: Visual Studio-Projekt mit einem XML-Knoten im Bereich des XML-Editors und eine Strukturansicht des festgelegten Schemas im Bereich des XML-Schema-Explorers.](../xml-tools/media/xsddesignerwithxmleditor.gif)

Manchmal ist es hilfreich, den Code im XML-Editor und dem grafischen Designer nebeneinander zu sehen. Klicken Sie an einer beliebigen Stelle im XML-Editor mit der rechten Maustaste, und wählen Sie **Ansichts-Designer** aus, um beide Dateien gleichzeitig anzuzeigen. Wählen Sie im Visual Studio-Menü „Fenster“ die Option **Neue horizontale (oder vertikale) Registerkartengruppe** aus.

![Screenshot: Visual Studio-Projekt mit den Bereichen „Ansicht-Designer“, „XML-Editor“ und „XML-Schema-Explorer“](../xml-tools/media/xsddesignerwithxmleditorandcmv.gif)

## <a name="see-also"></a>Siehe auch

- [XML-Schema-Explorer](../xml-tools/xml-schema-explorer.md)
