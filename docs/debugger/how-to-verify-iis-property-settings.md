---
title: Überprüfen von IIS-Eigenschafteneinstellungen | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie Sie IIS-Eigenschafteneinstellungen überprüfen, die Sie mithilfe des IIS-Verwaltungstools für eine Webanwendung festlegen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- IIS, property settings
- debugging Web applications, troubleshooting
- IIS administration tool
- Web applications, setting properties
- properties [debugger], setting with IIS administration tool
ms.assetid: 9efc50bf-02fb-4750-9b3e-f03c38f10d8b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2ed11efb0d493844456d2493153a41df140095cc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99853117"
---
# <a name="how-to-verify-iis-property-settings"></a>Vorgehensweise: Überprüfen von IIS-Eigenschafteneinstellungen

Sie können die Eigenschaften für eine Webanwendung mit dem IIS-Verwaltungstool festlegen. Diese Eigenschaften müssen korrekt festgelegt sein, damit die Anwendung ausgeführt werden kann. Das Überprüfen dieser Einstellungen ist daher ein häufig erforderlicher Schritt bei der Fehlerbehebung.

> [!NOTE]
> Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Reset settings (Zurücksetzen der Einstellungen)](../ide/environment-settings.md#reset-settings).

## <a name="to-check-iis-settings-for-the-web-application"></a>So überprüfen Sie die IIS-Einstellungen der Webanwendung

1. Öffnen Sie das Fenster **Verwaltungstools**: Zeigen Sie im Menü **Start** auf **Programme**, und klicken Sie dann auf **Verwaltungstools**. Falls der Eintrag **Verwaltung** nicht im Menü **Programme** vorhanden ist, befindet er sich in der **Systemsteuerung**.

   - Unter Windows 2000 klicken Sie auf **Internetdienste-Manager**.

   - Unter Windows XP wählen Sie **Internetinformationsdienste**.

   - Unter Windows Server 2003 doppelklicken Sie auf **Serververwaltung**.

        Das Fenster **Serververwaltung** wird geöffnet. Klicken Sie im Bereich **Anwendungsserver** auf **Diesen Anwendungsserver verwalten**.

        Das Fenster **Anwendungsserver** wird geöffnet. Erweitern Sie im linken Bereich den Knoten **Internetinformationsdienste-Manager**.

2. Klicken Sie im Dialogfeld in der Strukturansicht auf den Knoten für den Computer. Klicken Sie auf den Knoten **Websites**, und wählen Sie den Knoten der Webanwendung aus. Dies ist entweder ein Websiteknoten (also ein gleichgeordneter Knoten des Knotens **Standardwebsite**) oder ein virtueller Verzeichnisknoten unter einem vorhandenen Websiteknoten.

3. Klicken Sie mit der rechten Maustaste auf die Webanwendung, und klicken Sie im Kontextmenü auf **Eigenschaften**.

4. Überprüfen Sie die Sicherheitseinstellungen für die Webanwendung:

   1. Wählen Sie im **Eigenschaftenfenster** der Webanwendung die Registerkarte **Verzeichnissicherheit** aus, und klicken Sie auf **Bearbeiten**.

   2. Aktivieren Sie im Dialogfeld **Authentifizierungsmethoden** die Optionen **Anonymen Zugriff aktivieren** und **Integrierte Windows-Authentifizierung**, falls sie nicht bereits aktiviert sind.

   3. Klicken Sie auf **OK**, um das Dialogfeld **Authentifizierungsmethoden** zu schließen.

5. Bei ATL-Serveranwendungen müssen Sie sicherstellen, dass das Verb DEBUG mit der ISAPI-Erweiterung verknüpft ist. Weitere Informationen finden Sie unter [Vorgehensweise: Zuordnen des DEBUG-Verbs zur Erweiterung](/previous-versions/ms165022(v=vs.100)).

6. Stellen Sie bei einer [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Anwendung sicher, dass für das virtuelle Verzeichnis der Anwendung in **Internetinformationsdienste-Manager**, **Internetdienste-Manager** bzw. **Internetinformationsdienste** ein Anwendungsname festgelegt ist.

   1. Klicken Sie im **Eigenschaftenfenster** der Webanwendung auf die Registerkarte **Verzeichnis**, wenn sich die Anwendung in einem virtuellen Verzeichnis befindet, bzw. auf die Registerkarte **Basisverzeichnis**, wenn sich die Anwendung in einer Website befindet.

   2. Vergewissern Sie sich, dass der Name in **Lokaler Pfad** mit dem Namen des Verzeichnisses übereinstimmt, in dem die Anwendung bereitgestellt wurde.

   3. Geben Sie unter **Anwendungseinstellungen** den Namen des Stammverzeichnisses ein, in dem die Anwendung enthalten ist.

   4. Klicken Sie auf **OK**, um das Dialogfeld **Eigenschaften** zu schließen.

7. Klicken Sie bei einer [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Anwendung auf die Registerkarte **ASP.NET**, und vergewissern Sie sich, dass die richtige Version von [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] angegeben ist.

8. Klicken Sie auf **OK**, um das Dialogfeld **Eigenschaften** zu schließen.

9. Klicken Sie auf **OK**, um das Dialogfeld **Internetinformationsdienste-Manager**, **Internetdienste-Manager** bzw. **Internetinformationsdienste** zu schließen.

## <a name="see-also"></a>Siehe auch

- [Problembehandlung](../debugger/debugging-web-applications-troubleshooting.md)