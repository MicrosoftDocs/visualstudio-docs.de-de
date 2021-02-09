---
title: 'Test Bereich 3: Überprüfen Sie Out-Undo Checkout | Microsoft-Dokumentation'
description: Dieser Testbereich des Quell Code Verwaltungs-Plug-ins behandelt das Bearbeiten und Wiederherstellen von Elementen aus dem Versionsspeicher mithilfe der Befehle Auschecken und rückgängig machen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, checkout
- source control plug-ins, undo checkout
- source control [Visual Studio SDK], checking out
- source control [Visual Studio SDK], undo checkout
ms.assetid: ce00c5a5-d472-4f45-8776-d77a1fbe9d37
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bb59b0342d67ab9118ffcdba74c177106fcceea0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99898114"
---
# <a name="test-area-3-check-outundo-checkout"></a>Testbereich 3: Auschecken/Auschecken rückgängig machen
Dieser Testbereich der Quell Code Verwaltung umfasst das Bearbeiten und Wiederherstellen von Elementen aus dem Versionsspeicher über die Befehle **Auschecken** und **rückgängig machen** .

**Auschecken**: markiert ein Element im Versionsspeicher als ausgecheckt und ändert die lokale Kopie in den Lese-/Schreibmodus.

Auschecken **rückgängig machen**: markiert ein Element im Versionsspeicher als eingecheckt und setzt vor dem Auschecken eine lokale Kopie in den Zustand zurück (abhängig von den Optionen).

## <a name="command-menu-access"></a>Befehlsmenü Zugriff

Die folgenden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierten Menü Pfade der Entwicklungsumgebung werden in den Testfällen verwendet.

##### <a name="check-out"></a>Auschecken:

- **Datei**, **Quell** Code Verwaltung, **Auschecken**.

- **Datei**, **Auschecken**.

- **Überprüfen Sie** das Kontextmenü.

- Auschecken rückgängig machen: **Datei**, **Quell** Code Verwaltung, **rückgängig machen**

## <a name="common-expected-behavior"></a>Häufiges erwartetes Verhalten

- Nach dem Auschecken werden die Zieldateien und/oder Ordner im Versionsspeicher als ausgecheckt markiert.

- Der Versionsspeicher schreibt das Auschecken dem richtigen Benutzer.

- Uhrzeit und Datum des Auscheck Vorgangs sind korrekt (gemäß den Einstellungen des Benutzers).

## <a name="test-cases"></a>Testfälle

Im folgenden finden Sie spezifische Testfälle für den Testbereich Checkout/rückgängig.

### <a name="case-3a-check-out"></a>Fall 3a: Auschecken

In diesem Abschnitt liegt der Schwerpunkt auf der Ausführung des Auscheck Befehls.

|Aktion|Test Schritte|Erwartete Ergebnisse zur Überprüfung|
|------------|----------------|--------------------------------|
|Exklusives (CoE) ein Client Projekt Auschecken|1. Erstellen Sie ein Client Projekt.<br />2. Fügen Sie die Projekt Mappe der Quell Code Verwaltung hinzu.<br />3. Überprüfen Sie das gesamte Projekt exklusiv (**Datei**, **Auschecken**).|Auschecken.|
|Auschecken eines Dateisystems oder eines lokalen IIS-Webprojekts (CoE)|1. Legen Sie die Webserver Verbindung **mit der Datei** Freigabe unter Extras, **Optionen**, **Projekte** und **Webeinstellungen** fest.<br />2. Erstellen Sie ein Webprojekt.<br />3. Fügen Sie die Projekt Mappe der Quell Code Verwaltung hinzu.<br />4. sehen Sie sich das gesamte Projekt exklusiv an (**Datei**, **Quell** Code Verwaltung, **Auschecken**).|Auschecken.|
|Auschecken von Projektmappenelementen in einer Lösung (neue Methode zum behandeln anderer Dateien)|1. Erstellen Sie eine leere Projekt Mappe.<br />2. Fügen Sie die Projekt Mappe der Quell Code Verwaltung hinzu.<br />3. sehen Sie sich die Lösung an.<br />4. Fügen Sie mehrere Projektmappenelemente hinzu.<br />5. Überprüfen Sie alle neu hinzugefügten Elemente.<br />6. Wählen Sie mehrere Projektmappenelemente aus.<br />7. sehen Sie sich die ausgewählten Elemente an (Kontextmenü, **Auschecken**).|Ausgewählte Dateien werden ausgecheckt.|
|Lokale Version Auschecken (wenn das Plug-in unter Test dieses Feature unterstützt)|1. Benutzer 1: Erstellen Sie ein Client Projekt.<br />2. Benutzer 1: Fügen Sie die Projekt Mappe zur Quell Code Verwaltung hinzu.<br />3. Benutzer 2: Öffnen Sie die Projekt Mappe aus der Quell Code Verwaltung an einem anderen Speicherort.<br />4. Benutzer 2: Auschecken einer Datei.<br />5. Benutzer 2: Ändern Sie die Datei.<br />6. Benutzer 2: Checken Sie die Datei ein.<br />7. Benutzer 1: sehen Sie sich die lokale Version der Datei an (aktivieren Sie die Option "Erweiterte **lokale Version auschecken** " im Dialogfeld " **Auschecken** ").|Die lokale Version der Datei ist ausgecheckt.<br /><br /> Änderungen von Benutzer 2 werden nicht auf die Datei User 1 angewendet.|

