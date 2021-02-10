---
title: Arbeiten mit C++-Code (Klassen-Designer)
description: Lernen Sie, mit Klassendiagrammen C++-Codeelemente, Klassen und andere Typen in einem Projekt zu entwerfen und zu visualisieren.
ms.custom: SEO-VS-2020
ms.date: 06/21/2017
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.cpplimitation
helpviewer_keywords:
- C++, Class Designer
- Class Designer, C++ support
- Class Designer, limitations
- Class Designer, tasks in C++
- C++, class diagrams
- C++, class diagrams
- C++, Class Designer
ms.assetid: f5b40921-2ef7-4de0-b595-45b44c79ffa6
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: 62993611ef7359095512f494767bbd3ea4cce5d9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946578"
---
# <a name="work-with-c-code-in-class-designer"></a>Arbeiten mit C++-Code im Klassen-Designer

Der **Klassen-Designer** enthält eine visuelle Entwurfsoberfläche, ein sogenanntes *Klassendiagramm*, die die Codeelemente in Ihrem Projekt visuell darstellt. Sie können mit Klassendiagrammen Klassen und andere Typen in einem Projekt entwerfen und visualisieren.

Der **Klassen-Designer** unterstützt folgende C++-Codeelemente:

- Klasse (ähnlich eine verwalteten Klassenform, außer dass sie mehrere Vererbungsbeziehungen haben kann)

- Anonyme Klasse (zeigt den von der Klassenansicht generierten Namen für den anonymen Typ an)

- Vorlagenklasse

- Struktur

- Enum

- Makro (zeigt die Ansicht des Makros nach der Verarbeitung an)

- TypeDef

> [!NOTE]
> Dies ist nicht identisch mit dem UML-Klassendiagramm, das Sie in einem Modellierungsprojekt erstellt können. Weitere Informationen finden Sie unter [UML-Klassendiagramme: Referenz](../../modeling/what-s-new-for-design-in-visual-studio.md).

## <a name="troubleshoot-type-resolution-and-display-issues"></a>Behandlung von Anzeigeproblemen und Problemen bei der Typauflösung

### <a name="location-of-source-files"></a>Speicherort der Quelldateien

Der **Klassen-Designer** merkt sich den Speicherort der Quelldateien nicht. Wenn Sie die Projektstruktur ändern oder Quelldateien im Projekt verschieben, kann der **Klassen-Designer** daher den Typ verlieren (insbesondere den Quelltyp einer TypeDef, von Basisklassen oder von Zuordnungstypen). Es wird möglicherweise ein Fehler angezeigt, z.B. **Dieser Typ kann im Klassen-Designer nicht angezeigt werden**. In diesem Fall ziehen Sie den geänderten oder verschobenen Quellcode in das Klassendiagramm, um ihn erneut anzuzeigen.

### <a name="update-and-performance-issues"></a>Update- und Leistungsprobleme

Bei C++-Projekten kann es zwischen 30 und 60 Sekunden dauern, bis eine Änderung in der Quelldatei im Klassendiagramm angezeigt wird. Diese Verzögerung kann auch dazu führen, dass der **Klassen-Designer** den Fehler **In der Auswahl wurden keine Typen gefunden** auslöst. Wenn Sie einen solchen Fehler erhalten, klicken Sie in der Fehlermeldung auf **Abbrechen**, und warten Sie darauf, dass das Codeelement in der **Klassenansicht** angezeigt wird. Danach sollte der **Klassen-Designer** den Typ anzeigen können.

Wenn ein Klassendiagramm nicht mit den Änderungen aktualisiert wird, die Sie im Code vorgenommen haben, müssen Sie möglicherweise das Diagramm schließen und erneut öffnen.

### <a name="type-resolution-issues"></a>Probleme bei der Typauflösung

Der **Klassen-Designer** kann Typen aus folgenden Gründen möglicherweise nicht auflösen:

- Der Typ ist in einem Projekt oder einer Assembly, auf das/die nicht aus dem Projekt mit dem Klassendiagramm verwiesen wird. Um diesen Fehler zu beheben, fügen Sie einen Verweis auf das Projekt oder die Assembly mit dem Typ hinzu. Weitere Informationen finden Sie unter [Verwalten von Verweisen in einem Projekt](../managing-references-in-a-project.md).

- Der Typ befindet sich nicht im richtigen Bereich, sodass der **Klassen-Designer** ihn nicht finden kann. Stellen Sie sicher, dass dem Code nicht eine Anweisung `using`, `imports`, oder `#include` fehlt. Stellen Sie außerdem sicher, dass Sie den Typ (oder einen zugehörigen Typ) nicht aus dem Namespace verschoben haben, in dem er sich ursprünglich befand.

- Der Typ ist nicht vorhanden (oder wurde auskommentiert). Stellen Sie zum Beheben dieses Fehlers sicher, dass Sie den Typ nicht gelöscht oder auskommentiert haben.

- Der Typ befindet sich in einer Bibliothek, auf die mit einer #import-Direktive verwiesen wird. Eine mögliche Problemumgehung besteht darin, den generierten Code (die TLH-Datei) manuell zu einer #include-Anweisung in der Headerdatei hinzufügen.

