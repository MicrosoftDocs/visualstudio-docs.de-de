---
title: Entwerfen eines Business Data Connectivity-Modells | Microsoft-Dokumentation
description: Entwerfen Sie ein Business Data Connectivity-Modell (BDC). Fügen Sie Entitäten und Methoden hinzu. Definieren Sie Methoden Parameter. Filter Deskriptoren hinzufügen. Überprüfen Sie das BDC-Modell.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], designing a model
- Business Data Connectivity service [SharePoint development in Visual Studio], designing a model
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b574c52b9081cc6640c5611e0759b5559e7a4f6d
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672651"
---
# <a name="design-a-business-data-connectivity-model"></a>Entwerfen eines Business Data Connectivity-Modells
  Sie können ein Modell für den Business Data Connectivity (BDC)-Dienst entwickeln, indem Sie einer Modelldatei Entitäten und Methoden hinzufügen. Eine Entität beschreibt eine Auflistung von Datenfeldern. Beispielsweise kann eine Entität eine Tabelle in einer Datenbank darstellen. Eine Methode führt eine Aufgabe aus, z. b. das Hinzufügen, löschen oder Aktualisieren von Daten, die von den Entitäten dargestellt Weitere Informationen finden Sie unter [integrieren von Geschäftsdaten in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md).

## <a name="add-entities"></a>Hinzufügen von Entitäten
 Sie können eine Entität hinzufügen, indem Sie eine **Entität** aus der Visual Studio- **Toolbox** auf den BDC-Designer ziehen oder kopieren. Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen einer Entität zu einem Modell](../sharepoint/how-to-add-an-entity-to-a-model.md).

 Definieren Sie die Felder der Entität in einer Klasse. Beispielsweise können Sie einer Klasse ein Feld mit dem Namen hinzufügen `Address` `Customer` . Sie können dem Projekt entweder eine neue Klasse hinzufügen oder eine vorhandene Klasse verwenden, die mit anderen Tools wie dem objektrelationaler Designer (O/R-Designer) erstellt wurde. Der Name der Entität und der Name der Klasse, die die Entität darstellt, müssen nicht abgeglichen werden. Sie verknüpfen die-Klasse mit der-Entität, wenn Sie die Methoden in Ihrem Modell definieren.

## <a name="add-methods"></a>Methoden hinzufügen
 Der BDC-Dienst ruft Methoden in Ihrem Modell auf, wenn Benutzerinformationen in einer Liste oder einem Webpart, die auf Ihrem Modell basiert, anzeigen, hinzufügen, aktualisieren oder löschen. Sie müssen dem Modell für jede Aufgabe, die der Benutzer ausführen kann, eine Methode hinzufügen. Erstellen Sie Methoden, indem Sie einen der fünf grundlegenden Methoden Typen aus dem Details-Fenster der **BDC-Methode** auswählen. In der folgenden Tabelle werden die fünf grundlegenden Methoden eines BDC-Modells beschrieben.

|Methode|Beschreibung|
|------------|-----------------|
|Finder|Gibt eine Auflistung von Entitäts Instanzen zurück. Wird aufgerufen, wenn der Benutzer die Liste oder das WebPart öffnet. Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen einer Finder-Methode](../sharepoint/how-to-add-a-finder-method.md).|
|Spezifischer Finder|Gibt eine bestimmte Entitäts Instanz zurück. Wird aufgerufen, wenn ein Benutzer die Details eines bestimmten Elements in einer Liste anzeigt. Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen einer bestimmten Finder-Methode](../sharepoint/how-to-add-a-specific-finder-method.md).|
|Creator|Fügt der Datenquelle einer Entität neue Daten hinzu. Wird aufgerufen, wenn Benutzer die Schaltfläche **Neues Element** auf dem Menüband einer Liste auswählen, die auf dem Modell basiert. Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen einer Creator-Methode](../sharepoint/how-to-add-a-creator-method.md).|
|Updater|Ändert die Daten in einer Liste. Wird aufgerufen, wenn Benutzerinformationen in einer Liste aktualisieren. Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen einer Updater-Methode](../sharepoint/how-to-add-an-updater-method.md).|
|Deleter|Entfernt Daten. Wird aufgerufen, wenn Benutzer ein Element aus der Liste löschen. Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen einer Deleter-Methode](../sharepoint/how-to-add-a-deleter-method.md).|

