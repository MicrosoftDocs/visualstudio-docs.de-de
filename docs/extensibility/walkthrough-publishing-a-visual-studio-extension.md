---
title: 'Exemplarische Vorgehensweise: Veröffentlichen einer Visual Studio-Erweiterung | Microsoft-Dokumentation'
description: Erfahren Sie, wie Sie eine Visual Studio-Erweiterung für den Visual Studio Marketplace veröffentlichen, sodass Entwickler nach neuen und aktualisierten Erweiterungen suchen können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cbdd283c5d147c53e7d82843207b48d0dbf6e6e9
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877883"
---
# <a name="walkthrough-publish-a-visual-studio-extension"></a>Exemplarische Vorgehensweise: Veröffentlichen einer Visual Studio-Erweiterung

In dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie eine Visual Studio-Erweiterung für den Visual Studio Marketplace veröffentlichen. Wenn Sie Ihre Erweiterung zum Marketplace hinzufügen, können Entwickler **Erweiterungen und Updates** verwenden, um nach neuen und aktualisierten Erweiterungen zu suchen.

## <a name="prerequisites"></a>Voraussetzungen

 Um dieser exemplarischen Vorgehensweise folgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-visual-studio-extension"></a>Erstellen einer Visual Studio-Erweiterung

In diesem Artikel wird eine standardmäßige VSPackage-Erweiterung verwendet, die Schritte sind jedoch für jede Art von Erweiterung gültig.

1. Erstellen Sie ein VSPackage in c# mit `TestPublish` dem Namen, das über einen Menübefehl verfügt. Weitere Informationen finden Sie unter [Erstellen der ersten Erweiterung: Hallo Welt](../extensibility/extensibility-hello-world.md).

## <a name="package-your-extension"></a>Packen der Erweiterung

1. Aktualisieren Sie die Erweiterung " *. vsixmanifest* " mit den korrekten Informationen zu "Produktname", "Autor" und "Version".

   ![Erweiterungs-vsixmanifest aktualisieren](media/update-extension-vsixmanifest.png)

2. Erstellen Sie die Erweiterung im **Releasemodus** . Nun wird Ihre Erweiterung als VSIX im Ordner "\bin\release" verpackt.

3. Sie können auf die VSIX doppelklicken, um die Installation zu überprüfen.

## <a name="test-the-extension"></a>Testen der Erweiterung

 Bevor Sie die Erweiterung verteilen, erstellen und testen Sie Sie, um sicherzustellen, dass Sie ordnungsgemäß in der experimentellen Instanz von Visual Studio installiert ist.

1. Starten Sie in Visual Studio das Debuggen, um eine experimentelle Instanz von Visual Studio zu öffnen.

2. Wechseln Sie **in der experimentellen Instanz zum Menü Extras** , und klicken Sie dann auf **Erweiterungen und Updates**. Die Erweiterung testpublish sollte im mittleren Bereich angezeigt und aktiviert werden.

3. Vergewissern Sie sich, dass **im Menü Extras der Befehl** Test angezeigt wird.

## <a name="publish-the-extension-to-the-visual-studio-marketplace"></a>Veröffentlichen Sie die Erweiterung auf dem Visual Studio Marketplace

1. Stellen Sie sicher, dass Sie die Releaseversion ihrer Erweiterung erstellt haben und auf dem neuesten Stand sind.

2. Öffnen Sie in einem Webbrowser die [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) Website.

3. Klicken Sie in der oberen rechten Ecke auf **Anmelden**.

4. Melden Sie sich mit dem Microsoft-Konto an. Wenn Sie keine Microsoft-Konto haben, können Sie an dieser Stelle eine erstellen.

5. Klicken Sie auf **Erweiterungen veröffentlichen**.  Mit dieser Option gelangen Sie zur Seite verwalten für alle Ihre Erweiterungen. Wenn Sie über kein Herausgeber Konto verfügen, werden Sie aufgefordert, das Konto zu diesem Zeitpunkt zu erstellen.

   ![In Marketplace hochladen](media/upload-to-marketplace.png)

6. Wählen Sie den Verleger aus, den Sie zum Hochladen der Erweiterung verwenden möchten. Sie können den Verleger ändern, indem Sie auf die auf der linken Seite aufgeführten Verleger Namen klicken. Klicken Sie auf **neue Erweiterung** , und wählen Sie **Visual Studio** aus.

