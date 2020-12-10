---
title: Verwalten eines privaten Katalogs mithilfe von Registrierungs Einstellungen
description: Erfahren Sie, wie Sie den Zugriff auf die Steuerelemente, Vorlagen und Tools in der Visual Studio Gallery, in der Samples Gallery oder in privaten Galerien steuern können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSIX private galleries, managing
- managing VSIX private galleries
ms.assetid: 86b86442-4293-4cad-9fe2-876eef65f426
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d15d845f07310e3efcba6f05538a2207d9c416e4
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2020
ms.locfileid: "96994006"
---
# <a name="how-to-manage-a-private-gallery-by-using-registry-settings"></a>Vorgehensweise: Verwalten eines privaten Katalogs mithilfe von Registrierungs Einstellungen
Wenn Sie Administrator oder Entwickler einer isolierten Shellerweiterung sind, können Sie den Zugriff auf die Steuerelemente, Vorlagen und Tools in der Visual Studio Gallery, in der Beispiel Galerie oder in privaten Galerien steuern. Um einen Katalog verfügbar zu machen oder nicht verfügbar zu machen, erstellen Sie eine *pkgdef* -Datei, in der die geänderten Registrierungsschlüssel und deren Werte beschrieben werden.

## <a name="manage-private-galleries"></a>Private Galerien verwalten
 Sie können eine *pkgdef* -Datei erstellen, um den Zugriff auf Galerien auf mehreren Computern zu steuern. Diese Datei muss das folgende Format aufweisen:

```
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]
@={URI}  (REG_SZ)
Disabled=0 | 1 (DWORD)
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)
Protocol=Atom Feed|Sharepoint (REG_SZ)
DisplayName={DisplayName} (REG_SZ)
DisplayNameResourceID={ID} (REG_SZ)
DisplayNamePackageGuid={GUID} (REG_SZ)

```

 Der `Repositories` Schlüssel bezieht sich auf den Katalog, der aktiviert oder deaktiviert werden soll. Die Visual Studio Gallery und die Samples Gallery verwenden die folgenden Repository-GUIDs:

- Visual Studio Gallery: 0F 45e408-7995-4375-9485-86b8db553dc9

- Beispiel Katalog: AEB9CB40-D8E6-4615-B52C-27E307F8506C

  Der `Disabled` Wert ist optional. Standardmäßig ist ein-Katalog aktiviert.

  Der- `Priority` Wert bestimmt die Reihenfolge, in der die Galerien im Dialogfeld **Optionen** aufgelistet werden. Visual Studio Gallery hat Priorität 10, und die Samples Gallery hat Priorität 20. Private Galerien beginnen mit Priorität 100. Wenn mehrere Kataloge denselben Prioritätswert aufweisen, wird die Reihenfolge, in der Sie angezeigt werden, durch die Werte ihrer lokalisierten `DisplayName` Attribute bestimmt.

  Der `Protocol` Wert ist für Atom-basierte oder SharePoint-basierte Galerien erforderlich.

  Entweder `DisplayName` oder `DisplayNameResourceID` und `DisplayNamePackageGuid` müssen angegeben werden. Wenn all angegeben wird, wird das `DisplayNameResourceID` -Paar und das- `DisplayNamePackageGuid` Paar verwendet.

## <a name="disable-the-visual-studio-gallery-using-a-pkgdef-file"></a>Deaktivieren der Visual Studio Gallery mithilfe einer pkgdef-Datei
 Sie können einen Katalog in einer *pkgdef* -Datei deaktivieren. Der folgende Eintrag deaktiviert die Visual Studio Gallery:

```
[$RootKey$\ExtensionManager\Repositories\{0F45E408-7995-4375-9485-86B8DB553DC9}]
"Disabled"=dword:00000001

```

 Der folgende Eintrag deaktiviert die Samples Gallery:

```
[$RootKey$\ExtensionManager\Repositories\{AEB9CB40-D8E6-4615-B52C-27E307F8506C}]
"Disabled"=dword:00000001

```

## <a name="see-also"></a>Weitere Informationen
- [Private Kataloge](../extensibility/private-galleries.md)
