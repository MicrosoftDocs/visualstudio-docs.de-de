---
title: Registrieren von Interop-Assembly-Befehls Handlern | Microsoft-Dokumentation
description: Erfahren Sie mehr über den grundlegenden Befehls Vertrag von allen VSPackages, die Befehle mithilfe von Interop-Assemblys implementieren.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, command handlers
- command handling with interop assemblies, registering
ms.assetid: 303cd399-e29d-4ea1-8abe-5e0b59c12a0c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 67c01aa9ecb3661235670866d92b29d7d8eef543
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837277"
---
# <a name="registering-interop-assembly-command-handlers"></a>Registrieren der Befehlshandler von Interop-Assemblys
Ein VSPackage muss bei registriert werden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , damit die integrierte Entwicklungsumgebung (IDE) die Befehle ordnungsgemäß weiterleitet.

 Die Registrierung kann entweder per manueller Bearbeitung oder mithilfe einer Registrierungsstelle (RGS-Datei) aktualisiert werden. Weitere Informationen finden Sie unter [Creating Registrar Scripts](/cpp/atl/creating-registrar-scripts).

 Das Managed Package Framework (MPF) stellt diese Funktionalität durch die- <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> Klasse bereit.

- [Referenz Ressourcen des Befehls Tabellen Formats](/previous-versions/bb164647(v=vs.100)) befinden sich in nicht verwalteten Satelliten-UI-DLLs.

## <a name="command-handler-registration-of-a-vspackage"></a>Befehls Handler-Registrierung eines VSPackages
 Ein VSPackage, das als Handler für Benutzeroberflächen basierte Befehle fungiert, erfordert einen Registrierungs Eintrag, der nach dem VSPackage benannt ist `GUID` . Dieser Registrierungs Eintrag gibt den Speicherort der UI-Ressourcen Datei des VSPackages und die Menü Ressource in dieser Datei an. Der Registrierungs Eintrag selbst befindet sich unter HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\ *\<Version>* \menüs, wobei *\<Version>* die Version von ist [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , z. b. 9,0.

> [!NOTE]
> Der Stammpfad von HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\ *\<Version>* kann mit einem alternativen Stamm überschrieben werden, wenn die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Shell initialisiert wird. Weitere Informationen zum Stammpfad finden Sie unter [Installieren von VSPackages mit Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md).

### <a name="the-ctmenu-resource-registry-entry"></a>Der ctmenu-Ressourcen Registrierungs Eintrag
 Die Struktur des Registrierungs Eintrags lautet:

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\<Version>\
  Menus\
    <GUID> = <Resource Information>
```

 \<*GUID*> der `GUID` des VSPackage im Format {xxxxxx-xxxx-xxxx-xxxx-xxxxxxxxx}.

 *\<Resource Information>* besteht aus drei durch Kommas getrennten Elementen. Diese Elemente sind in der angegebenen Reihenfolge:

 \<*Path to Resource DLL*>, \<*Menu Resource ID*>, \<*Menu Version*>

 In der folgenden Tabelle werden die Felder von beschrieben \<*Resource Information*> .

| Element | Beschreibung |
|---------------------------| - |
| \<*Path to Resource DLL*> | Dies ist der vollständige Pfad zur Ressourcen-DLL, die die Menü Ressource enthält, oder diese ist leer. Dies gibt an, dass die Ressourcen-DLL des VSPackages verwendet werden soll (wie im Paket Unterschlüssel angegeben, in dem das VSPackage selbst registriert ist).<br /><br /> Es ist üblich, dieses Feld leer zu lassen. |
| \<*Menu Resource ID*> | Dies ist die Ressourcen-ID der `CTMENU` Ressource, die alle Benutzeroberflächen Elemente für das VSPackage enthält, wie aus einer [vsct](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) -Datei kompiliert. |
| \<*Menu Version*> | Dies ist eine Zahl, die als Version für die `CTMENU` Ressource verwendet wird. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] verwendet diesen Wert, um zu bestimmen, ob der Inhalt der `CTMENU` Ressource mit dem Cache aller Ressourcen neu zusammengeführt werden muss `CTMENU` . Eine erneute Zusammenführung wird durch Ausführen des Befehls "Debug-Setup" ausgelöst.<br /><br /> Dieser Wert sollte zunächst auf 1 festgelegt und nach jeder Änderung der `CTMENU` Ressource und vor dem erneuten zusammenführen erhöht werden. |

### <a name="example"></a>Beispiel
 Im folgenden finden Sie ein Beispiel für eine Reihe von Ressourcen Einträgen:

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\9.0Exp\
  Menus\
    {019971D6-4685-11D2-B48A-0000F87572EB} = ,1, 10
    {1b027a40-8f43-11d0-8d11-00a0c91bc942} = , 10211, 3
```

## <a name="see-also"></a>Weitere Informationen
- [Hinzufügen von Benutzeroberflächenelementen mit VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Befehle und Menüs, die Interop-Assemblys verwenden](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)