---
title: Hinzufügen einer Anmerkung zum Sperr Verhalten | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _Releases_nonreentrant_lock_
- _Lock_kind_mutex_
- _Lock_kind_critical_section_
- _Acquires_lock_
- _Releases_lock_
- _Has_lock_kind_
- _Releases_exclusive_lock_
- _Post_same_lock_
- _Requires_exclusive_lock_held_
- _Requires_shared_lock_held_
- _Lock_kind_semaphore_
- _Requires_lock_held_
- _Acquires_exclusive_lock_
- _Create_lock_level_
- _Acquires_nonreentrant_lock_
- _Releases_shared_lock_
- _Has_lock_level_
- _Lock_kind_spin_lock_
- _Requires_lock_not_held_
- _Acquires_shared_lock_
- _Requires_no_locks_held_
- _Lock_level_order_
- _Lock_kind_event_
ms.assetid: 07769c25-9b97-4ab7-b175-d1c450308d7a
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 00d3c90ce7e21ab4e9852ed937481103c351609b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "77271590"
---
# <a name="annotating-locking-behavior"></a>Hinzufügen einer Anmerkung zum Sperrverhalten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Um Parallelitäts Fehler in Ihrem Multithread-Programm zu vermeiden, befolgen Sie immer eine angemessene Sperr Disziplin, und verwenden Sie SAL-Anmerkungen.  
  
 Parallelitäts Fehler sind bekanntermaßen schwer zu reproduzieren, zu diagnostizieren und zu debuggen, da Sie nicht deterministisch sind. Die Argumentation der Thread Interaktion ist am besten schwierig und ist nicht mehr praktikabel, wenn Sie einen Code Körper entwerfen, der mehr als einige Threads enthält. Daher empfiehlt es sich, eine Sperr Disziplin in ihren Multithreadprogrammen zu befolgen. Wenn Sie z. b. eine Sperr Reihenfolge während des Erstellens mehrerer Sperren einhalten, können Deadlocks vermieden werden, und das Abrufen der richtigen Schutzsperre, bevor Sie auf eine freigegebene Ressource zugreifen, hilft  
  
 Leider können scheinbar einfache Sperr Regeln in der Praxis erstaunlich schwer befolgt werden. Eine grundlegende Einschränkung in den heutigen Programmiersprachen und Compilern besteht darin, dass Sie die Spezifikation und die Analyse der Parallelitäts Anforderungen nicht direkt unterstützen. Programmierer müssen sich auf informelle Code Kommentare verlassen, um Ihre Absichten in Bezug auf die Verwendung von Sperren auszudrücken.  
  
 Parallelitäts SAL-Anmerkungen sind so konzipiert, dass Sie das Sperren von Nebeneffekten, die Sperr Verantwortung, die Daten Überwachungen, die Hierarchie der Sperr Reihenfolge und ein anderes erwartetes Sperr Verhalten angeben können. Durch die explizite Durchführung impliziter Regeln bieten SAL-Parallelitäts Anmerkungen eine konsistente Möglichkeit, zu dokumentieren, wie der Code Sperr Regeln verwendet. Neben läufigkeits Anmerkungen verbessern auch die Fähigkeit von Code Analysetools, Racebedingungen, Deadlocks, nicht übereinstimmende Synchronisierungs Vorgänge und andere feine Parallelitäts Fehler zu finden.  
  
## <a name="general-guidelines"></a>Allgemeine Richtlinien  
 Mithilfe von Anmerkungen können Sie die Verträge, die durch Funktionsdefinitionen zwischen Implementierungen (Callees) und Clients (Aufrufer) impliziert werden, sowie Express invarianten und andere Eigenschaften des Programms angeben, die die Analyse weiter verbessern können.  
  
 SAL unterstützt viele verschiedene Arten von Sperr primitiven – z. b. kritische Abschnitte, Mutexen, Spin-Sperren und andere Ressourcen Objekte. Viele Parallelitäts Anmerkungen nehmen einen Sperr Ausdruck als Parameter an. Gemäß der Konvention wird eine Sperre durch den Pfad Ausdruck des zugrunde liegenden Sperr Objekts bezeichnet.  
  
 Einige Thread Besitz Regeln, die berücksichtigt werden sollten:  
  
