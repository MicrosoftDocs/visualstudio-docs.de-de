---
title: IDE-Defined Befehle, Menüs und Gruppen | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Menüs, Befehle und Befehls Gruppen, die in der integrierten Entwicklungsumgebung (IDE) von Visual Studio definiert sind.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, environment-defined
- .vsct files, environment-defined constants
- command groups, environment-defined
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e46832803008ea65d0f7ec4f2723a615ba496b94
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840079"
---
# <a name="ide-defined-commands-menus-and-groups"></a>IDE-definierte Befehle, Menüs und Gruppen
Viele Menüs, Befehle und Befehls Gruppen sind bereits für die Verwendung durch die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE definiert. Diese Befehle sind auch für ihre Verwendung verfügbar, wenn Sie erweitern [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="finding-environment-defined-commands"></a>Suchen nach Environment-Defined-Befehlen
 Die Umgebungs Befehle sind in einem Satz von vier vsct-Dateien definiert:

- Sharedcmddef. vsct

- Sharedcmdplace. vsct

- Shellcmddef. vsct

- Shellcmdplace. vsct

  Diese Dateien befinden sich unter *\<Visual Studio SDK installation path>* \visualstudiointegration\common\inc \\ . Diese Dateien enthalten die Definitionen und GUIDs der Menüs und Gruppen, die Sie in der Befehls Tabellen Konfigurationsdatei (vsct-Datei) Ihres VSPackage als Container für Ihre eigenen Menüs, Gruppen und Befehle verwenden können.

## <a name="in-this-section"></a>In diesem Abschnitt
- [GUIDs und IDs der Visual Studio-Menüs](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)

 Gibt die GUID-und ID-Werte der Menüs in der Visual Studio-Menüleiste und der Gruppen an, die Sie enthalten.

- [GUIDs und IDs der Visual Studio-Symbolleisten](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)

 Gibt die GUID-und ID-Werte von Symbolleisten in der Visual Studio-IDE und der darin enthaltenen Gruppen an.

- [GUIDs und IDs der Visual Studio-Befehle](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)

 Gibt die GUID-und ID-Werte von Befehlen an, die von der Visual Studio-IDE definiert werden.

## <a name="see-also"></a>Weitere Informationen
- [VSCT-Dateien (Visual Studio Command Table)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [IDE-definierte Befehle zum Erweitern von Projektsystemen](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)
- [Hinzufügen von Benutzeroberflächenelementen mit VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
