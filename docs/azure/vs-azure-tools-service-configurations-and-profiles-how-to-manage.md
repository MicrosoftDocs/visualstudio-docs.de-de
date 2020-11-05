---
title: Verwalten von Dienstkonfigurationen und Profilen | Microsoft Docs
description: Erfahren Sie, wie Sie mit Dienstkonfigurationen und Profilkonfigurationsdateien arbeiten,| in denen Einstellungen für die Bereitstellungsumgebungen gespeichert und Einstellungen für Clouddienste veröffentlicht werden.
author: ghogen
manager: jillfra
assetId: 7da8c551-fb06-4057-b5c7-c77f4b39d803
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/11/2017
ms.author: ghogen
ms.openlocfilehash: 42c4668b2bf9925fe92db51b6a4275c535960a61
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2020
ms.locfileid: "93398877"
---
# <a name="how-to-manage-service-configurations-and-profiles"></a>Verwalten von Dienstkonfigurationen und Profilen
## <a name="overview"></a>Übersicht
Wenn Sie einen Clouddienst veröffentlichen, speichert Visual Studio Konfigurationsinformationen in zwei Arten von Konfigurationsdateien: Dienstkonfigurationen und Profile. In Dienstkonfigurationen (CSCFG-Dateien) werden Einstellungen für die Bereitstellungsumgebungen für einen Azure-Clouddienst gespeichert. Azure verwendet diese Konfigurationsdateien für die Verwaltung der Clouddienste. Auf der anderen Seite werden in Profilen (AZUREPUBXML-Dateien) Veröffentlichungseinstellungen für Clouddienste gespeichert. Diese Einstellungen werden bei der Verwendung des Veröffentlichungs-Assistenten gespeichert und lokal von Visual Studio verwendet. In diesem Thema wird die Arbeit mit den beiden Konfigurationsdateitypen erläutert.

## <a name="service-configurations"></a>Dienstkonfigurationen
Sie können mehrere Dienstkonfigurationen für jede Ihrer Bereitstellungsumgebungen erstellen. Beispielsweise können Sie eine Dienstkonfiguration für die lokale Umgebung, die zum Ausführen und Testen einer Azure-Anwendung verwendet wird, und eine andere Dienstkonfiguration für Ihre Produktionsumgebung erstellen.

Sie können diese Dienstkonfigurationen basierend auf Ihren Anforderungen hinzufügen, löschen, umbenennen und ändern. Sie können diese Dienstkonfigurationen in Visual Studio verwalten, wie in der folgenden Abbildung dargestellt.

![Dienstkonfigurationen verwalten](./media/vs-azure-tools-service-configurations-and-profiles-how-to-manage/manage-service-config.png)

Sie können das Dialogfeld **Konfigurationen verwalten** auch über die Eigenschaftenseiten der Rolle öffnen. Öffnen Sie das Kontextmenü für diese Rolle, und wählen Sie dann **Eigenschaften** aus, um die Eigenschaften für eine Rolle im Azure-Projekt zu öffnen. Erweitern Sie auf der Registerkarte **Einstellungen** die Liste **Dienstkonfiguration** , und klicken Sie dann auf **Verwalten** , um das Dialogfeld **Konfigurationen verwalten** zu öffnen.

### <a name="to-add-a-service-configuration"></a>So fügen Sie eine Dienstkonfiguration hinzu
1. Öffnen Sie im Projektmappen-Explorer das Kontextmenü für Ihr Azure-Projekt, und klicken Sie anschließend auf **Konfigurationen verwalten**.

    Das Dialogfeld **Dienstkonfigurationen verwalten** wird angezeigt.
2. Um eine Dienstkonfiguration hinzuzufügen, müssen Sie eine Kopie einer vorhandenen Konfiguration erstellen.Wählen Sie dazu die zu kopierende Konfiguration in der Liste Name aus, und klicken Sie dann auf die Schaltfläche Kopie erstellen. Wählen Sie dazu die zu kopierende Konfiguration in der Liste „Name“ aus, und klicken Sie dann auf die Schaltfläche **Kopie erstellen**.
3. (Optional) Wählen Sie die neue Dienstkonfiguration in der Liste „Name“ aus, um der Dienstkonfiguration einen neuen Namen zu geben, und klicken Sie dann auf die Schaltfläche **Umbenennen**. Geben Sie im Textfeld **Name** den Namen ein, den Sie für diese Dienstkonfiguration verwenden möchten, und klicken Sie dann auf **OK**.

    Eine neue Dienstkonfigurationsdatei mit dem Namen "ServiceConfiguration.[Neuer Name].cscfg" wird dem Azure-Projekt im Projektmappen-Explorer hinzugefügt.

