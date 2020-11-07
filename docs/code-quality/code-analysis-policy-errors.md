---
title: Code Analysis Policy Errors
ms.date: 11/04/2016
description: Erfahren Sie mehr über Fehler bei der Code Analyse Richtlinie in Visual Studio. Zeigt Beschreibungen von Fehlern an, die auftreten, wenn die Richtlinie beim Einchecken von Code nicht erfüllt wird.
ms.custom: SEO-VS-2020
ms.topic: reference
f1_keywords:
- vs.codeanalysis.policyfailures
helpviewer_keywords:
- policy errors, code analysis
ms.assetid: d1f221cd-68c0-4277-9397-b76ad0dbae77
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 43dae5ec9ca68c746b914ad0a75b792f2a6e6b43
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94349099"
---
# <a name="code-analysis-policy-errors"></a>Code Analysis Policy Errors

Die folgenden Fehler treten auf, wenn die Codeanalyserichtlinie beim Einchecken nicht erfüllt wird:

**Die Codeanalyseeinstellungen für mindestens ein Projekt sind mit der Codeanalyserichtlinie nicht kompatibel.**

Die Code Analyseanforderungen, die an die Projekt Quell Code Verwaltung einchecken, wurden für ein oder mehrere Code Projekte nicht erfüllt. Dieser Fehler kann durch eine oder mehrere der folgenden Bedingungen verursacht werden:

- Die Codeanalyse ist nicht für das Build für alle Projekte in der Projektmappe aktiviert.

- Der lokale Regelsatz für das Projekt in Visual Studio verfügt über eine weniger einschränkende **Aktions** Einstellung als der Projekt Regelsatz. eine Regel, die auf " **Aktions** = **Fehler** " auf dem Server festgelegt ist, ist für die **Aktion** " **Warning** " oder " **None** " in dem Regel Satz, der in Visual Studio ausgeführt wird, festgelegt.

- Der in Visual Studio angegebene Regelsatz enthält nicht alle Regeln, die im Regelsatz angegeben sind, der in der Eincheck Richtlinie für die Code Analyse für das Projekt angegeben ist.

**Die Code Analyse Richtlinie ist fehlgeschlagen. Es sind Fehler in Project vorhanden {0} , oder der Build ist nicht auf dem neuesten Stand.**

Der Build enthält entweder Fehler, oder die Fehler wurden korrigiert. Nach der Korrektur wurde jedoch keine Codeanalyse ausgeführt.

**Fehler beim Einchecken. Die Code Analyse Richtlinie erfordert, dass Sie Visual Studio mit einer geöffneten Projekt Mappe einchecken.**

Die Codeanalyserichtlinie setzt voraus, dass alle eingecheckten Dateien in der aktuell geöffneten Projektmappe enthalten sein müssen. Um diesen Fehler zu korrigieren, öffnen Sie die Projektmappe, in der die einzucheckende Datei enthalten ist.

**Nicht alle Dateien im ausstehenden Einchecken befinden sich in der gerade geöffneten Projektmappe.**

Die Codeanalyserichtlinie setzt voraus, dass alle eingecheckten Dateien in der aktuell geöffneten Projektmappe enthalten sein müssen. Dieser Fehler tritt auf, wenn eine Projektmappe geöffnet ist, aber einige Dateien in der Ansicht "Anstehende Eincheckvorgänge" nicht zur gerade geöffneten Projektmappe gehören. Um diesen Fehler zu korrigieren, öffnen Sie die Projektmappe, in der die einzucheckende Datei enthalten ist.

**Die Version von ' {0} ' ist nicht richtig. Der in der Richtlinie angegebene starke Name ist " {1} ".**

Dieser Fehler bezieht sich auf .NET-Projekte. Eine für die Codeanalyserichtlinie erforderliche Regel-DLL ist auf dem lokalen Computer vorhanden, aber die Version/der öffentliche Schlüssel stimmt nicht überein. Um diesen Fehler zu beheben, muss der Richtlinien Ersteller die DLLs im Verzeichnis " *c:\Programme\Microsoft Visual Studio 8 \ Team Tools\Static Analysis Tools\FxCop\Rules \\* " auf dem Computer aktualisieren.

**die {0} in der Richtlinie angegebene Assembly ist nicht vorhanden.**

Dieser Fehler bezieht sich auf .NET-Projekte. Für eine für die Codeanalyserichtlinie erforderliche Regel ist die entsprechende DLL nicht auf dem Clientcomputer installiert. Um diesen Fehler zu beheben, muss der Richtlinien Ersteller die dll im Verzeichnis " *c:\Programme\Microsoft Visual Studio 8 \ Team Tools\Static Analysis Tools\FxCop\Rules \\* " auf dem Computer aktualisieren.

**{0}Die Projekt Regel Einstellungen stimmen nicht mit der Code Analyse Richtlinie überein.**

Dieser Fehler bezieht sich auf .NET-Projekte. Die Regeleinstellungen des verwalteten Codes sind nicht so streng wie von der Richtlinie gefordert. Um diesen Fehler zu beheben, muss die Clienteinstellung mindestens so streng wie die Richtlinienanforderung auf dem Server sein.

**Die Code Analyse ist für die aktive Konfiguration nicht aktiviert. Wechseln Sie zu Konfiguration, {0} und erstellen Sie das Projekt, {1} bevor Sie einchecken.**

In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ist für die aktive Konfiguration keine Codeanalyse aktiviert, es ist jedoch mindestens eine Codeanalyse aktiviert.

**Sie müssen die Code Analyse für verwaltete Binärdateien in den Projekt {0} Eigenschaften und den Build vor dem Einchecken aktivieren.**

Dieser Fehler gilt für [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]-.NET-Anwendungen. Gemäß der Richtlinie muss eine verwaltete Codeanalyse ausgeführt werden, dies ist jedoch im aktuellen Projekt auf dem Client nicht aktiviert.

**Sie müssen die Code Analyse in den Projekt {0} Eigenschaften aktivieren und den Build vor dem Einchecken aktivieren.**

Dieser Fehler wurde auf [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Projekte und Webprojekte angewendet. Gemäß der Richtlinie muss eine verwaltete Codeanalyse ausgeführt werden, dies ist jedoch im aktuellen Projekt auf dem Client nicht aktiviert.

**Sie müssen die C/C++-Code Analyse in den Projekt {0} Eigenschaften und den Build vor dem Einchecken aktivieren.**

Dieser Fehler bezieht sich auf nicht verwaltete Projekte. Gemäß der Codeanalyserichtlinie ist eine Codeanalyse für C/C++ erforderlich, dies ist jedoch im aktuellen Projekt auf dem Client nicht aktiviert.

## <a name="see-also"></a>Weitere Informationen

- [Anwendungsfehler bei der Codeanalyse](../code-quality/code-analysis-application-errors.md)
