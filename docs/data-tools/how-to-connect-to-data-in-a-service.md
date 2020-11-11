---
title: 'Gewusst wie: Herstellen einer Verbindung mit Daten in einem Dienst'
description: Verbinden Sie Ihre APP mit Daten, die von einem Dienst zurückgegeben werden, indem Sie den Assistenten zum Konfigurieren von Datenquellen ausführen und auf der Seite Daten Quellentyp auswählen die Option Dienst auswählen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- data [Visual Studio], connecting to web services
- data sources, creating from web services
- data [Visual Studio], reading from web services
- reading data, from web services
- web services, reading data
- web services, as data sources
- web services, connecting
ms.assetid: a6b54353-05fe-4e5c-8631-90231fc95504
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 3c565f7238edf9126dd651fa567de82aed7b8d21
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94435012"
---
# <a name="how-to-connect-to-data-in-a-service"></a>Vorgehensweise: Herstellen einer Verbindung mit Daten in einem Dienst

Sie verbinden Ihre Anwendung mit den Daten, die von einem Dienst zurückgegeben werden, indem Sie den [Assistenten zum Konfigurieren von Datenquellen](../data-tools/media/data-source-configuration-wizard.png) ausführen und auf der Seite **Daten Quellentyp auswählen** die Option **Dienst** auswählen.

Nach Abschluss des Assistenten wird dem Projekt ein Dienst Verweis hinzugefügt, der sofort im [Datenquellen Fenster](add-new-data-sources.md#data-sources-window)verfügbar ist.

> [!NOTE]
> Die im Fenster **Datenquellen** angezeigten Elemente hängen von den vom Dienst zurückgegebenen Informationen ab. Einige Dienste stellen möglicherweise nicht genügend Informationen bereit, damit der **Assistent zum Konfigurieren von Datenquellen** bindbare Objekte erstellen kann. Wenn der Dienst beispielsweise ein nicht typisiertes DataSet zurückgibt, werden beim Abschließen des Assistenten keine Elemente im **Datenquellen** Fenster angezeigt. Dies liegt daran, dass nicht typisierte Datasets kein Schema bereitstellen, sodass der Assistent nicht über genügend Informationen zum Erstellen der Datenquelle verfügt.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-connect-your-application-to-a-service"></a>So verbinden Sie Ihre Anwendung mit einem Dienst

1. Klicken Sie im Menü **Daten** auf **Neue Datenquelle hinzufügen**.

2. Wählen Sie auf der Seite **Daten Quellentyp auswählen** die Option **Dienst** aus, und klicken Sie dann auf **weiter**.

3. Geben Sie die Adresse des Diensts ein, den Sie verwenden möchten, oder klicken Sie auf **ermitteln** , um die Dienste in der aktuellen Projekt Mappe zu suchen, **und klicken Sie dann auf**

4. Optional können Sie anstelle des Standardwerts einen neuen **Namespace** eingeben.

    > [!NOTE]
    > Klicken Sie auf **erweitert** , um das [Dialogfeld Dienst Verweis konfigurieren](../data-tools/configure-service-reference-dialog-box.md)zu öffnen.

5. Klicken Sie auf **OK** , um dem Projekt einen Dienst Verweis hinzuzufügen.

6. Klicken Sie auf **Fertig stellen**.

     Die Datenquelle wird dem Fenster **Datenquellen** hinzugefügt.

## <a name="next-steps"></a>Nächste Schritte

Wenn Sie der Anwendung Funktionen hinzufügen möchten, wählen Sie im Fenster **Datenquellen** ein Element aus, und ziehen Sie es auf ein Formular, um gebundene Steuerelemente zu erstellen. Weitere Informationen finden Sie unter [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="see-also"></a>Siehe auch

- [Binden von WPF-Steuerelementen an einen WCF-Datendienst](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)
- [Windows Communication Foundation Dienste und WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
