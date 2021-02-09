---
title: 'Test Bereich 7: Freigeben | Microsoft-Dokumentation'
description: Dieser Quell Code Verwaltungs Testbereich deckt das Freigeben von Elementen Zwischenstand Orten mithilfe des Befehls "freigeben" für das Visual Studio-Quellcodeverwaltungs-Plug-in ab.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], sharing items
- source control plug-ins, sharing items
ms.assetid: 6ec4780a-bda4-4327-bb3e-c6c9e7eabf35
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5c006c5f4746f83e571475d93bedc452c7c23c75
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888133"
---
# <a name="test-area-7-share"></a>Testbereich 7: Freigeben
In diesem Testbereich wird das Freigeben von Elementen Zwischenstand Orten über den **Freigabe** Befehl behandelt.

 Bei einem hhare-Vorgang handelt es sich um die offensichtliche Duplizierung von Dateien und Ordner Elementen zwischen mindestens zwei Speicherorten in einer Quell Code Verwaltungs Datei Hierarchie. Die Duplizierung erfolgt nicht wirklich auf dem Server, aber der Benutzer sieht dieselbe Datei an zwei oder mehr angegebenen Speicherorten. Wenn an einem der freigegebenen Elemente Änderungen vorgenommen werden, werden diese Änderungen an allen anderen freigegebenen Speicherorten angezeigt.

 Die Freigabe in Ordner funktioniert, wenn Sie einen Ordner auswählen, in dem sich mindestens eine Datei unter Quell Code Verwaltung befindet. Der Freigabe Befehl ist unter den folgenden Bedingungen deaktiviert:

- , Wenn es sich bei dem ausgewählten Ordner um einen leeren Ordner handelt.

- Wenn ein echter Ordner vorhanden ist, jedoch keine Quell Code Verwaltungs Dateien vorhanden sind.

- Wenn ein virtueller Ordner vorhanden ist, ob sich die Dateien in der Quell Code Verwaltung befinden oder nicht.

- , Wenn ein Remoteweb Projekt vorhanden ist.

## <a name="command-menu-access"></a>Befehlsmenü Zugriff
 Die folgenden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierten Menü Pfade der Entwicklungsumgebung werden in den Testfällen verwendet.

 Freigabe: Freigabe der **Datei** -> **Quell** Code Verwaltung -> .

## <a name="expected-behavior"></a>Erwartetes Verhalten

- Freigegebene Dateien werden am freigegebenen Speicherort angezeigt.

- Wenn Sie den Versionsspeicher Verlauf der Quell Code Verwaltung anzeigen, wird angezeigt, dass die Datei freigegeben ist.

- Beim Bearbeiten einer freigegebenen Datei werden die beiden Speicherorte der Datei bearbeitet.

## <a name="test-cases"></a>Testfälle
 Im folgenden finden Sie spezifische Testfälle für den Freigabe Testbereich.

