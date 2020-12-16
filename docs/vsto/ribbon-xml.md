---
title: Ribbon XML
description: Erfahren Sie, wie Sie das Menüband (XML)-Element verwenden, wenn Sie das Menüband auf eine Weise anpassen möchten, die nicht vom Element "Menüband (visueller Designer)" unterstützt wird.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VSTO.Ribbon.RibbonXMLItem
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom Ribbon, XML
- customizing the Ribbon, XML
- Ribbon [Office development in Visual Studio], XML
- callback methods
- custom Ribbon, displaying
- custom Ribbon, defining behavior
- XML [Office development in Visual Studio], Ribbon
- customizing the Ribbon, defining behavior
- Ribbon [Office development in Visual Studio], customizing
- customizing the Ribbon, displaying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1c9e1cf4c6af266495b3d85d96aa8cce1697cca7
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528415"
---
# <a name="ribbon-xml"></a>Ribbon XML
  Das Element "Menüband (XML)" ermöglicht das Anpassen eines Menübands mithilfe von XML. Verwenden Sie das Element Menüband (XML), wenn Sie das Menüband auf eine Weise anpassen möchten, die vom Element Menüband (visueller Designer) nicht unterstützt wird. Einen Vergleich dazu, was Sie mit den einzelnen Elementen tun können, finden Sie unter [Übersicht über das Menüband](../vsto/Ribbon-overview.md).

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

## <a name="add-a-ribbon-xml-item-to-a-project"></a>Hinzufügen eines Elements "Menüband (XML)" zu einem Projekt
 Können Sie einem Office-Projekt ein Element **Menüband (XML)** über das Dialogfeld **Neues Element hinzufügen** hinzufügen. Visual Studio fügt die folgenden Dateien automatisch hinzu:

