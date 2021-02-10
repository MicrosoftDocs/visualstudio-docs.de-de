---
title: 'Exemplarische Vorgehensweise: Anzeigen von Quick Infos für QuickInfo | Microsoft-Dokumentation'
description: In dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie QuickInfo für Textinhalte anzeigen. QuickInfo zeigt Methoden Signaturen und Beschreibungen für einen Methodennamen an.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - QuickInfo
ms.assetid: 23fb8384-4f12-446f-977f-ce7910347947
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- csharp
- vb
ms.openlocfilehash: 3c07dd32b889a9d75222bc8ff5a245f516fab528
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935923"
---
# <a name="walkthrough-display-quickinfo-tooltips"></a>Exemplarische Vorgehensweise: Anzeigen von Quick Infos
QuickInfo ist eine IntelliSense-Funktion, die Methoden Signaturen und Beschreibungen anzeigt, wenn ein Benutzer den Zeiger auf einen Methodennamen verschiebt. Sie können sprachbasierte Funktionen wie QuickInfo implementieren, indem Sie die Bezeichner definieren, für die QuickInfo-Beschreibungen bereitgestellt werden sollen, und dann eine QuickInfo erstellen, in der der Inhalt angezeigt werden soll. Sie können QuickInfo im Kontext eines sprach Dienstanbieter definieren, oder Sie können eine eigene Dateinamenerweiterung und einen Inhaltstyp definieren und die QuickInfo nur für diesen Typ anzeigen, oder Sie können QuickInfo für einen vorhandenen Inhaltstyp (z. b. "Text") anzeigen. In dieser exemplarischen Vorgehensweise wird gezeigt, wie QuickInfo für den Inhaltstyp "Text" angezeigt wird.

 Im QuickInfo-Beispiel in dieser exemplarischen Vorgehensweise werden die Quick Infos angezeigt, wenn ein Benutzer den Mauszeiger über einen Methodennamen verschiebt. Dieser Entwurf erfordert, dass Sie diese vier Schnittstellen implementieren:

- Quell Schnittstelle

- Quell Anbieter Schnittstelle

- Controller Schnittstelle

- Schnittstelle des Controller Anbieters

  Der Quell-und der Controller Anbieter sind Managed Extensibility Framework Komponenten (MEF-Komponenten), die für den Export der Quell-und Controller Klassen und das Importieren von Diensten und Brokern wie der <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> , der den QuickInfo-Text Puffer erstellt, und der <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> , der die QuickInfo-Sitzung auslöst, verantwortlich sind.

  In diesem Beispiel verwendet die QuickInfo-Quelle eine hart codierte Liste von Methodennamen und Beschreibungen, aber in vollständigen Implementierungen sind der Sprachdienst und die Sprachdokumentation für die Bereitstellung dieses Inhalts verantwortlich.

## <a name="prerequisites"></a>Voraussetzungen
 Ab Visual Studio 2015 müssen Sie das Visual Studio SDK nicht aus dem Download Center installieren. Es ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Erstellen eines MEF-Projekts

### <a name="to-create-a-mef-project"></a>So erstellen Sie ein MEF-Projekt

1. Erstellen Sie ein c#-VSIX-Projekt. (Wählen Sie im Dialogfeld **Neues Projekt** die Option **Visual c#/Erweiterbarkeit** und dann **VSIX-Projekt** aus.) Benennen Sie die Projekt Mappe `QuickInfoTest` .

2. Fügen Sie dem Projekt eine Editor-Klassifizierungs Element Vorlage hinzu. Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einer Editor-Element Vorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Löschen Sie die vorhandenen Klassendateien.

## <a name="implement-the-quickinfo-source"></a>Implementieren der QuickInfo-Quelle
 Die QuickInfo-Quelle ist dafür verantwortlich, den Satz von bezeichern und deren Beschreibungen zu erfassen und den Inhalt dem QuickInfo-Text Puffer hinzuzufügen, wenn einer der Bezeichner gefunden wird. In diesem Beispiel werden die Bezeichner und ihre Beschreibungen soeben im quellkonstruktor hinzugefügt.

#### <a name="to-implement-the-quickinfo-source"></a>So implementieren Sie die QuickInfo-Quelle

1. Fügen Sie eine Klassendatei hinzu, und nennen Sie sie `TestQuickInfoSource`.

