---
title: Legacy-Sprachdienst Schnittstellen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IVsLanguageInfo interface
- language services, objects
ms.assetid: 03b2d507-f463-417e-bc22-bdac68eeda52
caps.latest.revision: 25
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 02f63cd5e3f0599723aee12f7aed2c56b74c3249
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196106"
---
# <a name="legacy-language-service-interfaces"></a>Schnittstellen von Legacysprachdiensten
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Für eine bestimmte Programmiersprache kann jeweils nur eine Instanz eines sprach Dienstanbieter vorhanden sein. Ein einzelner Sprachdienst kann jedoch mehr als einen Editor verarbeiten.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ordnet einen Sprachdienst keinem bestimmten Editor zu. Wenn Sie also einen Sprachdienst Vorgang anfordern, müssen Sie den entsprechenden Editor als Parameter angeben.  
  
## <a name="common-interfaces-associated-with-language-services"></a>Allgemeine Schnittstellen, die Sprachdiensten zugeordnet sind  
 Der Editor Ruft den Sprachdienst durch Aufrufen von <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> für das entsprechende VSPackage ab. Die in diesem-Befehl ausgeführte Dienst-ID (SID) identifiziert den angeforderten Sprachdienst.  
  
 Sie können die Schnittstellen des Kern sprach Dienstanbieter für eine beliebige Anzahl von separaten Klassen implementieren. Eine gängige Vorgehensweise besteht jedoch darin, die folgenden Schnittstellen in einer einzigen Klasse zu implementieren:  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageBlock> (optional)  
  
  Die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> Schnittstelle muss für alle Sprachdienste implementiert werden. Sie enthält Informationen zu Ihrem Sprachdienst, wie z. b. den lokalisierten Namen der Sprache, die Dateinamen Erweiterungen, die dem Sprachdienst zugeordnet sind, und das Abrufen einer Farbgebung.  
  
## <a name="additional-language-service-interfaces"></a>Zusätzliche Sprachdienst Schnittstellen  
 Andere Schnittstellen können mit Ihrem Sprachdienst bereitgestellt werden. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] fordert für jede Instanz des Text Puffers eine separate Instanz dieser Schnittstellen an. Daher sollten Sie jede dieser Schnittstellen in einem eigenen-Objekt implementieren. In der folgenden Tabelle sind Schnittstellen aufgeführt, für die eine Instanz pro Text Puffer Instanz erforderlich ist.  
  
|Schnittstelle|BESCHREIBUNG|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Verwaltet Code Fenster-Zusatzelemente, wie z. b. die Dropdown Leiste. Sie können diese Schnittstelle mithilfe der- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> Methode erhalten. Es ist ein <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> pro Code Fenster vorhanden.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>|Farmiert sprach Schlüsselwörter und Trennzeichen. Sie können diese Schnittstelle mithilfe der- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> Methode erhalten. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> wird zur zeichnungszeit aufgerufen. Vermeiden Sie eine rechenintensive Arbeit innerhalb von <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> oder Leistungseinbußen.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>|Stellt Quick Infos für IntelliSense-Parameter bereit. Wenn der Sprachdienst ein Zeichen erkennt, das angibt, dass Methoden Daten angezeigt werden sollen, z. b. eine öffnende Klammer, wird die-Methode aufgerufen, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> um die Textansicht zu benachrichtigen, dass der Sprachdienst zum Anzeigen einer QuickInfo für die Parameter Info bereit ist. Die Textansicht ruft dann den Sprachdienst mithilfe der Methoden der- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> Schnittstelle zurück, um die erforderlichen Informationen zum Anzeigen der QuickInfo zu erhalten.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>|Bietet die IntelliSense-Anweisungs Vervollständigung. Wenn der Sprachdienst bereit ist, eine Vervollständigungsliste anzuzeigen, wird die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> Methode für die Textansicht aufgerufen. Die Textansicht ruft dann den Sprachdienst mithilfe von Methoden für das- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> Objekt zurück.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|Ermöglicht das Ändern der Textansicht mithilfe des Befehls Handlers. Die Klasse, in der Sie die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> Schnittstelle implementieren, muss auch die- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle implementieren. Die Textansicht Ruft das- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> Objekt ab, indem das-Objekt abgefragt <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> wird, das an die-Methode weitergegeben wird <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> . Es sollte ein- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> Objekt für jede Ansicht vorhanden sein.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Fängt die Befehle ab, die vom Benutzer in das Code Fenster eingetippt werden. Überwachen der Ausgabe der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Implementierung, um benutzerdefinierte Vervollständigungs Informationen bereitzustellen und Änderungen anzuzeigen<br /><br /> Um <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> das Objekt an die Textansicht zu übergeben, geben Sie an <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> .|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Entwickeln eines Legacy sprach Dienstanbieter](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [Prüfliste: Erstellen eines Legacysprachdiensts](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)
