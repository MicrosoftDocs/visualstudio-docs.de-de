---
title: Erweitern einer Testversion oder Aktualisieren einer Lizenz
description: Erfahren Sie, wie Sie eine kostenlose Testversion von Visual Studio verlängern, ein Onlineabonnement oder einen Produktschlüssel zum Freischalten von Visual Studio verwenden und eine veraltete oder abgelaufene Lizenz aktualisieren können.
ms.date: 12/18/2019
ms.topic: conceptual
ms.assetid: ffb580a1-8b5d-48f5-b811-87f8036f50ea
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.openlocfilehash: 3dd2a688ef70064f44caccfd7c64150b7c649769
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869127"
---
# <a name="extend-a-trial-version-or-update-a-license"></a>Erweitern einer Testversion oder Aktualisieren einer Lizenz

Sie können eine kostenlose Testversion von [Visual Studio Professional oder Visual Studio Enterprise](https://visualstudio.microsoft.com/vs/compare/) für 30 Tage testen. Und wenn Sie sich anmelden, können Sie den Testzeitraum auf 90 Tage verlängern. (Visual Studio Community ist ohne Testzeitraum kostenlos. Allerdings müssen Sie sich regelmäßig [anmelden](signing-in-to-visual-studio.md), um Ihre [Lizenz auf dem neuesten Stand zu halten](#update-a-stale-license).)

Um Visual Studio nach Ablauf des Testzeitraums weiterhin zu verwenden, schalten Sie es mit einem [Onlineabonnement](#use-an-online-subscription) oder einem [Product Key](#enter-a-product-key) frei.

## <a name="use-an-online-subscription"></a>Verwenden eines Onlineabonnements

1. Wählen Sie die Schaltfläche **Anmelden** in der rechten oberen Ecke der IDE aus (oder wechseln Sie zu **Datei** > **Kontoeinstellungen**, um das Dialogfeld **Kontoeinstellungen** zu öffnen, und wählen Sie dann die Schaltfläche **Anmelden** aus).

1. Geben Sie die Anmeldeinformationen für ein Microsoft-Konto oder ein Geschäfts- bzw. Schulkonto ein. Visual Studio sucht daraufhin nach einem Visual Studio-Abonnement oder einer Azure DevOps-Organisation, die Ihrem Konto zugeordnet sind.

> [!IMPORTANT]
> Visual Studio sucht automatisch nach mit dem Konto verknüpften Onlineabonnements, wenn Sie eine Verbindung mit einer Azure DevOps-Organisation im **Team Explorer**-Toolfenster herstellen. Wenn Sie eine Verbindung mit einer Azure DevOps-Organisation herstellen, können Sie sich sowohl mithilfe von Microsoft- als auch mit Geschäfts-, Schul- oder Unikonten anmelden. Wenn ein Onlineabonnement für dieses Benutzerkonto vorhanden ist, wird die IDE-Schnittstelle automatisch durch Visual Studio für Sie entsperrt.

Weitere Informationen zu Visual Studio-Abonnements und deren Funktionsweise finden Sie auf der Seite zu den [Häufig gestellten Fragen (FAQ) zum Support für Abonnements](https://visualstudio.microsoft.com/subscriptions/support/).

## <a name="enter-a-product-key"></a>Eingeben eines Product Keys

1. Klicken Sie auf **Datei** > **Kontoeinstellungen**, um das Dialogfeld **Kontoeinstellungen** zu öffnen, und klicken Sie auf den Link **Mit einem Product Key lizenzieren**.

1. Geben Sie den Product Key an der dafür vorgesehenen Stelle ein.

> [!TIP]
> Vorabversionen von Visual Studio verfügen über keine Product Keys. Sie müssen sich bei der IDE-Schnittstelle anmelden, um Vorabversionen zu verwenden.

Weitere Informationen zu Visual Studio-Product Keys und dazu, wie Sie diese erhalten, finden Sie auf der Seite [Verwenden von Product Keys in Visual Studio-Abonnements](/visualstudio/subscriptions/product-keys).

## <a name="update-a-stale-license"></a>Aktualisieren einer veralteten Lizenz

In Visual Studio wird möglicherweise eine Meldung angezeigt, die besagt, dass Ihre Lizenz abgelaufen ist und aktualisiert werden muss.

![Visual Studio-Meldung zu abgelaufener Lizenz](../ide/media/vs2017_stale-license.png)

Diese Meldung gibt an, dass Ihr Abonnement zwar ggf. noch immer gültig ist, das von Visual Studio für Ihr Abonnement verwendete Lizenztoken jedoch nicht aktualisiert wurde. Visual Studio meldet, dass die Lizenz aus einem der folgenden Gründe veraltet ist:

* Sie haben Visual Studio nicht verwendet oder Sie haben über einen längeren Zeitraum keine Verbindung zum Internet hergestellt.
* Sie haben sich bei Visual Studio abgemeldet.

Bevor das Lizenztoken abläuft, zeigt Visual Studio eine Warnmeldung an, in der Sie aufgefordert werden, Ihre Anmeldeinformationen erneut einzugeben.

Wenn Sie Ihre Anmeldeinformationen nicht erneut eingeben, beginnt der Ablaufzeitraum für das Token, und im Dialogfeld **Kontoeinstellungen** wird angezeigt, wie viele Tage noch verbleiben, bevor das Token abläuft. Nachdem Ihr Token abgelaufen ist, müssen Sie Ihre Anmeldeinformationen für das Konto neu eingeben, bevor Sie Visual Studio weiter verwenden können.

> [!Important]
> Bei Verwendung von Visual Studio für einen längeren Zeitraum in Umgebungen mit wenig oder keinem Internetzugang sollten Sie einen Product Key verwenden, um Visual Studio zu entsperren, um Unterbrechungen zu vermeiden.

## <a name="update-an-expired-license"></a>Aktualisieren einer abgelaufenen Lizenz

Wenn Ihr Abonnement abgelaufen ist und Sie keine Zugriffsrechte mehr für Visual Studio besitzen, müssen Sie Ihr Abonnement erneuern oder ein anderes Konto hinzufügen, das über ein Abonnement verfügt. Wechseln Sie zu **Datei** > **Kontoeinstellungen**, um weitere Informationen über die verwendete Lizenz zu erhalten. Die Lizenzinformationen werden auf der rechten Seite des Dialogfelds angezeigt. Wenn Sie über ein weiteres Abonnement verfügen, das mit einem anderen Konto verknüpft ist, fügen Sie dieses Konto zur Liste **Alle Konten** auf der linken Seite des Dialogfelds hinzu, indem Sie auf den Link **Konto hinzufügen** klicken.

## <a name="get-support"></a>Support

Manchmal geht etwas schief. Wenn Sie ein Problem haben, finden Sie hier einige Supportoptionen:

* Melden Sie Produktprobleme mit dem Tool [Problem melden](how-to-report-a-problem-with-visual-studio.md).
* Hier finden Sie Antworten auf Fragen zu Abonnements, Konten und Abrechnung auf der Seite zu den [Häufig gestellten Fragen (FAQ) zum Support für Abonnements](https://visualstudio.microsoft.com/subscriptions/support/).

## <a name="see-also"></a>Weitere Informationen

* [Anmelden bei Visual Studio](../ide/signing-in-to-visual-studio.md)
* [Vergleichen von Visual Studio-Editionen](https://visualstudio.microsoft.com/vs/compare/)
* [Weitere Informationen zu Visual Studio-Abonnements](/visualstudio/subscriptions/)
