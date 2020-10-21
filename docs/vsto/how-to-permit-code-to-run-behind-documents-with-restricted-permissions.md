---
title: Zulassen, dass Code hinter Dokumenten mit eingeschränkten Berechtigungen ausgeführt wird
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Information Rights Management [Office development in Visual Studio]
- permissions [Office development in Visual Studio]
- IRM [Office development in Visual Studio]
- code [Office development in Visual Studio], running behind restricted documents
- documents [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio, restricted permissions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 14c468a806160fd31c84b164a4b995f904e71fc6
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2020
ms.locfileid: "92298489"
---
# <a name="how-to-permit-code-to-run-behind-documents-with-restricted-permissions"></a>Gewusst wie: zulassen, dass Code hinter Dokumenten mit eingeschränkten Berechtigungen ausgeführt wird
  Sie können die Funktion Information Rights Management (unm) von Microsoft Office verwenden, um die Berechtigungen für ein Dokument oder eine Arbeitsmappe einzuschränken. Standardmäßig darf der Code hinter einem eingeschränkten Microsoft Office Word-Dokument oder Microsoft Office Excel-Arbeitsmappe nicht ausgeführt werden. Sie können den Standardwert ändern, sodass die Erweiterungen des verwalteten Codes auf das Objektmodell zugreifen können und die Lösung funktioniert.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Sie müssen der Autor des Dokuments oder der Arbeitsmappe sein oder über Vollzugriff verfügen, um die Berechtigungseinstellungen ändern zu können.

## <a name="to-permit-code-to-run-behind-documents-with-restricted-permissions"></a>So lassen Sie zu, dass Code hinter Dokumenten mit eingeschränkten Berechtigungen ausgeführt wird

1. Öffnen Sie das Dokument oder die Arbeitsmappe in Word oder Excel.

2. Klicken Sie auf die Registerkarte **Datei** , zeigen Sie auf **vorbereiten**, zeigen Sie auf **Berechtigung einschränken**, und klicken Sie dann auf **Eingeschränkter Zugriff**.

   > [!NOTE]
   > Bei der ersten Verwendung werden Sie aufgefordert, den Windows Rights Management-Client zu installieren. Nachdem Sie den-Client installiert haben, müssen Sie die Schritte möglicherweise wiederholen.

3. Wählen Sie im Dialogfeld **Berechtigung** die Option **Berechtigung einschränken für dieses Dokument**aus, und klicken Sie dann auf **Weitere Optionen**.

4. Wählen Sie unter **zusätzliche Berechtigungen für Benutzer**Programm gesteuert auf **Inhalt zugreifen**aus.

   Word oder Excel ermöglicht den programmgesteuerten Zugriff auf das Objektmodell.

## <a name="see-also"></a>Weitere Informationen
- [Übersicht über Verwaltung von Informationsrechten und Erweiterungen von verwalteten Code](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Dokument Schutz in Projektmappen auf Dokument Ebene](../vsto/document-protection-in-document-level-solutions.md)
- [Kenn Wort Schutz für Office-Dokumente](../vsto/password-protection-on-office-documents.md)
- [Entwerfen und Erstellen von Office-Lösungen](../vsto/designing-and-creating-office-solutions.md)
- [Sichere Office-Lösungen](../vsto/securing-office-solutions.md)
- [Bereitstellen einer Office-Projekt Mappe](../vsto/deploying-an-office-solution.md)