- Dreh Sperren sind nicht gezählte sperren, die den Thread Besitz löschen.  
  
- Mutexen und wichtige Abschnitte sind gezählte Sperren mit einem eindeutigen Thread Besitz.  
  
- Semaphore und Ereignisse sind gezählte sperren, die keinen eindeutigen Thread Besitz aufweisen.  
  
## <a name="locking-annotations"></a>Sperren von Anmerkungen  
 In der folgenden Tabelle sind die Sperr Anmerkungen aufgeführt.  
  
|Anmerkung|BESCHREIBUNG|  
|----------------|-----------------|  
|`_Acquires_exclusive_lock_(expr)`|Kommentiert eine Funktion und gibt an, dass die Funktion im Post-Zustand um eine exklusive Sperr Anzahl des Sperr Objekts, das durch benannt wird, inkreliert `expr` .|  
|`_Acquires_lock_(expr)`|Kommentiert eine Funktion und gibt an, dass die Funktion im Post-Zustand um eine die Sperrenanzahl des Sperr Objekts, das durch benannt wird, inkreliert `expr` .|  
|`_Acquires_nonreentrant_lock_(expr)`|Die Sperre, die von benannt `expr` wird, wird abgerufen.  Wenn die Sperre bereits besteht, wird ein Fehler gemeldet.|  
|`_Acquires_shared_lock_(expr)`|Kommentiert eine Funktion und gibt an, dass die Funktion im Post-Zustand um eine Anzahl der freigegebenen Sperren des Sperr Objekts, das durch benannt wird, inkreliert `expr` .|  
|`_Create_lock_level_(name)`|Eine Anweisung, die das Symbol `name` als Sperr Ebene deklariert, damit Sie in den Anmerkungen und verwendet werden kann `_Has_Lock_level_` `_Lock_level_order_` .|  
|`_Has_lock_kind_(kind)`|Kommentiert alle-Objekte, um die Typinformationen eines Ressourcen Objekts zu verfeinern. Manchmal wird ein gemeinsamer Typ für verschiedene Arten von Ressourcen verwendet, und der überladene Typ reicht nicht aus, um die semantischen Anforderungen zwischen verschiedenen Ressourcen zu unterscheiden. Im folgenden finden Sie eine Liste vordefinierter `kind` Parameter:<br /><br /> `_Lock_kind_mutex_`<br /> Sperrenkind-ID für Mutexes.<br /><br /> `_Lock_kind_event_`<br /> Sperrenkind-ID für Ereignisse.<br /><br /> `_Lock_kind_semaphore_`<br /> Sperrenkind-ID für Semaphore.<br /><br /> `_Lock_kind_spin_lock_`<br /> Sperrenkind-ID für Spin-sperren.<br /><br /> `_Lock_kind_critical_section_`<br /> Sperrenkind-ID für kritische Abschnitte.|  
|`_Has_lock_level_(name)`|Kommentiert ein Sperr Objekt und gibt ihm die Sperr Ebene von `name` .|  
|`_Lock_level_order_(name1, name2)`|Eine-Anweisung, die die Sperr Anordnung zwischen `name1` und ermöglicht `name2` .|  
|`_Post_same_lock_(expr1, expr2)`|Kommentiert eine Funktion und gibt an, dass die beiden Sperren im Post-Zustand `expr1` `expr2` so behandelt werden, als wären Sie das gleiche Sperr Objekt.|  
|`_Releases_exclusive_lock_(expr)`|Kommentiert eine Funktion und gibt an, dass die-Funktion im Post-Zustand um eine exklusive Sperrenanzahl des Sperr Objekts dekregiert, das von benannt wird `expr` .|  
|`_Releases_lock_(expr)`|Kommentiert eine Funktion und gibt an, dass die-Funktion im Post-Zustand um eine Sperrenanzahl des Sperr Objekts dekregiert, das durch benannt wird `expr` .|  
|`_Releases_nonreentrant_lock_(expr)`|Die Sperre, die von benannt `expr` wird, wird freigegeben. Wenn die Sperre derzeit nicht aufrechterhalten wird, wird ein Fehler gemeldet.|  
|`_Releases_shared_lock_(expr)`|Kommentiert eine Funktion und gibt an, dass die Funktion im Post-Zustand um einen Wert für die freigegebene Sperre des Sperr Objekts, das durch benannt wird, dekregiert `expr` .|  
|`_Requires_lock_held_(expr)`|Kommentiert eine Funktion und gibt an, dass die Sperrenanzahl des Objekts, das durch benannt ist, mindestens `expr` eins ist.|  
|`_Requires_lock_not_held_(expr)`|Kommentiert eine Funktion und gibt an, dass die Sperrenanzahl des Objekts, das durch benannt ist, in der Vorbedingung `expr` 0 (null) ist.|  
|`_Requires_no_locks_held_`|Kommentiert eine Funktion und gibt an, dass die Sperr Anzahl aller Sperren, die der Prüfung bekannt sind, 0 (null) ist.|  
|`_Requires_shared_lock_held_(expr)`|Kommentiert eine Funktion und gibt an, dass die freigegebene Sperrenanzahl des Objekts, das durch benannt ist, mindestens `expr` eins ist.|  
|`_Requires_exclusive_lock_held_(expr)`|Kommentiert eine Funktion und gibt an, dass im Voraus die exklusive Sperr Anzahl des Objekts, das durch benannt ist, mindestens `expr` eins ist.|  
  
