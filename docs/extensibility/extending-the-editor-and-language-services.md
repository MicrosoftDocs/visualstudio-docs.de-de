---
title: Erweitern des Editors und der Sprachdienste | Microsoft-Dokumentation
description: Sie können einem Editor Sprachdienst Funktionen hinzufügen und Features des Visual Studio Code-Editors erweitern. Erfahren Sie mehr über die Managed Extensibility Framework.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new -
ms.assetid: 8d04f8db-eda7-4b3e-b6eb-c06df104502a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 49d4b76fe7feadb4458ef68acb351b81c6fa494c
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2020
ms.locfileid: "96995745"
---
# <a name="extend-the-editor-and-language-services"></a>Erweitern des Editors und der Sprachdienste
Sie können einem eigenen Editor Sprachdienst Funktionen (z. b. IntelliSense) hinzufügen und die meisten Funktionen des Visual Studio Code-Editors erweitern.  Eine vollständige Liste der Erweiterungen, die Sie erweitern können, finden Sie unter [Sprachdienst-und Editor-Erweiterungs Punkte](../extensibility/language-service-and-editor-extension-points.md).

 Die meisten Editor-Features werden mithilfe des Managed Extensibility Framework (MEF) erweitert. Wenn z. b. das Editor-Feature, das Sie erweitern möchten, Syntax Farben ist, können Sie einen MEF- *Komponenten Teil* schreiben, der die Klassifizierungen definiert, für die Sie unterschiedliche Farben und deren Handhabung wünschen. Der Editor unterstützt auch mehrere Erweiterungen desselben Features.

 Die Präsentationsebene des Editors basiert auf Windows Presentation Framework (WPF). WPF stellt eine Grafikbibliothek für die flexible Textformatierung bereit und bietet auch Visualisierungen wie Grafiken und Animationen.

 Das Visual Studio SDK bietet Adapter, die als *Shims* bezeichnet werden, um VSPackages zu unterstützen, die für frühere Versionen geschrieben wurden. Wenn Sie jedoch über ein vorhandenes VSPackage verfügen, empfiehlt es sich, es auf die neue Technologie zu aktualisieren, um eine bessere Leistung und Zuverlässigkeit zu erzielen.

## <a name="related-topics"></a>Verwandte Themen

