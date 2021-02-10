---
title: Befehl "Shell"
description: Hier erfahren Sie mehr über den Shell-Befehl sowie darüber, wie damit ausführbare Programme aus Visual Studio heraus gestartet werden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- tools.shell
helpviewer_keywords:
- exe files
- Shell command
- Tools.Shell command
- executables, running from Visual Studio
- .exe files
- Shell, launching exe files
- Visual Studio, executables from
ms.assetid: 737fda23-b852-45c4-a9fe-41cbce6ba70f
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6b520d3bedf31bc09dc0cf48e86777872176e2e0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957620"
---
# <a name="shell-command"></a>Befehl "Shell"
Startet ausführbare Programme aus [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="syntax"></a>Syntax

```cmd
Tools.Shell [/command] [/output] [/dir:folder] path [args]
```

## <a name="arguments"></a>Argumente
`path`

Erforderlich. Der Pfad und Dateiname der auszuführenden Datei oder des zu öffnenden Dokuments. Wenn die angegebene Datei sich nicht in einem der Verzeichnisse in der Umgebungsvariable PATH befindet, ist der vollständige Pfad erforderlich.

`args`

Optional. Alle Argumente, die an das aufgerufene Programm übergeben werden sollen.

## <a name="switches"></a>Switches
/commandwindow [oder] /command [oder] /c [oder] /cmd

Optional. Gibt an, dass die Ausgabe für die ausführbare Datei im **Befehlsfenster** angezeigt werden soll.

/dir:`folder` [oder] /d: `folder`

Optional. Gibt das bei der Ausführung des Programms festzulegende Arbeitsverzeichnis an.

/outputwindow [oder] /output [oder] /out [oder] /o

Optional. Gibt an, dass die Ausgabe für die ausführbare Datei im Fenster **Ausgabe** angezeigt wird.

## <a name="remarks"></a>Bemerkungen
Die /dir-, /o- und /c-Schalter müssen unmittelbar nach `Tools.Shell` angegeben werden. Alles, was nach dem Namen der ausführbaren Datei angegeben wird, wird als Befehlszeilenargumente übergeben.

Der vordefinierte Alias `Shell` kann anstelle von `Tools.Shell` verwendet werden.

> [!CAUTION]
> Wenn im `path`-Argument der Verzeichnispfad und der Dateiname angegeben sind, sollten Sie den gesamten Pfadnamen wie im Folgenden dargestellt in literale Anführungszeichen (""") einschließen:

```cmd
Tools.Shell """C:\Program Files\SomeFile.exe"""
```

Jede aus drei doppelten Anführungszeichen bestehende Gruppe (""") wird vom `Shell`-Prozessor als einzelnes doppeltes Anführungszeichen interpretiert. Daher wird im vorherigen Beispiel tatsächlich die folgende Pfadzeichenfolge an den `Shell`-Befehl übergeben:

```cmd
"C:\Program Files\SomeFile.exe"
```

> [!CAUTION]
> Wenn Sie die Pfadzeichenfolge nicht in literale Anführungszeichen (""") einschließen, wird von Windows nur der Teil der Zeichenfolge bis zum ersten Leerzeichen verwendet. Wäre die oben aufgeführte Pfadzeichenfolge beispielsweise nicht ordnungsgemäß in Anführungszeichen eingeschlossen, würde Windows im Stammverzeichnis C:\ nach einer Datei mit dem Namen „Program“ suchen. Wenn tatsächlich eine ausführbare Datei „C:\Program.exe“ vorhanden wäre, die möglicherweise sogar widerrechtlich installiert wurde, würde Windows versuchen, dieses Programm anstelle des gewünschten Programms „C:\Programme\SomeFile.exe“ auszuführen.

## <a name="example"></a>Beispiel
Der folgende Befehl verwendet „xcopy.exe“, um die Datei `MyText.txt` in den Ordner `Text` zu kopieren. Die Ausgabe von „xcopy.exe“ wird im **Befehlsfenster** und im Fenster **Ausgabe** angezeigt.

```cmd
>Tools.Shell /o /c xcopy.exe c:\MyText.txt c:\Text\MyText.txt
```

## <a name="see-also"></a>Weitere Informationen

- [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
- [Befehlsfenster](../../ide/reference/command-window.md)
- [Ausgabefenster](../../ide/reference/output-window.md)
- [Feld „Suchen/Befehl“](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
