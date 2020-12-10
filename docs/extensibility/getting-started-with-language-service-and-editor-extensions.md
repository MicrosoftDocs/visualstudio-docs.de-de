---
title: Einstieg in die Erweiterungen für Sprachdienste und Editoren
description: Erfahren Sie, wie Sie Sprachdienst Funktionen zu beliebigen Inhaltstyp hinzufügen und das Aussehen und Verhalten des Visual Studio-Editors anpassen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 6b151891-c06d-40b1-9867-42298caa8492
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 471acaef0145b3bf1a73925b42e17a6343439ea2
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2020
ms.locfileid: "96994393"
---
# <a name="get-started-with-language-service-and-editor-extensions"></a>Einstieg in die Erweiterungen für Sprachdienste und Editoren

Sie können Editor-Erweiterungen verwenden, um Sprachdienst Funktionen wie Gliederung, übereinstimmende Klammern, IntelliSense und Glühbirnen ihrer eigenen Programmiersprache oder beliebigen Inhaltstyp hinzuzufügen. Sie können auch das Aussehen und Verhalten des Visual Studio-Editors anpassen, z. b. Text Farbgebung, Ränder, Zusatzelemente und andere visuelle Elemente. Sie können auch einen eigenen Inhaltstyp definieren und die Darstellung und das Verhalten der Text Ansichten angeben, in denen der Inhalt angezeigt wird.

 Um mit dem Schreiben von Editor-Erweiterungen zu beginnen, verwenden Sie die Editor-Projektvorlagen, die im Rahmen des Visual Studio SDK installiert werden. Das Visual Studio SDK ist ein herunterladbarer Satz von Tools, die die Entwicklung von Visual Studio-Erweiterungen vereinfachen, entweder mithilfe von VSPackages oder mithilfe der Managed Extensibility Framework (MEF).

> [!NOTE]
> Weitere Informationen zum Visual Studio SDK finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

 Es wird empfohlen, dass Sie sich mit den folgenden Konzepten und Technologien vertraut machen, bevor Sie eigene Editor-Erweiterungen schreiben.

## <a name="the-windows-presentation-foundation-wpf-and-editor-extensions"></a>Die Windows Presentation Foundation (WPF)-und Editor-Erweiterungen

 Die Benutzeroberfläche des Visual Studio-Editors (User Interface, UI) wird mithilfe des Windows Presentation Foundation (WPF) implementiert. Das WPF bietet eine umfassende visuelle Darstellung und ein konsistentes Programmiermodell, das die visuellen Aspekte des Codes von der Geschäftslogik trennt. Sie können beim Erstellen von Editor-Erweiterungen viele WPF-Elemente und-Funktionen verwenden. Weitere Informationen finden Sie unter [Windows Presentation Foundation](/dotnet/framework/wpf/index).

## <a name="the-managed-extensibility-framework-mef-and-editor-extensions"></a>Die Erweiterungen des Managed Extensibility Framework (MEF) und des Editors

 Der Visual Studio-Editor verwendet die Managed Extensibility Framework (MEF), um seine Komponenten und Erweiterungen zu verwalten. Mit dem MEF können Entwickler auch Erweiterungen für eine Host Anwendung wie Visual Studio einfacher erstellen. In diesem Framework definieren Sie eine Erweiterung gemäß einem MEF-Vertrag und exportieren Sie als MEF-Komponenten Teil. Die Host Anwendung verwaltet die Komponenten Teile, indem Sie Sie findet, registriert und sicherstellt, dass Sie auf den richtigen Kontext angewendet werden.

> [!NOTE]
> Weitere Informationen zur MEF im Editor finden Sie unter [Managed Extensibility Framework im Editor](../extensibility/managed-extensibility-framework-in-the-editor.md).

## <a name="visual-studio-editor-extension-points-and-extensions"></a>Erweiterungs Punkte und Erweiterungen von Visual Studio-Editor

 Editor-Erweiterungs Punkte sind MEF-Komponenten, die Sie anpassen und erweitern können. In einigen Fällen erweitern Sie den Erweiterungs Punkt, indem Sie eine Schnittstelle implementieren und Sie mit den richtigen Metadaten exportieren. In anderen Fällen deklarieren Sie einfach eine Erweiterung und exportieren Sie als einen bestimmten Typ.

 Im folgenden sind einige der grundlegenden Arten von Editor Erweiterungen aufgeführt:

- Ränder und Bild Lauf leisten

- Tags

- Zusatzelemente

- Optionen

- IntelliSense

  Weitere Informationen zu Editor-Erweiterungs Punkten finden Sie unter [Sprachdienst-und Editor-Erweiterungs Punkte](../extensibility/language-service-and-editor-extension-points.md).

