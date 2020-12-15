---
title: Assistenten | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie den Assistenten unter den verfügbaren Assistenten und Vorlagen in Visual Studio auflisten, und informieren Sie sich über die Anforderungen, die der Assistent in der IDE erfüllen muss.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], providing wizard support
ms.assetid: 59d9a77f-ee80-474b-a14f-90f477ab717b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f367723a3c819635f2d7cf20ed812a36cda12830
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97487750"
---
# <a name="wizards"></a>Assistenten
Nachdem Sie einen Assistenten erstellt haben, möchten Sie ihn in der Regel der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) hinzufügen, damit er von anderen Benutzern verwendet werden kann. Der hinzugefügte Assistent wird dann in den Dialogfeldern **Neues Projekt hinzufügen** oder **Neues Element hinzufügen** angezeigt. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf eine geöffnete Projekt Mappe, zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf **Neues Projekt** oder **Neues Element**, um die Dialogfelder **Neues Projekt hinzufügen** oder **Neues Element hinzufügen** anzuzeigen.

 Assistenten können in implementiert werden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , um Benutzern die Auswahl aus einer Strukturansicht verfügbarer Werte zu ermöglichen, wenn Sie das Dialogfeld **Neues Projekt hinzufügen** oder das Dialogfeld **Neues Element hinzufügen** öffnen, oder wenn Sie mit der rechten Maustaste auf ein Element in **Projektmappen-Explorer** klicken.

 In Ihrem Assistenten können Sie die Option zum Lokalisieren des Namens eines neuen Projekts oder von "Ites" bereitstellen, und Sie können das Symbol ermitteln, das Benutzern angezeigt wird, wenn Sie den Assistenten auswählen. Sie können auch die Reihenfolge steuern, in der neue Elemente relativ zu anderen verfügbaren Elementen angezeigt werden. Elemente müssen nicht alphabetisch angeordnet werden.

 Sie können auch einen Assistenten bereitstellen, der je nach benutzerdefinierten Parametern, die beim Öffnen an den Assistenten übergeben werden, unterschiedlich gestartet werden.

 In den Themen in diesem Abschnitt werden die Dateien erläutert, die Sie implementieren, um die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Dialogfelder **Neues Projekt hinzufügen** und **Neues Element hinzufügen** zu veranlassen, den Assistenten unter den verfügbaren Assistenten und Vorlagen aufzulisten und die Anforderungen zu erfüllen, die der Assistent erfüllen muss, damit er in der IDE ordnungsgemäß funktioniert.

## <a name="in-this-section"></a>In diesem Abschnitt
- [Dateien zur Beschreibung des Vorlagenverzeichnisses (VSDIR)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)

 Bietet einen Überblick über die Vorlagen Verzeichnis Beschreibungsdateien und erläutert, wie Sie in der IDE funktionieren, um Ordner, Assistenten. VSZ-Dateien und Vorlagen Dateien anzuzeigen, die einem Projekt in den Dialogfeldern zugeordnet sind.

- [Assistentendatei (VSZ)](../../extensibility/internals/wizard-dot-vsz-file.md)

 Erläutert, wie die IDE die Assistenten startet und die drei Teile der VSZ-Datei auflistet.

- [Assistentenschnittstelle (IDTWizard)](../../extensibility/internals/wizard-interface-idtwizard.md)

 Beschreibt die `IDTWizard` Schnittstelle, die Assistenten implementieren müssen, damit Sie in der IDE funktioniert.

- [Kontextparameter](../../extensibility/internals/context-parameters.md)

 Erläutert, wie Assistenten implementiert werden und was geschieht, wenn die IDE Kontext Parameter an die-Implementierung übergibt.

- [Benutzerdefinierte Parameter](../../extensibility/internals/custom-parameters.md)

 Erläutert die Verwendung von benutzerdefinierten Parametern zum Steuern des Vorgangs des Assistenten, nachdem der Assistent gestartet wurde.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Projekttypen](../../extensibility/internals/project-types.md)

 Enthält Links zu weiteren Themen, in denen Informationen zum Entwerfen neuer Projekttypen angeboten werden.

- [Erweitern von Projekten](../../extensibility/extending-projects.md)

 Beschreibt, wie Codedateien und Ressourcendateien mithilfe von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]-Projekten und -Projektmappen organisiert werden und wie die Quellcodeverwaltung implementiert wird.
