---
title: Best Practices für MSBuild | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
helpviewer_keywords:
- best practices, MSBuild
- MSBuild, best practices
ms.assetid: 90ef8693-e921-410a-a377-fe4d13f58c48
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e597b10913ad495193545ab304b3b324d8f66b41
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68181119"
---
# <a name="msbuild-best-practices"></a>Best Practices für MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Es werden die folgenden bewährten Methoden zum Schreiben von MSBuild-Skripts empfohlen:  
  
- Standardwerte für Eigenschaften werden am besten mit dem `Condition`-Attribut verarbeitet und nicht durch Deklarieren einer Eigenschaft, deren Standardwert in der Befehlszeile überschrieben werden kann. Verwenden Sie beispielsweise  
  
     `<MyProperty Condition="$(MyProperty)" == ''>`  
  
     `MyDefaultValue`  
  
     `</MyProperty>`  
  
- Vermeiden Sie beim Auswählen von Elementen den Einsatz von Platzhaltern. Geben Sie stattdessen Dateien explizit an. Dies erleichtert das Auffinden von Fehlern, die beim Hinzufügen oder Löschen von Dateien auftreten können.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterte Konzepte](../msbuild/msbuild-advanced-concepts.md)