|Aktion|Test Schritte|Erwartete Ergebnisse zur Überprüfung|
|------------|----------------|--------------------------------|
|Freigeben einer Datei aus einem geladenen Projekt unter Quell Code Verwaltung in ein anderes geladenes Projekt|1. Erstellen Sie ein neues Projekt.<br />2. Fügen Sie der Projekt Mappe ein zweites Projekt hinzu.<br />3. Erstellen Sie eine Datei im zweiten Projekt mit einem Namen, der sich nicht im ersten Projekt befindet.<br />4. Fügen Sie die Projekt Mappe der Quell Code Verwaltung hinzu.<br />5. Wählen Sie das erste Projekt aus.<br />6. Öffnen Sie das Dialogfeld **Freigabe** (**Datei**  ->    ->  **Freigabe-Freigabe Freigabe**).<br />7. Geben Sie die Datei aus dem zweiten Projekt für das erste Projekt frei.<br />8. Wenn Sie dazu aufgefordert werden **, überprüfen Sie** .|Häufiges erwartetes Verhalten.|
|Freigeben einer Datei von einem Projekt in ein anderes|1. Erstellen Sie ein neues Projekt.<br />2. Fügen Sie Sie der Quell Code Verwaltung hinzu.<br />3. Schließen Sie die Projekt Mappe.<br />4. Erstellen Sie ein zweites Projekt (neue Projekt Mappe).<br />5. Fügen Sie die Projekt Mappe der Quell Code Verwaltung hinzu.<br />6. Wählen Sie das Projekt aus.<br />7. Öffnen Sie das Dialogfeld " **Freigeben** " (**Datei**  ->    ->  **Freigabe-Freigabe**).<br />8. Geben Sie eine Datei aus dem zuvor hinzugefügten Projekt dem geöffneten Projekt frei.<br />9. Wenn Sie dazu aufgefordert werden **, überprüfen**|Häufiges erwartetes Verhalten.|
|Freigeben einer Datei, die nicht Teil des Projekts ist, aus der Quell Code Verwaltung in das zurzeit geladene Projekt|1. Erstellen Sie ein neues Projekt.<br />2. Fügen Sie die Projekt Mappe der Quell Code Verwaltung hinzu.<br />3. Fügen Sie der Quell Code Verwaltung eine Datei hinzu, die nicht Teil des Projekts oder der Projekt Mappe ist.<br />4. Wählen Sie das Projekt aus, und öffnen Sie das Dialogfeld **Freigeben** (**Datei**  ->    ->  **Freigabe-Freigabe**).<br />5. Wählen Sie eine Datei im Dialogfeld **Freigeben** aus, die im aktuellen Projekt oder in der aktuellen Projekt Mappe nicht vorhanden ist, und geben Sie Sie frei.<br />6. Wenn Sie dazu aufgefordert werden **, überprüfen**|Der Quell Code Verwaltungs Speicher hat einen Get-Vorgang durchgeführt, sodass sich die Datei jetzt am lokalen Speicherort des Projekts befindet.|
|Freigeben von Dateien innerhalb desselben Projekts in einem anderen Ordner|1. wählen **Sie unter Extras** Optionen Quell Code Verwaltung die Option **automatisch Auschecken aus**  ->    ->  .<br />2. Erstellen Sie ein neues Projekt, und fügen Sie es der Quell Code Verwaltung hinzu.<br />3. Fügen Sie dem Projekt einen Ordner hinzu.<br />4. Fügen Sie dem Ordner eine Datei hinzu, und checken Sie den Ordner ein.<br />5. Wählen Sie den Ordner aus.<br />6. Öffnen Sie das Dialogfeld **Freigabe** (**Datei**  ->    ->  **Freigabe-Freigabe Freigabe**).<br />7. Geben Sie die Datei für den ausgewählten Ordner frei.|Häufiges erwartetes Verhalten.<br /><br /> Der Ordner muss mit einer darin ausgecheckten Datei eingeglichen werden, bevor er für die Freigabe verwendet werden kann.|
|Freigeben eines Ordners im geladenen Projekt – rekursiv|1. Erstellen Sie ein neues Projekt.<br />2. Fügen Sie die Projekt Mappe der Quell Code Verwaltung hinzu.<br />3. Wählen Sie das Projekt aus.<br />4. Öffnen Sie das Dialogfeld " **Freigeben** " (**Datei**  ->    ->  **Freigabe-Freigabe**).<br />5. Wählen Sie einen Ordner aus.<br />6. Geben Sie den Ordner rekursiv in das Projekt ein.|Häufiges erwartetes Verhalten.|
|Freigeben mehrerer Dateien von einem Projekt in ein anderes|1. Erstellen Sie ein neues Projekt mit mehreren darin erstellten Dateien.<br />2. Fügen Sie die Projekt Mappe der Quell Code Verwaltung hinzu.<br />3. Schließen Sie die Projekt Mappe.<br />4. Erstellen Sie ein neues Projekt in einer neuen Projekt Mappe.<br />5. Fügen Sie die Projekt Mappe der Quell Code Verwaltung hinzu.<br />6. Wählen Sie das Projekt aus.<br />7. Öffnen Sie das Dialogfeld " **Freigeben** " (**Datei**  ->    ->  **Freigabe-Freigabe**).<br />8. Freigeben mehrerer Dateien aus dem zuvor erstellten Projekt für das aktuell geöffnete Projekt.|Häufiges erwartetes Verhalten.|

## <a name="see-also"></a>Weitere Informationen
- [Testleitfaden für Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
