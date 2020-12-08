---
title: Zuordnen eines Formular Bereichs zu einer Outlook-Nachrichten Klasse
description: Erfahren Sie, wie Sie angeben können, welche Microsoft Office Outlook-Elemente einen Formular Bereich anzeigen, indem Sie den Formular Bereich der Nachrichten Klasse der einzelnen Elemente zuordnen.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VSTO.NewFormRegionWizard.InvalidMessageClassName
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FormRegionMessageClassAttribute
- form regions [Office development in Visual Studio], message classes
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 213b167bf7fe10c83b028fce2d97c67cd837d272
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96846999"
---
# <a name="associate-a-form-region-with-an-outlook-message-class"></a>Zuordnen eines Formular Bereichs zu einer Outlook-Nachrichten Klasse
  Sie können angeben, welche Microsoft Office Outlook-Elemente einen Formular Bereich anzeigen, indem Sie den Formular Bereich der Nachrichten Klasse der einzelnen Elemente zuordnen. Wenn Sie z. b. einen Formular Bereich am unteren Rand eines Mail Elements anfügen möchten, können Sie den Formular Bereich der `IPM.Note` Message-Klasse zuordnen.

 Um einen Formular Bereich einer Nachrichten Klasse zuzuordnen, geben Sie den Namen der Nachrichten Klasse im Assistenten für **neue Outlook-Formular** Bereiche an, oder wenden Sie ein Attribut auf die Formularbereichsfactory-Klasse an.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="understand-outlook-message-classes"></a>Grundlegendes zu Outlook-Nachrichten Klassen
 Eine Outlook-Nachrichten Klasse identifiziert einen Typ von Outlook-Element. In der folgenden Tabelle werden diese acht Standardtypen von Elementen und deren Nachrichten Klassennamen aufgelistet.

|Outlook-Elementtyp|Name der Nachrichten Klasse|
|-----------------------|------------------------|
|AppointmentItem|`IPM.Appointment`|
|ContactItem|`IPM.Contact`|
|DistListItem|`IPM.DistList`|
|Journtem|`IPM.Activity`|
|MailItem|`IPM.Note`|
|PostItem|`IPM.Post` oder `IPM.Post.RSS`|
| TaskItem|`IPM.Task`|

 Sie können auch die Namen von benutzerdefinierten Nachrichten Klassen angeben. Benutzerdefinierte Nachrichten Klassen identifizieren benutzerdefinierte Formulare, die Sie in Outlook definieren.

> [!NOTE]
> Für die Formular Bereiche "Ersetzung" und "Alle ersetzen" können Sie einen neuen benutzerdefinierten Nachrichten Klassennamen angeben. Sie müssen nicht den Nachrichten Klassennamen eines vorhandenen benutzerdefinierten Formulars verwenden. Der Name der benutzerdefinierten Nachrichten Klasse muss eindeutig sein. Eine Möglichkeit, um sicherzustellen, dass der Name eindeutig ist, besteht darin, eine Benennungs Konvention zu verwenden, die der folgenden ähnelt: \<*StandardMessageClassName*> . \<*Company*>\<*MessageClassName*> (Beispiel: `IPM.Note.Contoso.MyMessageClass` ).

## <a name="associate-a-form-region-with-an-outlook-message-class"></a>Zuordnen eines Formular Bereichs zu einer Outlook-Nachrichten Klasse
 Es gibt zwei Möglichkeiten, einem Formular Bereich eine Nachrichten Klasse zuzuordnen:

- Verwenden Sie den Assistenten **Neuer Outlook-Formular Bereich** .

- Klassenattribute anwenden.

### <a name="use-the-new-outlook-form-region-wizard"></a>Verwenden des Assistenten für neue Outlook-Formular Bereiche
 Auf der letzten Seite des Assistenten **Neuer Outlook-Formular Bereich** können Sie Standard Nachrichten Klassen auswählen und die Namen der benutzerdefinierten Nachrichten Klassen eingeben, die Sie dem Formular Bereich zuordnen möchten.

 Die Standard Nachrichten Klassen sind nicht verfügbar, wenn der Formular Bereich zum Ersetzen des gesamten Formulars oder der Standardseite eines Formulars entworfen wurde. Sie können Standard Nachrichten Klassennamen nur für Formulare angeben, die eine neue Seite zu einem Formular hinzufügen oder die am Ende eines Formulars angefügt werden. Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen eines Formular Bereichs zu einem Outlook-Add-in-Projekt](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).

 Wenn Sie eine oder mehrere benutzerdefinierte Nachrichten Klassen einschließen möchten, geben Sie Ihre Namen in das Feld **welche benutzerdefinierten Meldungs Klassen dieses Formular Bereich anzeigen?** ein.

 Die Namen, die Sie eingeben, müssen den folgenden Richtlinien entsprechen:

