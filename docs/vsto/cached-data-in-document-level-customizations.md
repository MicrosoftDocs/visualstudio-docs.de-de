---
title: Zwischengespeicherte Daten in Anpassungen auf Dokument Ebene
description: Erfahren Sie, wie Visual Studio die Daten in Anpassungen auf Dokument Ebene von der Sicht trennt, indem Sie die Speicherung von Daten als Daten Cache ermöglichen.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data islands [Office development in Visual Studio]
- view [Office development in Visual Studio]
- caching data [Office development in Visual Studio], about caching data
- data caching [Office development in Visual Studio], about data caching
- data [Office development in Visual Studio], cache
- data [Office development in Visual Studio], document-level solutions
- document-level customizations [Office development in Visual Studio], data model
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: be4229c179ec6c5640ab612d28991fe476363a53
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96847896"
---
# <a name="cached-data-in-document-level-customizations"></a>Zwischengespeicherte Daten in Anpassungen auf Dokument Ebene
  Das Hauptziel der Anpassungen auf Dokument Ebene besteht darin, Daten von der Sicht in Office-Dokumenten zu trennen. Daten bezieht sich auf die im Dokument gespeicherten Informationen, einschließlich Zahlen und Text. Die Ansicht bezieht sich auf die Benutzeroberfläche und das Objektmodell von Microsoft Office Word und Microsoft Office Excel.

 Visual Studio trennt die Daten von der Sicht in Anpassungen auf Dokument Ebene, indem es ermöglicht wird, dass Daten als *Daten Insel* eingebettet werden, auch als *Daten Cache* bezeichnet. Sie können die Daten direkt lesen oder ändern, ohne Word oder Excel zu starten. Dies ist hilfreich, wenn Sie Daten in Dokumenten auf einem Server ändern müssen, auf dem Microsoft Office nicht installiert ist. Word und Excel sind für die Verwendung in Client Umgebungen vorgesehen. Sie sind nicht für die Durchführung auf einem Server konzipiert.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Weitere Informationen zu Anpassungen auf Dokument Ebene finden Sie unter Übersicht über die Entwicklung von Office-Projektmappen [&#40;VSTO-&#41;](../vsto/office-solutions-development-overview-vsto.md) und [Architektur von Anpassungen auf Dokument Ebene](../vsto/architecture-of-document-level-customizations.md).

## <a name="understand-the-cached-data-programming-model"></a>Grundlegendes zum zwischengespeicherten Daten Programmiermodell
 Die Daten Insel kann ein beliebiges Objekt in der Projekt Mappe enthalten, das bestimmte Anforderungen erfüllt. Zu diesen Objekten gehören <xref:System.Data.DataSet> -Objekte, <xref:System.Data.DataTable> -Objekte und alle anderen Objekte, die von der-Klasse serialisiert werden können <xref:System.Xml.Serialization.XmlSerializer> . Weitere Informationen finden Sie unter zwischen [Speichern von Daten](../vsto/caching-data.md).

 Um die Ansicht für die zwischengespeicherten Daten bereitzustellen, können Sie Windows Forms Steuerelemente und *Host Steuerelemente* im Dokument an Objekte in der Daten Insel binden. Bei der Datenbindung zwischen der Daten Insel und den Daten gebundenen Steuerelementen werden die beiden synchronisiert. Sie können auch Validierungscode zu den Daten hinzufügen, die unabhängig von den Steuerelementen sind. Weitere Informationen finden Sie unter [Binden von Daten an Steuerelemente in Office](../vsto/binding-data-to-controls-in-office-solutions.md)-Projektmappen.

 Host Steuerelemente sind erweiterte Versionen von systemeigenen Objekten in den Excel-und Word-Objekt Modellen. Im Gegensatz zu den systemeigenen Objekten können Host Steuerelemente direkt an verwaltete Datenobjekte gebunden werden. Weitere Informationen finden Sie unter [Übersicht über Host Elemente und Host Steuerelemente](../vsto/host-items-and-host-controls-overview.md) und [Windows Forms Steuerelemente in der Übersicht über Office-Dokumente](../vsto/windows-forms-controls-on-office-documents-overview.md).

## <a name="access-cached-data-on-the-server"></a>Zugreifen auf zwischengespeicherte Daten auf dem Server
 Wenn Sie in einem Dokument auf zwischengespeicherte Daten zugreifen möchten, können Sie die- <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> Klasse verwenden. Diese Klasse ist Teil von [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] und kann auf einem Server ohne Ausführen von Excel oder Word verwendet werden. Wenn der Benutzer das Dokument öffnet, nachdem Sie die zwischengespeicherten Daten geändert haben, werden alle Steuerelemente, die an die Daten gebunden sind, automatisch mit den Änderungen synchronisiert, und dem Benutzer werden die aktualisierten Daten angezeigt. Weitere Informationen finden Sie unter [zugreifen auf Daten in Dokumenten auf dem Server](../vsto/accessing-data-in-documents-on-the-server.md).

 Excel und Word sind nicht zum Schreiben in die Daten auf dem Server erforderlich, sondern nur zum Anzeigen auf dem Client. Excel und Word müssen nicht einmal auf dem Server installiert werden. Dies ermöglicht eine verbesserte Skalierbarkeit und die Möglichkeit, eine schnelle Batch Verarbeitung von Dokumenten auszuführen, die Dateninseln enthalten.

## <a name="data-caching-for-offline-use"></a>Zwischenspeichern von Daten für die Offline Verwendung
 Das Speichern von Daten auf der Daten Insel ermöglicht Offline Szenarien. Wenn ein Benutzer zum ersten Mal ein Dokument öffnet oder das Dokument vom Server anfordert, wird die Daten Insel mit den neuesten Daten gefüllt. Die Daten Insel wird im Dokument zwischengespeichert und ist dann offline verfügbar. Der Benutzer (und Ihr Code) kann die Daten bearbeiten, obwohl keine Live Verbindung verfügbar ist. Wenn der Benutzer erneut eine Verbindung herstellt, können die Änderungen an den Daten an eine Serverdaten Quelle zurückgegeben werden.

## <a name="cached-data-and-custom-xml-parts-compared"></a>Vergleich zwischen zwischengespeicherten Daten und benutzerdefinierten XML-teilen
 Benutzerdefinierte XML-Teile wurden im 2007-Microsoft Office System als Möglichkeit eingeführt, beliebige XML-Elemente in einem Dokument zu speichern. Obwohl benutzerdefinierte XML-Abschnitte in vielen der gleichen Szenarien wie der Daten Cache nützlich sind, gibt es einige Unterschiede zwischen der Daten Insel und den benutzerdefinierten XML-Komponenten. Weitere Informationen zu benutzerdefinierten XML-Elementen finden Sie unter [Übersicht über benutzerdefinierte XML-Abschnitte](../vsto/custom-xml-parts-overview.md).

 In der folgenden Tabelle sind einige der Unterschiede und Ähnlichkeiten aufgeführt.

|Frage/Merkmal|Datencache|Benutzerdefinierte XML-Elemente|
|-|----------------|----------------------|
|Welche Office-Anwendungen können diese verwenden?|Anpassungen auf Dokument Ebene für die folgenden Anwendungen:<br /><br /> -Excel<br />-Word|Lösungen auf Dokument-und Anwendungsebene für die folgenden Anwendungen:<br /><br /> -Excel<br />-PowerPoint<br />-Word|
|Welche Arten von Daten können gespeichert werden?|Ein beliebiges öffentliches Objekt in der Anpassungsassembly, das bestimmte Anforderungen erfüllt. Weitere Informationen finden Sie unter zwischen [Speichern von Daten](../vsto/caching-data.md).|Beliebige XML-Daten.|
|Können Sie auf die Daten zugreifen, ohne Microsoft Office Anwendungen zu starten?|Ja, mithilfe der- <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> Klasse, die von bereitgestellt wird [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .|Ja, mithilfe von Klassen im- <xref:System.IO.Packaging> Namespace oder mit dem Open XML-Format-SDK.|

## <a name="see-also"></a>Siehe auch
- [Daten in Office-Projektmappen](../vsto/data-in-office-solutions.md)
- [Architektur von Office-Projektmappen in Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
