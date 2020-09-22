---
title: 'Vorgehensweise: Verweisen auf Windows-Symbolinformationen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, symbol servers
- servers, symbol servers
- profiling tools, symbol servers
- symbol servers
ms.assetid: b7c67318-6be2-4b1e-a161-077b1f4a7c30
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c7a123a42c1a46faf67fb5b63b1ab4ef300735f3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841205"
---
# <a name="how-to-reference-windows-symbol-information"></a>Gewusst wie: Verweisen auf Windows-Symbolinformationen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der Visual Studio-Profilerstellungstools verwenden Symboldateien (.pdb), um symbolische Namen wie Funktionsnamen in Programmbinärdateien aufzulösen. Sie können diese Schritte befolgen, um automatisch die richtigen PDB-Dateien für die Windows-Version auf dem lokalen Computer herunterzuladen und zu aktualisieren.  
  
> [!NOTE]
> Diese Einstellung wirkt sich nicht auf vorhandene Berichte aus. Nur Berichte, die nach Angabe des Symbolservers erstellt wurden, werden die Symbolinformationen haben.  
  
 Weitere Informationen finden Sie unter [Angeben von Symbol (.pdb)- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
### <a name="to-use-the-microsoft-symbol-server"></a>So verwenden Sie den Microsoft-Symbolserver  
  
1. Erstellen Sie einen Ordner, um die Symboldateiinformationen aufzubewahren, wie z.B. C:\SymbolCache.  
  
2. Klicken Sie im Menü **Extras** auf **Optionen**.  
  
     Das Dialogfeld **Optionen** wird angezeigt.  
  
3. Erweitern Sie die Struktur **Debuggen**, und klicken Sie anschließend auf **Symbole**.  
  
4. Wählen Sie in **Speicherort für Symboldateien (.pdb)** **Microsoft-Symbolserver** aus  
  
5. Geben Sie in **Symbole vom Symbolserver zwischenspeichern** den Ordnerpfad ein, der in Schritt 1 erstellt wurde. Beispiel:  
  
     **C:\SymbolCache**  
  
     Sie können auch die Schaltfläche mit den Auslassungszeichen ( **...** ) anklicken und anschließend ein Verzeichnis vom Dialogfeld **Nach Ordner suchen** auswählen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren von Leistungs Sitzungen](../profiling/configuring-performance-sessions.md)   
 [Gewusst wie: Serialisieren von Symbol Informationen](../profiling/how-to-serialize-symbol-information.md)
