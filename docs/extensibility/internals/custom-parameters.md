---
title: Benutzerdefinierte Parameter | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie benutzerdefinierte Parameter erstellen, die den Vorgang eines Assistenten nach dem Start eines Assistenten steuern, indem Sie eine VSZ-Datei ändern.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- wizards, custom parameters
- custom parameters
ms.assetid: ba5c364b-66e6-47ea-9760-a0b70de8f0a0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1b4927e63bec93fbe7b6730e131a0893372aa70d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902966"
---
# <a name="custom-parameters"></a>Benutzerdefinierte Parameter
Benutzerdefinierte Parameter steuern den Vorgang eines Assistenten, nachdem ein Assistent gestartet wurde. Eine verwandte *VSZ* -Datei stellt ein Array von benutzerdefinierten Parametern bereit, die von der integrierten Entwicklungsumgebung (IDE) verpackt und beim Start des Assistenten als Zeichen folgen Array an den Assistenten übermittelt werden. Der Assistent analysiert dann das Array von Zeichen folgen und verwendet die Informationen, um die tatsächliche Ausführung des Assistenten zu steuern. Auf diese Weise kann ein Assistent die Funktionalität abhängig vom Inhalt der *VSZ* -Datei anpassen.

 Kontext Parameter definieren hingegen den Status des Projekts, wenn der Assistent gestartet wird. Weitere Informationen finden Sie unter [Kontext Parameter](../../extensibility/internals/context-parameters.md).

 Im folgenden finden Sie ein Beispiel für eine *VSZ* -Datei mit benutzerdefinierten Parametern:

```
VSWIZARD 8.0
Wizard=VsWizard.VsWizard_Engine
Param="WIZARD_NAME = Sample Wizard"
Param="WIZARD_UI = FALSE"
Param="RELATIVE_PATH = VSWizards\Classwiz\ATL"
Param="PREPROCESS_FUNCTION = CanAddATLSupport"
Param="PROJECT_TYPE = CSPROJ"
```

 Der Autor der *VSZ* -Datei fügt die Werte der Parameter hinzu. Wenn ein Benutzer im Menü **Datei** die Option **Neues Projekt** oder **Neues Element hinzufügen** oder in **Projektmappen-Explorer** mit der rechten Maustaste auf ein Projekt klickt, sammelt die IDE diese Werte in einem Array von Zeichen folgen. Die IDE ruft dann die-Methode des Projekts <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> mit dem <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> festgelegten Flag auf, und das Projekt Ruft die <xref:EnvDTE.IVsExtensibility.RunWizardFile%2A> Methode auf, die für die Ausführung des Assistenten zuständig ist, und gibt das Ergebnis zurück.

 Der Assistent ist dafür verantwortlich, das Array von Zeichen folgen zu parsen und entsprechend den Zeichen folgen zu agieren. Auf diese Weise können Sie durch die Implementierung von benutzerdefinierten Parametern einen Assistenten erstellen, der eine Vielzahl von Funktionen ausführt. Anders ausgedrückt: ein Assistent könnte drei verschiedene *VSZ* -Dateien haben. Jede Datei übergibt verschiedene Sätze von benutzerdefinierten Parametern, um das Verhalten des Assistenten in unterschiedlichen Situationen zu steuern.

 Weitere Informationen finden Sie in der [Assistenten Datei (VSZ-Datei)](../../extensibility/internals/wizard-dot-vsz-file.md).

## <a name="see-also"></a>Weitere Informationen
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>
- [Kontextparameter](../../extensibility/internals/context-parameters.md)
- [The](../../extensibility/internals/wizards.md)
- [Assistenten Datei (. vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
