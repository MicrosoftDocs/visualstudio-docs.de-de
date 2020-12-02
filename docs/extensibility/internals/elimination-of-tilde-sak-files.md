---
title: Beseitigung von ~ Sak-Dateien | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie ~ Sak-Dateien aus der Quellcodeverwaltungs-Plug-in-API 1,2 eliminieren und wie Sie durch funktionsflags und neue Funktionen ersetzt wurden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- temporary files
- ~sak files
- source control plug-ins, ~SAK files
ms.assetid: 5277b5fa-073b-4bd1-8ba1-9dc913aa3c50
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8e846354b2d48b2f7866daa14987e757f41779c8
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480511"
---
# <a name="elimination-of-sak-files"></a>Beseitigung von ~ Sak-Dateien
In der Quellcodeverwaltungs-Plug-in-API 1,2 wurden die *~ Sak* -Dateien durch funktionsflags und neue Funktionen ersetzt, die erkennen, ob ein Quellcodeverwaltungs-Plug-in die *Mssccprj* -Datei und freigegebene Auscheck Vorgänge unterstützt.

## <a name="sak-files"></a>~ Sak-Dateien
Visual Studio .NET 2003 hat temporäre Dateien mit dem Präfix *~ Sak* erstellt. Diese Dateien werden verwendet, um zu bestimmen, ob ein Quellcodeverwaltungs-Plug-in Folgendes unterstützt:

- Die *Mssccprj. SCC* -Datei.

- Mehrere (freigegebene) Checkouts.

Für Plug-ins, die erweiterte Funktionen unterstützen, die in der Quellcodeverwaltungs-Plug-in-API 1,2 bereitgestellt werden, kann die IDE diese Funktionen erkennen, ohne die temporären Dateien durch die Verwendung neuer Funktionen, Flags und Funktionen zu erstellen, die in den folgenden Abschnitten beschrieben werden.

## <a name="new-capability-flags"></a>Neue funktionsflags
 `SCC_CAP_SCCFILE`

 `SCC_CAP_MULTICHECKOUT`

## <a name="new-functions"></a>Neue Funktionen
- [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)

- [SccIsMultiCheckoutEnabled](../../extensibility/sccismulticheckoutenabled-function.md)

 Wenn ein Quellcodeverwaltungs-Plug-in mehrere (freigegebene) Checkouts unterstützt, deklariert es die `SCC_CAP_MULTICHECKOUT` Funktion und implementiert die- `SccIsMultiCheckOutEnabled` Funktion. Diese Funktion wird immer dann aufgerufen, wenn ein Auscheck Vorgang für eines der Projekte mit Quell Code Verwaltung ausgeführt wird.

 Wenn ein Quellcodeverwaltungs-Plug-in die Erstellung und Verwendung einer *Mssccprj. SCC* -Datei unterstützt, wird die `SCC_CAP_SCCFILE` Funktion deklariert und [sccwillkreatesccfile](../../extensibility/sccwillcreatesccfile-function.md)implementiert. Diese Funktion wird mit einer Liste von Dateien aufgerufen. Die Funktion gibt `TRUE' or 'FALSE` für jede Datei zurück, um anzugeben, ob Visual Studio eine *Mssccprj. SCC* -Datei für Sie verwenden soll. Wenn das Quellcodeverwaltungs-Plug-in diese neuen Funktionen und Funktionen nicht unterstützt, kann der folgende Registrierungsschlüssel verwendet werden, um die Erstellung dieser Dateien zu deaktivieren:

 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl]DoNotCreateTemporaryFilesInSourceControl**  =  *DWORD: 00000001*

> [!NOTE]
> Wenn dieser Registrierungsschlüssel auf *DWORD: 00000000* festgelegt ist, entspricht er dem Schlüssel, der nicht vorhanden ist, und Visual Studio versucht weiterhin, die temporären Dateien zu erstellen. Wenn der Registrierungsschlüssel jedoch auf *DWORD: 00000001* festgelegt ist, versucht Visual Studio nicht, die temporären Dateien zu erstellen. Stattdessen wird davon ausgegangen, dass das Quellcodeverwaltungs-Plug-in die Datei " *Mssccprj. SCC* " nicht unterstützt und keine freigegebenen Auscheck Vorgänge unterstützt.

## <a name="see-also"></a>Siehe auch
- [Neuerungen in der Quellcodeverwaltungs-Plug-in-API, Version 1,2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
