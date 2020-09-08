---
title: Übersicht über XAML
ms.date: 06/23/2020
ms.topic: overview
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: e14e23f9820301374bd435484ba784edf50294bb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85331953"
---
# <a name="overview-of-xaml"></a>Übersicht über XAML

Bei Extensible Application Markup Language (XAML) handelt es sich um eine deklarative Sprache, die auf XML basiert. XAML wird häufig in den folgenden Anwendungstypen zum Erstellen von Benutzeroberflächen verwendet:

- [Windows Presentation Foundation-Apps (WPF)](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [Universelle Windows-Plattform-Apps (UWP)](/windows/uwp/xaml-platform/xaml-overview)
- [Xamarin.Forms-Apps](/xamarin/xamarin-forms/xaml/)

Der folgende XAML-Code definiert ein einfaches Schaltflächen-Steuerelement.

```xaml
<Button Click="ButtonClick">Show updates</Button>
```

XAML wird auch zum Definieren von Workflows in [Windows Workflow Foundation-Apps (WF)](/dotnet/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml) verwendet.

## <a name="xaml-code-editor"></a>XAML-Code-Editor

Der [XAML-Code-Editor](xaml-code-editor.md) in der Visual Studio-IDE enthält alle Tools, die Sie zum Erstellen von WPF- und UWP-Apps für die Windows-Plattform und für Xamarin.Forms benötigen. Obwohl die IDE in Visual Studio viele Features bietet, mit denen Sie Apps für weitere Plattformen entwickeln können, weist sie auch einige XAML-spezifische Features auf.

## <a name="xaml-designer"></a>XAML-Designer

Visual Studio und Blend für Visual Studio beinhalten einen [XAML-Designer](creating-a-ui-by-using-xaml-designer-in-visual-studio.md), der Sie beim Erstellen von Benutzeroberflächen für WPF-, UWP-und Xamarin.Forms-Apps unterstützt. Sie können Steuerelemente aus dem Fenster „Toolbox“ oder „Objekte“ ziehen und Eigenschaften im Eigenschaftenfenster festlegen. Wenn Sie diese Aktionen ausführen, erstellen Visual Studio und Blend für Visual Studio den entsprechenden XAML-Code. Wenn Sie den XAML-Code direkt bearbeiten möchten, ist dies ebenfalls möglich.

## <a name="whats-new"></a>Neues

Aktuelle Informationen finden Sie in den folgenden Ressourcen:

- Blogbeitrag **[Verbesserungen an XAML-Tools in Visual Studio 2019, Version 16.7, Preview 1](https://devblogs.microsoft.com/visualstudio/improvements-to-xaml-tooling-in-visual-studio-2019-version-16-7-preview-1/)**
- Blogbeitrag **[Neuerungen in den XAML-Entwicklertools in Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/whats-new-in-xaml-developer-tools-in-visual-studio-2019-for-wpf-uwp/)**
- YouTube-Video **[Neue XAML-Features in Visual Studio](https://youtu.be/yI9OyA4ZM2E)**

## <a name="see-also"></a>Weitere Informationen

- [XAML in WPF-Apps](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [XAML in UWP-Apps](/windows/uwp/xaml-platform/xaml-overview)
- [XAML in Xamarin.Forms-Apps](/xamarin/xamarin-forms/xaml/)
