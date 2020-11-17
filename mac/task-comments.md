---
title: Aufgabenkommentare
description: Hinzufügen von Aufgabenkommentaren zum Code
author: jmatthiesen
ms.author: jomatthi
ms.date: 11/09/2020
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: 02eacb312931d941b716ee65f91cd478eac8bb8a
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493529"
---
# <a name="task-comments"></a>Aufgabenkommentare

Beim Schreiben von Code ist es üblich, unerledigten oder fragwürdigen Code explizit zu kommentieren oder schnelle Problemumgehungen mit Warnungen zu erstellen. Die Standardsignaltoken von Visual Studio für Mac sind TODO, HACK, FIXME und UNDONE. Personalisierte Token können unter **Visual Studio > Einstellungen > Umgebung > Aufgaben** definiert werden, wie in der folgenden Abbildung dargestellt:

![Aufgabenliste unter Einstellungen](media/source-editor-image10.png)

Um einen neuen Aufgabenkommentar hinzuzufügen, fügen Sie einen Kommentar ein, der das Aufgabenschlüsselwort enthält. Beispiel:

```csharp
//TODO: Finish this for all properties.
```

In Visual Studio für Mac werden diese Markierungen hervorgehoben, indem sie im Fenster **Aufgabenliste** kenntlich gemacht werden, das Sie unter **Ansicht > Aufgaben** anzeigen können:

![Das Aufgabenlistenfenster mit einem einzelnen TODO-Element](media/source-editor-image11.png)

## <a name="see-also"></a>Weitere Informationen

- [Verwenden der Aufgabenliste (Visual Studio unter Windows)](/visualstudio/ide/using-the-task-list)