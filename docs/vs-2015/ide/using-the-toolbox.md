---
title: Verwenden der Toolbox | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.chooseitems
- vs.toolboxpages.activexcontrols
- VS.CHOOSEITEMS.windowsuixamlcomponents
- VS.chooseitems.silverlightcomponents
- VC.EDITORS.RIBBON
- vs.customizetoolbox
- VS.chooseitems.System.Workflow_Components
- vs.chooseitems.frameworkcomponents
- VS.ToolboxPages..NET_Framework_Components
- VS.chooseitems.Microsoft.VisualStudio.Toolbox.VsToolboxPage
- vs.chooseitems.comcomponents
- vs.toolboxpages.NGWS_components
helpviewer_keywords:
- toolbox, adding items
- Visual Studio, toolbox
- toolbox, tabs
- toolbox
ms.assetid: 82e7cb43-4d0b-4e17-b7b0-43f96c22c3c2
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ba8a37ac9e049455ffe19314dee0e228c3c14c97
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "74295610"
---
# <a name="using-the-toolbox"></a>Verwenden der Toolbox
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mithilfe des Werkzeugkastens können Sie Ihrem Projekt Steuerelemente und andere Elemente hinzufügen. Sie können verschiedene Steuerelemente per Drag & Drop auf die Oberfläche des verwendeten Designers verschieben und die Größe und Position der Steuerelemente ändern.

 Der Werkzeugkasten wird in Verbindung mit Designeransichten angezeigt, wie der Entwurfsansicht einer XAML-Datei. Im Werkzeugkasten werden nur die Steuerelemente angezeigt, die im aktuellen Designer verwendet werden können.

 Die in Ihrem Projekt verwendete .NET Framework-Version wirkt sich auch auf den Satz von Steuerelementen aus, der im Werkzeugkasten angezeigt wird. Standardmäßig verwenden [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]-Projekte das .NET Framework 4.5.1. Sie können festlegen, dass Ihr Projekt eine andere Version von .NET Framework verwendet, indem Sie den Projektknoten im **Projektmappen-Explorer** auswählen und anschließend mit **Eigenschaften > Anwendung > Zielframework** durchsuchen.

## <a name="managing-the-toolbox-and-its-controls"></a>Verwalten der Toolbox und deren Steuerelemente
 Standardmäßig wird die Toolbox auf der linken Seite der Visual Studio IDE reduziert dargestellt und wird angezeigt, wenn der Mauszeiger darüber bewegt wird. Sie können die Toolbox anheften (durch Klicken auf das Symbol **Anheften** auf der Toolbox-Symbolleiste), sodass dieser geöffnet bleibt, wenn Sie den Cursor verschieben. Sie können das Toolboxfenster auch abdocken und es an eine beliebige Stelle auf dem Bildschirm ziehen. Sie können den Werkzeugkasten andocken, abdocken und ausblenden, indem Sie mit der rechten Maustaste auf die Werkzeugkasten-Symbolleiste klicken und eine der Optionen auswählen.

 Mithilfe der folgenden Befehle im Kontextmenü können Sie die Elemente auf einer Toolboxregisterkarte neu anordnen oder benutzerdefinierte Registerkarten und Elemente hinzufügen:

- **Element umbenennen** : benennt das ausgewählte Element um.

- **Alle anzeigen**: zeigt alle möglichen Steuerelemente an (nicht nur die für den aktuellen Designer).

- **Listenansicht**: zeigt die Steuerelemente in einer vertikalen Liste an. Wenn dieses Kontrollkästchen deaktiviert ist, werden die Steuerelemente horizontal angezeigt.

- **Elemente auswählen**: öffnet das Dialogfeld **Toolboxelemente auswählen**, sodass Sie die Elemente festlegen können, die in der **Toolbox** angezeigt werden. Sie können ein Element ein- oder ausblenden, indem Sie dessen Kontrollkästchen aktivieren oder deaktivieren.

- **Elemente alphabetisch sortieren** : sortiert die Elemente nach Namen.

- **Symbolleiste zurücksetzen** : stellt die Standardeinstellungen und Elemente der Toolbox wieder her.

- **Registerkarte hinzufügen** : Fügt eine neue Toolbox Registerkarte hinzu.

- **Nach oben**: verschiebt das ausgewählte Element nach oben.

- **Nach unten**: verschiebt das ausgewählte Element nach unten.

## <a name="creating-and-distributing-custom-toolbox-controls"></a>Erstellen und Verteilen von benutzerdefinierten Toolbox-Steuerelementen
 Sie können ein benutzerdefiniertes Toolbox-Steuerelement in Visual Basic oder Visual C++ erstellen, und Sie können mit einer Projektvorlage beginnen, die auf [Windows Presentation Foundation](../extensibility/creating-a-wpf-toolbox-control.md) oder [Windows Forms](../misc/how-to-create-a-toolbox-control-that-uses-windows-forms.md) basiert. Sie können Ihr Steuerelement dann an Ihre Teamkollegen verteilen oder es im Internet mithilfe des [Installationsprogramms für Toolbox-Steuerelemente](http://www.unicode.org/versions/Unicode5.2.0/ch04.pdf) veröffentlichen.
