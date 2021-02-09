---
title: 'Exemplarische Vorgehensweise: Veröffentlichen einer Visual Studio-Erweiterung | Microsoft-Dokumentation'
description: Erfahren Sie, wie Sie eine Visual Studio-Erweiterung in Visual Studio Marketplace veröffentlichen, sodass Entwickler nach neuen und aktualisierten Erweiterungen suchen können.
ms.custom: SEO-VS-2020
ms.date: 01/15/2021
ms.topic: how-to
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bda44c0c3f6c4b1986fc45a7c9cbf5c4ffa83043
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889004"
---
# <a name="walkthrough-publish-a-visual-studio-extension"></a>Exemplarische Vorgehensweise: Veröffentlichen einer Visual Studio-Erweiterung

In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie eine Visual Studio-Erweiterung in Visual Studio Marketplace veröffentlichen. Wenn Sie die Erweiterung Visual Studio Marketplace hinzufügen, können Entwickler **Erweiterungen und Updates** verwenden, um nach neuen und aktualisierten Erweiterungen zu suchen.

## <a name="prerequisites"></a>Voraussetzungen

 Um dieser exemplarischen Vorgehensweise folgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-visual-studio-extension"></a>Erstellen einer Visual Studio-Erweiterung

In diesem Artikel wird eine standardmäßige VSPackage-Erweiterung verwendet, die Schritte sind jedoch für jede Art von Erweiterung gültig.

- Erstellen Sie ein VSPackage in c# mit `TestPublish` dem Namen, das über einen Menübefehl verfügt. Weitere Informationen finden Sie unter [Erstellen der ersten Erweiterung: Hallo Welt](../extensibility/extensibility-hello-world.md).

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

## <a name="publish-the-extension-to-visual-studio-marketplace"></a>Veröffentlichen Sie die Erweiterung in Visual Studio Marketplace

1. Stellen Sie sicher, dass Sie die Releaseversion ihrer Erweiterung erstellt haben und auf dem neuesten Stand sind.

2. Wechseln Sie in einem Webbrowser zu [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs).

3. Klicken Sie in der oberen rechten Ecke auf **Anmelden**.

4. Melden Sie sich mit dem Microsoft-Konto an. Wenn Sie keine Microsoft-Konto haben, können Sie an dieser Stelle eine erstellen.

5. Klicken Sie auf **Erweiterungen veröffentlichen**. Mit dieser Option gelangen Sie zur Seite verwalten für alle Ihre Erweiterungen. Wenn Sie über kein Herausgeber Konto verfügen, werden Sie aufgefordert, das Konto zu diesem Zeitpunkt zu erstellen.

   ![In Marketplace hochladen](media/upload-to-marketplace.png)

6. Wählen Sie den Verleger aus, den Sie zum Hochladen der Erweiterung verwenden möchten. Sie können den Verleger ändern, indem Sie auf die auf der linken Seite aufgeführten Verleger Namen klicken. Klicken Sie auf **neue Erweiterung** , und wählen Sie **Visual Studio**.

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

    * Die **Unterstützte Visual Studio-Edition** ermöglicht Ihnen die Auswahl der Editionen von Visual Studio, in denen Ihre Erweiterung funktioniert. Die Erweiterung wird nur für diese Editionen installiert.

    * **Typ**. Der häufigste Erweiterungstyp **ist Extras**.

    * **Kategorien**. Wählen Sie bis zu drei aus, die für Ihre Erweiterung am besten geeignet sind.

    * **Tags** sind Schlüsselwörter, die Benutzer beim Auffinden Ihrer Erweiterung unterstützen. Tags können dabei helfen, die Such Relevanz der Erweiterungen in Visual Studio Marketplace zu erhöhen.

    * **Kategorie Preise** sind die Kosten ihrer Erweiterung.

    * Mit dem **Quellcoderepository** können Sie einen Link zu Ihrem Quellcode mit der Community freigeben.

    * **Wenn Sie Q&A für Ihre Erweiterung zulassen** , können Benutzer auf der Erweiterungs Eintrags Seite Fragen hinterlassen.

9. Klicken Sie auf **speichern & hochladen**. Mit dieser Option gelangen Sie zurück zur Seite für die Verwaltung des Verlegers. Ihre Erweiterung wurde noch nicht veröffentlicht.

10. Um die Erweiterung zu veröffentlichen, klicken Sie mit der rechten Maustaste auf die Erweiterung, und wählen Sie **dann** veröffentlichen aus. Um zu sehen, wie die Erweiterung in Visual Studio Marketplace aussieht, wählen Sie **Erweiterung anzeigen** aus. Klicken Sie für Erwerbs Nummern auf **Berichte**. Wenn Sie Änderungen an der Erweiterung vornehmen möchten, klicken Sie auf **Bearbeiten**.

    ![Erweiterungs Eingabe Menü](media/extension-entry-menu.png)

11. Klicken Sie auf **öffentlich machen**, und ihre Erweiterung ist jetzt öffentlich. Suchen Sie Visual Studio Marketplace nach ihrer Erweiterung.

