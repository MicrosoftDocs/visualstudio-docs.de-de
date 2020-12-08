---
title: 'Gewusst wie: Zwischenspeichern von Daten zur Offline Verwendung oder auf einem Server'
description: Markieren Sie ein Datenelement, das im Dokument zwischengespeichert werden soll, damit es offline verfügbar ist. Dies ermöglicht es, dass die Daten im Dokument durch anderen Code bearbeitet werden können.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data caching [Office development in Visual Studio], server use
- Office applications [Office development in Visual Studio], data
- datasets [Office development in Visual Studio], caching
- offline data [Office development in Visual Studio]
- data [Office development in Visual Studio], caching
- data caching [Office development in Visual Studio], offline use
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cefd4cd132e75f8ff622c8e0d809d317242c10f5
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96844321"
---
# <a name="how-to-cache-data-for-use-offline-or-on-a-server"></a>Gewusst wie: Zwischenspeichern von Daten zur Offline Verwendung oder auf einem Server
  Sie können ein Datenelement markieren, das im Dokument zwischengespeichert werden soll, damit es offline verfügbar ist. Dies ermöglicht es auch, dass die Daten im Dokument durch anderen Code manipuliert werden, wenn das Dokument auf einem Server gespeichert wird.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Sie können ein Datenelement markieren, das zwischengespeichert werden soll, wenn das Datenelement im Code deklariert wird, oder wenn Sie einen verwenden <xref:System.Data.DataSet> , indem Sie im **Eigenschaften** Fenster eine Eigenschaft festlegen. Wenn Sie ein Datenelement Zwischenspeichern, das keine <xref:System.Data.DataSet> oder ist <xref:System.Data.DataTable> , müssen Sie sicherstellen, dass es die Kriterien für die Zwischenspeicherung im Dokument erfüllt. Weitere Informationen finden Sie unter zwischen [Speichern von Daten](../vsto/caching-data.md).

> [!NOTE]
> Datasets, die mit Visual Basic erstellt werden, die als **zwischengespeicherte** und **widervents** gekennzeichnet sind (einschließlich Datasets, die aus dem **Datenquellen** Fenster oder der **Toolbox** gezogen werden, für die die **CacheInDocument** -Eigenschaft auf **true** festgelegt ist), haben einen Unterstrich mit dem Namen im Cache. Wenn Sie z. b. ein Dataset erstellen **und ihm einen** Namen geben, wird der <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> Name im Cache **_Customers** . Wenn Sie <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> für den Zugriff auf dieses zwischengespeicherte Element verwenden, müssen Sie **_Customers** anstelle von **Kunden** angeben.

### <a name="to-cache-data-in-the-document-using-code"></a>So speichern Sie Daten im Dokument mithilfe von Code zwischen

1. Deklarieren Sie ein öffentliches Feld oder eine öffentliche Eigenschaft für das Datenelement als Member einer Host Element Klasse in Ihrem Projekt, z `ThisDocumen` . b. die t-Klasse in einem Word-Projekt oder die- `ThisWorkbook` Klasse in einem Excel-Projekt.

2. Wenden Sie das- <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> Attribut auf das-Element an, um das Datenelement zu kennzeichnen, das im Daten Cache des Dokuments gespeichert werden soll. Im folgenden Beispiel wird dieses Attribut auf eine Feld Deklaration für eine angewendet <xref:System.Data.DataSet> .

     [!code-csharp[Trin_VstcoreDataExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#11)]
     [!code-vb[Trin_VstcoreDataExcel#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#11)]

3. Fügen Sie Code hinzu, um eine Instanz des Datenelements zu erstellen und ggf. aus der Datenbank zu laden.

     Das Datenelement wird nur bei der ersten Erstellung geladen. anschließend bleibt der Cache im Dokument erhalten, und Sie müssen weiteren Code schreiben, um ihn zu aktualisieren.

### <a name="to-cache-a-dataset-in-the-document-by-using-the-properties-window"></a>So speichern Sie ein DataSet im Dokument mithilfe der Eigenschaftenfenster

1. Fügen Sie das Dataset zum Projekt hinzu, indem Sie Tools im Visual Studio-Designer verwenden, z. b. durch Hinzufügen einer Datenquelle zum Projekt mithilfe des **Datenquellen** Fensters.

2. Erstellen Sie eine Instanz des Datasets, wenn Sie noch nicht über eine Instanz verfügen, und wählen Sie im Designer die Instanz aus.

3. Legen Sie im Fenster **Eigenschaften** die **CacheInDocument** -Eigenschaft auf **true** fest.

     Weitere Informationen finden Sie unter [Eigenschaften in Office-Projekten](../vsto/properties-in-office-projects.md).

4. Legen Sie im Fenster **Eigenschaften** die **modifizierereigenschaft** auf **Public** fest (Standardmäßig ist Sie **intern**).

## <a name="see-also"></a>Siehe auch
- [Daten zwischenspeichern](../vsto/caching-data.md)
- [Vorgehensweise: Programm gesteuertes Zwischenspeichern einer Datenquelle in einem Office-Dokument](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)
- [Vorgehensweise: Zwischenspeichern von Daten in einem Kenn Wort geschützten Dokument](../vsto/how-to-cache-data-in-a-password-protected-document.md)
- [Zugreifen auf Daten in Dokumenten auf dem Server](../vsto/accessing-data-in-documents-on-the-server.md)
- [Speichern von Daten](../data-tools/save-data-back-to-the-database.md)
