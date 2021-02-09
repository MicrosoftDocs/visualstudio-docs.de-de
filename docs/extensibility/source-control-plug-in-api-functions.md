---
title: API-Funktionen der Quellcodeverwaltungs-Plug-in | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Funktionen, die von der API für Quellcodeverwaltungs-Plug-ins bereitstellen, die vom Quellcodeverwaltungs-Plug-in implementiert werden müssen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, functions
ms.assetid: 4b0536dd-4f92-4ef2-9031-4548281f37aa
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8df7a4be9c8a270feebd7e27d25c006eb4dc5817
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927937"
---
# <a name="source-control-plug-in-api-functions"></a>API-Funktionen von Quellcodeverwaltungs-Plug-Ins
Die Quellcodeverwaltungs-Plug-in-API bietet die folgenden Funktionen, die in Übereinstimmung mit dieser API vom Quellcodeverwaltungs-Plug-in implementiert werden müssen. Die Signaturen der einzelnen Funktionen und der Semantik, die den Bitflags und anderen Parametern zugeordnet sind, werden in dieser Referenz ausführlich beschrieben.

## <a name="initialization-and-housekeeping-functions"></a>Initialisierungs-und Verwaltungsfunktionen

|Funktion|BESCHREIBUNG|
|--------------|-----------------|
|[SccCloseProject](../extensibility/scccloseproject-function.md)|Schließt ein Projekt.|
|[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)|Fordert den Benutzer auf, erweiterte Optionen für den angegebenen Befehl zu erhalten.|
|[SccGetVersion](../extensibility/sccgetversion-function.md)|Gibt die Version des Quellcodeverwaltungs-Plug-ins zurück.|
|[SccInitialize](../extensibility/sccinitialize-function.md)|Initialisiert das Quellcodeverwaltungs-Plug-in. Sie wird einmal für jede Instanz des Plug-Ins aufgerufen.|
|[SccOpenProject](../extensibility/sccopenproject-function.md)|Öffnet ein Projekt.|
|[SccSetOption](../extensibility/sccsetoption-function.md)|Eine generische Funktion, die verwendet wird, um eine Vielzahl von Optionen festzulegen. Jede Option beginnt mit `SCC_OPT_xxx` und verfügt über einen eigenen definierten Satz von Werten.|
|[SccUninitialize](../extensibility/sccuninitialize-function.md)|Wird einmal aufgerufen, wenn ein Quellcodeverwaltungs-Plug-in getrennt werden muss.|

## <a name="core-source-control-functions"></a>Kernfunktionen der Quell Code Verwaltung

|Funktion|BESCHREIBUNG|
|--------------|-----------------|
|[SccAdd](../extensibility/sccadd-function.md)|Fügt ein Array von Dateien, die durch voll qualifizierte Pfadnamen angegeben werden, dem Quell Code Verwaltungssystem hinzu.|
|[SccAddFromScc](../extensibility/sccaddfromscc-function.md)|Ermöglicht es dem Benutzer, Dateien zu suchen, die sich bereits im Quell Code Verwaltungssystem befinden, und diese Dateien dann zu einem Teil des aktuellen Projekts zu machen.|
|[SccCheckin](../extensibility/scccheckin-function.md)|Prüft ein Array von Dateien.|
|[SccCheckout](../extensibility/scccheckout-function.md)|Prüft ein Array von Dateien.|
|[SccDiff](../extensibility/sccdiff-function.md)|Zeigt die Unterschiede zwischen der Datei des lokalen Benutzers, die durch einen voll qualifizierten Pfadnamen angegeben ist, und der Version unter Quell Code Verwaltung an.|
|[SccGet](../extensibility/sccget-function.md)|Ruft eine schreibgeschützte Kopie eines Satzes von Dateien ab.|
|[SccGetEvents](../extensibility/sccgetevents-function.md)|Überprüft den Status der Dateien, die der Aufrufer angefordert hat (via `SccQueryInfo` ).|
|[SccGetProjPath](../extensibility/sccgetprojpath-function.md)|Bewirkt, dass das Quellcodeverwaltungs-Plug-in den Benutzer zur Eingabe eines Projekt Pfads auffordert, der für das Plug-in sinnvoll ist.|
|[SccHistory](../extensibility/scchistory-function.md)|Zeigt den Verlauf eines Arrays von voll qualifizierten lokalen Dateinamen an.|
|[SccPopulateList](../extensibility/sccpopulatelist-function.md)|Überprüft die Liste der Dateien auf Ihren aktuellen Status. Außerdem verwendet die- `pfnPopulate` Funktion, um den Aufrufer zu benachrichtigen, wenn eine Datei nicht mit den Kriterien für übereinstimmt `nCommand` .|
|[SccProperties](../extensibility/sccproperties-function.md)|Zeigt die Eigenschaften einer voll qualifizierten Datei an.|
|[SccQueryInfo](../extensibility/sccqueryinfo-function.md)|Überprüft eine Liste voll qualifizierter Dateien auf Ihren aktuellen Status.|
|[SccRemove](../extensibility/sccremove-function.md)|Entfernt das Array voll qualifizierter Dateien aus dem Quell Code Verwaltungssystem.|
|[SccRename](../extensibility/sccrename-function.md)|Benennt die angegebene Datei in einen neuen Namen im Quell Code Verwaltungssystem um.|
|[SccRunScc](../extensibility/sccrunscc-function.md)|Greift auf den vollständigen Bereich der Features des Quell Code Verwaltungssystems zu.|
|[SccUncheckout](../extensibility/sccuncheckout-function.md)|Macht das Auschecken eines Arrays von Dateien rückgängig.|