|Titel|BESCHREIBUNG|
|-----------|-----------------|
|[Einstieg in die Erweiterungen für Sprachdienste und Editoren](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|Erläutert, wie eine Erweiterung für den Editor erstellt wird.|
|[Innerhalb des Editors](../extensibility/inside-the-editor.md)|Beschreibt die allgemeine Struktur des Editors und listet einige Funktionen auf.|
|[Im Editor Managed Extensibility Framework](../extensibility/managed-extensibility-framework-in-the-editor.md)|Erläutert, wie die Managed Extensibility Framework (MEF) mit dem-Editor verwendet wird.|
|[Sprachdienst-und Editor-Erweiterungs Punkte](../extensibility/language-service-and-editor-extension-points.md)|Listet die Erweiterungs Punkte des Editors auf. Erweiterungs Punkte stellen die Editor-Funktionen dar, die erweitert werden können.|
|[Exemplarische Vorgehensweise: Erstellen eines Ansichts Zusatz Elements, von Befehlen und Einstellungen (Spalten Handbücher)](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|Führt Sie durch und erläutert die Entwicklung eines Ansichts Zusatz Elements, das Spalten Führungslinien zeichnet, damit Sie Code in einer bestimmten Anzeigebreite behalten können.  Außerdem werden Lese-und Schreib Einstellungen sowie das Deklarieren und Implementieren von Befehlen angezeigt, die Sie über das Befehlsfenster aufrufen können.|
|[Editor Importe](../extensibility/editor-imports.md)|Listet die Dienste auf, die eine Erweiterung importieren kann.|
|[Anpassen von Legacy Code an den Editor](/previous-versions/visualstudio/visual-studio-2015/extensibility/adapting-legacy-code-to-the-editor?preserve-view=true&view=vs-2015)|Erläutert verschiedene Möglichkeiten zum Anpassen von Legacy Code (Pre-Visual Studio 2010), um den Editor zu erweitern.|
|[Migrieren eines Legacy sprach Dienstanbieter](../extensibility/internals/migrating-a-legacy-language-service.md)|Erläutert, wie ein VSPackage-basierter Sprachdienst migriert wird.|
|[Exemplarische Vorgehensweise: Verknüpfen eines Inhaltstyps mit einer Dateinamenerweiterung](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|Zeigt, wie Sie einen Inhaltstyp mit einer Dateinamenerweiterung verknüpfen.|
|[Exemplarische Vorgehensweise: Erstellen eines Rand Symbols](../extensibility/walkthrough-creating-a-margin-glyph.md)|Zeigt, wie ein Symbol zu einem Rand hinzugefügt wird.|
|[Exemplarische Vorgehensweise: Markieren von Text](../extensibility/walkthrough-highlighting-text.md)|Zeigt, wie *Tags* zum Markieren von Text verwendet werden.|
|[Exemplarische Vorgehensweise: Hinzufügen](../extensibility/walkthrough-outlining.md)|Zeigt, wie Gliederung für bestimmte Arten von geschweiften Klammern hinzugefügt wird.|
|[Exemplarische Vorgehensweise: anzeigen passender geschweifter Klammern](../extensibility/walkthrough-displaying-matching-braces.md)|Zeigt, wie passende geschweifte Klammern hervorgehoben werden.|
|[Exemplarische Vorgehensweise: Anzeigen von Quick Infos](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|Zeigt, wie QuickInfo-Popups angezeigt werden, die Code Elemente beschreiben, wie z. b. Eigenschaften, Methoden und Ereignisse.|
|[Exemplarische Vorgehensweise: Anzeigen der Signatur Hilfe](../extensibility/walkthrough-displaying-signature-help.md)|Zeigt, wie Popups angezeigt werden, die Informationen über die Anzahl und Typen von Parametern in einer Signatur enthalten.|
|[Exemplarische Vorgehensweise: Anzeigen von Anweisungsvervollständigung](../extensibility/walkthrough-displaying-statement-completion.md)|Zeigt, wie die Anweisungs Vervollständigung implementiert wird.|
|[Exemplarische Vorgehensweise: Implementieren von Code Ausschnitten](../extensibility/walkthrough-implementing-code-snippets.md)|Zeigt, wie die Code Ausschnitt Erweiterung implementiert wird.|
|[Exemplarische Vorgehensweise: Anzeigen von Glühbirnen Vorschlägen](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|Zeigt, wie Glühbirnen für Code Vorschläge angezeigt werden.|
|[Exemplarische Vorgehensweise: Verwenden eines Shellbefehls mit einer Editor-Erweiterung](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|Zeigt, wie einem Menübefehl in einem VSPackage eine MEF-Komponente zugeordnet wird.|
|[Exemplarische Vorgehensweise: Verwenden einer Tastenkombination mit einer Editor-Erweiterung](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|Zeigt, wie eine Menü Verknüpfung in einem VSPackage mit einer MEF-Komponente verknüpft wird.|
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|Stellt Informationen zum Managed Extensibility Framework (MEF) bereit.|
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|Stellt Informationen zum Windows Presentation Foundation (WPF) bereit.|

## <a name="reference"></a>Verweis
 Der Visual Studio-Editor enthält die folgenden Namespaces.

 <xref:Microsoft.VisualStudio.Language.Intellisense>

 <xref:Microsoft.VisualStudio.Language.StandardClassification>

 <xref:Microsoft.VisualStudio.Editor>

 <xref:Microsoft.VisualStudio.Text>

 <xref:Microsoft.VisualStudio.Text.Adornments>

 <xref:Microsoft.VisualStudio.Text.Classification>

 <xref:Microsoft.VisualStudio.Text.Differencing>

 <xref:Microsoft.VisualStudio.Text.Document>

 <xref:Microsoft.VisualStudio.Text.Editor>

 <xref:Microsoft.VisualStudio.Text.Editor.OptionsExtensionMethods>

 <xref:Microsoft.VisualStudio.Text.Formatting>

 <xref:Microsoft.VisualStudio.Text.IncrementalSearch>

 <xref:Microsoft.VisualStudio.Text.Operations>

 <xref:Microsoft.VisualStudio.Text.Outlining>

 <xref:Microsoft.VisualStudio.Text.Projection>

 <xref:Microsoft.VisualStudio.Text.Tagging>

 <xref:Microsoft.VisualStudio.Utilities>