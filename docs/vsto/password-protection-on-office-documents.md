---
title: Kenn Wort Schutz für Office-Dokumente
description: Erfahren Sie, wie Sie ein Kennwort für Ihre Microsoft Word-Dokumente und Excel-Arbeitsmappen festlegen, sodass Sie nicht von unbefugten Benutzern geöffnet werden können.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- passwords [Office development in Visual Studio], document protections
- documents [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio, restricted permissions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b6beaf85000438846e5d440e48c9722b9660f9bd
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528060"
---
# <a name="password-protection-on-office-documents"></a>Kenn Wort Schutz für Office-Dokumente
  Es ist möglich, ein Kennwort für Ihre Microsoft Office Word-Dokumente festzulegen und Excel-Arbeitsmappen Microsoft Office, damit Sie nicht von einem Benutzer geöffnet werden können, der das Kennwort nicht kennt. Diese Option wird **beim Öffnen als Kennwort** bezeichnet.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Sie können Projekte auf Dokument Ebene mithilfe vorhandener Dokumente und Arbeitsmappen erstellen, **für die beim Öffnen das Kennwort** aktiviert ist. Das Verhalten in Visual Studio unterscheidet sich bei Word-und Excel-Dokumenten, für die **beim Öffnen ein Kennwort** aktiviert ist.

 Informationen zum Aktivieren des **Kennworts beim Öffnen** finden Sie in der Hilfe zu Word oder Excel.

## <a name="behavior-of-excel-and-word"></a>Verhalten von Excel und Word
 Jedes Mal, wenn Sie eine Excel-Arbeitsmappe in Visual Studio öffnen, für die das **Kennwort** aktiviert ist, werden Sie von Excel zur Eingabe des Kennworts aufgefordert. Wenn Sie Ihre Lösung erstellen, werden Sie erneut zur Eingabe des Kennworts aufgefordert, da das Dokument während des Builds geöffnet wird.

 Wenn Sie zum ersten Mal ein Word-Dokument in Visual Studio öffnen, bei dem das **Kennwort beim Öffnen** aktiviert ist, fordert Word Sie zur Eingabe des Kennworts auf. Nachdem Sie das Kennwort erfolgreich eingegeben haben, wird das **Kennwort beim Öffnen** aus dem Dokument entfernt, und beim Öffnen des Dokuments ist kein Kennwort mehr erforderlich. Wenn Sie möchten, dass für das Dokument in der Projekt Mappe ein Kennwort erforderlich ist, bevor es geöffnet werden kann, müssen Sie nach dem endgültigen Build und vor der Bereitstellung der Lösung das **Kennwort für das Öffnen** aktivieren.

## <a name="see-also"></a>Weitere Informationen
- [Dokument Schutz in Projektmappen auf Dokument Ebene](../vsto/document-protection-in-document-level-solutions.md)
- [Übersicht über Verwaltung von Informationsrechten und Erweiterungen von verwalteten Code](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Gewusst wie: zulassen, dass Code hinter Dokumenten mit eingeschränkten Berechtigungen ausgeführt wird](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)
- [Entwerfen und Erstellen von Office-Lösungen](../vsto/designing-and-creating-office-solutions.md)
