---
title: 'Vorgehensweise: Bearbeiten von XML-Dateien'
ms.date: 11/04/2016
description: In diesem Artikel erfahren Sie, wie Sie den XML-Editor in Visual Studio verwenden, um Dateien zu bearbeiten, die XML- oder DTD-Inhalte enthalten.
ms.custom: SEO-VS-2020
ms.topic: how-to
ms.assetid: 07fa3ecf-6345-4d30-9d85-d5ef5b083319
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 933ce2912845b69ceb73584c0599566b0a037fef
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2020
ms.locfileid: "93399981"
---
# <a name="how-to-edit-xml-files"></a>Vorgehensweise: Bearbeiten von XML-Dateien

Der XML-Editor ist der neue Editor für XML-Dateien. Er kann für eine eigenständige XML-Datei oder für eine einem Visual Studio-Projekt zugeordnete Datei verwendet werden. Der XML-Editor ist den folgenden Dateierweiterungen zugeordnet: *.config*, *.dtd*, *.xml*, *.xsd*, *.xdr*, *.xsl*, *.xslt* und *.vssettings*. Dem XML-Editor wird auch jeder andere Dateityp mit XML- bzw. DTD-Inhalten zugeordnet, für den kein bestimmter Editor registriert ist.

> [!NOTE]
> XHTML-Dokumente werden vom HTML-Editor behandelt.

Um eine XML-Datei zu bearbeiten, öffnen Sie die Datei, die Sie bearbeiten möchten.

## <a name="add-a-new-xml-file-to-a-project"></a>Hinzufügen einer neuen XML-Datei zu einem Projekt

1. Wählen Sie im Menü **Projekt** die Option **Neues Element hinzufügen** aus.

2. Wählen Sie im Bereich **Vorlagen** die Option **XML-Datei** aus.

3. Geben Sie im Feld **Name** den Dateinamen ein, und klicken Sie auf **Hinzufügen**.

   Die XML-Datei wird dem Projekt hinzugefügt und im XML-Editor geöffnet. Die Datei enthält die XML-Standarddeklaration, `<?xml version="1.0" encoding="utf-8" ?>`.

## <a name="add-an-existing-xml-file-to-a-project"></a>Hinzufügen einer vorhandenen XML-Datei zu einem Projekt

1. Klicken Sie im Menü **Projekt** auf **Vorhandenes Element hinzufügen**.

   Das Dialogfeld **Vorhandenes Element hinzufügen** wird angezeigt.

2. Wählen Sie eine XML-Datei aus, und klicken Sie auf **Hinzufügen**.

## <a name="create-a-new-xml-or-xslt-file"></a>Erstellen einer neuen XML- oder XSLT-Datei

1. Wählen Sie im Menü **Datei** die Option **Neu** aus.

   Das Dialogfeld **Neue Datei** wird angezeigt.

2. Wählen Sie **XML-Datei** aus, um eine neue XML-Datei zu erstellen, oder wählen Sie **XSLT-Datei** aus, um ein neues XSLT-Stylesheet zu erstellen.

3. Wählen Sie **Open**(Öffnen).

## <a name="create-an-empty-project-for-xml-files"></a>Erstellen eines leeren Projekts für XML-Dateien

::: moniker range="vs-2017"

1. Klicken Sie im Menü **Datei** auf **Neu** > **Projekt**.

   Das Dialogfeld **Neues Projekt** wird angezeigt.

2. Wählen Sie die gewünschte Codesprache aus, und wählen Sie dann die Vorlage **Empty Project (.NET Framework)** (Leeres Projekt (.NET Framework)) aus.

3. Klicken Sie auf **OK**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Klicken Sie im Menü **Datei** auf **Neu** > **Projekt**.

2. Geben Sie **Empty Project** (Leeres Projekt) in das Vorlagensuchfeld ein, wählen Sie die Vorlage **Empty Project (.NET Framework)** (Leeres Projekt (.NET Framework)) aus, und wählen Sie dann **Weiter** aus.

3. Klicken Sie auf **Erstellen**.

::: moniker-end

4. Fügen Sie dem Projekt XML-Dateien hinzu.

   Der XML-Editor sucht die dem Projekt hinzugefügten Schemata und verwendet sie für die Validierung und für IntelliSense in allen XML-, Schema- oder XSLT-Dateien, die Sie bearbeiten, während das Projekt geöffnet ist.

## <a name="see-also"></a>Siehe auch

- [XML-Editor](../xml-tools/xml-editor.md)
- [XML-Dokumenteigenschaften, Eigenschaftenfenster](../xml-tools/xml-document-properties-properties-window.md)
- [How to: Erstellen eines XML-Schemas aus einem XML-Dokument](../xml-tools/how-to-create-an-xml-schema-from-an-xml-document.md)
