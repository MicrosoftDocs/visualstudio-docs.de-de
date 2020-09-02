---
title: Interoperabilitätswarnungen
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.Interoperabilityrules
helpviewer_keywords:
- managed code analysis warnings, interoperability warnings
- interoperability warnings
- warnings, interoperability
ms.assetid: 95de6eb3-40c4-4063-9f59-25cb70e3b2b3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 74bffffa2b4f95aeab20438199bb19693a1a3b94
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "87235120"
---
# <a name="interoperability-warnings"></a>Interoperabilitätswarnungen

Interoperabilitäts Warnungen unterstützen Interaktionen mit com-Clients.

## <a name="in-this-section"></a>In diesem Abschnitt

| Regel | Beschreibung |
| - | - |
| [CA1400: P/aufrufende Einstiegspunkte müssen vorhanden sein](../code-quality/ca1400.md) | Eine öffentliche oder geschützte Methode wird mit dem System.Runtime.InteropServices.DllImportAttribute-Attribut markiert. Entweder konnte die nicht verwaltete Bibliothek nicht gefunden werden, oder die Methode konnte keiner Funktion in der Bibliothek zugeordnet werden. |
| [CA1401: P/Aufrufe dürfen nicht sichtbar sein.](../code-quality/ca1401.md) | Eine öffentliche oder geschützte Methode in einem öffentlichen Typ weist das System.Runtime.InteropServices.DllImportAttribute-Attribut auf (wird auch vom Declare-Schlüsselwort in Visual Basic implementiert). Solche Methoden sollten nicht verfügbar gemacht werden. |
| [CA1402: Überladungen in für COM sichtbaren Schnittstellen vermeiden.](../code-quality/ca1402.md) | Wenn für COM-Clients überladene Methoden verfügbar gemacht werden, behält nur die erste Methodenüberladung ihren Namen. Nachfolgende Überladungen werden eindeutig umbenannt, indem dem Namen ein Unterstrich (_) und eine ganze Zahl angefügt werden, die der Reihenfolge der Deklaration der Überladung entspricht. |
| [CA1403: Typen mit automatischem Layout sollten nicht für COM sichtbar sein.](../code-quality/ca1403.md) | Ein COM-sichtbarer Werttyp wird mit dem System. Runtime. InteropServices. StructLayoutAttribute-Attribut gekennzeichnet, das auf LayoutKind. Auto festgelegt ist. Das Layout dieser Typen kann sich zwischen .NET-Versionen ändern, wodurch com-Clients, die ein bestimmtes Layout erwarten, unterbricht werden. |
| [CA1404: GetLastError unmittelbar nach P/aufrufen aufrufen](../code-quality/ca1404.md) | An die Marshal. GetLastWin32Error-Methode oder die entsprechende [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] GetLastError-Funktion wird ein Aufruf gerichtet, und der unmittelbar vorherige Aufruf erfolgt nicht an eine Platt Form Aufruf Methode. |
| [CA1405: Für COM sichtbare Basistypen sollten für COM sichtbar sein.](../code-quality/ca1405.md) | Ein für COM sichtbarer Typ wird von einem Typ abgeleitet, der nicht für COM sichtbar ist. |
| [CA1406: Int64-Argumente für Visual Basic 6-Clients vermeiden.](../code-quality/ca1406.md) | Visual Basic 6-COM-Clients können nicht auf 64-Bit-Ganzzahlen zugreifen. |
| [CA1407: Statische Member in für COM sichtbaren Typen vermeiden.](../code-quality/ca1407.md) | COM unterstützt keine statischen Methoden. |
| [CA1408: AutoDual ClassInterfaceType nicht verwenden.](../code-quality/ca1408.md) | Typen, die eine duale Schnittstelle verwenden, ermöglichen Clients die Bindung an ein bestimmtes Schnittstellenlayout. Änderungen an einer zukünftigen Version des Layouts des Typs oder eines Basistyps führen zur Aufhebung der Verbindung zu COM-Clients, die eine Bindung zu der Schnittstelle haben. Standardmäßig wird eine auf Dispatch beschränkte Schnittstelle verwendet, wenn das ClassInterfaceAttribute-Attribut nicht angegeben wird. |
| [CA1409: Für COM sichtbare Typen müssen erstellt werden können.](../code-quality/ca1409.md) | Ein Verweistyp, der speziell als für COM sichtbar gekennzeichnet ist, enthält einen öffentlichen parametrisierten Konstruktor, jedoch keinen öffentlichen (parameterlosen) Standardkonstruktor. Ein Typ ohne einen öffentlichen Standardkonstruktor kann nicht von COM-Clients erstellt werden. |
| [CA1410: Die COM-Registrierungsmethoden müssen übereinstimmen.](../code-quality/ca1410.md) | Ein Typ deklariert eine Methode, die mit dem-Attribut markiert ist <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> , deklariert jedoch keine Methode, die mit dem-Attribut gekennzeichnet ist <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> , oder umgekehrt. |
| [CA1411: Die COM-Registrierungsmethoden dürfen nicht sichtbar sein.](../code-quality/ca1411.md) | Eine Methode, die mit dem System. Runtime. InteropServices. ComRegisterFunctionAttribute-Attribut oder dem System. Runtime. InteropServices. ComUnregisterFunctionAttribute-Attribut markiert ist, ist extern sichtbar. |
| [CA1412: ComSource-Schnittstellen als IDispatch markieren.](../code-quality/ca1412.md) | Ein Typ ist mit dem System.Runtime.InteropServices.ComSourceInterfacesAttribute-Attribut markiert, und mindestens eine der angegebenen Schnittstellen ist nicht mit dem auf ComInterfaceType.InterfaceIsIDispatch festgelegten System.Runtime.InteropServices.InterfaceTypeAttribute-Attribut markiert. |
| [CA1413: Nicht öffentliche Felder in für COM sichtbaren Werttypen vermeiden.](../code-quality/ca1413.md) | Nicht öffentliche Instanzenfelder von COM-sichtbaren Werttypen sind für COM-Clients sichtbar. Überprüfen Sie den Inhalt der Felder auf Informationen, die nicht verfügbar gemacht werden sollen oder unbeabsichtigte Auswirkungen auf Design oder Sicherheit haben. |
| [CA1414: Boolesche P/aufrufen-Argumente mit MarshalAs markieren](../code-quality/ca1414.md) | Der boolesche Datentyp verfügt über mehrere Darstellungen in nicht verwaltetem Code. |
| [CA1415: "P/" korrekt deklarieren](../code-quality/ca1415.md) | Diese Regel sucht nach Methoden Deklarationen für Platt Form Aufrufe, die [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] auf Funktionen abzielen, die über einen Zeiger auf einen übergebenen Struktur Parameter verfügen, und der entsprechende verwaltete Parameter kein Zeiger auf eine- <xref:System.Threading.NativeOverlapped?displayProperty=fullName> Struktur ist. |
| [CA1417: nicht `OutAttribute` für Zeichen folgen Parameter für P/Aufrufe verwenden](../code-quality/ca1417.md) | Zeichen folgen Parameter, die mit dem als Wert übermittelt werden, `OutAttribute` können die Laufzeit destabilisieren, wenn die Zeichenfolge eine Internpool vorhanden Zeichenfolge ist. |