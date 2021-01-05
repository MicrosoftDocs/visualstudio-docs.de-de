---
title: Einschränkungen für Zeichen folgen Längen | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Längen von Zeichen folgen, die von verschiedenen von der Quellcodeverwaltungs-Plug-in-API festgelegten Funktionen verwendet werden
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, restrictions on string lengths
ms.assetid: 877173d2-ca27-43b3-b1f4-8379f7c5e268
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5412e930937d029f803f5c6c2b4ddc9d396d9485
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/21/2020
ms.locfileid: "97715521"
---
# <a name="restrictions-on-string-lengths"></a>Einschränkungen für Zeichen folgen Längen
Die Quellcodeverwaltungs-Plug-in-API beschränkt die Längen von Zeichen folgen, die in verschiedenen Funktionen verwendet werden.

## <a name="string-length-values"></a>Zeichen folgen Längenwerte

|Konstante|Wert|
|--------------|-----------|
|`SCC_NAME_LEN`|31|
|`SCC_AUXLABEL_LEN`|31|
|`SCC_USER_LEN`|31|
|`SCC_PRJPATH_LEN`|300|

> [!NOTE]
> Die Länge schließt das abschließende nicht ein `null` . Andere Konstanten mit dem Suffix "_SIZE" anstelle von "_LEN" enthalten Platz für das abschließende `null` .

|Konstante|Wert|
|--------------|-----------|
|SCC_NAME_SIZE|32|
|SCC_AUXLABEL_SIZE|32|
|SCC_USER_SIZE|32|
|SCC_PRJPATH_SIZE|301|

## <a name="see-also"></a>Weitere Informationen
- [Quellcodeverwaltungs-Plug-ins](../extensibility/source-control-plug-ins.md)
