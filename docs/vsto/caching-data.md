---
title: Daten zwischenspeichern
description: Erfahren Sie, wie Sie Datenobjekte in einer Anpassung auf Dokument Ebene Zwischenspeichern können, damit auf die Daten offline zugegriffen werden kann, oder ohne Microsoft Office Word oder Excel zu öffnen.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data caching [Office development in Visual Studio], about caching data
- data [Office development in Visual Studio], caching
- data caching [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: db22378477daffd4562a9d60c6b30bc7b96e58e2
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96847870"
---
# <a name="cache-data"></a>Daten zwischenspeichern
  Sie können Datenobjekte in einer Anpassung auf Dokument Ebene Zwischenspeichern, damit auf die Daten offline zugegriffen werden kann, oder ohne Microsoft Office Word oder Microsoft Office Excel zu öffnen. Zum Zwischenspeichern eines Objekts muss das Objekt über einen Datentyp verfügen, der bestimmte Anforderungen erfüllt. Viele gängige Datentypen im .NET Framework erfüllen diese Anforderungen, einschließlich <xref:System.String> , <xref:System.Data.DataSet> und <xref:System.Data.DataTable> .

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Es gibt zwei Möglichkeiten, dem Daten Cache ein Objekt hinzuzufügen:

- Um dem Daten Cache ein Objekt hinzuzufügen, wenn die Projekt Mappe erstellt wird, wenden Sie das- <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> Attribut auf die Objekt Deklaration an. Weitere Informationen finden Sie unter Gewusst [wie: Zwischenspeichern von Daten zur Offline Verwendung oder auf einem Server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).

- Um ein Objekt Programm gesteuert zur Laufzeit zum Daten Cache hinzuzufügen, verwenden Sie die- `StartCaching` Methode eines-Host Elements, z. b. die- `ThisDocument` Klasse oder die- `ThisWorkbook` Klasse. Weitere Informationen finden Sie unter Gewusst [wie: Programm gesteuertes Zwischenspeichern einer Datenquelle in einem Office-Dokument](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md).

  Nachdem Sie dem Daten Cache ein Objekt hinzugefügt haben, können Sie auf die zwischengespeicherten Daten zugreifen und diese ändern, ohne Word oder Excel zu starten. Weitere Informationen finden Sie unter [zugreifen auf Daten in Dokumenten auf dem Server](../vsto/accessing-data-in-documents-on-the-server.md).

## <a name="requirements-for-data-objects-to-be-cached"></a>Anforderungen für Datenobjekte, die zwischengespeichert werden sollen
 Um ein Datenobjekt in der Projekt Mappe zwischenzuspeichern, muss das-Objekt die folgenden Anforderungen erfüllen:

- Ein öffentliches Lese-/Schreibfeld oder eine Eigenschaft eines Host Elements, z. b. die- `ThisDocument` Klasse oder die- `ThisWorkbook` Klasse.

- Es darf sich nicht um einen Indexer oder eine andere parametrisierte Eigenschaft handeln.

  Außerdem muss das Datenobjekt von der-Klasse serialisierbar sein <xref:System.Xml.Serialization.XmlSerializer> , was bedeutet, dass der Objekttyp über diese Merkmale verfügen muss:

- Ein öffentlicher Typ.

- Sie verfügen über einen öffentlichen Konstruktor ohne Parameter.

- Führen Sie keinen Code aus, der zusätzliche Sicherheits Berechtigungen erfordert.

- Nur öffentliche Lese-/Schreibeigenschaften verfügbar machen (andere Eigenschaften werden ignoriert).

- Mehrdimensionale Arrays nicht verfügbar machen (die übereingefügten Arrays werden akzeptiert).

- Es werden keine Schnittstellen von Eigenschaften und Feldern zurückgegeben.

- Nicht implementieren, <xref:System.Collections.IDictionary> Wenn eine Auflistung ist.

  Wenn Sie ein Datenobjekt Zwischenspeichern, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] serialisiert das Objekt in eine XML-Zeichenfolge, die in einem *benutzerdefinierten XML-Abschnitt* im Dokument gespeichert ist. Weitere Informationen finden Sie unter [Übersicht über benutzerdefinierte XML-Abschnitte](../vsto/custom-xml-parts-overview.md).

