---
title: Herunterladen von Assemblys nach Bedarf mithilfe des Designers
description: Erfahren Sie, wie Sie bestimmte Assemblys in der ClickOnce-Anwendung mit dem-Designer als optional markieren und Sie herunterladen, wenn Sie vom Common Language Runtime benötigt werden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- assemblies, downloading [ClickOnce]
- Windows applications, ClickOnce deployments
- ClickOnce deployment, on-demand download
- on-demand assemblies, ClickOnce
ms.assetid: 59a0dd5f-1cab-4f2f-b780-0ab7399905d5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0c2ced89c73d39fecb6b6cee80a8fddb0a8c2391
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917334"
---
# <a name="walkthrough-download-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer"></a>Exemplarische Vorgehensweise: Herunterladen von Assemblys bei Bedarf mit der ClickOnce-Bereitstellungs-API mit
Standardmäßig werden alle Assemblys, die in einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendung enthalten sind, beim ersten Ausführen der Anwendung heruntergeladen. Allerdings gibt es möglicherweise Teile der Anwendung, die von einer begrenzten Anzahl von Benutzern verwendet werden. In diesem Fall soll eine Assembly erst heruntergeladen werden, wenn eine der in ihr definierten Typen erstellt wird. Die folgende exemplarische Vorgehensweise bietet Hinweise zum Markieren bestimmter Assemblys in der Anwendung als „optional“ sowie zum Herunterladen dieser Assemblys, indem Sie Klassen im <xref:System.Deployment.Application> -Namespace verwenden, wenn diese von der Common Language Runtime angefordert werden.

> [!NOTE]
> Die Anwendung muss mit voller Vertrauenswürdigkeit ausgeführt werden, um dieses Verfahren zu verwenden.

