---
title: Freigeben des Unity-Protokollrückrufs für VSTU | Microsoft-Dokumentation
description: Hier erfahren Sie, wie Sie Ihren Unity-Protokollrückruf für denjenigen freigeben, der in Visual Studio-Tools für Unity (VSTU) registriert ist, um die dazugehörige Konsole an Visual Studio zu streamen.
ms.custom: ''
ms.date: 07/26/2018
ms.technology: vs-unity-tools
ms.topic: how-to
ms.assetid: 5d71f906-6e50-4399-b59b-d38c6dfef7ee
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 88abc27ad757487ae8f65b8bbb66d4dfee9791cc
ms.sourcegitcommit: 01c1b040b12d9d43e3e8ccadee20d6282154faad
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/14/2020
ms.locfileid: "92039871"
---
# <a name="share-the-unity-log-callback-with-vstu"></a>Freigeben des Unity-Protokollrückrufs für VSTU
Visual Studio-Tools für Unity registrieren einen Protokollrückruf bei Unity, damit dessen Konsole in Visual Studio gestreamt werden kann. Wenn Ihre Editorskripts auch einen Protokollrückruf bei Unity registrieren, kann der VSTU-Rückruf Ihren Rückruf stören. Um dies zu verhindern, verwenden Sie das Ereignis `VisualStudioIntegration.LogCallback` für die Zusammenarbeit mit VSTU.

## <a name="demonstrates"></a>Zeigt
 Das Freigeben des von Visual Studio-Tools für Unity erstellten Unity-Protokollrückrufs.

## <a name="example"></a>Beispiel

```csharp
#if ENABLE_VSTU
using System;

using UnityEngine;
using UnityEditor;

using SyntaxTree.VisualStudio.Unity.Bridge;

[InitializeOnLoad]
public class LogCallbackHook
{
    static LogCallbackHook()
    {
        VisualStudioIntegration.LogCallback += (string condition, string trace, LogType type) =>
        {
            // place code that implements your log callback here
        };
    }
}
#endif
```

## <a name="see-also"></a>Siehe auch
 [Beispiel: Erstellen der Projektdatei](../cross-platform/customize-project-files-created-by-vstu.md)
