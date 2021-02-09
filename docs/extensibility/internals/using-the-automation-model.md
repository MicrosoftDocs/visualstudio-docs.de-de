---
title: Verwenden des Automatisierungs Modells | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie Eigenschaften und Methoden Ihres VSPackage abrufen, nachdem es mit dem Automatisierungs Modell verbunden ist.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], automation model
ms.assetid: 0c7f7889-fbfb-4b19-804f-b742138baecd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e856153462819599124f3dce2e16c6de9f01cdfc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883089"
---
# <a name="using-the-automation-model"></a>Verwenden des Automatisierungsmodells
Nachdem Sie das VSPackage mit Automation verbunden haben, können Sie die Eigenschaften und Methoden abrufen, indem Sie die- <xref:EnvDTE.DTEClass.GetObject%2A> Methode für das-Objekt aufrufen und <xref:EnvDTE._DTE> eine Zeichenfolge übergeben, die das Objekt darstellt, das Sie abrufen möchten.

## <a name="obtaining-project-objects"></a>Abrufen von Projekt Objekten
 Im folgenden finden Sie zwei Codebeispiele, die zeigen, wie ein automatisierungsconsumer die Project Automation-Objekte abruft. Weitere Informationen zum erhalten des DTE-Objekts finden Sie unter Gewusst [wie: verweisen auf die DTE-und DTE2-Objekte](/previous-versions/68shb4dw(v=vs.140)).

```vb
Sub DoAutomation()
    Dim MyProjects As Projects
    MyProjects = DTE.GetObject("AcmeProject")
End Sub
```

```cpp
void DoAutomation(void)
{
  CComQIPtr<Projects> pMyPkg; // Use an IDispatch-derived object type.
    pMyPkg = pDTE->GetObject("AcmeProjects");

   // The '=' performs a Query Interface.
   // Assumes pDTE is already available as a global.
   // Use pMyPkg to access your projects object's properties and methods.
}

```

 An diesem Punkt können Sie die Standard Projekt Objekte verwenden, die Teil eines bestimmten VSPackages sind, um das Hierarchie Modell zu verschieben.

 Im folgenden Codebeispiel wird veranschaulicht, wie ein benutzerdefiniertes Objekt, das eine Eigenschaft eines benutzerdefinierten Projekt Typs ist, angezeigt wird:

```vb
Dim MyPrj As Project
Dim MyPrjItem As ProjectItem
Dim objMyObject as MyExtendedObject

MyPrj = MyProjects.Item(1) 'use the Projects collection to get a project
objMyObject = MyPrj.Object 'You call .Object to get to special Project
                           'implementation
objMyObject.MySpecialMethodOrProperty
```

 Im folgenden Code werden die Namen aller Eigenschaften in der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Option Umgebung **Allgemein** im Menü Extras aufgeführt: 

```vb
dim objDTE
dim objEnv
set objDTE = CreateObject("VisualStudio.DTE")
set objEnv = objDTE.Properties("Environment", "General")
for each obj in ObjEnv
MsgBox obj.Name
Next

```

## <a name="see-also"></a>Weitere Informationen
- <xref:EnvDTE.DTEClass.GetObject%2A>