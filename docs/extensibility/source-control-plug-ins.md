---
title: Quellcodeverwaltungs-Plug-ins | Microsoft-Dokumentation
description: In den Artikeln in diesem Abschnitt wird die gesamte Schnittstellen Spezifikation beschrieben, mit der Quell Code Verwaltungssysteme in Visual Studio integriert werden können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, reference
ms.assetid: 964980ca-21c5-4706-8535-6ea23e1c9cc9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ab076cef7aaab96779e303ee7b85c8047eb6b52e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99848116"
---
# <a name="source-control-plug-ins"></a>Quellcodeverwaltungs-Plug-Ins
Der Abschnitt SDK-Referenz für das Quellcodeverwaltungs-Plug-in enthält die gesamte Schnittstellen Spezifikation, mit der Quell Code Verwaltungssysteme in integriert werden können [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Sie gibt die Syntax und die Semantik der verschiedenen Funktionen und Datentypen an, die das Quellcodeverwaltungs-Plug-in für die Schnittstelle mit der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) implementieren muss.

## <a name="in-this-section"></a>In diesem Abschnitt
- [API-Funktionen der Quellcodeverwaltungs-Plug-in](../extensibility/source-control-plug-in-api-functions.md) Listet Funktionen auf, die vom Quellcodeverwaltungs-Plug-in implementiert werden müssen, um die API für das Quellcodeverwaltungs-Plug-in zu erfüllen.

- [Von der IDE implementierte Rückruf Funktionen](../extensibility/callback-functions-implemented-by-the-ide.md) Beschreibt Funktionen, die das Quellcodeverwaltungs-Plug-in verwendet, um Informationen zurück an die IDE zu übergeben, während bestimmte Befehle ausgeführt werden.

- [Enumeratoren](../extensibility/enumerators.md) Listet die enumeratordatentypen in der Quellcodeverwaltungs-Plug-in-API auf, über die das Quellcodeverwaltungs-Plug-in informiert sein muss.

- [Funktionsflags](../extensibility/capability-flags.md) Beschreibt die `SCC_CAP_xxx` -Flags, die die Funktionen eines Anbieters angeben.

- [Bitflags, die von bestimmten Befehlen verwendet werden](../extensibility/bitflags-used-by-specific-commands.md) Listet Flags auf, die im Kontext bestimmter Befehle nützlich sind.

- [Fehler Codes](../extensibility/error-codes.md) Listet allgemeine Fehler Werte auf, die von Functions als zurückgegeben werden `SCCTRN` .

- [Als Schlüssel für die Suche nach einem Quellcodeverwaltungs-Plug-in verwendete](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md) Zeichen folgen Beschreibt Schlüssel für den Zugriff auf die Registrierung, um das Quellcodeverwaltungs-Plug-in zu suchen.

- [Mssccprj. ](../extensibility/mssccprj-scc-file.md) In der SCC-Datei wird eine Client seitige Datei beschrieben, die Informationen enthält, die für die IDE nicht transparent sind, aber vom Quellcodeverwaltungs-Plug-in verwendet werden, um die Projekt Mappe oder das Projekt in der Versionskontrolle zu finden

- [Bewährte Methoden für die Implementierung eines Quellcodeverwaltungs-Plug-ins](../extensibility/best-practices-for-implementing-a-source-control-plug-in.md) Bietet eine Auflistung wichtiger technischer Erinnerungen, die Sie beim Implementieren der Quellcodeverwaltungs-Plug-in-API beachten sollten.

- [Einschränkungen für Zeichen folgen Längen](../extensibility/restrictions-on-string-lengths.md) Beschreibt Einschränkungen in der Quellcodeverwaltungs-Plug-in-API für die Längen von Zeichen folgen, die in verschiedenen Funktionen verwendet werden.

- [Glossar](../extensibility/source-control-plug-in-glossary.md) Bietet hilfreiche Begriffe und ihre Definitionen zum Lesen der SDK-Dokumentation für das Quellcodeverwaltungs-Plug-in.

- Gewusst [wie: Deaktivieren von Kompatibilitäts Warnungen für Quellcodeverwaltungs-Plug-ins](../extensibility/how-to-turn-off-compatibility-warnings-for-source-control-plug-ins.md) Beschreibt, wie Warnungen deaktiviert werden.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Beispiel für Quellcodeverwaltungs-Plug-in](https://www.microsoft.com/download/details.aspx?id=55984) Enthält ein Beispiel für die Funktionalität der Quellcodeverwaltungs-Plug-ins.

- [Test Handbuch für Quellcodeverwaltungs-Plug-ins](../extensibility/internals/test-guide-for-source-control-plug-ins.md) Beschreibt Test Prozeduren im Zusammenhang mit einem Quellcodeverwaltungs-Plug-in.

- [Erstellen eines Quellcodeverwaltungs-Plug-ins](../extensibility/internals/creating-a-source-control-plug-in.md) Erläutert das Erstellen eines Quellcodeverwaltungs-Plug-ins, das Quell Code Verwaltungsfunktionen bereitstellt, während Sie die Benutzeroberfläche der Quell Code Verwaltung verwenden [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

- [Visual Studio SDK-Referenz](../extensibility/visual-studio-sdk-reference.md) Zeigt eine Liste der Referenz Themen an.
