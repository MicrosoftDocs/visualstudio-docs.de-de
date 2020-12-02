---
title: Verwenden von Speicherabbilddateien im Debugger | Microsoft-Dokumentation
ms.custom: seodec18
ms.date: 11/05/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.crashdump
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- dumps, about dumps
- crash dumps
- dump files
- dumps
ms.assetid: b71be6dc-57e0-4730-99d2-b540a0863e49
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dbfd8ac877fce4b1808a76e3bb2a66ac595693de
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/25/2020
ms.locfileid: "95970624"
---
# <a name="dump-files-in-the-visual-studio-debugger"></a>Speicherabbilddateien im Visual Studio-Debugger

<a name="BKMK_What_is_a_dump_file_"></a> Bei einer *Speicherabbilddatei* handelt es sich um eine Momentaufnahme, die den Prozess anzeigt, der ausgeführt wurde, sowie die Module, die zu einem bestimmten Zeitpunkt für eine App geladen wurden. Ein Speicherabbild mit Heapinformationen enthält außerdem eine Momentaufnahme des Arbeitsspeichers der App zu diesem Zeitpunkt.

Das Öffnen einer Speicherabbilddatei mit einem Heap in Visual Studio ist vergleichbar mit dem Anhalten an einem Haltepunkt in einer Debugsitzung. Obwohl die Ausführung nicht fortgesetzt werden kann, können Sie die Stapel-, Thread- und Variablenwerte der App zum Zeitpunkt der Erstellung des Speicherabbilds überprüfen.

Speicherabbilder werden hauptsächlich dazu verwendet, Probleme auf Computern zu debuggen, auf die Entwickler keinen Zugriff haben. Sie können eine Speicherabbilddatei vom Computer eines Kunden verwenden, wenn der Absturz des Kundencomputers oder ein nicht reagierendes Programm auf Ihrem Computer nicht reproduzierbar ist. Tester erstellen außerdem Speicherabbilder, um Daten zu Abstürzen oder nicht reagierenden Programmen für weitere Tests zu speichern.

Der Visual Studio-Debugger kann Dumpdateien für verwalteten oder systemeigenen Code speichern. Er kann Speicherabbilddateien debuggen, die von Visual Studio oder anderen Apps erstellt wurden, die Dateien im *Minidump*-Format speichern.

## <a name="requirements-and-limitations"></a><a name="BKMK_Requirements_and_limitations"></a> Anforderungen und Einschränkungen

- Für das Debuggen von Speicherabbilddateien von 64-Bit-Computern muss Visual Studio auf einem 64-Bit-Computer ausgeführt werden.

- Visual Studio kann Dumpdateien systemeigener Anwendungen von ARM-Geräten debuggen. Visual Studio kann auch Speicherabbilddateien verwalteter Apps von ARM-Geräten debuggen, jedoch nur im nativen Debugger.

- Für das Debuggen von Speicherabbilddateien im [Kernel-Modus](/windows-hardware/drivers/debugger/kernel-mode-dump-files) oder zum Verwenden der Debugerweiterung [SOS.dll](/dotnet/framework/tools/sos-dll-sos-debugging-extension) in Visual Studio laden Sie die Debugtools für Windows im [Windows-Treiberkit (WDK)](/windows-hardware/drivers/download-the-wdk) herunter.

- Visual Studio kann die Speicherabbilddateien nicht debuggen, die im älteren Format gespeichert wurden, das auch als [vollständiges Benutzermodusspeicherabbild](/windows/desktop/wer/collecting-user-mode-dumps) bezeichnet wird. Beachten Sie, dass ein vollständiges Benutzermodusspeicherabbild nicht mit einem Speicherabbild mit Heapinformationen identisch ist.

- Das Debuggen von Dumpdateien mit optimiertem Code kann unübersichtlich sein. Beispielsweise kann das Compiler-Inlining von Funktionen unerwartete Aufruflisten ergeben, und andere Optimierungen könnten die Lebensdauer der Variablen beeinflussen.

