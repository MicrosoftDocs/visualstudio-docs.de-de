---
title: Suchen in Dateien
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.findreplace.findinfiles
- vs.findinfiles
helpviewer_keywords:
- objects [Visual Studio], finding
- text searches, replacing text
- objects [Visual Studio], searching for
- Find and Replace window, Find in Files tab
- text searches, Find and Replace window
- documents, searching
- files, searching
- Find in Files tab, Find and Replace window
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1a32720475bda124c563d45133028f43b4f1b9cd
ms.sourcegitcommit: e132a870ec198fdcec289227f1a0c1c48fef070c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2020
ms.locfileid: "93344506"
---
# <a name="find-in-files"></a>In Dateien suchen

Mit der Option **Suchen in Dateien** können Sie einen bestimmten Satz Dateien durchsuchen. Die gefundenen Übereinstimmungen und ausgeführten Aktionen werden im Fenster **Suchergebnisse** angezeigt, das unter **Ergebnisoptionen** ausgewählt wurde.

Rufen Sie die Option **Suchen in Dateien** im Fenster **Suchen und Ersetzen** mithilfe einer der folgenden Methoden auf.

## <a name="to-display-find-in-files"></a>So rufen Sie die Option "In Dateien suchen" auf

1. Klicken Sie in der Menüleiste auf **Bearbeiten** > **Suchen und Ersetzen**.

1. Wählen Sie die Option **Suchen in Dateien** aus.

Drücken Sie zum Abbrechen eines Suchvorgangs **STRG** + **UNTBR**.

> [!NOTE]
> Das Tool zum Suchen und Ersetzen durchsucht keine Verzeichnisse mit dem `Hidden`- oder `System`-Attribut.

## <a name="find-what"></a>Suchen nach

Um eine neue Zeichenfolge oder einen neuen Ausdruck zu suchen, geben Sie die Zeichenfolge oder den Ausdruck im Feld ein. Öffnen Sie die Dropdownliste, und wählen Sie die Zeichenfolge aus, um nach einer der 20 Zeichenfolgen zu suchen, nach denen Sie zuletzt gesucht haben. Wählen Sie die benachbarte Schaltfläche **Ausdrucks-Generator** aus, wenn Sie einen oder mehrere reguläre Ausdrücke in der Suchzeichenfolge verwenden möchten. Weitere Informationen finden Sie unter [Verwenden von regulären Ausdrücken in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

> [!NOTE]
> Die Schaltfläche **Ausdrucks-Generator** wird nur aktiviert, wenn Sie in den **Suchoptionen****Reguläre Ausdrücke verwenden** ausgewählt haben.

## <a name="look-in"></a>Suchen in

Über die aus der Dropdownliste **Suchen in** ausgewählte Option legen Sie fest, ob die Funktion **In Dateien suchen** nur in den zurzeit aktiven Dateien oder in allen in bestimmten Ordnern gespeicherten Dateien sucht. Wählen Sie einen Suchbereich aus der Liste aus, oder klicken Sie auf die Schaltfläche **Durchsuchen (...)** , um das Dialogfeld **Suchordner auswählen** aufzurufen und Ihre eigene Gruppe von Verzeichnissen anzugeben. Sie können auch direkt im Feld **Suchen in** einen Pfad eingeben.

> [!WARNING]
> Mit den Optionen **Gesamte Projektmappe** oder **Aktuelles Projekt** werden Projekt- und Projektmappendateien nicht durchsucht. Wenn Sie die Projektdateien durchsuchen möchten, wählen Sie einen Suchordner aus.

> [!NOTE]
> Wenn Sie mit der Option **Suchen in** eine Datei durchsuchen, die Sie aus der Quellcodeverwaltung ausgecheckt haben, wird nur eine Version der Datei durchsucht, die Sie auf den lokalen Computer heruntergeladen haben.

## <a name="include-subfolders"></a>Unterordner einbeziehen

Gibt an, dass auch die Unterordner des im Feld **Suchen in** angegebenen Ordners durchsucht werden.

## <a name="find-options"></a>Suchoptionen

Der Bereich **Suchoptionen** kann erweitert oder reduziert werden. Die folgenden Optionen können aktiviert oder deaktiviert werden:

**Groß-/Kleinschreibung beachten**

Wenn diese Option ausgewählt ist, wird im Fenster **Suchergebnisse** zwischen Groß- und Kleinschreibung unterschieden.

**Nur ganzes Wort suchen**

Wenn diese Option ausgewählt ist, werden im Fenster **Suchergebnisse** nur Übereinstimmungen zurückgegeben, bei denen die gefundene Wortfolge vollständig mit der Suchzeichenfolge übereinstimmt.

**Verwenden von regulären Ausdrücken**

Wenn dieses Kontrollkästchen aktiviert ist, können Sie spezielle Notationen zur Definition von Textmustern verwenden, die mit den Textfeldern **Suchen nach** oder **Ersetzen durch** übereinstimmen. Eine Liste dieser Notationen finden Sie unter [Verwenden von regulären Ausdrücken in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

**Nach diesen Dateitypen suchen**

Diese Liste gibt Dateitypen an, die in den unter **Suchen in** angegebenen Verzeichnissen durchsucht werden sollen. Wenn dieses Feld leer ist, werden alle Dateien in den Verzeichnissen unter **Suchen in** durchsucht.

Wählen Sie ein beliebiges Element aus der Liste aus, um eine vordefinierte Suchzeichenfolge zu übernehmen, mit der nur Dateien des angegebenen Typs durchsucht werden.

## <a name="result-options"></a>Ergebnisoptionen

Der Bereich **Ergebnisoptionen** kann erweitert oder reduziert werden. Die folgenden Optionen können aktiviert oder deaktiviert werden:

**Fenster „Suchergebnisse: 1“**

Wenn diese Option ausgewählt ist, ersetzen die Ergebnisse der aktuellen Suche den Inhalt des Fensters **Suchergebnisse: 1**. Dieses Fenster wird automatisch geöffnet, um die Suchergebnisse anzuzeigen. Um dieses Fenster manuell zu öffnen, wählen Sie im Menü **Ansicht** die Option **Weitere Fenster** und anschließend **Suchergebnisse: 1** aus.

**Fenster „Suchergebnisse: 2“**

Wenn diese Option ausgewählt ist, ersetzen die Ergebnisse der aktuellen Suche den Inhalt des Fensters **Suchergebnisse: 2**. Dieses Fenster wird automatisch geöffnet, um die Suchergebnisse anzuzeigen. Um dieses Fenster manuell zu öffnen, wählen Sie im Menü **Ansicht** die Option **Weitere Fenster** und anschließend **Suchergebnisse: 2** aus.

**Nur Dateinamen anzeigen**

Zeigt eine Liste mit Dateien an, in denen die gefundenen Übereinstimmungen enthalten sind, und nicht die Übereinstimmungen selbst.

**Ergebnisse anfügen**

Fügt die Ergebnisse der Suche den Ergebnissen der vorherigen Suche hinzu.

## <a name="see-also"></a>Weitere Informationen

- [Suchen und Ersetzen von Text](../ide/finding-and-replacing-text.md)
- [In Dateien ersetzen](../ide/replace-in-files.md)
- [Visual Studio-Befehle](../ide/reference/visual-studio-commands.md)