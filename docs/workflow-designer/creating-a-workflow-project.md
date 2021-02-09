---
title: Erstellen eines Workflow Foundation-Projekts
description: Erfahren Sie, wie Sie Bibliotheken und Anwendungen mit den in Visual Studio verfügbaren Projektvorlagen erstellen.
ms.custom: SEO-VS-2020
ms.date: 06/25/2018
ms.topic: conceptual
helpviewer_keywords:
- Workflow Designer, creating a workflow project
- creating a workflow project
ms.assetid: 235a125e-ebe7-4a98-bf77-86c8558728fb
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cf8c0fe0b716cecee19c00bb0b300d4ffdc99355
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894360"
---
# <a name="workflow-project-templates"></a>Workflow-Projektvorlagen

Mithilfe von Visual Studio-Projektvorlagen können Sie Workflows, Windows Communication Foundation (WCF)-Workflow Dienste, benutzerdefinierte Aktivitäten und benutzerdefinierte Aktivitäts Designer erstellen. In diesem Artikel wird beschrieben, wie Sie Bibliotheken und Anwendungen mit den in Visual Studio verfügbaren Projektvorlagen erstellen.

## <a name="create-a-workflow-project"></a>Erstellen eines Workflowprojekts

Visual Studio bietet vier verschiedene Workflow Projektvorlagen:

- Workflow Konsolen-App

- WCF-Workflow Dienst-App

- Aktivitäts Bibliothek

- Aktivitäts Designer Bibliothek

Um auf diese Vorlagen zuzugreifen, installieren Sie zunächst die **Windows Workflow Foundation** Komponente von Visual Studio. Ausführliche Anweisungen finden Sie unter [install Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation).

1. Nachdem Sie die **Windows Workflow Foundation** Komponente installiert haben, wählen Sie **Datei**  >  **neu**  >  **Projekt** aus.

1. Suchen Sie eine Workflow Projektvorlage, und wählen Sie Sie aus, z. b. die Vorlage **Workflow Konsolenanwendung** .

1. Fahren Sie mit fort, um das Projekt zu erstellen.

   > [!NOTE]
   > Wenn Sie einer vorhandenen Projekt Mappe ein neues Projekt hinzufügen möchten, öffnen Sie die Projekt Mappe in Visual Studio, klicken Sie mit der rechten Maustaste auf **Projektmappen-Explorer**, und wählen Sie   >  **Neues Projekt** hinzufügen aus.

## <a name="workflow-console-app"></a>Workflow Konsolen-App

Wenn Sie die Vorlage **Konsolenanwendung für Workflows** auswählen, erstellt Visual Studio eine Workflow Definition in XAML. Der Workflow-Designer wird geöffnet und zeigt den Canvas für den Workflow an, den Sie erstellt haben. Um einen Workflow zu erstellen, ziehen Sie Aktivitäten oder andere Workflow Elemente aus der **Toolbox** in die Entwurfs Oberfläche.

## <a name="wcf-workflow-service-app"></a>WCF-Workflow Dienst-App

Wenn Sie die Vorlage **WCF-Workflow Dienst Anwendung** auswählen, erstellt Visual Studio eine Dienst Definition als XAML. Der Workflow-Designer öffnet die Entwurfs Ansicht mit einer <xref:System.Activities.Statements.Sequence> -Aktivität, die eine Reihe von <xref:System.ServiceModel.Activities.Receive> - <xref:System.ServiceModel.Activities.SendReply> Aktivitäten und-Aktivitäten enthält.

## <a name="activity-library"></a>Aktivitäts Bibliothek

Wenn Sie die Vorlage **Aktivitäts Bibliothek** auswählen, erstellt Visual Studio eine Aktivitäts Definition in XAML. Workflow-Designer öffnet den Canvas für Ihre benutzerdefinierte Aktivität und zeigt ihn an. Ziehen Sie eine Aktivität aus der **Toolbox** auf die Entwurfs Oberfläche, um Sie in die benutzerdefinierte Aktivität einzubeziehen.

> [!NOTE]
> Es ist nur eine untergeordnete Aktivität im Textkörper der benutzerdefinierten Aktivität zulässig. Diese untergeordnete Aktivität kann jedoch eine zusammengesetzte Aktivität sein, z. b. eine- <xref:System.Activities.Statements.Sequence> Aktivität oder eine- <xref:System.Activities.Statements.Flowchart> Aktivität.

## <a name="activity-designer-library"></a>Aktivitäts Designer Bibliothek

Wenn Sie die Bibliotheks Vorlage für den **Aktivitäts Designer** auswählen, erstellt Visual Studio eine Aktivitäts Designer Definition in XAML und eine Code-Behind-Implementierungs Datei. Der Workflow-Designer wird geöffnet und zeigt den Canvas für den Aktivitäts Designer an. Ziehen Sie Windows Presentation Foundation (WPF)-Steuerelemente aus der **Toolbox** auf die-Entwurfs Oberfläche, um Sie im benutzerdefinierten Aktivitäts Designer zu verwenden.

Ein Beispiel für das Implementieren eines benutzerdefinierten Aktivitäts Designers finden Sie unter Gewusst [wie: Erstellen eines benutzerdefinierten Aktivitäts Designers](/dotnet/framework/windows-workflow-foundation/how-to-create-a-custom-activity-designer).

> [!NOTE]
> Benutzerdefinierte Aktivitäts Designer können für benutzerdefinierte Aktivitäten und für .net-Standardaktivitäten verwendet werden.

## <a name="see-also"></a>Weitere Informationen

- [Workflow Designer verwenden](developing-applications-with-the-workflow-designer.md)
- [Entwerfen von Workflows (.NET Framework)](/dotnet/framework/windows-workflow-foundation/designing-workflows)