> [!NOTE]
> Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Reset settings (Zurücksetzen der Einstellungen)](../ide/environment-settings.md#reset-settings).

## <a name="create-the-projects"></a>Erstellen der Projekte

### <a name="to-create-a-project-that-uses-an-on-demand-assembly-with-visual-studio"></a>So erstellen Sie ein Projekt, das eine bedarfsabhängige Assembly mit Visual Studio verwendet

1. Erstellen Sie ein neues Windows Forms-Projekt in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Zeigen Sie im Menü **Datei** auf **Hinzufügen**, und klicken Sie dann auf **Neues Projekt**. Wählen Sie ein **Klassenbibliothek** -Projekt im Dialogfeld aus, und nennen Sie es `ClickOnceLibrary`.

   > [!NOTE]
   > In Visual Basic empfiehlt es sich, dass Sie die Projekteigenschaften bearbeiten, um den Stammnamespace für dieses Projekt zu `Microsoft.Samples.ClickOnceOnDemand` oder dem Namespace Ihrer Wahl zu ändern. Der Einfachheit halber befinden sich die beiden Projekte in dieser exemplarischen Vorgehensweise im selben Namespace.

2. Definieren Sie eine Klasse mit dem Namen `DynamicClass` mit einer einzelnen Eigenschaft mit dem Namen `Message`.

    [!code-vb[ClickOnceLibrary#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_1.vb)]
    [!code-csharp[ClickOnceLibrary#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_1.cs)]

3. Wählen Sie das Windows Forms-Projekt im **Projektmappen-Explorer** aus. Fügen Sie einen Verweis zu einer <xref:System.Deployment.Application> -Assembly und einen Projektverweis zum `ClickOnceLibrary` -Projekt hinzu.

   > [!NOTE]
   > In Visual Basic empfiehlt es sich, dass Sie die Projekteigenschaften bearbeiten, um den Stammnamespace für dieses Projekt zu `Microsoft.Samples.ClickOnceOnDemand` oder dem Namespace Ihrer Wahl zu ändern. Der Einfachheit halber befinden sich die beiden Projekte in dieser exemplarischen Vorgehensweise im selben Namespace.

4. Klicken Sie mit der rechten Maustaste auf das Formular, klicken Sie anschließend auf **Code anzeigen** , und fügen Sie dem Formular den folgenden Verweis hinzu.

    [!code-csharp[ClickOnceOnDemand#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_2.cs)]
    [!code-vb[ClickOnceOnDemand#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_2.vb)]

5. Fügen Sie den folgenden Code hinzu, um diese Assembly bei Bedarf herunterzuladen. Dieser Code zeigt, wie dem Gruppennamen mithilfe einer generischen <xref:System.Collections.DictionaryBase.Dictionary%2A> -Klasse ein Satz von Assemblys zugeordnet wird. Da wir nur eine einzige Assembly in dieser exemplarischen Vorgehensweise herunterladen, ist nur eine Assembly in unserer Gruppe enthalten. In einer echten Anwendung würden Sie wahrscheinlich alle Assemblys herunterladen, die gleichzeitig mit einer einzelnen Funktion verknüpft sind. Mit der Zuordnungstabelle können Sie diesen Schritt leicht ausführen, indem Sie alle DLLs zuordnen, die zu einer Funktion mit einem Downloadgruppennamen gehören.

    [!code-csharp[ClickOnceOnDemand#2](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_3.cs)]
    [!code-vb[ClickOnceOnDemand#2](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_3.vb)]

6. Klicken Sie im Menü **Ansicht** auf **Toolbox**. Ziehen Sie eine <xref:System.Windows.Forms.Button> aus der **Toolbox** auf das Formular. Doppelklicken Sie auf die Schaltfläche, und fügen Sie dem <xref:System.Windows.Forms.Control.Click> -Ereignishandler den folgenden Code hinzu.

    [!code-csharp[ClickOnceOnDemand#3](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_4.cs)]
    [!code-vb[ClickOnceOnDemand#3](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_4.vb)]

## <a name="mark-assemblies-as-optional"></a>Assemblys als optional markieren

### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-visual-studio"></a>So markieren Sie Assemblys in der ClickOnce-Anwendung mithilfe von Visual Studio als optional

1. Klicken Sie im Windows Forms-Projekt in den **Projektmappen-Explorer** , und klicken Sie auf **Eigenschaften**. Wählen Sie die Registerkarte **Veröffentlichen** aus.

2. Klicken Sie auf die Schaltfläche **Anwendungsdateien** .

3. Suchen Sie das Listing für *ClickOnceLibrary.dll*. Legen Sie das Dropdownfeld **Veröffentlichungsstatus** auf **Einschließen** fest.

4. Erweitern Sie das Dropdownfeld **Gruppe** , und wählen Sie **Neu** aus. Geben Sie den Namen `ClickOnceLibrary` als den neuen Gruppennamen ein.

5. Setzen Sie die Veröffentlichung Ihrer Anwendung wie unter Gewusst [wie: Veröffentlichen einer ClickOnce-Anwendung mit dem](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)Webpublishing-Assistenten beschrieben fort.

### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-manifest-generation-and-editing-tool--graphical-client-mageuiexe"></a>So markieren Sie Assemblys in der ClickOnce-Anwendung mithilfe von Manifest Generation and Editing Tool— Graphical Client (MageUI.exe) als optional

1. Erstellen Sie Ihre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Manifeste wie unter Exemplarische Vorgehensweise [: Manuelles Bereitstellen einer ClickOnce-Anwendung](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)beschrieben.

2. Wählen Sie vor dem Schließen von MageUI.exe die Registerkarte aus, die das Anwendungsmanifest Ihrer Bereitstellung enthält, und wählen Sie auf der Registerkarte die Registerkarte **Dateien** aus.

3. Suchen Sie ClickOnceLibrary.dll in der Liste der Anwendungsdateien, und legen Sie die Spalte **Dateityp** auf **Keine** fest. Geben Sie für die Spalte **Gruppe**`ClickOnceLibrary.dll`ein.

## <a name="test-the-new-assembly"></a>Testen der neuen Assembly

So testen Sie die bedarfsabhängige Assembly:

1. Starten Sie Ihre Anwendung, die mit [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]bereitgestellt wurde.

2. Wenn das Hauptformular angezeigt wird, drücken Sie die <xref:System.Windows.Forms.Button>. Daraufhin sollte eine Zeichenfolge in einem Meldungsfeldfenster angezeigt werden, die „Hello, World!“ lautet.

## <a name="see-also"></a>Weitere Informationen

- <xref:System.Deployment.Application.ApplicationDeployment>
