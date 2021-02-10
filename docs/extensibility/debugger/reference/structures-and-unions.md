---
title: Strukturen und Unions | Microsoft-Dokumentation
description: Dieser Artikel verknüpft Sie mit Referenz Beschreibungen von Strukturen und Unions im Visual Studio-debuggingsdk.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- structures [Visual Studio SDK]
ms.assetid: 9ff0a8f8-1ee6-4fdd-8b80-206436ff589b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6b055446e6bdf147c99cf96b48c03bfcfdd2eda2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99938693"
---
# <a name="structures-and-unions"></a>Structures and Unions
Im folgenden finden Sie Strukturen und Unions im Visual Studio-debuggingsdk.

- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) Gibt die Prozess-ID an, bei der es sich entweder um eine System-ID oder eine GUID handeln kann.

- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) Beschreibt die Bedingungen, unter denen ein Breakpoint ausgelöst wird.

- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) Beschreibt die Auflösung eines Fehler-Breakpoints, einschließlich Speicherort, Programm und Thread.

- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) Gibt den Strukturtyp an, der verwendet wird, um den Speicherort des Breakpoints zu beschreiben.

- [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md) Definiert die Komponenten, die den Speicherort eines halte Punkts an einer Adresse im Code beschreiben.

- [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md) Beschreibt den Speicherort eines Breakpoints, der direkt an eine Adresse im debuggten Programm gebunden ist.

- [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) Beschreibt die Position eines halte Punkts in Zeile in einer Code Quelldatei.

- [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) Beschreibt die Offset Position eines Breakpoints in einer Funktion im Code.

- [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md) Dient zum Festlegen von Code Breakpoints basierend auf einer Zeichenfolge, die der Benutzer aus der IDE eingeben kann.

- [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md) Wird verwendet, um Daten Breakpoints festzulegen, die auf einer Zeichenfolge basieren, die der Benutzer aus der IDE eingeben kann.

- [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md) Beschreibt die Auflösung eines Breakpoints an einer bestimmten Position.

- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) Beschreibt die Anzahl und die Bedingungen, nach denen ein Breakpoint ausgelöst wird, nachdem er zuvor übermittelt wurde.

- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) Enthält die erforderlichen Informationen zum Implementieren eines Breakpoints.

- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) Enthält die Informationen, die erforderlich sind, um einen Breakpoint zu implementieren (identisch mit der [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) Struktur, enthält jedoch Hersteller-GUID, Einschränkung und Ablauf Verfolgungs Punkt-Informationen).

- [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md) Beschreibt den Speicherort eines Code Breakpoints.

- [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) Beschreibt das Ergebnis der Bindung eines Daten Breakpoints.

- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) Beschreibt die gebundenen Haltepunkt Informationen für einen Code-Haltepunkt oder einen Daten Breakpoint.

- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) Gibt die Struktur der Haltepunkt Auflösung an.

- [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md) Beschreibt ein Array von Zeichen folgen.

- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) Gibt Informationen zu einem Feldtyp an, der aus Metadaten entnommen wurde.

- [CODE_PATH](../../../extensibility/debugger/reference/code-path.md) Beschreibt einen-Rückruf für eine Funktion oder Methode.

- [COMPUTER_INFO](../../../extensibility/debugger/reference/computer-info.md) Beschreibt den Computer, auf dem der Debugger ausgeführt wird.

- [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md) Beschreibt eine Liste von GUIDs.

- [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) Beschreibt einen Arbeitsspeicher Kontext oder Code Kontext.

- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) Beschreibt eine Adresse in einem Programm, das deentschlgt wird.

- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) Stellt eine Zahl verschiedener Arten von Adressen dar.

- [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) Identifiziert einen benutzerdefinierten Viewer oder eine typschnell Ansicht.

- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Beschreibt eine Debug-Eigenschaft, die wiederum ein Objekt einer hierarchischen Natur mit Name, Typ und Wert beschreibt.

- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) Beschreibt einen-Verweis.

- [Disassemblydata](../../../extensibility/debugger/reference/disassemblydata.md) Beschreibt die Disassembly zur IDE für die Anzeige.

- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) Beschreibt eine Ausnahme oder einen Laufzeitfehler, der von dem Programm ausgelöst wird, das deentschlgt wird.

- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) Beschreibt eine lokale Variable, einen Parameter oder ein anderes Feld.

- [FrameInfo](../../../extensibility/debugger/reference/frameinfo.md) Beschreibt einen Stapel Rahmen.

- [GUID_ARRAY](../../../extensibility/debugger/reference/guid-array.md) Beschreibt ein Array eindeutiger Bezeichner für verfügbare Debug-engines.

- [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) Wird verwendet, um die JustMyCode-Informationen für ein Modul festzulegen.

- [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) Beschreibt einen bestimmten Computer.

- [METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) Beschreibt ein Array Element in einem Array.

- [METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) Beschreibt die Adresse eines Felds einer Klasse oder Struktur.

- [METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) Beschreibt die Adresse einer lokalen Variablen innerhalb eines Bereichs (in der Regel eine Funktion oder Methode).

- [METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) Beschreibt die Adresse einer Methode einer-Klasse.

- [METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) Beschreibt einen Parameter einer Methode oder Funktion.

- [METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) Beschreibt einen Rückgabewert einer Methode oder Funktion.

- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) Beschreibt einen Feldtyp, der aus Metadaten entnommen wurde.

- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) Beschreibt ein bestimmtes Modul (dll, exe oder Assembly).

- [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) Beschreibt Statusinformationen zu Symbol Suchpfaden, die durchsucht wurden.

- [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) Beschreibt eine native Adresse.

- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) Beschreibt einen Feldtyp, der aus einem PDB-Symbol entnommen wurde.

- [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) Beschreibt den Zustand eines Breakpoints, der für die Bindung an einen Code Speicherort bereit ist.

- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) Beschreibt einen Prozess.

- [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md) Beschreibt eine Liste von [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) -Objekten, die Programmknoten darstellen.

- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) Beschreibt Prozesse, die auf einem Computer ausgeführt werden.

- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) Beschreibt den Zeilen-und Spalten Speicherort im angegebenen Text.

- [Thread Properties](../../../extensibility/debugger/reference/threadproperties.md) Beschreibt die Eigenschaften eines Threads.

- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) Beschreibt den Typ eines Felds.

- [UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) Beschreibt eine physische Adresse.

- [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) Beschreibt eine Adresse, die relativ zu einem `this` Zeiger ist ( `Me` in Visual Basic).

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h, sh. h oder EE. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [API-Referenz](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
