---
title: 'Vorgehensweise: Erstellen einer. Vsct-Datei aus einer vorhandenen. CTO-Datei | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, creating based on a .cto file
ms.assetid: 847717c9-477d-4ac9-8b2c-2da878912478
caps.latest.revision: 11
manager: jillfra
ms.openlocfilehash: 83608d768940158dcdab427a557577677e56f7c8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62822437"
---
# <a name="how-to-create-a-vsct-file-from-an-existing-cto-file"></a>Gewusst wie: Erstellen einer VSCT-Datei anhand einer vorhandenen CTO-Datei
Sie können eine XML-basierte VSCT-Datei anhand einer vorhandenen binären CTO-Datei erstellen. Diese Vorgehensweise ermöglicht es Ihnen, das neue Befehlstabellen-Compilerformat zu nutzen. Dies funktioniert sogar, wenn die CTO-Datei aus einer CTC-Datei kompiliert wurde. Sie können die VSCT-Datei bearbeiten und in eine andere CTO-Datei kompilieren.  
  
### <a name="to-create-a-vsct-file-from-a-cto-file"></a>So erstellen Sie eine VSCT-Datei anhand einer CTO-Datei  
  
1. Erstellen Sie Kopien der CTO-Datei und der zugehörigen .CRSYM-Datei.  
  
2. Platzieren Sie die Dateien in dem Verzeichnis, in dem sich der Compiler „vsct.exe“ befindet.  
  
3. Navigieren Sie an der Visual Studio-Eingabeaufforderung zu dem Verzeichnis, das die CTO- und die CTSYM-Datei enthält.  
  
4. Geben Sie **vsct.exe** _ctofilename_**.cto** _vsctfilename_**.vsct -S**_symfilename_**.ctsym**ein.  
  
     `ctofilename` ist der Name der CTO-Datei, `vsctfilename` ist der Name der VSCT-Datei, die Sie erstellen möchten, und `symfilename` ist der Name der CTSYMDatei.  
  
     Bei diesem Vorgang wird eine neue VSCT-XML-Befehlstabellen-Compilerdatei erstellt. Sie können die Datei mit „vsct.exe“, dem vsct-Compiler, wie jede andere VSCT-Datei bearbeiten und kompilieren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Vorgehensweise: Erstellen einer. Vsct-Datei](../extensibility/internals/how-to-create-a-dot-vsct-file.md)   
 [VSCT-Dateien (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)