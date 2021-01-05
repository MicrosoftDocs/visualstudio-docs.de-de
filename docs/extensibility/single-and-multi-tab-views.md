---
title: Ansichten für einzelne und mehrere Registerkarten | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie Ansichten mit mehreren Registerkarten in Editoren implementieren, z. b. in einem Code-Editor Fenster und einem Forms-Designer
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - single and multi-tab views
ms.assetid: e3611704-349f-4323-b03c-f2b0a445d781
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 94081af0bfdb85793c092f76d28758f220f4628b
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/21/2020
ms.locfileid: "97715209"
---
# <a name="single-and-multi-tab-views"></a>Ansichten mit einer und mehreren Registerkarten
Ein Editor kann verschiedene Typen von Ansichten erstellen. Ein Beispiel hierfür ist ein Code-Editor-Fenster, ein weiteres ist ein Forms-Designer.

 Eine Ansicht mit mehreren Registerkarten ist eine Ansicht mit mehreren Registerkarten. Der HTML-Editor verfügt beispielsweise über zwei Registerkarten am unteren Rand: **Entwurf** und **Quelle**, jeweils eine logische Ansicht. In der Entwurfs Ansicht wird eine gerenderte Webseite angezeigt, während die andere den HTML-Code anzeigt, der die Webseite umfasst.

## <a name="accessing-physical-views"></a>Zugreifen auf physische Sichten
 Physische Sichten hosten Dokument Ansichts Objekte, die jeweils eine Ansicht der Daten im Puffer darstellen (z. b. Code oder ein Formular). Dementsprechend hat jedes Dokument Ansichts Objekt eine physische Ansicht (identifiziert durch etwas, das als physische Ansichts Zeichenfolge bezeichnet wird) und in der Regel eine einzelne logische Ansicht.

 In einigen Fällen kann eine physische Ansicht jedoch über zwei oder mehr logische Sichten verfügen. Bei einigen Beispielen handelt es sich um einen Editor, der über ein geteiltes Fenster mit parallelen Ansichten verfügt, oder um einen Formular-Designer, der über eine GUI/Entwurfs Ansicht und eine Code-Behind-the-Form-Ansicht verfügt.

 Damit der Editor auf alle verfügbaren physischen Ansichten zugreifen kann, müssen Sie für jeden Typ von Dokument Ansichts Objekt, das die Editorfactory erstellen kann, eine eindeutige physische Ansichts Zeichenfolge erstellen. Beispielsweise kann die [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] Editorfactory Dokument Ansichts Objekte für ein Code Fenster und ein Formular-Designer-Fenster erstellen.

## <a name="creating-multi-tabbed-views"></a>Erstellen von Ansichten mit mehreren Registerkarten
 Obwohl ein Dokument Ansichts Objekt einer physischen Ansicht über eine eindeutige physische Ansichts Zeichenfolge zugeordnet werden muss, können Sie mehrere Registerkarten innerhalb der physischen Ansicht platzieren, um die Anzeige von Daten auf verschiedene Weise zu ermöglichen. Bei dieser Konfiguration mit mehreren Registerkarten werden alle Registerkarten derselben physischen Ansichts Zeichenfolge zugeordnet, aber jeder Registerkarte wird eine andere logische Ansichts-GUID zugewiesen.

 Um für einen Editor eine Ansicht mit mehreren Registerkarten zu erstellen, müssen <xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiViewDocumentView> Sie die-Schnittstelle implementieren und dann <xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID> jeder von Ihnen erstellten Registerkarte eine andere logische Ansichts-GUID () zuordnen.

 Der HTML-Editor von Visual Studio ist ein Beispiel für einen Editor mit einer Ansicht mit mehreren Registerkarten. Es verfügt über **Entwurfs** -und **Quell** Registerkarten. Um dies zu ermöglichen, wird jeder Registerkarte eine andere logische Ansicht zugeordnet, `LOGICALVIEWID_TextView` für die Registerkarte **Entwurf** und `LOGICALVIEWID_Code` für die Registerkarte **Quelle** .

 Durch die Angabe der entsprechenden logischen Ansicht kann ein VSPackage auf die Sicht zugreifen, die einem bestimmten Zweck entspricht, z. b. das Entwerfen eines Formulars, das Bearbeiten von Code oder das Debuggen von Code. Eines der Fenster muss jedoch durch die NULL-Zeichenfolge identifiziert werden, und diese muss der primären logischen Ansicht ( `LOGVIEWID_Primary` ) entsprechen.

 In der folgenden Tabelle sind die verfügbaren logischen Ansichts Werte und deren Verwendung aufgeführt.