### <a name="to-delete-a-service-configuration"></a>So löschen Sie eine Dienstkonfiguration
1. Öffnen Sie im Projektmappen-Explorer das Kontextmenü für Ihr Azure-Projekt, und klicken Sie anschließend auf **Konfigurationen verwalten**.

    Das Dialogfeld **Dienstkonfigurationen verwalten** wird angezeigt.
2. Wählen Sie zum Löschen einer Dienstkonfiguration die zu löschende Konfiguration in der Liste **Name** aus, und klicken Sie dann auf **Entfernen**. Ein Dialogfeld wird angezeigt, in dem Sie bestätigen, dass Sie diese Konfiguration wirklich löschen möchten.
3. Klicken Sie auf **Löschen**.

     Die Dienstkonfigurationsdatei wird aus dem Azure-Projekt im Projektmappen-Explorer entfernt.

### <a name="to-rename-a-service-configuration"></a>So benennen Sie eine Dienstkonfiguration um
1. Öffnen Sie in Projektmappen-Explorer das Kontextmenü für das Azure-Projekt, und klicken Sie dann auf **Konfigurationen verwalten**.

    Das Dialogfeld **Dienstkonfigurationen verwalten** wird angezeigt.
2. Wählen Sie die neue Dienstkonfiguration in der Liste **Name** aus, um die Dienstkonfiguration umzubenennen, und klicken Sie dann auf **Umbenennen**. Geben Sie im Textfeld **Name** den Namen ein, den Sie für diese Dienst Konfiguration verwenden möchten, und klicken Sie dann auf **OK**.

    Der Name der Dienstkonfigurationsdatei wird im Azure-Projekt im Projektmappen-Explorer geändert.

### <a name="to-change-a-service-configuration"></a>So ändern Sie eine Dienstkonfiguration
* Wenn Sie eine Dienstkonfiguration ändern möchten, öffnen Sie das Kontextmenü für die jeweilige Rolle, die Sie im Azure-Projekt ändern möchten. Klicken Sie dann auf **Eigenschaften**. Weitere Informationen finden Sie unter [Konfigurieren der Rollen für einen Azure-Clouddienst mit Visual Studio](vs-azure-tools-configure-roles-for-cloud-service.md).

## <a name="make-different-setting-combinations-by-using-profiles"></a>Erstellen verschiedener Einstellungskombinationen mithilfe von Profilen
Mithilfe eines Profils können Sie den **Veröffentlichungs-Assistenten** mit verschiedenen Kombinationen von Einstellungen für unterschiedliche Verwendungszwecke automatisch auffüllen. Beispielsweise können Sie ein Profil für Debugging und ein weiteres für Releasebuilds verwenden. In diesem Fall ist im **Debug** -Profil **IntelliTrace** aktiviert und die **Debug** -Konfiguration ausgewählt, und im **Release** -Profil wäre **IntelliTrace** deaktiviert und die **Release** -Konfiguration ausgewählt. Sie können auch verschiedene Profile verwenden, um einen Dienst mithilfe eines anderen Speicherkontos bereitzustellen.

Wenn Sie den Assistenten zum ersten Mal ausführen, wird ein Standardprofil erstellt. Visual Studio speichert das Profil in einer AZUREPUBXML-Datei, die Ihrem Azure-Projekt unter dem Ordner **Profile** hinzugefügt wird. Wenn Sie den Assistenten später ausführen und manuell andere Optionen angeben, wird die Datei automatisch aktualisiert. Bevor Sie die folgende Prozedur ausführen, sollten Sie den Clouddienst bereits mindestens einmal veröffentlicht haben.

