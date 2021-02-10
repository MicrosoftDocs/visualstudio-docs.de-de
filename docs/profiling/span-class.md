---
title: span-Klasse | Microsoft-Dokumentation
description: In diesem Artikel erhalten Sie Informationen zur Span-Klasse, und Sie erfahren, wie damit eine Phase der Anwendung definiert werden kann. Außerdem lernen Sie die öffentlichen Konstruktoren der Span-Klasse und die Vererbungshierarchie kennen.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::span
helpviewer_keywords:
- Concurrency::diagnostic::span class
ms.assetid: 527826a8-2590-43ad-b907-7bc0b7288e92
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fff7f91326cac47100f5b2b1b42e22b9c0fc1d9b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949960"
---
# <a name="span-class"></a>span-Klasse
Definiert eine Phase der Anwendung.

## <a name="syntax"></a>Syntax

```cpp
class span;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[span::span-Konstruktor](../profiling/span-span-constructor.md)|Initialisiert eine neue Instanz der `span`-Klasse.|
|[span::~span-Destruktor](../profiling/span-tilde-span-destructor.md)|Zerstört das `span`-Objekt und gibt seine Ressourcen frei.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie
 `span`

## <a name="requirements"></a>Requirements (Anforderungen)
 **Header:** *cvmarkersobj.h*

 **Namespace:** Concurrency::diagnostic

## <a name="see-also"></a>Siehe auch
- [diagnostic-Namespace](../profiling/diagnostic-namespace.md)