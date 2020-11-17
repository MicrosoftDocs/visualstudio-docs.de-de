---
title: 'Exemplarische Vorgehensweise: Verwenden der Features des XML-Editors'
description: In diesem Artikel erfahren Sie, wie Sie ein neues XML-Dokument erstellen, indem Sie die Schritte in dieser exemplarischen Vorgehensweise befolgen, die Features des XML-Editors veranschaulicht.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: ea8dc357-2e66-455a-aec2-7ccaccfc9adf
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f8aa7daef6e427b7355eb7676db0728a4af4ca42
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94351478"
---
# <a name="walkthrough-use-xml-editor-features"></a>Exemplarische Vorgehensweise: Verwenden von Features des XML-Editors

Die Schritte in dieser exemplarischen Vorgehensweise veranschaulichen die Erstellung eines neuen XML-Dokuments. Bei der exemplarischen Vorgehensweise werden auch die Funktionen des XML-Editors verwendet, die für das Verfassen von XML nützlich sind.

> [!NOTE]
> Speichern Sie vor dem Starten der exemplarischen Vorgehensweise die Datei *hireDate.xsd* (weiter unten in diesem Thema aufgeführt) auf dem lokalen Computer.

## <a name="to-create-a-new-xml-file-and-associate-it-with-an-xml-schema"></a>So erstellen Sie eine neue XML-Datei und ordnen ihr ein XML-Schema zu

1. Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie auf **Datei**.

2. Wählen Sie im Bereich **Vorlagen** die Option **XML-Datei** aus, und klicken Sie auf **Öffnen**.

     Im Editor wird eine neue Datei geöffnet. Die Datei enthält eine XML-Standarddeklaration, `<?xml version="1.0" encoding="utf-8">`.

3. Klicken Sie im Dokumenteigenschaftenfenster im Feld **Schemata** auf die Schaltfläche zum Durchsuchen ( **…** ).

     Das Dialogfeld **XSD-Schemas** wird angezeigt.

4. Klicken Sie auf **Hinzufügen**.

     Das Dialogfeld **XSD-Schema öffnen** wird angezeigt.

5. Wählen Sie die Datei *hireDate.xsd* aus, und klicken Sie auf **Öffnen**.

6. Klicken Sie auf **OK**.

     Das XML-Schema wird jetzt dem XML-Dokument zugeordnet. Mithilfe des XML-Schemas wird das Dokument validiert. Es wird auch von IntelliSense verwendet, um die Memberliste der gültigen Elemente aufzufüllen.

## <a name="to-add-data"></a>So fügen Sie Daten hinzu

1. Geben Sie im Editorbereich `<` ein.

     In der Memberliste werden die möglichen Elemente angezeigt:

    - **!--** zum Hinzufügen eines Kommentars.

    - **!DOCTYPE** zum Hinzufügen eines Dokumenttyps.

    - **?** zum Hinzufügen einer Verarbeitungsanweisung.

    - **employee** zum Hinzufügen des Stammelements.

2. Wählen Sie **&lt;!--** aus, um einen Kommentarknoten hinzuzufügen, und drücken Sie die **EINGABETASTE**.

     Der Editor fügt ein Kommentar-Endtag ein und platziert den Cursor zwischen dem Start- und Endtag des Kommentars.

3. Geben Sie **XML-Testdatei** ein.

4. Geben Sie auf einer neuen Zeile `<` ein, und wählen Sie **employee** in der Memberliste aus.

     Im Editor wird der Anfang eines XML-Elements, `<employee`, hinzugefügt. An dieser Stelle können Sie dem Element Attribute hinzufügen, oder Sie können das Starttag schließen, indem Sie `>` eingeben.

5. Geben Sie `>` ein, um das Tag zu schließen.

6. Der Editor fügt das Endtag hinzu. Das Endtag wird mit einer wellenförmigen Unterstreichung hinzugefügt, womit auf einen Validierungsfehler hingewiesen wird. In der **QuickInfo** wird folgende Meldung angezeigt: **Der Inhalt des Elements „employee“ ist unvollständig. Erwartet wurde „ID“** .

7. Geben Sie `<` ein, und wählen Sie die **ID** in der Memberliste aus. Geben Sie anschließend `>` ein.

     Der Editor fügt das XML-Element `<ID></ID>` hinzu und platziert den Cursor hinter dem ID-Starttag.

8. Geben Sie **abc** ein.

     Der Text **abc** weist eine wellenförmige Unterstreichung auf. In der **QuickInfo** wird folgende Meldung angezeigt: **Der Wert des Elements „ID“ ist gemäß seinem Datentyp ungültig**.

9. Klicken Sie mit der rechten Maustaste auf das ID-Element, und wählen Sie **Gehe zu Definition** aus.

     Der Editor öffnet die Datei *hireDate.xsd* in einem neuen Dokumentfenster und platziert den Cursor auf der ID-Schemaelementdefinition.

10. Kehren Sie zur XML-Datei zurück, und ersetzen Sie den Text **abc** durch **123**.

     Die wellenförmige Unterstreichung und die **QuickInfo** unter dem ID-Elementwert werden gelöscht. In der **QuickInfo** für das „employee“-Endtag wird jetzt folgende Meldung angezeigt: **Der Inhalt des Elements „employee“ ist unvollständig. Erwartet wurde „hire-date“** .

11. Positionieren Sie den Cursor hinter dem ID-Endtag, geben Sie `<` ein, wählen Sie **hire-date** in der Memberliste aus, und geben Sie anschließend `>` ein.

     Der Editor fügt das XML-Element `<hire-date></hire-date>` hinzu und platziert den Cursor hinter dem 'hire-date'-Starttag.

12. Geben Sie **2003-01-10** als Wert für „hire-date“ ein.

## <a name="to-format-the-xml-document"></a>So formatieren Sie das XML-Dokument

- Wählen Sie auf der Symbolleiste des XML-Editors die Schaltfläche **Dokument formatieren** aus, oder drücken Sie **STRG**+**E**,**D**.

   ![Schaltfläche „XML-Dokument formatieren“ in Visual Studio](media/format-xml-document.png)

   Das XML-Dokument wird neu formatiert.

## <a name="to-save-the-xml-document"></a>So speichern Sie das XML-Dokument

1. Wählen Sie im Menü **Datei** die Option **Speichern unter**.

     Das Dialogfeld **Datei speichern unter** wird angezeigt. Der Standarddateiname lautet *'XMLFile1'* .

2. Geben Sie den Dateinamen und den Speicherort für das XML-Dokument ein, und klicken Sie auf **Speichern**.

## <a name="hiredatexsd-file"></a>Die Datei „hireDate.xsd“

In dieser exemplarischen Vorgehensweise wird die folgende Schemadatei verwendet:

```xml
<?xml version="1.0"?>
<xs:schema attributeFormDefault="unqualified"
     elementFormDefault="qualified" targetNamespace="urn:empl-hire"
     xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="employee">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="ID" type="xs:unsignedShort" />
        <xs:element name="hire-date" type="xs:date" />
      </xs:sequence>
    </xs:complexType>
  </xs:element>
</xs:schema>
```

## <a name="see-also"></a>Siehe auch

- [XML-Editor](../xml-tools/xml-editor.md)