## <a name="define-method-parameters"></a>Definieren von Methoden Parametern
 Wenn Sie eine Methode erstellen, fügt Visual Studio die Eingabe-und Ausgabeparameter hinzu, die für den Methodentyp geeignet sind. Diese Parameter sind nur Platzhalter. In den meisten Fällen müssen Sie die Parameter so ändern, dass Sie den richtigen Datentyp übergeben oder zurückgeben. Standardmäßig gibt eine Finder-Methode z. b. eine Zeichenfolge zurück. In den meisten Fällen möchten Sie den Rückgabe Parameter der Finder-Methode so ändern, dass er eine Auflistung von Entitäten zurückgibt. Dies können Sie erreichen, indem Sie den Typdeskriptor des Parameters ändern. Ein Typdeskriptor ist eine Auflistung von Attributen, die den Datentyp eines Parameters beschreibt. Weitere Informationen finden Sie unter Gewusst [wie: Definieren des Typdeskriptors für einen Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

 Visual Studio ermöglicht Ihnen das Kopieren von Typdeskriptoren zwischen Parametern im Modell. Beispielsweise können Sie einen Typdeskriptor `CustomerTD` mit dem Namen für den Rückgabe Parameter der `GetCustomer` Methode definieren. Sie können den `CustomerTD` Typdeskriptor in den **BDC-Explorer** kopieren und dann den Typdeskriptor in den Eingabeparameter der Methode einfügen `CreateCustomer` . Dies verhindert, dass Sie denselben Typdeskriptor mehrmals definieren müssen.

## <a name="method-instances"></a>Methoden Instanzen
 Wenn Sie eine Methode erstellen, fügt Visual Studio eine Standardmethoden Instanz hinzu. Eine Methoden Instanz ist ein Verweis auf eine Methode, zuzüglich der Standardwerte für die Parameter. Eine einzelne Methode kann über mehrere Methoden Instanzen verfügen. Jede Instanz ist eine Kombination aus der Methoden Signatur und einem Satz von Standardwerten. Weitere Informationen finden Sie unter Gewusst [wie: Definieren des Typdeskriptors für einen Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

 Wenn Sie das Projekt ausführen, werden Methoden Instanzen in einer Dropdown Liste oberhalb der SharePoint-Liste angezeigt. Benutzer können Methoden Instanzen auswählen, um die Daten anzuzeigen.

 Um der Methoden Instanz Standardwerte hinzuzufügen, müssen Sie den XML-Code des Modells direkt ändern. Weitere Informationen finden Sie unter [DefaultValue](/previous-versions/office/developer/sharepoint-2010/ee559319(v=office.14)).

## <a name="add-filter-descriptors"></a>Filter Deskriptoren hinzufügen
 Consumer des Modells möchten möglicherweise Instanzen einer Entität abrufen, die bestimmten Kriterien entsprechen. Um diese Funktionalität zu aktivieren, können Sie einer Methode einen Filter Deskriptor hinzufügen. Filter Deskriptoren ermöglichen modellconsumern das Filtern von methodenresultsets, indem vor der Ausführung Werte an Methoden übergeben werden. Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen von Filter Parametern zu Vorgängen zum Einschränken von Instanzen vom externen System](/previous-versions/office/developer/sharepoint-2010/ee554889(v=office.14)).

 SharePoint bietet mehrere Features, die es Benutzern ermöglichen, Filter Werte bereitzustellen. Beispielsweise Webparts Geschäftsdaten ein Filter Textfeld bereitstellen. Benutzer können die Daten in einer Liste einschränken, indem Sie einen Wert in das Textfeld eingeben. Weitere Informationen zum Hinzufügen eines Filter Deskriptors zu einer Methode finden Sie unter Gewusst [wie: Hinzufügen eines Filter Deskriptors zu einer Finder-Methode](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md).

### <a name="filter-descriptor-properties"></a>Filter deskriptoreigenschaften
 Sie müssen den Wert der **zugeordneten Typdeskriptoren**, den **Namen** und die **Typeigenschaften** eines Filter Deskriptors festlegen. Alle anderen Eigenschaften sind optional.

 Die zugeordnete **typdeskriptoreigenschaft verknüpft** den Filter Deskriptor mit einem Eingabeparameter. Wenn ein Benutzer einen Filter Wert bereitstellt, übergibt der BDC-Dienst diesen Wert mithilfe des-Eingabe Parameters an die-Methode.

 Die **Type** -Eigenschaft beschreibt das Filter Muster, das Sie verwenden möchten. In SharePoint wirkt sich das Filter Muster, das Sie auswählen, auf den Text aus, der in der Benutzeroberfläche angezeigt wird. Bei einem Vergleichs Filter Muster **wird** der Text beispielsweise als Steuerelement oberhalb eines Geschäftsdaten-Webparts angezeigt. Weitere Informationen zu den einzelnen Filter Mustern finden Sie [unter vom BDC unterstützte Filtertypen](/previous-versions/office/developer/sharepoint-2010/ee556392(v=office.14)).

 Weitere Informationen zu den Eigenschaften eines Filter Deskriptors finden Sie unter [FilterDescriptor](/previous-versions/office/developer/sharepoint-2010/ee557835(v=office.14)).

### <a name="provide-default-values"></a>Angeben von Standardwerten
 In einigen Fällen kann der Benutzer keinen Filter Wert angeben. Sie können einen Standardwert angeben, indem Sie der-Methoden Instanz einen Standardwert hinzufügen oder indem Sie den Standardwert im Code der-Methode festlegen. Weitere Informationen zum Hinzufügen eines Standardwerts zur-Methoden Instanz finden Sie unter [MethodInstance](/previous-versions/office/developer/sharepoint-2010/ee556838(v=office.14)). Ein Beispiel für das Festlegen des Standardwerts eines Eingabe Parameters im Code der-Methode finden Sie unter Gewusst [wie: Hinzufügen eines Filter Deskriptors zu einer Finder-Methode](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md).

## <a name="validate-the-model"></a>Überprüfen des Modells
 Sie können das Modell während der Entwicklung überprüfen. Visual Studio identifiziert Probleme, die verhindern können, dass sich das Modell erwartungsgemäß verhält. Diese Probleme werden in der Visual Studio- **Fehlerliste** angezeigt.

 Sie können ein Modell validieren, indem Sie das Kontextmenü für den BDC-Designer öffnen und dann über **prüfen auswählen.** Wenn das Modell Fehler enthält, werden diese in der **Fehlerliste** angezeigt. Sie können den Cursor schnell in den Code verschieben, der einen Fehler enthält, indem Sie auf den Fehler in der Liste doppelklicken. Als Alternative können Sie die Taste **F8** oder **Shift** + **F8** wiederholt auswählen, um die Fehler in der Liste vorwärts oder rückwärts zu durchlaufen.

 Validierungs Fehler können auftreten, wenn die Regeln des Modells auf irgendeine Weise verletzt werden. Wenn z. b. die **IsCollection** -Eigenschaft eines Typdeskriptors auf **true** festgelegt ist, aber keine untergeordneten Typdeskriptoren vorhanden sind, wird ein Validierungs Fehler angezeigt. Möglicherweise müssen Sie auf die Regeln eines BDC-Modells verweisen, um einige Fehler zu verstehen, die in der Visual Studio- **Fehlerliste** angezeigt werden. Weitere Informationen zu den Regeln eines BDC-Modells finden Sie unter [bdcmetadata-Schema](/previous-versions/office/developer/sharepoint-2010/ee556387(v=office.14)).

## <a name="debug-the-solution-that-contains-the-model"></a>Debuggen der Projekt Mappe, die das Modell enthält
 Sie können Ihren Code Debuggen, während Sie jeden beliebigen Code in Visual Studio debuggen. Legen Sie zum Debuggen des Codes Haltepunkte an beliebiger Stelle im Code fest, und starten Sie dann den Debugger. Die SharePoint-Website wird von Visual Studio geöffnet. Erstellen Sie in SharePoint eine Liste oder ein Webpart, das Ihre Geschäftsdaten verwendet. Anschließend können Sie den Code schrittweise durchlaufen. Weitere Informationen zum Debuggen von SharePoint-Projekten finden Sie unter [Problembehandlung von SharePoint-Lösungen](../sharepoint/troubleshooting-sharepoint-solutions.md).

 Sie können auch Code in benutzerdefinierten Assemblys Debuggen, die Sie dem Projekt hinzufügen. Wenn Sie jedoch Code in einer benutzerdefinierten Assembly debuggen möchten, müssen Sie die Assembly dem Projektmappenpaket hinzufügen. Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen und Entfernen zusätzlicher](../sharepoint/how-to-add-and-remove-additional-assemblies.md)Assemblys.

 Weitere Informationen zum Hinzufügen einer benutzerdefinierten Assembly zu Ihrem Projekt finden Sie unter Gewusst [wie: Einschließen einer benutzerdefinierten Assembly in eine BDC-Funktion](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md).

