---
title: Assistenten Schnittstelle (IDTWizard) | Microsoft-Dokumentation
description: Die IDE verwendet die IDTWizard-Schnittstelle für die Kommunikation mit Assistenten. Assistenten müssen diese Schnittstelle implementieren, damit Sie in der IDE installiert werden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDTWizard interface
- wizards, interface
ms.assetid: 09618d9d-d115-45b6-bccc-de328994b39c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e87759a979d0c680018d99a1e18a12e645f430c6
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97487763"
---
# <a name="wizard-interface-idtwizard"></a>Assistentenschnittstelle (IDTWizard)
Die integrierte Entwicklungsumgebung (Integrated Development Environment, IDE) verwendet die- <xref:EnvDTE.IDTWizard> Schnittstelle für die Kommunikation mit Assistenten. Assistenten müssen diese Schnittstelle implementieren, um in der IDE installiert werden zu können.

 Die- <xref:EnvDTE.IDTWizard.Execute%2A> Methode ist die einzige Methode, die der- <xref:EnvDTE.IDTWizard> Schnittstelle zugeordnet ist. Assistenten implementieren diese Methode, und die IDE Ruft die-Methode für die-Schnittstelle auf. Im folgenden Beispiel wird die Signatur der-Methode veranschaulicht.

```
/* IDTWizard Method */
STDMETHOD(Execute)(THIS_
   /* [in] */ IDispatch *Application,
   /* [in] */ long hwndOwner,
   /* [in] */ SAFEARRAY * *ContextParams,
   /* [in] */ SAFEARRAY * *CustomParams,
   /* [out] [in] */ wizardResult *RetVal
   );
```

 Der Startmechanismus ist für die Assistenten " **Neues Projekt** " und " **Neues Element hinzufügen** " ähnlich. Um zu beginnen, müssen Sie die <xref:EnvDTE.IDTWizard> in "Dteinternal. h" definierte-Schnittstelle aufzurufen. Der einzige Unterschied ist der Satz von Kontext-und benutzerdefinierten Parametern, die beim Aufrufen der-Schnittstelle an die-Schnittstelle übermittelt werden.

 Die folgenden Informationen beschreiben die <xref:EnvDTE.IDTWizard> Schnittstelle, die Assistenten implementieren müssen, um in der IDE arbeiten zu können [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Die IDE Ruft die- <xref:EnvDTE.IDTWizard.Execute%2A> Methode für den Assistenten auf und übergibt dabei Folgendes:

- Das DTE-Objekt

     Das DTE-Objekt ist der Stamm des Automatisierungs Modells.

- Das Handle für das Fenster Dialogfeld, wie im Codesegment dargestellt `hwndOwner ([in] long)` .

     Der Assistent verwendet dieses `hwndOwner` als übergeordnetes Element für das Dialogfeld für den Assistenten.

- Kontext Parameter, die als Variant für SAFEARRAY an die Schnittstelle übergeben werden, wie im Codesegment dargestellt `[in] SAFEARRAY (VARIANT)* ContextParams` .

     Kontext Parameter enthalten ein Array von Werten, die für den Starttyp und den aktuellen Status des Projekts spezifisch sind. Die IDE übergibt die Kontext Parameter an den Assistenten. Weitere Informationen finden Sie unter [Kontext Parameter](../../extensibility/internals/context-parameters.md).

- Benutzerdefinierte Parameter, die an die Schnittstelle als Variant für SAFEARRAY übergeben werden, wie im Codesegment dargestellt `[in] SAFEARRAY (VARIANT)* CustomParams` .

     Benutzerdefinierte Parameter enthalten ein Array benutzerdefinierter Parameter. Eine VSZ-Datei übergibt benutzerdefinierte Parameter an die IDE. Die Werte werden durch die- `Param=` Anweisungen bestimmt. Weitere Informationen finden Sie unter [benutzerdefinierte Parameter](../../extensibility/internals/custom-parameters.md).

- Rückgabewerte für die-Schnittstelle sind

    ```
    wizardResultSuccess = -1,
    wizardResultFailure = 0
    wizardResultCancel = 1
    wizardResultBackout = 2
    ```

## <a name="see-also"></a>Weitere Informationen
- [Kontextparameter](../../extensibility/internals/context-parameters.md)
- [Benutzerdefinierte Parameter](../../extensibility/internals/custom-parameters.md)
- [The](../../extensibility/internals/wizards.md)
- [Assistentendatei (VSZ)](../../extensibility/internals/wizard-dot-vsz-file.md)
