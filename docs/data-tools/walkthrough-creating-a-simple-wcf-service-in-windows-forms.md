---
title: Erstellen eines einfachen WCF-Dienstanbieter in Windows Forms
description: Erstellen Sie in dieser exemplarischen Vorgehensweise einen Windows Communication Foundation (WCF)-Dienst in Visual Studio, testen Sie ihn, und greifen Sie dann über eine Windows Forms Anwendung darauf zu.
ms.date: 11/04/2016
ms.custom: SEO-VS-2020
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WCF, walkthrough [Visual Studio]
- WCF, Visual Studio tools for
- WCF services
- WCF services, walkthrough
ms.assetid: 5fef1a64-27a4-4f10-aa57-29023e28a2d6
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 215ae1409c36417526bb1362f0029029ed95e801
ms.sourcegitcommit: 72a49c10a872ab45ec6c6d7c4ac7521be84526ff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2020
ms.locfileid: "94998134"
---
# <a name="walkthrough-create-a-simple-wcf-service-in-windows-forms"></a>Exemplarische Vorgehensweise: Erstellen eines einfachen WCF-Dienstanbieter in Windows Forms

In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie ein Simple Windows Communication Foundation (WCF)-Dienst erstellt, getestet und dann über eine Windows Forms Anwendung darauf zugegriffen wird.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="create-a-service"></a>Erstellen von Diensten

1. Öffnen Sie Visual Studio.

::: moniker range="vs-2017"

2. Klicken Sie im Menü **Datei** auf **Neu** > **Projekt**.

3. Erweitern Sie im Dialogfeld **Neues Projekt** den Knoten **Visual Basic** oder **Visual c#** , und wählen Sie **WCF** und dann **WCF-Dienst Bibliothek** aus.

