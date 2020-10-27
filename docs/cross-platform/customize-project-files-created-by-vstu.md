---
title: Anpassen mit VSTU erstellter Projektdateien | Microsoft-Dokumentation
description: Hier erfahren Sie, wie Sie von Visual Studio-Tools für Unity (VSTU) erstellte Projektdateien anpassen. Sie überprüfen ein C#-Codebeispiel.
ms.custom: ''
ms.date: 07/26/2018
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 60b8cc1d-cacc-404d-b768-77e81bc354f8
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: a2e4abb707f07e0a781460e5efe6996325e5ca00
ms.sourcegitcommit: 01c1b040b12d9d43e3e8ccadee20d6282154faad
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/14/2020
ms.locfileid: "92039424"
---
# <a name="customize-project-files-created-by-vstu"></a>Anpassen von mit VSTU erstellten Projektdateien
Visual Studio-Tools für Unity bieten während der Generierung der Projektdatei einen Rückruf im Unity-Stil. Registrieren Sie das `VisualStudioIntegration.ProjectFileGeneration`-Ereignis, um die Projektdatei zu ändern, immer wenn sie neu erstellt wird.

## <a name="demonstrates"></a>Zeigt
 Anpassen der von Visual Studio-Tools für Unity generierten Visual Studio-Projektdateien.

## <a name="example"></a>Beispiel

```csharp
#if ENABLE_VSTU
using System;
using System.IO;
using System.Linq;
using System.Text;
using System.Xml.Linq;

using UnityEngine;
using UnityEditor;

using SyntaxTree.VisualStudio.Unity.Bridge;

[InitializeOnLoad]
public class ProjectFileHook
{
    // necessary for XLinq to save the xml project file in utf8
    class Utf8StringWriter : StringWriter
    {
        public override Encoding Encoding
        {
            get { return Encoding.UTF8; }
        }
    }

    static ProjectFileHook()
    {
        ProjectFilesGenerator.ProjectFileGeneration += (string name, string content) =>
        {
            // parse the document and make some changes
            var document = XDocument.Parse(content);
            document.Root.Add(new XComment("FIX ME"));

            // save the changes using the Utf8StringWriter
            var str = new Utf8StringWriter();
            document.Save(str);

            return str.ToString();
        };
    }
}
#endif
```

## <a name="see-also"></a>Siehe auch
 [Beispiel: Protokollrückruf](../cross-platform/share-the-unity-log-callback-with-vstu.md)
