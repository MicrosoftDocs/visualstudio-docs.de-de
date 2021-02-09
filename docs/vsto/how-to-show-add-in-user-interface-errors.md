---
title: 'Gewusst wie: Anzeigen von Add-in-Benutzeroberflächen Fehlern'
description: Erfahren Sie, wie Sie Visual Studio verwenden können, um vtso-Add-in-Benutzeroberflächen Fehler in Microsoft Office Anwendungen Programm gesteuert anzuzeigen.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], user interface errors
- errors [Office development in Visual Studio], user interface errors
- user interfaces [Office development in Visual Studio], errors
- application-level add-ins [Office development in Visual Studio], user interface errors
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 29e07e49d901b44b534d9d274e5535be663e97ef
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927677"
---
# <a name="how-to-show-add-in-user-interface-errors"></a>Gewusst wie: Anzeigen von Add-in-Benutzeroberflächen Fehlern
  Wenn ein VSTO-Add-in versucht, die Microsoft Office-Benutzeroberfläche zu bearbeiten, wird standardmäßig keine Fehlermeldung angezeigt. Sie können Microsoft Office-Anwendungen aber so konfigurieren, dass Meldungen für Fehler angezeigt werden, die sich auf die Benutzeroberfläche beziehen. Anhand dieser Meldungen können Sie feststellen, warum ein benutzerdefiniertes Menüband nicht angezeigt wird oder warum ein Menüband angezeigt wird, aber keine Steuerelemente angezeigt werden.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

## <a name="to-show-vsto-add-in-user-interface-errors"></a>So zeigen Sie VSTO-Add-In-Benutzeroberflächenfehler an

1. Starten Sie die Anwendung.

2. Klicken Sie auf die Registerkarte **Datei** .

3. Klicken Sie auf **Optionen**.

4. Klicken Sie im Bereich "Kategorien" auf **Erweitert**.

5. Wählen Sie im Detailbereich die Option **VSTO-Add-In-Benutzeroberflächenfehler anzeigen** aus, und klicken Sie dann auf **OK**.

    > [!NOTE]
    > Für Outlook befindet sich das Kontrollkästchen **VSTO-Add-In-Benutzeroberflächenfehler anzeigen** im Abschnitt **Entwickler** des Detailbereichs. Für andere Anwendungen befindet sich das Kontrollkästchen im Abschnitt **Allgemein** des Detailbereichs.

## <a name="see-also"></a>Weitere Informationen
- [Office-Benutzeroberflächen Anpassung](../vsto/office-ui-customization.md)
- [Erstellen von Outlook-Formular Bereichen](../vsto/creating-outlook-form-regions.md)
- [Übersicht über Menüband](../vsto/ribbon-overview.md)
- [Übersicht über den Aktionsbereich](../vsto/actions-pane-overview.md)