## <a name="update-a-published-extension-in-visual-studio-marketplace"></a>Aktualisieren einer veröffentlichten Erweiterung in Visual Studio Marketplace

Bevor Sie beginnen, stellen Sie sicher, dass Sie die neue Releaseversion ihrer Erweiterung erstellt haben und auf dem neuesten Stand sind.

1.  Wechseln Sie in einem Webbrowser zu [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs).

1.  Klicken Sie in der oberen rechten Ecke auf **Anmelden**, und melden Sie sich dann mit Ihrem Microsoft-Konto an.

    :::image type="content" source="media/marketplace-upload-extension.png" alt-text="Screenshot, der die Auswahl einer hochgeladenen Erweiterungs Datei im Datei-Explorer anzeigt":::

1.  Klicken Sie auf **Erweiterungen veröffentlichen**, und wählen Sie dann den Verleger aus, den Sie verwenden möchten, um die aktualisierte Erweiterung hochzuladen.

    :::image type="content" source="media/marketplace-select-extension-version.png" alt-text="Screenshot der Visual Studio Marketplace mit hervorgehobenem Link &quot;Erweiterungen veröffentlichen&quot;.":::

1.  Bewegen Sie den Mauszeiger auf die drei horizontalen Punkte neben der Erweiterung, die Sie aktualisieren möchten, und wählen Sie dann **Bearbeiten** aus.

    :::image type="content" source="media/marketplace-select-extension.png" alt-text="Screenshot, der das Auswählen einer zu bearbeitenden Erweiterung anzeigt.":::

1.  Klicken Sie in **1: Hochladen der Erweiterung** nach dem VSIX-Dateinamen auf das Stift Symbol, um die veröffentlichte Erweiterung zu bearbeiten.

     :::image type="content" source="media/marketplace-edit-extension-details.png" alt-text="Screenshot, der zeigt, wie Sie auf das Stift Symbol klicken, um die Erweiterung zu bearbeiten":::

1.  Navigieren Sie zu ihrer aktualisierten VSIX-Erweiterungs Datei. Klicken Sie auf die Datei, und klicken Sie dann auf **Öffnen**.

    Die aktualisierte Erweiterung wird hochgeladen.

    :::image type="content" source="media/marketplace-upload-extension-notification.png" alt-text="Screenshot einer Datei Benachrichtigung, die nach dem Hochladen einer bearbeiteten Erweiterung angezeigt wird.":::

1. In **2: Geben Sie Erweiterungs Details** an. einige Details sind für ein Erweiterungs Update schreibgeschützt, oder Sie werden automatisch aus der Datei " *Source. Extension. vsixmanifest* " aus der Erweiterung aufgefüllt. Hier finden Sie weitere Informationen zu Erweiterungs Details:

    - **Interner Name** \* wird in der URL der Detailseite der Erweiterung verwendet. Beispiel: Wenn Sie eine Erweiterung unter dem Verleger Namen "myname" veröffentlichen und den internen Namen als "meine Erweiterung" angeben, ergibt sich für die Detailseite ihrer Erweiterung die URL "marketplace.VisualStudio.com/Items?ItemName=myname.MyExtension".

    - **Anzeige Name** \* ihrer Erweiterung. Dieser Name wird automatisch aus der Datei " *Source. Extension. vsixmanifest* " aufgefüllt.

    - **Version** \* die Nummer der Erweiterung, die Sie hochladen. Diese Version wird automatisch aus der Datei " *Source. Extension. vsixmanifest* " aufgefüllt.

    - **VSIX-ID** \* ist der eindeutige Bezeichner, der von Visual Studio für die Erweiterung verwendet wird. Dieser Bezeichner ist erforderlich, wenn Sie möchten, dass die Erweiterung automatisch aktualisiert wird. Dieser Bezeichner wird automatisch aus der Datei " *Source. Extension. vsixmanifest* " aufgefüllt.

    - **Logo** \* , der für die Erweiterung verwendet wird. Dieses Logo wird automatisch aus der Datei " *Source. Extension. vsixmanifest* ", sofern angegeben, aufgefüllt.

    - **Kurze Beschreibung** \* der Funktionsweise ihrer Erweiterung. Diese Beschreibung wird automatisch aus der Datei " *Source. Extension. vsixmanifest* " aufgefüllt.

    - **Übersicht** ist ein guter Ort, um Screenshots und ausführliche Informationen zu den Funktionen ihrer Erweiterung einzuschließen.

    - **Unterstützte Visual Studio-Versionen** \* ermöglicht Ihnen die Auswahl der Versionen von Visual Studio, an denen die Erweiterung ausgeführt wird. Die Erweiterung wird nur für diese Versionen installiert.

    - **Unterstützte Visual Studio-Edition** \* ermöglicht Ihnen die Auswahl der Editionen von Visual Studio, in denen Ihre Erweiterung funktioniert. Die Erweiterung wird nur in diesen Editionen installiert.

    - **Typ**. Der häufigste Erweiterungstyp **ist Extras**.

    - **Kategorien**. Wählen Sie bis zu drei aus, die für Ihre Erweiterung am besten geeignet sind.

    - **Tags** sind Schlüsselwörter, die Benutzer beim Auffinden Ihrer Erweiterung unterstützen. Tags können dabei helfen, die Such Relevanz der Erweiterungen in Visual Studio Marketplace zu erhöhen.

    - **Kategorie Preise** sind die Kosten ihrer Erweiterung.

    - Mit dem **Quellcoderepository** können Sie einen Link zu Ihrem Quellcode mit der Community freigeben.

    - **Wenn Sie Q&A für Ihre Erweiterung zulassen** , können Benutzer auf der Erweiterungs Eintrags Seite Fragen hinterlassen.

       \* Diese Details können für ein Erweiterungs Update nicht geändert werden.

