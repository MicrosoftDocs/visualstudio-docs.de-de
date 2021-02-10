---
title: Einstieg in die VSIX-Projektvorlage | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie die VSIX-Projektvorlage verwenden, um eine Erweiterung zu erstellen oder eine vorhandene Erweiterung für die Bereitstellung zu verpacken.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- Visual Studio SDK, VSIX project template
ms.assetid: 89fac33e-9380-4723-9b45-048a6e16f0ed
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 231b7e1595a7674280a56b4655643c2b77baeb85
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945798"
---
# <a name="get-started-with-the-vsix-project-template"></a>Beginnen Sie mit der VSIX-Projektvorlage

Sie können die VSIX-Projektvorlage verwenden, um eine Erweiterung zu erstellen oder eine vorhandene Erweiterung für die Bereitstellung zu verpacken. Die VSIX-Projektvorlage verfügt sowohl über Visual Basic-als auch über Visual c#-Versionen und wird als Teil des Visual Studio SDK installiert.

 Die VSIX-Projektvorlage besteht lediglich aus der Datei " *Source. Extension. vsixmanifest* ", die Informationen über die Erweiterung und die darin enthaltenen Ressourcen enthält.

 Zum Suchen der VSIX-Projektvorlage müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="deploy-a-custom-project-template-using-the-vsix-project-template"></a>Bereitstellen einer benutzerdefinierten Projektvorlage mithilfe der VSIX-Projektvorlage

 Die folgenden Schritte zeigen, wie Sie das VSIX-Projekt verwenden, um eine Projektvorlage zu verpacken, die Sie für andere Entwickler freigeben oder in die Visual Studio Gallery hochladen können.

1. Erstellen Sie eine Projektvorlage.

    1. Öffnen Sie das Projekt, aus dem eine Vorlage erstellt werden soll. Dieses Projekt kann einen beliebigen Projekttyp aufweisen.

    2. Klicken Sie im Menü **Projekt** auf **Vorlage exportieren**. Führen Sie die Schritte des Assistenten aus.

         Eine *ZIP* -Datei wird in *%UserProfile%\My Documents\Visual Studio {Version} \Meine exportierten Vorlagen \\* erstellt.

2. Erstellen Sie ein leeres VSIX-Projekt.

     Klicken Sie auf **Datei** > **Neu** > **Projekt**. Geben Sie im Suchfeld "VSIX" ein, und wählen Sie entweder die **c#** -oder **Visual Basic** Version des **VSIX-Projekts** aus.

3. Fügen Sie dem Projekt die *ZIP* -Datei hinzu. Legen Sie die Eigenschaft **in Ausgabeverzeichnis kopieren** auf fest `Copy Always` .

4. Doppelklicken Sie in **Projektmappen-Explorer** auf die Datei " *Source. Extension. vsixmanifest* ", um Sie im **VSIX-Manifest-Designer** zu öffnen, und nehmen Sie dann die folgenden Änderungen vor:

    - Legen Sie das Feld " **Product Name** " auf **meine Projektvorlage** fest.

    - Legen Sie das Feld **Product ID** auf **MyProjectTemplate-1** fest.

    - Legen Sie das Feld **Autor** auf **Fabrikam** fest.

    - Legen Sie das **Beschreibungs** Feld auf **meine Projektvorlage** fest.

    - Fügen Sie im Abschnitt **Assets** einen **Microsoft. VisualStudio. ProjectTemplate** -Typ hinzu, und legen Sie den Pfad auf den Namen der *ZIP* -Datei fest.

5. Speichern und schließen Sie die Datei " *Source. Extension. vsixmanifest* ".

6. Erstellen Sie das Projekt.

7. Doppelklicken Sie im Ausgabeverzeichnis auf die *VSIX* -Datei.

8. Ein **VSIX-Installations** Dialogfeld wird angezeigt. Befolgen Sie die Anweisungen, um die Erweiterung zu installieren.

9. Schließen Sie Visual Studio, und öffnen Sie es anschließend erneut.

::: moniker range="vs-2017"

10. Wählen Sie **Erweiterungen und Updates** (im **Menü Extras** ) aus, und wählen Sie die Kategorie **Vorlagen** aus. Eine der verfügbaren Erweiterungen sollte **meine Projektvorlage** sein.

::: moniker-end

::: moniker range=">=vs-2019"

10. Wählen Sie **Erweiterungen verwalten** (im Menü **Erweiterungen** ) aus, und wählen Sie die Kategorie **Vorlagen** aus. Eine der verfügbaren Erweiterungen sollte **meine Projektvorlage** sein.

::: moniker-end

11. Die neue Projektvorlage wird im Dialogfeld " **Neues Projekt** " am gleichen Speicherort wie die ursprüngliche Projektvorlage angezeigt. Wenn Sie z. b. eine Vorlage mit dem Namen **VB Console** aus einer Visual Basic-Konsolenanwendung erstellt haben, wird die **VB-Konsole** im gleichen Bereich wie die Vorlage Visual Basic **Konsolenanwendung** angezeigt.

### <a name="to-specify-the-location-of-the-template-in-the-new-project-dialog-box"></a>So geben Sie den Speicherort der Vorlage im Dialog Feld "Neues Projekt" an

1. Vorlagen Ordner befinden sich in den Verzeichnissen *{Visual Studio-Installationspfad} \Common7\IDE\ProjectTemplates* und *{Visual Studio-Installationspfad} \Common7\IDE\ItemTemplates* . Die Namen der Abschnitte der obersten Ebene im Dialogfeld " **Neues Projekt** " entsprechen nicht exakt den Namen der Vorlagen Ordner. Wenn Sie sich unterscheiden, verwenden Sie den Namen des Vorlagen Ordners.

    Ändern Sie die *VSIX* -Dateierweiterung in *. zip*, und öffnen Sie dann die Datei.

2. Erstellen Sie einen neuen Ordner mit dem gleichen Namen wie im Abschnitt des Dialog Felds " **Neues Projekt** ", in dem die Vorlage angezeigt werden soll.

3. Wenn die Vorlage in einem unter Abschnitt angezeigt werden soll, erstellen Sie einen Unterordner mit demselben Namen.

4. Verschieben Sie die *ZIP* -Datei der Vorlage in den neuen Ordner.

5. Ändern Sie die Erweiterung *. zip* in *. vsix*.

6. Öffnen Sie das VSIX-Manifest.

7. Aktualisieren Sie im VSIX-Manifest den **assetpfad** der Vorlage, sodass er auf den Stamm der Verzeichnisstruktur verweist, die die Vorlagen Datei enthält. Wenn sich die Vorlage beispielsweise in " *\csharp\windows*" befindet, sollte der Verweis auf " *\csharp*" zeigen.
