---
title: Programm gesteuertes Zwischenspeichern von Datenquellen in Office-Dokumenten
description: Erfahren Sie, wie Sie dem Daten Cache in einem Dokument Programm gesteuert ein Datenobjekt hinzufügen können, indem Sie die StartCaching-Methode eines Host Elements aufrufen.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], data
- datasets [Office development in Visual Studio], caching
- StartCaching method
- data caching [Office development in Visual Studio], programmatically
- data [Office development in Visual Studio], caching
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d1e66b587a149c02059e549fb20a5293f296a4a8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99968943"
---
# <a name="how-to-programmatically-cache-a-data-source-in-an-office-document"></a>Vorgehensweise: Programm gesteuertes Zwischenspeichern einer Datenquelle in einem Office-Dokument
  Sie können dem Daten Cache in einem Dokument Programm gesteuert ein Datenobjekt hinzufügen, indem Sie die- `StartCaching` Methode eines-Host Elements aufrufen, <xref:Microsoft.Office.Tools.Word.Document> z <xref:Microsoft.Office.Tools.Excel.Workbook> . b <xref:Microsoft.Office.Tools.Excel.Worksheet> ., oder. Entfernen Sie ein Datenobjekt aus dem Daten Cache, indem Sie die- `StopCaching` Methode eines-Host Elements aufrufen.

 Die `StartCaching` -Methode und die- `StopCaching` Methode sind beide privat, aber Sie werden in IntelliSense angezeigt.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Wenn Sie die- `StartCaching` Methode verwenden, um dem Daten Cache ein Datenobjekt hinzuzufügen, muss das Datenobjekt nicht mit dem-Attribut deklariert werden <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> . Das Datenobjekt muss jedoch bestimmte Anforderungen erfüllen, die dem Daten Cache hinzugefügt werden sollen. Weitere Informationen finden Sie unter zwischen [Speichern von Daten](../vsto/caching-data.md).

## <a name="to-programmatically-cache-a-data-object"></a>So speichern Sie ein Datenobjekt Programm gesteuert zwischen

1. Deklarieren Sie das Datenobjekt auf Klassenebene, nicht innerhalb einer Methode. In diesem Beispiel wird davon ausgegangen, dass Sie einen mit dem Namen deklarieren <xref:System.Data.DataSet> `dataSet1` , den Sie Programm gesteuert zwischenspeichern möchten.

     [!code-csharp[Trin_VstcoreDataExcel#12](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#12)]
     [!code-vb[Trin_VstcoreDataExcel#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#12)]

2. Instanziieren Sie das Datenobjekt, und wählen Sie dann die- `StartCaching` Methode des Dokuments oder der Arbeitsblatt Instanz aus, und übergeben Sie den Namen des Datenobjekts.

     [!code-csharp[Trin_VstcoreDataExcel#13](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#13)]
     [!code-vb[Trin_VstcoreDataExcel#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#13)]

## <a name="to-stop-caching-a-data-object"></a>So verhindern Sie das Zwischenspeichern eines Datenobjekts

1. Ruft die `StopCaching` -Methode des Dokuments oder der Arbeitsblatt Instanz auf und übergibt den Namen des Datenobjekts. In diesem Beispiel wird davon ausgegangen, dass Sie über einen <xref:System.Data.DataSet> Namen verfügen `dataSet1` , den Sie zwischenspeichern möchten.

     [!code-csharp[Trin_VstcoreDataExcel#14](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#14)]
     [!code-vb[Trin_VstcoreDataExcel#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#14)]

    > [!NOTE]
    > Ruft nicht `StopCaching` vom-Ereignishandler für das- `Shutdown` Ereignis eines Dokuments oder Arbeitsblatts auf. Wenn das- `Shutdown` Ereignis ausgelöst wird, ist es zu spät, den Daten Cache zu ändern. Weitere Informationen zum `Shutdown` Ereignis finden Sie unter [Ereignisse in Office-Projekten](../vsto/events-in-office-projects.md).

## <a name="see-also"></a>Weitere Informationen

- [Daten zwischenspeichern](../vsto/caching-data.md)
- [Gewusst wie: Zwischenspeichern von Daten zur Offline Verwendung oder auf einem Server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)
- [Vorgehensweise: Zwischenspeichern von Daten in einem Kenn Wort geschützten Dokument](../vsto/how-to-cache-data-in-a-password-protected-document.md)
- [Zugreifen auf Daten in Dokumenten auf dem Server](../vsto/accessing-data-in-documents-on-the-server.md)
- [Speichern von Daten](../data-tools/save-data-back-to-the-database.md)