## <a name="dump-files-with-or-without-heaps"></a><a name="BKMK_Dump_files__with_or_without_heaps"></a> Dumpdateien mit oder ohne Heaps

Speicherabbilddateien können Heapinformationen enthalten, müssen es jedoch nicht.

- **Speicherabbilddateien mit Heaps** enthalten eine Momentaufnahme des Arbeitsspeichers der App, einschließlich der Werte von Variablen zum Zeitpunkt der Erstellung des Speicherabbilds. Visual Studio speichert auch die Binärdateien der geladenen nativen Module in der Speicherabbilddatei mit einem Heap, wodurch das Debuggen wesentlich vereinfacht wird. Visual Studio kann Symbole aus einer Speicherabbilddatei mit einem Heap laden, selbst wenn keine App-Binärdatei gefunden werden kann.

- **Speicherabbilddateien ohne Heaps** sind wesentlich kleiner als Speicherabbilder mit Heaps. Der Debugger muss jedoch die App-Binärdateien laden, um Symbolinformationen finden zu können. Die geladenen Binärdateien müssen exakt mit denen übereinstimmen, die während der Erstellung des Speicherabbilds ausgeführt wurden. Speicherabbilddateien ohne Heaps speichern nur die Werte der Stapelvariablen.

## <a name="create-a-dump-file"></a><a name="BKMK_Create_a_dump_file"></a> Erstellen einer Dumpdatei

Beim Debuggen eines Prozesses in Visual Studio können Sie eine Speicherabbilddatei speichern, wenn der Debugger an einer Ausnahme oder an einem Haltepunkt angehalten wurde.

