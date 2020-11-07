---
title: Assemblys bei Bedarf herunterladen (ClickOnce-API)
description: Erfahren Sie, wie Sie bestimmte Assemblys in der ClickOnce-Anwendung als optional markieren und Sie herunterladen, wenn Sie vom Common Language Runtime benötigt werden.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- assemblies, downloading [ClickOnce]
- ClickOnce deployment, on-demand download
- on-demand assemblies, ClickOnce
ms.assetid: d20e2789-8621-4806-b5b7-841122da1456
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fb74d7fd5ad388b9b3dc217bae8782b24517c13b
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94349259"
---
# <a name="walkthrough-download-assemblies-on-demand-with-the-clickonce-deployment-api"></a>Exemplarische Vorgehensweise: Bedarfs gesteuertes herunterladen von Assemblys mit der ClickOnce-
Standardmäßig werden alle in einer-Anwendung enthaltenen Assemblys [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] heruntergeladen, wenn die Anwendung zum ersten Mal ausgeführt wird. Allerdings haben Sie möglicherweise Teile der Anwendung, die von einer kleinen Gruppe von Benutzern verwendet werden. In diesem Fall soll eine Assembly erst heruntergeladen werden, wenn eine der in ihr definierten Typen erstellt wird. Die folgende exemplarische Vorgehensweise bietet Hinweise zum Markieren bestimmter Assemblys in der Anwendung als „optional“ sowie zum Herunterladen dieser Assemblys, indem Sie Klassen im <xref:System.Deployment.Application>-Namespace verwenden, wenn diese von der Common Language Runtime (CLR) angefordert werden.

> [!NOTE]
> Die Anwendung muss mit voller Vertrauenswürdigkeit ausgeführt werden, um dieses Verfahren zu verwenden.

## <a name="prerequisites"></a>Voraussetzungen
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie eine der folgenden Komponenten:

- Der Windows SDK. Der Windows SDK kann aus dem Microsoft Download Center heruntergeladen werden.

- Visual Studio.

## <a name="create-the-projects"></a>Erstellen der Projekte

#### <a name="to-create-a-project-that-uses-an-on-demand-assembly"></a>So erstellen Sie ein Projekt, das eine Bedarfs gesteuerte Assembly verwendet

1. Erstellen Sie ein Verzeichnis mit dem Namen ClickOnceOnDemand.

2. Öffnen Sie die Windows SDK Eingabeaufforderung oder die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Eingabeaufforderung.

3. Wechseln Sie zum Verzeichnis ClickOnceOnDemand.

4. Generieren Sie mit dem folgenden Befehl ein öffentliches/privates Schlüsselpaar:

   ```cmd
   sn -k TestKey.snk
   ```

5. Definieren Sie mithilfe von Editor oder einem anderen Text-Editor eine Klasse `DynamicClass` mit dem Namen mit einer einzelnen Eigenschaft mit dem Namen `Message` .

    [!code-vb[ClickOnceLibrary#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.vb)]
    [!code-csharp[ClickOnceLibrary#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.cs)]

6. Speichern Sie den Text in Abhängigkeit von der verwendeten Sprache als Datei mit dem Namen *ClickOnceLibrary.cs* oder *ClickOnceLibrary. vb* im Verzeichnis *ClickOnceOnDemand* .

7. Kompilieren Sie die Datei in eine Assembly.

   ```csharp
   csc /target:library /keyfile:TestKey.snk ClickOnceLibrary.cs
   ```

   ```vb
   vbc /target:library /keyfile:TestKey.snk ClickOnceLibrary.vb
   ```

8. Um das öffentliche Schlüssel Token für die Assembly zu erhalten, verwenden Sie den folgenden Befehl:

   ```cmd
   sn -T ClickOnceLibrary.dll
   ```

9. Erstellen Sie mit dem Text-Editor eine neue Datei, und geben Sie den folgenden Code ein. Dieser Code erstellt eine Windows Forms Anwendung, die die ClickOnceLibrary-Assembly herunterlädt, wenn Sie benötigt wird.

     [!code-csharp[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.cs)]
     [!code-vb[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.vb)]

10. Suchen Sie im Code den-Befehl <xref:System.Reflection.Assembly.LoadFile%2A> .

11. Legen `PublicKeyToken` Sie auf den Wert fest, den Sie zuvor abgerufen haben.

12. Speichern Sie die Datei entweder als *Form1.cs* oder *Form1. vb*.

13. Kompilieren Sie ihn mithilfe des folgenden Befehls in eine ausführbare Datei.

    ```csharp
    csc /target:exe /reference:ClickOnceLibrary.dll Form1.cs
    ```

    ```vb
    vbc /target:exe /reference:ClickOnceLibrary.dll Form1.vb
    ```

## <a name="mark-assemblies-as-optional"></a>Assemblys als optional markieren

#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-mageuiexe"></a>So markieren Sie Assemblys in der ClickOnce-Anwendung mithilfe MageUI.exe als optional

1. Erstellen Sie mithilfe *MageUI.exe* ein Anwendungs Manifest, wie in Exemplarische Vorgehensweise [: Manuelles Bereitstellen einer ClickOnce-Anwendung](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)beschrieben. Verwenden Sie die folgenden Einstellungen für das Anwendungs Manifest:

    - Benennen Sie das Anwendungs Manifest `ClickOnceOnDemand` .

    - Legen Sie auf der Seite **Dateien** in der Zeile *ClickOnceLibrary.dll* die Spalte **Dateityp** auf **keine** fest.

    - Geben Sie auf der Seite **Dateien** in der Zeile *ClickOnceLibrary.dll* `ClickOnceLibrary.dll` in die Spalte **Gruppe** ein.

2. Erstellen Sie mithilfe *MageUI.exe* ein Bereitstellungs Manifest, wie in Exemplarische Vorgehensweise [: Manuelles Bereitstellen einer ClickOnce-Anwendung](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)beschrieben. Verwenden Sie für das Bereitstellungs Manifest die folgenden Einstellungen:

    - Benennen Sie das Bereitstellungs Manifest `ClickOnceOnDemand` .

## <a name="testing-the-new-assembly"></a>Testen der neuen Assembly

#### <a name="to-test-your-on-demand-assembly"></a>So testen Sie die bedarfsabhängige Assembly

1. Laden Sie die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellung auf einen Webserver hoch.

2. Starten Sie Ihre Anwendung [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , die mit bereitgestellt wird, über einen Webbrowser, indem Sie die URL des Bereitstellungs Manifests eingeben. Wenn Sie Ihre Anwendung aufzurufen [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `ClickOnceOnDemand` und Sie in das Stammverzeichnis von adatum.com hochladen, sieht die URL wie folgt aus:

   ```
   http://www.adatum.com/ClickOnceOnDemand/ClickOnceOnDemand.application
   ```

3. Wenn das Hauptformular angezeigt wird, drücken Sie die <xref:System.Windows.Forms.Button>. Daraufhin sollte eine Zeichenfolge in einem Meldungsfeldfenster angezeigt werden, die „Hello, World!“ lautet.

## <a name="see-also"></a>Weitere Informationen
- <xref:System.Deployment.Application.ApplicationDeployment>