- Stellen Sie sicher, dass der **Klassen-Designer** den von Ihnen eingegebenen Typ unterstützt. Siehe [Einschränkungen für C++-Codeelemente](#limitations-for-c-code-elements).

Der Fehler, der am ehesten für eine Typauflösung angezeigt wird, ist **Für mindestens eine Form im Klassendiagramm „\<element>“ wurde kein Code gefunden**. Diese Fehlermeldung besagt nicht notwendigerweise, dass der Code fehlerhaft ist. Es gibt nur an, dass Klassen-Designer den Code nicht anzeigen kann. Versuchen Sie folgende Maßnahmen:

- Stellen Sie sicher, dass der Typ vorhanden ist. Stellen Sie sicher, dass Sie den Quellcode nicht versehentlich auskommentiert oder gelöscht haben.

- Versuchen Sie, den Typ aufzulösen. Der Typ befindet sich möglicherweise in einem Projekt oder einer Assembly, auf das/die nicht aus dem Projekt mit dem Klassendiagramm verwiesen wird. Um diesen Fehler zu beheben, fügen Sie einen Verweis auf das Projekt oder die Assembly mit dem Typ hinzu. Weitere Informationen finden Sie unter [Verwalten von Verweisen in einem Projekt](../managing-references-in-a-project.md).

- Stellen Sie sicher, dass sich der Typ im richtigen Bereich befindet, sodass Klassen-Designer ihn finden kann. Stellen Sie sicher, dass dem Code nicht eine Anweisung `using`, `imports`, oder `#include` fehlt. Stellen Sie außerdem sicher, dass Sie den Typ (oder einen zugehörigen Typ) nicht aus dem Namespace verschoben haben, in dem er sich ursprünglich befand.

### <a name="troubleshoot-other-error-messages"></a>Problembehandlung bei anderen Fehlermeldungen

Hilfe bei der Problembehandlung für Fehler und Warnungen finden Sie in den öffentlichen Foren von MSDN (Microsoft Developer Network). Weitere Informationen finden Sie im [Forum des Visual Studio-Klassen-Designers](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsclassdesigner).

## <a name="limitations-for-c-code-elements"></a>Einschränkungen für C++-Codeelemente

- Wenn ein C++-Projekt geladen ist, befindet sich der **Klassen-Designer** in einem schreibgeschützten Modus. Sie können das Klassendiagramm ändern, aber keine Änderungen am Klassendiagramm im Quellcode speichern.

- Der **Klassen-Designer** unterstützt nur die native C++-Semantik. Bei C++-Projekten, die in verwalteten Code kompiliert werden, visualisiert der **Klassen-Designer** nur Codeelemente, bei denen es sich um native Typen handelt. Daher können Sie zwar ein Klassendiagramm zu einem Projekt hinzufügen, aber der **Klassen-Designer** visualisiert keine Elemente, in denen die `IsManaged`-Eigenschaft auf `true` festgelegt ist (d.h. Werttypen und Referenztypen).

- Bei C++-Projekten liest der **Klassen-Designer** nur die Definition des Typs. Nehmen wir beispielsweise an, dass Sie einen Typ in einer Headerdatei (. h) und dessen Member in einer Implementierungsdatei (.cpp) definieren. Wenn Sie „Klassendiagramm anzeigen“ für die Implementierungsdatei (.cpp) aufrufen, zeigt der **Klassen-Designer** nichts an. Ein weiteres Beispiel: Wenn Sie „Klassendiagramm anzeigen“ für eine CPP-Datei aufrufen, die eine `#include`-Anweisung zum Einschließen anderer Dateien verwendet, aber keine eigentlichen Klassendefinitionen enthält, zeigt der **Klassen-Designer** erneut nichts an.

- IDL-Dateien (.idl), die COM-Schnittstellen und Typbibliotheken definieren, werden in Diagrammen nicht angezeigt, sofern sie nicht in systemeigenen C++-Code kompiliert werden.

- Der **Klassen-Designer** unterstützt keine globale Funktionen und Variablen.

- Der **Klassen-Designer** unterstützt keine Unions. Dies ist eine besondere Art von Klasse, bei der der zugeordnete Arbeitsspeicher nur so groß wie der größte Datenmember der Union ist.

- Der **Klassen-Designer** zeigt keine grundlegenden Datentypen wie `int` und `char` an.

- Der **Klassen-Designer** zeigt keine Typen an, die außerhalb des aktuellen Projekts definiert sind, wenn das Projekt keinen richtigen Verweise auf diese Typen besitzt.

- Der **Klassen-Designer** kann geschachtelte Typen anzeigen, jedoch keine Beziehungen zwischen einem geschachtelten Typ und anderen Typen.

- Der **Klassen-Designer** kann keine Typen anzeigen, die „void“ sind oder von einem void-Typ abgeleitet sind.

## <a name="see-also"></a>Weitere Informationen

- [Entwerfen und Anzeigen von Klassen und Typen](designing-and-viewing-classes-and-types.md)
- [Zusätzliche Informationen zu Klassen-Designer-Fehlern](additional-information-about-errors.md)
- [C++Klassen in Klassen-Designer](visual-cpp-classes.md)
- [C++-Strukturen im Klassen-Designer](visual-cpp-structures.md)
- [C++-Enumerationen im Klassen-Designer](visual-cpp-enumerations.md)
- [C++-TypeDefs im Klassen-Designer](visual-cpp-typedefs.md)