### <a name="configure-bdc-security"></a>Konfigurieren der BDC-Sicherheit
 Möglicherweise müssen Sie Ihre Sicherheitseinstellungen in SharePoint ändern, bevor Sie Ihre Lösung Debuggen können. Um diese Einstellungen zu ändern, öffnen Sie die Anwendung Business Data Connectivity-Dienst auf der Website SharePoint 2010-zentral Administration. Fügen Sie im Dialogfeld **Metadatenspeicher-Berechtigungen festlegen** das Benutzerkonto hinzu, und wählen Sie dann eine der folgenden Optionen aus:

|Aufgabe|Option|
|----------|------------|
|Zum Bereitstellen von Modellen für den BDC-Dienst.|Bearbeiten|
|Zum Erstellen von Listen und Webparts mithilfe externer Inhaltstypen (Entitäten) in Ihrem Modell.|In Clients auswählbar|
|Zum Erstellen, lesen, aktualisieren und Löschen von Entitäts Daten.|Execute|

 Weitere Informationen zu diesen Einstellungen finden Sie [unter Business Data Connectivity-Dienst Verwaltung](/previous-versions/office/sharepoint-server-2010/ee661742(v=office.14)).

 Sie können auch Sicherheits Berechtigungen für einzelne Modelle oder externe Inhaltstypen festlegen. Weitere Informationen zum Festlegen der Sicherheits Berechtigungen für ein Modell finden Sie unter [BDC-Modell Verwaltung](/previous-versions/office/sharepoint-server-2010/ee524073(v=office.14)). Weitere Informationen zum Festlegen der Sicherheits Berechtigungen für einen externen Inhaltstyp finden Sie unter [Verwaltung externer Inhaltstyp](/previous-versions/office/sharepoint-server-2010/ee524076(v=office.14)).

