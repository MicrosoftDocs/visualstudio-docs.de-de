---
title: Verzögertes Laden von Dokumenten | Microsoft-Dokumentation
description: Erfahren Sie mehr über das verzögerte Laden von Dokumenten in Visual Studio und wie Sie Erweiterungen codieren, sodass Sie keine Elemente in einem Dokument Abfragen, bevor Sie geladen werden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 80c12780b2177c6715af9dc047a5652633993127
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902902"
---
# <a name="delayed-document-loading"></a>Verzögerte Dokument Ladevorgänge

Wenn ein Benutzer eine Visual Studio-Projekt Mappe erneut öffnet, werden die meisten zugeordneten Dokumente nicht sofort geladen. Der Dokument Fensterrahmen wird mit dem Status "ausstehende Initialisierung" erstellt, und ein Platzhalter Dokument (als Stub-Frame bezeichnet) wird in der ausgelaufenden dokumententabelle (RDT) platziert.

Ihre Erweiterung kann bewirken, dass Projektdokumente unnötig geladen werden, indem Sie Elemente in den Dokumenten Abfragen, bevor Sie geladen werden. Dadurch kann der Gesamt Speicherbedarf für Visual Studio erhöht werden.

## <a name="document-loading"></a>Laden von Dokumenten

Der Stub-Frame und das Dokument werden vollständig initialisiert, wenn der Benutzer auf das Dokument zugreift, z. b. durch Auswählen der Registerkarte des Fensterrahmens. Das Dokument kann auch durch eine Erweiterung initialisiert werden, die die Daten des Dokuments anfordert, indem Sie entweder direkt auf den RDT zugreifen, um die Dokument Daten abzurufen, oder indirekt auf den RDT zugreifen, indem Sie einen der folgenden Aufrufe durchführen:

- Die Fensterrahmen <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> Methode.

- Die Fensterrahmen <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> Methode in einer der folgenden Eigenschaften:

  - [__VSFPROPID. VSFPROPID_DocView](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocView>)

  - [__VSFPROPID. VSFPROPID_ViewHelper](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ViewHelper>)

  - [__VSFPROPID. VSFPROPID_DocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocData>)

  - [__VSFPROPID. VSFPROPID_AltDocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_AltDocData>)

  - [__VSFPROPID. VSFPROPID_RDTDocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_RDTDocData>)

  - [__VSFPROPID. VSFPROPID_SPProjContext](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_SPProjContext>)

- Wenn die Erweiterung verwalteten Code verwendet, sollten Sie nicht aufzurufen, <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> es sei denn, Sie sind sicher, dass sich das Dokument nicht im Status der ausstehenden Initialisierung befindet oder ob das Dokument vollständig initialisiert werden soll. Der Grund hierfür ist, dass die Methode immer das doc-Datenobjekt zurückgibt und es bei Bedarf erstellt. Stattdessen sollten Sie eine der-Methoden für die- `IVsRunningDocumentTable4` Schnittstelle abrufen.

- Wenn die Erweiterung C++ verwendet, können Sie `null` für die Parameter übergeben, die Sie nicht möchten.

- Sie können das Laden unnötiger Dokumente vermeiden, indem Sie eine der folgenden Methoden aufrufen, bevor Sie die relevanten Eigenschaften anfordern, bevor Sie andere Eigenschaften anfordern:

  - <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> mit [__VSFPROPID6. VSFPROPID_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6.VSFPROPID_PendingInitialization>).

  - <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>. Diese Methode gibt ein- <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> Objekt zurück, das einen Wert für [_VSRDTFLAGS4 enthält. RDT_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>) , wenn das Dokument noch nicht initialisiert wurde.

Sie können herausfinden, wann ein Dokument geladen wurde, indem Sie das RDT-Ereignis abonnieren, das ausgelöst wird, wenn ein Dokument vollständig initialisiert wurde. Es gibt zwei Möglichkeiten:

- Wenn die Ereignis Senke implementiert <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2> , können Sie abonnieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A> .

- Andernfalls können Sie abonnieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A> .

Das folgende Beispiel ist ein hypothetisches Dokument Zugriffs Szenario: eine Visual Studio-Erweiterung möchte einige Informationen zu geöffneten Dokumenten anzeigen, z. b. die Anzahl der Bearbeitungs Sperren und etwas über die Dokument Daten. Die Dokumente werden im RDT mithilfe <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments> von aufgelistet. Anschließend wird <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> für jedes Dokument aufgerufen, um die Anzahl der Bearbeitungs Sperren und die Dokument Daten abzurufen. Wenn sich das Dokument im Zustand "ausstehende Initialisierung" befindet, bewirkt das Anfordern der Dokument Daten, dass es unnötig initialisiert wird.

Eine effizientere Methode des Zugriffs auf ein Dokument ist die Verwendung <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> von, um die Anzahl der Bearbeitungs Sperren zu erhalten, und anschließend mithilfe von können Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> bestimmen, ob das Dokument initialisiert wurde. , Wenn die Flags keine [_VSRDTFLAGS4 enthalten. RDT_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>)wurde das Dokument bereits initialisiert, und das Anfordern der Dokument Daten mit <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> verursacht keine unnötige Initialisierung. , Wenn die Flags [_VSRDTFLAGS4 enthalten. RDT_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>)sollte die Erweiterung die Dokument Daten erst anfordern, wenn das Dokument initialisiert wird. Diese Initialisierung kann im- `OnAfterAttributeChange(Ex)` Ereignishandler erkannt werden.

## <a name="test-extensions-to-see-if-they-force-initialization"></a>Testen von Erweiterungen, um festzustellen, ob Sie die Initialisierung erzwingen

Es gibt keinen sichtbaren Hinweis, der angibt, ob ein Dokument initialisiert wurde. Daher kann es schwierig sein, herauszufinden, ob die Erweiterung die Initialisierung erzwingt. Sie können einen Registrierungsschlüssel festlegen, der die Überprüfung vereinfacht, da dadurch der Titel jedes Dokuments, das nicht vollständig initialisiert ist, den Text *[Stub]* im Titel enthält.

Legen **** Sie inHKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0\BackgroundSolutionLoad **stubtabtitleformatstring** auf *{0} [Stub]* fest.
