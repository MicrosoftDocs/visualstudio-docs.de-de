---
title: 'Test Bereich 2: aus Quell Code Verwaltung beziehen | Microsoft-Dokumentation'
description: In diesem Testbereich werden Testfälle zum Abrufen von Elementen aus dem Versionsspeicher mit Get behandelt. Diese Testfälle können sowohl auf lokale als auch auf Webprojekte angewendet werden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, getting items from source control
- source control [Visual Studio SDK], getting items from
ms.assetid: cbd345c5-ca43-4630-b7a4-85564f4e2090
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 98ed765f78a9e7330e5e1d3864c8a91b63239a3f
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877701"
---
# <a name="test-area-2-get-from-source-control"></a>Testbereich 2: Abrufen aus der Quellcodeverwaltung
In diesem Testbereich werden Testfälle zum Abrufen von Elementen aus dem Versionsspeicher über den get-Befehl behandelt. Diese Testfälle können sowohl auf lokale als auch auf Webprojekte angewendet werden.

## <a name="command-menu-access"></a>Befehlsmenü Zugriff
 Die folgenden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierten Menü Pfade der Entwicklungsumgebung werden in den Testfällen verwendet.

##### <a name="get-latest-version"></a>Aktuelle Version erhalten:

- **Datei**, **Quell** Code Verwaltung, **aktuelle Version erhalten**.

- **Datei**, **aktuelle Version erhalten**.

- Kontextmenü, **aktuelle Version erhalten**.

- Get: **File**, **Source Control**, **Get**.

## <a name="expected-behavior"></a>Erwartetes Verhalten

##### <a name="get-latest-version"></a>Aktuelle Version erhalten:
 Führt einen unbeaufsichtigten Abruf (keine Benutzeroberfläche) der aktuellen Version des Elements aus dem Versionsspeicher aus.

##### <a name="get"></a>Get:
 Zeigt das **Dialogfeld** abrufen an und ermöglicht es dem Benutzer, Änderungen am abzurufenden Dateisatz vorzunehmen und die Optionen zu ändern, die sich auf die Art und Weise auswirken, wie die Dateien abgerufen werden.

## <a name="test-cases"></a>Testfälle

|Aktion|Test Schritte|Erwartete Ergebnisse zur Überprüfung|
|------------|----------------|--------------------------------|
|Neueste Version einer Datei, die nicht lokal vorhanden ist, erhalten|1. Erstellen Sie ein Projekt.<br />2. Fügen Sie dem Projekt ein Element hinzu.<br />3. Platzieren Sie das Projekt unter Quell Code Verwaltung.<br />4. Löschen der lokalen Kopie des Elements.<br />5. aktuellste Version des Elements erhalten (Kontextmenü, **neueste Version erhalten**).|Die Element Datei wird lokal abgerufen.|
|Ruft eine Datei ab, die nicht lokal vorhanden ist.|1. Erstellen Sie ein Projekt.<br />2. Fügen Sie dem Projekt ein Element hinzu.<br />3. Platzieren Sie das Projekt unter Quell Code Verwaltung.<br />4. Löschen der lokalen Kopie des Elements.<br />5. beziehen Sie das Element (**Datei**, **Quell** Code Verwaltung, **Get** \<item> ).|Die Element Datei wird lokal abgerufen.|
|Datei erhalten, die exklusiv ausgecheckt und lokal geändert wurde|1. Erstellen Sie ein Projekt.<br />2. Fügen Sie dem Projekt ein Element hinzu.<br />3. Platzieren Sie das Projekt unter Quell Code Verwaltung.<br />4. Überprüfen Sie das Projekt Element exklusiv.<br />5. ändern Sie die lokale Kopie.<br />6. aktuelle Version des Elements (**Datei**, **neueste Version von** \<item> ) erhalten. Wenn dieser Schritt erfolgreich ist, fahren Sie mit dem nächsten Schritt fort.<br />7. Klicken Sie im Warnungs Dialogfeld auf die Schaltfläche **ersetzen** .|**Aus Schritt 6 erneut ausführen**`:`<br /><br /> Dialogfeld "Warnung" zeigt an, dass die Datei ausgecheckt ist.<br /><br /> **Führen Sie erneut aus Schritt 7:**<br /><br /> Die geänderte lokale Datei wird durch die ursprüngliche Version aus dem Versionsspeicher ersetzt.<br /><br /> Die Datei ist Lese-/Schreibzugriff.|
|Dient zum Anfordern und Ersetzen von Dateien, die ausgecheckt, freigegeben und lokal geändert werden.|1. Erstellen Sie ein neues Projekt.<br />2. Fügen Sie dem Projekt ein Element hinzu.<br />3. Platzieren Sie das Projekt unter Quell Code Verwaltung.<br />4. sehen Sie sich das Projekt Element als freigegeben an.<br />5. ändern Sie die lokale Kopie.<br />6. aktuelle Version des Elements (**Datei**, **neueste Version von** \<item> ) erhalten. Wenn dieser Schritt erfolgreich ist, fahren Sie mit dem nächsten Schritt fort.<br />7. Klicken Sie im Dialogfeld "Warnung" auf **ersetzen** .|**Ergebnis aus Schritt 6:**<br /><br /> Dialogfeld "Warnung" zeigt an, dass die Datei ausgecheckt ist.<br /><br /> **Ergebnis aus Schritt 7:**<br /><br /> Die geänderte lokale Datei wird durch die ursprüngliche Version aus dem Versionsspeicher ersetzt.<br /><br /> Die Datei ist Lese-/Schreibzugriff.|
|Ruft eine Datei ab, die lokal vorhanden ist, identisch mit der aktuellen Version im Versionsspeicher.|1. Erstellen Sie ein neues Projekt.<br />2. Fügen Sie dem Projekt ein Element hinzu.<br />3. Platzieren Sie das Projekt unter Quell Code Verwaltung.<br />4. beziehen Sie das Element (**Datei**, **Quell** Code Verwaltung, **Get** \<item> ).|Die lokale Datei ist unverändert.|
|Eine Projekt Mappe mit einem Projekt erhalten|1. Erstellen Sie eine Projekt Mappe mit einem Projekt.<br />2. Platzieren Sie die Projekt Mappe unter Quell Code Verwaltung.<br />3. löschen Sie alle Projektdateien lokal.<br />4. Holen Sie sich die Projekt **Mappe (Datei**, **Quell** Code Verwaltung, **Get**).|Alle gelöschten Dateien werden lokal wieder hergestellt.|

## <a name="see-also"></a>Weitere Informationen
- [Testleitfaden für Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