> [!NOTE]
> Verwenden Sie diese Einstellungen, um eine Lösung auf dem lokalen SharePoint-Server zu debuggen. Weitere Informationen zum Konfigurieren von BDC-bezogenen Sicherheitseinstellungen auf der SharePoint-Produktionsumgebung finden Sie [unter Business Data Connectivity Services-Sicherheitsübersicht](/previous-versions/office/sharepoint-server-2010/ee661743(v=office.14)).

### <a name="retract-models-that-become-corrupt"></a>Zurückziehen von Modellen, die beschädigt werden
 Wenn Sie den Debugger zum ersten Mal starten, stellt Visual Studio das gesamte Modell für SharePoint bereit. Danach aktualisiert Visual Studio das Modell in SharePoint mit allen Änderungen, die Sie zwischen bereit Stellungen vornehmen.

 Es kann Situationen geben, in denen Visual Studio das Modell vollständig von SharePoint zurückziehen soll. Ein Modell kann z. b. beschädigt werden.  Um das Modell erneut in SharePoint bereitzustellen, legen Sie die Eigenschaft **Inkrementelles Update** des Modells auf **false** fest, und starten Sie dann den Debugger. Die Eigenschaft **Inkrementelles Update** wird im Fenster **Eigenschaften** angezeigt, wenn Sie den Knoten auswählen, der das Modell im **BDC-Explorer** darstellt. Standardmäßig lautet der Name des Modells **BdcModel1**.

### <a name="change-identifier-names-of-entities-in-the-model"></a>Ändern von Bezeichnernamen von Entitäten im Modell
 Wenn Sie den Namen eines Bezeichners ändern, nachdem Sie das Modell bereitgestellt haben, erhalten Sie möglicherweise einen Bereitstellungs Fehler. Dieser Fehler kann nicht behoben werden, indem Sie die Eigenschaft für das **inkrementelle Update** des Modells auf **false** festlegen. Sie müssen das Modell manuell zurückziehen und die Lösung dann erneut bereitstellen. Weitere Informationen finden Sie unter Problembehandlung bei [SharePoint-Lösungen](../sharepoint/troubleshooting-sharepoint-solutions.md). Sie können diesen Fehler vermeiden, indem Sie die Eigenschaft **Inkrementelles Update** auf **false** festlegen, bevor Sie das Modell anfänglich bereitstellen.

## <a name="locate-documentation-for-bdc-model-elements"></a>Dokumentation für BDC-Modellelemente suchen
 Visual Studio fügt dem Modell für jede Entität, Methode oder jedes andere Element, das Sie erstellen, ein XML-Element hinzu. Element Attribute werden im **Eigenschaften** Fenster als Eigenschaften angezeigt. Informationen zu den Elementen und Attributen, die Visual Studio beim Entwerfen des Modells generiert, finden Sie unter [bdcmetadata-Schema](/previous-versions/office/developer/sharepoint-2010/ee556387(v=office.14)).