### <a name="case-3b-disconnected-check-out"></a>Fall 3B: Auschecken getrennt

Der Betrieb im getrennten Modus ermöglicht Benutzern ein gewisses Maß an Unterstützung der Quell Code Verwaltung, wenn Sie nicht direkt an einen Versionsspeicher angefügt werden. Dies erfolgt durch lokales Zwischenspeichern aller relevanten Informationen über die eingetragene Lösung und die zugehörigen Projekte.

Exklusive Auscheck Vorgänge können nur auftreten, wenn eine Verbindung mit dem Quell Code Verwaltungs Speicher besteht. Freigegebene Auscheck Vorgänge können jederzeit (unabhängig davon, ob verbunden oder getrennt) erfolgen. Aus diesem Grund ist, wenn die Trennung vom Versionsspeicher besteht, nur der Befehl zum **Auschecken Shared** (COS) aktiviert. Wenn die getrennte Version getrennt ist, wird das Auschecken **Rückgängig** gemacht, da die alte Version nicht abgerufen werden kann, um Änderungen zu ersetzen

Wenn der Benutzer erneut eine Verbindung mit dem Versionsspeicher herstellt, werden die Auscheck Zustände aller eingetragenen Lösungen und Projekte synchronisiert. Dadurch werden die erforderlichen Updates für den Speicher für die vom Benutzer ausgeführten Auscheck Vorgänge ausgeführt. Nachdem die Synchronisierung durchgeführt wurde, kann der Benutzer weiterhin wie gewohnt arbeiten (verbunden).

#### <a name="expected-behavior"></a>Erwartetes Verhalten

- Der Befehl zum **Auschecken exklusiv** kann nicht verwendet werden, wenn die Trennung mit dem Versionsspeicher

- Der Befehl " **Rückgängig** Auschecken" kann nicht verwendet werden, wenn die Trennung mit

- Der **Shared Check out** -Befehl funktioniert.

|Aktion|Test Schritte|Erwartete Ergebnisse zur Überprüfung|
|------------|----------------|--------------------------------|
|Wenn Sie getrennt sind, checken Sie eine Datei aus, und verbinden Sie dann die Synchronisierung.|1. Trennen Sie ein kontrolliertes Projekt mithilfe des Dialog Felds "Quell Code Verwaltung ändern" (**Datei**, **Quell** Code Verwaltung, Quell Code Verwaltung **ändern**).<br />2. Überprüfen Sie eine Datei.<br />3. Klicken Sie im Dialogfeld "Warnung" auf "Auschecken (getrennt)".<br />4. Bearbeiten Sie die Datei.<br />5. Verbinden Sie sich über das Dialogfeld Quell Code Verwaltung ändern.<br />6. aktuelle Version der bearbeiteten Datei erhalten.|Häufiges erwartetes Verhalten|

### <a name="case-3c-query-editquery-save-qeqs"></a>Fall 3c: Bearbeiten/Speichern von Abfragen (Query Edit/Query Save, QEQS)
 Elemente unter Quell Code Verwaltung werden für Bearbeitungen, Änderungen und speichern nachverfolgt, damit Benutzer Ihre Dateien problemlos verwalten können. Wenn ein kontrolliertes Element bearbeitet wird, das eingecheckt ist, fängt QEQS den versuchten Bearbeitungsvorgang ab und fordert den Benutzer auf, die Datei zu bearbeiten, um Sie zu bearbeiten. Abhängig von den **Tools** und den **options** Einstellungen ist es entweder erzwungen, dass der Benutzer die Datei auschecken muss, um die Datei zu bearbeiten, oder eine Kopie im Speicher bearbeiten und später Auschecken können. Wenn die **options** Einstellung des Benutzers nicht festgelegt **ist, um** das Dialogfeld "Auschecken" anzuzeigen und einfach auszuchecken, wird die Datei nach Möglichkeit automatisch ausgecheckt, wenn dies möglich ist.

