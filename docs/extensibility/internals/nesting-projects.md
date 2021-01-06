---
title: Schachteln von Projekten | Microsoft-Dokumentation
description: Erfahren Sie mehr über das Schachteln von Projekten, mit denen Anwendungsentwickler, die Ihr VSPackage verwenden, ähnliche Projekttypen in Visual Studio gruppieren können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project nesting
- nested projects
- projects [Visual Studio SDK], child projects
- projects [Visual Studio SDK], nesting
ms.assetid: 12cce037-9840-4761-845e-5abd5fb317b0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 464538d7f7be68737715cb6fd10fda4017a5556a
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97876661"
---
# <a name="nesting-projects"></a>Schachteln von Projekten
Unternehmens Anwendungsentwickler, die ihr vs-Paket verwenden, können ähnliche Projekttypen in mithilfe der Projekt Schachtelung bequem gruppieren [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .  Beispielsweise verwendet das Enterprise-Vorlagen Projekt für die Gruppierung von Projekten in Kategorien. Geschäfts Fassaden Projekte, Webbenutzer Oberflächen Projekte usw. werden in einer Kategorie zusammengefasst.

 In diesem Szenario gibt es keine Beschränkung für die Anzahl von Projekten, die der Entwickler unter jedem übergeordneten Projekt Schachteln kann, obwohl der Entwicklerprogramm gesteuert Beschränkungen bereitstellen kann. Diese Art von Gruppierung kann auch rekursiv gemacht werden. in diesem Fall können die Projekte desselben Typs wie ein untergeordnetes Projekt unter dem untergeordneten Projekt untergeordnet werden, um ein untergeordnetes Element des untergeordneten Elements zu werden, bei dem es sich um ein untergeordnetes Element des übergeordneten Projekts handelt.

 Die Projekt Schachtelung ist kein intrinsischer Bestandteil von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Sie müssen den Code schreiben, um Schachtelung und untergeordnete Projekt Schachtelungen in untergeordneten Projekten zu aktivieren. Das übergeordnete Projekt ist ein spezielles VSPackage oder Projekttyp, der mit einer eigenen GUID erstellt und registriert wird, die den Code enthält, der zum Implementieren der Projekt Schachtelung erforderlich ist.

 Ein Beispiel zum Schachteln von Projekten finden Sie unter Gewusst [wie: Implementieren](../../extensibility/internals/how-to-implement-nested-projects.md)von geschachtelten Projekten.

## <a name="nested-projects-example"></a>Beispiel für ein Beispiel für ein Beispiel
 ![Projekt Mappe für Projektmappen](../../extensibility/internals/media/vsnestedprojects.gif "vsnestedprojects") Beispiel für ein Beispiel für ein Beispiel

## <a name="see-also"></a>Weitere Informationen
- [Überlegungen für das Entladen und Neuladen von geschachtelten Projekten](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)
- [Assistentenunterstützung für geschachtelte Projekte](../../extensibility/internals/wizard-support-for-nested-projects.md)
- [Registrieren von Projekt- und Elementvorlagen](../../extensibility/internals/registering-project-and-item-templates.md)
- [Implementieren der Befehlsbehandlung für geschachtelte Projekte](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)
- [Filtern des AddItem-Dialogfelds für geschachtelte Projekte](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)
- [Prüfliste: Erstellen neuer Projekttypen](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Kontextparameter](../../extensibility/internals/context-parameters.md)
- [Assistentendatei (VSZ)](../../extensibility/internals/wizard-dot-vsz-file.md)
