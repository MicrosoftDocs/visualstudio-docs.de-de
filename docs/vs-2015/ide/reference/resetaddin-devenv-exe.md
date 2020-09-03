---
title: -ResetAddin (devenv.exe) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- disable addin
- addin state
- reset addin
ms.assetid: 9e339c8d-d768-4d86-8f45-2f479fc8255b
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9958e6e9a540dce1a405df8991780600b8f4a702
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665598"
---
# <a name="resetaddin-devenvexe"></a>/ResetAddin (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Entfernt Befehle und die Befehlsbenutzeroberfläche, die dem angegebenen Add-In zugeordnet sind.

## <a name="syntax"></a>Syntax

```
Devenv /ResetAddin AddIn
```

## <a name="arguments"></a>Argumente
 `AddIn` ist optional. Der Befehlsname des Add-Ins.

## <a name="remarks"></a>Bemerkungen
 Standardmäßig ist der Befehls Name des Add-ins gleich *\<AddInSolutionName>* . Verbinden<em>Sie \<AddInSolutionName> .</em>, und wird in Connect.cs als- `commandName` Parameter der- `Exec` Methode angezeigt. Sie können den Befehlsnamen auch überprüfen, indem Sie den Namen des Add-Ins im Befehlsfenster von Visual Studio eingeben und die Eingabe von IntelliSense vervollständigen lassen.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird Visual Studio gestartet. Die Ausführung des Add-Ins `MyAddin` beim Starten wird verhindert.

```
Devenv.exe /ResetAddin MyAddin.Connect.MyAddin
```

## <a name="see-also"></a>Weitere Informationen
 [Anpassen von Entwicklungseinstellungen in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3) [devenv-Befehls zeilenschaltern](../../ide/reference/devenv-command-line-switches.md)