#### <a name="expected-behavior"></a>Erwartetes Verhalten

- Nach dem Auschecken werden die Zieldateien und/oder Ordner im Versionsspeicher als ausgecheckt markiert.

- Der Versionsspeicher führt das Auschecken dem richtigen Benutzer aus.

- Die Uhrzeit und das Datum der Überprüfung sind korrekt (gemäß den Einstellungen des Benutzers).

- Die lokale Kopie der Zieldatei oder des Ziel Ordners ist beschreibbar.

|Aktion|Test Schritte|Erwartete Ergebnisse zur Überprüfung|
|------------|----------------|--------------------------------|
|Textdatei bearbeiten, die eingeklickt ist|1. Erstellen Sie ein neues Projekt, das eine Textdatei enthält.<br />2. Fügen Sie die Projekt Mappe der Quell Code Verwaltung hinzu.<br />3. Legen Sie **Tools**, **Optionen** und **Quell** Code Verwaltung fest, lassen Sie die Bearbeitung **von Dateien** zu, während schreibgeschützt auf dem Datenträger aktiviert ist.<br />4 **. legen** Sie Extras, **Optionen**, **Quell** Code Verwaltung, **Aufforderung zum Auschecken** im Kombinations Feld bei Bearbeitung von **Dateien aktiviert** fest.<br />5 **. legen** Sie Extras, **Optionen** und **Quell** Code Verwaltung fest, und **Aktivieren Sie das Kontroll** Kästchen **Wenn eingecheckte Dateien gespeichert werden** .<br />6. Öffnen Sie die Textdatei im Editor, und versuchen Sie, neuen Text in die Datei einzugeben. Wenn dieser Schritt erfolgreich ist, fahren Sie mit dem nächsten Schritt fort.<br />7. Klicken Sie im Dialogfeld " **Auschecken zum Bearbeiten** " auf " **Abbrechen** ". Wenn dieser Schritt erfolgreich ist, fahren Sie mit dem nächsten Schritt fort.<br />8. Legen Sie **Tools**, **Optionen** und **Quell** Code Verwaltung fest, gestatten Sie die Bearbeitung **von Dateien, während Sie auf** dem Datenträger schreibgeschützt sind.<br />9. Öffnen Sie die Projektdatei im Editor, und versuchen Sie, neuen Text in der Datei einzugeben. Wenn dieser Schritt erfolgreich ist, fahren Sie mit dem nächsten Schritt fort.<br />10. Klicken Sie im Dialogfeld **Auschecken zum Bearbeiten** auf **Bearbeiten** . Wenn dieser Schritt erfolgreich ist, fahren Sie mit dem nächsten Schritt fort.<br />11. Bearbeiten Sie die Textdatei, und versuchen Sie, Sie zu speichern.|`Result of step 6:`<br /><br /> Das Dialogfeld zum Bearbeiten Auschecken wird angezeigt.<br /><br /> `Result of step 7:`<br /><br /> Die Datei ist unverändert.<br /><br /> `Result of step 9:`<br /><br /> Das Dialogfeld zum Bearbeiten Auschecken wird angezeigt.<br /><br /> `Result of step 10:`<br /><br /> Sie können die Projektdatei im Arbeitsspeicher bearbeiten.<br /><br /> `Result of step 11:`<br /><br /> Beim Speichern wird das Dialogfeld Auschecken beim Speichern angezeigt.|
|Bearbeiten einer in eingecheckten Projektmappendatei|Wiederholen Sie die Schritte wie im vorherigen Test beschrieben. ändern Sie die Projekt Mappe jedoch nicht, indem Sie die Projektmappeneigenschaften ändern.|Identisch mit dem vorherigen Test|
|Bearbeiten einer in eingecheckten Projektdatei|Wiederholen Sie die Schritte, wie im vorherigen Test beschrieben, aber ändern Sie das Projekt, anstatt eine Textdatei zu ändern, indem Sie die Projekteigenschaften ändern.|Identisch mit dem vorherigen Test.|

### <a name="case-3d-silent-check-out"></a>Case 3D: Silent Check out
 In diesem Unterbereich werden Szenarios behandelt, in denen das Dialogfeld " **Auschecken** " nicht gemäß den **Tools**, **Optionen** und **Einstellungen der Quell** Code Verwaltung des Benutzers angezeigt wird.

#### <a name="expected-behavior"></a>Erwartetes Verhalten

- Nach dem Auschecken werden die Zieldateien und/oder Ordner im Versionsspeicher als ausgecheckt markiert.

