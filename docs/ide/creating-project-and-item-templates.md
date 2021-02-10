---
title: Vorlagen für Projekte und Dateien
description: Erfahren Sie mehr darüber, wie Projekt- und Elementvorlagen wiederverwendbare Stubs bereitstellen, die Benutzen grundlegenden Code sowie eine grundlegende Struktur bieten.
ms.custom: SEO-VS-2020
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- templates [Visual Studio], project
- templates [Visual Studio], item
- item templates [Visual Studio]
- project templates [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: e5a3a555a9c0674c70e93ec557416c05d282fbcf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956814"
---
# <a name="project-and-item-templates"></a>Projekt- und Elementvorlagen

Projekt- und Elementvorlagen stellen wiederverwendbare Stubs bereit, die Benutzern grundlegenden Code sowie eine grundlegende Struktur vermitteln, die sie an ihre jeweiligen Zwecke anpassen können.

## <a name="visual-studio-templates"></a>Visual Studio-Vorlagen

Zusammen mit Visual Studio wird eine Reihe vordefinierter Projekt- und Elementvorlagen installiert. Diese Vorlagen, wie etwa die Vorlagen **ASP.NET-Webanwendung** und **Klassenbibliothek**, stehen beim Erstellen eines neuen Projekts zur Wahl. Elementvorlagen, wie etwa Codedateien, HTML-Seiten und Stylesheets, werden im Fenster **Neues Element hinzufügen** angezeigt.

Diese Vorlagen stellen einen Ausgangspunkt bereit, von dem aus Benutzer Projekte erstellen oder vorhandene Projekte erweitern können. Projektvorlagen stellen die Dateien bereit, die für einen bestimmten Projekttyp erforderlich sind; sie umfassen standardmäßige Assemblyverweise und legen standardmäßige Projekteigenschaften und Compileroptionen fest. Elementvorlagen können eine unterschiedliche Komplexität aufweisen. Diese reicht von einer einfachen leeren Datei mit einer bestimmten Erweiterung bis hin zu mehreren Quellcodedateien mit Stubcode, Dateien mit Designer-Informationen und eingebetteten Ressourcen.

Sie können die installierten Vorlagen verwenden, eigene benutzerdefinierte Vorlagen verfassen oder von der Community erstellte Vorlagen herunterladen und verwenden. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von Projektvorlagen](../ide/how-to-create-project-templates.md) und [Vorgehensweise: Erstellen von Elementvorlagen](../ide/how-to-create-item-templates.md).

## <a name="contents-of-a-template"></a>Inhalte einer Vorlage

Alle Projekt- und Elementvorlagen, unabhängig davon, ob diese zusammen mit Visual Studio installiert oder von Ihnen erstellt wurden, funktionieren nach demselben Prinzip und umfassen ähnliche Inhalte. Alle Vorlagen enthalten die folgenden Elemente:

- Die Dateien, die bei Verwendung der Vorlage erstellt werden sollen. In diesen Dateien sind unter anderem Quellcodedateien, eingebettete Ressourcen, Projektdateien enthalten.

::: moniker range="vs-2017"

- Eine Datei *.vstemplate*, die die Metadaten enthält, die zum Erstellen eines Projekts oder eines Elements aus der Vorlage und zum Anzeigen der Vorlage in den Fenstern **Neues Projekt** und **Neues Element hinzufügen** benötigt werden.

::: moniker-end

::: moniker range=">=vs-2019"

- Eine Datei *.vstemplate*, die die Metadaten enthält, die zum Erstellen eines Projekts oder Elements aus der Vorlage und zum Anzeigen der Vorlage auf der Seite **Neues Projekt erstellen** oder im Dialogfeld **Neues Element hinzufügen** benötigt werden.

::: moniker-end

   Weitere Informationen zu *VSTEMPLATE*-Dateien finden Sie unter [Vorlagentags](template-tags.md) und [Vorlagenparameter](../ide/template-parameters.md).

Wenn diese Dateien in eine *ZIP-Datei* komprimiert sind und sich im richtigen Ordner befinden, werden sie automatisch von Visual Studio an folgenden Orten angezeigt:

::: moniker range="vs-2017"

- Die Projektvorlagen werden im Fenster **Neues Projekt** angezeigt.

::: moniker-end

::: moniker range=">=vs-2019"

- Projektvorlagen werden auf der Seite **Neues Projekt erstellen** angezeigt.

::: moniker-end

- Elementvorlagen werden im Fenster **Neues Element hinzufügen** angezeigt.

Weitere Informationen zu Vorlagenordnern finden Sie unter [Vorgehensweise: Suchen und Organisieren von Vorlagen](../ide/how-to-locate-and-organize-project-and-item-templates.md).

## <a name="see-also"></a>Weitere Informationen

- [How to: Erstellen von Projektvorlagen](../ide/how-to-create-project-templates.md)
- [How to: Erstellen von Elementvorlagen](../ide/how-to-create-item-templates.md)
- [Vorlagentags](template-tags.md)
- [Vorlagenparameter](../ide/template-parameters.md)
- [Anpassen von Projekt- und Elementvorlagen](../ide/customizing-project-and-item-templates.md)
- [NuGet-Pakete in Visual Studio-Vorlagen](/nuget/visual-studio-extensibility/visual-studio-templates)
