---
title: Anzeigen von Dateien mit dem Befehl "Datei öffnen" | Microsoft-Dokumentation
description: Erfahren Sie, wie die integrierte Entwicklungsumgebung (IDE) von Visual Studio den Befehl "Datei öffnen" im Menü Datei zum Anzeigen von Dateien verarbeitet.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open File command
- Open File command
- persistence, supporting Open File command
ms.assetid: 4fff0576-b2f3-4f17-9769-930f926f273c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 96f92aa921c7bb78511ed685d846e288518258fb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946825"
---
# <a name="display-files-by-using-the-open-file-command"></a>Anzeigen von Dateien mit dem Befehl "Datei öffnen"
In den folgenden Schritten wird beschrieben, wie die IDE den Befehl **Open File** behandelt, der im Menü **Datei** in verfügbar ist [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Die Schritte beschreiben auch, wie Projekte auf Aufrufe reagieren sollen, die aus diesem Befehl stammen.

 Wenn ein Benutzer im Menü **Datei** auf den Befehl **Datei öffnen** klickt und im Dialogfeld **Datei öffnen** eine Datei auswählt, erfolgt der folgende Vorgang:

1. Mithilfe der laufenden dokumententabelle bestimmt die IDE, ob die Datei bereits in einem Projekt geöffnet ist.

    - Wenn die Datei geöffnet ist, wird das Fenster von der IDE neu angeordnet.

    - Wenn die Datei nicht geöffnet ist, ruft die IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> auf, um jedes Projekt abzufragen, um zu bestimmen, welches Projekt die Datei öffnen kann.

        > [!NOTE]
        > Geben Sie in der Projekt Implementierung von <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> einen Prioritätswert an, der die Ebene angibt, auf der das Projekt die Datei öffnet. Prioritätswerte werden in der- <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> Enumeration bereitgestellt.

2. Jedes Projekt antwortet mit einer Prioritätsstufe, die angibt, wie wichtig es ist, dass das Projekt das Öffnen der Datei durchsetzt.

3. Die IDE verwendet die folgenden Kriterien, um zu bestimmen, welches Projekt die Datei öffnet:

    - Das Projekt, das mit der höchsten Priorität ( `DP_Intrinsic` ) antwortet, öffnet die Datei. Wenn mehr als ein Projekt mit dieser Priorität antwortet, wird die Datei vom ersten Projekt, das antwortet, geöffnet.

    - Wenn kein Projekt mit der höchsten Priorität ( `DP_Intrinsic` ) antwortet, aber alle Projekte mit der gleichen, niedrigeren Priorität Antworten, öffnet das aktive Projekt die Datei. Wenn kein Projekt aktiv ist, wird die Datei mit dem ersten Projekt, das antwortet, geöffnet.

    - Wenn kein Projekt den Besitz der Datei ( `DP_Unsupported` ) beansprucht, wird die Datei im Projekt "sonstige Dateien" geöffnet.

         Wenn eine Instanz des Projekts sonstige Dateien erstellt wird, antwortet das Projekt immer mit dem Wert `DP_CanAddAsExternal` . Dieser Wert gibt an, dass das Projekt die Datei öffnen kann. Dieses Projekt wird verwendet, um geöffnete Dateien zu beherbergen, die nicht in einem anderen Projekt vorhanden sind. Die Liste der Elemente in diesem Projekt wird nicht beibehalten. Dieses Projekt ist nur in **Projektmappen-Explorer** sichtbar, wenn es zum Öffnen einer Datei verwendet wird.

         Wenn das Projekt "sonstige Dateien" nicht anzeigt, dass es die Datei öffnen kann, wurde keine Instanz des Projekts erstellt. In diesem Fall erstellt die IDE eine Instanz des Projekts sonstige Dateien und weist das Projekt an, die Datei zu öffnen.

4. Sobald die IDE ermittelt, welches Projekt die Datei öffnet, ruft Sie die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> Methode für dieses Projekt auf.

5. Das Projekt hat dann die Möglichkeit, die Datei mit einem projektspezifischen Editor oder einem Standard-Editor zu öffnen. Weitere Informationen finden Sie unter Gewusst [wie: Öffnen von projektspezifischen Editoren](../../extensibility/how-to-open-project-specific-editors.md) und Gewusst [wie: Öffnen von Standard-Editoren](../../extensibility/how-to-open-standard-editors.md).

## <a name="see-also"></a>Weitere Informationen
- [Anzeigen von Dateien mit dem Befehl "Öffnen mit"](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)
- [Öffnen und Speichern von Projekt Elementen](../../extensibility/internals/opening-and-saving-project-items.md)
- [Gewusst wie: Öffnen von projektspezifischen Editoren](../../extensibility/how-to-open-project-specific-editors.md)
- [Vorgehensweise: Öffnen von Standard-Editoren](../../extensibility/how-to-open-standard-editors.md)
