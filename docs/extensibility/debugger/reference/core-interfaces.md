---
description: Die folgenden Schnittstellen sind die Kern Schnittstellen zum Erweitern des Debuggers mit dem vs SDK.
title: Kern Schnittstellen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], core interfaces
ms.assetid: 666b9116-8550-4bdd-bc15-55fc57de87df
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4f24dd16656144fa155d0473d7f722487c0edd03
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170756"
---
# <a name="core-interfaces"></a>Wichtige Schnittstellen
Die folgenden Schnittstellen sind die Kern Schnittstellen zum Erweitern des Debuggers mithilfe von [!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)] .

## <a name="discussion"></a>Diskussion
 Diese Schnittstellen werden hauptsächlich verwendet, um die Debug-Engine (de) zu erstellen. Sie sind hier nach Kategorien organisiert:

- [Breakpoints](#Breakpoints)

- [Kontexte](#Contexts)

- [Core-Server](#CoreServer)

- [Debug-engines](#DebugEngines)

- [Dokumente](#Documents)

- [Ereignisse](#Events)

- [Ausdrücke](#Expressions)

- [Arbeitsspeicher](#Memory)

- [Module](#Modules)

- [Ports](#Ports)

- [Prozesse](#Processes)

- [Programs](#Programs)

- [Eigenschaften](#Properties)

- [Stapelrahmen](#StackFrames)

- [Threads](#Threads)

- [Typvisualisierungen](#TypeVisualizers)

  Die Entitäten, die die Schnittstellen implementieren können, sind:

- Debug-Engine (de)

- Port Lieferant (PS)

- Ausdrucks Auswertung (EE)

- Visual Studio (VS)

## <a name="breakpoints"></a><a name="Breakpoints"></a> Haltepunkte
 Diese Schnittstellen stehen im Zusammenhang mit der Implementierung und Nachverfolgung von Breakpoints.

|Schnittstelle|Implementiert von|BESCHREIBUNG|
|---------------|--------------------|-----------------|
|[IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)|DE|Stellt einen Haltepunkt dar, der an eine Speicheradresse gebunden ist.|
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|Wird von der de gesendet, wenn ein Breakpoint an eine Speicheradresse gebunden ist.|
|[IDebugBreakpointChecksumRequest2](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2.md)|VS|Stellt eine Dokument Prüfsumme für eine Haltepunkt Anforderung dar.|
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|Wird von der de gesendet, wenn ein Breakpoint nicht an eine Speicheradresse gebunden werden kann.|
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|Wird von der de gesendet, wenn ein Breakpoint erreicht wird.|
|[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)|VS|Stellt eine Anforderung für einen Haltepunkt dar. wird zum Erstellen eines ausstehenden Breakpoints verwendet.|
|[IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)|VS|Stellt eine Anforderung für einen Haltepunkt dar. wird zum Erstellen eines ausstehenden Breakpoints verwendet.|
|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|DE|Stellt die Informationen dar, die zum Binden eines Breakpoints verwendet werden.|
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|Wird von der de gesendet, wenn die Bindung eines Breakpoints an eine Speicheradresse aufgehoben wird.|
|[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)|DE|Stellt einen ungültigen Breakpoint dar (von zurückgegeben `IDebugBreakpointErrorEvent2` ).|
|[IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)|DE|Stellt die Auflösungsinformationen zu einem ungültigen Breakpoint dar.|
|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|DE|Stellt eine Position in einer Funktion dar, bei der ein Breakpoint festgelegt ist.|
|[IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)|DE|Stellt einen Haltepunkt dar, der gebunden werden soll. wird zum Erstellen eines gebundenen halte Punkts verwendet.|
|[IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)|DE|Stellt eine Enumeration für einen Satz von gebundenen Haltepunkten dar.|
|[IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)|DE|Stellt eine Enumeration für einen Satz von Breakpoints dar, die nicht an eine Speicheradresse gebunden werden konnten.|

## <a name="contexts"></a><a name="Contexts"></a> Kontexte
 Diese Schnittstellen stellen verschiedene Arten von Kontexten in dem Programm dar, das gedebuggt wird.

|Schnittstelle|Implementiert von|BESCHREIBUNG|
|---------------|--------------------|-----------------|
|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|DE|Stellt die Anfangsposition einer Code Anweisung dar.|
|[IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)|DE|Erweitert die [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) -Schnittstelle, um das Abrufen von Modul-und Prozessschnittstellen zu ermöglichen.|
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS, de|Stellt eine Position in einem Dokument dar.|
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|Stellt den Kontext dar, in dem ein Ausdruck ausgewertet werden soll.|
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|Stellt die Startposition einer Auflistung von Bytes im Arbeitsspeicher dar.|
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|Stellt einen Stapel Rahmen Kontext an einem Haltepunkt oder einer Ausnahme dar.|
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Stellt einen Stapel Rahmen Kontext an einem Haltepunkt oder einer Ausnahme dar.|
|[IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)|DE|Stellt eine Enumeration für einen Satz von Code Kontexten dar.|

## <a name="core-server"></a><a name="CoreServer"></a> Core-Server
 Diese Schnittstellen stellen den Computer dar, auf dem ein Programm gedebuggt wird. Diese werden von implementiert, Sie [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] können jedoch von Debug-engines aufgerufen werden.

|Schnittstelle|Implementiert von|BESCHREIBUNG|
|---------------|--------------------|-----------------|
|[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)|VS|Bietet Zugriff auf Ports und Port Lieferanten sowie Informationen über den Computer.|
|[IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)|VS|Stellt eine [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) dar, die das Remote Debugging unterstützt.|

## <a name="debug-engines"></a><a name="DebugEngines"></a> Debug-engines
 Diese Schnittstellen stellen Debug-engines und die zugehörigen Ereignisse dar.

|Schnittstelle|Implementiert von|BESCHREIBUNG|
|---------------|--------------------|-----------------|
|[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)|DE|Stellt eine benutzerdefinierte Debug-Engine dar.|
|[IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)|DE|Stellt eine benutzerdefinierte Debug-Engine dar, die das Laden von Symbolen, JustMyCode und Ausnahmen unterstützt.|
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|Wird von jeder neuen Instanz von de gesendet, um anzugeben, dass Sie zum Verarbeiten von Debuggingaufgaben bereit ist.|
|[IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)|DE|Stellt ein benutzerdefiniertes Debug-Modul dar, das das Starten von Programmen|
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE, PS|Stellt einen Programmknoten dar, der mehrere debugengines behandelt.|
|[IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)|DE|Bietet eine Möglichkeit für SDM, eine Schnittstelle von einem Thread, einem Programm oder einem Stapel Rahmen zur Debug-Engine abzurufen.|

## <a name="documents"></a><a name="Documents"></a> Dokumenten
 Diese Schnittstellen stellen Dokumente (Quelldateien) und die zugehörigen Elemente dar.

|Schnittstelle|Implementiert von|BESCHREIBUNG|
|---------------|--------------------|-----------------|
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|Wird von der de gesendet, um anzufordern, dass ein Dokument geöffnet wird.|
|[IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)|DE|Stellt einen Datenstrom disassemblierten Anweisungen aus einem Dokument dar.|
|[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)|VS, de|Stellt ein von der de bereitgestelltes Dokument dar und gibt einen Namen und eine Klassen-ID (CLSID) an.|
|[IDebugDocumentChecksum2](../../../extensibility/debugger/reference/idebugdocumentchecksum2.md)|DE, EE|Stellt eine Prüfsumme für ein debugdokument dar und ermöglicht die Übergabe der Prüfsumme zwischen Komponenten.|
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS, de|Stellt einen Dokument Kontext dar, eine Position in einem Dokument, das einer bestimmten Anweisung und einem Code Kontext entspricht.|
|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|VS, de|Stellt eine allgemeine Position in einem Dokument dar.|
|[IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)|VS|Stellt eine Position in einer Quelldatei als Zeichen Offset dar.|
|[IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)|VS, de|Stellt ein Textdokument dar, das von der de (abgeleitet von [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)) bereitgestellt wird und den eigentlichen Text bereitstellt.|
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|Wird von der de gesendet, um Änderungen an einer Quelldatei anzugeben, die sich im Arbeitsspeicher befindet.|

## <a name="events"></a><a name="Events"></a> Fall
 Diese Schnittstellen stellen alle Ereignisse dar, die zwischen de und dem sitzungsdebug-Manager (SDM) gesendet werden.

| Schnittstelle | Implementiert von | BESCHREIBUNG |
| - |----------------| - |
| [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md) | DE | Wird von der de gesendet, um anzufordern, dass ein Dokument geöffnet wird. |
| [IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md) | DE | Die Debug-Engine (de) sendet diese Schnittstelle an den Sitzungs-Debug-Manager (SDM), um die Status leisten Nachricht während der Symbol Auslastung festzulegen. |
| [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) | DE | Wird von der de gesendet, wenn eine Unterbrechung des Programms abgeschlossen wurde. |
| [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) | DE | Wird von der de gesendet, wenn ein Breakpoint gebunden ist. |
| [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) | DE | Wird von der de gesendet, wenn ein Breakpoint nicht gebunden werden kann. |
| [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) | DE | Wird von der de gesendet, wenn ein Breakpoint erreicht wird. |
| [IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md) | DE | Wird von der de gesendet, wenn ein Breakpoint nicht gebunden ist. |
| [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md) | DE | Wird von der de gesendet, um zu bestimmen, ob Sie an einer bestimmten Position angehalten werden soll. |
| [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md) | DE | Wird von der de gesendet, um Änderungen an einer Quelldatei anzugeben, die sich im Arbeitsspeicher befindet. |
| [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) | DE | Wird von jeder neuen Instanz von de gesendet, um anzugeben, dass Sie zum Verarbeiten von Debuggingaufgaben bereit ist. |
| [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) | DE | Wird von der de gesendet, um anzugeben, dass das zu deaktivier Ende Programm bereit ist, die erste Anweisung auszuführen. |
| [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) | DE | Eine Schnittstelle, die von anderen Ereignis Schnittstellen verwendet wird, die möglicherweise einen Fehler zurückgibt, um lesbare Fehlermeldungen bereitzustellen. |
| [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) | DE, PS | Basisschnittstelle, von der alle anderen Ereignis Schnittstellen abgeleitet werden. |
| [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) | VS | Stellt eine von SDM implementierte Schnittstelle dar, mit der Ereignisse (ausgedrückt als Objekte, die eine bestimmte Ereignis Schnittstelle implementieren) gesendet werden. |
| [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) | DE | Wird von der de gesendet, wenn eine Ausnahme in dem Programm aufgetreten ist, das deentschlgt wird. |
| [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) | DE | Wird von der de gesendet, wenn eine asynchrone Ausdrucks Auswertung beendet ist. |
| IDebugFindSymbolEvent2 | | VERALTET. Verwenden Sie nicht. |
| [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) | DE | Wird von der de gesendet, wenn die Verarbeitung für eine abgefangene Ausnahme abgeschlossen wurde. |
| [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) | DE | Wird von der de gesendet, wenn ein Programm den Ladevorgang abgeschlossen hat. |
| [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md) | DE | Wird von der de gesendet, damit die IDE eine Informations Meldung für den Benutzer anzeigt. |
| [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) | DE | Wird von der de gesendet, wenn ein Modul geladen oder entladen wird. |
| [IDebugNoSymbolsEvent2](../../../extensibility/debugger/reference/idebugnosymbolsevent2.md) | DE | Signalisiert der [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Debugger-Benutzeroberfläche, den Benutzer zu warnen, dass Symbole für die gestartete ausführbare Datei nicht gefunden werden konnten. |
| [IDebugOutputStringEvent2](../../../extensibility/debugger/reference/idebugoutputstringevent2.md) | DE | Wird von der de gesendet, damit die IDE eine beliebige Zeichenfolge anzeigt. |
| [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) | VS, de | Wird von einem Port gesendet, um Port Ereignisse an einen beliebigen Listener zu übermitteln. |
| [IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md) | DE, PS | Wird von der de oder dem Port gesendet, wenn ein Prozess erstellt wurde. |
| [IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) | DE, PS | Wird von der de oder dem Port gesendet, wenn ein Prozess zerstört wurde. |
| [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) | DE, PS | Wird von der de oder dem Port gesendet, wenn ein Programm erstellt wurde. |
| [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) | DE, PS | Wird von der de oder dem Port gesendet, wenn ein Programm zerstört wurde. |
| [IDebugProgramDestroyEventFlags2](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2.md) | DE | Ermöglicht es einer Debug-Engine, das Standardverhalten der Benutzeroberfläche zu überschreiben, [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Wenn Sie eine Debugsitzung beenden. |
| [IDebugProgramNameChangedEvent2](../../../extensibility/debugger/reference/idebugprogramnamechangedevent2.md) | DE | Wird von der Debug-Engine (de) an den Sitzungs-Debug-Manager (SDM) gesendet, wenn der Name eines Programms geändert wird. |
| [IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md) | DE | Wird von der de gesendet, wenn eine neue Eigenschaft (dargestellt durch die- `IDebugProperty2` Schnittstelle) erstellt wurde. |
| [IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md) | DE | Wird von der de gesendet, wenn eine Eigenschaft zerstört wurde. |
| [IDebugReturnValueEvent2](../../../extensibility/debugger/reference/idebugreturnvalueevent2.md) | DE | Wird von der de beim Durchlaufen einer Funktion oder über eine Funktion gesendet, sodass der Rückgabewert ordnungsgemäß angezeigt werden kann. |
| [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md) | VS | Ermöglicht Debug-engines das Remote Lesen von Metrikeinstellungen. |
| [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md) | DE | Wird von der de gesendet, wenn ein Einzelschritt, eine over-Anweisung oder eine FROM-Anweisung abgeschlossen wurde. |
| [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) | DE | Wird von der de gesendet, um den Erfolg oder das Fehlschlagen des Ladens von Symbolen für ein Modul anzugeben. |
| [IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md) | DE | Wird von der de gesendet, wenn ein Thread erstellt wurde. |
| [IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) | DE | Wird von der de gesendet, wenn ein Thread zerstört wurde. |
| [IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md) | DE | Wird von der de gesendet, wenn ein Thread seinen Namen geändert hat. |

## <a name="expressions"></a><a name="Expressions"></a>-Ausdrücke
 Diese Schnittstellen stellen Ausdrücke dar, die in einem bestimmten Kontext ausgewertet werden.

|Schnittstelle|Implementiert von|BESCHREIBUNG|
|---------------|--------------------|-----------------|
|[IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)|DE|Stellt einen Ausdruck dar, der ausgewertet werden soll. Abgerufen von der [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) -Schnittstelle.|
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|Stellt einen Kontext dar, in dem ein Ausdruck ausgewertet wird. Abgerufen von der [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) -Schnittstelle.|
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|Wird von der de gesendet, wenn eine asynchrone Ausdrucks Auswertung beendet ist.|

## <a name="memory"></a><a name="Memory"></a> Gedenkens
 Diese Schnittstellen stellen Sequenzen von Bytes im Arbeitsspeicher dar.

|Schnittstelle|Implementiert von|BESCHREIBUNG|
|---------------|--------------------|-----------------|
|[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)|DE|Stellt eine Sequenz von Bytes im Arbeitsspeicher dar, in die gelesen oder geschrieben werden kann.|
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|Stellt eine Position im Speicher einer Byte Sequenz dar.|

## <a name="modules"></a><a name="Modules"></a> Module
 Diese Schnittstellen stellen ein Modul dar, das einer ausführbaren Datei oder entspricht. DLL-Datei.

|Schnittstelle|Implementiert von|BESCHREIBUNG|
|---------------|--------------------|-----------------|
|[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)|DE|Stellt eine einzelne ausführbare Datei oder dll dar.|
|[IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)|DE|Stellt ein [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) -Zeichen dar, das Symbole unterstützt.|
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|Wird von der de gesendet, wenn ein Modul geladen oder entladen wird.|
|[IDebugSourceServerModule](../../../extensibility/debugger/reference/idebugsourceservermodule.md)|DE|Stellt die Quell Server Informationen dar, die in einer PDB-Datei enthalten sind.|
|[IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)|DE|Stellt eine Enumeration für einen Satz von Modulen dar, die von einem [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)bekannt sind.|

## <a name="ports"></a><a name="Ports"></a> Landungen
 Diese Schnittstellen stellen Ports und Port Lieferanten dar.

| Schnittstelle | Implementiert von | BESCHREIBUNG |
| - |----------------| - |
| [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md) | VS, PS | Stellt den Standardport auf dem lokalen Computer dar. |
| [IDebugFirewallConfigurationCallback2](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2.md) | VS | Aktiviert eine Debug-Engine, die DCOM verwendet, um die [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Benutzeroberfläche zu Fragen, um sicherzustellen, dass die Firewall das Remote Debugging nicht blockiert. |
| [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) | VS, PS | Stellt einen Port dar. |
| [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) | PS | Wird von einem Port gesendet, um Port Ereignisse an einen beliebigen Listener zu übermitteln. |
| [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md) | PS | Stellt einen Port dar, der Prozesse starten und beenden kann. |
| [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) | PS | Wird verwendet, um Programme mit einem Port zu registrieren und die Registrierung aufzuheben. ermöglicht dem Port, Programme zu überprüfen, die aktuell debuggt werden. |
| [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md) | PS | Stellt eine angepasste Benutzeroberfläche zum Auswählen des Ports dar. |
| [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) | VS | Stellt eine Anforderung für einen Port dar, von dem ein neuer Port erstellt oder gespeichert wird. |
| [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) | PS | Stellt einen Lieferanten von Ports dar. |
| [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md) | PS | Stellt einen Lieferanten von Ports dar, die Informationen zu den erstellten Ports beibehalten (auf dem Datenträger speichern) können. |
| [IDebugPortSupplierDescription2](../../../extensibility/debugger/reference/idebugportsupplierdescription2.md) | PS | Ermöglicht der [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Benutzeroberfläche, Text innerhalb des Abschnitts **Transport Informationen** im Dialogfeld **an den Prozess anhängen** anzuzeigen. |
| [IDebugWindowsComputerPort2](../../../extensibility/debugger/reference/idebugwindowscomputerport2.md) | VS | Ermöglicht das Abfragen von Informationen über den Bereitstellungs Zielcomputer. |
| [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md) | VS, PS | Stellt eine Enumeration für einen Satz von Ports dar. |
| [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) | VS | Stellt eine Enumeration für einen Satz von Port Lieferanten dar. |

## <a name="processes"></a><a name="Processes"></a> Prozesse
 Diese Schnittstellen stellen Prozesse dar, eine einzelne ausführbare Datei, die ein oder mehrere Programme enthält.

|Schnittstelle|Implementiert von|BESCHREIBUNG|
|---------------|--------------------|-----------------|
|[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)|PS, de|Stellt einen Prozess dar, der auf einem Computer ausgeführt wird.|
|[IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)|PS, de|Stellt einen Prozess dar, der das Debuggen aktiv unterstützt (zum Ersetzen der Methoden Step, Continue und Execute in der [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) -Schnittstelle).|
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|DE, PS|Wird von der de oder dem Port gesendet, wenn ein Prozess erstellt wurde.|
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|DE, PS|Wird von der de oder dem Port gesendet, wenn ein Prozess zerstört wurde.|
|[IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)|PS|Stellt einen Prozess dar, der nachverfolgen muss, welche Sitzung an ihn angefügt ist.|
|[IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)|PS|Stellt eine Enumeration eines Satzes von Prozessen auf einem Port dar.|

## <a name="programs"></a><a name="Programs"></a> Programme
 Diese Schnittstellen stellen Programme, logische Ausführungs Einheiten dar, die nicht notwendigerweise mit einer physischen ausführbaren Datei oder einem physischen Modul übereinstimmen.

|Schnittstelle|Implementiert von|BESCHREIBUNG|
|---------------|--------------------|-----------------|
|[IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)|DE|Stellt ein [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) dar, das gemeinsam mit anderen Programmen verwendet werden muss, die gleichzeitig gedebuggt werden.|
|[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)|DE, PS|Stellt eine logische Ausführungs Einheit dar.|
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|DE, PS|Wird von der de oder dem Port gesendet, wenn ein Programm erstellt wurde.|
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|DE, PS|Wird von der de oder dem Port gesendet, wenn ein Programm zerstört wurde.|
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE, PS|Stellt eine [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) dar, die von mehreren Debug-engines behandelt werden kann.|
|[IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)|PS|Stellt einen [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) dar, der in der Lage sein muss, die angefügte Sitzung zu verfolgen.|
|[IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)|DE, PS|Stellt eine [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) dar, die Informationen über den Prozess zurückgeben kann, in dem Sie ausgeführt wird.|
|[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)|DE, PS|Stellt ein Programm dar, das deentschlbelt werden kann.|
|[IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)|DE, PS|Ermöglicht, dass ein Programmknoten über einen Versuch benachrichtigt wird, dem zugeordneten Programm anzufügen.|
|[IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)|DE|Bietet eine Möglichkeit für SDM, eine de über die Programme abzufragen, die von dieser de gesteuert werden.|
|[IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)|VS|Wird von des zum Registrieren von Programmen bei SDM verwendet, um anzuzeigen, dass Sie gedebuggt werden.|
|[IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)|DE, PS|Stellt ein [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) dar, das Schnittstellen über Thread-oder Prozess Grenzen hinweg Mars Hallen kann.|
|[IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)|DE, PS|Stellt eine Enumeration eines Satzes von Programmen dar.|

## <a name="properties"></a><a name="Properties"></a> Eigenschaften
 Diese Schnittstellen stellen Eigenschaften dar, einen Wert, der einem bestimmten Kontext zugeordnet ist, normalerweise das Ergebnis einer Ausdrucks Auswertung.

|Schnittstelle|Implementiert von|BESCHREIBUNG|
|---------------|--------------------|-----------------|
|[IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)|EE|Stellt ein [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) dar, das seinen Wert auf benutzerdefinierte Weise anzeigen kann.|
|[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)|DE|Stellt einen Wert für einen Stapel Rahmen, ein Dokument oder das Ergebnis einer Ausdrucks Auswertung dar.|
|[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)|DE|Stellt ein [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) dar, das willkürlich lange Zeichen folgen unterstützt.|
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|Wird von der de gesendet, wenn eine neue Eigenschaft (dargestellt durch die [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) -Schnittstelle) erstellt wurde.|
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|Wird von der de gesendet, wenn eine Eigenschaft zerstört wurde.|
|[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)|DE|Stellt einen Verweis auf eine Eigenschaft dar, die außerhalb eines bestimmten Stapel Rahmens vorhanden sein kann.|
|[IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)|DE|Stellt eine Enumeration für einen Satz von [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Strukturen dar, die Variablen, Register, Parameter und Ausdrücke beschreiben.|
|[IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)|DE|Stellt eine Enumeration für einen Satz von [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) Strukturen dar.|

## <a name="stack-frames"></a><a name="StackFrames"></a> Stapel Rahmen
 Diese Schnittstellen stellen einen Stapel Rahmen dar, einen Kontext, in dem ein Breakpoint oder eine Ausnahme aufgetreten ist.

|Schnittstelle|Implementiert von|BESCHREIBUNG|
|---------------|--------------------|-----------------|
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|Stellt einen Kontext dar, in dem ein Breakpoint oder eine Ausnahme aufgetreten ist.|
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Stellt ein [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) dar, das abgefangene Ausnahmen behandeln kann.|
|[IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)|DE|Stellt eine Enumeration für den Satz von [CODE_PATH](../../../extensibility/debugger/reference/code-path.md) Strukturen dar, die die Funktions Aufrufsequenz angeben, die verwendet wird, um an einem bestimmten Stapel Rahmen zu gelangen.|
|[IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)|DE|Stellt eine Enumeration für einen Satz von [frameInfo](../../../extensibility/debugger/reference/frameinfo.md) -Strukturen dar, die Stapel Rahmen beschreiben.|

## <a name="threads"></a><a name="Threads"></a> Threads
 Diese Schnittstellen stellen Threads und ihre zugeordneten Ereignisse dar.

|Schnittstelle|Implementiert von|BESCHREIBUNG|
|---------------|--------------------|-----------------|
|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|DE|Stellt einen Ausführungs Thread dar.|
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|Wird von der de gesendet, wenn ein Thread erstellt wurde.|
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|Wird von der de gesendet, wenn ein Thread zerstört wurde.|
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|Wird von der de gesendet, wenn ein Thread seinen Namen geändert hat.|
|[IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)|DE|Stellt eine Enumeration für eine Gruppe von Threads dar.|

## <a name="type-visualizers"></a><a name="TypeVisualizers"></a> Typvisualisierungen
 Diese Schnittstellen bieten Unterstützung für typvisualisierungen. Diese Schnittstellen werden in der Regel durch eine Ausdrucks Auswertung implementiert.

|Schnittstelle|Implementiert von|BESCHREIBUNG|
|---------------|--------------------|-----------------|
|[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)|EE|Stellt ein Array von Bytes dar, das einer typschnell Ansicht angezeigt werden soll.|
|[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)|EE|Stellt Methoden bereit, mit denen Sie Zugriff auf Daten erhalten, die an eine typschnell Ansicht übermittelt werden.|
|[IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)|EE|Stellt eine Eigenschaft dar, die Zugriff auf [ipropertyproxyeeside](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) -Implementierungen bereitstellt.|

## <a name="see-also"></a>Weitere Informationen
- [API-Referenz](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
- [Erstellen einer benutzerdefinierten Debug-Engine](../../../extensibility/debugger/creating-a-custom-debug-engine.md)
