---
title: Projektordner mit Quellcode-Steuerungs Speicher vergleichen | Microsoft-Dokumentation
description: In der Quellcodeverwaltungs-Plug-in-API wird der Vergleich zwischen dem lokalen Projektordner und der Quell Code Verwaltung mithilfe von sccdirqueryinfo und sccdirdiff durchgeführt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, comparing versions
- source control plug-ins, local project folders
ms.assetid: 65217e8b-15a6-4446-92b0-4cff1c6220f5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ed69c6e503614cd1b2ed8e21716a5edcb4babd2b
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877584"
---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>Optionaler Vergleich des lokalen Projektordners mit dem Speicher der Quellcodeverwaltung
In der Quellcodeverwaltungs-Plug-in-API 1,2 wird der Vergleich zwischen dem lokalen Projektordner und der Quell Code Verwaltung mithilfe der Funktionen [sccdirqueryinfo](../../extensibility/sccdirqueryinfo-function.md) und [sccdirdiff](../../extensibility/sccdirdiff-function.md)durchgeführt.

 Wenn Sie in **Projektmappen-Explorer** einen Ordner anstelle einer einzelnen Datei auswählen, ruft das Kontextmenü für die **Vergleichs Versionen** das neue [sccdirqueryinfo](../../extensibility/sccdirqueryinfo-function.md) -und [sccdirdiff](../../extensibility/sccdirdiff-function.md) -Element im Quellcodeverwaltungs-Plug-in auf.

## <a name="new-capability-flags"></a>Neue funktionsflags
 `SCC_CAP_DIRECTORYDIFF`

 `SCC_CAP_DIRECTORYCHECKOUT`

## <a name="new-functions"></a>Neue Funktionen
- [SccDirDiff](../../extensibility/sccdirdiff-function.md)

- [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)

 Die- `SccDirQueryInfo` Funktion wird vor aufgerufen `SccDirDiff` , um zu bestimmen, ob das Arbeitsverzeichnis Quell gesteuert ist. Die `SccDirDiff` -Funktion zeigt die Unterschiede zwischen dem aktuellen lokalen Verzeichnis und dem entsprechenden Ordner für die Quell Code Verwaltung an. Dieser Befehl fordert das Quellcodeverwaltungs-Plug-in auf, die Liste der Änderungen im Verzeichnis anzuzeigen. Ein Quellcodeverwaltungs-Plug-in stellt eine eigene Benutzeroberfläche zum Anzeigen der Unterschiede bereit.

> [!NOTE]
> Diese Funktion verwendet die gleichen [Befehlsflags wie sccdiff](../../extensibility/sccdiff-function.md). Als Anbieter von Quellcodeverwaltungs-Plug-Ins können Sie den Vorgang für die schnelle diff-Ausführung für Verzeichnisse nicht unterstützen.

## <a name="see-also"></a>Weitere Informationen
- [Neuigkeiten in API-Version 1.2 des Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
