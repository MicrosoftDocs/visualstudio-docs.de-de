---
title: Befehls Code Enumerator | Microsoft-Dokumentation
description: Der Befehls Code Enumerator wird in Optionen für sccgetcommandoptions und sccauffüllen verwendet, um den Befehl anzugeben, für den die Optionen angegeben werden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command code enumerator
- source control plug-ins, command code enumeration
ms.assetid: 5d2c360c-59e4-4da8-bcb4-dd07c7441e40
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2911a39c15fa259057e0b7b48d79e142cda34094
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99938244"
---
# <a name="command-code-enumerator"></a>Befehls Code Enumerator
Dieser Enumerator wird in den Optionen für [sccgetcommandoptions](../extensibility/sccgetcommandoptions-function.md) und [sccpopulatelist](../extensibility/sccpopulatelist-function.md)zum Angeben des Befehls verwendet, für den die Optionen angegeben werden.

## <a name="syntax"></a>Syntax

```
enum SCCCOMMAND {
   SCC_COMMAND_GET,
   SCC_COMMAND_CHECKOUT,
   SCC_COMMAND_CHECKIN,
   SCC_COMMAND_UNCHECKOUT,
   SCC_COMMAND_ADD,
   SCC_COMMAND_REMOVE,
   SCC_COMMAND_DIFF,
   SCC_COMMAND_HISTORY,
   SCC_COMMAND_RENAME,
   SCC_COMMAND_PROPERTIES,
   SCC_COMMAND_OPTIONS
};
```

## <a name="members"></a>Member
SCC_COMMAND_GET entspricht dem [sccget](../extensibility/sccget-function.md).

SCC_COMMAND_CHECKOUT entspricht dem [scccheckout](../extensibility/scccheckout-function.md).

SCC_COMMAND_CHECKIN entspricht dem [scccheckin](../extensibility/scccheckin-function.md).

SCC_COMMAND_UNCHECKOUT entspricht dem [sccuncheckout](../extensibility/sccuncheckout-function.md).

SCC_COMMAND_ADD entspricht dem [sccadd](../extensibility/sccadd-function.md)-.

SCC_COMMAND_REMOVE entspricht dem [SCUP](../extensibility/sccremove-function.md)-Vorgang.

SCC_COMMAND_DIFF entspricht dem [sccdiff](../extensibility/sccdiff-function.md).

SCC_COMMAND_HISTORY entspricht [scchistory](../extensibility/scchistory-function.md).

SCC_COMMAND_RENAME entspricht dem [sccrename](../extensibility/sccrename-function.md).

SCC_COMMAND_PROPERTIES entspricht den [sccproperties-Objekten](../extensibility/sccproperties-function.md).

SCC_COMMAND_OPTIONS entspricht der [sccsetoption](../extensibility/sccsetoption-function.md).

## <a name="see-also"></a>Weitere Informationen
- [Quellcodeverwaltungs-Plug-ins](../extensibility/source-control-plug-ins.md)
- [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)
- [SccPopulateList](../extensibility/sccpopulatelist-function.md)