|logviewid-GUID|Empfohlene Verwendung|
|--------------------|---------------------|
|`LOGVIEWID_Primary`|Standard/primäre Ansicht der Editorfactory.<br /><br /> Alle editorfactorys müssen diesen Wert unterstützen. In dieser Sicht muss die NULL-Zeichenfolge als physische Ansichts Zeichenfolge verwendet werden. Mindestens eine logische Ansicht muss auf diesen Wert festgelegt werden.|
|`LOGVIEWID_Debugging`|Debugansicht. In der Regel wird `LOGVIEWID_Debugging` der gleichen Ansicht wie zugeordnet `LOGVIEWID_Code` .|
|`LOGVIEWID_Code`|Ansicht, die vom Befehl " **Code anzeigen** " gestartet wird.|
|`LOGVIEWID_Designer`|Ansicht, die vom Befehl " **Formular anzeigen** " gestartet wird.|
|`LOGVIEWID_TextView`|Text-Editor-Ansicht. Dies ist die Ansicht, die zurückgibt <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> , von der aus Sie auf zugreifen können <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .|
|`LOGVIEWID_UserChooseView`|Fordert den Benutzer auf, die zu verwendende Ansicht auszuwählen.|
|`LOGVIEWID_ProjectSpecificEditor`|Wird vom Dialogfeld **Öffnen mit** an<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.OpenItem%2A><br /><br /> Wenn der Benutzer den Eintrag "(Projekt Standard-Editor)" auswählt.|

 Obwohl die GUIDs der logischen Ansicht erweiterbar sind, können Sie nur die in Ihrem VSPackage definierten GUIDs der logischen Ansicht verwenden.

 Beim Herunterfahren behält Visual Studio die GUID der Editorfactory und die dem Dokument Fenster zugeordneten physischen Ansichts Zeichenfolgen bei, damit Sie Dokument Fenster erneut öffnen kann, wenn die Projekt Mappe erneut geöffnet wird. Nur Fenster, die geöffnet sind, wenn eine Projekt Mappe geschlossen wird, werden in der Projektmappendatei (. suo) beibehalten. Diese Werte entsprechen den `VSFPROPID_guidEditorType` Werten und, die `VSFPROPID_pszPhysicalView` im- `propid` Parameter in der-Methode übergeben werden <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> .

## <a name="example"></a>Beispiel
 Dieser Code Ausschnitt veranschaulicht, wie das- <xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID.TextView> Objekt verwendet wird, um auf eine Ansicht zuzugreifen, die implementiert `IVsCodeWindow` . In diesem Fall wird der <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument> -Dienst verwendet, um aufzurufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> und anzufordern `LOGVIEWID_TextView` , wodurch ein Zeiger auf einen Fensterrahmen abgerufen wird. Ein Zeiger auf das Dokument Ansichts Objekt wird durch Aufrufen von <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> und durch Angeben des Werts abgerufen `VSFPROPID_DocView` . Aus dem Dokument `QueryInterface` Ansichts Objekt wird für aufgerufen `IVsCodeWindow` . In diesem Fall wird erwartet, dass ein Text-Editor zurückgegeben wird, sodass das in der-Methode zurückgegebene Dokument Ansichts Objekt <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> ein Code Fenster ist.

```cpp
HRESULT CFindTool::GotoFileLocation(const WCHAR * szFile, long iLine, long iStart, long iLen)
{
  HRESULT hr;
  if (NULL == szFile || !*szFile)
    return E_INVALIDARG;

  if (iLine == -1L)
    return S_FALSE;

  VSITEMID                  itemid;
  VARIANT                   var;
  RECT                      rc;
  IVsUIShellOpenDocument *  pOpenDoc    = NULL;
  IVsCodeWindow *           pCodeWin    = NULL;
  IVsTextView *             pTextView   = NULL;
  IVsUIHierarchy *          pHierarchy  = NULL;
  IVsWindowFrame *          pFrame      = NULL;
  IUnknown *                pUnk        = NULL;
  IVsHighlight *            pHighlight  = NULL;

  IfFailGo(CGlobalServiceProvider::HrQueryService(SID_SVsUIShellOpenDocument, IID_IVsUIShellOpenDocument, (void **)&pOpenDoc));
  IfFailGo(pOpenDoc->OpenDocumentViaProject(szFile, LOGVIEWID_TextView, NULL, &pHierarchy, &itemid, &pFrame));
  pFrame->Show();
  VariantInit(&var);
  IfFailGo(pFrame->GetProperty(VSFPROPID_DocView, &var));
  if (VT_UNKNOWN != var.vt) { hr = E_FAIL; goto Error; }
  pUnk = V_UNKNOWN(&var);
  if (NULL != pUnk)
  {
    IfFailGo(pUnk->QueryInterface(IID_IVsCodeWindow, (void **)&pCodeWin));
    if (SUCCEEDED(hr = pCodeWin->GetLastActiveView(&pTextView)) ||
        SUCCEEDED(hr = pCodeWin->GetPrimaryView(&pTextView)) )
    {
      pTextView->SetSelection(iLine, iStart, iLine, iStart + iLen);
      // uncover selection
      IfFailGo(pTextView->QueryInterface(IID_IVsHighlight, (void**)&pHighlight));
      IfFailGo(SUCCEEDED(pHighlight->GetHighlightRect(&rc)));
      UncoverSelectionRect(&rc);
    }
  }

Error:
  CLEARINTERFACE(pHighlight);
  CLEARINTERFACE(pTextView);
  CLEARINTERFACE(pCodeWin);
  CLEARINTERFACE(pUnk);
  CLEARINTERFACE(pFrame);
  CLEARINTERFACE(pOpenDoc);
  CLEARINTERFACE(pHierarchy);
  RedrawWindow(m_hwndResults, NULL, NULL, RDW_ERASE|RDW_FRAME|RDW_INVALIDATE|RDW_ALLCHILDREN);
  return hr;
}
```

## <a name="see-also"></a>Weitere Informationen
- [Unterstützen mehrerer Dokumentansichten](../extensibility/supporting-multiple-document-views.md)
- [Gewusst wie: Anfügen von Ansichten zu Dokumentdaten](../extensibility/how-to-attach-views-to-document-data.md)
- [Erstellen von benutzerdefinierten Editoren und Designern](../extensibility/creating-custom-editors-and-designers.md)
