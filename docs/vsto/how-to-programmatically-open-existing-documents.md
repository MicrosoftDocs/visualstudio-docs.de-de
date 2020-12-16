---
title: 'Gewusst wie: Programm gesteuertes Öffnen vorhandener Dokumente'
description: Erfahren Sie, wie Sie die Open-Methode verwenden, um ein vorhandenes Microsoft Word-Dokument zu öffnen, das durch einen voll qualifizierten Pfad und Dateinamen angegeben wird.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], opening
- Word [Office development in Visual Studio], opening documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 994afc6f0d8d9bb76aff56097d0a18b8c3f940d9
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525563"
---
# <a name="how-to-programmatically-open-existing-documents"></a>Gewusst wie: Programm gesteuertes Öffnen vorhandener Dokumente
  Die- <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> Methode öffnet das vorhandene Microsoft Office Word-Dokument, das durch einen voll qualifizierten Pfad und Dateinamen angegeben wird. Diese Methode gibt einen zurück <xref:Microsoft.Office.Interop.Word.Document> , der das geöffnete Dokument darstellt.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-open-a-document"></a>So öffnen Sie ein Dokument

- Ruft die <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> -Methode der <xref:Microsoft.Office.Interop.Word.Documents> -Auflistung auf und stellt einen Pfad zum Dokument bereit.

     [!code-vb[Trin_VstcoreWordAutomation#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#5)]
     [!code-csharp[Trin_VstcoreWordAutomation#5](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#5)]

## <a name="to-open-a-document-as-read-only"></a>So öffnen Sie ein Dokument als schreibgeschützt

- Nennen Sie die- <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> Methode, geben Sie einen Pfad zum Dokument an,  und legen Sie im Methoden aufrufdas Argument "schreibgeschützt" auf " **true** " fest.

     [!code-vb[Trin_VstcoreWordAutomation#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#6)]
     [!code-csharp[Trin_VstcoreWordAutomation#6](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#6)]

## <a name="compile-the-code"></a>Kompilieren des Codes
 Für dieses Codebeispiel benötigen Sie Folgendes:

- Ein Dokument mit dem Namen *NewDocument.doc* muss in einem Verzeichnis mit dem Namen *Test* auf Laufwerk C vorhanden sein.

## <a name="see-also"></a>Weitere Informationen
- [Gewusst wie: Programm gesteuertes Erstellen neuer Dokumente](../vsto/how-to-programmatically-create-new-documents.md)
- [Gewusst wie: Programm gesteuertes schließen von Dokumenten](../vsto/how-to-programmatically-close-documents.md)
- [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)