- Der Versionsspeicher führt das Auschecken dem richtigen Benutzer aus.

- Die Uhrzeit und das Datum der Überprüfung sind korrekt (gemäß den Einstellungen des Benutzers).

- Die lokale Kopie der Zieldatei oder des Ziel Ordners ist beschreibbar.

|Aktion|Test Schritte|Erwartete Ergebnisse zur Überprüfung|
|------------|----------------|--------------------------------|
|Automatisches Auschecken für eine Datei|1. Legen Sie **Tools**, **Optionen** und **Quell** Code Verwaltung fest, um **Dateien beim Bearbeiten automatisch auszuchecken**.<br />2. Erstellen Sie ein neues Projekt mit einer Datei.<br />3. Fügen Sie die Projekt Mappe der Quell Code Verwaltung hinzu.<br />4. sehen Sie sich die Datei an.|Die Datei wird im Hintergrund ausgecheckt (keine Benutzeroberfläche).|
|Automatisches Auschecken für ein Projekt|1. Legen Sie **Tools**, **Optionen** und **Quell** Code Verwaltung fest, um **Dateien beim Bearbeiten automatisch auszuchecken**.<br />2. Erstellen Sie ein neues Projekt.<br />3. Fügen Sie die Projekt Mappe der Quell Code Verwaltung hinzu.<br />4. sehen Sie sich das Projekt an.|Die Datei wird im Hintergrund ausgecheckt (keine Benutzeroberfläche).|

### <a name="case-3e-undo-check-out"></a>Fall 3e: Auschecken rückgängig machen
 **Auschecken rückgängig** wird verwendet, um den ausgecheckten Status einer Datei abzubrechen und das Einchecken von Änderungen an der Datei zu vermeiden.

#### <a name="expected-behavior"></a>Erwartetes Verhalten

- Der Standardwert basiert auf der Einstellung der **lokalen Version** des Benutzers. Wenn der Benutzer die lokale Version auschecken möchte, ist die Standardeinstellung für das Auschecken rückgängig, dass immer auf die ausgecheckte Version zurückgegriffen wird.

- Bei der Annahme der Rückgängigmachen werden die Symbole in **Projektmappen-Explorer** für betroffene Dateien aktualisiert, und das Element wird aus dem Fenster **anstehende Eincheck** Vorgänge entfernt.

|Aktion|Test Schritte|Erwartete Ergebnisse zur Überprüfung|
|------------|----------------|--------------------------------|
|Rückgängig machen einer einzelnen Datei, die exklusiv ausgecheckt ist|1. Erstellen Sie ein Client Projekt.<br />2. Fügen Sie die Projekt Mappe der Quell Code Verwaltung hinzu.<br />3. Überprüfen Sie exklusiv eine Datei.<br />4. ändern Sie die Datei.<br />5. rückgängig machen (**Datei**, **Quell** Code Verwaltung, Auschecken **rückgängig machen**).|Häufiges erwartetes Verhalten.|
|Auschecken einer einzelnen Datei, die freigegeben ist, rückgängig machen|1. Erstellen Sie ein Client Projekt.<br />2. Fügen Sie die Projekt Mappe der Quell Code Verwaltung hinzu.<br />3. sehen Sie sich eine freigegebene Datei an.<br />4. ändern Sie die Datei.<br />5. rückgängig machen (**Datei**, **Quell** Code Verwaltung, Auschecken **rückgängig machen**).|Häufiges erwartetes Verhalten.|
|Auschecken eines Projekts nach dem Hinzufügen von Dateien zum Projekt rückgängig machen|1. Erstellen Sie ein neues Projekt, und fügen Sie es der Quell Code Verwaltung hinzu.<br />2. sehen Sie sich das Projekt an.<br />3. Fügen Sie dem Projekt eine Datei hinzu.<br />4. rückgängig machen des Projekts.|Die hinzugefügte Datei wurde aus dem Projekt in Projektmappen-Explorer entfernt.<br /><br /> Das Projekt ist nicht mehr ausgecheckt.|
|Auschecken eines Projekts nach dem Löschen von Dateien aus dem Projekt rückgängig machen|1. Erstellen Sie ein neues Projekt, und fügen Sie es der Quell Code Verwaltung hinzu.<br />2. sehen Sie sich das Projekt an.<br />3. löschen Sie eine Datei aus dem Projekt.<br />4. rückgängig machen des Projekts.|Die gelöschte Datei wird unter dem Projekt in Projektmappen-Explorer angezeigt.<br /><br /> Das Projekt ist nicht mehr ausgecheckt.|

## <a name="see-also"></a>Weitere Informationen
- [Testleitfaden für Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
