---
title: Intellisenabhostflags | Microsoft-Dokumentation
description: Die intellisenabhostflags-Enumeration gibt IntelliSense-hostflags an. In diesem Artikel werden die Enumerationswerte beschrieben.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IntellisenseHostFlags
helpviewer_keywords:
- IntelliSense, IntellisenseHostFlags enumeration
- IntellisenseHostFlags enumeration
ms.assetid: 0930640b-eb84-48ef-a8f7-d4268f55c99c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b206cc4aa7c1ff388d6868fa8a0533d15da094ff
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97487503"
---
# <a name="intellisensehostflags"></a>IntelliSenseHostFlags
Gibt IntelliSense-Hostflags an.

## <a name="syntax"></a>Syntax

```cpp
enum IntellisenseHostFlags
{
    IHF_READONLYCONTEXT      = 0x00000001
    IHF_NOSEPARATESUBJECT    = 0x00000002
    IHF_SINGLELINESUBJECT    = 0x00000004
    IHF_FORCECOMMITTOCONTEXT = 0x00000008
    IHF_OVERTYPE             = 0x00000010
};
```

### <a name="parameters"></a>Parameter

|Member|Beschreibung|
|-------------|-----------------|
|`IHF_READONLYCONTEXT`|Der Kontext Puffer ist schreibgeschützt.|
|`IHF_NOSEPARATESUBJECT`|Kein Betrefftext. Der Kontext Puffer enthält IntelliSense-Target (impliziert `!IHF_READONLYCONTEXT` ).|
|`IHF_SINGLELINESUBJECT`|Der Betrefftext ist nicht mehrzeilige Werte.|
|`IHF_FORCECOMMITTOCONTEXT`|Wie in `CanCommitIntoReadOnlyBuffer`.|
|`IHF_OVERTYPE`|Die Bearbeitung (im Betreff oder Kontext) sollte im über Schreib-Modus erfolgen.|

## <a name="requirements"></a>Anforderungen
 Singlefileeditor. idl

## <a name="see-also"></a>Weitere Informationen
- <xref:Microsoft.VisualStudio.TextManager.Interop>
