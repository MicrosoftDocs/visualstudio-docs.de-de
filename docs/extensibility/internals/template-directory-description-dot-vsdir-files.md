---
title: Beschreibung des Vorlagen Verzeichnisses (. VSDIR-Dateien | Microsoft-Dokumentation
description: Erfahren Sie, wie eine Vorlagen Verzeichnis Beschreibungsdatei es der Visual Studio-IDE ermöglicht, Ordner, VSZ-Dateien und Vorlagen anzuzeigen, die dem Projekt zugeordnet sind.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .vsdir files
- VSDIR files
- template directory description files
ms.assetid: 9df51800-190e-4662-b685-fdaafcff1400
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0e2b56c061ce6e3124a7ed5a5dc00e41c3964204
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99898241"
---
# <a name="template-directory-description-vsdir-files"></a>Dateien zur Beschreibung des Vorlagenverzeichnisses (VSDIR)
Eine Vorlagen Verzeichnis Beschreibungsdatei (VSDIR) ist eine Textdatei, die es der integrierten Entwicklungsumgebung (IDE) ermöglicht, Ordner, Wizard. VSZ-Dateien und Vorlagen Dateien anzuzeigen, die dem Projekt in Dialogfeldern zugeordnet sind. Der Inhalt enthält einen Datensatz pro Datei oder Ordner. Alle VSDIR-Dateien an einem Speicherort, auf den verwiesen wird, werden zusammengeführt, obwohl im Allgemeinen nur eine VSDIR-Datei bereitgestellt wird, um mehrere Ordner, Assistenten oder Vorlagen Dateien zu beschreiben.

 Ordner (Unterverzeichnisse), Dateien, auf die in der VSDIR-Datei verwiesen wird, und die VSDIR-Datei selbst befinden sich alle im selben Verzeichnis. Wenn die IDE einen Assistenten ausführt oder einen Ordner oder eine Datei in den Dialogfeldern **Neues Projekt** oder **Neues Element hinzufügen** anzeigt, wird das Verzeichnis, in dem die ausgeführten Dateien enthalten sind, von der IDE überprüft, um zu bestimmen, ob eine VSDIR-Datei vorhanden ist. Wenn eine VSDIR-Datei gefunden wird, wird Sie von der IDE gelesen, um zu bestimmen, ob Sie einen Eintrag für den ausgeführten oder angezeigten Ordner bzw. die angezeigte Datei enthält. Wenn ein Eintrag gefunden wird, werden die Informationen von der IDE in der Ausführung des Assistenten oder in der Anzeige des Inhalts verwendet.

 Das folgende Codebeispiel wird aus der Datei "SourceFiles. vsdir" im \<EnvSDK> Registrierungsschlüssel "\bscprj\bscprj\bscprjprojectitems\ Source_Files" abgerufen:

```
HeaderFile.h|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#125|130|#126|0|0|0|#127
SourceFile.cpp|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#122|110|#123|0|0|0|#124
```

 In diesem Fall befinden sich zwei Datensätze in einer Datei. Die einzelnen Datensätze werden von einer neuen Zeile (Wagen Rücklauf Zeichen) getrennt. Jede Zeile stellt einen anderen Dateityp dar. Ein Pipe-Zeichen (&#124;) trennt Felder in jedem Datensatz. Ein einzelnes Verzeichnis kann mehrere VSDIR-Dateien mit unterschiedlichen Dateinamen enthalten, oder Sie können eine VSDIR-Datei für jeden Dateityp haben.

## <a name="fields"></a>Felder
 In der folgenden Tabelle sind die für die einzelnen Datensätze angegebenen Felder aufgeführt.

| Feld | BESCHREIBUNG |
| - | - |
| Relativer Pfadname (relpathname) | Der Name des Ordners, der Vorlage oder der VSZ-Datei, z. b. Headerfile. h oder MyWizard. VSZ. Dieses Feld kann auch ein Name sein, der zum Darstellen eines Ordners verwendet wird. |
| {clsidPackage} | Die GUID des VSPackage, das den Zugriff auf lokalisierte Zeichen folgen wie LocalizedName, Description, IconResourceID und Vorschlags Basis Name in den Satelliten-DLL-Ressourcen (Dynamic Link Library) des VSPackages ermöglicht. IconResourceID ist anwendbar, wenn DllPath nicht angegeben wird. **Hinweis:**  Dieses Feld ist optional, es sei denn, mindestens eines der vorherigen Felder ist ein Ressourcen Bezeichner. Dieses Feld ist in der Regel leer für VSDIR-Dateien, die den Drittanbieter-Assistenten entsprechen, die Ihren Text nicht lokalisieren. |
| LocalizedName | Der lokalisierte Name der Vorlagen Datei oder des Assistenten. Dieses Feld kann eine Zeichenfolge oder ein Ressourcen Bezeichner der Form "#Resid" sein. Dieser Name wird im Dialogfeld **Neues Element hinzufügen** angezeigt. **Hinweis:**  Wenn LocalizedName ein Ressourcen Bezeichner ist, ist {clsidPackage} erforderlich. |
| SortPriority | Eine ganze Zahl, die die relative Priorität dieser Vorlagen Datei oder des Assistenten darstellt. Wenn dieses Element z. b. den Wert 1 hat, wird dieses Element neben anderen Elementen mit dem Wert 1 und vor allen Elementen mit dem Sortier Wert 2 oder größer angezeigt.<br /><br /> Die Sortier Priorität ist relativ zu den Elementen im gleichen Verzeichnis. Es können mehrere VSDIR-Dateien im selben Verzeichnis vorhanden sein. In diesem Fall die Elemente aus allen <em>.</em> VSDIR-Dateien in diesem Verzeichnis werden zusammengeführt. Elemente mit gleicher Priorität werden in lexikografischer Reihenfolge des angezeigten Namens ohne Beachtung der Groß-/Kleinschreibung aufgelistet. Die- `_wcsicmp` Funktion wird verwendet, um die Elemente zu sortieren.<br /><br /> Elemente, die nicht in VSDIR-Dateien beschrieben werden, enthalten eine Prioritäts Nummer, die größer als die höchste Prioritäts Nummer ist, die in den VSDIR-Dateien Das Ergebnis ist, dass diese Elemente unabhängig von Ihrem Namen am Ende der angezeigten Liste angezeigt werden. |
| BESCHREIBUNG | Die lokalisierte Beschreibung der Vorlagen Datei oder des Assistenten. Dieses Feld kann eine Zeichenfolge oder ein Ressourcen Bezeichner der Form "#Resid" sein. Diese Zeichenfolge wird im Dialogfeld **Neues Projekt** oder **Neues Element hinzufügen** angezeigt, wenn das Element ausgewählt wird. |
| DLL-Pfad oder {CLSID-Paket} | Wird verwendet, um ein Symbol für die Vorlagen Datei oder den Assistenten zu laden. Das Symbol wird mithilfe von IconResourceID als Ressource aus einer DLL-oder exe-Datei geladen. Diese DLL-oder exe-Datei kann entweder mithilfe eines vollständigen Pfads oder mithilfe einer GUID eines VSPackages identifiziert werden. Die Implementierungs-DLL des VSPackage wird verwendet, um das Symbol (nicht die Satelliten-DLL) zu laden. |
| Symbolressourcenkennung | Der Ressourcen Bezeichner in der DLL-oder VSPackage-Implementierungs-DLL, der das anzuzeigende Symbol bestimmt. |
| Flags ( <xref:Microsoft.VisualStudio.Shell.Interop.__VSDIRFLAGS> ) | Dient zum Deaktivieren oder Aktivieren der Felder " **Name** " und " **Speicherort** " im Dialogfeld " **Neues Element hinzufügen** ". Der Wert des **Flags** -Felds ist das Dezimaltrennzeichen der Kombination von erforderlichen Bitflags.<br /><br /> Wenn ein Benutzer auf der Registerkarte **neu** ein Element auswählt, bestimmt das Projekt, ob das Feld Name und das Feld Speicherort angezeigt werden, wenn das Dialogfeld **Neues Element hinzufügen** zuerst angezeigt wird. Ein Element kann über eine VSDIR-Datei nur steuern, ob die Felder aktiviert oder deaktiviert sind, wenn das Element ausgewählt wird. |
| SuggestedBaseName | Stellt den Standardnamen für die Datei, den Assistenten oder die Vorlage dar. Dieses Feld ist entweder eine Zeichenfolge oder ein Ressourcen Bezeichner der Form "#Resid". Die IDE verwendet diesen Wert, um einen Standardnamen für das Element bereitzustellen. Diesem Basiswert wird ein ganzzahliger Wert angehängt, um den Namen eindeutig zu machen, z. b. MyFile21. ASP.<br /><br /> In der vorherigen Liste gelten die Beschreibungen, DllPath, IconResourceID, Flags und Vorschlags basenumber nur für Vorlagen-und Assistenten Dateien. Diese Felder gelten nicht für Ordner. Diese Tatsache wird im Code in der Datei bscprjprojectitems im \<EnvSDK> Registrierungsschlüssel \bscprj\bscprj\bscprjprojectitems veranschaulicht. Diese Datei enthält drei Datensätze (einen für jeden Ordner) mit vier Feldern für jeden Datensatz: relpathname, {clsidPackage}, LocalizedName und SortPriority.<br /><br /> `General&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#110&#124;100`<br /><br /> `Source_Files&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#111&#124;110`<br /><br /> `Env&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#112&#124;120` |

 Wenn Sie eine Assistenten Datei erstellen, sollten Sie auch die folgenden Probleme berücksichtigen.

- Ein optionales Feld, für das es keine sinnvollen Daten gibt, sollte als Platzhalter 0 (null) enthalten.

- Wenn kein lokalisierter Name angegeben ist, wird der relative Pfadname in der Assistenten Datei verwendet.

- DllPath überschreibt clsidPackage für Symbol Speicherort.

- Wenn kein Symbol definiert ist, ersetzt die IDE das Standard Symbol für eine Datei mit dieser Erweiterung.

- Wenn kein vorgeschlagene Basisname bereitgestellt wird, wird "Project" verwendet.

- Wenn Sie die VSZ-Dateien, Ordner oder Vorlagen Dateien löschen, müssen Sie auch die zugehörigen Datensätze aus der VSDIR-Datei entfernen.

## <a name="see-also"></a>Weitere Informationen
- [The](../../extensibility/internals/wizards.md)
- [Assistentendatei (VSZ)](../../extensibility/internals/wizard-dot-vsz-file.md)
