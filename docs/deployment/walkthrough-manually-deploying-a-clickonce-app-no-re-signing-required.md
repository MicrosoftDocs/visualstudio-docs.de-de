---
title: Manuelles Bereitstellen einer ClickOnce-app & Branding beibehalten
description: Erfahren Sie, wie Sie ClickOnce-Anwendungen erstellen, die von Kunden bereitgestellt werden, ohne ein neues Bereitstellungs Manifest zu erzeugen, das das Kunden Branding verwenden kann.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- branding
- preserved branding information
- ClickOnce deployment, manually
- multiple ClickOnce deployment and branding
- ClickOnce deployment, SDK tools
- customer deployments
- manual ClickOnce deployments
- manifests [ClickOnce]
- ClickOnce applications, deployed by others
ms.assetid: c21822fb-d4ee-42e4-b72d-41ee9786efe5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 29bdd080e87e8fad44c7b8943d0d017749b8c30b
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94350308"
---
# <a name="walkthrough-manually-deploy-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information"></a>Exemplarische Vorgehensweise: Manuelles Bereitstellen einer ClickOnce-Anwendung, die keine erneute Signierung erfordert und Brandinginformationen beibehält
Wenn Sie eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung erstellen und Sie dann einem Kunden zum Veröffentlichen und Bereitstellen zuweisen, musste der Kunde das Bereitstellungs Manifest traditionell aktualisieren und neu signieren. Obwohl dies in den meisten Fällen immer noch die bevorzugte Methode ist, können Sie mit dem .NET Framework 3,5 bereit [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Stellungen erstellen, die von Kunden bereitgestellt werden können, ohne ein neues Bereitstellungs Manifest generieren zu müssen. Weitere Informationen finden Sie unter Bereitstellen [von ClickOnce-Anwendungen für Test-und Produktionsserver ohne erneutes Signieren](../deployment/deploying-clickonce-applications-for-testing-and-production-without-resigning.md).

 Wenn Sie eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung erstellen und Sie dann einem Kunden zur Veröffentlichung und Bereitstellung zur Verfügung stellen, kann die Anwendung das Branding des Kunden nutzen oder Ihr Branding beibehalten. Wenn es sich bei der Anwendung beispielsweise um eine einzelne proprietäre Anwendung handelt, können Sie Ihr Branding beibehalten. Wenn die Anwendung für jeden Kunden hochgradig angepasst wird, können Sie das Branding des Kunden verwenden. Mit dem .NET Framework 3,5 können Sie Branding, Verleger Informationen und Sicherheits Signaturen beibehalten, wenn Sie eine Anwendung an eine bereit zustellende Organisation übergeben. Weitere Informationen finden Sie unter [Erstellen von ClickOnce-Anwendungen für die](../deployment/creating-clickonce-applications-for-others-to-deploy.md)Bereitstellung durch andere Benutzer.

> [!NOTE]
> In dieser exemplarischen Vorgehensweise erstellen Sie bereit Stellungen manuell, indem Sie entweder das Befehlszeilen Tool *Mage.exe* oder das grafische Tool *MageUI.exe* verwenden. Weitere Informationen zu manuellen bereit Stellungen finden Sie unter Exemplarische Vorgehensweise [: Manuelles Bereitstellen einer ClickOnce-Anwendung](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

## <a name="prerequisites"></a>Voraussetzungen
 Zum Ausführen der Schritte in dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

- Eine Windows Forms Anwendung, die Sie bereitstellen können. Diese Anwendung wird als *WindowsFormsApp1* bezeichnet.

- Visual Studio oder das Windows SDK.

### <a name="to-deploy-a-clickonce-application-with-multiple-deployment-and-branding-support-using-mageexe"></a>So stellen Sie eine ClickOnce-Anwendung mit mehreren Bereitstellungs-und Brandingunterstützung mithilfe Mage.exe bereit

1. Öffnen Sie eine Visual Studio-Eingabeaufforderung oder eine [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] Eingabeaufforderung, und wechseln Sie in das Verzeichnis, in dem Sie die Dateien speichern möchten [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

2. Erstellen Sie ein Verzeichnis mit dem Namen nach der aktuellen Version der Bereitstellung. Wenn Sie die Anwendung zum ersten Mal bereitstellen, werden Sie wahrscheinlich **1.0.0.0** auswählen.

   > [!NOTE]
   > Die Version der Bereitstellung kann sich von der Version Ihrer Anwendungs Dateien unterscheiden.

3. Erstellen Sie ein Unterverzeichnis mit dem Namen **bin** , und kopieren Sie alle Ihre Anwendungs Dateien, einschließlich ausführbarer Dateien, Assemblys, Ressourcen und Datendateien.

4. Generieren Sie das Anwendungs Manifest mit einem Mage.exe aufzurufenden.

   ```cmd
   mage -New Application -ToFile 1.0.0.0\WindowsFormsApp1.exe.manifest -Name "Windows Forms App 1" -Version 1.0.0.0 -FromDirectory 1.0.0.0\bin -UseManifestForTrust true -Publisher "A. Datum Corporation"
   ```

5. Signieren Sie das Anwendungs Manifest mit Ihrem digitalen Zertifikat.

   ```cmd
   mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx
   ```

6. Generieren Sie das Bereitstellungs Manifest mit einem *Mage.exe* aufzurufenden. Standardmäßig wird *Mage.exe* die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellung vonMage.exeals installierte Anwendung markiert, sodass Sie online und offline ausgeführt werden kann. Um die Anwendung nur verfügbar zu machen, wenn der Benutzer online ist, verwenden Sie das- `-i` Argument mit dem Wert `f` . Da diese Anwendung das Feature für mehrere bereit Stellungen nutzt, schließen Sie das `-providerUrl` Argument in *Mage.exe* aus. (In Versionen der .NET Framework vor Version 3,5 führt der Ausschluss `-providerUrl` für eine Offline Anwendung zu einem Fehler.)

   ```cmd
   mage -New Deployment -ToFile WindowsFormsApp1.application -Name "Windows Forms App 1" -Version 1.0.0.0 -AppManifest 1.0.0.0\WindowsFormsApp1.manifest
   ```

7. Signieren Sie das Bereitstellungs Manifest nicht.

8. Stellen Sie alle Dateien für den Kunden bereit, der die Anwendung in seinem Netzwerk bereitstellen wird.

9. An diesem Punkt muss der Kunde das Bereitstellungs Manifest mit seinem eigenen selbst generierten Zertifikat signieren. Wenn der Kunde beispielsweise für ein Unternehmen mit dem Namen Adventure Works arbeitet, kann er mithilfe des *MakeCert.exe* Tools ein selbst signiertes Zertifikat generieren. Verwenden Sie als nächstes das *Pvk2pfx.exe* Tool, um die von *MakeCert.exe* erstellten Dateien in einer PFX-Datei zu kombinieren, die an *Mage.exe* übermittelt werden kann.

    ```cmd
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx
    ```

10. Der Kunde verwendet dieses Zertifikat, um das Bereitstellungs Manifest zu signieren.

    ```cmd
    mage -Sign WindowsFormsApp1.application -CertFile MyCert.pfx
    ```

11. Der Kunde stellt die Anwendung für Ihre Benutzer bereit.

### <a name="to-deploy-a-clickonce-application-with-multiple-deployment-and-branding-support-using-mageuiexe"></a>So stellen Sie eine ClickOnce-Anwendung mit mehreren Bereitstellungs-und Brandingunterstützung mithilfe MageUI.exe bereit

1. Öffnen Sie eine Visual Studio-Eingabeaufforderung oder eine [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] Eingabeaufforderung, und navigieren Sie zu dem Verzeichnis, in dem Sie die Dateien speichern möchten [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

2. Erstellen Sie ein Unterverzeichnis mit dem Namen **bin** , und kopieren Sie alle Ihre Anwendungs Dateien, einschließlich ausführbarer Dateien, Assemblys, Ressourcen und Datendateien.

3. Erstellen Sie ein Unterverzeichnis, das nach der aktuellen Version der Bereitstellung benannt wird. Wenn Sie die Anwendung zum ersten Mal bereitstellen, werden Sie wahrscheinlich **1.0.0.0** auswählen.

   > [!NOTE]
   > Die Version der Bereitstellung kann sich von der Version Ihrer Anwendungs Dateien unterscheiden.

4. Verschieben Sie das Verzeichnis " \\ **bin** " in das Verzeichnis, das Sie in Schritt 2 erstellt haben.

5. Starten Sie das grafische Tool *MageUI.exe*.

   ```cmd
   MageUI.exe
   ```

6. Erstellen Sie ein neues Anwendungs Manifest, indem Sie im Menü **Datei** , **neu** und **Anwendungs Manifest** auswählen.

7. Geben Sie auf der Registerkarte Standard **Name** den Namen und die Versionsnummer dieser Bereitstellung ein. Geben Sie außerdem einen Wert für **Publisher** an, der als Ordnername für den Verknüpfungs Link der Anwendung im Startmenü bei der Bereitstellung verwendet wird.

8. Wählen Sie die Registerkarte **Anwendungs Optionen** aus, und klicken Sie auf **Anwendungs Manifest für Vertrauens Informationen verwenden**. Dadurch wird das Branding von Drittanbietern für diese [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung aktiviert.

9. Wählen Sie die Registerkarte **Dateien** aus, und klicken Sie auf die Schaltfläche **Durchsuchen** neben dem Textfeld **Anwendungsverzeichnis** .

10. Wählen Sie das Verzeichnis mit den Anwendungs Dateien aus, die Sie in Schritt 2 erstellt haben, und klicken Sie im Dialogfeld Ordner Auswahl auf **OK** .

11. Klicken Sie **auf die Schalt** Fläche auffüllen, um alle Anwendungs Dateien der Datei Liste hinzuzufügen. Wenn die Anwendung mehr als eine ausführbare Datei enthält, markieren Sie die ausführbare Hauptdatei für diese Bereitstellung als Start Anwendung, indem Sie in der Dropdown Liste **Dateityp** den **Eintrag Einstiegspunkt** auswählen. (Wenn Ihre Anwendung nur eine ausführbare Datei enthält, wird Sie von *MageUI.exe* für Sie markiert.)

12. Wählen Sie die Registerkarte **erforderliche Berechtigungen** aus, und wählen Sie die Vertrauens Ebene aus, die Ihre Anwendung für die Bestätigung benötigt. Der Standardwert ist " **volle Vertrauens** Würdigkeit", der für die meisten Anwendungen geeignet ist.

13. Wählen Sie im Menü **Datei** , **Speichern** aus, und speichern Sie das Anwendungs Manifest. Sie werden aufgefordert, das Anwendungs Manifest zu signieren, wenn Sie es speichern.

14. Wenn Sie über ein Zertifikat verfügen, das als Datei auf Ihrem Dateisystem gespeichert ist, verwenden Sie die Option **als Zertifikat Datei signieren** , und wählen Sie das Zertifikat aus dem Dateisystem mithilfe der Schaltfläche mit den Auslassungs Punkten ( **...** ) aus.

     - oder -

     Wenn Ihr Zertifikat in einem Zertifikat Speicher gespeichert ist, auf den von Ihrem Computer aus zugegriffen werden kann, wählen Sie die **Option gespeichertes Zertifikat signieren** aus, und wählen Sie das Zertifikat aus der Liste aus.

15. Wählen Sie im Menü **Datei** , **neu** und **Bereitstellungs Manifest** aus, um das Bereitstellungs Manifest zu erstellen, und geben Sie dann auf der Registerkarte **Name** einen Namen und eine Versionsnummer ein (in diesem Beispiel **1.0.0.0** ).

16. Wechseln Sie zur Registerkarte **Update** , und geben Sie an, wie oft diese Anwendung aktualisiert werden soll. Wenn Ihre Anwendung die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellungs-API verwendet, um nach Updates zu suchen, deaktivieren Sie das Kontrollkästchen **diese Anwendung sollte nach Updates suchen**.

17. Wechseln Sie zur Registerkarte **Anwendungs Verweis** . Sie können alle Werte auf dieser Registerkarte vorab auffüllen, indem Sie auf die Schaltfläche **Manifest auswählen** klicken und das Anwendungs Manifest auswählen, das Sie in den vorherigen Schritten erstellt haben.

18. Wählen Sie **Speichern** , und speichern Sie das Bereitstellungs Manifest auf dem Datenträger Sie werden aufgefordert, das Anwendungs Manifest zu signieren, wenn Sie es speichern. Klicken Sie auf **Abbrechen** , um das Manifest ohne Signierung zu speichern.

19. Stellen Sie dem Kunden alle Anwendungs Dateien bereit.

20. An diesem Punkt muss der Kunde das Bereitstellungs Manifest mit seinem eigenen selbst generierten Zertifikat signieren. Wenn der Kunde beispielsweise für ein Unternehmen mit dem Namen Adventure Works arbeitet, kann er mithilfe des *MakeCert.exe* Tools ein selbst signiertes Zertifikat generieren. Verwenden Sie als nächstes das *Pvk2pfx.exe* Tool, um die von *MakeCert.exe* erstellten Dateien in einer PFX-Datei zu kombinieren, die an *MageUI.exe* übermittelt werden kann.

    ```cmd
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx
    ```

21. Nachdem das Zertifikat generiert wurde, signiert der Kunde das Bereitstellungs Manifest, indem er das Bereitstellungs Manifest in *MageUI.exe* öffnet und dann speichert. Wenn das Dialogfeld "Signierung" angezeigt wird, wählt der Kunde die Option " **als Zertifikat Datei anmelden** " aus und wählt die PFX-Datei aus, die er auf dem Datenträger

22. Der Kunde stellt die Anwendung für Ihre Benutzer bereit.

## <a name="see-also"></a>Weitere Informationen
- [Mage.exe (Tool zum Generieren und Bearbeiten von Manifesten)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [MageUI.exe (Tool zum Generieren und Bearbeiten von Manifesten, grafischer Client)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)
- [Makecert](/windows/desktop/SecCrypto/makecert)