Wenn [Just-In-Time-Debuggen](../debugger/just-in-time-debugging-in-visual-studio.md) aktiviert wurde, können Sie den Visual Studio-Debugger an einen abgestürzten Prozess außerhalb von Visual Studio anfügen und dann eine Speicherabbilddatei des Debuggers speichern. Weitere Informationen finden Sie unter [Anfügen an laufende Prozesse mit dem Visual Studio Debugger](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

**So speichern Sie eine Dumpdatei:**

1. Wenn die Ausführung während des Debuggens an einem Fehler oder Haltepunkt angehalten wurde, klicken Sie auf **Debuggen** > **Speicherabbild speichern unter…** .

1. Wählen Sie im Dialogfeld **Speicherabbild speichern unter…** in der Liste **Dateityp** die Option **Minidump** oder **Minidump mit Heap** (Standardeinstellung) aus.

1. Folgen Sie einem Pfad, wählen Sie einen Namen für die Speicherabbilddatei aus, und klicken Sie dann auf **Speichern**.

>[!NOTE]
>Speicherabbilddateien können mit jedem Programm erstellt werden, das das Windows-Minidumpformat unterstützt. Beispielsweise können mit dem **Procdump**-Befehlszeilenhilfsprogramm von [Windows Sysinternals](/sysinternals/) Dumpdateien zu Prozessabstürzen anhand von Triggern oder bedarfsabhängig erstellt werden. Unter [Anforderungen und Einschränkungen](../debugger/using-dump-files.md#BKMK_Requirements_and_limitations) finden Sie weitere Informationen zur Verwendung anderer Tools für die Erstellung von Speicherabbilddateien.

## <a name="open-a-dump-file"></a><a name="BKMK_Open_a_dump_file"></a> Öffnen einer Dumpdatei

1. Klicken Sie in Visual Studio auf **Datei** > **Öffnen** > **Datei**.

1. Wählen Sie im Dialogfeld **Datei öffnen** die Dumpdatei aus. Die Dateierweiterung lautet in der Regel *DMP*. Klicken Sie auf **OK**.

   Das Fenster **Zusammenfassung der Minidump-Datei** zeigt eine Zusammenfassung und Informationen zum Modul für die Speicherabbilddatei sowie Aktionen, die Sie ausführen können.

   ![Minidump-Zusammenfassungsseite](../debugger/media/dbg_dump_summarypage.png "Minidump-Zusammenfassungsseite")

1. Führen Sie unter **Aktionen** Folgendes aus:
   - Klicken Sie auf **Symbolpfade festlegen**, um Speicherorte für das Laden der Symbole festzulegen.
   - Klicken Sie zum Starten des Debuggens auf **Debug with Managed Only** (Nur verwaltet debuggen), **Debug with Native Only** (Nur nativ debuggen), **Debug with Mixed** (Gemischt debuggen) oder **Debug with Managed Memory** (Mit verwaltetem Arbeitsspeicher debuggen).

## <a name="find-exe-pdb-and-source-files"></a><a name="BKMK_Find_binaries__symbol___pdb__files__and_source_files"></a> Suchen nach EXE-, PDB- und Quelldateien

Wenn Sie alle Debugfeatures für eine Speicherabbilddatei verwenden möchten, ist für Visual Studio Folgendes erforderlich:

- Die *EXE*-Datei, für die das Speicherabbild erstellt wurde, sowie weitere Binärdateien (z. B. DLLs), die der Speicherabbildprozess verwendet hat.
- Symboldateien (*PDB*-Dateien) für die *EXE*-Datei und andere Binärdateien.
- Die *EXE*- und *PDB*-Dateien, die exakt mit der Version und dem Build der Dateien zum Zeitpunkt der Erstellung des Speicherabbilds übereinstimmen.
- Quelldateien für die relevanten Module. Sie können die Disassemblierung der Module verwenden, wenn Sie die Quelldateien nicht finden können.

Wenn die Speicherabbilddatei Heapdaten enthält, kann Visual Studio mit fehlenden Binärdateien für einige Module umgehen, es müssen jedoch Binärdateien für genügend Module vorhanden sein, um gültige Aufruflisten generieren zu können.

### <a name="search-paths-for-exe-files"></a>Suchpfade für EXE-Dateien

Visual Studio durchsucht automatisch diese Speicherorte für *EXE*-Dateien, die nicht in der Speicherabbilddatei enthalten sind:

1. Der Ordner, der die Speicherabbilddatei enthält.
2. Der Modulpfad, den die Speicherabbilddatei angibt. Dabei handelt es sich um den Modulpfad auf dem Computer, der das Speicherabbild erfasst hat.
3. Die unter **Extras** (oder **Debuggen**) > **Optionen** > **Debuggen** > **Symbole** angegebenen Symbolpfade. Sie können auch die Seite **Symbole** im Bereich **Aktionen** des Fensters **Dump File Summary** (Zusammenfassung der Speicherabbilddatei) öffnen. Auf dieser Seite können Sie mehr Speicherorte für die Suche hinzufügen.

### <a name="use-the-no-binary-no-symbols-or-no-source-found-pages"></a>Verwenden der Seiten „Keine Binärdatei gefunden“, „Keine Symbole gefunden“ oder „Keine Quelle gefunden“

Wenn Visual Studio die Dateien nicht finden kann, die zum Debuggen eines Moduls im Speicherabbild erforderlich sind, wird eine entsprechende Seite angezeigt (**Keine Binärdatei gefunden**, **Keine Symbole gefunden** oder **Keine Quelle gefunden**). Diese Seiten enthalten ausführliche Informationen zu den Ursachen des Problems und stellen Aktionslinks bereit, mit denen Sie den richtigen Speicherort der Dateien identifizieren können. Weitere Informationen finden Sie unter [Angeben von Symbol- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="see-also"></a>Siehe auch

- [Just-In-Time debugging (Just-In-Time-Debuggen)](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Specify symbol (.pdb) and source files (Angeben von Symboldateien (PDB) und Quelldateien)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [IntelliTrace](../debugger/intellitrace.md)