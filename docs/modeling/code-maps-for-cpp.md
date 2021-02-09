---
title: Siehe Abhängigkeiten zwischen C++-Quell-und Header Dateien
description: Stellt Informationen zu Code Maps für C++-Projekte bereit.
ms.date: 05/16/2018
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
ms.custom: SEO-VS-2020
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9c2aa1e49c0465fcf75917f0d9bd134962794c74
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861750"
---
# <a name="code-maps-for-c-projects"></a>Code Maps für C++-Projekte

Wenn Sie ausführlichere Code Maps für C++-Projekte erstellen möchten, aktivieren Sie für diese Projekte die Compileroption zum Durchsuchen von Informationen (**/FR**). Andernfalls werden Sie anhand einer Meldung aufgefordert, diese Option festzulegen. Bei Auswahl von **OK** wird die Option nur für die aktuelle Code Map festgelegt. Sie können angeben, dass die Meldung für alle späteren Code Maps ausgeblendet werden soll.

Wenn Sie eine Projektmappe öffnen, die Visual C++-Projekte enthält, könnte die Aktualisierung der IntelliSense-Datenbank etwas Zeit beanspruchen. Während dieser Zeit sind Sie möglicherweise nicht in der Lage, Code Maps für Header Dateien (*. h* oder) zu erstellen, `#include` bis die Aktualisierung der IntelliSense-Datenbank abgeschlossen ist. Sie können den Status der Aktualisierung in der Statusleiste von Visual Studio überwachen.

- Um Abhängigkeiten zwischen allen Quelldateien und Header Dateien in ihrer Projekt Mappe anzuzeigen, wählen Sie **Architektur**  >  **Diagramm für Includedateien generieren aus**.

   ![Abhängigkeitsdiagramm für nativen Code](../modeling/media/dependencygraphgeneral_nativecode.png)

- Um Abhängigkeiten zwischen den aktuell geöffneten Datei und zugehörige Quelldateien und Headerdateien anzuzeigen, öffnen Sie die Quelldatei oder die Header-Datei. Öffnen Sie das Kontextmenü "Datei" an einer beliebigen Stelle in der Datei. Wählen Sie **Diagramm für Includedateien generieren** aus.

   ![Abhängigkeitsdiagramm der ersten Ebene für H-Datei](../modeling/media/dependencygraph_native_firstlevel.png)

## <a name="troubleshoot-code-maps-for-c-and-c-code"></a>Problembehandlung bei Code Maps für C-und C++-Code

Diese Elemente werden für C- und C++-Code nicht unterstützt:

- Basistypen werden in Code Maps, die die übergeordnete Hierarchie enthalten, nicht angezeigt.

- Die meisten Elemente im Menü **Anzeigen** sind für C- und C++-Code nicht verfügbar.

Diese Probleme können auftreten, wenn Sie Code Maps für C-und C++-Code erstellen:

|**Problem**|**Mögliche Ursache**|**Auflösung**|
|-|-|-|
|Fehler beim Generieren der Code Map.|Kein Projekt in der Projektmappe wurde erfolgreich erstellt.|Korrigieren Sie die aufgetretenen Buildfehler, und generieren Sie dann die Code Map erneut.|
|Visual Studio reagiert nicht mehr, wenn Sie versuchen, eine Code Map über das Menü **Architektur** zu generieren.|Die Programmdatenbankdatei (.pdb) ist möglicherweise beschädigt.<br /><br /> In einer PDB-Datei werden Debuginformationen gespeichert, z. B. Typ, Methode und Quelldateiinformationen.|Erstellen Sie die Projektmappe neu, und versuchen Sie es dann erneut.|
|Bestimmte Einstellungen für die IntelliSense-Suchdatenbank sind deaktiviert.|Bestimmte IntelliSense-Einstellungen sind im Dialogfeld Visual Studio- **Optionen** möglicherweise deaktiviert.|Aktivieren Sie die Einstellungen, um sie verfügbar zu machen.<br /><br /> Weitere Informationen finden Sie unter [Optionen, Text-Editor, C/C++, erweitert](../ide/reference/options-text-editor-c-cpp-advanced.md).|
|Die Meldung **Unbekannte Methode** wird in einem Methodenknoten angezeigt.<br /><br /> Dieses Problem tritt auf, da der Name der Methode nicht aufgelöst werden kann.|Die Binärdatei weist möglicherweise keine Basisverschiebungstabelle auf.|Aktivieren Sie die Option **/FIXED:NO** im Linker.|
||Die Programmdatenbankdatei (.pdb) wird möglicherweise nicht erstellt.<br /><br /> In einer PDB-Datei werden Debuginformationen gespeichert, z. B. Typ, Methode und Quelldateiinformationen.|Aktivieren Sie die Option **/DEBUG** im Linker.|
||Die PDB-Datei kann an den erwarteten Speicherorten nicht geöffnet oder gefunden werden.|Stellen Sie sicher, dass die PDB-Datei an den erwarteten Speicherorten vorhanden ist.|
||Debuginformationen wurden aus der PDB-Datei entfernt.|Wenn die Option **/PDBSTRIPPED** im Linker verwendet wurde, schließen Sie stattdessen die vollständige PDB-Datei ein.|
||Der Aufrufer ist keine Funktion und ist entweder ein Thunk in der Binärdatei oder ein Zeiger im Datenabschnitt.|Wenn der Aufrufer ein Thunk ist, versuchen Sie, den Thunk mithilfe von `_declspec(dllimport)` zu vermeiden.|

## <a name="see-also"></a>Weitere Informationen

- [Zuordnen von Abhängigkeiten zu Code Maps](../modeling/map-dependencies-across-your-solutions.md)
