---
title: Parallele Installation mehrerer Visual Studio-Versionen
description: Hier erfahren Sie, wie Sie Visual Studio auf einem Computer installieren, auf dem bereits eine frühere oder spätere Version von Visual Studio installiert ist.
ms.custom: SEO-VS-2020
ms.date: 07/24/2019
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.topic: conceptual
helpviewer_keywords:
- side-by-side installations [Visual Studio]
- Help [Visual Studio], installing
- install multiple versions of Visual Studio
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.openlocfilehash: f17759d186805dc72623f27c9f254c7a6c0d36e2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941527"
---
# <a name="install-visual-studio-versions-side-by-side"></a>Parallele Installation mehrerer Visual Studio-Versionen

Sie können Visual Studio auf einem Computer installieren, auf dem bereits eine frühere oder spätere Version von Visual Studio installiert ist.

::: moniker range="vs-2017"

Bevor Sie Versionen parallel installieren, sollten Sie sich mit folgenden Bedingungen vertraut machen:

* Wenn Sie Visual Studio 2017 verwenden, um eine Projektmappe zu öffnen, die in Visual Studio 2015 erstellt wurde, können Sie die Projektmappe später erneut in der früheren Version öffnen und ändern, sofern Sie keine Funktionen implementiert haben, die für Visual Studio 2017 spezifisch sind.

* Wenn Sie versuchen, eine Projektmappe mit Visual Studio 2017 zu öffnen, die mit Visual Studio 2015 oder einer früheren Version erstellt wurde, müssen Sie möglicherweise Ihre Projekte und Dateien ändern, damit diese mit Visual Studio 2017 kompatibel sind. Weitere Informationen finden Sie unter [Projektmigration und Upgradereferenz für Visual Studio 2017](../porting/port-migrate-and-upgrade-visual-studio-projects.md?view=vs-2017&preserve-view=true).

::: moniker-end

::: moniker range=">= vs-2019"

Bevor Sie Versionen parallel installieren, sollten Sie sich mit folgenden Bedingungen vertraut machen:

* Wenn Sie Visual Studio 2019 verwenden, um eine Projektmappe zu öffnen, die in Visual Studio 2017 erstellt wurde, können Sie die Projektmappe später erneut in der früheren Version öffnen und ändern, sofern Sie keine Funktionen implementiert haben, die für Visual Studio 2019 spezifisch sind.

* Wenn Sie versuchen, eine Projektmappe mit Visual Studio 2019 zu öffnen, die mit Visual Studio 2017 oder einer früheren Version erstellt wurde, müssen Sie möglicherweise Ihre Projekte und Dateien ändern, damit diese mit Visual Studio 2019 kompatibel sind. Weitere Informationen finden Sie unter [Projektmigration und Upgradereferenz für Visual Studio 2017](../porting/port-migrate-and-upgrade-visual-studio-projects.md).

::: moniker-end

* Wenn Sie eine Visual Studio-Version auf einem Computer deinstallieren, auf dem mehrere Versionen installiert sind, werden die Visual Studio-Dateizuordnungen für alle Versionen entfernt.

