---
title: Quellserver-Sicherheitswarnung | Microsoft-Dokumentation
description: In diesem Artikel finden Sie Informationen zur Quellserver-Sicherheitswarnung im Visual Studio-Debugger. Achten Sie bei der Verwendung von Quellservern auf mögliche Sicherheitsbedrohungen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.sourceserver.enablewarning
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 8451c281-6914-469c-b80c-6271cc3f3d17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bf62abb91411048f46bfe7240074bd86c119bcd4
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2021
ms.locfileid: "98149117"
---
# <a name="source-server-security-alert"></a>Quellserver-Sicherheitswarnung
Verwenden Sie bei Verwendung von Source Server nur Symboldateien, die aus bekannten und vertrauenswürdigen Quellen stammen.

 Diese Warnung wird angezeigt, wenn Sie die Quellserverunterstützung aktivieren. Quellserverbefehle sind in Debugsymboldateien ( **\*.pdb**-Dateien) eingebettet. Stellen Sie sicher, dass Sie wissen, woher die PDB-Dateien stammen.

> [!IMPORTANT]
> Die folgenden potenziellen Sicherheitsrisiken müssen bei der Verwendung des Quellservers berücksichtigt werden: In der PDB-Datei der Anwendung können beliebige Befehle eingebettet sein. Deshalb sollten Sie sicherstellen, dass Sie der Datei „srcsrv.ini“ nur die Befehle hinzufügen, die ausführt werden dürfen. Beim Versuch, einen nicht in der Datei srcsvr.ini enthaltenen Befehl auszuführen, wird ein Bestätigungsdialogfeld geöffnet. Weitere Informationen finden Sie unter [Sicherheitswarnung: Der Debugger muss diesen nicht vertrauenswürdigen Befehl ausführen](../debugger/security-warning-debugger-must-execute-untrusted-command.md). Es wird keine Validierung für Befehlsparameter durchgeführt, seien Sie deshalb bei vertrauenswürdigen Befehlen vorsichtig. Beispielsweise kann bei Vertrauenswürdigkeit für den Befehl cmd.exe ein böswilliger Benutzer Parameter angeben, die den Befehl gefährlich machen.

## <a name="see-also"></a>Siehe auch
- [Angeben von Symbol(PDB)- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Debuggersicherheit](../debugger/debugger-security.md)
- [Quellserver](/windows/desktop/Debug/source-server-and-source-indexing)
