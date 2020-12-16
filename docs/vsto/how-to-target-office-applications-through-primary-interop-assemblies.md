---
title: Office-Apps über primäre Interopassemblys als Ziel
description: Erfahren Sie, wie Sie Visual Studio verwenden können, um Microsoft Office Anwendungen mithilfe primärer Interop-Assemblys Programm gesteuert zu verwenden.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- assemblies [Office development in Visual Studio], PIA references
- primary interop assemblies [Office development in Visual Studio], adding references to
- Office primary interop assemblies in Visual Studio, adding references to
- Office applications [Office development in Visual Studio], automating
- application development [Office development in Visual Studio], automating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 81c2852a92124a7cf9fb6078b196982d22100be7
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528104"
---
# <a name="how-to-target-office-applications-through-primary-interop-assemblies"></a>Gewusst wie: Ausrichten von Office-Anwendungen über primäre Interop-Assemblys
  Wenn Sie ein neues Office-Projekt erstellen, fügt Visual Studio automatisch Verweise auf die primären Interopassemblys (PIAs) von Microsoft Office hinzu, die zum Erstellen des Projekts erforderlich sind. Verweise auf andere PIAs müssen in den folgenden Szenarien hinzugefügt werden:

- Sie möchten Features anderer Microsoft Office-Anwendungen im Projekt verwenden. Sie möchten z. B. Features von Microsoft Office Excel in einem Projekt für Microsoft Office Word verwenden.

- Sie möchten Microsoft Office-Anwendungen automatisieren, die nicht über dedizierte Projekte in Visual Studio verfügen, z. B. Microsoft Office Access.

  [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="to-add-a-reference-to-a-primary-interop-assembly"></a>So fügen Sie einen Verweis auf eine primäre Interopassembly hinzu

1. Öffnen Sie das Office-Projekt, und wählen Sie den Projektnamen in **Projektmappen-Explorer** aus.

2. Klicken Sie im Menü **Projekt** auf **Verweis hinzufügen**.

3. Wählen Sie auf der Registerkarte **Framework** die gewünschte Pia in der Liste **Komponenten Name** aus. Weitere Informationen zu den verfügbaren Microsoft Office primären Interop-Assemblys finden Sie unter Primäre Interopassemblys für [Office](../vsto/office-primary-interop-assemblies.md).

     Wenn das Projekt auf oder höher ausgerichtet [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ist, wird die Eigenschaft **Interop-Typen einbetten** für den Assemblyverweis standardmäßig auf **true** festgelegt. Mit dieser Einstellung erfordert die Lösung keine PIA auf Endbenutzercomputern. Weitere Informationen finden Sie unter [Entwerfen und Erstellen von Office-](../vsto/designing-and-creating-office-solutions.md)Projektmappen.

    > [!NOTE]
    > Fügen Sie in Office-Projekten Verweise auf Office-PIAs immer hinzu, indem Sie die Registerkarte **.net** des Dialog Felds **Verweis hinzufügen** anstelle der Registerkarte **com** verwenden. Weitere Informationen finden Sie unter [primäre Interop](../vsto/office-primary-interop-assemblies.md)-Assemblys in Office.

4. Klicken Sie auf **OK**.

     Der AssemblyName wird im Ordner **Verweise** von **Projektmappen-Explorer** angezeigt.

## <a name="see-also"></a>Weitere Informationen
- [Primäre Interopassemblys für Office](../vsto/office-primary-interop-assemblies.md)
- [Schreiben von Code in Office-Lösungen](../vsto/writing-code-in-office-solutions.md)
- [Entwickeln von Office-Lösungen](../vsto/developing-office-solutions.md)
- [Gewusst wie: Installieren von primären Interop-Assemblys in Office](../vsto/how-to-install-office-primary-interop-assemblies.md)