## <a name="sal-intrinsics-for-unexposed-locking-objects"></a>Systeminterne SAL-Funktionen für nicht verfügbare Sperrobjekte  
 Bestimmte Sperrobjekte werden von der Implementierung der zugehörigen Sperr Funktionen nicht verfügbar gemacht.  In der folgenden Tabelle werden die systeminternen SAL-Variablen aufgelistet, die Anmerkungen für Funktionen ermöglichen, die für diese nicht verfügbar gemachten Sperrobjekte verwendet werden.  
  
|Anmerkung|BESCHREIBUNG|  
|----------------|-----------------|  
|`_Global_cancel_spin_lock_`|Beschreibt die Abbruch Drehsperre.|  
|`_Global_critical_region_`|Beschreibt den kritischen Bereich.|  
|`_Global_interlock_`|Beschreibt Interlocked-Vorgänge.|  
|`_Global_priority_region_`|Beschreibt den Prioritäts Bereich.|  
  
## <a name="shared-data-access-annotations"></a>Anmerkungen zum freigegebenen Datenzugriff  
 In der folgenden Tabelle sind die Anmerkungen für den Zugriff auf freigegebene Daten aufgeführt.  
  
|Anmerkung|BESCHREIBUNG|  
|----------------|-----------------|  
|`_Guarded_by_(expr)`|Kommentiert eine Variable und gibt an, dass bei jedem Zugriff auf die Variable die Sperrenanzahl des Sperr Objekts, das durch benannt ist, mindestens `expr` eins ist.|  
|`_Interlocked_`|Kommentiert eine Variable und entspricht `_Guarded_by_(_Global_interlock_)` .|  
|`_Interlocked_operand_`|Der mit Anmerkungen versehene Funktionsparameter ist der Ziel Operand einer der verschiedenen Interlocked-Funktionen.  Diese Operanden müssen über bestimmte zusätzliche Eigenschaften verfügen.|  
|`_Write_guarded_by_(expr)`|Kommentiert eine Variable und gibt an, dass bei jeder Änderung der Variablen die Sperrenanzahl des Sperr Objekts, das durch benannt ist, mindestens `expr` eins ist.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwenden von Sal-Anmerkungen zum Reduzieren von C/C++-Code Fehlern](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Grundlegendes zur SAL](../code-quality/understanding-sal.md)   
 [Kommentieren von Funktionsparametern und Rückgabe Werten](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Hinzufügen einer Anmerkung zum Funktionsverhalten](../code-quality/annotating-function-behavior.md)   
 [Hinzufügen einer Anmerkung zu Strukturen und Klassen](../code-quality/annotating-structs-and-classes.md)   
 [Angeben, wann und wo eine Anmerkung angewendet wird](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Intrinsische Funktionen](../code-quality/intrinsic-functions.md)   
 [Bewährte Methoden und Beispiele](../code-quality/best-practices-and-examples-sal.md)   
 [Blog des Code Analyseteams](https://blogs.msdn.com/b/codeanalysis/)
