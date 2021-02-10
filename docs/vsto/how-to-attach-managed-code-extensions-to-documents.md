---
title: 'Gewusst wie: Anfügen von Erweiterungen durch verwalteten Code an Dokumente'
description: Erfahren Sie, wie Sie eine Anpassungsassembly an ein vorhandenes Microsoft Office Word-Dokument oder Microsoft Office Excel-Arbeitsmappe anfügen können.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- managed code extensions [Office development in Visual Studio], attaching
- documents [Office development in Visual Studio], managed code extensions
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 063b66af781ee412e7f7d2ab8014e009bc93bad9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99954110"
---
# <a name="how-to-attach-managed-code-extensions-to-documents"></a>Gewusst wie: Anfügen von Erweiterungen durch verwalteten Code an Dokumente
  Sie können eine Anpassungsassembly an ein vorhandenes Microsoft Office Word-Dokument oder an Microsoft Office Excel-Arbeitsmappe anfügen. Das Dokument oder die Arbeitsmappe kann ein beliebiges Dateiformat aufweisen, das von den Microsoft Office Projekten und Entwicklungs Tools in Visual Studio unterstützt wird. Weitere Informationen finden Sie unter [Architektur von Anpassungen auf Dokument Ebene](../vsto/architecture-of-document-level-customizations.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Um eine Anpassung an ein Word-oder Excel-Dokument anzufügen, verwenden Sie die- <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> Methode der- <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> Klasse. Da die- <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> Klasse auf einem Computer ausgeführt werden soll, auf dem Microsoft Office nicht installiert ist, können Sie diese Methode in Projektmappen verwenden, die sich nicht direkt auf Microsoft Office Entwicklung (z. b. eine Konsole oder eine Windows Forms Anwendung) beziehen.

> [!NOTE]
> Die Anpassung wird nicht geladen, wenn der Code Steuerelemente erwartet, die das angegebene Dokument nicht besitzt.

### <a name="to-attach-managed-code-extensions-to-a-document"></a>So fügen Sie Erweiterungen durch verwalteten Code an ein Dokument an

1. Fügen Sie in einem Projekt, das keine Microsoft Office benötigt, wie z. b. eine Konsolenanwendung oder ein Windows Forms Projekt, einen Verweis auf die *Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll* -und *Microsoft.VisualStudio.Tools.Applications.Runtime.dll* -Assemblys hinzu.

2. Fügen Sie am Anfang der Codedatei die folgenden **Importe** oder **using** -Anweisungen hinzu.

     [!code-csharp[Trin_VstcoreDeployment#4](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#4)]
     [!code-vb[Trin_VstcoreDeployment#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#4)]

3. Ruft die statische <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> Methode auf.

     Im folgenden Codebeispiel wird die-Überladung verwendet <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> . Diese Überladung übernimmt den vollständigen Pfad des Dokuments und einen <xref:System.Uri> , der den Speicherort des Bereitstellungs Manifests für die Anpassung angibt, die Sie an das Dokument anfügen möchten. In diesem Beispiel wird davon ausgegangen, dass sich ein Word-Dokument mit dem Namen **WordDocument1.docx** auf dem Desktop befindet und das Bereitstellungs Manifest sich in einem Ordner mit dem Namen " **Publish** " befindet, der sich auch auf dem Desktop befindet.

     [!code-csharp[Trin_VstcoreDeployment#3](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#3)]
     [!code-vb[Trin_VstcoreDeployment#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#3)]

4. Erstellen Sie das Projekt, und führen Sie die Anwendung auf dem Computer aus, auf dem Sie die Anpassung anfügen möchten. Auf dem Computer muss die Visual Studio 2010-Tools für Office-Laufzeit installiert sein.

## <a name="see-also"></a>Weitere Informationen
- [Verwalten von Dokumenten auf einem Server mit der ServerDocument-Klasse](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Gewusst wie: Entfernen von Erweiterungen durch verwalteten Code aus Dokumenten](../vsto/how-to-remove-managed-code-extensions-from-documents.md)
- [Anwendungs-und Bereitstellungs Manifeste in Office-Lösungen](../vsto/application-and-deployment-manifests-in-office-solutions.md)
