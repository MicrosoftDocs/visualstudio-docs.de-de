---
title: -Log („devenv.exe“)
description: Hier erfahren Sie, wie Sie mit der devenv-Befehlszeilenoption „Log“ alle Aktivitäten für die Problembehandlung in der Protokolldatei protokollieren.
ms.custom: SEO-VS-2020
ms.date: 12/12/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Log switch
- Log switch [devenv.exe]
- /Log Devenv switch
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e9dae594df60d75ced4ba6bdda5cb37c8c07a852
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040575"
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)

Protokolliert sämtliche Aktivitäten zur Problembehandlung in der Protokolldatei. Diese Datei wird angezeigt, nachdem Sie `devenv /log` mindestens einmal aufgerufen haben. Standardmäßig befindet sich die Protokolldatei an folgendem Speicherort:

**%APPDATA%\\Microsoft\\VisualStudio\\** \<Version\> **\\ActivityLog.xml**

Dabei ist \<Version\> die Visual Studio-Version. Sie können jedoch einen anderen Pfad und Dateinamen angeben.

## <a name="syntax"></a>Syntax

```shell
devenv /Log NameOfLogFile
```

## <a name="arguments"></a>Argumente

- *NameOfLogFile*

  Erforderlich. Der vollständige Pfad und Name der Protokolldatei, in die gespeichert werden soll.

## <a name="remarks"></a>Bemerkungen

Dieser Schalter muss am Ende der Befehlszeile nach allen anderen Schaltern angezeigt werden.

Das Protokoll wird nur für alle Instanzen von Visual Studio geschrieben, die Sie mit dem `/Log`-Schalter geöffnet haben.

## <a name="example"></a>Beispiel

In diesem Beispiel erfolgt die Protokollierung in der Datei `MyVSLog.xml` im Basisverzeichnis des Benutzers.

```shell
devenv /log "%USERPROFILE%\MyVSLog.xml"
```

## <a name="see-also"></a>Weitere Informationen

- [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)
