---
title: Bereitstellen & veröffentlichen einer SharePoint-Lösung auf einer lokalen SharePoint-Website
titleSuffix: ''
description: Informieren Sie sich über das Bereitstellen oder Veröffentlichen von SharePoint-Lösungen auf einem lokalen SharePoint-Server auf Ihrem Entwicklungs Computer.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 65683544f345a2378fdec559f582985ffec7bc43
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94903584"
---
# <a name="how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site"></a>Vorgehensweise: Bereitstellen und Veröffentlichen einer SharePoint-Lösung auf einer lokalen SharePoint-Website
  Sie können SharePoint-Lösungen auf einem lokalen SharePoint-Server auf dem Entwicklungs Computer bereitstellen oder veröffentlichen. Beim Bereitstellungs Prozess wird die *wsp* -Datei auf den SharePoint-Server kopiert, die Projekt Mappe installiert und anschließend die Funktionen aktiviert. Beim Veröffentlichungsprozess wird die *wsp* -Datei nur auf den SharePoint-Server kopiert und installiert. Sie müssen Sie manuell aktivieren, um Sie in SharePoint zu aktivieren.

## <a name="to-deploy-a-sharepoint-solution-to-the-local-sharepoint-server"></a>So stellen Sie eine SharePoint-Lösung auf dem lokalen SharePoint-Server bereit

1. Wählen Sie in **Projektmappen-Explorer** das Projekt aus, das Sie bereitstellen möchten.

2. Wählen Sie in der Menüleiste **Erstellen** und dann Projekt Mappe bereitstellen **aus.**

     Die *wsp* -Datei wird auf dem lokalen SharePoint-Server erstellt und installiert. Außerdem werden die-Funktionen aktiviert.

## <a name="to-publish-a-sharepoint-solution-to-a-local-sharepoint-server"></a>So veröffentlichen Sie eine SharePoint-Lösung auf einem lokalen SharePoint-Server

1. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für das SharePoint-Projekt, das Sie veröffentlichen möchten, und wählen Sie dann **veröffentlichen** aus.

2. Klicken Sie im Dialogfeld **veröffentlichen** auf das Optionsfeld **in Datei System veröffentlichen** .

3. Geben Sie im Textfeld **Ziel Speicherort** einen lokalen Pfad ein, und klicken Sie dann auf die Schaltfläche **veröffentlichen** .

     Der Veröffentlichungs Fortschritt wird im **Ausgabe** Fenster von Visual Studio angezeigt. Wenn der Prozess abgeschlossen ist, wird die Projektmappendatei (*. wsp*) auf dem lokalen SharePoint-Server installiert. Allerdings muss Sie weiterhin aktiviert werden, damit Sie in SharePoint verwendet werden kann. Wenn die Projektmappendatei bereits vorhanden ist, tritt ein Fehler auf, und Sie werden gefragt, ob Sie die vorhandene Datei überschreiben möchten. Weitere Informationen zum Aktualisieren des Pakets finden Sie im Abschnitt Aktualisieren von Remote Paketen unter Gewusst [wie: bereitstellen, veröffentlichen und Aktualisieren von SharePoint-Lösungen auf einem Remote Server](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).

## <a name="see-also"></a>Weitere Informationen
- [Vorgehensweise: bereitstellen, veröffentlichen und Aktualisieren von SharePoint-Lösungen auf einem Remote Server](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)
- [Erstellen von SharePoint-Lösungs Paketen](../sharepoint/creating-sharepoint-solution-packages.md)
- [Vorgehensweise: Anpassen eines SharePoint-Lösungs Pakets](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [Vorgehensweise: Hinzufügen und Entfernen von Features und Elementen zu einem Paket mit dem Paket-Designer](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)