7. In **1: Hochladen der Erweiterung** können Sie auswählen, dass Sie eine VSIX-Datei direkt in Visual Studio Marketplace hochladen oder einfach einen Link zu ihrer eigenen Website hinzufügen. In diesem Beispiel wird die Erweiterung *testpublish. vsix* hochgeladen. Ziehen Sie die Erweiterung per Drag & Drop, oder **Klicken Sie** auf den Link klicken, um die Datei zu suchen. Suchen Sie die Erweiterung im Ordner "\bin\release" des Projekts.  Klicken Sie auf **Continue**(Weiter).

8. In **2: Geben Sie Erweiterungs Details** an. einige Felder werden automatisch aus der Datei " *Source. Extension. vsixmanifest* " aus der Erweiterung aufgefüllt. Weitere Details finden Sie unten:

    * Der **interne Name** wird in der URL der Detailseite der Erweiterung verwendet. Beispiel: Wenn Sie eine Erweiterung unter dem Verleger Namen "myname" veröffentlichen und den internen Namen als "meine Erweiterung" angeben, ergibt sich die URL "marketplace. VisualStudio \. com/Items? ItemName = myname. MyExtension" für die Detailseite ihrer Erweiterung.

    * **Anzeige Name** der Erweiterung. Dieser Name wird automatisch aus der Datei " *Source. Extension. vsixmanifest* " aufgefüllt.

    * **Versions** Nummer der Erweiterung, die Sie hochladen. Diese Version wird automatisch aus der Datei " *Source. Extension. vsixmanifest* " aufgefüllt.

    * **VSIX-ID** ist der eindeutige Bezeichner, der von Visual Studio für die Erweiterung verwendet wird. Dieser Bezeichner ist erforderlich, wenn Sie möchten, dass die Erweiterung automatisch aktualisiert wird. Dieser Bezeichner wird automatisch aus der Datei " *Source. Extension. vsixmanifest* " aufgefüllt.

    * **Logo** , das für die Erweiterung verwendet wird. Dieses Logo wird automatisch aus der Datei " *Source. Extension. vsixmanifest* ", sofern angegeben, aufgefüllt.

    * **Kurze Beschreibung** der Funktionsweise der Erweiterung. Diese Beschreibung wird automatisch aus der Datei " *Source. Extension. vsixmanifest* " aufgefüllt.

    * **Übersicht** ist ein guter Ort, um Screenshots und ausführliche Informationen zu den Funktionen ihrer Erweiterung einzuschließen.

    * **Unterstützte Visual Studio-Versionen** ermöglicht Ihnen die Auswahl der Versionen von Visual Studio, in denen Ihre Erweiterung funktioniert. Die Erweiterung wird nur für diese Versionen installiert.

    * * * Die unterstützte Visual Studio-Edition ermöglicht Ihnen die Auswahl der Editionen von Visual Studio, in denen Ihre Erweiterung funktioniert. Die Erweiterung wird nur für diese Editionen installiert.

    * **Art:** Die gängigsten Typen von Erweiterungen sind **Tools**.

    * **Kategorien**. Wählen Sie bis zu drei aus, die für Ihre Erweiterung am besten geeignet sind.

    * **Tags** sind Schlüsselwörter, die Benutzer beim Auffinden Ihrer Erweiterung unterstützen. Mithilfe von Tags können Sie die Such Relevanz Ihrer Erweiterungen im Marketplace steigern.

    * **Kategorie Preise** sind die Kosten ihrer Erweiterung.

    * Mit dem **Quellcoderepository** können Sie einen Link zu Ihrem Quellcode mit der Community freigeben.

    * **Wenn Sie Q&A für Ihre Erweiterung zulassen** , können Benutzer auf der Erweiterungs Eintrags Seite Fragen hinterlassen.