## <a name="deploying-editor-extensions"></a>Bereitstellen von Editor Erweiterungen

 In Visual Studio stellen Sie Editor Erweiterungen bereit, indem Sie der Projekt Mappe eine Metadatendatei mit dem Namen *Source. Extension. vsixmanifest* hinzufügen, die Projekt Mappe aufbauen und dann eine Kopie der Binärdateien und des Manifests in einem Ordner hinzufügen, der Visual Studio bekannt ist. Die Manifest-Datei definiert die grundlegenden Fakten über die Erweiterung (z. b. Name, Autor, Version und Inhaltstyp). Weitere Informationen zur VSIX-Manifest-Datei und zum Bereitstellen von Erweiterungen finden Sie Unterlieferung von [Visual Studio-Erweiterungen](../extensibility/shipping-visual-studio-extensions.md).

 Wenn Sie eine Erweiterung auf einem Computer installieren, schließen Sie die Binärdateien und das Manifest in einen Unterordner des Ordners ein, der Visual Studio bekannt ist.

> [!WARNING]
> Sie müssen sich keine Gedanken über die Details von Manifesten und Bereitstellungs Standorten machen, wenn Sie eine der Editor-Erweiterbarkeits Vorlagen verwenden, die in Visual Studio enthalten sind. Die Vorlagen enthalten alles, was erforderlich ist, um eine Erweiterung zu registrieren und bereitzustellen.

## <a name="run-extensions-in-the-experimental-instance"></a>Ausführen von Erweiterungen in der experimentellen Instanz

 Sie können Ihre funktionierende Version von Visual Studio isolieren, während Sie eine Erweiterung entwickeln, indem Sie Sie im folgenden experimentellen Ordner (unter Windows Vista und Windows 7) bereitstellen:

 *{% LocalAppData%} \visualstudio\10.0exp\extensions \\ {Company} \\ {extensionID}*

 Wenn " *% LocalAppData%* " der Name des angemeldeten Benutzers ist, ist " *Company* " der Name des Unternehmens, das die Erweiterung besitzt, und " *extensionID* " ist die ID der Erweiterung.

 Wenn Sie eine Erweiterung am experimentellen Speicherort bereitstellen, wird Sie im Debugmodus ausgeführt. Eine zweite Instanz von Visual Studio wird gestartet, und Sie wird **Microsoft Visual Studio experimentelle Instanz** benannt.

## <a name="manage-extensions"></a>Verwalten von Erweiterungen

 Erweiterungen für Visual Studio werden unter **Erweiterungen und Updates** ( **im Menü Extras** ) aufgelistet. Wenn Sie eine Erweiterung in der experimentellen Instanz testen, wird Sie in **Erweiterungen und Updates** in der experimentellen Instanz aufgeführt, ist aber nicht in der Entwicklungs Instanz aufgeführt.

 Weitere Informationen finden Sie untersuchen [und Verwenden von Visual Studio-Erweiterungen](../ide/finding-and-using-visual-studio-extensions.md).

## <a name="use-templates-to-create-editor-extensions"></a>Verwenden von Vorlagen zum Erstellen von Editor-Erweiterungen

 Mithilfe von Editor-Vorlagen können Sie MEF-Erweiterungen erstellen, mit denen Klassifizierer, Zusatzelemente und Ränder angepasst werden. Es sind Vorlagen für c#-und Visual Basic-Projekte vorhanden. Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einer Editor-Element Vorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md).

 Sie können auch die VSIX-Projektvorlage zum Erstellen von Erweiterungen verwenden. Mit dieser Vorlage werden nur die Elemente bereitgestellt, die zum Bereitstellen einer beliebigen Erweiterung erforderlich sind, sowie die Datei " *Source. Extension. vsixmanifest* ", die erforderlichen Assemblyverweise und eine Projektdatei, die die Buildaufgaben enthält, die Ihnen die Bereitstellung der Erweiterung ermöglichen. Weitere Informationen finden Sie unter [VSIX-Projektvorlage](../extensibility/vsix-project-template.md).

 Sie können auch Editoren-MEF-Komponenten aus einer Visual Studio-Paket Erweiterung erstellen. Weitere Informationen finden Sie in den folgenden exemplarischen Vorgehensweisen:

- [Exemplarische Vorgehensweise: Verwenden eines Shellbefehls mit einer Editor-Erweiterung](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)

- [Exemplarische Vorgehensweise: Verwenden einer Tastenkombination mit einer Editor-Erweiterung](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)

## <a name="see-also"></a>Weitere Informationen

- [Sprachdienst-und Editor-Erweiterungs Punkte](../extensibility/language-service-and-editor-extension-points.md)
