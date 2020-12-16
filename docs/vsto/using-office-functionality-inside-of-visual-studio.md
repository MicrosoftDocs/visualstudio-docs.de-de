---
title: Verwenden von Office-Funktionen in Visual Studio
description: Erfahren Sie, wie das Dokument und die zugehörige Anwendung aus einem Projekt auf Dokument Ebene in Visual Studio gehostet werden, damit Sie direkt mit dem Dokument arbeiten können.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], document protection
- Office applications [Office development in Visual Studio]
- Office functionality inside Visual Studio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c93994b233990e2362c62445909adb66a0eeeb9b
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528404"
---
# <a name="use-office-functionality-inside-of-visual-studio"></a>Verwenden von Office-Funktionen in Visual Studio
  Wenn Sie ein Projekt auf Dokument Ebene erstellen, werden das Dokument und die zugehörige Anwendung in Visual Studio gehostet, damit Sie das Dokument direkt entwerfen und bearbeiten können. Wenn Sie eine Microsoft Office Anwendung in Visual Studio geöffnet haben, funktioniert Sie im allgemeinen erwartungsgemäß. Ein Teil der Funktionalität der Anwendung ist jedoch unterschiedlich oder nicht zugänglich.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="document-protection"></a>Dokument Schutz
 Microsoft Office Word und Microsoft Office Excel bieten Dokument Schutz Features, die Sie in Ihren Projekten verwenden können. Wenn der Dokument Schutz jedoch aktiviert ist, während das Dokument in Visual Studio geöffnet ist, können Sie Änderungen an den Entwurfs Änderungen vornehmen. Weitere Informationen finden Sie unter [Dokument Schutz in Projektmappen auf Dokument Ebene](../vsto/document-protection-in-document-level-solutions.md).

## <a name="information-rights-management"></a>Verwaltung von Informationsrechten
 Information Rights Management (unm) ist in Microsoft Office Word und Microsoft Office Excel verfügbar. Mithilfe von "IRiM" können Sie verhindern, dass nicht autorisierte Personen vertrauliche Informationen anzeigen oder ändern. Allerdings kann es auch verhindern, dass der Code ausgeführt wird. Weitere Informationen finden Sie unter [Übersicht über Verwaltung von Informationsrechten und Erweiterungen von verwalteten Code](../vsto/information-rights-management-and-managed-code-extensions-overview.md).

## <a name="password-protection"></a>Kennwortschutz
 Microsoft Office Word-Dokumente und Microsoft Office Excel-Arbeitsmappen können so festgelegt werden, dass Sie nicht von einem Benutzer geöffnet werden können, der das Kennwort nicht kennt. Der Kenn Wort Schutz wird in Word und Excel anders behandelt und kann sich auf den Entwicklungsprozess auswirken. Weitere Informationen finden Sie unter Kenn [Wort Schutz für Office-Dokumente](../vsto/password-protection-on-office-documents.md).

## <a name="see-also"></a>Weitere Informationen
- [Dokument Schutz in Projektmappen auf Dokument Ebene](../vsto/document-protection-in-document-level-solutions.md)
- [Übersicht über Verwaltung von Informationsrechten und Erweiterungen von verwalteten Code](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Kenn Wort Schutz für Office-Dokumente](../vsto/password-protection-on-office-documents.md)
- [Gewusst wie: Öffnen von Office-Projektmappen ohne Ausführen von Code](../vsto/how-to-open-office-solutions-without-running-code.md)
