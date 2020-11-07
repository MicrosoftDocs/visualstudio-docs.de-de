---
title: Installieren der erforderlichen Komponenten mit einer ClickOnce-App
description: Erfahren Sie, wie Sie erforderliche Komponenten auswählen, die zusammen mit der ClickOnce-Anwendung verpackt werden sollen, wenn Sie installiert ist.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], prerequisites
- prerequisites, ClickOnce
- components, bootstrapping
ms.assetid: e964fca5-fdfd-47cf-a1c9-7fb96b1c88b5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e4a2f2b951881208d3995aeb1f5f1f655b80674f
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94349931"
---
# <a name="how-to-install-prerequisites-with-a-clickonce-application"></a>Vorgehensweise: Installieren von erforderlichen Komponenten mit einer ClickOnce-Anwendung
Alle [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungen erfordern, dass die richtige Version der .NET Framework auf einem Computer installiert ist, bevor Sie ausgeführt werden können. viele Anwendungen haben ebenfalls andere Voraussetzungen. Beim Veröffentlichen einer- [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung können Sie einen Satz von erforderlichen Komponenten auswählen, der zusammen mit der Anwendung verpackt werden soll. Zum Zeitpunkt der Installation wird für jede erforderliche Komponente eine Überprüfung durchgeführt, um festzustellen, ob Sie bereits vorhanden ist. Wenn dies nicht der Fall ist, wird er vor der Installation der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung installiert.

 Anstatt die Voraussetzungen zu verpacken und zu veröffentlichen, können Sie auch einen Download Speicherort für die Komponenten angeben. Anstatt die Voraussetzungen für jede von Ihnen veröffentlichte Anwendung einzuschließen, können Sie z. b. eine zentralisierte Dateifreigabe oder einen Webspeicherort verwenden, die die Installationsprogramme für alle ihre Voraussetzungen enthält – zur Installationszeit werden die Komponenten heruntergeladen und von diesem Speicherort aus installiert.

> [!IMPORTANT]
> Sie sollten dem Entwicklungs Computer erforderliche Installer-Pakete hinzufügen, bevor Sie die erste [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung veröffentlichen. Weitere Informationen finden Sie unter Gewusst [wie: einschließen von erforderlichen Komponenten mit einer ClickOnce-Anwendung](../deployment/how-to-include-prerequisites-with-a-clickonce-application.md).

 Erforderliche Komponenten werden **im Dialogfeld** erforderliche Komponenten verwaltet, das über den Bereich **veröffentlichen** des **Projekt-Designers** zugänglich ist.

> [!NOTE]
> Zusätzlich zur vordefinierten Liste der Voraussetzungen können Sie der Liste eigene Komponenten hinzufügen. Weitere Informationen finden Sie unter [Erstellen von Bootstrapperpaketen](../deployment/creating-bootstrapper-packages.md).

### <a name="to-specify-prerequisites-to-install-with-a-clickonce-application"></a>So geben Sie Voraussetzungen für die Installation mit einer ClickOnce-Anwendung an

1. Wenn ein Projekt in **Projektmappen-Explorer** ausgewählt ist, klicken Sie im Menü **Projekt** auf **Eigenschaften**.

2. Wählen Sie den Bereich **veröffentlichen** aus.

3. Klicken Sie auf die Schaltfläche erforderliche **Prerequisites** Komponenten, **um das Dialog** Feld erforderliche Komponenten anzuzeigen

4. Stellen Sie im Dialogfeld **Erforderliche Komponenten** sicher, dass das Kontrollkästchen **Setupprogramm zur Installation erforderlicher Komponenten erstellen** aktiviert ist.

5. Überprüfen Sie in der Liste der **Voraussetzungen** die Komponenten, die Sie installieren möchten, und klicken Sie dann auf **OK**.

     Die ausgewählten Komponenten werden zusammen mit Ihrer Anwendung verpackt und veröffentlicht.

### <a name="to-specify-a-different-download-location-for-prerequisites"></a>So geben Sie einen anderen Download Speicherort für erforderliche Komponenten an

1. Wenn ein Projekt in **Projektmappen-Explorer** ausgewählt ist, klicken Sie im Menü **Projekt** auf **Eigenschaften**.

2. Wählen Sie den Bereich **veröffentlichen** aus.

3. Klicken Sie auf die Schaltfläche erforderliche **Prerequisites** Komponenten, **um das Dialog** Feld erforderliche Komponenten anzuzeigen

4. Stellen Sie im Dialogfeld **Erforderliche Komponenten** sicher, dass das Kontrollkästchen **Setupprogramm zur Installation erforderlicher Komponenten erstellen** aktiviert ist.

5. Wählen Sie im Abschnitt **Installationsort für** erforderliche Komponenten angeben die Option erforderliche Komponenten **von folgendem Speicherort herunterladen aus**.

6. Wählen Sie einen Speicherort aus der Dropdown Liste aus, oder geben Sie URL, Dateipfad oder FTP-Speicherort ein, und klicken Sie dann auf **OK.**

    > [!NOTE]
    > Sie müssen sicherstellen, dass die Installationsprogramme für die angegebenen Komponenten an der angegebenen Position vorhanden sind.

## <a name="see-also"></a>Weitere Informationen
- [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)
- [Gewusst wie: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)