4. Klicken Sie auf **OK**, um das Projekt zu erstellen.

   ![Das WCF-Dienstbibliotheksprojekt](../data-tools/media/wcf1.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. Wählen Sie im Startfenster **Neues Projekt erstellen** aus.

3. Geben Sie im Suchfeld auf der Seite **Neues Projekt erstellen** die **WCF-Dienst Bibliothek** ein. Wählen Sie entweder die c#-oder Visual Basic Vorlage für die **WCF-Dienst Bibliothek** aus, und klicken Sie dann auf **weiter**.

   ![Neues WCF-Dienst Bibliotheksprojekt in Visual Studio 2019 erstellen](media/vs-2019/create-new-wcf-service-library.png)

   > [!TIP]
   > Wenn keine Vorlagen angezeigt werden, müssen Sie möglicherweise die **Windows Communication Foundation** Komponente von Visual Studio installieren. Wählen Sie **Weitere Tools und Features installieren** aus, um Visual Studio-Installer zu öffnen. Wählen Sie die Registerkarte **einzelne Komponenten** aus, Scrollen Sie nach unten zu **Entwicklungsaktivitäten**, und wählen Sie dann **Windows Communication Foundation** aus. Klicken Sie auf **Ändern**.

4. Klicken Sie auf der Seite **Neues Projekt konfigurieren** auf **Erstellen**.

::: moniker-end

   > [!NOTE]
   > Dadurch wird ein funktionierender Dienst erstellt, der getestet und aufgerufen werden kann. Die folgenden beiden Schritte veranschaulichen, wie Sie die Standardmethode ändern können, um einen anderen Datentyp zu verwenden. In einer echten Anwendung würden Sie dem Dienst auch Ihre eigenen Funktionen hinzufügen.

5. Doppelklicken Sie in **Projektmappen-Explorer** auf **IService1. vb** oder **IService1.cs**.

   ![Die Datei "IService1"](../data-tools/media/wcf2.png)

   Suchen Sie die folgende Zeile:

   [!code-csharp[WCFWalkthrough#4](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_1.cs)]
   [!code-vb[WCFWalkthrough#4](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_1.vb)]

   Ändern Sie den Typ für den `value` Parameter in Zeichenfolge:

   [!code-csharp[WCFWalkthrough#1](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_2.cs)]
   [!code-vb[WCFWalkthrough#1](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_2.vb)]

   Beachten Sie im obigen Code die `<OperationContract()>`- oder `[OperationContract]`-Attribute. Diese Attribute sind für jede Methode erforderlich, die vom Dienst zur Verfügung gestellt wird.

6. Doppelklicken Sie in **Projektmappen-Explorer** auf **Service1. vb** oder **Service1.cs**.

   ![Die Datei "Service1"](../data-tools/media/wcf3.png)

   Suchen Sie die folgende Zeile:

   [!code-vb[WCFWalkthrough#5](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_3.vb)]
   [!code-csharp[WCFWalkthrough#5](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_3.cs)]

   Ändern Sie den Typ für den `value` Parameter in Zeichenfolge:

   [!code-csharp[WCFWalkthrough#2](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_4.cs)]
   [!code-vb[WCFWalkthrough#2](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_4.vb)]

## <a name="test-the-service"></a>Testen des Diensts

1. Drücken Sie **F5**, um den Dienst auszuführen. Ein **WCF-Test Client** Formular wird angezeigt, und der Dienst wird geladen.

2. Doppelklicken Sie im **WCF-Testclient**-Formular auf die **GetData()**-Methode unter **IService1**. Die Registerkarte **GetData** wird angezeigt.

     ![Die GetData-&#40;&#41; Methode](../data-tools/media/wcf4.png)

3. Wählen Sie im Feld **Anforderung** das Feld **Wert** aus, und geben Sie `Hello` ein.

     ![Das Wertfeld](../data-tools/media/wcf5.png)

4. Klicken Sie auf die Schaltfläche **Aufrufen**. Wenn ein Dialogfeld mit einer **Sicherheitswarnung** angezeigt wird, klicken Sie auf **OK**. Das Ergebnis wird im Feld **Antwort** angezeigt.

     ![Das Ergebnis im Feld "Antwort"](../data-tools/media/wcf6.png)

5. Klicken Sie im Menü **Datei** auf **Beenden**, um das Testformular zu schließen.

## <a name="access-the-service"></a>Auf den Dienst zugreifen

### <a name="reference-the-wcf-service"></a>Verweisen auf den WCF-Dienst

1. Zeigen Sie im Menü **Datei** auf **Hinzufügen** , und klicken Sie dann auf **Neues Projekt**.

2. Erweitern Sie im Dialogfeld **Neues Projekt** den Knoten **Visual Basic** oder **Visual c#** , wählen Sie **Windows** aus, und wählen Sie dann **Windows Forms Anwendung** aus. Klicken Sie auf **OK**, um das Projekt zu öffnen.

     ![Windows Forms-Anwendungsprojekt](../data-tools/media/wcf7.png)

3. Klicken Sie mit der rechten Maustaste auf **WindowsApplication1** und dann auf **Dienstverweis hinzufügen**. Das Dialogfeld **Dienstverweis hinzufügen** wird angezeigt.

4. Klicken Sie im Dialogfeld **Dienstverweis hinzufügen** auf **Ermitteln**.

     ![Das Dialogfeld "Dienstverweis hinzufügen"](../data-tools/media/wcf8.png)

     **Service1** wird im Bereich **Dienste** angezeigt.

5. Klicken Sie auf **OK**, um den Dienstverweis hinzuzufügen.

### <a name="build-a-client-application"></a>Erstellen Sie eine Clientanwendung

1. Doppelklicken Sie im **Projektmappen-Explorer** auf **Form1.vb** oder **Form1.cs**, um den Windows Forms-Designer zu öffnen, wenn er nicht bereits geöffnet ist.

2. Ziehen Sie aus der **Toolbox** ein `TextBox`-Steuerelement, ein `Label`-Steuerelement und ein `Button`-Steuerelement auf das Formular.

     ![Hinzufügen von Steuerelementen zum Formular](../data-tools/media/wcf9.png)

3. Doppelklicken Sie auf `Button`, und fügen Sie dem `Click`-Ereignishandler den folgenden Code hinzu:

     [!code-csharp[WCFWalkthrough#3](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_5.cs)]
     [!code-vb[WCFWalkthrough#3](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_5.vb)]

4. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **WindowsApplication1**, und klicken Sie auf **Als Startprojekt festlegen**.

5. Drücken Sie **F5** , um das Projekt auszuführen. Geben Sie Text ein, und klicken Sie auf die Schaltfläche. Die Bezeichnung zeigt "Sie haben Sie eingegeben:" und zeigt den Text an, den Sie eingegeben haben.

     ![Das Formular mit dem Ergebnis](../data-tools/media/wcf10.png)

## <a name="see-also"></a>Weitere Informationen

- [Windows Communication Foundation Dienste und WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