## <a name="cached-data-size-limits"></a>Größenbeschränkungen zwischen gespeicherter Daten
 Es gibt einige Einschränkungen für die Gesamtmenge der Daten, die Sie dem Daten Cache in einem Dokument hinzufügen können, und für die Größe jedes einzelnen Objekts im Daten Cache. Wenn Sie diese Grenzwerte überschreiten, wird die Anwendung möglicherweise unerwartet geschlossen, wenn die Daten im Daten Cache gespeichert werden.

 Um diese Grenzwerte zu vermeiden, befolgen Sie die folgenden Richtlinien:

- Fügen Sie dem Daten Cache kein Objekt hinzu, das größer als 10 MB ist.

- Fügen Sie dem Daten Cache in einem einzelnen Dokument nicht mehr als 100 MB Gesamtdaten hinzu.

  Dies sind ungefähre Werte. Die genauen Grenzwerte hängen von verschiedenen Faktoren ab, einschließlich des verfügbaren Arbeitsspeichers und der Anzahl der laufenden Prozesse.

## <a name="control-the-behavior-of-cached-objects"></a>Steuern des Verhaltens zwischen gespeicherter Objekte
 Um mehr Kontrolle über das Verhalten eines zwischengespeicherten Objekts zu erhalten, können Sie die- <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> Schnittstelle für den Typ des zwischengespeicherten Objekts implementieren. Beispielsweise können Sie diese Schnittstelle implementieren, wenn Sie steuern möchten, wie der Benutzer benachrichtigt wird, wenn das Objekt geändert wurde. Codebeispiele, in denen die Implementierung von veranschaulicht <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> wird, finden Sie `ControlCollection` in der-Klasse im Beispiel für dynamische Steuerelemente für Excel und Word Dynamic Controls Sample in [Office Development Samples und](../vsto/office-development-samples-and-walkthroughs.md)Exemplarische Vorgehensweisen.

## <a name="persist-changes-to-cached-data-in-password-protected-documents"></a>Beibehalten von Änderungen an zwischengespeicherten Daten in Kenn Wort geschützten Dokumenten
 Wenn Sie Datenobjekte in einem Dokument zwischenspeichern, das mit einem Kennwort geschützt ist, werden Änderungen an den zwischengespeicherten Daten nicht gespeichert. Sie können Änderungen an den zwischengespeicherten Daten speichern, indem Sie zwei Methoden überschreiben. Überschreiben Sie diese Methoden, um den Schutz vorübergehend zu entfernen, wenn das Dokument gespeichert wird, und wenden Sie den Schutz nach Abschluss des Speicher Vorgangs erneut an.

 Weitere Informationen finden Sie unter Gewusst [wie: Zwischenspeichern von Daten in einem Kenn Wort geschützten Dokument](../vsto/how-to-cache-data-in-a-password-protected-document.md).

## <a name="prevent-data-loss-when-adding-null-values-to-the-data-cache"></a>Vermeiden von Datenverlusten beim Hinzufügen von NULL-Werten zum Daten Cache
 Beim Hinzufügen von Objekten zum Daten Cache müssen alle zwischengespeicherten Objekte mit einem Wert ungleich **null** initialisiert werden, bevor das Dokument gespeichert und geschlossen wird. Wenn ein zwischengespeichertes Objekt einen **null** -Wert aufweist, wenn das Dokument gespeichert und geschlossen wird, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] werden alle zwischengespeicherten Objekte automatisch aus dem Daten Cache entfernt.

 Wenn Sie dem Daten Cache ein Objekt mit einem **null** -Wert hinzufügen, indem Sie das- <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> Attribut zur Entwurfszeit verwenden, können Sie die-Klasse verwenden, <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> um die zwischengespeicherten Datenobjekte zu initialisieren, bevor das Dokument geöffnet wird. Dies ist hilfreich, wenn Sie die zwischengespeicherten Daten auf einem Server ohne Word oder Excel initialisieren möchten, bevor das Dokument von einem Endbenutzer geöffnet wird. Weitere Informationen finden Sie unter [zugreifen auf Daten in Dokumenten auf dem Server](../vsto/accessing-data-in-documents-on-the-server.md).

## <a name="see-also"></a>Siehe auch
- [Gewusst wie: Zwischenspeichern von Daten zur Offline Verwendung oder auf einem Server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)
- [Vorgehensweise: Programm gesteuertes Zwischenspeichern einer Datenquelle in einem Office-Dokument](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)
- [Vorgehensweise: Zwischenspeichern von Daten in einem Kenn Wort geschützten Dokument](../vsto/how-to-cache-data-in-a-password-protected-document.md)
- [Exemplarische Vorgehensweise: Erstellen einer Master Detail Beziehung mithilfe eines zwischengespeicherten Datasets](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md)
