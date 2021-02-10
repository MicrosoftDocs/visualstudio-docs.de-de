---
title: Felder und Schnittstellen des Eigenschaften Fensters | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Auswahl, die bestimmt, welche Informationen im Eigenschaftenfenster basierend auf dem Fenster angezeigt werden, das in der Visual Studio-IDE den Fokus hat.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, fields and interfaces
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: eb1f0a0f78b935a3b61596e4dd0b595030640b00
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970009"
---
# <a name="properties-window-fields-and-interfaces"></a>Felder und Schnittstellen des Eigenschaftenfensters
Das Modell für die Auswahl, um zu bestimmen, welche Informationen im **Eigenschaften** Fenster angezeigt werden, basiert auf dem Fenster, das in der IDE den Fokus besitzt. Jedes Fenster und Objekt innerhalb des ausgewählten Fensters können das Auswahl Kontext Objekt in den globalen Auswahl Kontext übermittelt haben. Die Umgebung aktualisiert den globalen Auswahl Kontext mit Werten aus einem Fensterrahmen, wenn dieses Fenster den Fokus besitzt. Wenn sich der Fokus ändert, wird der Auswahl Kontext angezeigt.

## <a name="tracking-selection-in-the-ide"></a>Nachverfolgen der Auswahl in der IDE
 Der Fensterrahmen oder die Website, der im Besitz der IDE ist, verfügt über einen Dienst mit dem Namen <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> . Die folgenden Schritte zeigen, wie eine Änderung in einer Auswahl, die durch den Benutzer bewirkt wird, dass der Fokus entweder auf ein anderes geöffnetes Fenster wechselt, oder das Auswählen eines anderen Projekt Elements in **Projektmappen-Explorer** implementiert wird, damit der im **Eigenschaften** Fenster angezeigte Inhalt geändert wird.

1. Das-Objekt, das von Ihrem VSPackage erstellt wird, das im ausgewählten Fenster angezeigt wird <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> , um aufrufen zu können <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> .

2. Der Auswahl Container, der vom ausgewählten Fenster bereitgestellt wird, erstellt ein eigenes- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> Objekt. Wenn sich die Auswahl ändert, ruft das VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> auf, um alle Listener in der Umgebung (einschließlich des **Eigenschaften** Fensters) der Änderung zu benachrichtigen. Sie ermöglicht außerdem den Zugriff auf Hierarchie-und Element Informationen im Zusammenhang mit der neuen Auswahl.

3. Durch Aufrufen von <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> und übergeben der ausgewählten Hierarchie Elemente im- `VSHPROPID_BrowseObject` Parameter wird das-Objekt aufgefüllt <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> .

4. Ein von der [IDispatch-Schnittstelle](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) abgeleitetes Objekt wird für __VSHPROPID zurückgegeben [. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>) für das angeforderte Element, und die Umgebung umschließt Sie in eine <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> (siehe folgenden Schritt). Wenn der-Befehl fehlschlägt, führt die Umgebung einen zweiten Rückruf aus `IVsHierarchy::GetProperty` und übergibt dabei den Auswahl Container [__VSHPROPID. VSHPROPID_SelContainer](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_SelContainer>) , den das Hierarchie Element oder die Elemente bereitstellen.

    Das VSPackage für das Projekt wird nicht erstellt <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> , weil das von der Umgebung bereitgestellte Fenster VSPackage, das es implementiert (z. b. **Projektmappen-Explorer**), <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> in seinem Namen erstellt wird.