* Visual Studio aktualisiert die Erweiterungen nicht automatisch, da nicht alle Erweiterungen kompatibel sind. Installieren Sie erneut die Erweiterungen aus dem [Visual Studio Marketplace](https://marketplace.visualstudio.com/) oder vom Softwareherausgeber.

## <a name="install-minor-visual-studio-versions-side-by-side"></a>Parallele Installation von Visual Studio-Nebenversionen

Beim Durchführen eines Upgrades von einer Visual Studio-Nebenversion zur nächsten, aktualisiert das Visual Studio-Installationsprogramm Ihre aktuelle Installation standardmäßig auf die nächste Version dieses Kanals. Wenn Sie beispielsweise Preview 16.6.4 installieren, versucht das Installationsprogramm, Ihre aktuelle Installation von Preview 16.6.3 zu ersetzen, da beide Versionen sich im Previewkanal 16.6 befinden. Dadurch wird sichergestellt, dass ältere Versionen von Visual Studio keinen Speicherplatz auf Ihrem Computer belegen. In einigen spezifischen Fällen kann es hilfreich sein, Nebenversionen parallel zu installieren. Im genannten Beispiel bedeutet dies, dass sich die Versionen 16.6.3 und 16.6.4 auf dem gleichen Computer befinden.

1. Laden Sie die [Visual Studio-Bootstrapperdatei](/visualstudio/releases/2019/history#installing-an-earlier-release) für die Nebenversion herunter, die Sie parallel mit Ihren vorhandenen Versionen von Visual Studio installieren möchten.
2. Öffnen Sie die Eingabeaufforderung im Administratormodus. Hierzu öffnen Sie das Windows-Startmenü, geben Sie „cmd“ ein, klicken Sie mit der rechten Maustaste auf die gefundene Eingabeaufforderung, und klicken Sie dann auf **Als Administrator ausführen**. Ändern Sie in der Eingabeaufforderung das Verzeichnis in den Ordner, in dem sich Ihre Visual Studio-Bootstrapperdatei befindet.
3. Führen Sie den folgenden Befehl aus, legen Sie einen neuen Ordnerpfad für den Installationsspeicherort fest, und ersetzen Sie den Namen der EXE-Datei durch den Namen der entsprechenden Bootstrapperdatei für die Version von Visual Studio, die Sie installieren. Der Name der EXE-Datei sollte mit einer der folgenden Dateien übereinstimmen oder ähneln:
   * „vs_community.exe“ für Visual Studio Community
   * „vs_professional.exe“ für Visual Studio Professional
   * „vs_enterprise.exe“ für Visual Studio Enterprise

   ```
   vs_Enterprise.exe --installPath "C:\Program Files (x86)\Microsoft Visual Studio\<2019 AddNewPath>"
   ```

4. Befolgen Sie die Installationsanweisungen, um die Komponenten auszuwählen, die Sie für Ihre Installation benötigen. Weitere Informationen finden Sie unter [Installieren von Visual Studio](install-visual-studio.md#step-4---choose-workloads).

## <a name="net-framework-versions-and-side-by-side-installations"></a>.NET Framework-Versionen und parallele Installationen

Visual Basic-, Visual C#- und Visual F#-Projekte nutzen die Option **Zielframework** im **Projekt-Designer**, um festzulegen, welche Version des .NET Frameworks ein Projekt verwendet. Für ein C++-Projekt können Sie das Zielframework durch Bearbeiten der Projektdatei (.vcxproj) ändern. Weitere Informationen finden Sie unter [Kompatibilität von .NET Framework-Versionen](/dotnet/framework/migration-guide/version-compatibility).

Wenn Sie ein Projekt erstellen, können Sie angeben, auf welche Version von .NET Framework das Projekt in der Liste **.NET Framework** im Dialogfeld **Neues Projekt** abzielt.

Sprachspezifische Informationen finden Sie im entsprechenden Thema in der folgenden Tabelle.

::: moniker range="vs-2017"

| Sprache | Thema |
|--------------|-----------|
| Visual Basic | [Seite „Anwendung“, Projekt-Designer (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md?view=vs-2017&preserve-view=true) |
| Visual C# | [Seite „Anwendung“, Projekt-Designer (C#)](../ide/reference/application-page-project-designer-csharp.md?view=vs-2017&preserve-view=true) |
| Visual F# | [Entwickeln mit Visual F# in Visual Studio](../ide/fsharp-visual-studio.md?view=vs-2017&preserve-view=true) |
|C++ | [How to: Modify the target framework and platform toolset (Vorgehensweise: Ändern des Zielframeworks und des Plattformtoolsets)](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset/). |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Siehe auch

* [Installieren von Visual Studio](install-visual-studio.md?view=vs-2017&preserve-view=true)
* [Übertragung, Migration und Upgrade der Visual Studio-Projekte](../porting/port-migrate-and-upgrade-visual-studio-projects.md?view=vs-2017&preserve-view=true)
* [Erstellen von isolierten Anwendungen und parallelen Assemblys (C/C++)](/cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies/)

::: moniker-end

::: moniker range=">= vs-2019"

| Sprache | Thema |
|--------------|-----------|
| Visual Basic | [Seite „Anwendung“, Projekt-Designer (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md) |
| Visual C# | [Seite „Anwendung“, Projekt-Designer (C#)](../ide/reference/application-page-project-designer-csharp.md) |
| Visual F# | [Entwickeln mit Visual F# in Visual Studio](../ide/fsharp-visual-studio.md) |
| C++ | [How to: Modify the target framework and platform toolset (Vorgehensweise: Ändern des Zielframeworks und des Plattformtoolsets)](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset/). |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Siehe auch

* [Installieren von Visual Studio](install-visual-studio.md)
* [Übertragung, Migration und Upgrade der Visual Studio-Projekte](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
* [Erstellen von isolierten Anwendungen und parallelen Assemblys (C/C++)](/cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies/)

::: moniker-end
