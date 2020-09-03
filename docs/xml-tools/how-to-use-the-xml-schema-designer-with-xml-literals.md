---
title: 'Vorgehensweise: Verwenden des XML-Schema-Designers mit XML-Literalen'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d11803e7-f81a-41a2-a145-ba494a45cc93
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: b515092087ab213db5d3002f00c56753c2e3de14
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85814641"
---
# <a name="how-to-use-the-xml-schema-designer-with-xml-literals"></a>Vorgehensweise: Verwenden des XML-Schema-Designers mit XML-Literalen

In diesem Thema wird beschrieben, wie ein mit einem XML-Literal verknüpftes Schema in einem Visual Basic-Projekt angezeigt wird.

## <a name="create-a-new-visual-basic-project"></a>Erstellen eines neuen Visual Basic-Projekts

1. Öffnen Sie Visual Studio.

2. Erstellen Sie ein neues Visual Basic-**Konsolenanwendung**sprojekt namens **XMLLiterals**.

     Das neue Projekt enthält die eine Visual Basic-Quelldatei *Module1.vb*.

## <a name="add-an-existing-xsd-file"></a>Hinzufügen einer vorhandenen XSD-Datei

1. Öffnen Sie eine neue Textdatei in Editor. Kopieren Sie den XML-Schemabeispielcode aus dem [Bestellungsschema](../xml-tools/sample-xsd-file-simple-schema.md), und fügen Sie ihn in die Datei ein.

2. Speichern Sie die Datei unter dem Namen *PurchaseOrderSchema.xsd* an einem beliebigen Speicherort.

3. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Projektnamen, wählen Sie **Hinzufügen** aus, und wählen Sie dann **Vorhandenes Element** aus. Das Dialogfeld **Vorhandenes Element hinzufügen** wird angezeigt. Navigieren Sie zur Datei *PurchaseOrderSchema.xsd*, wählen Sie sie aus, und klicken Sie dann auf **Hinzufügen**.

     Das Projekt „XMLLiterals“ enthält jetzt zwei Dateien: *Module1.vb* und *PurchaseOrderSchema.xsd*.

## <a name="add-code"></a>Code hinzufügen

So fügen Sie basierend auf der XSD-Datei im Projekt Visual Basic-Code mit einem XML-Literal hinzu

1. Ersetzen Sie den Code in der Datei *Module1.vb* durch folgenden Code:

   ```vb
   Imports <xmlns:ns="http://tempuri.org/PurchaseOrderSchema.xsd">

   Module Module1
      Sub Main()

          Dim XMLLiteral = <ns:PurchaseOrder OrderDate="1900-01-01">
                               <ns:ShipTo country="US">
                                   <ns:name>name1</ns:name>
                                   <ns:street>street1</ns:street>
                                   <ns:city>city1</ns:city>
                                   <ns:state>state1</ns:state>
                                   <ns:zip>1</ns:zip>
                               </ns:ShipTo>
                               <ns:BillTo country="US">
                                   <ns:name>name1</ns:name>
                                   <ns:street>street1</ns:street>
                                   <ns:city>city1</ns:city>
                                   <ns:state>state1</ns:state>
                                   <ns:zip>1</ns:zip>
                               </ns:BillTo>
                           </ns:PurchaseOrder>

      End Sub
   End Module
   ```

2. Klicken Sie mit der rechten Maustaste auf einen XML-Knoten in einem XML-Literal oder einem XML-Namespaceimport, und wählen Sie **In XML-Schema-Explorer anzeigen** aus.

   Der **XML-Schema-Explorer** wird neben einer Visual Basic-Datei angezeigt, die das mit dem XML-Schemaset verknüpfte XML-Literal enthält.
