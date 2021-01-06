---
title: Modell eines Legacy sprach Dienstanbieter | Microsoft-Dokumentation
description: Verwenden Sie dieses Modell eines minimalen sprach Dienstanbieter für den Visual Studio-Kern-Editor als Leitfaden zum Erstellen eines eigenen sprach Dienstanbieter.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, model
ms.assetid: d8ae1c0c-ee3d-4937-a581-ee78d0499793
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2928d3c09a54ea8e9548f7751381279f153643e5
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97876739"
---
# <a name="model-of-a-legacy-language-service"></a>Modell eines Legacysprachdiensts
Ein Sprachdienst definiert die Elemente und Features für eine bestimmte Sprache und wird verwendet, um dem Editor spezifische Informationen für diese Sprache bereitzustellen. Der Editor muss z. b. die Elemente und Schlüsselwörter der Sprache kennen, um die Syntax Farbgebung zu unterstützen.

 Der Sprachdienst arbeitet eng mit dem vom Editor verwalteten Text Puffer und der Ansicht, die den Editor enthält, zusammen. Die Microsoft IntelliSense **Quick Info** -Option ist ein Beispiel für eine Funktion, die von einem Sprachdienst bereitgestellt wird.

## <a name="a-minimal-language-service"></a>Ein minimaler Sprachdienst
 Der grundlegendste Sprachdienst enthält die folgenden beiden Objekte:

- Der *Sprachdienst* implementiert die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> Schnittstelle. Ein Sprachdienst enthält Informationen zur Sprache, einschließlich des Namens, der Dateinamen Erweiterungen, des Code Fenster-Managers und der Farbauswahl.

- Die *Farbgebung* implementiert die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> Schnittstelle.

  Die folgende konzeptionelle Zeichnung zeigt ein Modell eines grundlegenden sprach Dienstanbieter.

  ![Grafik zum Sprachdienst Modell](../../extensibility/media/vslanguageservicemodel.gif "vslanguageservicemodel") Basic-Sprachdienst Modell

  Das Dokument Fenster hostet die *Dokument Ansicht* des Editors, in diesem Fall der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Kern Editor. Die Dokument Ansicht und der Text Puffer befinden sich im Besitz des Editors. Diese Objekte funktionieren mit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] über ein spezielles Dokument Fenster, das als *Code Fenster* bezeichnet wird. Das Code Fenster ist in einem <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> Objekt enthalten, das von der IDE erstellt und gesteuert wird.

  Wenn eine Datei mit einer bestimmten Erweiterung geladen wird, sucht der Editor den Sprachdienst, der dieser Erweiterung zugeordnet ist, und übergibt das Code Fenster durch Aufrufen der- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> Methode. Der Sprachdienst gibt einen *Code Fenster-Manager* zurück, der die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> Schnittstelle implementiert.

  In der folgenden Tabelle finden Sie eine Übersicht über die Objekte im Modell.

| Komponente | Object | Funktion |
|------------------| - | - |
| Text Puffer | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> | Ein Unicode-Lese-/Schreib-Textstream. Es ist möglich, dass Text andere Codierungen verwendet. |
| Codefenster | <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> | Ein Dokument Fenster, das mindestens eine Textansicht enthält. Wenn [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sich im MDI-Modus (Multiple Document Interface) befindet, ist das Code Fenster ein untergeordnetes MDI-Element. |
| Text Ansicht | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> | Ein Fenster, in dem der Benutzer mithilfe der Tastatur und der Maus navigieren und Text anzeigen kann. Dem Benutzer wird eine Textansicht als Editor angezeigt. Sie können Text Ansichten in normalen Editor Fenstern, im Ausgabefenster und im direkt Fenster verwenden. Darüber hinaus können Sie eine oder mehrere Text Ansichten innerhalb eines Code Fensters konfigurieren. |
| Text-Manager | <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>Wird vom Dienst verwaltet, von dem Sie einen Zeiger erhalten. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> | Eine Komponente, die allgemeine Informationen verwaltet, die von allen zuvor beschriebenen Komponenten gemeinsam genutzt werden. |
| Sprachdienst | Implementierungsabhängig; implementiert <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> | Ein Objekt, das den Editor sprachspezifische Informationen wie Syntax Hervorhebung, Anweisungs Vervollständigung und zugehörige Klammern bereitstellt. |

## <a name="see-also"></a>Weitere Informationen
- [Dokumentdaten und Dokumentansicht in benutzerdefinierten Editoren](../../extensibility/document-data-and-document-view-in-custom-editors.md)
