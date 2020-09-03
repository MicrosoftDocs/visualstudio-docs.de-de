---
title: Befehl „Befehlsfensterausgaben protokollieren“ | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- tools.logcommandwindowoutput
helpviewer_keywords:
- log Command window output command
- View.LogCommandWindowOutput command
ms.assetid: d4ecec35-5af4-4954-8d60-2cd24583fbb4
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d9a5a29cd63f9d51f86d41d2f0f5986a77666318
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72666868"
---
# <a name="log-command-window-output-command"></a>Befehl "Befehlsfensterausgaben protokollieren"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Kopiert die gesamte Ein- und Ausgabe aus dem **Befehlsfenster** in eine Datei.

## <a name="syntax"></a>Syntax

```
Tools.LogCommandWindowOutput [filename] [/on|/off] [/overwrite]
```

## <a name="arguments"></a>Argumente
 `filename` ist optional. Der Name der Protokolldatei. Standardmäßig wird die Datei im Profilordner des Benutzers erstellt. Wenn der Dateiname bereits vorhanden ist, wird „log“ dem Ende der vorhandenen Datei angefügt. Wenn keine Datei angegeben ist, wird die zuletzt angegebene Datei verwendet. Wenn noch keine Datei angegeben wurde, wird eine Standardprotokolldatei mit dem Namen „cmdline.log“ erstellt.

> [!TIP]
> Geben Sie den vollständigen Dateipfad in Anführungszeichen an, wenn der Pfad Leerzeichen enthält, um den Speicherort der Protokolldatei zu ändern.

## <a name="switches"></a>Schalter
 /on optional. Startet das Protokoll für das **Befehlsfenster** in der angegebenen Datei und hängt die Datei mit den neuen Informationen an.

 /off – ist optional. Stoppt das Protokoll für das **Befehlsfenster**.

 /overwrite optional. Wenn die angegebene Datei im `filename`-Argument mit einer vorhandenen Datei übereinstimmt, wird die Datei überschrieben.

## <a name="remarks"></a>Bemerkungen
 Wenn noch keine Datei angegeben ist, wird standardmäßig die Datei „cmdline.log“ erstellt. Der Alias dieses Befehls lautet standardmäßig „Log“.

## <a name="examples"></a>Beispiele
 In diesem Beispiel wird eine neue Protokolldatei („cmdlog“) erstellt, und das Befehlsprotokoll wird gestartet.

```
>Tools.LogCommandWindowOutput cmdlog
```

 In diesem Beispiel werden Protokollierungsbefehle angehalten.

```
>Tools.LogCommandWindowOutput /off
```

 In diesem Beispiel wird das Protokollieren von Befehlen in der vormals verwendeten Protokolldatei wieder aufgenommen.

```
>Tools.LogCommandWindowOutput /on
```

## <a name="see-also"></a>Weitere Informationen
 [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md) [Befehlsfenster](../../ide/reference/command-window.md) [Suchen/Befehlsfeld](../../ide/find-command-box.md) [Visual Studio-Befehls Aliase](../../ide/reference/visual-studio-command-aliases.md)