2. Fügen Sie einen Verweis auf *Microsoft. VisualStudio. Language. IntelliSense* hinzu.

3. Fügen Sie die folgenden Importe hinzu.

     [!code-vb[VSSDKQuickInfoTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_1.vb)]
     [!code-csharp[VSSDKQuickInfoTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_1.cs)]

4. Deklarieren Sie eine Klasse <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> , die implementiert, und benennen Sie Sie `TestQuickInfoSource` .

     [!code-vb[VSSDKQuickInfoTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_2.vb)]
     [!code-csharp[VSSDKQuickInfoTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_2.cs)]

5. Fügen Sie Felder für den QuickInfo-Quell Anbieter, den Text Puffer und einen Satz von Methodennamen und Methoden Signaturen hinzu. In diesem Beispiel werden die Methodennamen und Signaturen im- `TestQuickInfoSource` Konstruktor initialisiert.

     [!code-vb[VSSDKQuickInfoTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_3.vb)]
     [!code-csharp[VSSDKQuickInfoTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_3.cs)]

6. Fügen Sie einen Konstruktor hinzu, der den QuickInfo-Quell Anbieter und den Text Puffer festlegt und den Satz von Methodennamen und Methoden Signaturen und Beschreibungen auffüllt.

     [!code-vb[VSSDKQuickInfoTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_4.vb)]
     [!code-csharp[VSSDKQuickInfoTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_4.cs)]

7. Implementieren Sie die <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A>-Methode. In diesem Beispiel findet die-Methode das aktuelle Wort oder das vorherige Wort, wenn sich der Cursor am Ende einer Zeile oder eines Text Puffers befindet. Wenn es sich bei dem Wort um einen der Methodennamen handelt, wird dem QuickInfo-Inhalt die Beschreibung für den Namen der Methode hinzugefügt.

     [!code-vb[VSSDKQuickInfoTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_5.vb)]
     [!code-csharp[VSSDKQuickInfoTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_5.cs)]

8. Sie müssen auch eine verwerfen ()-Methode implementieren, da Folgendes <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> implementiert <xref:System.IDisposable> :

     [!code-vb[VSSDKQuickInfoTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_6.vb)]
     [!code-csharp[VSSDKQuickInfoTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_6.cs)]

## <a name="implement-a-quickinfo-source-provider"></a>Implementieren eines QuickInfo-Quell Anbieters
 Der Anbieter der QuickInfo-Quelle dient in erster Linie dazu, sich selbst als MEF-Komponenten Teil zu exportieren und die QuickInfo-Quelle zu instanziieren. Da es sich um einen MEF-Komponenten Teil handelt, kann er andere MEF-Komponenten Teile importieren.

#### <a name="to-implement-a-quickinfo-source-provider"></a>So implementieren Sie einen QuickInfo-Quell Anbieter

1. Deklarieren Sie einen QuickInfo-Quell Anbieter mit dem Namen, der `TestQuickInfoSourceProvider` implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider> , und exportieren Sie ihn mit <xref:Microsoft.VisualStudio.Utilities.NameAttribute> der QuickInfo-Quelle "QuickInfo", einer <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> von "Before =" Default "und <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> " Text ".

     [!code-vb[VSSDKQuickInfoTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_7.vb)]
     [!code-csharp[VSSDKQuickInfoTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_7.cs)]

2. Importieren Sie zwei Editor Dienste <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> und <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> als Eigenschaften von `TestQuickInfoSourceProvider` .

     [!code-vb[VSSDKQuickInfoTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_8.vb)]
     [!code-csharp[VSSDKQuickInfoTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_8.cs)]

3. Implementieren <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A> Sie, um einen neuen zurückzugeben `TestQuickInfoSource` .

     [!code-vb[VSSDKQuickInfoTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_9.vb)]
     [!code-csharp[VSSDKQuickInfoTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_9.cs)]

## <a name="implement-a-quickinfo-controller"></a>Implementieren eines QuickInfo-Controllers
 QuickInfo-Controller legen fest, wann QuickInfo angezeigt wird. In diesem Beispiel wird QuickInfo angezeigt, wenn sich der Zeiger über einem Wort befindet, das einem der Methodennamen entspricht. Der QuickInfo-Controller implementiert einen Mauszeiger-Ereignishandler, der eine QuickInfo-Sitzung auslöst.

