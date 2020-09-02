---
title: BscMake-Aufgabe | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- vc.task.bscmake
- VC.Project.VCBscMakeTool.PreserveSBR
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), tasks
- BscMake task (MSBuild (Visual C++))
ms.assetid: bb98fc67-cad8-43a7-9598-60df6d734db2
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7ed246255fc20b9660d24f234767fdeb451102f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65684547"
---
# <a name="bscmake-task"></a>BscMake-Aufgabe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

WICHTIG]
> bscmake wird nicht mehr von der Visual Studio-IDE verwendet werden. Seit Visual Studio 2008 werden Browseinformationen automatisch in einer SDF-Datei im Projektmappenordner gespeichert.  
  
 Führt das Microsoft-Wartungshilfsprogramm zum Durchsuchen von Informationen aus (bscmake.exe).  Das Tool bscmake.exe erstellt eine Browseinformationsdatei (.bsc) von Quellbrowserdateien (.sbr), die während der Kompilierung erstellt werden. Verwenden Sie den **Objektkatalog**, um eine BSC-Datei anzuzeigen. Weitere Informationen finden Sie unter [BSCMAKE-Referenz](https://msdn.microsoft.com/library/b97ad994-1355-4809-98db-6abc12c6fb13).  
  
## <a name="parameters"></a>Parameter  
 In der folgenden Tabelle werden die Parameter der **BscMake**-Aufgabe beschrieben. Die meisten Aufgabenparameter entsprechen einer Befehlszeilenoption.  
  
|Parameter|BESCHREIBUNG|  
|---------------|-----------------|  
|**AdditionalOptions**|Optionaler **String** -Parameter.<br /><br /> Eine Liste von Optionen, wie in der Befehlszeile angegeben. Beispiel: "/*Option1*  / *Option2*  / *Option #*". Verwenden Sie diesen Parameter, um Optionen anzugeben, die nicht durch einen anderen **BscMake**-Aufgabenparameter repräsentiert werden.<br /><br /> Weitere Informationen finden Sie unter den Optionen in [BSCMAKE-Optionen](https://msdn.microsoft.com/library/fa2f1e06-c684-41cf-80dd-6a554835ebd2).|  
|**OutputFile**|Optionaler **String** -Parameter.<br /><br /> Gibt einen Dateinamen an, der den Standardausgabedateinamen überschreibt.<br /><br /> Weitere Informationen finden Sie unter der **/o** -Option in [BSCMAKE-Optionen](https://msdn.microsoft.com/library/fa2f1e06-c684-41cf-80dd-6a554835ebd2).|  
|**PreserveSBR**|Optionaler **boolescher** Parameter.<br /><br /> Bei `true` wird ein nicht inkrementelles Erstellen erzwungen. Ein vollständiges nicht inkrementelles Erstellen tritt unabhängig davon auf, ob eine BSC-Datei vorhanden ist, und verhindert, dass SBR-Dateien abgeschnitten werden.<br /><br /> Weitere Informationen finden Sie unter der **/n** -Option in [BSCMAKE-Optionen](https://msdn.microsoft.com/library/fa2f1e06-c684-41cf-80dd-6a554835ebd2).|  
|**Sources**|Optionaler **ITaskItem []** -Parameter.<br /><br /> Definiert ein Array von MSBuild-Quelldateielementen, die verbraucht und von Aufgaben ausgegeben werden können.|  
|**SuppressStartupBanner**|Optionaler **boolescher** Parameter.<br /><br /> Bei `true` wird die Anzeige der Copyright- und Versionsnummernmeldung bei Aufgabenstart verhindert.<br /><br /> Weitere Informationen finden Sie unter der **/nologo** -Option in [BSCMAKE-Optionen](https://msdn.microsoft.com/library/fa2f1e06-c684-41cf-80dd-6a554835ebd2).|  
|**TrackerLogDirectory**|Optionaler **String** -Parameter.<br /><br /> Gibt das Verzeichnis für das Nachverfolgungsprotokoll an.|  
  
## <a name="remarks"></a>Bemerkungen  
  
## <a name="see-also"></a>Weitere Informationen  
 [Aufgaben Referenz](../msbuild/msbuild-task-reference.md)