## <a name="related-topics"></a>Verwandte Themen

|Titel|Beschreibung|
|-----------|-----------------|
|[Übersicht über die BDC-Modell Entwurfs Tools](../sharepoint/bdc-model-design-tools-overview.md)|Beschreibt die Tools, die Sie verwenden können, um ein Modell für den BDC visuell zu entwerfen.|
|[Gewusst wie: Hinzufügen einer Entität zu einem Modell](../sharepoint/how-to-add-an-entity-to-a-model.md)|Zeigt, wie dem Modell externe Inhaltstypen oder Entitäten hinzugefügt werden.|
|[Gewusst wie: Hinzufügen einer Finder-Methode](../sharepoint/how-to-add-a-finder-method.md)|Zeigt, wie Sie eine Methode hinzufügen, mit der Benutzer eine Liste von Entitäten in einer Liste oder einem Webpart anzeigen können.|
|[Gewusst wie: Hinzufügen einer bestimmten Finder-Methode](../sharepoint/how-to-add-a-specific-finder-method.md)|Zeigt, wie Sie eine Methode hinzufügen, mit der Benutzer die Details einer bestimmten Entität anzeigen können.|
|[Gewusst wie: Hinzufügen einer Creator-Methode](../sharepoint/how-to-add-a-creator-method.md)|Zeigt, wie Sie eine Methode hinzufügen, mit der Benutzerdaten Sätze einer Datenquelle direkt aus einer Liste oder einem Webpart hinzufügen können.|
|[Gewusst wie: Hinzufügen einer Deleter-Methode](../sharepoint/how-to-add-a-deleter-method.md)|Zeigt, wie Sie eine Methode hinzufügen, die Benutzern ermöglicht, Daten aus einer Datenquelle zu entfernen, indem Sie Optionen in der Benutzeroberfläche einer Liste oder einem Webpart verwenden.|
|[Gewusst wie: Hinzufügen einer Updater-Methode](../sharepoint/how-to-add-an-updater-method.md)|Zeigt, wie Sie eine Methode hinzufügen, die es Benutzern ermöglicht, Datensätze in einer Datenquelle direkt aus einer Liste oder einem Webpart zu ändern.|
|[Gewusst wie: Hinzufügen eines Parameters zu einer Methode](../sharepoint/how-to-add-a-parameter-to-a-method.md)|Zeigt, wie Sie das Fenster "Methoden Details" in Visual Studio verwenden, um einer Methode Eingabe-und Rückgabe Parameter hinzuzufügen.|
|[Gewusst wie: Definieren des Typdeskriptors für einen Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)|Zeigt, wie Parameter Datentypen im Modell definiert werden.|
|[Gewusst wie: Definieren einer Methoden Instanz](../sharepoint/how-to-define-a-method-instance.md)|Zeigt, wie Sie eine Instanz einer Methode erstellen, die vom BDC ausgeführt wird.|
|[Gewusst wie: Hinzufügen eines Filter Deskriptors zu einer Finder-Methode](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md)|Zeigt, wie Sie es Benutzern ermöglichen, die Anzahl der von einer Finder-Methode zurückgegebenen Instanzen einzuschränken.|
|[Erstellen einer Assoziation zwischen Entitäten](../sharepoint/creating-an-association-between-entities.md)|Beschreibt, wie Sie Beziehungen zwischen Entitäten im Modell definieren können. Geschäftsdaten Webparts, externe Listen und benutzerdefinierte Anwendungen können diese Daten Beziehungen in einer Benutzeroberfläche (UI) anzeigen.|
|[Gewusst wie: Erstellen einer Zuordnung zwischen Entitäten](../sharepoint/how-to-create-an-association-between-entities.md)|Zeigt, wie Beziehungen zwischen Entitäten im Modell definiert werden.|
|[Exemplarische Vorgehensweise: externe Liste in SharePoint mithilfe von Geschäftsdaten](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)|Enthält Schritt-für-Schritt-Anleitungen, die Ihnen zeigen, wie Sie ein Modell erstellen und testen, in dem Kontakte in einer externen SharePoint-Liste angezeigt werden.|
|[Integrieren von Geschäftsdaten in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)|Bietet eine Übersicht über das Erstellen und Entwerfen von Modellen für den BDC-Dienst.|
