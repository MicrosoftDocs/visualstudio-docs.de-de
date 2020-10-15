---
title: Einstieg in die Entwicklung von Visual Studio-Erweiterungen | Microsoft-Dokumentation
ms.date: 09/18/2017
ms.topic: conceptual
helpviewer_keywords:
- getting started, Visual Studio integration
- Visual Studio, integration
ms.assetid: 8fe5e2ab-a424-4173-9d39-dd082c4d58d0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 812c5b2366e40226011a15acfc1cae2327e4b897
ms.sourcegitcommit: 9c57730000d5ced37d3887f3928b17076f49d0f7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2020
ms.locfileid: "92099387"
---
# <a name="starting-to-develop-visual-studio-extensions"></a>Beginnen mit der Entwicklung von Visual Studio-Erweiterungen

Wenn Sie noch nie eine Visual Studio-Erweiterung geschrieben haben, haben Sie wahrscheinlich einige Fragen. Wir haben hier einige der gängigsten aufgelistet. Wenn Ihnen die gesuchten Informationen nicht angezeigt werden, verwenden Sie die Feedback Schaltflächen (**ist diese Seite hilfreich?** in der oberen rechten Ecke des Bildschirms), um zu Fragen, was Sie möchten.

> [!NOTE]
> Dieser Artikel gilt für Visual Studio unter Windows. Visual Studio für Mac finden Sie unter [Erweitern von Visual Studio für Mac](/visualstudio/mac/extending-visual-studio-mac). Visual Studio Code finden Sie unter [Visual Studio Code Extension-API](https://code.visualstudio.com/api).

## <a name="what-software-do-i-need-to-develop-visual-studio-extensions"></a>Welche Software benötige ich zum Entwickeln von Visual Studio-Erweiterungen?

Sie müssen zusätzlich zu Visual Studio das Visual Studio SDK installieren, um Visual Studio-Erweiterungen zu entwickeln. Sie können das Visual Studio SDK als Teil des regulären Setups installieren, oder Sie können es später installieren. Weitere Informationen zum Installieren des Visual Studio SDK finden Sie unter [Installieren des Visual Studio](../extensibility/installing-the-visual-studio-sdk.md)SDK.

## <a name="what-kinds-of-things-can-i-do-with-visual-studio-extensions"></a>Welche Arten von Dingen kann ich mit Visual Studio-Erweiterungen tun?

Der Himmel ist das Limit bei der Imaginierung verschiedener Visual Studio-Erweiterungen. Natürlich haben die meisten Erweiterungen etwas, was mit dem Schreiben von Code zu tun ist, dies muss jedoch nicht der Fall sein. Im folgenden finden Sie einige Beispiele für die Erweiterungen, die Sie erstellen können:

- Unterstützung für Sprachen, die nicht in Visual Studio enthalten sind, mit Syntax Farben, IntelliSense und Compilerunterstützung und Debugunterstützung

- Produktivitäts Tools zur Erweiterung der zentralen IDE-Umgebung mit zusätzlichen Vorlagen, Code Umgestaltung, neuen Dialogfeldern oder Tool Fenstern

- Domänenspezifische Designer für Szenarien wie Daten Entwurf oder cloudunterstützung

Beispiele für Erweiterungen finden Sie in der [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs). Viele Erweiterungen sind Open Source-Erweiterungen, und der Marketplace enthält Links zu Ihrem GitHub-Repository.

## <a name="which-visual-studio-features-can-i-extend"></a>Welche Features von Visual Studio können erweitert werden?

Theoretisch können Sie fast jeden Teil von Visual Studio erweitern: Menüs, Symbolleisten, Befehle, Fenster, Projektmappen, Projekte, Editoren usw.

In der Praxis haben wir festgestellt, dass die Funktionen, die die meisten Benutzer erweitern möchten, Befehle, Menüs und Symbolleisten, Fenster, IntelliSense und Projekte sind. Hier finden Sie Links zu den relevanten Abschnitten:

- [Erweitern von Menüs und Befehlen](../extensibility/extending-menus-and-commands.md): Hinzufügen eigener Elemente zu Visual Studio-Menüs und-Symbolleisten. Sie können Sie verwenden, um neue Visual Studio-Funktionen oder eigene externe Hilfsanwendungen zu starten. Sie können auch benutzerdefinierte Tastenkombinationen für die Menü Elemente bereitstellen.

- [Erweitern und Anpassen von Tool Fenstern](../extensibility/extending-and-customizing-tool-windows.md): Erweitern Sie vorhandene Tool Fenster, oder erstellen Sie eigene Tool Fenster. Beispielsweise können Sie den **Eigenschaften**neue Eigenschaften hinzufügen, oder Sie können ein neues Tool Fenster erstellen, um zusätzliche Funktionen hinzuzufügen.

- [Editor-und Sprachdienst Erweiterungen](../extensibility/editor-and-language-service-extensions.md): Fügen Sie Ihren eigenen Anpassungen zu IntelliSense für Visual Studio-Sprachen hinzu, oder erstellen Sie Unterstützung für neue Programmiersprachen. Sie können neue-Anweisungs Vervollständigungen, Vorschläge und neue Quick Infos erstellen. Mit Glühbirnen können Sie refactoringvorschläge und Code Korrekturen hinzufügen, um neue Programmiersprachen zu unterstützen.

- [Erweitern von Projekten](../extensibility/extending-projects.md)

- [Erweitern von Benutzereinstellungen und Optionen](../extensibility/extending-user-settings-and-options.md)

- [Erweitern von Eigenschaften und des Eigenschaftenfensters](../extensibility/extending-properties-and-the-property-window.md)

- [Erweitern anderer Teile von Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)

- [Visual Studio Isolated Shell](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)

## <a name="what-project-templates-are-provided-by-the-vssdk"></a><a name="BKMK_ProjectTemplate"></a> Welche Projektvorlagen werden vom VSSDK bereitgestellt?
 Die zwei Haupttypen von Erweiterungen sind VSPackages und MEF-Erweiterungen. Im Allgemeinen werden VSPackage-Erweiterungen für Erweiterungen verwendet, die Befehle, Tool Fenster und Projekte verwenden oder erweitern. MEF-Erweiterungen werden zum Erweitern oder Anpassen des Visual Studio-Editors verwendet.

 Für Visual c#-und Visual Basic Erweiterungen bietet das VSSDK eine leere VSIX-Projektvorlage, die Sie in Verbindung mit den neuen Element Vorlagen, die Menübefehle, Tool Fenster und Editor Erweiterungen erstellen, verwenden können. Sie können diese Vorlage auch verwenden, um Projektvorlagen, Code Ausschnitte und andere Artefakte für die Verteilung an andere Benutzer zu verpacken.

 Für C++ stellt der VSPackage-Assistent den Code zum Hinzufügen von Menübefehlen, Tool Fenstern und benutzerdefinierten Editoren bereit.

 Die Vorlage für isolierte Shell wird verwendet, um eine Erweiterung in einer Version der Visual Studio-Shell zu verpacken, die Sie als eigenständig verteilen und verteilen können. In den folgenden Themen erfahren Sie, wie Sie mit den einzelnen Erweiterungs Arten beginnen:

- Menübefehle: [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md)

- Tool Fenster: [Erstellen einer Erweiterung mit einem Tool Fenster](../extensibility/creating-an-extension-with-a-tool-window.md)

- Editor-Erweiterungen: [Erstellen einer Erweiterung mit einer Editor-Element Vorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md)

- Grundlegende VSPackages: [Erstellen einer Erweiterung mit einem VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)

- VSIX-Projektvorlage: [Einstieg in die VSIX-Projektvorlage](../extensibility/getting-started-with-the-vsix-project-template.md)

## <a name="how-do-i-get-my-extension-to-look-like-visual-studio"></a>Gewusst wie meine Erweiterung wie in Visual Studio aussehen?
 Hier erhalten Sie gute Tipps zum Entwerfen der Benutzeroberfläche für Ihre Erweiterung in den [Richtlinien zur Benutzeroberfläche von Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).

## <a name="where-can-i-find-examples-of-vssdk-code"></a>Wo finde ich Beispiele für VSSDK-Code?
 Jeder der Links im vorherigen Abschnitt enthält schrittweise exemplarische Vorgehensweisen, die veranschaulichen, wie bestimmte Funktionen implementiert werden. Open-Source-VSSDK-Beispiele finden Sie auch auf GitHub unter [Visual Studio-Beispiele](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

## <a name="how-can-i-distribute-my-extension"></a>Wie kann ich meine Erweiterung verteilen?
 Sie können Ihre Erweiterung auf einem anderen Computer installieren oder Sie als vsix-Datei an Ihre Freunde senden, indem Sie darauf doppelklicken. Weitere Informationen zu VSIX-Paketen finden Sie unter " [Versand von Visual Studio-Erweiterungen](../extensibility/shipping-visual-studio-extensions.md)".

 Sie können Ihre Erweiterung auch auf dem Visual Studio Marketplace veröffentlichen, wodurch Sie für eine große Anzahl von Visual Studio-Kunden sichtbar wird. Ein Beispiel für das Packen einer Erweiterung in den Marketplace finden Sie unter Exemplarische Vorgehensweise [: Veröffentlichen einer Visual Studio-Erweiterung](../extensibility/walkthrough-publishing-a-visual-studio-extension.md). Weitere Informationen zu den Voraussetzungen für die Veröffentlichung im Marketplace finden Sie unter [Produkte und Erweiterungen für Visual Studio](/azure/devops/extend/overview?view=vsts&preserve-view=true).

## <a name="see-also"></a>Weitere Informationen

- [Extending Visual Studio for Mac (Erweitern von Visual Studio für Mac)](/visualstudio/mac/extending-visual-studio-mac)
- [Erweitern von Visual Studio Code](https://code.visualstudio.com/api)