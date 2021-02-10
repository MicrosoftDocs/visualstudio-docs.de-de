---
title: Threading Unterstützung in Office
description: Threading wird im Microsoft Office-Objektmodell unterstützt. Das Office-Objektmodell ist nicht Thread sicher, kann jedoch mit mehreren Threads in einer Office-Projekt Mappe arbeiten.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- multiple threads [Office development in Visual Studio]
- threading [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], threading support
- object models [Office development in Visual Studio], threading support
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 6fd35551c5c40494c169fb569113e3530f633a6f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99940799"
---
# <a name="threading-support-in-office"></a>Threading Unterstützung in Office
  Dieser Artikel enthält Informationen dazu, wie Threading im Microsoft Office-Objektmodell unterstützt wird. Das Office-Objektmodell ist nicht Thread sicher, aber es ist möglich, mit mehreren Threads in einer Office-Projekt Mappe zu arbeiten. Office-Anwendungen sind Component Object Model (com)-Server. Com ermöglicht Clients, com-Server für beliebige Threads aufzurufen. Bei com-Servern, die nicht Thread sicher sind, bietet com einen Mechanismus zum Serialisieren gleichzeitiger Aufrufe, sodass immer nur ein logischer Thread auf dem Server ausgeführt wird. Dieser Mechanismus wird als Single Thread-Apartment-Modell (STA) bezeichnet. Da Aufrufe serialisiert werden, werden Aufrufer möglicherweise für Zeiträume blockiert, während der Server ausgelastet ist oder andere Aufrufe in einem Hintergrund Thread verarbeitet.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="knowledge-required-when-using-multiple-threads"></a>Erforderliche Kenntnisse bei der Verwendung mehrerer Threads
 Um mit mehreren Threads arbeiten zu können, müssen Sie mindestens über grundlegende Kenntnisse der folgenden Aspekte von Multithreading verfügen:

- Windows-APIs

- COM-Multithread-Konzepte

- Parallelität

- Synchronisierung

- Marshalling

  Allgemeine Informationen zum Multithreading finden Sie unter [verwaltetes Threading](/dotnet/standard/threading/).

  Office wird im Haupt-STA ausgeführt. Wenn Sie sich mit den Auswirkungen von vertraut machen, können Sie verstehen, wie mehrere Threads mit Office verwendet werden.

## <a name="basic-multithreading-scenario"></a>Grundlegendes Multithreading-Szenario
 Code in Office-Projektmappen wird immer auf dem Hauptbenutzer Oberflächen-Thread ausgeführt. Möglicherweise möchten Sie die Anwendungsleistung durch Ausführen einer separaten Aufgabe in einem Hintergrund Thread glätten. Das Ziel besteht darin, zwei Aufgaben scheinbar gleichzeitig auszuführen, anstatt eine Aufgabe gefolgt von einer anderen Aufgabe, die zu einer reibungsloseren Ausführung führen sollte (der Hauptgrund für die Verwendung mehrerer Threads). Beispielsweise können Sie Ihren Ereignis Code im Haupt Thread der Excel-Benutzeroberfläche ausführen, und in einem Hintergrund Thread können Sie eine Aufgabe ausführen, die Daten von einem Server sammelt und Zellen in der Excel-Benutzeroberfläche mit den Daten vom Server aktualisiert.

## <a name="background-threads-that-call-into-the-office-object-model"></a>Hintergrundthreads, die das Office-Objektmodell aufzurufen
 Wenn ein Hintergrund Thread eine Office-Anwendung aufruft, wird der-Befehl automatisch über die STA-Grenze gemarshallt. Es gibt jedoch keine Garantie dafür, dass die Office-Anwendung den Aufruf zu dem Zeitpunkt verarbeiten kann, zu dem der Hintergrund Thread dies vornimmt. Es gibt mehrere Möglichkeiten:

1. Die Office-Anwendung muss Nachrichten Nachrichten, die die Möglichkeit haben, in den-Befehl einzugeben. Wenn eine hohe Verarbeitung durchgeführt wird, ohne dies zu erzielen, kann es eine Weile dauern.

