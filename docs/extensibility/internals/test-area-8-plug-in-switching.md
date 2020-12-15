---
title: 'Test Bereich 8: Plug-in-Wechsel | Microsoft-Dokumentation'
description: Dieser Bereich der Quell Code Verwaltung enthält Testfälle für die Auswahl des Plug-ins, das für die Quell Code Verwaltung von Projektmappen in Visual Studio verwendet werden soll.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], switching plug-ins
- source control plug-ins, switching
ms.assetid: 01370792-b5da-4e46-9ce2-7dd326587141
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b6c3a25aa9312073d3ce4a60752d41585fcee7b3
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97487646"
---
# <a name="test-area-8-plug-in-switching"></a>Testbereich 8: Plug-In-Wechsel
Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierte Entwicklungsumgebung (Integrated Development Environment, IDE) verfügt über die Benutzeroberfläche (UI), um das aktuelle Quellcodeverwaltungs-Plug-in zu ändern. Dieser Testbereich enthält Testfälle für die Auswahl des Plug-ins, das für die Quell Code Verwaltung der Projekt Mappe verwendet werden soll.

## <a name="command-menu-access"></a>Befehlsmenü Zugriff
 Die folgenden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierten Menü Pfade der Entwicklungsumgebung werden in den Testfällen verwendet.

- Aktuelles Quellcodeverwaltungs-Plug- **in: Extras**  ->  **Optionen**  ->  **Quellcodeverwaltungs**-  ->  **Plug-in-Auswahl**.

- Quell Code Verwaltungs Bindung ändern: Quell Code Verwaltung der **Datei** Quell Code Verwaltung wird geändert  ->    ->  ...

## <a name="common-expected-behavior"></a>Häufiges erwartetes Verhalten
 Das Ändern des Quellcodeverwaltungs-Plug-Ins für eine Lösung ist möglich, ohne Visual Studio zu beenden oder die Projekt Mappe erneut zu laden. Außerdem wechselt das aktuelle Quellcodeverwaltungs-Plug-in automatisch zu dem, das von einer Lösung verwendet wird, wenn diese Projekt Mappe geladen wird.

## <a name="test-cases"></a>Testfälle
 Im folgenden finden Sie spezifische Testfälle für das Plug-in-Wechseln des Testbereichs.

### <a name="case-8a-automatic-change"></a>Fall 8a: Automatische Änderung

#### <a name="expected-behavior"></a>Erwartetes Verhalten
 Wenn ein Benutzer eine Projekt Mappe lädt, die der Quell Code Verwaltung unterliegt, wird die Projekt Mappe automatisch geladen, und das entsprechende Quellcodeverwaltungs-Plug-in wird als aktuell ausgewählt.

| Aktion | Test Schritte | Erwartete Ergebnisse zur Überprüfung |
| - | - | - |
| Automatische Änderung der Quellcodeverwaltungs-Plug-in | 1. Wählen Sie das Plug-in unter Test as **Current (Extras**  ->  **Optionen**  ->  **Quellcodeverwaltungs**-  ->  **Plug-in-Auswahl**).<br />2. Erstellen Sie ein neues Projekt.<br />3. Fügen Sie die Projekt Mappe der Quell Code Verwaltung hinzu.<br />4. Wählen Sie ein anderes Plug-in aus (z. b [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] .).<br />5. Aufforderung zum Entladen der Projekt Mappe akzeptieren.<br />6. Öffnen Sie die Projekt Mappe erneut vom Datenträger. | Die Projekt Mappe wird geöffnet.<br /><br /> Das unter Test-Plug-in ist das aktuelle Quellcodeverwaltungs-Plug-in. |

### <a name="case-8b-solution-based-change"></a>Fall 8b: Projektmappenbasierte Änderung

#### <a name="expected-behavior"></a>Erwartetes Verhalten
 Das zugehörige Quellcodeverwaltungs-Plug-in kann in der Lösung geändert werden.

| Aktion | Test Schritte | Erwartete Ergebnisse zur Überprüfung |
|----------------------------------| - | - |
| Änderung des Plug-Ins für eine Lösung | 1. Wählen Sie das Plug-in unter Test as **Current (Extras**  ->  **Optionen**  ->  **Quellcodeverwaltungs**-  ->  **Plug-in-Auswahl**) aus.<br />2. Erstellen Sie ein neues Projekt und eine Projekt Mappe.<br />3. Fügen Sie die Projekt Mappe der Quell Code Verwaltung hinzu.<br />4. heben Sie die Bindung der Projekt Mappe aus der Quell Code Verwaltung auf (über das Dialogfeld Quell Code Verwaltung **ändern** ).<br />5. Wählen Sie ein anderes Plug-in aus (z. b [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] .).<br />6. Laden Sie die Projekt Mappe beim Entladen von der Festplatte neu.<br />7. Fügen Sie die Projekt Mappe der Quell Code Verwaltung hinzu.<br />8. heben Sie die Bindung der Projekt Mappe aus der Quell Code Verwaltung auf (im Dialogfeld Quell Code Verwaltung **ändern** ).<br />9. Wählen Sie das Plug-in unter Test erneut aus.<br />10. Laden Sie die Projekt Mappe beim Entladen von der Festplatte neu<br />11. binden Sie die Projekt Mappe an den ursprünglichen Speicherort (über das Dialogfeld Quell Code Verwaltung **ändern** ). | Die Projekt Mappe wird mit dem ausgewählten Plug-in zur Quell Code Verwaltung hinzugefügt. |

## <a name="see-also"></a>Weitere Informationen
- [Testleitfaden für Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
