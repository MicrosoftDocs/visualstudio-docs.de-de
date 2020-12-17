---
title: Init | Microsoft-Dokumentation
description: Verwenden der Init()-Methode von VsgDbg, um die In-App-Komponente der Grafikdiagnose zum Protokollieren von Grafikinformationen vorzubereiten.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c55ddec8-9101-4673-979b-4109caca9146
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 094f4f3c64570a0af5396e903541c70a919cc0d3
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996187"
---
# <a name="init"></a>Init
Bereitet die In-App-Komponente der Grafikdiagnose vor, um Grafikinformationen aktiv in einer Grafikprotokolldatei zu erfassen und aufzuzeichnen.

## <a name="syntax"></a>Syntax

```C++
void Init(
  std::function<void (int len, wchar_t * pszBuffer)> vsgLogGetter
);
```

#### <a name="parameters"></a>Parameter
 `vsgLogGetter` Eine aufrufbare Entität, wie etwa eine Funktion, ein Funktionszeiger, Lambda oder ein Funktionsobjekt, die als Parameter die Länge eines Puffers verwendet, der aus `wchar_t` und einem Zeiger auf diesen Puffer besteht, und `void` zurückgibt. Wenn sie aufgerufen wird, bestimmt die aufrufbare Entität den Dateinamen, der verwendet wird, um Grafikinformationen aufzuzeichnen, und schreibt in den angegebenen Puffer, bevor eine Rückgabe erfolgt.

## <a name="remarks"></a>Hinweise
 Die `Init`-Funktion wird automatisch aufgerufen, wenn eine Instanz der `VsgDbg`-Klasse erstellt wird, indem der `bDefaultInit`-Parameter des Konstruktors auf `true` festgelegt wird. Andernfalls muss `Init` explizit aufgerufen werden, bevor Sie Grafikinformationen aktiv erfassen und aufzeichnen können.

 Sie können die aktive Grafikprotokolldatei durch Aufrufen von `UnInit` abschließen und schließen und anschließend weitere Grafikinformationen in einer neuen Grafikprotokolldatei erfassen und aufzeichnen, indem Sie `Init` erneut aufrufen. Sie können dies so oft wiederholen, wie Sie möchten, um mehrere unabhängige Grafikprotokolldateien mithilfe derselben `VsgDbg`-Instanz zu erstellen.

## <a name="see-also"></a>Siehe auch
- [UnInit](init.md)