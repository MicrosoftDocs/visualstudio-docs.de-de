---
title: Zugreifen auf virtuelle Azure-Computer über den Server-Explorer | Microsoft Docs
description: In diesem Artikel erhalten Sie einen Überblick darüber, wie virtuelle Azure-Computer im Server-Explorer von Visual Studio angezeigt, erstellt und verwaltet werden können.
author: ghogen
manager: jillfra
assetId: eb3afde6-ba90-4308-9ac1-3cc29da4ede0
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/31/2017
ms.author: ghogen
ms.openlocfilehash: a9ca956400956ae337d8d1e0f5a881f1dc4c6377
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2020
ms.locfileid: "93398552"
---
# <a name="accessing-azure-virtual-machines-from-server-explorer"></a>Zugreifen auf virtuelle Computer in Azure über den Server-Explorer

Wenn Sie in Azure gehostete virtuelle Computer verwenden, können Sie über den Server-Explorer auf diese Computer zugreifen. Sie müssen sich zunächst bei Ihrem Azure-Abonnement anmelden, um die mobilen Dienste anzeigen zu können. Öffnen Sie das Kontextmenü für den Azure-Knoten, und wählen Sie **Verbindung mit Microsoft Azure-Abonnement herstellen** aus, um sich anzumelden.

1. Wählen Sie im Cloud-Explorer einen virtuellen Computer aus, und drücken Sie anschließend die F4-Taste, um das Eigenschaftenfenster für den Computer anzuzeigen.

    Die folgende Tabelle zeigt, welche Eigenschaften verfügbar sind – diese jedoch alle schreibgeschützt. Sie können sie über das [Azure-Portal](https://portal.azure.com) ändern.

   | Eigenschaft | Beschreibung |
   | --- | --- |
   | DNS-Name |Die URL mit der Internetadresse des virtuellen Computers. |
   | Environment |Für einen virtuellen Computer lautet der Wert dieser Eigenschaft immer "Produktion". |
   | Name |Der Name des virtuellen Computers. |
   | Size |Die Größe des virtuellen Computers. Diese Eigenschaft gibt die Menge an verfügbarem Arbeitsspeicher und Festplattenspeicher an. Weitere Informationen finden Sie unter [Größen virtueller Computer](/azure/cloud-services/cloud-services-sizes-specs). |
   | Status |Mögliche Werte lauten "Wird gestartet", "Gestartet", "Wird angehalten", "Angehalten" und "Status wird abgerufen". Wird "Status wird abgerufen" angezeigt, ist der aktuelle Status unbekannt. Die Werte für diese Eigenschaft unterscheiden sich von den Werten, die im [Azure-Portal](https://portal.azure.com) verwendet werden. |
   | SubscriptionID |Die Abonnement-ID für Ihr Azure-Konto. Sie können diese Informationen im [Azure-Portal](https://portal.azure.com) anzeigen, indem Sie die Eigenschaften für ein Abonnement öffnen. |
2. Wählen Sie einen Endpunktknoten aus, und zeigen Sie dann das Fenster **Eigenschaften** an.
3. Die folgende Tabelle beschreibt die verfügbaren Endpunkteigenschaften. Alle Eigenschaften sind schreibgeschützt. Verwenden Sie zum Hinzufügen oder Bearbeiten der Endpunkte für einen virtuellen Computer das [Azure-Portal](https://portal.azure.com).

   | Eigenschaft | Beschreibung |
   | --- | --- |
   | Name |Ein Bezeichner für den Endpunkt. |
   | Privater Port |Der Port für den internen Netzwerkzugriff auf Ihre Anwendung. |
   | Protocol |Das Protokoll, das von der Transportschicht für diesen Endpunkt verwendet wird – entweder TCP oder UDP. |
   | Öffentlicher Port |Der Port, der für den öffentlichen Zugang auf Ihrer Anwendung verwendet wird. |
