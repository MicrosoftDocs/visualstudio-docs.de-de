---
title: 'Gewusst wie: Programm gesteuertes Öffnen von Textdateien als Arbeitsmappen'
description: Erfahren Sie, wie Sie Visual Studio verwenden können, um eine Textdatei Programm gesteuert als Microsoft Excel-Arbeitsmappe zu öffnen.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, opening text files as
- text [Office development in Visual Studio], text files
- text files, opening as workbooks
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 47582718128fc9818bb42571e3f33c0190a32d9e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888744"
---
# <a name="how-to-programmatically-open-text-files-as-workbooks"></a>Gewusst wie: Programm gesteuertes Öffnen von Textdateien als Arbeitsmappen
  Sie können eine Textdatei als-Arbeitsmappe öffnen. Sie müssen den Namen der Textdatei übergeben, die Sie öffnen möchten. Sie können mehrere optionale Parameter angeben, z. b. die Zeilennummer, mit der die Verarbeitung beginnen soll, und das Spalten Format der Daten in der Datei.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="example"></a>Beispiel
 [!code-csharp[Trin_VstcoreExcelAutomation#80](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#80)]
 [!code-vb[Trin_VstcoreExcelAutomation#80](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#80)]

## <a name="compile-the-code"></a>Kompilieren des Codes
 Für dieses Beispiel sind die folgenden Komponenten erforderlich:

- Eine durch Trennzeichen getrennte Textdatei `Test.txt` mit dem Namen, die mindestens drei Textzeilen enthält.

- Die Textdatei `Test.txt` , die auf Laufwerk C gespeichert werden soll.

## <a name="see-also"></a>Weitere Informationen
- [Arbeiten mit Arbeitsmappen](../vsto/working-with-workbooks.md)
- [Gewusst wie: Programm gesteuertes Öffnen von Arbeitsmappen](../vsto/how-to-programmatically-open-workbooks.md)
- [Vorgehensweise: Programm gesteuertes Erstellen neuer Arbeitsmappen](../vsto/how-to-programmatically-create-new-workbooks.md)
- [Vorgehensweise: Programm gesteuertes Speichern von Arbeitsmappen](../vsto/how-to-programmatically-save-workbooks.md)
- [Vorgehensweise: Programm gesteuertes schließen von Arbeitsmappen](../vsto/how-to-programmatically-close-workbooks.md)
- [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)
