---
title: Arbeitsbereiche und Sprachdienste in Visual Studio | Microsoft-Dokumentation
description: Erfahren Sie, wie Sprachdienste offene Ordner Benutzern die gleichen Rich-Language-Funktionen bereitstellen können, die Sie bei der Arbeit mit Projektmappen und Projekten verwenden.
ms.custom: SEO-VS-2020
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 815cfb9e17fed38b519719010acd997f7fdc5242
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877038"
---
# <a name="workspaces-and-language-services"></a>Arbeitsbereiche und Sprachdienste

Sprachdienste können den Benutzern offener Ordner die gleichen Rich-Language-Funktionen bereitstellen, die bei der Arbeit mit Projekt [Mappen](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) und Projekten verwendet werden. Ein Sprachdienst kann basierend auf der Dateierweiterung oder dem Inhalt eines geöffneten Dokuments selbst aktiviert werden, obwohl der Sprachdienst "lose Datei" auf Syntax Hervorhebung beschränkt ist. Zusätzliche Informationen sind erforderlich, um beim Bearbeiten/überprüfen von Quellcode ein umfasseneres Verhalten zu bieten. Jeder Sprachdienst verfügt über eine eigene API für die Initialisierung mit diesen zusätzlichen kontextbezogenen Daten für ein Dokument. Dies wird in der Regel von einem Projekt System verwaltet, das sowohl mit dem Sprachdienst als auch mit dem Buildsystem eng gekoppelt ist.

## <a name="initialization"></a>Initialisierung

In einem [Arbeitsbereich](workspaces.md)werden Sprachdienste von einem <xref:Microsoft.VisualStudio.Workspace.Intellisense.ILanguageServiceProvider> Erweiterungs Punkt initialisiert, der sich nur auf diesen Sprachdienst spezialisiert hat und nichts über die Builderstellung weiß. Auf diese Weise kann der Besitzer eines sprach Dienstanbieter unabhängig davon, wie viele Muster in Ordnern und Dateien für die Ausführung des Compilers während eines Builds vorhanden sind (z. b. MSBuild, Makefiles usw.), eine einzelne Erweiterung für geöffnete Ordner verwalten. Wenn Dateien, aus denen ein Datei Kontext erstellt wurde, auf dem Datenträger geändert werden und der Datei Kontext aktualisiert wird, wird der sprach Dienstanbieter über den aktualisierten Satz von Datei Kontexten benachrichtigt. Der sprach Dienstanbieter kann dann sein Modell aktualisieren.

Wenn ein Dokument im Editor geöffnet wird, berücksichtigt Visual Studio nur sprach Dienstanbieter, die Datei Kontext Typen benötigen, für die ein übereinstimmender Datei Kontext Anbieter gefunden werden kann. Anschließend übergibt er die Datei Kontext von den übereinstimmenden Anbietern an den ausgewählten sprach Dienstanbieter über `ILanguageServiceProvider.InitializeAsync` . Das, was der Sprachdienst Anbieter mit den Datei Kontext Daten durchführt, ist ein Implementierungsdetail des sprach Dienstanbieters, aber die erwartete Benutzer Leistung ist ein umfangreicherer Sprachdienst für das geöffnete Dokument.

## <a name="using-ilanguageserviceprovider"></a>Verwenden von ilanguageserviceprovider

Der Sprachdienst wird benachrichtigt, wenn ein Datei Kontext mit einem erstellt wird, der mit einem der `ContextType` `SupportedContextTypes` Werte des Language Server-Export Attributs übereinstimmt.

Um einen Sprachdienst zu unterstützen, benötigt eine Erweiterung Folgendes:

- Eine eindeutige `Guid` . Diese wird für `SupportedContextTypes` Attribut Argumente und in einem- `FileContext` Objekt verwendet.
- Sprachdatei Kontext
  - Anbieterfactory
    - `ExportFileContextProviderAttribute`Attribut mit dem obigen, das in eindeutig generiert wurde `Guid``SupportedContextTypes`
    - Implementiert `IWorkspaceProviderFactory<IFileContextProvider>`
  - Anbieter Implementierung von `IFileContextProvider.GetContextsForFileAsync`
    - Erstellen Sie eine neue `FileContext` mit dem `contextType` Konstruktorargument als eindeutig generierte `Guid`
    - Verwenden Sie die- `Context` Eigenschaft des `FileContext` , um zusätzliche Daten für das `ILanguageServiceProvider`
- Sprachdienst
  - Anbieterfactory
    - `ExportLanguageServiceProvider`Attribut mit dem obigen, das in eindeutig generiert wurde `Guid``SupportedContextTypes`
    - Implementiert `IWorkspaceProviderFactory<ILanguageServiceProvider>`
  - Anbieter
    - Implementiert `ILanguageServiceProvider`
    - Verwenden `ILanguageServiceProvider.InitializeAsync` Sie, um Sprachdienste für die bereitgestellten Argumente zu aktivieren, wenn eine Datei geöffnet wird.
    - Verwenden `ILanguageServiceProvider.UninitializeAsync` Sie, um Sprachdienste für die bereitgestellten Argumente zu deaktivieren, wenn eine Datei geschlossen wird.

>[!WARNING]
>Die `ILanguageServiceProvider` Methoden können vom Arbeitsbereich im Haupt Thread aufgerufen werden. Planen Sie die Planung von Arbeitsaufgaben in einem anderen Thread, um die Einführung von UI-Verzögerungen

## <a name="language-server-protocol"></a>Sprachserverprotokoll

Die `Microsoft.VisualStudio.Workspace.*` APIs sind nicht die einzige Möglichkeit, ihren Sprachdienst im geöffneten Ordner zu aktivieren. Eine andere Möglichkeit besteht darin, einen Sprachserver zu verwenden. Weitere Informationen finden Sie unter [sprach Server Protokoll](language-server-protocol.md).

## <a name="related-interfaces"></a>Verwandte Schnittstellen

- <xref:Microsoft.VisualStudio.Workspace.Intellisense.ILanguageServiceProvider> wird aufgerufen, wenn eine Datei mit übereinstimmenden Dateitypen zum Bearbeiten geöffnet oder geschlossen wird.

## <a name="next-steps"></a>Nächste Schritte

* Der [Arbeitsbereich Build](workspace-build.md) : der Ordner wird geöffnet und unterstützt Buildsysteme wie MSBuild und Makefiles.