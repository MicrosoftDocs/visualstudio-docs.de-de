---
title: Anpassen einer domänenspezifischen Sprache
description: Erfahren Sie, wie Sie benutzerdefinierten Code verwenden, um auf ein Modell in einer domänenspezifischen Sprache (DSL) zuzugreifen, Sie zu ändern oder ein Modell zu erstellen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3363857d9a953b61e18eb4b0cb891b20dbed1eb5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923958"
---
# <a name="write-code-to-customize-a-domain-specific-language"></a>Schreiben von Code zum Anpassen einer domänenspezifischen Sprache

In diesem Abschnitt wird gezeigt, wie Sie benutzerdefinierten Code verwenden, um auf eine domänenspezifische Sprache zuzugreifen, Sie zu ändern oder ein Modell zu erstellen.

Es gibt mehrere Kontexte, in denen Sie Code schreiben können, der mit einer DSL funktioniert:

- **Benutzerdefinierte Befehle.** Sie können einen Befehl erstellen, den Benutzer aufrufen können, indem Sie mit der rechten Maustaste auf das Diagramm klicken und das Modell ändern. Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen eines Befehls zum Kontextmenü](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).

- **Prüfung** Sie können Code schreiben, mit dem überprüft wird, ob sich das Modell in einem ordnungsgemäßen Zustand befindet. Weitere Informationen finden Sie unter [Validierung in einer Domain-Specific Sprache](../modeling/validation-in-a-domain-specific-language.md).

- **Überschreiben des Standard Verhaltens.** Sie können zahlreiche Aspekte des Codes ändern, der aus "DslDefinition. DSL" generiert wird. Weitere Informationen finden Sie unter Überschreiben [und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).

- **Text Transformation.** Sie können Textvorlagen schreiben, die Code enthalten, der auf ein Modell zugreift und eine Textdatei generiert, z. b. um Programmcode zu generieren. Weitere Informationen finden Sie unter [Erstellen von Code aus einer Domain-Specific Sprache](../modeling/generating-code-from-a-domain-specific-language.md).

- **Weitere Visual Studio-Erweiterungen.** Sie können separate VSIX-Erweiterungen schreiben, um Modelle zu lesen und zu ändern. Weitere Informationen finden Sie unter Gewusst [wie: Öffnen eines Modells aus einer Datei im Programm Code](../modeling/how-to-open-a-model-from-file-in-program-code.md) .

Instanzen der Klassen, die Sie in der Datei "DslDefinition. DSL" definieren, werden in einer Daten *Struktur gespeichert,* die als *in-Memory-Speicher ("in-Memory-Speicher* ", Die Klassen, die Sie in einer DSL definieren, nehmen immer einen Speicher als Argument für den Konstruktor an. Wenn Ihre DSL z. b. eine Klasse namens "example" definiert:

`Example element = new Example (theStore);`

das Beibehalten von Objekten im Speicher (anstelle der normalen Objekte) bietet mehrere Vorteile.

- **Transaktionen**: Sie können eine Reihe verwandter Änderungen in eine Transaktion gruppieren:

     `using (Transaction t = store.TransactionManager.BeginTransaction("updates"))`

     `{`

     `// make several changes to Store elements here`

     `t.Commit();`

     `}`

     Wenn während der Änderungen eine Ausnahme auftritt, sodass der endgültige Commit () nicht ausgeführt wird, wird der Speicher auf seinen vorherigen Zustand zurückgesetzt. Dadurch wird sichergestellt, dass Fehler nicht in einem inkonsistenten Zustand bleiben. Weitere Informationen finden Sie unter [navigieren und Aktualisieren eines Modells im Programm Code](../modeling/navigating-and-updating-a-model-in-program-code.md).

- **Binäre Beziehungen**. Wenn Sie eine Beziehung zwischen zwei Klassen definieren, haben Instanzen an beiden Enden eine Eigenschaft, die zum anderen Ende navigiert. Die beiden Enden sind immer synchronisiert. Wenn Sie z. b. eine Klammer Beziehung mit Rollen namens übergeordneten und untergeordneten Elementen definieren, können Sie Folgendes schreiben:

     `John.Children.Add(Mary)`

     Beide der folgenden Ausdrücke sind jetzt "true":

     `John.Children.Contains(Mary)`

     `Mary.Parents.Contains(John)`

     Sie können auch denselben Effekt erzielen, indem Sie Folgendes schreiben:

     `Mary.Parents.Add(John)`

     Weitere Informationen finden Sie unter [navigieren und Aktualisieren eines Modells im Programm Code](../modeling/navigating-and-updating-a-model-in-program-code.md).

- **Regeln und Ereignisse**. Sie können Regeln definieren, die immer dann ausgelöst werden, wenn bestimmte Änderungen vorgenommen werden. Regeln werden z. b. verwendet, um die Formen im Diagramm mit den Modellelementen auf dem neuesten Stand zu halten. Weitere Informationen finden Sie unter [reagieren auf und](../modeling/responding-to-and-propagating-changes.md)weitergeben von Änderungen.

- **Serialisierung:** Der Speicher bietet eine Standardmethode zum Serialisieren der darin enthaltenen Objekte in eine Datei. Sie können die Regeln für die Serialisierung und Deserialisierung anpassen. Weitere Informationen finden Sie unter [Anpassen von File Storage und XML-Serialisierung](../modeling/customizing-file-storage-and-xml-serialization.md).

## <a name="see-also"></a>Weitere Informationen

- [Anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md)