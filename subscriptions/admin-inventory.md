---
title: Inventur von Präproduktionsumgebungen | Visual Studio Marketplace
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 7d74e113-8fb2-490e-8502-48cce7b1327a
ms.date: 03/06/2020
ms.topic: conceptual
description: Hier erfahren Sie mehr über die Aufgaben eines Administrators bei der Inventur der Präproduktionsumgebung.
ms.openlocfilehash: 1abc3c15a7bd9e47b0f449c5a49fdbbc8e7bb590
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/22/2020
ms.locfileid: "91004156"
---
# <a name="inventory-of-pre-production-environment"></a>Inventur der Präproduktion
Visual Studio-Abonnements vereinfachen das Ressourcenmanagement, indem die Anzahl der Benutzer und nicht die der Geräte im Vordergrund steht.

Visual Studio-Administratoren müssen Visual Studio-Abonnements **bestimmten Personen** zuweisen. Namenskonventionen wie „Dev1“, „Dev2“ oder die Verwendung von Teamnamen wie „FeatureTeam“ sind **nicht zulässig**.

Im Folgenden werden einige Möglichkeiten aufgelistet, um das Inventar Ihrer Präproduktionsumgebung zu vereinfachen:
- Prüfen Sie die Benutzerzuweisungen. Es gibt eine Website von Microsoft mit dem Namen [Visual Studio Administration Portal (Visual Studio-Administrationsportal)](https://manage.visualstudio.com/), die Ihnen dabei helfen soll, die Zuweisungen von Visual Studio-Abonnements nachzuverfolgen.
- Verwenden Sie eine lokale oder cloudbasierte Version von Active Directory, um Benutzer aufzulisten. Wenn Sie Active Directory verwenden, um den Benutzerzugriff zu verwalten, können Sie möglicherweise Entwicklungs- und Testbenutzer anhand Ihrer Directory-Mitgliedschaft erkennen.
- Verwenden Sie automatisierte Tools, um eine Inventur für Systeme durchzuführen. Möglicherweise müssen Sie auch ein Tool für die Softwareinventur verwenden, um Ihre Softwareobjekte besser verwalten und Präproduktionsumgebungen von Produktionsumgebungen unterscheiden zu können. Viele Kunden des Microsoft System Center erstellen Namenskonventionen, um die Automatisierung dieses Teils des Inventurprozesses voranzubringen.
- Lassen Sie sich bei der manuellen Abstimmung helfen. Erstellen Sie eine Liste Ihrer Mitarbeiter, damit Sie die Entwicklungs- und Testbenutzer auf die Entwicklungs- und Testumgebungen abstimmen können.

## <a name="resources"></a>Ressourcen
- [Whitepaper zur Visual Studio-Lizenzierung](https://visualstudio.microsoft.com/wp-content/uploads/2019/06/Visual-Studio-Licensing-Whitepaper-May-2019.pdf)
- [Support für die Verwaltung von Visual Studio und Abonnements](https://visualstudio.microsoft.com/support/support-overview-vs)
- [Nutzungsbedingungen für die Volumenlizenzierung](https://www.microsoft.com/licensing/product-licensing/products.aspx)

## <a name="see-also"></a>Weitere Informationen
- [Dokumentation zu Visual Studio](/visualstudio/)
- [Dokumentation zu Azure DevOps](/azure/devops/)
- [Azure-Dokumentation](/azure/)
- [Dokumentation zu Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Nächste Schritte
Weitere Informationen zu den Aufgaben von Administratoren:
- [Administratoraufgaben](admin-responsibilities.md)
- [Verwalten von großen Teams und externen Vertragspartnern](manage-teams.md)
- [Nachverfolgen von Benutzerzuweisungen und Verarbeiten von Bestellungen](assignments-orders.md)
- Verwenden des Berichts [Maximum Usage](maximum-usage.md) (Maximale Auslastung) zum Nachverfolgen von Kaufverpflichtungen