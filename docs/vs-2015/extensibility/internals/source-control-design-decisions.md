---
title: Entwurfsentscheidungen für die Quell Code Verwaltung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], design decisions
ms.assetid: 5f60ec1a-5a74-4362-8293-817a4dd73872
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 89d125dc52340e8528ee9692d5de00784632e6f2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187899"
---
# <a name="source-control-design-decisions"></a>Entwurfsentscheidungen bei der Quellcodeverwaltung
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die folgenden Entwurfsentscheidungen sollten bei der Implementierung der Quell Code Verwaltung für Projekte berücksichtigt werden.  
  
## <a name="will-information-be-shared-or-private"></a>Werden die Informationen freigegeben oder privat?  
 Die wichtigste Entwurfs Entscheidung besteht darin, welche Informationen freigegeben werden können und was privat ist. Beispielsweise ist die Liste der Dateien für das Projekt freigegeben, aber in dieser Liste von Dateien möchten einige Benutzer möglicherweise private Dateien haben. Compilereinstellungen werden gemeinsam genutzt, das Startprojekt ist jedoch im allgemeinen privat. Einstellungen sind entweder rein freigegeben, werden mit einer außer Kraft Setzung freigegeben oder rein privat. Entwurfs bedingt werden private Elemente, wie z. b. Benutzeroptionen für Projektmappen (suo), nicht in eingecheckt [!INCLUDE[vsvss](../../includes/vsvss-md.md)] . Achten Sie darauf, dass Sie private Informationen in privaten Dateien, z. b. Die SUO-Datei, oder eine bestimmte private Datei speichern, die Sie erstellen, z. b. eine csproj. User-Datei für Visual c# oder eine vbproj. User-Datei für Visual Basic.  
  
 Diese Entscheidung ist nicht alle inklusiv und kann auf Element Basis erstellt werden.  
  
## <a name="will-the-project-include-special-files"></a>Enthält das Projekt spezielle Dateien?  
 Eine weitere wichtige Entwurfs Entscheidung ist, ob die Projektstruktur spezielle Dateien verwendet. Bei speziellen Dateien handelt es sich um verborgene Dateien, die den Dateien zugrunde liegen, die in Projektmappen-Explorer und in den Eincheck-und Auscheck Dialogfeldern sichtbar sind. Wenn Sie spezielle Dateien verwenden, befolgen Sie die folgenden Richtlinien:  
  
1. Ordnen Sie dem Projektstamm Knoten keine speziellen Dateien zu – d. h. mit der Projektdatei selbst. Die Projektdatei muss eine einzelne Datei sein.  
  
2. Beim Hinzufügen, entfernen oder umbenennen spezieller Dateien in einem Projekt müssen die entsprechenden <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> Ereignisse mit dem festgelegten Flag ausgelöst werden, das angibt, dass es sich bei den Dateien um spezielle Dateien handelt. Diese Ereignisse werden von der Umgebung als Reaktion auf das Projekt aufgerufen, das die entsprechenden Methoden aufruft <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> .  
  
3. Wenn das Projekt oder der Editor <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> eine Datei aufruft, werden die dieser Datei zugeordneten speziellen Dateien nicht automatisch ausgecheckt. Übergeben Sie die speziellen Dateien zusammen mit der übergeordneten Datei. Die Umgebung erkennt die Beziehung zwischen allen Dateien, die übermittelt werden, und blendet die speziellen Dateien in der Benutzeroberfläche für das Auschecken entsprechend aus.  
  
## <a name="see-also"></a>Weitere Informationen  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [Unterstützen der Quellcodeverwaltung](../../extensibility/internals/supporting-source-control.md)
