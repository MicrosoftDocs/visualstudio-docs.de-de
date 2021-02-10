---
title: Der Zielprozess wurde mit dem Code &apos;Code&apos; beim Auswerten der Funktion &apos;Funktion&apos; beendet | Microsoft-Dokumentation
ms.date: 4/06/2018
ms.topic: error-reference
f1_keywords:
- vs.debug.error.process_exit_during_func_eval
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 07891e5bcbcab35a4ec5652676a014b87dd32d43
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871636"
---
# <a name="error-the-target-process-exited-with-code-39code39-while-evaluating-the-function-39function39"></a>Fehler: Der Zielprozess wurde mit dem Code &#39;Code&#39; beim Auswerten der Funktion &#39;function&#39; beendet

Vollständiger Meldungstext: Der Zielprozess wurde mit dem Code „Code“ beim Auswerten der Funktion „Funktion“ beendet.

Um das Überprüfen des Status von .NET-Objekten zu vereinfachen, zwingt der Debugger den debuggten Prozess automatisch zur Ausführung von zusätzlichem Code (in der Regel Eigenschaftengettermethoden und `ToString`-Funktionen). In den meisten Szenarien werden diese Funktionen erfolgreich ausgeführt, oder es werden Ausnahmen ausgelöst, die vom Debugger abgefangen werden können. Es gibt jedoch einige Situationen, in denen Ausnahmen nicht abgefangen werden können, weil sie Kernelgrenzen überschreiten, ein Benutzermeldungssystem erfordern oder nicht behebbar sind. Folglich beendet eine Eigenschaftengetter- oder ToString-Methode, die Code ausführt, der den Prozess entweder explizit beendet (z. B. `ExitProcess()` aufruft) oder eine unbehandelte Ausnahme auslöst, die nicht abgefangen werden kann (z. B. `StackOverflowException`), den debuggten Prozess und die Debugsitzung. Wenn diese Fehlermeldung angezeigt wird, ist dieser Fall eingetreten.

Ein häufiger Grund für dieses Problem ist, dass es zu einer Stapelüberlaufausnahme führen kann, wenn der Debugger eine Eigenschaft auswertet, die sich selbst aufruft. Die Stapelüberlaufausnahme kann nicht behoben werden, und der Zielprozess wird beendet.

## <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

Für dieses Problem gibt es zwei mögliche Lösungen.

### <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>Lösung 1: Verhindern, dass der Debugger die Eigenschaftengetter- oder ToString-Methode aufruft 

In der Fehlermeldung wird der Name der Funktion angegeben, die der Debugger aufzurufen versucht hat. Mithilfe des Namens der Funktion können Sie versuchen, diese Funktion im Fenster **Direkt** erneut auszuwerten, um die Auswertung zu debuggen. Das Debuggen ist beim Auswerten über das Fenster **Direkt** (im Gegensatz zu impliziten Auswertungen über die Fenster **Auto/Lokal/Überwachung**) möglich, weil der Debugger bei unbehandelten Ausnahmen unterbricht.

Wenn es Ihnen möglich ist, diese Funktion zu ändern, können Sie verhindern, dass der Debugger die Eigenschaftengetter- oder `ToString`-Methode aufruft. Probieren Sie einen der folgenden Lösungsschritte aus:

* Ändern Sie die Methode in einen anderen Codetyp neben einer Eigenschaftengetter- oder ToString-Methode. Dadurch wird das Problem gelöst.
    - oder -
* (Für `ToString`) Definieren Sie ein `DebuggerDisplay`-Attribut für den Typ. Dann kann der Debugger etwas anderes als `ToString` auswerten.
    - oder -
* (Für einen Eigenschaftengetter) Legen Sie das Attribut `[System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)]` für die Eigenschaft fest. Dies kann sinnvoll sein, wenn Sie über eine Methode verfügen, die aus Gründen der API-Kompatibilität eine Eigenschaft bleiben muss, aber tatsächlich eine Methode sein sollte.

Wenn es Ihnen nicht möglich ist, diese Methode zu ändern, können Sie möglicherweise den Zielprozess möglicherweise an einer alternativen Anweisung unterbrechen und die Auswertung wiederholen.

### <a name="solution-2-disable-all-implicit-evaluation"></a>Lösung 2: Deaktivieren aller impliziten Auswertungen

Wenn das Problem durch die vorherigen Lösungen nicht behoben werden kann, navigieren Sie zu **Extras** > **Optionen**, und deaktivieren Sie die Einstellung **Debuggen** > **Allgemein** > **Eigenschaftenauswertung und andere implizite Funktionsaufrufe zulassen**. Dadurch werden die meisten impliziten Funktionsauswertungen deaktiviert, und das Problem sollte behoben sein.