- Eine Menüband-XML-Datei. Diese Datei definiert die Menüband-Benutzeroberfläche (User Interface, UI). Verwenden Sie diese Datei, um Benutzeroberflächenelemente (z. B. Registerkarten, Gruppen und Steuerelemente) hinzuzufügen. Weitere Informationen finden Sie unter [Menüband-XML-Dateireferenz](#RibbonDescriptorFile) weiter unten in diesem Thema.

- Eine Menüband-Codedatei. Diese Datei enthält die *Klasse "Menüband"*. Diese Klasse trägt den Namen, den Sie im Dialogfeld **Neues Element hinzufügen** für das Element **Menüband (XML)** angeben. Microsoft Office Anwendungen verwenden eine Instanz dieser Klasse, um das benutzerdefinierte Menüband zu laden. Weitere Informationen finden Sie unter Übersicht über die [Menüband-Klasse](#RibbonExtensionClass) weiter unten in diesem Thema.

  Standardmäßig fügen diese Dateien der Registerkarte **Add-ins** im Menüband eine benutzerdefinierte Gruppe hinzu.

## <a name="display-the-custom-ribbon-in-a-microsoft-office-application"></a>Anzeigen des benutzerdefinierten Menübands in einer Microsoft Office Anwendung
 Nachdem Sie dem Projekt ein **Menüband (XML)** -Element hinzugefügt haben, müssen Sie der **ThisAddIn**-, **ThisWorkbook**-oder **ThisDocument** -Klasse Code hinzufügen, der die-Methode überschreibt `CreateRibbonExtensibilityObject` und die Menüband-XML-Klasse an die Office-Anwendung zurückgibt.

 Der folgende Codebeispiel setzt die Methode `CreateRibbonExtensibilityObject` außer Kraft und gibt eine Klasse "Menüband-XML" namens "MyRibbon" zurück.

 [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
 [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]

## <a name="define-the-behavior-of-the-custom-ribbon"></a>Definieren des Verhaltens des benutzerdefinierten Menübands
 Sie können auf Benutzeraktionen (z. b. das Klicken auf eine Schaltfläche im Menüband) reagieren, indem Sie *Rückruf Methoden* erstellen. Rückrufmethoden ähneln Ereignissen in Windows Forms-Steuerelementen, werden jedoch durch ein Attribut im XML-Code des Benutzeroberflächenelements identifiziert. Sie schreiben Methoden in der Klasse "Menüband", und ein Steuerelement ruft die Methode auf, die den gleichen Namen wie der Attributwert aufweist. Beispielsweise können Sie eine Rückruf Methode erstellen, die aufgerufen wird, wenn ein Benutzer auf eine Schaltfläche auf dem Menüband klickt. Zum Erstellen einer Rückrufmethode sind zwei Schritte erforderlich:

- Zuweisen eines Attributs zu einem Steuerelement in der Menüband-XML-Datei, die eine Rückrufmethode in Ihrem Code identifiziert.

- Definieren der Rückrufmethode in der Klasse "Menüband".

> [!NOTE]
> Für Outlook ist ein zusätzlicher Schritt erforderlich. Weitere Informationen finden Sie unter [Anpassen eines Menübands für Outlook](../vsto/customizing-a-ribbon-for-outlook.md).

 Eine exemplarische Vorgehensweise, die das Automatisieren einer Anwendung über das Menüband veranschaulicht, finden Sie unter Exemplarische Vorgehensweise [: Erstellen einer benutzerdefinierten Registerkarte mit Menüband-XML](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md).

### <a name="assign-callback-methods-to-controls"></a>Zuweisen von Rückruf Methoden zu Steuerelementen
 Wenn Sie einem Steuerelement eine Rückrufmethode in der Menüband-XML-Datei zuzuweisen möchten, fügen Sie ein Attribut hinzu, das den Typ der Rückrufmethode und den Namen der Methode angibt. Das folgende Element definiert z. B. eine Umschaltfläche, die über eine **onAction** -Rückrufmethode mit dem Namen `OnToggleButton1`.

```xml
<toggleButton id="toggleButton1" onAction="OnToggleButton1" />
```

 **onAction** wird aufgerufen, wenn der Benutzer die einem bestimmten Steuerelement zugeordnete Hauptaufgabe ausführt. Die **onAction** -Rückrufmethode einer Umschaltfläche wird z. B. aufgerufen, wenn der Benutzer auf die Schaltfläche klickt.

 Die Methode, die Sie im Attribut angeben, kann einen beliebigen Namen besitzen. Er muss jedoch mit dem Namen der Methode übereinstimmen, den Sie in der Menüband-Codedatei definieren.

 Es gibt viele verschiedene Typen von Rückrufmethoden, die Sie Menüband-Steuerelementen zuweisen können. Eine umfassende Liste der für jedes Steuerelement verfügbaren Rückruf Methoden finden Sie im technischen Artikel [Anpassen der Menüband-Benutzeroberfläche von Office (2007) für Entwickler (Teil 3 von 3)](/previous-versions/office/developer/office-2007/aa722523(v=office.12)).

### <a name="define-callback-methods"></a><a name="CallBackMethods"></a> Definieren von Rückruf Methoden
 Definieren Sie die Rückrufmethoden in der Klasse "Menüband" in der Menüband-Codedatei. Für eine Rückrufmethode gelten mehrere Anforderungen:

- Sie muss als öffentlich deklariert werden.

- Ihr Name muss mit dem Namen einer Rückrufmethode übereinstimmen, die Sie einem Steuerelement in der Menüband-XML-Datei zugewiesen haben.

- Ihre Signatur muss mit die Signatur eines Typs einer Rückrufmethode übereinstimmen, die für das zugehörige Menüband-Steuerelement verfügbar ist.

  Eine umfassende Liste der Rückruf Methoden Signaturen für Menüband-Steuerelemente finden Sie im technischen Artikel [Anpassen der Menüband-Benutzeroberfläche von Office (2007) für Entwickler (Teil 3 von 3)](/previous-versions/office/developer/office-2007/aa722523(v=office.12)). Visual Studio bietet keine IntelliSense-Unterstützung für Rückrufmethoden, die Sie in der Menüband-Codedatei erstellen. Wenn Sie eine Rückrufmethode erstellen, die nicht mit einer gültigen Signatur übereinstimmt, wird der Code zwar kompiliert. Es geschieht jedoch nichts, wenn der Benutzer auf das Steuerelement klickt.

  Alle Rückrufmethoden verfügen über einen Parameter <xref:Microsoft.Office.Core.IRibbonControl> , der das Steuerelement darstellt, das die Methode aufgerufen hat. Sie können diesen Parameter verwenden, um die gleiche Rückrufmethode für mehrere Steuerelemente wiederzuverwenden. Das folgende Codebeispiel veranschaulicht eine **onAction** -Rückrufmethode, die verschiedene Aufgaben abhängig davon ausführt, auf welches Steuerelement der Benutzer klickt.

  [!code-csharp[Trin_RibbonOutlookBasic#2](../vsto/codesnippet/CSharp/Trin_RibbonOutlookBasic/Ribbon1.cs#2)]
  [!code-vb[Trin_RibbonOutlookBasic#2](../vsto/codesnippet/VisualBasic/Trin_RibbonOutlookBasic/Ribbon1.vb#2)]

## <a name="ribbon-xml-file-reference"></a><a name="RibbonDescriptorFile"></a> Menüband-XML-Dateireferenz
 Sie können das benutzerdefinierte Menüband definieren, indem Sie der Menüband-XML-Dateielemente und Attribute hinzufügen. Standardmäßig enthält die Menüband-XML-Datei die folgenden XML-Elemente.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<customUI xmlns="http://schemas.microsoft.com/office/2006/01/customui" onLoad="OnLoad">
  <ribbon>
    <tabs>
      <tab idMso="TabAddIns">
        <group id="MyGroup"
               label="My Group">
        </group>
      </tab>
    </tabs>
  </ribbon>
</customUI>
```

 In der folgende Tabelle werden die Standardelemente in der Menüband-XML-Datei beschrieben.

|Element|BESCHREIBUNG|
|-------------|-----------------|
|**customUI**|Stellt das benutzerdefinierte Menüband im VSTO-Add-in-Projekt dar.|
|**Band**|Stellt das Menüband dar.|
|**Tafeln**|Stellt eine Sammlung von Registerkarten des Menübands dar.|
|**Zeche**|Stellt eine einzelne Registerkarte des Menübands dar.|
|**group**|Stellt eine Gruppe von Steuerelementen auf der Registerkarte des Menübands dar.|

 Diese Elemente verfügen über Attribute, die die Darstellung und das Verhalten des benutzerdefinierten Menübands angeben. In der folgende Tabelle werden die Standardattribute in der Menüband-XML-Datei beschrieben.

|Attribut|Übergeordnetes Element|Beschreibung|
|---------------|--------------------|-----------------|
|**onLoad**|**customUI**|Bezeichnet eine Methode, die aufgerufen wird, wenn die Anwendung das Menüband lädt.|
|**idMso**|**Zeche**|Gibt eine integrierte Registerkarte an, die im Menüband angezeigt werden soll.|
|**id**|**group**|Gibt die Gruppe an.|
|**label**|**group**|Gibt den Text an, der für die Gruppe angezeigt wird.|

 Die Standardelemente und -attribute in der Menüband-XML-Datei sind eine kleine Teilmenge der Elemente und Attribute, die verfügbar sind. Eine umfassende Liste der verfügbaren Elemente und Attribute finden Sie im technischen Artikel [Anpassen der Menüband-Benutzeroberfläche von Office (2007) für Entwickler (Teil 2 von 3)](/previous-versions/office/developer/office-2007/aa338199(v=office.12)).

## <a name="ribbon-class-reference"></a><a name="RibbonExtensionClass"></a> Menü bandklasse, Referenz
 Visual Studio generiert die Klasse "Menüband" in der Menüband-Codedatei. Fügen Sie dieser Klasse die Rückruf Methoden für Steuerelemente auf dem Menüband hinzu. Diese Klasse implementiert die <xref:Microsoft.Office.Core.IRibbonExtensibility> -Schnittstelle.

 Die folgende Tabelle beschreibt die Standardmethoden in dieser Klasse.

|Methode|BESCHREIBUNG|
|------------|-----------------|
|`GetCustomUI`|Gibt den Inhalt der Menüband-XML-Datei zurück. Microsoft Office Anwendungen rufen diese Methode auf, um eine XML-Zeichenfolge abzurufen, die die Benutzeroberfläche des benutzerdefinierten Menübands definiert. Diese Methode implementiert die Methode <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> . **Hinweis:** `GetCustomUI` sollte nur implementiert werden, um den Inhalt der Menüband-XML-Datei zurückzugeben. Sie sollte nicht zum Initialisieren des VSTO-Add-Ins verwendet werden.   Insbesondere sollten nicht versuchen, Dialogfelder oder andere Fenster in Ihrer `GetCustomUI` Implementierung anzuzeigen. Andernfalls verhält sich das benutzerdefinierte Menüband möglicherweise nicht ordnungsgemäß. Wenn Sie Code ausführen müssen, der Ihr VSTO-Add-In initialisiert, fügen Sie den Code dem `ThisAddIn_Startup` -Ereignishandler hinzu.|
|`OnLoad`|Weist den Parameter <xref:Microsoft.Office.Core.IRibbonControl> dem Feld `Ribbon` zu. Microsoft Office Anwendungen diese Methode beim Laden des benutzerdefinierten Menübands aufruft. Sie können dieses Feld verwenden, um das benutzerdefinierte Menüband dynamisch zu aktualisieren. Weitere Informationen finden Sie im technischen Artikel [Anpassen der Menüband-Benutzeroberfläche von Office (2007) für Entwickler (Teil 1 von 3)](/previous-versions/office/developer/office-2007/aa338202(v=office.12)).|
|`GetResourceText`|Wird von der Methode `GetCustomUI` aufgerufen, um den Inhalt der Menüband-XML-Datei abzurufen.|

## <a name="see-also"></a>Weitere Informationen
- [Übersicht über Menüband](../vsto/ribbon-overview.md)
- [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit Menüband-XML](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
- [Office-Benutzeroberflächen Anpassung](../vsto/office-ui-customization.md)