### <a name="to-add-a-profile"></a>So fügen Sie ein Profil hinzu
1. Öffnen Sie das Kontextmenü des Azure-Projekts, und klicken Sie auf **Veröffentlichen**.
2. Klicken Sie wie in der folgenden Abbildung gezeigt neben der Liste **Zielprofil** auf die Schaltfläche **Profil speichern**. Dadurch wird ein Profil für Sie erstellt.

    ![Erstellen eines neuen Profils](./media/vs-azure-tools-service-configurations-and-profiles-how-to-manage/create-new-profile.png)
3. Nach dem Erstellen des Profils klicken Sie in der Liste **Zielprofil** auf **<Verwalten…>**.

    Das Dialogfeld **Profile verwalten** wird angezeigt, wie in der folgenden Abbildung gezeigt.

    ![Dialogfeld "Profile verwalten"](./media/vs-azure-tools-service-configurations-and-profiles-how-to-manage/manage-profiles.png)
4. Wählen Sie in der Liste **Name** ein Profil aus, und klicken Sie dann auf **Kopie erstellen**.
5. Klicken Sie auf die Schaltfläche **Schließen**.

    Das neue Profil wird in der Liste "Zielprofil" angezeigt.
6. Klicken Sie in der Liste **Zielprofil** auf das soeben erstellte Profil. Die Einstellungen des Veröffentlichungs-Assistenten werden mit den Optionen aus dem ausgewählten Profil aufgefüllt.
7. Klicken Sie auf die Schaltflächen **Zurück** und **Weiter** , um die einzelnen Seiten des Veröffentlichungs-Assistenten anzuzeigen, und passen Sie dann die Einstellungen für dieses Profil an. Informationen hierzu finden Sie unter [Assistent zum Veröffentlichen der Azure-Anwendung](vs-azure-tools-publish-azure-application-wizard.md) .
8. Klicken Sie nach dem Anpassen der Einstellungen auf **Weiter** , um zur Seite „Einstellungen“ zurückzukehren. Das Profil wird gespeichert, wenn Sie den Dienst mit diesen Einstellungen veröffentlichen oder auf die Schaltfläche **Speichern** neben der Liste mit den Profilen klicken.

### <a name="to-rename-or-delete-a-profile"></a>So benennen Sie ein Profil um oder löschen es
1. Öffnen Sie das Kontextmenü des Azure-Projekts, und klicken Sie auf **Veröffentlichen**.
2. Klicken Sie in der Liste **Zielprofil** auf **Verwalten**.
3. Wählen Sie im Dialogfeld **Profile verwalten** das zu löschende Profil aus, und klicken Sie dann auf **Entfernen**.
4. Klicken Sie im angezeigten Bestätigungsdialogfeld auf **OK**.
5. Klicken Sie auf **Schließen**.

### <a name="to-change-a-profile"></a>So ändern Sie ein Profil
1. Öffnen Sie das Kontextmenü des Azure-Projekts, und klicken Sie auf **Veröffentlichen**.
2. Klicken Sie in der Liste **Zielprofil** auf das Profil, das Sie ändern möchten.
3. Klicken Sie auf die Schaltflächen **Zurück** und **Weiter** , um die einzelnen Seiten des Veröffentlichungs-Assistenten anzuzeigen, und ändern Sie dann die gewünschten Einstellungen an. Informationen hierzu finden Sie unter [Assistent zum Veröffentlichen der Azure-Anwendung](vs-azure-tools-publish-azure-application-wizard.md) .
4. Klicken Sie nach dem Ändern der Einstellungen auf **Weiter** , um zur Seite **Einstellungen** zurückzukehren.
5. (Optional) Klicken Sie auf **Veröffentlichen** , um den Clouddienst mit den neuen Einstellungen zu veröffentlichen. Wenn Sie den Clouddienst nicht unmittelbar veröffentlichen möchten und den Veröffentlichungs-Assistenten schließen, werden Sie von Visual Studio gefragt, ob Sie die Änderungen am Profil speichern möchten.

## <a name="next-steps"></a>Nächste Schritte
Weitere Informationen zum Konfigurieren anderer Teile des Azure-Projekts in Visual Studio finden Sie unter [Konfigurieren eines Azure-Projekts](vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address.md).
