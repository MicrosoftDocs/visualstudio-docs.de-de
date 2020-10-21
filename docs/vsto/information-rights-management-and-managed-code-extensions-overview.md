---
title: Verwaltung von Informationsrechten & Erweiterungen durch verwalteten Code
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Information Rights Management [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- IRM [Office development in Visual Studio]
- documents [Office development in Visual Studio], restricted permissions
- rights management [Office development in Visual Studio]
- Office documents [Office development in Visual Studio, restricted permissions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 06b55855184aaef57ec0a3425abed7d235ec837b
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2020
ms.locfileid: "92298073"
---
# <a name="information-rights-management-and-managed-code-extensions-overview"></a>Übersicht über Verwaltung von Informationsrechten und Erweiterungen von verwalteten Code
  Microsoft Office Word und Microsoft Office Excel enthalten Informationen Rights Management (unm), eine Funktion, mit der Sie verhindern können, dass nicht autorisierte Personen vertrauliche Informationen anzeigen oder ändern. Ausführliche Informationen über die Funktionsweise von Informationen Rights Management finden Sie in der Hilfe zu einer bestimmten Office-Anwendung.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="run-code-behind-documents-with-restricted-permissions"></a>Ausführen von Code hinter Dokumenten mit eingeschränkten Berechtigungen
 Wenn Ihre Projekt Mappe ein Dokument oder eine Arbeitsmappe enthält, die die Verwendung von "unm" enthält, können Word und Excel standardmäßig keinen Code ausführen. Wenn Sie der Autor des Dokuments sind oder über Vollzugriff verfügen, können Sie die Standardeinstellung so ändern, dass die Lösung funktioniert. Weitere Informationen finden Sie unter Gewusst [wie: zulassen, dass Code hinter Dokumenten mit eingeschränkten Berechtigungen ausgeführt](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)wird.

 Mit "unm" <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> wird verhindert, dass die im Dokument zwischengespeicherten Daten mithilfe von abgerufen oder bearbeitet werden.

## <a name="end-users-to-restrict-permissions-to-documents-that-use-managed-code-extensions"></a>Endbenutzer zum Einschränken von Berechtigungen für Dokumente, die Erweiterungen durch verwalteten Code verwenden
 Jeder Benutzer, der über Vollzugriff auf das Dokument oder die Arbeitsmappe in der Lösung verfügt, kann die Berechtigungen mithilfe von "unm" einschränken. Wenn z. b. ein Endbenutzer in der Buchhaltungsabteilung eine Lösung verwendet, die automatisch ein Arbeitsblatt mit Daten aus einer Datenbank auffüllt, möchte dieser Benutzer möglicherweise nur den Zugriff für Personen in seiner Abteilung zulassen und Lesezugriff für andere Benutzer gewähren. Wenn der Benutzer die eingeschränkten Berechtigungen hinzufügt, kann der Code hinter dem Arbeitsblatt standardmäßig nicht ausgeführt werden, und das Arbeitsblatt wird nicht mit Daten aufgefüllt.

 Um das Problem zu beheben, muss ein Benutzer mit Vollzugriff auf das Dokument oder die Arbeitsmappe die Standard Berechtigungseinstellungen ändern, um den programmgesteuerten Zugriff auf das Objektmodell zuzulassen. Weitere Informationen finden Sie unter Gewusst [wie: zulassen, dass Code hinter Dokumenten mit eingeschränkten Berechtigungen ausgeführt](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)wird.

## <a name="see-also"></a>Weitere Informationen
- [Dokument Schutz in Projektmappen auf Dokument Ebene](../vsto/document-protection-in-document-level-solutions.md)
- [Kenn Wort Schutz für Office-Dokumente](../vsto/password-protection-on-office-documents.md)
- [Sichere Office-Lösungen](../vsto/securing-office-solutions.md)
- [Bereitstellen einer Office-Projekt Mappe](../vsto/deploying-an-office-solution.md)
- [Entwerfen und Erstellen von Office-Lösungen](../vsto/designing-and-creating-office-solutions.md)