9. Klicken Sie auf **speichern & hochladen**. Mit dieser Option gelangen Sie zurück zur Seite für die Verwaltung des Verlegers. Ihre Erweiterung wurde noch nicht veröffentlicht. Um die Erweiterung zu veröffentlichen, klicken Sie mit der rechten Maustaste auf die Erweiterung, und wählen Sie **dann** veröffentlichen aus. Durch Auswahl von **Erweiterung anzeigen** können Sie anzeigen, wie Ihre Erweiterung im Marketplace aussehen soll. Klicken Sie für Erwerbs Nummern auf **Berichte**. Wenn Sie Änderungen an der Erweiterung vornehmen möchten, klicken Sie auf **Bearbeiten**.

   ![Erweiterungs Eingabe Menü](media/extension-entry-menu.png)

10. Nachdem Sie auf " **öffentlich machen**" geklickt haben, ist die Erweiterung jetzt öffentlich. Durchsuchen Sie die Visual Studio Marketplace nach ihrer Erweiterung.

## <a name="add-additional-users-to-manage-your-publisher-account"></a>Hinzufügen zusätzlicher Benutzer zum Verwalten Ihres Herausgeber Kontos

Marketplace unterstützt das erteilen zusätzlicher Benutzerberechtigungen für den Zugriff auf und die Verwaltung eines Verleger Kontos.

1. Navigieren Sie zu dem Verleger Konto, dem Sie weitere Benutzer hinzufügen möchten.

2. Wählen Sie **Mitglieder** aus, und klicken Sie auf **Hinzufügen**.

   ![Zusätzlichen Benutzer hinzufügen](media/add-users.png)

3. Sie können dann die e-Mail-Adresse des Benutzers angeben, den Sie hinzufügen möchten, und unter **Rolle auswählen** die richtige Zugriffsebene erteilen.  Sie können eine der folgenden Optionen auswählen:

   * **Ersteller**: der Benutzer kann Erweiterungen veröffentlichen, aber keine von anderen Benutzern veröffentlichten Erweiterungen anzeigen oder verwalten.

   * **Reader**: der Benutzer kann Erweiterungen anzeigen, aber keine Erweiterungen veröffentlichen oder verwalten.

   * **Mitwirkender**: der Benutzer kann Erweiterungen veröffentlichen und verwalten, aber keine Verleger Einstellungen bearbeiten oder den Zugriff verwalten.

   * **Besitzer**: der Benutzer kann Erweiterungen veröffentlichen und verwalten, Herausgeber Einstellungen bearbeiten und den Zugriff verwalten.

## <a name="install-the-extension-from-the-visual-studio-marketplace"></a>Installieren Sie die Erweiterung aus der Visual Studio Marketplace

Nachdem die Erweiterung veröffentlicht wurde, installieren Sie Sie in Visual Studio und testen Sie dort.

1. Klicken Sie in Visual Studio im **Menü Extras** auf **Erweiterungen und Updates**.

2. Klicken Sie auf **Online** , und suchen Sie nach **testpublish**.

3. Klicken Sie auf **Download**. Die Erweiterung wird dann für die Installation geplant.

4. Schließen Sie alle Instanzen von Visual Studio, um die Installation abzuschließen.

## <a name="remove-the-extension"></a>Entfernen der Erweiterung

Sie können die Erweiterung aus dem Visual Studio Marketplace und von Ihrem Computer entfernen.

### <a name="to-remove-the-extension-from-the-visual-studio-marketplace"></a>So entfernen Sie die Erweiterung aus der Visual Studio Marketplace

1. Öffnen Sie die [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) Website.

2. Klicken Sie in der oberen rechten Ecke auf Erweiterungen **veröffentlichen** . Wählen Sie den Verleger aus, den Sie zum Veröffentlichen von **testpublish** verwendet haben. Die Auflistung für **testpublish** wird angezeigt.

3. Klicken Sie mit der rechten Maustaste auf den Erweiterungs Eintrag und dann auf **Entfernen**. Sie werden aufgefordert zu bestätigen, dass Sie die Erweiterung entfernen möchten. Klicken Sie auf **OK**.

### <a name="to-remove-the-extension-from-your-computer"></a>So entfernen Sie die Erweiterung auf dem Computer

1. Klicken Sie in Visual Studio im **Menü Extras** auf **Erweiterungen und Updates**.

2. Wählen Sie **testpublish** aus, und klicken Sie auf **deinstallieren** Die Erweiterung wird dann für die Deinstallation geplant.

3. Schließen Sie alle Instanzen von Visual Studio, um die Installation abzuschließen.
