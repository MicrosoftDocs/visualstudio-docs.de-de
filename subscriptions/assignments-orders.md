---
title: Nachverfolgen der Zuweisungen und Verarbeitung von Aufträgen in Visual Studio-Abonnements | Visual Studio Marketplace
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 83a9162a-b9e7-43a4-b07f-6c1fd8580f78
ms.date: 03/02/2020
ms.topic: conceptual
description: Erfahren Sie mehr über die Verantwortung von Administratoren hinsichtlich des Nachverfolgens von Benutzerzuweisungen und des Verarbeitens von Aufträgen.
ms.openlocfilehash: 90de1c426a387cb27fe35990394a41d34c1172ce
ms.sourcegitcommit: bf5e2bba5acdcf05869b861211f8bb755081e5ce
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2020
ms.locfileid: "92467413"
---
# <a name="track-user-assignment-and-process-orders"></a>Nachverfolgen der Benutzerzuweisungen und der Verarbeitung von Aufträgen
Es wird von Administratoren für Visual Studio-Abonnements erwartet, dass sie die Nutzung von Visual Studio und die Verarbeitung von Aufträgen nachverfolgen und darauf achten, ob die Nutzung im Vergleich zu dem Zeitplan angestiegen ist, der in der Volumenlizenzierungsvereinbarung oder der Microsoft Produkt- und Servicevereinbarung festgelegt wurde. Das neue Administrationsportal für Visual Studio-Abonnements hat zur Vereinfachung dieser Aufgabe einen einfachen, hilfreichen Tracker implementiert, der die verfügbaren und bereits verwendeten Lizenzen anzeigt.

## <a name="maximum-usage"></a>Maximale Nutzung
**Ihr Unternehmen ist dazu verpflichtet, Visual Studio-Abonnements unmittelbar zu erwerben, wenn:**
- Einem Benutzer eine Lizenz zugewiesen wird **ODER**
- Ein Benutzer mit Visual Studio-Software interagiert

Die Verpflichtung zum Kauf wird anhand der maximalen Anzahl an Abonnements festgelegt, die Sie Benutzern zuweisen. Diese Ebene der Abonnementzuweisung gilt entweder für die täglichen Zuweisungen an Benutzer oder für die Anzahl der Benutzer, die mit Visual Studio-Software interagieren. Dabei gilt immer der höhere der beiden Werte.

- Das Zuweisen von Visual Studio-Abonnements zu weiteren Benutzern erhöht die maximale Nutzungsebene.  
- Administratoren von Visual Studio-Abonnements können die zugewiesene Abonnementstufe für eine Einzelperson unter Umständen ändern. Dabei wird die Abonnementstufe des einen Benutzers erhöht und dafür die des anderen herabgestuft. Wenn Sie das Abonnement eines zugewiesenen Abonnenten herabstufen, muss diese Person alle Produkte, die nur im höheren Abonnement enthalten sind, beenden und deinstallieren. 
- Administratoren von Visual Studio-Abonnements können Abonnements nach 90 Tagen ab der ursprünglichen Zuweisung erneut von einem Benutzer an einen anderen übertragen. 
    > [!NOTE]
    > Dafür müssen sie zunächst das bereits vorhandene Abonnement entfernen und ein neues hinzufügen, um zu vermeiden, dass die maximale Nutzungsebene künstlich in die Höhe getrieben wird. 
- Der Bericht [Maximale Auslastung](maximum-usage.md) im [Portal für die Verwaltung von Visual Studio-Abonnements](https://manage.visualstudio.com) bietet Unterstützung beim Überwachen der maximalen Auslastung Ihrer Organisation. 

## <a name="monthly-subscriptions-open-license-or-open-value"></a>Monatsabonnements, Open License oder Open Value
Möglicherweise weisen Sie Abonnements monatlich über Programme wie „Open License“ und „Open Value“ oder über den Visual Studio Marketplace zu. Wenn dies der Fall ist, müssen Sie Ihre Bestellung für zusätzliche Benutzer in dem Monat verarbeiten, in dem diese (Mitarbeiter oder externe Vertragspartner) mit der Interaktion mit lizenzierter Visual Studio-Software beginnen.

## <a name="enterprise-mpsa-and-select-agreements"></a>Enterprise, MPSA und ausgewählte Vereinbarungen
Microsoft Enterprise Agreements (EA), MPSA und Select Plus-Verträge bieten Ihnen Flexibilität im Hinblick auf die Verwendung und Lizenzierung von Visual Studio-Software über einen gewissen Zeitraum hinweg. Visual Studio-Administratoren müssen eine jährliche True Up-Bestellung aufgeben, um die Anzahl ihrer Softwarelizenzen entsprechend dem maximalen Nutzungswert aufzustocken, der für die Dauer der Vereinbarung festgelegt wurde.

## <a name="see-also"></a>Siehe auch
- [Dokumentation zu Visual Studio](/visualstudio/)
- [Dokumentation zu Azure DevOps](/azure/devops/)
- [Azure-Dokumentation](/azure/)
- [Dokumentation zu Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Nächste Schritte
Weitere Informationen zu den Aufgaben von Administratoren:
- [Administratoraufgaben](admin-responsibilities.md)
- [Inventory of pre-production environment (Inventur der Präproduktionsumgebung)](admin-inventory.md)
- [Verwalten von großen Teams und externen Vertragspartnern](manage-teams.md)
- Verwenden der [maximalen Auslastung](maximum-usage.md) zum Nachverfolgen von Kaufverpflichtungen