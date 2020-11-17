---
title: 'Vorgehensweise: Auswählen der zu verwendenden XML-Schemas'
description: In diesem Artikel erfahren Sie, wie Sie den XML-Editor verwenden, um ein XML-Schema aus dem Schemacache auszuwählen, das bekannte XML-Schemas umfasst, die für IntelliSense und die Validierung von XML-Dokumenten verwendet werden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d6fda3ef-d465-4788-8514-2f2d528d658c
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9773df597269d5f7044bf168626f530e4a454020
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400153"
---
# <a name="how-to-select-the-xml-schemas-to-use"></a>Vorgehensweise: Auswählen der zu verwendenden XML-Schemas

Der XML-Editor stellt einen Schemacache im Verzeichnis *%VSInstallDir%\xml\Schemas* bereit. Der Schemacache enthält bekannte XML-Schemata, die für IntelliSense und zur Validierung von XML-Dokumenten verwendet werden.

Mithilfe der Dokumenteigenschaft **Schemas** können Sie eins oder mehrere Schemas der XML Schema Definition Language (XSD) auswählen. Sie können Schemas aus dem Schemacache oder von einem anderen Ort auswählen.

Die von Ihnen ausgewählten Schemas werden zusammen mit allen anderen XML-Dokumenteigenschaften in einer (versteckten) Projektmappen-Benutzeroptionendatei (.*suo*) gespeichert. Dadurch müssen Sie diese Werte nicht erneut eingeben, wenn Sie die Projektmappe das nächste Mal öffnen.

> [!NOTE]
> Der Editor kann mithilfe eines Inlineschemas oder eines Schemas, auf das von dem `xsd:schemaLocation`-Attribut verwiesen wird, die Validierung vornehmen. Weitere Informationen finden Sie unter [Validierung von XML-Dokumenten](../xml-tools/xml-document-validation.md).

## <a name="to-select-an-xml-schema-from-the-schema-cache"></a>So wählen Sie ein XML-Schema aus dem Schemacache aus

1. Öffnen Sie eine Datei im XML-Editor.

2. Klicken Sie im Eigenschaftenfenster des Dokuments in das Feld **Schemas**. Wenn die Schaltfläche zum Durchsuchen (...) angezeigt wird, klicken Sie darauf.

   ![„Schemas“-Eigenschaft für eine XML-Datei](media/properties-schemas.png)

   Das [Dialogfeld „XML-Schemata“](xml-schemas-dialog-box.md) wird geöffnet. Im Dialogfeld werden alle Schemata mit einer *XSD*-Erweiterung im Schemacache aufgelistet (einschließlich Schemata, auf die in *catalog.xml* verwiesen wird) sowie alle Schemata, die sich in der aktuellen Projektmappe befinden, die in Visual Studio geöffnet sind bzw. auf die in einem `xsd:schemaLocation`-Attribut oder in der **Schemas**-Eigenschaft verwiesen wird.

3. Wählen Sie Schemata zu Validierungszwecken aus, indem Sie eine der folgenden Methoden verwenden:

   - Wählen Sie ein im Dialogfeld **XML-Schemas** aufgelistetes Schema aus, klicken Sie auf die Spalte **Verwendung**, und wählen Sie dann **Dieses Schema verwenden** aus.

     - oder -

   - Wählen Sie mehrere im Dialogfeld **XML-Schemas** aufgelistete Schemas aus, klicken Sie dann mit der rechten Maustaste, und wählen Sie **Dieses Schema verwenden** aus.

4. Klicken Sie auf **OK**.

   Die Liste der ausgewählten **Schemata** wird zurück in die Schemas-Eigenschaft des Dokuments kopiert.

## <a name="to-add-an-xml-schema-to-the-schema-cache"></a>So fügen Sie dem Schemacache ein XML-Schema hinzu

1. Klicken Sie im Eigenschaftenfenster des Dokuments im Feld **Schemas** auf die Schaltfläche.

2. Klicken Sie auf **Hinzufügen**.

   Das Dialogfeld **XSD-Schema öffnen** wird geöffnet.

3. Navigieren Sie zu den Schemas, die dem Schemacache hinzugefügt werden sollen, und markieren Sie diese.

4. Klicken Sie auf **Öffnen**.

   Die Schemas werden dem Schemacache hinzugefügt, und der Wert der Spalte **Verwendung** wird auf **Dieses Schema verwenden** festgelegt.

## <a name="to-delete-an-xml-schema-from-the-schema-cache"></a>So löschen Sie ein XML-Schema aus dem Schemacache

1. Klicken Sie im Eigenschaftenfenster des Dokuments im Feld **Schemas** auf die Schaltfläche.

2. Wählen Sie das zu entfernende Schema aus, und klicken Sie dann auf **Entfernen**.

   Das Schema wird aus dem In-Memory-Schemacache , jedoch nicht aus dem Dateisystem entfernt.

   > [!NOTE]
   > Wenn immer noch mit einem `schemaLocation`-Attribut oder einem entsprechenden `targetNamespace` auf das Schema verwiesen wird, funktioniert **Entfernen** aufgrund der automatischen Zuordnung in dieser Situation nicht. In diesem Fall sollten Sie das Schema in der Spalte **Verwendung** als **Ausgewählte Schemas nicht verwenden** markieren.

## <a name="see-also"></a>Siehe auch

- [Schemacache](../xml-tools/schema-cache.md)
- [XML-Schemas (Dialogfeld)](../xml-tools/xml-schemas-dialog-box.md)
- [XML-Editor](../xml-tools/xml-editor.md)