- Verwenden Sie den voll qualifizierten Nachrichten Klassennamen (z. b. "IPM". Hinweis....

- Verwenden Sie Semikolons, um mehrere Nachrichten Klassennamen voneinander zu trennen.

- Schließen Sie keine Outlook-Standard Nachrichten Klassen ein, z. b. "IPM". Hinweis "oder" IPM. Kontakt ". Schließen Sie nur benutzerdefinierte Nachrichten Klassen ein, z. b. "IPM". Hinweis....

- Geben Sie die Basis Nachrichten Klasse nicht eigenständig an (z. b.: "IPM").

- Nicht länger als 256 Zeichen für jeden Nachrichten Klassennamen.

  Der Assistent für **neue Outlook-Formular** Bereiche überprüft das Format Ihrer Eingabe, wenn Sie auf " **Fertig** stellen" klicken.

> [!NOTE]
> Der Assistent für **neue Outlook-Formular** Bereiche überprüft nicht, ob die von Ihnen angegebenen Nachrichten Klassennamen richtig oder gültig sind.

 Wenn Sie den Assistenten beenden, wendet der Assistent für **neue Outlook-Formular** Bereiche Attribute auf die Formular Bereichs Klasse an, die die angegebenen Nachrichten Klassennamen enthalten. Sie können diese Attribute auch manuell anwenden.

### <a name="apply-class-attributes"></a>Klassenattribute anwenden
 Nachdem Sie den Assistenten für **neue Outlook-Formular** Bereiche fertiggestellt haben, können Sie einen Formular Bereich einer Outlook-Nachrichten Klasse zuordnen. Dazu wenden Sie Attribute auf die Formularbereichsfactory-Klasse an.

 Das folgende Beispiel zeigt zwei <xref:Microsoft.Office.Tools.Outlook.FormRegionMessageClassAttribute> Attribute, die auf eine Formularbereichsfactory-Klasse mit dem Namen angewendet wurden `myFormRegion` . Mit dem ersten Attribut wird der Formular Bereich einer Standard Nachrichten Klasse für ein e-Mail-Nachrichten Formular zugeordnet. Das zweite Attribut ordnet den Formular Bereich einer benutzerdefinierten Nachrichten Klasse mit dem Namen zu `IPM.Task.Contoso` .

 [!code-vb[Trin_Outlook_FR_Attributes#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Attributes/FormRegion1.vb#1)]
 [!code-csharp[Trin_Outlook_FR_Attributes#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Attributes/FormRegion1.cs#1)]

 Attribute müssen den folgenden Richtlinien entsprechen:

- Verwenden Sie für benutzerdefinierte Nachrichten Klassen den voll qualifizierten Nachrichten Klassennamen (z. b. "IPM". Hinweis....

- Geben Sie die Basis Nachrichten Klasse nicht eigenständig an (z. b.: "IPM").

- Nicht länger als 256 Zeichen für jeden Nachrichten Klassennamen.

- Fügen Sie die Namen von Standard Nachrichten Klassen nicht ein, wenn der Formular Bereich das gesamte Formular oder die Standardseite eines Formulars ersetzt. Sie können Standard Nachrichten Klassennamen nur für Formulare angeben, die eine neue Seite zu einem Formular hinzufügen oder die am Ende eines Formulars angefügt werden. Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen eines Formular Bereichs zu einem Outlook-Add-in-Projekt](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).

  Visual Studio überprüft das Format der Nachrichten Klassennamen, wenn Sie das Projekt erstellen.

> [!NOTE]
> Visual Studio überprüft nicht, ob die von Ihnen angegebenen Nachrichten Klassennamen richtig oder gültig sind.

## <a name="see-also"></a>Siehe auch
- [Zugreifen auf einen Formular Bereich zur Laufzeit](../vsto/accessing-a-form-region-at-run-time.md)
- [Erstellen von Outlook-Formular Bereichen](../vsto/creating-outlook-form-regions.md)
- [Exemplarische Vorgehensweise: Entwerfen eines Outlook-Formular Bereichs](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Richtlinien zum Erstellen von Outlook-Formular Bereichen](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [Übersicht über Formular Name und Nachrichten Klasse](/office/vba/outlook/Concepts/Forms/form-name-and-message-class-overview)
- [Zusammenarbeiten von Outlook Forms und Elementen](/office/vba/outlook/Concepts/Forms/how-outlook-forms-and-items-work-together)