5. Die Umgebung Ruft die Methoden von <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> auf, um die Objekte auf der Grundlage der- `IDispatch` Schnittstelle zu erhalten, die im **Eigenschaften** Fenster ausgefüllt werden soll.

   Wenn ein Wert im **Eigenschaften** Fenster geändert wird, implementieren VSPackages `IVsTrackSelectionEx::OnElementValueChangeEx` und, `IVsTrackSelectionEx::OnSelectionChangeEx` um die Änderung an den Elementwert zu melden. Dann ruft die Umgebung <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> oder <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> auf, um die im **Eigenschaften** Fenster angezeigten Informationen mit den Eigenschafts Werten zu synchronisieren. Weitere Informationen finden Sie unter [Aktualisieren von Eigenschafts Werten im Eigenschaften Fenster](#updating-property-values-in-the-properties-window).

   Sie können nicht nur ein anderes Projekt Element in **Projektmappen-Explorer** auswählen, um Eigenschaften anzuzeigen, die mit diesem Element verknüpft sind. Sie können auch ein anderes Objekt innerhalb eines Formular-oder Dokument Fensters mithilfe der Dropdown Liste auswählen, die im **Eigenschaften** Fenster verfügbar ist. Weitere Informationen finden Sie in der [Objektliste Eigenschaften Fenster](../../extensibility/internals/properties-window-object-list.md).

   Sie können die Anzeige von Informationen im Fenster **Eigenschaften** Fenster von alphabetisch zu kategorischer Seite ändern. Wenn Sie verfügbar sind, können Sie auch eine Eigenschaften Seite für ein ausgewähltes Objekt öffnen, indem Sie auf die entsprechenden Schaltflächen im **Eigenschaften** Fenster klicken. Weitere Informationen finden Sie unter [Eigenschaften Fenster](../../extensibility/internals/properties-window-buttons.md) Schaltflächen und Eigenschaften [Seiten](../../extensibility/internals/property-pages.md).

   Schließlich enthält das Ende des Fensters **Eigenschaften** auch eine Beschreibung des Felds, das im Fenster **Eigenschaften** Fenster ausgewählt wurde. Weitere Informationen finden Sie unter [erhalten von Feldbeschreibungen aus dem Eigenschaften Fenster](#getting-field-descriptions-from-the-properties-window).

## <a name="updating-property-values-in-the-properties-window"></a><a name="updating-property-values-in-the-properties-window"></a> Aktualisieren von Eigenschafts Werten im Eigenschaften Fenster
Es gibt zwei Möglichkeiten, das **Eigenschaften** -Fenster ständig mit Änderungen von Eigenschaftswerten zu synchronisieren. Die erste besteht darin, die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>-Schnittstelle aufzurufen, die Zugriff auf die grundlegende Fensterverwaltungsfunktionalität bietet, einschließlich Zugriff auf und Erstellung von Tool- und Dokumentfenstern, die von der Umgebung bereitgestellt werden. In den folgenden Schritten ist dieser Synchronisierungsprozess beschrieben.

### <a name="updating-property-values-using-ivsuishell"></a>Aktualisieren von Eigenschaftswerten über IVsUIShell

#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>So aktualisieren Sie Eigenschaftswerte über die IVsUIShell-Schnittstelle

1. Rufen Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> (über den <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>-Dienst) jedes Mal auf, wenn VSPackages, Projekte oder Editoren Tool- oder Dokumentfenster erstellen oder durchlaufen müssen.

2. Implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A> Sie, um das **Eigenschaften** Fenster mit Eigenschafts Änderungen für ein Projekt (oder ein beliebiges anderes ausgewähltes Objekt, das im **Eigenschaften** Fenster durchsucht wird) synchron zu halten, ohne Ereignisse zu implementieren <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> und auszulösen <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A> .

3. Implementieren Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>-Methoden <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A>, um Clientbenachrichtigung zu Hierarchieereignissen einzurichten bzw. zu deaktivieren, ohne dass für die Hierarchie <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> implementiert werden muss.

### <a name="updating-property-values-using-iconnection"></a>Aktualisieren von Eigenschaftswerten über IConnection
 Die zweite Möglichkeit, das **Eigenschaften** -Fenster ständig mit Eigenschaftswertänderungen zu synchronisieren, besteht darin, `IConnection` für das verbindungsfähige Objekt zu implementieren, um das Vorhandensein der Ausgangsschnittstellen anzugeben. Wenn Sie den Eigenschaftsnamen lokalisieren möchten, leiten Sie das Objekt aus <xref:System.ComponentModel.ICustomTypeDescriptor> ab. Die <xref:System.ComponentModel.ICustomTypeDescriptor>-Implementierung kann die von ihr zurückgegebenen Eigenschaftsdeskriptoren sowie den Namen einer Eigenschaft ändern. Wenn Sie die Beschreibung lokalisieren möchten, erstellen Sie ein Attribut, das aus <xref:System.ComponentModel.DescriptionAttribute> abgeleitet wird, und überschreiben Sie die Description-Eigenschaft.

#### <a name="considerations-in-implementing-the-iconnection-interface"></a>Aspekte zur Implementierung der IConnection-Schnittstelle

1. `IConnection` bietet Zugriff auf ein Enumeratorunterobjekt mit der <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>-Schnittstelle. Die Schnittstelle bietet außerdem Zugriff auf alle Verbindungspunktunterobjekte, von denen jedes die <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>-Schnittstelle implementiert.

2. Für jedes Browseobjekt muss ein <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink>-Ereignis implementiert werden. Im **Eigenschaften** -Fenster erfolgt eine Empfehlung für das Ereignis, das über `IConnection`festgelegt ist.

3. Ein Verbindungspunkt steuert, wie viele Verbindungen in seiner Implementierung von <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A> zulässig sind. Ein Verbindungspunkt, der nur eine Schnittstelle zulässt, kann <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> aus der <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A>-Methode zurückgeben.

4. Ein Client kann die `IConnection`-Schnittstelle aufrufen, um Zugriff auf ein Enumeratorunterobjekt mit der <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>-Schnittstelle zu erhalten. Die <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>-Schnittstelle kann dann aufgerufen werden, um Verbindungspunkte für jede Ausgangsschnittstellen-ID (IID) zu durchlaufen.

5. `IConnection` kann auch aufgerufen werden, um mit der <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>-Schnittstelle Zugriff auf Verbindungspunktunterobjekte für jede ausgehende IID zu erhalten. Über die <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> -Schnittstelle startet oder beendet ein Client eine Beratungs Schleife mit dem Verbindungs fähigen-Objekt und der eigenen Synchronisierung des Clients. Der Client kann auch die- <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> Schnittstelle zum Abrufen eines Enumeratorobjekts mit der- <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections> Schnittstelle zum Auflisten der bekannten Verbindungen aufzählen.

## <a name="getting-field-descriptions-from-the-properties-window"></a><a name="getting-field-descriptions-from-the-properties-window"></a> Erhalten von Feldbeschreibungen aus dem Eigenschaften Fenster
Am unteren Rand des Fensters **Eigenschaften** werden in einem Beschreibungsbereich Informationen angezeigt, die zu dem ausgewählten Eigenschaftenfeld gehören. Diese Funktion ist standardmäßig aktiviert. Wenn Sie das Beschreibungsfeld ausblenden möchten, klicken Sie mit der rechten Maustaste in das Fenster **Eigenschaften** , und klicken Sie auf **Beschreibung**. Dies bewirkt auch, dass das Häkchen neben dem Titel **Beschreibung** im Menüfenster entfernt wird. Sie können das Feld wieder anzeigen, indem die gleichen Schritte ausführen, um **Beschreibung** erneut zu aktivieren.

 Die Informationen im Beschreibungsfeld stammen aus <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>. Jede Methode, Schnittstelle, Co-Klasse usw. kann ein nicht lokalisiertes `helpstring` Attribut in der Typbibliothek haben. Im Fenster **Eigenschaften** wird die Zeichenfolge aus abgerufen <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A> .

### <a name="to-specify-localized-help-strings"></a>So geben Sie lokalisierte Hilfetexte (Hilfezeichenfolgen) an

1. Fügen Sie das `helpstringdll` -Attribut zur library-Anweisung in der Typbibliothek (`typelib`) hinzu.

   > [!NOTE]
   > Dieser Schritt ist optional, wenn sich die Typbibliothek in einer Objektbibliotheksdatei (OLB-Datei) befindet.

2. Geben Sie `helpstringcontext` -Attribute für die Zeichenfolgen an. Sie können auch `helpstring` -Attribute angeben.

    Diese Attribute unterscheiden sich von den Attributen `helpfile` und `helpcontext` , die in den jeweiligen Hilfethemen in CHM-Datei enthalten sind.

   Zum Abrufen der Beschreibungs Informationen, die für den markierten Eigenschaftsnamen angezeigt werden sollen, ruft das **Eigenschaften** Fenster <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A> für die ausgewählte Eigenschaft auf und gibt das gewünschte `lcid` Attribut für die Ausgabe Zeichenfolge an. Intern findet <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2> die DLL-Datei, die im `helpstringdll`-Attribut angegeben ist, und ruft `DLLGetDocumentation` für diese DLL-Datei mit dem angegebenen Kontext und `lcid`-Attribut auf.

   Die Signatur und die Implementierung von `DLLGetDocumentation` sind:

```cpp
STDAPI DLLGetDocumentation
(
   ITypeLib * /* ptlib */,
   ITypeInfo * /* ptinfo */,
   LCID /* lcid */,
   DWORD dwCtx,
   BSTR * pbstrHelpString
);
```

 Die `DLLGetDocumentation` -Funktion muss ein Export sein, der in der DEF-Datei für die DLL-Datei definiert ist.

 Intern wird eine OLB-Datei erstellt, die tatsächlich eine DLL ist. Diese DLL enthält eine Ressource, die Typbibliotheksdatei (TLB-Datei), und eine exportierte Funktion, `DLLGetDocumentation`.

 Im Fall von OLB-Dateien ist das `helpstringdll` Attribut optional, weil es dieselbe Datei angibt, die selbst die TLB-Datei enthält.

 Wenn Sie möchten, dass Zeichenfolgen abgerufen und im Bereich **Beschreibung** angezeigt werden, ist es daher mindestens erforderlich, dass Sie das `helpstring` -Attribut in der Typbibliothek angeben. Sollen diese Zeichenfolgen lokalisiert sein, müssen Sie das (optionale) `helpstringdll` -Attribut und das (erforderliche) `helpstringcontext` -Attribut angeben sowie `DLLGetDocumentation`implementieren.

 Es gibt keine weiteren Schnittstellen, die implementiert werden müssen, wenn lokalisierte Informationen über das `helpstringcontext` -Attribut und `DLLGetDocumentation`abgerufen werden.

 Eine weitere Möglichkeit zum Abrufen des lokalisierten Namens und der lokalisierten Beschreibung einer Eigenschaft besteht darin, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.GetLocalizedPropertyInfo%2A> zu implementieren. Weitere Informationen über die Implementierung dieser Methode finden Sie unter [Properties Window Fields and Interfaces](../../extensibility/internals/properties-window-fields-and-interfaces.md).

## <a name="see-also"></a>Weitere Informationen

- [Erweitern von Eigenschaften](../../extensibility/internals/extending-properties.md)