2. Wenn bereits ein anderer logischer Thread im Apartment vorhanden ist, kann der neue Thread nicht eingegeben werden. Dies ist oft der Fall, wenn ein logischer Thread in die Office-Anwendung gelangt und dann einen wieder eintretende Rückruf an das Apartment des Aufrufers sendet. Die Anwendung ist blockiert und wartet darauf, dass der Rückruf zurückgegeben wird.

3. Excel befindet sich möglicherweise in einem Status, in dem ein eingehender-Vorgang nicht sofort behandelt werden kann. Beispielsweise kann die Office-Anwendung ein modales Dialogfeld anzeigen.

   Für die Möglichkeiten 2 und 3 stellt com die [IMessageFilter](/windows/desktop/api/objidl/nn-objidl-imessagefilter) -Schnittstelle bereit. Wenn der Server ihn implementiert, werden alle Aufrufe durch die [handleincomingcallmethode](/windows/desktop/api/objidl/nf-objidl-imessagefilter-handleincomingcall) eingegeben. Für die Möglichkeit 2 werden Aufrufe automatisch abgelehnt. Der Server kann den-Befehl abhängig von den jeweiligen Umständen ablehnen. Wenn der Aufruf abgelehnt wird, muss der Aufrufer entscheiden, was zu tun ist. Normalerweise implementiert der Aufrufer [IMessageFilter](/windows/desktop/api/objidl/nn-objidl-imessagefilter). in diesem Fall wird er über die Ablehnung durch die [retryrejectedcallmethode](/windows/desktop/api/objidl/nf-objidl-imessagefilter-retryrejectedcall) benachrichtigt.

   Im Fall von Projektmappen, die mithilfe der Office-Entwicklungs Tools in Visual Studio erstellt wurden, konvertiert COM-Interop allerdings alle abgelehnten Aufrufe in eine <xref:System.Runtime.InteropServices.COMException> ("der Nachrichtenfilter gibt an, dass die Anwendung ausgelastet ist"). Wenn Sie einen Objektmodell Aufruf in einem Hintergrund Thread durchführen, müssen Sie darauf vorbereitet sein, diese Ausnahme zu behandeln. In der Regel umfasst dies einen Wiederholungsversuch für eine bestimmte Zeitspanne und dann das Anzeigen eines Dialog Felds. Sie können den Hintergrund Thread jedoch auch als STA erstellen und dann einen Nachrichtenfilter für diesen Thread registrieren, um diesen Fall zu behandeln.

## <a name="start-the-thread-correctly"></a>Thread ordnungsgemäß starten
 Wenn Sie einen neuen STA-Thread erstellen, legen Sie den Apartment Zustand auf STA fest, bevor Sie den Thread starten. Das folgende Codebeispiel veranschaulicht, wie Sie dabei vorgehen:

 [!code-csharp[Trin_VstcoreCreatingExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/ThisWorkbook.cs#5)]
 [!code-vb[Trin_VstcoreCreatingExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/ThisWorkbook.vb#5)]

 Weitere Informationen finden Sie unter [bewährte Methoden für das verwaltete Threading](/dotnet/standard/threading/managed-threading-best-practices).

## <a name="modeless-forms"></a>Nicht modante Formulare
 Ein nicht modalem Formular ermöglicht eine bestimmte Art von Interaktion mit der Anwendung, während das Formular angezeigt wird. Der Benutzer interagiert mit dem Formular, und das Formular interagiert mit der Anwendung, ohne zu schließen. Das Office-Objektmodell unterstützt verwaltete, nicht Modalformen. Sie sollten jedoch nicht in einem Hintergrund Thread verwendet werden.

## <a name="see-also"></a>Weitere Informationen
- [Threading (c#)](/dotnet/csharp/programming-guide/concepts/threading/index)
- [Threading (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/threading/index)
- [Verwenden von Threads und Threading](/dotnet/standard/threading/using-threads-and-threading)
- [Entwerfen und Erstellen von Office-Lösungen](../vsto/designing-and-creating-office-solutions.md)
