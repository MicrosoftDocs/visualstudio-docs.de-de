---
description: Definiert durch das Vorhandensein, ob eine Standardinstanz der VsgDbg Class-Klasse bereitgestellt wird, die die programmgesteuerte Erfassungsschnittstelle bereitstellt.
title: VSG_NODEFAULT_INSTANCE | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 19c95b0d-9a4d-441f-9ed7-3acb39e67521
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: eccdd71c66a9f25e1b0a26f4ea851bcccb738a0b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155245"
---
# <a name="vsg_nodefault_instance"></a>VSG_NODEFAULT_INSTANCE
Definiert durch das Vorhandensein, ob eine Standardinstanz der [VsgDbg Class](vsgdbg-class.md)-Klasse bereitgestellt wird, die die programmgesteuerte Erfassungsschnittstelle bereitstellt.

## <a name="syntax"></a>Syntax

```C++
#define VSG_NODEFAULT_INSTANCE
```

## <a name="value"></a>Wert
 Ein Präprozessorsymbol, das durch sein Vorhandensein oder seine Abwesenheit bestimmt, ob eine Standardinstanz der `VsgDbg`-Klasse bereitgestellt wird. Wenn dieses Symbol definiert ist, wird keine Standardinstanz der `VsgDbg`-Klasse bereitgestellt. Andernfalls wird eine Standardinstanz bereitgestellt und initialisiert, bevor das Programm ausgeführt wird.

 Die programmgesteuerte Erfassungsschnittstelle wird durch einen Zeiger mit globalem Gültigkeitsbereich bereitgestellt, `g_pVsgDbg`.

```cpp
VsgDbg *g_pVsgDbg;
```

## <a name="remarks"></a>Hinweise
 Die Standardinstanz ist häufig ausreichend. Um aber die programmgesteuerte Erfassungsschnittstelle innerhalb einer DLL zu verwenden, wenn das D3D-Gerät außerhalb dieser DLL erstellt wurde, müssen Sie eine eigene Instanz der `VsgDbg`-Klasse erstellen und verwalten. Wenn Sie Ihre eigene Schnittstelle zur programmgesteuerten Erfassungs-API auf diese Weise verwalten, deaktivieren Sie die Standardinstanz, indem Sie `VSG_NODEFAULT_INSTANCE` definieren, um so Mehraufwand zu vermeiden.

 Wenn die Standardinstanz nicht deaktiviert ist, wird sie automatisch initialisiert, bevor Ihr Programm ausgeführt wird, und automatisch zerstört, wenn das Programm endet. Sie müssen diese Instanz nicht explizit initialisieren oder deinitialisieren.

 Um die Standardinstanz zu deaktivieren, müssen Sie `VSG_NODEFAULT_INSTANCE` definieren, bevor Sie `vsgcapture.h` in das Programm einschließen.

## <a name="example"></a>Beispiel
 Dieses Beispiel zeigt das Deaktivieren der Standardinstanz:

```cpp
// Define VSG_NODEFAULT_INSTANCE before including vsgcapture.h
#define VSG_NODEFAULT_INSTANCE

#include <vsgcapture.h>
```
