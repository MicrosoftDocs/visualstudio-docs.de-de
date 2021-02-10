---
title: 'span:: span-Konstruktor | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::span::span
helpviewer_keywords:
- Concurrency::diagnostic::span constructor
ms.assetid: 8b5578aa-5e5c-4ac7-87c7-ce87c4246e2c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0a813506e64242d1effdb9ed64d35c9ee5d31239
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949973"
---
# <a name="spanspan-constructor"></a>span::span-Konstruktor

Initialisiert eine neue Instanz der `span`-Klasse.

## <a name="syntax"></a>Syntax

```cpp
span(
   const marker_series& _Series,
   _In_ LPCTSTR _Format,
   ...
);
span(
   const marker_series& _Series,
   marker_importance _Importance,
   _In_ LPCTSTR _Format,
   ...
);
span(
   const marker_series& _Series,
   int _Category,
   _In_ LPCTSTR _Format,
   ...
);
span(
   const marker_series& _Series,
   marker_importance _Importance,
   int _Category,
   _In_ LPCTSTR _Format,
   ...
);
```

#### <a name="parameters"></a>Parameter

`_Series`: gültiger Markerreihenkontext.

`_Format`: eine zusammengesetzte Formatzeichenfolge mit Text, der „0“ (null) oder mehr Formatelemente enthält, die Objekten in der Argumentliste entsprechen.

`_Importance`: die Wichtigkeitsstufe.

`_Category`: die Kategorie.

## <a name="requirements"></a>Anforderungen

**Header:** *cvmarkersobj.h*

**Namespace:** Concurrency::diagnostic

## <a name="see-also"></a>Siehe auch

- [span-Klasse](../profiling/span-class.md)