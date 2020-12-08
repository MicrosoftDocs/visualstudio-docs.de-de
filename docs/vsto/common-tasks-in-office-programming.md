---
title: Häufige Aufgaben bei der Office-Programmierung
description: Erfahren Sie, wie Sie für die Daten in einer Anpassung auf Dokument Ebene programmieren können, ohne das Objektmodell von Microsoft Office Word oder Office Excel verwenden zu müssen.
ms.custom: SEO-VS-2020SS
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, getting started
- FAQs (frequently asked questions) [Office development in Visual Studio]
- Office development in Visual Studio, frequently asked questions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4f6fae2b7d446035a08e3fcb77bcffaaed6de3a9
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2020
ms.locfileid: "96846297"
---
# <a name="common-tasks-in-office-programming"></a>Häufige Aufgaben bei der Office-Programmierung
  Dieses Thema soll Ihnen helfen, Antworten auf die folgenden Kategorien häufig gestellter Fragen zum Programmieren von Office-Projektmappen mithilfe von Visual Studio zu finden.

- [Setup und allgemeine Aufgaben](#projects).

- [Anpassungs Aufgaben für die Benutzeroberfläche](#ui).

- [Excel-Automatisierungsaufgaben](#excel).

- [Word-Automatisierungsaufgaben](#word).

- [Daten Tasks](#data).

- [Serverseitige Dokumentverwaltungsaufgaben](#server).

- [Sicherheitsaufgaben](#security).

- [Bereitstellungs Aufgaben](#deployment).

## <a name="setup-and-general-tasks"></a><a name="projects"></a> Setup und allgemeine Aufgaben

- Gewusst [wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)

- Gewusst [wie: Aktualisieren von Office](/previous-versions/4bez6837(v=vs.140))-Projektmappen

- Gewusst [wie: Installieren von primären Interop](../vsto/how-to-install-office-primary-interop-assemblies.md)-Assemblys in Office

- Gewusst [wie: Ausrichten von Office-Anwendungen mithilfe primärer Interop](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)-Assemblys.

- Gewusst [wie: Erstellen von Ereignis Handlern in Office-Projekten](../vsto/how-to-create-event-handlers-in-office-projects.md).

- Gewusst [wie: Öffnen von Office](../vsto/how-to-open-office-solutions-without-running-code.md)-Projektmappen ohne Ausführen von Code.

- Gewusst [wie: Einrichten von Konfigurationsinformationen für eine Office](../vsto/how-to-set-up-configuration-information-for-an-office-solution.md)-Projekt Mappe.

- Gewusst [wie: Anzeigen der Registerkarte "Entwickler" im Menüband](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

- Gewusst [wie: Anzeigen von Add-in-Benutzeroberflächen Fehlern](../vsto/how-to-show-add-in-user-interface-errors.md)

## <a name="user-interface-customization-tasks"></a><a name="ui"></a> Aufgaben zur Anpassung der Benutzeroberfläche

### <a name="controls-on-documents-and-worksheets"></a>Steuerelemente für Dokumente und Arbeitsblätter

- Gewusst [wie: Hinzufügen von Windows Forms-Steuerelementen zu Office-Dokumenten](../vsto/how-to-add-windows-forms-controls-to-office-documents.md).

- Gewusst [wie: Hinzufügen von Name Drange-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-namedrange-controls-to-worksheets.md)

- Gewusst [wie: Hinzufügen von ListObject-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-listobject-controls-to-worksheets.md)

- Gewusst [wie: Hinzufügen von Windows Forms-Steuerelementen zu Office-Dokumenten](../vsto/how-to-add-windows-forms-controls-to-office-documents.md).

- Gewusst [wie: Hinzufügen von Inhalts Steuerelementen zu Word-Dokumenten](../vsto/how-to-add-content-controls-to-word-documents.md).

- Gewusst [wie: Hinzufügen von Lesezeichen-Steuerelementen zu Word-Dokumenten](../vsto/how-to-add-bookmark-controls-to-word-documents.md)

### <a name="task-panes-in-document-level-customizations"></a>Aufgabenbereiche in Anpassungen auf Dokument Ebene

- Gewusst [wie: Hinzufügen eines Aktionsbereichs zu Word-Dokumenten oder Excel-Arbeits](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)Mappen.

### <a name="task-panes-in-vsto-add-ins"></a>Aufgabenbereiche in VSTO-Add-ins

- Gewusst [wie: Hinzufügen eines benutzerdefinierten Aufgabenbereichs zu einer Anwendung](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)

### <a name="ribbon-customizations"></a>Menü Band Anpassungen

- Gewusst [wie: Starten der Anpassung des Menübands](../vsto/how-to-get-started-customizing-the-ribbon.md).

- Gewusst [wie: Ändern der Position einer Registerkarte im Menüband](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)

- Gewusst [wie: Anpassen einer integrierten Registerkarte](../vsto/how-to-customize-a-built-in-tab.md)

- Gewusst [wie: Hinzufügen von Steuerelementen zur Backstage-Ansicht](../vsto/how-to-add-controls-to-the-backstage-view.md)

- [Vorgehensweise: Exportieren eines Menübands aus dem Menüband-Designer in Menüband-XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md).

### <a name="outlook-form-regions"></a>Outlook-Formularbereiche

- Gewusst [wie: Hinzufügen eines Formular Bereichs zu einem Outlook-Add-in-Projekt](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).

- Gewusst [wie: verhindern der Anzeige eines Formular Bereichs in Outlook](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md).

### <a name="custom-menus"></a>Benutzerdefinierte Menüs

- Gewusst [wie: Hinzufügen von Befehlen zu Kontextmenüs](../vsto/how-to-add-commands-to-shortcut-menus.md)

## <a name="excel-automation-tasks"></a><a name="excel"></a> Excel-Automatisierungsaufgaben

- Gewusst [wie: Programm gesteuertes Anzeigen einer Zeichenfolge in einer Arbeitsblatt Zelle](../vsto/how-to-programmatically-display-a-string-in-a-worksheet-cell.md).

- Gewusst [wie: Programm gesteuertes Erstellen neuer Arbeits](../vsto/how-to-programmatically-create-new-workbooks.md)Mappen

- Gewusst [wie: Programm](../vsto/how-to-programmatically-open-workbooks.md)gesteuertes Öffnen von Arbeitsmappen.

- Vorgehens [Weise: Programm](../vsto/how-to-programmatically-save-workbooks.md)gesteuertes Speichern von Arbeitsmappen.

- Vorgehens [Weise: Programm gesteuertes schließen von Arbeitsmappen](../vsto/how-to-programmatically-close-workbooks.md).

- Gewusst [wie: Programm gesteuertes Hinzufügen neuer Arbeitsblätter zu Arbeits](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)Mappen.

- Gewusst [wie: Programm gesteuertes Ausblenden von Arbeitsblättern](../vsto/how-to-programmatically-hide-worksheets.md).

- Gewusst [wie: Programm gesteuertes Verschieben von Arbeitsblättern in Arbeits](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)Mappen.

- Vorgehens [Weise: Programm](../vsto/how-to-programmatically-protect-workbooks.md)gesteuertes schützen von Arbeitsmappen.

- Gewusst [wie: Programm gesteuertes verweisen auf Arbeitsblatt Bereiche im Code](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md).

- Gewusst [wie: Programm gesteuertes Anwenden von Formaten auf Bereiche in Arbeits](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)Mappen.

- Gewusst [wie: Programm gesteuertes Ändern der Formatierung in Arbeitsblatt Zeilen, die ausgewählte Zellen enthalten](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md).

- Gewusst [wie: Programm gesteuertes suchen nach Text in Arbeitsblatt Bereichen](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md).

- Gewusst [wie: Programm gesteuertes Drucken von Arbeitsblättern](../vsto/how-to-programmatically-print-worksheets.md)

- Gewusst [wie: Programm gesteuertes Ausführen von Excel-Berechnungen](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)

- Gewusst [wie: Programm gesteuertes Sortieren von Daten in Arbeitsblättern](../vsto/how-to-programmatically-sort-data-in-worksheets.md).

## <a name="word-automation-tasks"></a><a name="word"></a> Word-Automatisierungsaufgaben

- Gewusst [wie: Programm gesteuertes Erstellen neuer Dokumente](../vsto/how-to-programmatically-create-new-documents.md).

- Gewusst [wie: Programm gesteuertes Öffnen vorhandener Dokumente](../vsto/how-to-programmatically-open-existing-documents.md).

- Gewusst [wie: Programm](../vsto/how-to-programmatically-save-documents.md)gesteuertes Speichern von Dokumenten.

- Gewusst [wie: Programm gesteuertes schließen von Dokumenten](../vsto/how-to-programmatically-close-documents.md)

- Gewusst [wie: Programm gesteuertes Einfügen von Text in Word-Dokumente](../vsto/how-to-programmatically-insert-text-into-word-documents.md).

- Gewusst [wie: Programm gesteuertes definieren und Auswählen von Bereichen in Dokumenten](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md).

- Gewusst [wie: Programm gesteuertes Zurücksetzen von Bereichen in Word-Dokumenten](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md).

- Gewusst [wie: Programm gesteuertes Formatieren von Text in Dokumenten](../vsto/how-to-programmatically-format-text-in-documents.md).

- Gewusst [wie: Hinzufügen von XMLNode-Steuerelementen zu Word-Dokumenten](../vsto/how-to-add-xmlnode-controls-to-word-documents.md).

- Gewusst [wie: Programm gesteuertes Aktualisieren von Lesezeichen Text](../vsto/how-to-programmatically-update-bookmark-text.md)

- Gewusst [wie: Programm gesteuertes suchen und Ersetzen von Text in Dokumenten](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md).

- Gewusst [wie: Programm gesteuertes Drucken von Dokumenten](../vsto/how-to-programmatically-print-documents.md)

- Gewusst [wie: Programm](../vsto/how-to-programmatically-create-word-tables.md)gesteuertes Erstellen von Word-Tabellen.

- Gewusst [wie: Programm gesteuertes Hinzufügen von Zeilen und Spalten zu Word-Tabellen](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md).

- Gewusst [wie: Programm gesteuertes zählen von Zeichen in Dokumenten](../vsto/how-to-programmatically-count-characters-in-documents.md).

## <a name="data-tasks"></a><a name="data"></a> Daten Aufgaben

### <a name="data-bound-controls"></a>Datengebundene Steuerelemente

- Gewusst [wie: Auffüllen von Arbeitsblättern mit Daten aus einer Datenbank](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)

- Gewusst [wie: Auffüllen von Dokumenten mit Daten aus einer Datenbank](../vsto/how-to-populate-documents-with-data-from-a-database.md).

- Gewusst [wie: Auffüllen von Dokumenten mit Daten aus Diensten](../vsto/how-to-populate-documents-with-data-from-services.md)

- Gewusst [wie: Auffüllen von Dokumenten mit Daten aus Objekten](../vsto/how-to-populate-documents-with-data-from-objects.md).

- Gewusst [wie: Auffüllen von Dokumenten mit Daten aus einer Datenbank](../vsto/how-to-populate-documents-with-data-from-a-database.md).

- Gewusst [wie: Auffüllen von Dokumenten mit Daten aus Diensten](../vsto/how-to-populate-documents-with-data-from-services.md)

- Gewusst [wie: Aktualisieren einer Datenquelle mit Daten eines Host Steuer](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)Elements.

### <a name="cached-data-in-document-level-solutions"></a>Zwischengespeicherte Daten in Projektmappen auf Dokument Ebene

- Gewusst [wie: Zwischenspeichern von Daten zur Offline Verwendung oder auf einem Server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).

- Gewusst [wie: Programm gesteuertes Zwischenspeichern einer Datenquelle in einem Office-Dokument](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md).

- Gewusst [wie: Zwischenspeichern von Daten in einem Kenn Wort geschützten Dokument](../vsto/how-to-cache-data-in-a-password-protected-document.md).

### <a name="custom-xml-data"></a>Benutzerdefinierte XML-Daten

- Gewusst [wie: Hinzufügen benutzerdefinierter XML-Elemente zu Anpassungen auf Dokument Ebene](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md).

- Gewusst [wie: Hinzufügen von benutzerdefinierten XML-Elementen zu Dokumenten mithilfe von VSTO-Add-ins](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md).

## <a name="server-side-document-management-tasks"></a><a name="server"></a> Server seitige Dokument Verwaltungsaufgaben

- Gewusst [wie: Entfernen von Erweiterungen durch verwalteten Code aus Dokumenten](../vsto/how-to-remove-managed-code-extensions-from-documents.md).

- Gewusst [wie: Anfügen von Erweiterungen durch verwalteten Code an Dokumente](../vsto/how-to-attach-managed-code-extensions-to-documents.md)

## <a name="security-tasks"></a><a name="security"></a> Sicherheitsaufgaben

- Gewusst [wie: Signieren von Office](../vsto/how-to-sign-office-solutions.md)-Projektmappen

## <a name="deployment-tasks"></a><a name="deployment"></a> Bereitstellungs Aufgaben

- Gewusst [wie: Veröffentlichen einer Office-Projekt Mappe mithilfe von ClickOnce](/previous-versions/bb386095(v=vs.110)).

- Gewusst [wie: Veröffentlichen einer Office-Projekt Mappe auf Dokument Ebene auf einem SharePoint-Server mithilfe von ClickOnce](/previous-versions/bb608595(v=vs.110)).

- Gewusst [wie: Installieren einer ClickOnce-Office](/previous-versions/bb608592(v=vs.110))-Projekt Mappe.

- Gewusst [wie: Installieren von erforderlichen Komponenten auf Endbenutzer Computern zum Ausführen von Office](/previous-versions/bb608608(v=vs.110))-Projektmappen

- Vorgehens [Weise: Vorbereiten von IIS für die Bereitstellung von Office](/previous-versions/bb608629(v=vs.110))-Projektmappen

- Gewusst [wie: Aktualisieren](/previous-versions/bb157871(v=vs.110))von bereitgestellten Office-Projektmappen

- Gewusst [wie: Ändern des Installations Pfads einer Office](/previous-versions/bb608626(v=vs.110))-Projekt Mappe

## <a name="see-also"></a>Siehe auch
- [Beginnen Sie &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Verfügbare Funktionen nach Office-Anwendung und Projekttyp](../vsto/features-available-by-office-application-and-project-type.md)
- [Office-Entwicklungs Beispiele und Exemplarische Vorgehensweisen](../vsto/office-development-samples-and-walkthroughs.md)