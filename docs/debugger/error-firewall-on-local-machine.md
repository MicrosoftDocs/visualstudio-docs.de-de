---
description: Die Internetverbindungsfirewall auf dem lokalen Computer, auf dem Sie Visual Studio ausführen, ist nicht für Remotedebuggen eingerichtet.
title: Firewall auf lokalem Computer | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.firewall.localmachine
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bad1dcbfa2dd80ade46bd0e848e3c1f186f3c903
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146964"
---
# <a name="error-firewall-on-local-machine"></a>Fehler: Firewall auf lokalem Computer
Die Internetverbindungsfirewall auf dem lokalen Computer, auf dem Sie Visual Studio ausführen, ist nicht für Remotedebuggen eingerichtet. Für das Remotedebuggen von verwaltetem oder systemeigenem Code mit dem Standardtransport muss der TCP-Anschluss 135 für den DCOM-Datentransfer geöffnet werden. Datei- und Druckerfreigabe müssen geöffnet werden, und devenv.exe muss der Ausnahmenliste hinzugefügt werden. Es ist möglicherweise auch erforderlich, einige IPSEC-Anschlüsse zu öffnen.

 Weitere Informationen finden Sie unter [Remotedebuggen](../debugger/remote-debugging.md).
