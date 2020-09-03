---
title: Optionsseite, Eigenschaften des Knotens „Debuggen“ | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 564cc8b2-0084-420e-b560-200cc5621a7e
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 10537fb64e6ae0ebbe185024b76442704437e273
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668840"
---
# <a name="options-page-debugging-node-properties"></a>Optionsseite, Eigenschaften des Knotens 'Debuggen'
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

In den folgenden Tabellen werden die Seiten (bzw. Eigenschaftenauflistungen) beschrieben, die der Kategorie **Debugging**`DTE.Properties("Debugging", <Property Page>)` im Dialogfeld **Optionen** zugeordnet sind.

## <a name="general"></a>Allgemein
 `DTE.Properties("Debugging", "General")`

|Eigenschaftenelementname|Wert|BESCHREIBUNG|
|------------------------|-----------|-----------------|
|PromptOnBreakpointDelete|Get/Set (boolesch)|Bestimmt, ob der Debugger vor dem Löschen aller Haltepunkte in einem Projekt zur Bestätigung auffordert.|
|BreakAllProcesses|Get/Set (boolesch)|Bestimmt, ob der Debugger alle Prozesse unterbricht, sobald ein einzelner Prozess unterbrochen wird.|
|BreakAtBoundaries|Get/Set (boolesch)|Bestimmt, ob der Debugger die Ausführung unterbricht, wenn eine Ausnahme eine Grenze zwischen AppDomains oder zwischen verwaltetem und systemeigenem Code überschreitet.|
|EnableAddressLevelDebugging|Get/Set (boolesch)|Bestimmt, ob Debugfeatures auf Adressebene aktiviert werden.|
|ShowDisassemblyIfNoSource|Get/Set (boolesch)|Bestimmt, ob der Debugger Disassemblycode anzeigt, wenn Quellcode nicht verfügbar ist.|
|EnableBreakpointFilters|Get/Set (boolesch)|Bestimmt, ob die Haltepunktfilterung aktiviert ist.|
|EnableExceptionAssistant|Get/Set (boolesch)|Bestimmt, ob der Ausnahmen-Assistent für verwaltete Ausnahmen verwendet wird.|
|UnwindCallstack|Get/Set (boolesch)|Bestimmt, ob der Debugger die Aufrufliste für eine nicht behandelte Ausnahme entlädt.|
|EnableJustMyCode|Get/Set (boolesch)|Bestimmt, ob "Nur mein Code" für C#- und Visual Basic-Code aktiviert ist.|
|ShowAllMembers|Get/Set (boolesch)|Bestimmt für Nichtbenutzerobjekte, ob der Debugger alle Objektmember in den Variablenfenstern anzeigt. Diese Option ist nur wirksam, wenn "Nur mein Code" aktiviert ist.|
|WarnIfNoUserCode|Get/Set (boolesch)|Bestimmt, ob der Debugger eine Warnung ausgibt, wenn der Benutzer eine Verbindung mit einem Prozess herzustellen versucht, der keinen Benutzercode enthält. Diese Option ist nur wirksam, wenn "Nur mein Code" aktiviert ist.|
|EnablePropertyEvaluation|Get/Set (boolesch)|Bestimmt, ob der Debugger Eigenschaften und implizite Funktionsaufrufe in verwaltetem Code automatisch auswertet.|
|CallStringConversion|Get/Set (boolesch)|Bestimmt, ob der Debugger in den Variablenfenstern eine Zeichenfolgenkonvertierungsfunktion für Objekte implizit aufruft. Diese Option gilt nur für C#- und JScript-Code.|
|EnableSourceServer|Get/Set (boolesch)|Bestimmt, ob der Debugger auf Code von einem Quellserver zugreifen kann.|
|PrintSourceServerDiagnostics|Get/Set (boolesch)|Bestimmt, ob das Ausgabefenster Diagnosemeldungen über den Quellserver anzeigt. Diese Option nur wirksam, wenn der Zugriff auf den Quellserver aktiviert ist.|
|HighlightEntireLine|Get/Set (boolesch)|Bestimmt, ob der Debugger eine ganze Zeile für Haltepunkte und die aktuelle Anweisung hervorhebt.|
|RequireSourceToMatch|Get/Set (boolesch)|Bestimmt, ob der Debugger verlangt, dass Quelldateien genau mit der Originalversion übereinstimmen müssen, wenn Sie Dateien zum Debuggen öffnen.|
|RedirectOutputToImmediate|Get/Set (boolesch)|Bestimmt, ob die Ausgabe des Ausgabefensters zum Direktfenster umgeleitet wird.|
|ShowRawVariableStructure|Get/Set (boolesch)|Bestimmt, ob Objekte in den Variablenfenstern in unformatierter Form angezeigt werden.|
|SuppressJitOptimization|Get/Set (boolesch)|Bestimmt bei verwaltetem Code, ob Just-In-Time-Optimierung vom Debugger unterdrückt wird.|
|WarnIfNoSymbols|Get/Set (boolesch)|Bestimmt, ob der Debugger eine Warnung anzeigt, wenn beim Starten eines Prozesses keine Debugsymbole verfügbar sind.|
|WarnIfScriptDisabled|Get/Set (boolesch)|Bestimmt, ob der Debugger eine Warnung anzeigt, wenn beim Starten eines Prozesses das Skriptdebuggen nicht aktiviert ist.|
|ShowMarkersForAllThreads|Get/Set (boolesch)|Bestimmt, ob der Debugger Threadmarker anzeigt.|
|StepOverPropertiesAndOperators|Get/Set (boolesch)|Gibt an, ob Eigenschaften und Operatoren übersprungen werden (nur in verwaltetem Code).|

