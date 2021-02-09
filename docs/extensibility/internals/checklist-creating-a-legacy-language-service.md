---
title: 'Prüfliste: Erstellen eines Legacy sprach Dienstanbieter | Microsoft-Dokumentation'
description: Erfahren Sie mehr über die grundlegenden Schritte zum Erstellen eines Legacy sprach Dienstanbieter für den Visual Studio-Kern-Editor.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services
- language services, native code
ms.assetid: 8b73b341-a33a-4ab5-9390-178c9e563d2d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 823d46453ac6ad4a1a5a42c1f7d18a079b39d12d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905863"
---
# <a name="checklist-create-a-legacy-language-service"></a>Prüfliste: Erstellen eines Legacy sprach Dienstanbieter
In der folgenden Prüfliste werden die grundlegenden Schritte zusammengefasst, die Sie ausführen müssen, um einen Sprachdienst für den [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Kern Editor zu erstellen. Um Ihren Sprachdienst in zu integrieren [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , müssen Sie eine Debug-Ausdrucks Auswertung erstellen. Weitere Informationen finden Sie unter [Schreiben einer CLR-Ausdrucks Auswertung](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) in der [Visual Studio-Debugger-Erweiterbarkeit](../../extensibility/debugger/visual-studio-debugger-extensibility.md).

## <a name="steps-to-create-a-language-service"></a>Schritte zum Erstellen eines sprach Dienstanbieter

1. Implementieren Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>-Schnittstelle.

    - Implementieren Sie in Ihrem VSPackage die- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> Schnittstelle, um den Sprachdienst bereitzustellen.

    - Stellen Sie Ihren Sprachdienst für die integrierte Entwicklungsumgebung (Integrated Development Environment, IDE) in ihrer Implementierung zur Verfügung <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> .

2. Implementieren Sie die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> Schnittstelle in der Dienstklasse "Hauptsprache".

     Die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> Schnittstelle ist der Ausgangspunkt der Interaktion zwischen dem Kern-Editor und dem Sprachdienst.

### <a name="optional-features"></a>Optionale Features
 Die folgenden Funktionen sind optional und können in beliebiger Reihenfolge implementiert werden. Diese Features erweitern die Funktionalität Ihres sprach Dienstanbieter.

- Farben für Syntax

  Implementieren Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>-Schnittstelle. Die Implementierung dieser Schnittstelle sollte die Parserinformationen zum Zurückgeben der entsprechenden Farbinformationen haben.

  Die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> Methode gibt die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> Schnittstelle zurück. Für jeden Text Puffer wird eine separate Farbe-Instanz erstellt, sodass Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> Schnittstelle separat implementieren müssen. Weitere Informationen finden Sie unter [Syntax Farbgebung in einem Legacy Sprachdienst](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).

- Codefenster

  Implementieren Sie die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> Schnittstelle, damit der Sprachdienst benachrichtigt werden kann, wenn ein neues Code Fenster erstellt wird.

  Die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> Methode gibt die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> Schnittstelle zurück. Der Sprachdienst kann dann dem Code Fenster in eine spezielle Benutzeroberfläche hinzufügen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> . Der Sprachdienst kann auch eine spezielle Verarbeitung durchführen, z. b. das Hinzufügen eines Text Ansichts Filters in <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.OnNewView%2A> .

- Filter für Text Ansicht

  Um die IntelliSense-Anweisungs Vervollständigung in einem Sprachdienst bereitzustellen, müssen Sie einige der Befehle abfangen, die von der Textansicht andernfalls behandelt werden. Führen Sie die folgenden Schritte aus, um diese Befehle abzufangen:

  - Implementieren <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Sie, um an der Befehlskette teilzunehmen und Editor-Befehle zu verarbeiten.

  - Wenden <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> Sie die-Methode an, und übergeben Sie Ihre- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Implementierung.

  - Wenden Sie die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RemoveCommandFilter%2A> Methode an, wenn Sie von der Ansicht trennen, sodass diese Befehle nicht mehr an Sie weitergegeben werden.

  Befehle, die verarbeitet werden müssen, hängen von den Diensten ab, die bereitgestellt werden. Weitere Informationen finden Sie unter [wichtige Befehle für Sprachdienst Filter](../../extensibility/internals/important-commands-for-language-service-filters.md).

  > [!NOTE]
  > Die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> Schnittstelle muss auf demselben Objekt wie die- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle implementiert werden.

- Anweisungsvervollständigung

  Implementieren Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>-Schnittstelle.

  Unterstützt den Befehl "Anweisungs Vervollständigung" (d. h. <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> ) und ruft die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> Methode in der- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Schnittstelle auf <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> . Weitere Informationen finden Sie unter [Anweisungs Vervollständigung in einem Legacy Sprachdienst](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).

- Methoden Tipps

  Implementieren Sie die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> Schnittstelle, um Daten für das Methoden Tipp Fenster bereitzustellen.

  Installieren Sie den Text Ansichts Filter, damit Befehle entsprechend behandelt werden, damit Sie wissen, wann ein Methoden Daten-Tipp Fenster angezeigt werden soll. Weitere Informationen finden Sie unter [Parameter Informationen in einem Legacy Sprachdienst](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).

- Fehler Marker

  Implementieren Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>-Schnittstelle.

  Erstellen Sie die fehlermarkerobjekte, die die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> -Schnittstelle implementieren, und rufen Sie die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> Methode auf, indem Sie die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> Schnittstelle des Fehler Marker

  In der Regel verwaltet jeder Fehler Marker ein Element im Fenster Aufgabenliste.

- Aufgabenlisten Elemente

  Implementieren Sie eine Aufgaben Element Klasse, die die <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem> Schnittstelle bereitstellt.

  Implementieren Sie eine Aufgaben Anbieter Klasse, die die <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider> Schnittstelle und die <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2> Schnittstelle bereitstellt.

  Implementieren Sie eine taskenumeratorklasse, die die <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumTaskItems> Schnittstelle bereitstellt.

  Registrieren Sie den Aufgaben Anbieter bei der-Methode der Aufgabenliste <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RegisterTaskProvider%2A> .

  Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> -Schnittstelle durch Aufrufen des Dienstanbieters des sprach Dienstanbieters mit der Dienst-GUID ab <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList>

  Erstellen Sie Aufgaben Element Objekte, und rufen Sie die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RefreshTasks%2A> Methode in der- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> Schnittstelle auf, wenn neue oder aktualisierte Aufgaben vorhanden sind.

- Aufgaben Elemente kommentieren

  Verwenden <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> Sie die-Schnittstelle und die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> Schnittstelle zum Abrufen der Kommentar Aufgaben Token.

  Rufen Sie eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> Schnittstelle vom <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> Dienst ab.

  Rufen Sie die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> Schnittstelle aus der- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo.EnumTokens%2A> Methode ab.

  Implementieren Sie die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskListEvents> Schnittstelle, um Änderungen in der Tokenliste zu überwachen.

- Gliedern

  Es gibt mehrere Optionen, um Gliederung zu unterstützen. Sie können z. b. den Befehl " **in Definitionen** reduzieren" unterstützen, von Editor gesteuerte Gliederungs Bereiche bereitstellen oder Client gesteuerte Bereiche unterstützen. Weitere Informationen finden [Sie unter Gewusst wie: Bereitstellen erweiterter Gliederungs Unterstützung in einem Legacy Sprachdienst](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md).

- Sprachdienst Registrierung

  Weitere Informationen zum Registrieren eines sprach Dienstanbieter finden Sie unter [Registrieren eines Legacy sprach Dienstanbieter](../../extensibility/internals/registering-a-legacy-language-service2.md) und [Verwalten von VSPackages](../../extensibility/managing-vspackages.md).

- Kontextbezogene Hilfe

  Stellen Sie den Kontext für den Editor auf eine der folgenden Arten bereit:

  - Stellen Sie den Kontext für Textmarker durch Implementieren der- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> Schnittstelle bereit.

  - Stellen Sie den gesamten Benutzer Kontext durch Implementierung der- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> Schnittstelle bereit.

## <a name="see-also"></a>Weitere Informationen
- [Entwickeln eines Legacy sprach Dienstanbieter](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Schreiben einer CLR-Ausdrucks Auswertung](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
