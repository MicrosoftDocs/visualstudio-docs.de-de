---
title: Verschieben instrumentierter Binärdateien | Microsoft-Dokumentation
description: In diesem Artikel erhalten Sie Informationen dazu, wie während der Instrumentierung Tests für die Binärdatei ausgeführt werden, um die Anwendungsleistung zu messen.
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.property.binaries
helpviewer_keywords:
- binaries, instrumented
- instrumentation, instrumented binaries
- instrumented binaries and relocating
- profiling tools, instrumented binaries
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 7c63a1ce67095696d590670327a1a33e2471c145
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907085"
---
# <a name="how-to-relocate-instrumented-binaries"></a>Vorgehensweise: Verschieben instrumentierter Binärdateien

Während der Instrumentation werden Sonden in die Binärdatei eingeführt, um die Anwendungsleistung zu messen. Wenn Sie sich entscheiden, die instrumentierte Binärdatei an einem anderen Ort zu speichern, wird eine Kopie der ursprünglichen Binärdatei instrumentiert und am entsprechenden Speicherort abgelegt. Diese Option ist nützlich, wenn Sie vermeiden möchten, dass der Profiler Ihre ursprüngliche Binärdatei umbenennt. Wenn die Binärdatei nicht an einen anderen Speicherort ausgelagert wird, wird die ursprüngliche Version der Binärdatei überschrieben.

## <a name="to-relocate-instrumented-binary"></a>Verschieben von gemessenen Binärdateien

1. Klicken Sie im **Leistungs-Explorer** mit der rechten Maustaste auf die Leistungssitzung, und klicken Sie dann auf **Eigenschaften**.

2. Klicken Sie auf den **Eigenschaftenseiten** auf die Eigenschaften von **Binärdateien** .

3. Aktivieren Sie das Kontrollkästchen **Gemessene Binärdateien verschieben** .

4. Geben Sie den Speicherort für die instrumentierte Binärdatei an.

## <a name="see-also"></a>Siehe auch

[Konfigurieren von Leistungssitzungen](../profiling/configuring-performance-sessions.md)
[VSInstr](../profiling/vsinstr.md)
