---
title: 'Fehler: Der gemeinsame Dateizugriff von Windows wurde so konfiguriert... | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.remote_credentials_prohibited
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: c45a1b74-61ec-4c64-9e2c-13051a4f50a5
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 96d65ae615522bcee43ddf5e8181e96eecc0d958
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157503"
---
# <a name="error-windows-file-sharing-has-been-configured"></a>Fehler: Der gemeinsame Dateizugriff von Windows wurde so konfiguriert...
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der gemeinsame Dateizugriff von Windows wurde so konfiguriert, dass Sie mit einem anderen Benutzernamen eine Verbindung mit dem Remotecomputer herstellen. Dies ist mit dem Remotedebuggen nicht kompatibel.  
  
 Die aktuelle Dateifreigabekonfiguration wurde so eingerichtet, dass eine Verbindung mit dem Remotecomputer unter einem anderen Benutzernamen hergestellt wird. In diesem Szenario ist Remotedebuggen nicht möglich.  
  
 Beseitigen Sie diesen Fehler, indem Sie sich bei dem Computer unter dem anderen Kontonamen anmelden, oder ändern Sie die Dateifreigabe auf den Kontonamen, unter dem Sie debuggen.  
  
 Wenn Sie sich unter diesem Benutzernamen am Remotecomputer anmelden möchten, müssen Sie zuvor die Verbindung zum Remotecomputer beenden.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
1. Melden Sie sich auf dem lokalen Computer (der Computer, von dem Sie debuggen) mit dem anderen Kontonamen an.  
  
     – oder –  
  
     . Trennen Sie die Verbindung mit dem Remotecomputer, und konfigurieren Sie anschließend die Dateifreigabe, um anhand Ihres Kontonamens eine Verbindung mit dem anderen Computer herzustellen:  
  
    1. Zeigen Sie imMenü **Start** auf **Zubehör**, und klicken Sie dann auf **Eingabeaufforderung**.  
  
    2. Geben Sie an der Windows-Eingabeaufforderung Folgendes ein:  
  
         `net use /delete computer_name`  
  
    3. Ändern Sie die Dateifreigabeeinstellungen mit einer der in der Windows-Hilfe dokumentierten Methoden.
