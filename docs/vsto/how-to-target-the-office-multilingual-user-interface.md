---
title: 'Gewusst wie: Ausrichten der mehrsprachigen Office-Benutzeroberfläche'
description: Erfahren Sie, wie Sie Visual Studio verwenden können, um die Microsoft Office mehrsprachige Benutzeroberfläche Programm gesteuert zu verwenden.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- globalization [Office development in Visual Studio], user interface targeting
- MUI [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], localization
- Multilingual User Interface [Office development in Visual Studio]
- localization [Office development in Visual Studio], user interface targeting
- Office applications [Office development in Visual Studio], globalization
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 245b257140cd0b1f54719ec7a132bf2297fc2dd3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99962339"
---
# <a name="how-to-target-the-office-multilingual-user-interface"></a>Gewusst wie: Ausrichten der mehrsprachigen Office-Benutzeroberfläche
  Die mehrsprachige Benutzeroberfläche ist ein Microsoft Office Feature, mit dem Endbenutzer die Sprache der Benutzeroberfläche (UI) ändern können. Ein Endbenutzer, der mit einer englischen Benutzeroberfläche arbeitet, kann z. b. die Sprache der Benutzeroberfläche in Spanisch ändern.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Wenn Ihre Anwendung von Personen verwendet wird, die viele Sprachen von Office verwenden, können Sie Code hinzufügen, um die Sprache Ihrer UI-Zeichen folgen automatisch so zu ändern, dass Sie der Sprache entspricht, die von Office auf dem Computer des Benutzers verwendet wird (wenn der Benutzer die richtigen Ressourcen installiert hat).

## <a name="to-check-the-current-office-ui-setting"></a>So überprüfen Sie die aktuelle Einstellung der Office-Benutzeroberfläche

1. Verwenden Sie die- <xref:System.Threading.Thread.CurrentUICulture%2A> Eigenschaft des aktuellen Threads. Legen Sie die Sprache Ihrer UI-Zeichen folgen entsprechend der Sprache fest, die von der Office-Version verwendet wird, die derzeit auf dem Computer des Benutzers ausgeführt wird.

     [!code-vb[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb#10)]
     [!code-csharp[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs#10)]

## <a name="see-also"></a>Weitere Informationen
- [Gewusst wie: Ausrichten von Office-Anwendungen über primäre Interop-Assemblys](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Späte Bindung in Office-Projektmappen](../vsto/late-binding-in-office-solutions.md)
