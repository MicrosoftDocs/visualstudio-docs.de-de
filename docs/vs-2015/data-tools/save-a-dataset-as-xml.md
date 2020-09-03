---
title: Speichern eines Datasets als XML | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- XML [Visual Basic], datasets
- data [Visual Studio], saving as XML
- datasets [Visual Basic], saving as XML
- saving data
ms.assetid: 68b8327c-ae05-49ff-b9ba-99183e70b52c
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e64c3c17934e5cdc5d6ca1f510c7164b86a77c1a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652860"
---
# <a name="save-a-dataset-as-xml"></a>Speichern eines Datasets als XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der Zugriff auf die XML-Daten in einem DataSet ist möglich, indem die verfügbaren XML-Methoden für das DataSet aufgerufen werden. Um die Daten im XML-Format zu speichern, können Sie entweder die- <xref:System.Data.DataSet.GetXml%2A> Methode oder die-Methode einer-Methode von aufzurufen <xref:System.Data.DataSet.WriteXml%2A> <xref:System.Data.DataSet> .

 Beim Aufrufen der- <xref:System.Data.DataSet.GetXml%2A> Methode wird eine Zeichenfolge zurückgegeben, die die Daten aus allen Datentabellen im DataSet enthält, die als XML formatiert sind.

 Durch Aufrufen der <xref:System.Data.DataSet.WriteXml%2A> -Methode werden die XML-formatierten Daten an eine von Ihnen angegebene Datei gesendet.

### <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>So speichern Sie die Daten in einem DataSet als XML in einer Variablen

- Die <xref:System.Data.DataSet.GetXml%2A> Methode gibt einen zurück <xref:System.String> . Dies bedeutet, dass Sie eine Variable des Typs deklarieren <xref:System.String> und ihr die Ergebnisse der <xref:System.Data.DataSet.GetXml%2A> Methode zuweisen.

     [!code-csharp[VbRaddataSaving#12](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#12)]
     [!code-vb[VbRaddataSaving#12](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#12)]

### <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>So speichern Sie die Daten in einem DataSet als XML in einer Datei

- Die- <xref:System.Data.DataSet.WriteXml%2A> Methode verfügt über mehrere über Ladungen. Der folgende Code zeigt, wie die Daten in einer Datei gespeichert werden. Deklarieren Sie eine Variable, und weisen Sie Ihr einen gültigen Pfad zu, in dem die Datei gespeichert wird.

     [!code-csharp[VbRaddataSaving#13](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#13)]
     [!code-vb[VbRaddataSaving#13](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#13)]

## <a name="see-also"></a>Weitere Informationen
 [Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md)
