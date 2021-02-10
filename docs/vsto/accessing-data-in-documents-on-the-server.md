---
title: Zugreifen auf Daten in Dokumenten auf dem Server
description: Erfahren Sie, wie Sie für die Daten in einer Anpassung auf Dokument Ebene programmieren können, ohne das Objektmodell von Microsoft Office Word oder Microsoft Office Excel verwenden zu müssen.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], accessing on server
- data access [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1c610bdc33564e3e211d1ec5aab943af4eec49d1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965797"
---
# <a name="access-data-in-documents-on-the-server"></a>Zugreifen auf Daten in Dokumenten auf dem Server
  Sie können für die Daten in einer Anpassung auf Dokument Ebene programmieren, ohne das Objektmodell von Microsoft Office Word oder Microsoft Office Excel verwenden zu müssen. Dies bedeutet, dass Sie auf Daten zugreifen können, die in einem Dokument auf einem Server enthalten sind, auf dem Word oder Excel nicht installiert ist. Beispielsweise kann der Code auf einem Server (z. b. auf einer [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] Seite) die Daten in einem Dokument anpassen und das angepasste Dokument an einen Endbenutzer senden. Wenn der Endbenutzer das Dokument öffnet, bindet der Daten Bindungs Code in der Projektmappenassembly die angepassten Daten an das Dokument. Dies ist möglich, da die Daten im Dokument von der Benutzeroberfläche getrennt sind. Weitere Informationen finden Sie unter [zwischengespeicherte Daten in Anpassungen auf Dokument Ebene](../vsto/cached-data-in-document-level-customizations.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="cache-data-for-use-on-a-server"></a>Zwischenspeichern von Daten für die Verwendung auf einem Server
 Um ein Datenobjekt in einem Dokument zwischenzuspeichern, markieren Sie es zur Entwurfszeit mit dem- <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> Attribut, oder verwenden Sie die- `StartCaching` Methode eines Host Elements zur Laufzeit. Wenn Sie ein Datenobjekt in einem Dokument zwischenspeichern, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] serialisiert das Objekt in eine XML-Zeichenfolge, die im Dokument gespeichert ist. Objekte müssen bestimmte Anforderungen erfüllen, damit Sie für die Zwischenspeicherung geeignet sind. Weitere Informationen finden Sie unter zwischen [Speichern von Daten](../vsto/caching-data.md).

 Der Server seitige Code kann beliebige Datenobjekte im Daten Cache bearbeiten. Steuerelemente, die an zwischengespeicherte Daten Instanzen gebunden sind, werden mit der Benutzeroberfläche synchronisiert, sodass alle serverseitigen Änderungen, die an den Daten vorgenommen werden, automatisch angezeigt werden, wenn das Dokument auf dem Client geöffnet wird.

## <a name="access-data-in-the-cache"></a>Zugreifen auf Daten im Cache
 Sie können auf Daten im Cache von Anwendungen außerhalb von Office zugreifen, z. b. aus einer Konsolenanwendung, einer Windows Forms Anwendung oder einer Webseite. Die Anwendung, die auf die zwischengespeicherten Daten zugreift, muss voll vertrauenswürdig sein. eine Webanwendung, die über teilweise Vertrauenswürdigkeit verfügt, kann keine Daten einfügen, Abrufen oder ändern, die in einem Office-Dokument zwischengespeichert werden.

 Auf den Daten Cache kann über eine Hierarchie von Auflistungen zugegriffen werden, die von der-Eigenschaft der-Klasse verfügbar gemacht werden <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> :

- Die- <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> Eigenschaft gibt ein-Objekt zurück <xref:Microsoft.VisualStudio.Tools.Applications.CachedData> , das alle zwischengespeicherten Daten in einer Anpassung auf Dokument Ebene enthält.

- Jedes <xref:Microsoft.VisualStudio.Tools.Applications.CachedData> enthält mindestens ein <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem>-Objekt. Eine <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> enthält alle zwischengespeicherten Datenobjekte, die in einer einzelnen Klasse definiert sind.

- Jedes <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> enthält mindestens ein <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem>-Objekt. Ein <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> stellt ein einzelnes zwischengespeichertes Datenobjekt dar.

  Im folgenden Codebeispiel wird veranschaulicht, wie Sie in der- `Sheet1` Klasse eines Excel-Arbeitsmappenprojekts auf eine zwischengespeicherte Zeichenfolge zugreifen. Dieses Beispiel ist Teil eines größeren Beispiels, das für die-Methode bereitgestellt wird <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A> .

  [!code-csharp[Trin_ServerDocument#12](../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs#12)]
  [!code-vb[Trin_ServerDocument#12](../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb#12)]

## <a name="modify-data-in-the-cache"></a>Ändern von Daten im Cache
 Zum Ändern eines zwischengespeicherten Datenobjekts führen Sie in der Regel die folgenden Schritte aus:

1. Deserialisieren Sie die XML-Darstellung des zwischengespeicherten Objekts in eine neue Instanz des-Objekts. Sie können auf den XML-Code zugreifen, indem Sie die- <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> Eigenschaft des verwenden <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> , das das zwischengespeicherte Datenobjekt darstellt.

2. Nehmen Sie die Änderungen an dieser Kopie vor.

3. Serialisieren Sie das geänderte Objekt zurück in den Daten Cache, indem Sie eine der folgenden Optionen verwenden:

    - Wenn Sie die Änderungen automatisch serialisieren möchten, verwenden Sie die- <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> Methode. Diese Methode verwendet das **DiffGram** -Format für die Serialisierung von <xref:System.Data.DataSet> <xref:System.Data.DataTable> -,-und typisierten DataSet-Objekten im Daten Cache. Durch das **DiffGram** -Format wird sichergestellt, dass Änderungen am Daten Cache in einem Offline Dokument ordnungsgemäß an den Server gesendet werden.

    - Wenn Sie Ihre eigene Serialisierung für Änderungen an zwischengespeicherten Daten durchführen möchten, können Sie direkt in die- <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> Eigenschaft schreiben. Geben Sie das **DiffGram** -Format an, wenn Sie einen <xref:System.Data.Common.DataAdapter> zum Aktualisieren einer Datenbank mit Änderungen verwenden, die an den Daten in einem <xref:System.Data.DataSet> <xref:System.Data.DataTable> typisierten DataSet, oder vorgenommen werden. Andernfalls aktualisiert die <xref:System.Data.Common.DataAdapter> Datenbank, indem neue Zeilen hinzugefügt werden, anstatt vorhandene Zeilen zu ändern.

### <a name="modify-data-without-deserializing-the-current-value"></a>Daten ändern, ohne den aktuellen Wert zu deserialisieren
 In einigen Fällen möchten Sie möglicherweise den Wert des zwischengespeicherten Objekts ändern, ohne zuerst den aktuellen Wert zu deserialisieren. Dies ist z. b. der Fall, wenn Sie den Wert eines Objekts ändern, das über einen einfachen Typ verfügt, z. b. eine Zeichenfolge oder eine ganze Zahl, oder wenn Sie ein zwischengespeichertes <xref:System.Data.DataSet> in einem Dokument auf einem Server initialisieren. In diesen Fällen können Sie die-Methode verwenden, <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> ohne zuerst den aktuellen Wert des zwischengespeicherten Objekts zu deserialisieren.

 Im folgenden Codebeispiel wird veranschaulicht, wie der Wert einer zwischengespeicherten Zeichenfolge in der- `Sheet1` Klasse eines Excel-Arbeitsmappenprojekts geändert wird. Dieses Beispiel ist Teil eines größeren Beispiels, das für die-Methode bereitgestellt wird <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A> .

 [!code-csharp[Trin_ServerDocument#11](../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs#11)]
 [!code-vb[Trin_ServerDocument#11](../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb#11)]

### <a name="modify-null-values-in-the-data-cache"></a>Ändern von NULL-Werten im Daten Cache
 Der Daten Cache speichert keine Objekte, die den Wert **null** aufweisen, wenn das Dokument gespeichert und geschlossen wird. Diese Einschränkung hat mehrere Konsequenzen, wenn Sie zwischengespeicherte Daten ändern:

- Wenn Sie ein Objekt im Daten Cache auf den Wert **null** festlegen, werden alle Objekte im Daten Cache beim Öffnen des Dokuments automatisch auf **null** festgelegt, und der gesamte Daten Cache wird gelöscht, wenn das Dokument gespeichert und geschlossen wird. Das heißt, alle zwischengespeicherten Objekte werden aus dem Daten Cache entfernt, und die Auflistung ist <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> leer.

- Wenn Sie eine Projekt Mappe mit **null** -Objekten im Daten Cache erstellen und diese Objekte mithilfe der-Klasse initialisieren möchten <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> , bevor das Dokument zum ersten Mal geöffnet wird, müssen Sie sicherstellen, dass Sie alle Objekte im Daten Cache initialisieren. Wenn Sie nur einige der Objekte initialisieren, werden alle Objekte beim Öffnen des Dokuments auf **null** festgelegt, und der gesamte Daten Cache wird gelöscht, wenn das Dokument gespeichert und geschlossen wird.

## <a name="access-typed-datasets-in-the-cache"></a>Zugreifen auf typisierte Datasets im Cache
 Wenn Sie auf die Daten in einem typisierten DataSet sowohl aus einer Office-Projekt Mappe als auch aus einer Anwendung außerhalb von Office zugreifen möchten, z. b. eine Windows Forms Anwendung oder ein- [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] Projekt, müssen Sie das typisierte DataSet in einer separaten Assembly definieren, auf die in beiden Projekten verwiesen wird. Wenn Sie das typisierte DataSet mit dem Assistenten zum Konfigurieren von **Datenquellen** oder dem **DataSet-Designer** jedem Projekt hinzufügen, werden die typisierten Datasets in den beiden Projekten vom .NET Framework als verschiedene Typen behandelt. Weitere Informationen zum Erstellen von typisierten Datasets finden Sie unter [Erstellen und Konfigurieren von Datasets in Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md).

## <a name="see-also"></a>Weitere Informationen

- [Zugreifen auf Daten in Dokumenten auf dem Server](../vsto/accessing-data-in-documents-on-the-server.md)
- [Zwischengespeicherte Daten in Anpassungen auf Dokument Ebene](../vsto/cached-data-in-document-level-customizations.md)