---
title: 'DA0013: Umfangreiche Verwendung von String.Split oder String.Substring | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.13
- vs.performance.rules.DAAvoidStringSubstr
- vs.performance.DA0013
- vs.performance.rules.DA0013
helpviewer_keywords:
- vs.performance.13
- vs.performance.rules.DA0013
ms.assetid: f501f423-bef9-4e08-bf96-c9ac9957e5a2
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d6ff05e7e8cc74eacb00b5ec8ff42bd48faaa12c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68159195"
---
# <a name="da0013-high-usage-of-stringsplit-or-stringsubstring"></a>DA0013: Umfangreiche Verwendung von String.Split oder String.Substring
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Regel-ID | DA0013 |  
| Kategorie |. Leitfaden zur Verwendung von NET Framework |  
| Profil Erstellungs Methoden | Stichprobenentnahme |  
| Meldung | Reduzieren Sie die Verwendung von String. Split-und String. Substring-Funktionen. |  
| Regeltyp | Warnung |  
  
## <a name="cause"></a>Ursache  
 Aufrufe der System.String.Split-Methode oder der System.String.Substring-Methode machen einen großen Teil der Profilerstellungsdaten aus. Verwenden Sie ggf. „System.String.IndexOf“ oder „System.String.IndexOfAny“, wenn Sie testen möchten, ob in einer Zeichenfolge eine Teilzeichenfolge vorhanden ist.  
  
## <a name="rule-description"></a>Beschreibung der Regel  
 Die Split-Methode wirkt auf ein Zeichenfolgenobjekt und gibt ein neues Zeichenfolgenarray zurück, das die Teilzeichenfolgen des Originals enthält. Die Funktion belegt Speicher für das zurückgegebene Arrayobjekt und ordnet ein neues Zeichenfolgenobjekt für jedes gefundene Arrayelement zu. Auf ähnliche Weise behandelt die Substr-Methode ein Zeichenfolgenobjekt und gibt eine neue Zeichenfolge zurück, die der angeforderten Teilzeichenfolge entspricht.  
  
 Wenn die Verwaltung von Speicherbelegungen in der Anwendung wichtig ist, sollten Sie Alternativen zur String.Split-Methode und String.Substr-Methode verwenden. So können Sie beispielsweise mit der IndexOf-Methode oder mit der IndexOfAny-Methode eine bestimmte Teilzeichenfolge innerhalb einer Zeichenfolge suchen, ohne eine neue Instanz der Zeichenfolgenklasse zu erstellen.  
  
## <a name="how-to-investigate-a-warning"></a>Vorgehensweise bei der Überprüfung einer Warnung  
 Doppelklicken Sie auf die Meldung im Fenster Fehlerliste, um zur [Funktionsdetailansicht](../profiling/function-details-view.md) der Samplingprofildaten zu navigieren. Suchen Sie in den aufrufenden Funktionen nach den Programmabschnitten, in denen die System.String.Split-Methode oder die System.String.Substr-Methode am häufigsten verwendet wird. Wenn möglich können Sie mit der IndexOf-Methode oder mit der IndexOfAny-Methode eine bestimmte Teilzeichenfolge innerhalb einer Zeichenfolge suchen, ohne eine neue Instanz der Zeichenfolgenklasse zu erstellen.