1. Klicken Sie auf **speichern & hochladen**. Mit dieser Option gelangen Sie zurück zur Seite für die Verwaltung des Verlegers. Ihre Erweiterung wurde noch nicht veröffentlicht.

1. Um die Erweiterung zu veröffentlichen, klicken Sie mit der rechten Maustaste auf die Erweiterung, **und wählen Sie veröffentlichen aus**. Um zu sehen, wie die Erweiterung in Visual Studio Marketplace aussieht, wählen Sie **Erweiterung anzeigen** aus. Klicken Sie für Erwerbs Nummern auf **Berichte**. Wenn Sie Änderungen an der Erweiterung vornehmen möchten, klicken Sie auf **Bearbeiten**.

## <a name="add-additional-users-to-manage-your-publisher-account"></a>Hinzufügen zusätzlicher Benutzer zum Verwalten Ihres Herausgeber Kontos

Visual Studio Marketplace unterstützt das erteilen zusätzlicher Benutzerberechtigungen für den Zugriff und die Verwaltung eines Verleger Kontos.

1. Navigieren Sie zu dem Verleger Konto, dem Sie weitere Benutzer hinzufügen möchten.

2. Wählen Sie **Mitglieder** aus, und klicken Sie auf **Hinzufügen**.

   ![Zusätzlichen Benutzer hinzufügen](media/add-users.png)

3. Sie können dann die e-Mail-Adresse des Benutzers angeben, den Sie hinzufügen möchten, und unter **Rolle auswählen** die richtige Zugriffsebene erteilen.  Sie können eine der folgenden Optionen auswählen:

   * **Ersteller**: der Benutzer kann Erweiterungen veröffentlichen, aber keine von anderen Benutzern veröffentlichten Erweiterungen anzeigen oder verwalten.

   * **Reader**: der Benutzer kann Erweiterungen anzeigen, aber keine Erweiterungen veröffentlichen oder verwalten.

   * **Mitwirkender**: der Benutzer kann Erweiterungen veröffentlichen und verwalten, aber keine Verleger Einstellungen bearbeiten oder den Zugriff verwalten.

   * **Besitzer**: der Benutzer kann Erweiterungen veröffentlichen und verwalten, Herausgeber Einstellungen bearbeiten und den Zugriff verwalten.

## <a name="install-the-extension-from-visual-studio-marketplace"></a>Installieren Sie die Erweiterung von Visual Studio Marketplace

Nachdem die Erweiterung veröffentlicht wurde, installieren Sie Sie in Visual Studio und testen Sie dort.

1. Klicken Sie in Visual Studio im **Menü Extras** auf **Erweiterungen und Updates**.

2. Klicken Sie auf **Online** , und suchen Sie nach **testpublish**.

3. Klicken Sie auf **Download**. Die Erweiterung wird dann für die Installation geplant.

4. Schließen Sie alle Instanzen von Visual Studio, um die Installation abzuschließen.

## <a name="remove-the-extension"></a>Entfernen der Erweiterung

Sie können die Erweiterung aus Visual Studio Marketplace und von Ihrem Computer entfernen.

### <a name="to-remove-the-extension-from-visual-studio-marketplace"></a>So entfernen Sie die Erweiterung aus Visual Studio Marketplace

1. Wechseln Sie zu [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs).

2. Klicken Sie in der oberen rechten Ecke auf Erweiterungen **veröffentlichen** . Wählen Sie den Verleger aus, den Sie zum Veröffentlichen von **testpublish** verwendet haben. Die Auflistung für **testpublish** wird angezeigt.

3. Klicken Sie mit der rechten Maustaste auf den Erweiterungs Eintrag und dann auf **Entfernen**. Sie werden aufgefordert zu bestätigen, dass Sie die Erweiterung entfernen möchten. Klicken Sie auf **OK**.

### <a name="to-remove-the-extension-from-your-computer"></a>So entfernen Sie die Erweiterung auf dem Computer

1. Klicken Sie in Visual Studio im **Menü Extras** auf **Erweiterungen und Updates**.

2. Wählen Sie **testpublish** aus, und klicken Sie auf **deinstallieren** Die Erweiterung wird dann für die Deinstallation geplant.

3. Schließen Sie alle Instanzen von Visual Studio, um die Installation abzuschließen.
