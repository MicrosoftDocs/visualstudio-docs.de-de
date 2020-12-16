---
title: Übersicht über das Outlook-Objektmodell
description: Erfahren Sie, wie Sie mit den Objekten interagieren können, die vom Outlook-Objektmodell bereitgestellt werden, um VSTO-Add-Ins für Microsoft Outlook zu entwickeln.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.OutlookAddin
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook [Office development in Visual Studio], object model overview
- object models [Office development in Visual Studio], Office
- objects [Office development in Visual Studio], Office object models
- object models [Office development in Visual Studio], Outlook
- Office object models
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 83ada85ba346e83e5bc5ebc01e91b11be0e844e1
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528055"
---
# <a name="outlook-object-model-overview"></a>Übersicht über das Outlook-Objektmodell
  Zum Entwickeln von VSTO-Add-Ins für Microsoft Office Outlook können Sie mit den Objekten interagieren, die vom Outlook-Objektmodell bereitgestellt werden. Das Outlook-Objektmodell stellt Klassen und Schnittstellen bereit, die Elemente der Benutzeroberfläche darstellen. Das <xref:Microsoft.Office.Interop.Outlook.Application> -Objekt stellt beispielsweise die gesamte Anwendung, das <xref:Microsoft.Office.Interop.Outlook.Folder> -Objekt einen Ordner mit E-Mails oder anderen Elementen und das <xref:Microsoft.Office.Interop.Outlook.MailItem> -Objekt eine E-Mail dar.

 Dieses Thema enthält eine kurze Übersicht über einige der Hauptobjekte im Outlook-Objektmodell. Weitere Informationen über das gesamte Outlook-Objektmodell finden Sie unter [Verwenden der Dokumentation zum Outlook-Objektmodell](#refdoc).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="access-objects-in-an-outlook-project"></a>Zugreifen auf Objekte in einem Outlook-Projekt
 Outlook stellt zahlreiche Objekte bereit, mit denen Sie interagieren können. Damit Sie das Objektmodell effizient verwenden können, sollten Ihnen die folgenden Objekte der obersten Ebene vertraut sein:

- <xref:Microsoft.Office.Interop.Outlook.Application>

- <xref:Microsoft.Office.Interop.Outlook.Explorer>

- <xref:Microsoft.Office.Interop.Outlook.Inspector>

- <xref:Microsoft.Office.Interop.Outlook.Folder>

- <xref:Microsoft.Office.Interop.Outlook.MailItem>

- <xref:Microsoft.Office.Interop.Outlook.AppointmentItem>

- <xref:Microsoft.Office.Interop.Outlook.TaskItem>

- <xref:Microsoft.Office.Interop.Outlook.ContactItem>

### <a name="application-object"></a>Anwendungsobjekt
 Das <xref:Microsoft.Office.Interop.Outlook.Application> -Objekt stellt die Outlook-Anwendung dar und ist im Outlook-Objektmodell das Objekt der obersten Ebene. Zu den wichtigsten Membern dieses Objekts gehören:

- Die [CreateItem](/previous-versions/office/developer/office-2003/aa220082(v=office.11)) -Methode, die Sie zum Erstellen eines neuen Elements wie einer E-Mail, einer Aufgabe oder eines Termins verwenden können.

- Die <xref:Microsoft.Office.Interop.Outlook._Application.Explorers%2A> -Eigenschaft, die Sie für den Zugriff auf die Fenster verwenden können, in denen der Inhalt eines Ordners in der Outlook-Benutzeroberfläche (UI) angezeigt wird.

- Die <xref:Microsoft.Office.Interop.Outlook._Application.Inspectors%2A> -Eigenschaft, die Sie für den Zugriff auf die Fenster verwenden können, in denen der Inhalt eines einzelnen Elements wie einer E-Mail oder einer Besprechungsanfrage angezeigt wird.

  Um eine Instanz des-Objekts zu erhalten <xref:Microsoft.Office.Interop.Outlook.Application> , verwenden Sie das Anwendungsfeld der- `ThisAddIn` Klasse im Projekt. Weitere Informationen finden Sie unter [Program VSTO Add-ins](../vsto/programming-vsto-add-ins.md).

> [!NOTE]
> Um Sicherheitswarnungen zu vermeiden, wenn Sie Eigenschaften und Methoden verwenden, die vom Outlook-Objekt Modellschutz blockiert werden, sollten Sie Outlook-Objekte aus dem Anwendungsfeld der- `ThisAddIn` Klasse erhalten. Weitere Informationen finden Sie unter [spezifische Sicherheitsüberlegungen für Office](../vsto/specific-security-considerations-for-office-solutions.md)-Projektmappen.

### <a name="explorer-object"></a>Explorer-Objekt
 Das <xref:Microsoft.Office.Interop.Outlook.Explorer> -Objekt stellt ein Fenster dar, in dem der Inhalt eines Ordners angezeigt wird, der Elemente wie E-Mails, Aufgaben oder Termine enthält. Das <xref:Microsoft.Office.Interop.Outlook.Explorer> -Objekt enthält Methoden und Eigenschaften, die Sie zum Ändern des Fensters verwenden können, sowie Ereignisse, die bei einer Änderung des Fensters ausgelöst werden.

 Führen Sie einen der folgenden Schritte aus, um ein <xref:Microsoft.Office.Interop.Outlook.Explorer> -Objekt abzurufen:

- Verwenden Sie die <xref:Microsoft.Office.Interop.Outlook._Application.Explorers%2A> -Eigenschaft des <xref:Microsoft.Office.Interop.Outlook.Application> -Objekts, um auf alle <xref:Microsoft.Office.Interop.Outlook.Explorer> -Objekte in Outlook zuzugreifen.

- Verwenden Sie die <xref:Microsoft.Office.Interop.Outlook._Application.ActiveExplorer%2A> -Methode des <xref:Microsoft.Office.Interop.Outlook.Application> -Objekts, um den <xref:Microsoft.Office.Interop.Outlook.Explorer> abzurufen, der gerade den Fokus besitzt.

- Verwenden Sie die `GetExplorer`-Methode des <xref:Microsoft.Office.Interop.Outlook.Folder>-Objekts, um den <xref:Microsoft.Office.Interop.Outlook.Explorer> für den aktuellen Ordner abzurufen.

### <a name="inspector-object"></a>Inspector-Objekt
 Das <xref:Microsoft.Office.Interop.Outlook.Inspector> -Objekt stellt ein Fenster dar, in dem ein einzelnes Element wie eine E-Mail, eine Aufgabe oder ein Termin angezeigt wird. Das <xref:Microsoft.Office.Interop.Outlook.Inspector> -Objekt enthält Methoden und Eigenschaften, die Sie zum Ändern des Fensters verwenden können, sowie Ereignisse, die bei einer Änderung des Fensters ausgelöst werden.

 Führen Sie einen der folgenden Schritte aus, um ein <xref:Microsoft.Office.Interop.Outlook.Inspector> -Objekt abzurufen:

- Verwenden Sie die <xref:Microsoft.Office.Interop.Outlook._Application.Inspectors%2A> -Eigenschaft des <xref:Microsoft.Office.Interop.Outlook.Application> -Objekts, um auf alle <xref:Microsoft.Office.Interop.Outlook.Inspector> -Objekte in Outlook zuzugreifen.

- Verwenden Sie die <xref:Microsoft.Office.Interop.Outlook._Application.ActiveInspector%2A> -Methode des <xref:Microsoft.Office.Interop.Outlook.Application> -Objekts, um den <xref:Microsoft.Office.Interop.Outlook.Inspector> abzurufen, der gerade den Fokus besitzt.

- Verwenden Sie die `GetInspector`-Methode eines bestimmten Elements, z. B. <xref:Microsoft.Office.Interop.Outlook.MailItem> oder <xref:Microsoft.Office.Interop.Outlook.AppointmentItem>, um den dem Element zugeordneten Inspektor abzurufen.

### <a name="folder-object"></a>Folder-Objekt
 Das <xref:Microsoft.Office.Interop.Outlook.Folder> -Objekt stellt einen Ordner dar, der E-Mails, Kontakte, Aufgaben und andere Elemente enthält. Outlook stellt 16 <xref:Microsoft.Office.Interop.Outlook.Folder> -Standardobjekte bereit.

 Die <xref:Microsoft.Office.Interop.Outlook.Folder> -Standardobjekte werden durch die Werte der <xref:Microsoft.Office.Interop.Outlook.OlDefaultFolders> -Enumeration definiert. Beispiel:

 Microsoft. Office. Interop. Outlook. OlDefaultFolders. olFolderInbox entspricht dem Ordner " **Inbox** " in Outlook.

 Ein Beispiel für den Zugriff auf einen Standard und das <xref:Microsoft.Office.Interop.Outlook.Folder> Erstellen eines neuen <xref:Microsoft.Office.Interop.Outlook.Folder> finden Sie unter Gewusst [wie: Programm gesteuertes Erstellen von benutzerdefinierten Ordner Elementen](../vsto/how-to-programmatically-create-custom-folder-items.md).

### <a name="mailitem-object"></a>MailItem-Objekt
 Das <xref:Microsoft.Office.Interop.Outlook.MailItem> -Objekt stellt eine E-Mail dar. <xref:Microsoft.Office.Interop.Outlook.MailItem> -Objekte befinden sich normalerweise in Ordnern wie **Posteingang**, **Gesendete Elemente** und **Postausgang**. <xref:Microsoft.Office.Interop.Outlook.MailItem> macht Eigenschaften und Methoden verfügbar, die zum Erstellen und Senden von E-Mails verwendet werden können.

 Ein Beispiel für das Erstellen einer e-Mail-Nachricht finden Sie unter Gewusst [wie: Programm gesteuertes Erstellen eines e-Mail-Elements](../vsto/how-to-programmatically-create-an-e-mail-item.md).

### <a name="appointmentitem-object"></a>Objekt "Termin Objekt"
 Das <xref:Microsoft.Office.Interop.Outlook.AppointmentItem> -Objekt stellt eine Besprechung, einen einmaligen Termin, eine Terminserie oder eine Besprechungsserie im Ordner **Kalender** dar. Das <xref:Microsoft.Office.Interop.Outlook.AppointmentItem> -Objekt enthält Methoden zum Ausführen von Aktionen, z. B. Beantworten oder Weiterleiten von Besprechungsanfragen, sowie Eigenschaften, mit denen Besprechungsdetails wie Ort und Zeit angegeben werden.

 Ein Beispiel, das zeigt, wie Sie einen Termin erstellen, finden Sie unter Gewusst [wie: Programm gesteuertes Erstellen einer Besprechungs Anfrage](../vsto/how-to-programmatically-create-a-meeting-request.md).

### <a name="taskitem-object"></a>TaskItem-Objekt
 Das <xref:Microsoft.Office.Interop.Outlook.TaskItem> -Objekt stellt eine Aufgabe dar, die innerhalb eines bestimmten Zeitrahmens ausgeführt werden muss. <xref:Microsoft.Office.Interop.Outlook.TaskItem> -Objekte befinden sich im Ordner **Aufgaben** .

 Verwenden Sie zum Erstellen einer Aufgabe die [CreateItem](/previous-versions/office/developer/office-2003/aa220082(v=office.11)) -Methode des <xref:Microsoft.Office.Interop.Outlook.Application> -Objekts, und übergeben Sie für den Parameter den Wert <xref:Microsoft.Office.Interop.Outlook.OlItemType.olTaskItem> .

### <a name="contactitem-object"></a>ContactItem-Objekt
 Das <xref:Microsoft.Office.Interop.Outlook.ContactItem>-Objekt stellt einen Kontakt im Ordner **Kontakte** dar. <xref:Microsoft.Office.Interop.Outlook.ContactItem> -Objekte enthalten eine Reihe von Kontaktinformationen für die Personen, die sie darstellen, z. B. Anschriften, E-Mail-Adressen und Telefonnummern.

 Ein Beispiel für das Erstellen eines neuen Kontakts finden Sie unter Gewusst [wie: Programm gesteuertes Hinzufügen eines Eintrags zu Outlook-Kontakten](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md). Ein Beispiel, das zeigt, wie Sie nach einem vorhandenen Kontakt suchen, finden Sie unter Gewusst [wie: Programm gesteuertes suchen nach einem bestimmten Kontakt](../vsto/how-to-programmatically-search-for-a-specific-contact.md).

## <a name="use-the-outlook-object-model-documentation"></a><a name="refdoc"></a> Verwenden der Dokumentation zum Outlook-Objektmodell
 Vollständige Informationen zum Outlook-Objektmodell finden Sie in der Referenz zur primären Interopassembly (PIA) für Outlook und der VBA-Objektmodellreferenz.

### <a name="primary-interop-assembly-reference"></a>Referenz zur primären Interopassembly
 In der Referenz für die Outlook-PIA sind die Typen in den primären Interopassemblys für Outlook 2010 dokumentiert. Weitere Informationen finden Sie in der [Referenz zur primären Interopassembly von Outlook 2010](/previous-versions/office/developer/office-2010/bb652780(v=office.14)).

 Diese Dokumentation enthält neben Informationen zu allen Typen in den PIAs zusätzliche Informationen zur Struktur der PIAs und Codebeispiele für allgemeine Automatisierungsaufgaben in Outlook.

### <a name="vba-object-model-reference"></a>VBA-Objektmodell Referenz
 Die VBA-Objektmodellreferenz dokumentiert das Outlook-Objektmodell, das für VBA (Visual Basic for Applications)-Code verfügbar gemacht wird. Weitere Informationen finden Sie unter [Outlook 2010-Objektmodell Referenz](/office/vba/api/overview/Outlook/object-model).

 Alle Objekte und Member in der VBA-Objektmodellreferenz entsprechen Typen und Membern in der Outlook-PIA. Das Inspector-Objekt in der VBA-Objektmodell Referenz entspricht z. b <xref:Microsoft.Office.Interop.Outlook.Inspector> . dem-Objekt in der Outlook-Pia. Obwohl die VBA-Objektmodellreferenz Codebeispiele für die meisten Eigenschaften, Methoden und Ereignisse enthält, müssen Sie den VBA-Code in dieser Referenz in Visual Basic oder Visual C# übersetzen, wenn Sie ihn in einem mit Visual Studio erstellten Outlook-VSTO-Add-In-Projekt verwenden möchten.

### <a name="related-topics"></a>Verwandte Themen

|Titel|BESCHREIBUNG|
|-----------|-----------------|
|[Arbeiten mit Kontaktelementen](../vsto/working-with-contact-items.md)|Enthält Themen, die das Ausführen von Aufgaben mit Kontakten veranschaulichen.|
|[Arbeiten mit e-Mail-Elementen](../vsto/working-with-mail-items.md)|Enthält Themen, die das Ausführen von Aufgaben mit Mailelementen veranschaulichen.|
|[Arbeiten mit Ordnern](../vsto/working-with-folders.md)|Enthält Themen, die das Ausführen von Aufgaben mit Ordnern veranschaulichen.|
|[Arbeiten mit Kalenderelementen](../vsto/working-with-calendar-items.md)|Enthält Themen, die das Ausführen von Aufgaben mit Kalenderelementen veranschaulichen.|
|[Gewusst wie: Programm gesteuertes bestimmen des aktuellen Outlook-Elements](../vsto/how-to-programmatically-determine-the-current-outlook-item.md)|Zeigt, wie der Name des aktuellen Ordners und Informationen zum ausgewählten Element angezeigt werden.|
