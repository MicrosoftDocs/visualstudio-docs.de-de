---
title: Festlegen von Präinstrumentations- und Postinstrumentationsbefehlen | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie Sie Befehle angeben können, die ausgeführt werden, bevor oder nachdem die Binärdateien in einer Leistungssitzung instrumentiert werden.
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.property.instrument
helpviewer_keywords:
- profiling tools, pre-instrument events
- events [Visual Studio], pre-instrument
- pre-instrument events, performance tools
ms.assetid: 6a8d5340-1d1b-4d81-88dd-8e1f435eb828
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 172ca7a478dcc34443d2edf15186d9c040a04837
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2021
ms.locfileid: "98721891"
---
# <a name="how-to-specify-pre--and-post-instrument-commands"></a>Vorgehensweise: Festlegen von Präinstrumentations- und Postinstrumentationsbefehlen

Sie können Befehle angeben, die ausgeführt werden, bevor oder nachdem die Binärdateien in einer Leistungssitzung instrumentiert werden. Jeder Befehl, der über die Befehlszeile ausgegeben werden kann, kann als Präinstrumentations- oder Postinstrumentationsereignis angegeben werden. Beispielsweise können Sie Befehle angeben, die das erneute Signieren einer Assembly mit einem Schlüssel mit starkem Namen in einer Batchdatei automatisiert, die ausgeführt wird, nachdem die Binärdateien instrumentiert werden.

Sie können Befehle für alle instrumentierten Binärdateien in der Profilerstellung oder für einzelne Binärdateien angeben. Sie können jedoch nur jeweils ein Präinstrumentationsbefehl vor dem Ausführen und nur ein Postinstrumentationsbefehl zum Ausführen nach dem Instrumentationsprozess angeben. Sie können keine Befehle für jeweils alle und für einzelne Binärdateien angeben. Wenn Sie Befehle für alle Binärdateien angeben, werden die Befehle vor oder nach der Instrumentation jeder Binärdatei in der Sitzung ausgeführt.

Das Arbeitsverzeichnis, in dem die Befehle ausgeführt werden, hängt vom Betriebssystem ab, auf dem Sie [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] ausführen und von der Zielplattform der Anwendung, für die ein Profil erstellt wird.

Informationen zum Abrufen des Pfads zu den Profilerstellungstools finden Sie unter [Angeben des Pfads zu Befehlszeilentools](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).

## <a name="to-specify-pre-instrument-commands"></a>So geben Sie Präinstrumentationsbefehle an

1. Führen Sie einen der folgenden Schritte aus:

    - Zum Angeben von Präinstrumentationsbefehle für alle Binärdateien in einer Leistungssitzung wählen Sie den Knoten Leistungssitzung im **Leistungs-Explorer**, klicken Sie anschließend mit der rechten Maustaste und wählen Sie **Eigenschaften** aus.

    - Zum Angeben von Präinstrumentationsbefehlen für eine bestimmte Binärdatei klicken Sie mit der rechten Maustaste auf die Binärdatei in der Liste **Ziele** der Leistungssitzung und wählen Sie anschließend **Eigenschaften** aus.

2. Klicken Sie auf den **Eigenschaftenseiten** auf **Instrumentation** .

3. Geben Sie den Befehl im Textfeld **Befehlszeile** unter **Präinstrumentationsereignisse** ein.

    > [!NOTE]
    > Sie können auf die Auslassungszeichen **(…)** klicken, die neben dem Feld **Befehlszeile** stehen, um die entsprechende EXE-, CMD- oder BAT-Datei zu suchen und auszuwählen.

4. Klicken Sie auf **OK**.

     Um den Befehl zu deaktivieren, ohne ihn zu entfernen, wählen Sie das Kontrollkästchen **Aus Instrumentation ausschließen** aus. Verwenden Sie zum Ändern der Compiler- oder Linkereinstellungen die Eigenschaftenseiten des Projekts.

## <a name="to-specify-post-instrument-commands"></a>So geben Sie Postinstrumentationsbefehle an

1. Führen Sie einen der folgenden Schritte aus:

    - Zum Angeben von Postinstrumentationsbefehlen für alle Binärdateien in einer Leistungssitzung wählen Sie den Knoten Leistungssitzung im **Leistungs-Explorer**, klicken Sie anschließend mit der rechten Maustaste und wählen Sie **Eigenschaften** aus.

    - Zum Angeben von Präinstrumentationsbefehlen für eine bestimmte Binärdatei klicken Sie mit der rechten Maustaste auf die Binärdatei in der Liste **Ziele** der Leistungssitzung und wählen Sie anschließend **Eigenschaften** aus.

2. Klicken Sie auf den **Eigenschaftenseiten** auf **Instrumentation** .

3. Geben Sie den Befehl im Textfeld **Befehlszeile** unter **Postinstrumentationsereignisse** ein.

    > [!NOTE]
    > Sie können auf die Auslassungszeichen **(…)** klicken, die neben dem Feld **Befehlszeile** stehen, um die entsprechende EXE-, CMD- oder BAT-Datei zu suchen und auszuwählen.

4. Klicken Sie auf **OK**.

     Um den Befehl zu deaktivieren, ohne ihn zu entfernen, wählen Sie das Kontrollkästchen **Aus Instrumentation ausschließen** aus. Verwenden Sie zum Ändern der Compiler- oder Linkereinstellungen die Eigenschaftenseiten des Projekts.

## <a name="see-also"></a>Siehe auch

[Konfigurieren von Leistungssitzungen](../profiling/configuring-performance-sessions.md)