## <a name="functions-that-support-additional-capability-version-12-of-the-source-control-plug-in-api"></a>Funktionen, die zusätzliche Funktionen unterstützen (Version 1,2 der Quellcodeverwaltungs-Plug-in-API)
 Diese Gruppe von Funktionen definiert die zusätzlichen Funktionen, die in Version 1,2 der Quellcodeverwaltungs-Plug-in-API enthalten sind. Sie ermöglichen den Zugriff auf Erweiterte Features und Funktionen der Quell Code Verwaltung.

|Funktion|BESCHREIBUNG|
|--------------|-----------------|
|[SccBeginBatch](../extensibility/sccbeginbatch-function.md)|Startet einen Batch Vorgang.|
|[SccCreateSubProject](../extensibility/scccreatesubproject-function.md)|Erstellt ein Unterprojekt mit dem angegebenen Namen unter einem vorhandenen übergeordneten Projekt.|
|[SccDirDiff](../extensibility/sccdirdiff-function.md)|Zeigt die Unterschiede zwischen dem Verzeichnis des lokalen Benutzers an, das durch einen voll qualifizierten Pfadnamen und den Speicherort der Quellcodeverwaltungs-Datenbank angegeben wird.|
|[SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)|Überprüft eine Liste voll qualifizierter Verzeichnisse auf Ihren aktuellen Status.|
|[SccEndBatch](../extensibility/sccendbatch-function.md)|Beendet einen Batch Vorgang.|
|[SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)|Gibt den übergeordneten Pfad des angegebenen Projekts zurück (das Projekt muss vorhanden sein).|
|[SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md)|Überprüft, ob mehrere Auschecken für eine Datei zulässig sind.|
|[SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md)|Überprüft, ob das Plug-in "Mssccprj" erstellt. SCC-Dateien.|

## <a name="functions-that-support-advanced-capability-version-13-of-the-source-control-plug-in-api"></a>Funktionen, die erweiterte Funktionen unterstützen (Version 1,3 der Quellcodeverwaltungs-Plug-in-API)
 Diese Gruppe von Funktionen definiert die zusätzlichen Funktionen, die in Version 1,3 der Quellcodeverwaltungs-Plug-in-API enthalten sind. Sie ermöglichen den Zugriff auf Erweiterte Features und Funktionen der Quell Code Verwaltung.

|Funktion|BESCHREIBUNG|
|--------------|-----------------|
|[SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md)|Fügt eine Liste von Dateien aus der Quell Code Verwaltung zum aktuellen Projekt hinzu.|
|[SccBackgroundGet](../extensibility/sccbackgroundget-function.md)|Ruft eine Liste von Dateien aus der Quell Code Verwaltung ohne Benutzeroberfläche ab.|
|[SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md)|Ruft eine Liste der Dateien in der Quell Code Verwaltung ab, die sich von den lokalen Dateien unterscheiden.|
|[SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md)|Ruft Flags ab, die erweiterte Funktionen angeben, die vom Quellcodeverwaltungs-Plug-in unterstützt werden.|
|[SccGetUserOption](../extensibility/sccgetuseroption-function.md)|Ruft benutzerspezifische Optionen ab.|
|[SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)|Überprüft eine Liste von Verzeichnissen und Dateien in einem Projekt oder in Projekten, die der Quell Code Verwaltung unterliegen. Alle gefundenen Verzeichnis-und Dateinamen werden an eine Rückruffunktion übermittelt.|
|[SccQueryChanges](../extensibility/sccquerychanges-function.md)|Untersucht Namensänderungen, die an einer Liste von Dateien vorgenommen wurden. Jeder Dateiname wird mit seinem Änderungs Status an eine Rückruffunktion übermittelt.|

## <a name="requirements"></a>Anforderungen
 Header: SCC. h

 (Wird im Ordner "Environment SDK Common includes" angegeben, wird standardmäßig *[Laufwerk]* \programme\vsip 8.0 \ envsdk\common\inc; im VSIP-Ordner mit dem MSSCCI-Beispiel *[Laufwerk]* \programme\vsip 8.0 \ MSSCCI) bereitgestellt.

## <a name="see-also"></a>Weitere Informationen
- [Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-ins.md)
- [Erstellen eines Quellcodeverwaltungs-Plug-Ins](../extensibility/internals/creating-a-source-control-plug-in.md)
