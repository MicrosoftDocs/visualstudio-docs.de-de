---
title: VSCT-Compiler Command-Line Flags | Microsoft-Dokumentation
description: Der Visual Studio-Befehls Tabellen Compiler bietet Befehlszeilenoptionen, um eine erfolgreiche Kompilierung von vsct-Dateien sicherzustellen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, compiling
- command-table file compilation (VSCT files)
ms.assetid: 9dc6c33f-e6cf-4cf2-9b05-e8f7bfac1cfb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 53e50e408166eb2d2e1545549cdd6c72018c9553
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99938784"
---
# <a name="vsct-compiler-command-line-flags"></a>VSCT-Compiler-Befehlszeilenflags
Der VSCT-Compiler (Visual Studio Command Table) stellt Befehls Zeilenschalter bereit, um eine erfolgreiche Kompilierung von vsct-Dateien sicherzustellen.

## <a name="command-line-parameters"></a>Befehlszeilenparameter
 Navigieren Sie zum Anzeigen der grundlegenden vsct-Hilfe in einem [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **Befehls** Fenster zum Ordner *Visual Studio SDK-Installationspfad*\visualstudiointegration\tools\bin\, und geben Sie Folgendes ein:

```
vsct /?
```

 Dadurch wird Folgendes zurückgegeben:

```
Microsoft (R) Visual Studio (R) Command Table Compiler Version 3.00.2000

Syntax: vsct <infile> [<outfile>] [-S[symbols file]] [-D<preprocessor-define>]*
[-I<include-path>]* [-L<language>] [-E[C|H|N]:<name>]

  -D    Specify any additional preprocessor defines
  -I    Indicate what additional include paths to send to the preprocessor
  -L    Specify the language to use when selecting strings
  -E    Emit C# objects in the specified namespace for command items,
        followed by [L|F|H|N]:<value>
        F = Name of the file to emit (used if -EL is provided)
        L = Name of a language providing a CodeDOM provider
        N = namespace (required if -EL is provided)
        H = C++ header
  -c    Clean build skipping dependency checks
  -v    Verbose output
```

> [!NOTE]
> Die Zeichen-(Bindestrich) und/(Schrägstrich) sind sowohl akzeptierte Notation zum Angeben von Befehlszeilen Parametern.

 Zulässige Flags und deren Bedeutung lauten wie folgt.

|Schalter|BESCHREIBUNG|
|------------|-----------------|
|-d|Geben Sie zusätzliche definierte Symbole an.|
|-I|Geben Sie die zusätzlichen Include-Pfade an, die beim Auflösen von Datei verweisen verwendet werden sollen.|
|-l|Geben Sie den <xref:System.Globalization.CultureInfo> Kultur Namen an, z. b. "en-US".|
|-E|Gibt c#-Objekte im angegebenen Namespace für Befehls Elemente aus, gefolgt von [C&#124;H&#124;N]:*filename* WHERE C = c#, H = C++ Header, N = Namespace. Der Namespace ist für c# erforderlich.|
|-v|Ausführliche Ausgabe.|

 Der Schalter-L weist den Compiler an, eine Gruppe von Zeichen folgen auszuwählen, um die binäre CTO-Datei zu entwickeln, die dem angegebenen <xref:System.Globalization.CultureInfo> Kultur Namen entspricht. Der angegebene Kultur Name sollte mit dem Language-Attribut eines oder mehrerer [String-Elemente](../../extensibility/strings-element.md) in der vsct-Datei identisch sein. Wenn ein Strings-Element über kein Language-Attribut verfügt, wird es vom enthaltenden [commandtable-Element](../../extensibility/commandtable-element.md)geerbt.

 Eine vsct-Datei kann mehrere Zeichen folgen Elemente enthalten, und jede kann ein anderes sprach Attribut aufweisen. Die Globalisierung wird erreicht, indem der VSCT-Compiler mehrmals ausgeführt und der Schalter "-L" für jeden Kultur Namen geändert wird.

 Wenn der vom Schalter-L angegebene Kultur Name nicht mit dem Language-Attribut eines beliebigen Strings-Elements identisch ist, versucht der Compiler, die Sprache und nicht die Region abzugleichen. Wenn z. b. "en-US" nicht gefunden werden kann, versucht der Compiler stattdessen "en". Wenn ein Fehler auftritt, wird die aktuelle Kultur des Betriebssystems ausprobiert. Wenn ein Fehler auftritt, wird das erste gefundene Zeichen folgen Element kompiliert.

 Der Schalter-E kann verwendet werden, um eine Header Datei im C-Stil auszugeben, die die Symbole enthält, die von der Befehls Tabelle verwendet werden, oder um eine c#-Datei auszugeben, die-Objekte für die Befehls Symbole enthält.

 Die Schalter-D und-I verfügen über die Syntax der Cl.exe C-präprozessorflags, die denselben Namen aufweisen. -D-Definitionen, die das Format X = Y aufweisen, werden für die Erweiterung von XML-basierten \<Defined> Tests in `Condition` Attributen verwendet. -I Include-Pfade werden verwendet \<Include> , um \<Extern> die \<Bitmap> Datei Verweise aufzulösen. Weitere Informationen finden Sie in der [vsct-XML-Schema Referenz](../../extensibility/vsct-xml-schema-reference.md).

 Der VSCT-Compiler kann auch eine zuvor erstellter Binärdatei dekompilieren. Stellen Sie hierzu eine Binärdatei für das bereit \<infile> .   Wenn die Binärdatei vom VSCT-Compiler erstellt wurde, werden die zugehörigen Symbole bereits eingebettet, und es wird eine Ausgabe mit den symbolischen Namen in einem \<Symbols> Abschnitt der Ausgabe erzeugt. Wenn die Binärdatei vom CTC-Compiler erstellt wurde, enthält die Ausgabe die tatsächlichen GUIDs und IDs. Wenn sich die von den aktuellen Versionen von Ctc.exe erstellte *. ctsym-Datei im selben Ordner wie die binäre Eingabedatei befindet, werden die Symbole aus dieser Datei geladen und für die Ausgabe verwendet.

## <a name="see-also"></a>Weitere Informationen
- [VSCT-Dateien (Visual Studio Command Table)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [VSCT-XML-Schemareferenz](../../extensibility/vsct-xml-schema-reference.md)
- [Hinzufügen von Benutzeroberflächenelementen mit VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