## <a name="edit-and-continue"></a>Bearbeiten und Fortfahren
 `DTE.Properties("Debugging", "EditAndContinue")`

|Eigenschaftenelementname|Wert|BESCHREIBUNG|
|------------------------|-----------|-----------------|
|EnableEditAndContinue|Get/Set (boolesch)|Bestimmt, ob Bearbeiten und Fortfahren aktiviert ist. Diese Option gilt für alle Sprachen, die Bearbeiten und Fortfahren unterstützen.|
|InvokedByCommands|Get/Set (boolesch)|Bestimmt, ob beim Bearbeiten und Fortfahren Codeänderungen automatisch angewendet werden, wenn der Benutzer einen Debugbefehl wie **Schritt** oder **Fortfahren** auswählt. Diese Option gilt nur für nativen Code.|
|InvokedByCommandsAskFirst|Get/Set (boolesch)|Bestimmt, ob der Benutzer beim Bearbeiten und Fortfahren zur Bestätigung von Codeänderungen aufgefordert wird, wenn der Benutzer einen Debugbefehl wie **Schritt** oder **Fortfahren** auswählt. Diese Option gilt nur für nativen Code.|
|WarnAboutStaleCode|Get/Set (boolesch)|Bestimmt, ob der Debugger eine Warnung ausgibt, wenn das Bearbeiten und Fortfahren zur Ausführung von veraltetem Code führen würde. Diese Option gilt nur für nativen Code.|
|RelinkChangesOnStop|Get/Set (kurzer Name)|Bestimmt, ob Visual Studio Codeänderungen, die mit Bearbeiten und Fortfahren angewendet wurden, erneut bindet, wenn die Ausführung der Anwendung unterbrochen wird. Diese Option gilt nur für nativen Code.|
|AllowPrecompiling|Get/Set (kurzer Name)|Bestimmt, ob beim Bearbeiten und Fortfahren vorkompilierte Header im Hintergrund geladen werden können. Diese Option gilt nur für nativen Code.|

## <a name="just-in-time"></a>Just-In-Time
 `DTE.Properties("Debugging", "JustInTime")`

|Eigenschaftenelementname|Wert|BESCHREIBUNG|
|------------------------|-----------|-----------------|
|JitManaged|Get/Set (boolesch)|Bestimmt, ob Just-In-Time-Debuggen für verwalteten Code aktiviert ist.|
|JitNative|Get/Set (boolesch)|Bestimmt, ob Just-In-Time-Debuggen für systemeigenen Code aktiviert ist.|
|JitScript|Get/Set (boolesch)|Bestimmt, ob Just-In-Time-Debuggen für Skriptcode aktiviert ist.|

## <a name="native"></a>Systemeigenes Format
 `DTE.Properties("Debugging", "Native")`

|Eigenschaftenelementname|Wert|BESCHREIBUNG|
|------------------------|-----------|-----------------|
|LoadDllExports|Get/Set (boolesch)|Bestimmt, ob der Debugger DLL-Exporttabellen lädt.|
|EnableRPC|Get/Set (boolesch)|Bestimmt, ob der Debugger COM-Remoteprozeduraufrufe schrittweise ausführen kann.|

## <a name="see-also"></a>Weitere Informationen
 [Steuern von Options Einstellungen](https://msdn.microsoft.com/library/a09ed242-7494-4cde-bbd1-7a8ec617965d) [Festlegen der Namen von Eigenschaften Elementen auf Options Seiten](https://msdn.microsoft.com/library/d450422d-47c7-4eeb-9f9f-3286264bc5aa) Optionen (Dialogfeld) [, Schriftarten und Farben Knoten Eigenschaften](../../ide/reference/options-page-fonts-and-colors-node-properties.md) [Optionen-Seite, Text-Editor Knoten Eigenschaften](../../ide/reference/options-page-text-editor-node-properties.md) [Allgemein, Debuggen, Dialogfeld "Optionen](../../debugger/general-debugging-options-dialog-box.md) " [Bearbeiten und fortfahren, Debuggen, Dialog](https://msdn.microsoft.com/library/009d225f-ef65-463f-a146-e4c518f86103) Feld "Optionen" [Just-in-Time, Debugging, Dialogfeld](../../debugger/just-in-time-debugging-options-dialog-box.md)