### <a name="to-implement-a-quickinfo-controller"></a>So implementieren Sie einen QuickInfo-Controller

1. Deklarieren Sie eine Klasse <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> , die implementiert, und benennen Sie Sie `TestQuickInfoController` .

     [!code-vb[VSSDKQuickInfoTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_10.vb)]
     [!code-csharp[VSSDKQuickInfoTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_10.cs)]

2. Fügen Sie private Felder für die Textansicht, die in der Textansicht dargestellten Text Puffer, die QuickInfo-Sitzung und den QuickInfo-Controller Anbieter hinzu.

     [!code-vb[VSSDKQuickInfoTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_11.vb)]
     [!code-csharp[VSSDKQuickInfoTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_11.cs)]

3. Fügen Sie einen Konstruktor hinzu, der die Felder festlegt und den Mauszeiger-Bewegungs Ereignishandler hinzufügt.

     [!code-vb[VSSDKQuickInfoTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_12.vb)]
     [!code-csharp[VSSDKQuickInfoTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_12.cs)]

4. Fügen Sie den Mauszeiger-Ereignishandler hinzu, der die QuickInfo-Sitzung auslöst.

     [!code-vb[VSSDKQuickInfoTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_13.vb)]
     [!code-csharp[VSSDKQuickInfoTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_13.cs)]

5. Implementieren Sie die- <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A> Methode, sodass der Mauszeiger-Ereignishandler entfernt wird, wenn der Controller von der Textansicht getrennt wird.

     [!code-vb[VSSDKQuickInfoTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_14.vb)]
     [!code-csharp[VSSDKQuickInfoTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_14.cs)]

6. Implementieren Sie die <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A> -Methode und die- <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A> Methode als leere Methoden für dieses Beispiel.

     [!code-vb[VSSDKQuickInfoTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_15.vb)]
     [!code-csharp[VSSDKQuickInfoTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_15.cs)]

## <a name="implementing-the-quickinfo-controller-provider"></a>Implementieren des QuickInfo-Controller Anbieters
 Der Anbieter des QuickInfo-Controllers dient in erster Linie dazu, sich selbst als MEF-Komponenten Teil zu exportieren und den QuickInfo-Controller zu instanziieren. Da es sich um einen MEF-Komponenten Teil handelt, kann er andere MEF-Komponenten Teile importieren.

### <a name="to-implement-the-quickinfo-controller-provider"></a>So implementieren Sie den QuickInfo-Controller Anbieter

1. Deklarieren Sie eine Klasse mit dem Namen, `TestQuickInfoControllerProvider` die implementiert <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider> , und exportieren Sie Sie mit einem <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "QuickInfo-Controller" und einem <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> von "Text":

     [!code-vb[VSSDKQuickInfoTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_16.vb)]
     [!code-csharp[VSSDKQuickInfoTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_16.cs)]

2. Importieren Sie <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> als Eigenschaft.

     [!code-vb[VSSDKQuickInfoTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_17.vb)]
     [!code-csharp[VSSDKQuickInfoTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_17.cs)]

3. Implementieren Sie die- <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A> Methode, indem Sie den QuickInfo-Controller instanziieren.

     [!code-vb[VSSDKQuickInfoTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_18.vb)]
     [!code-csharp[VSSDKQuickInfoTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_18.cs)]

## <a name="build-and-test-the-code"></a>Erstellen und Testen des Codes
 Um diesen Code zu testen, erstellen Sie die quickinfotest-Projekt Mappe, und führen Sie Sie in der experimentellen Instanz aus.

### <a name="to-build-and-test-the-quickinfotest-solution"></a>So erstellen und testen Sie die QuickInfo Test-Projekt Mappe

1. Erstellen Sie die Projektmappe.

2. Wenn Sie dieses Projekt im Debugger ausführen, wird eine zweite Instanz von Visual Studio gestartet.

3. Erstellen Sie eine Textdatei, und geben Sie Text ein, der die Wörter "Add" und "Subtract" enthält.

4. Bewegen Sie den Mauszeiger über eines der Vorkommen von "Add". Die Signatur und die Beschreibung der `add` Methode sollten angezeigt werden.

## <a name="see-also"></a>Weitere Informationen
- [Exemplarische Vorgehensweise: Verknüpfen eines Inhaltstyps mit einer Dateinamenerweiterung](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
