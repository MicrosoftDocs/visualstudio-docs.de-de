---
title: 'Vorgehensweise: Lokalisieren einer Funktion | Microsoft-Dokumentation'
description: Erfahren Sie, wie Sie Featuretitel und Beschreibungen in SharePoint lokalisieren, indem Sie hart codierte Zeichen folgen Werte durch Ausdrücke ersetzen, die auf lokalisierte Ressourcen verweisen.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- features [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3865c11c67fd826e0ce914b6aeb88364da3212b7
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305199"
---
# <a name="how-to-localize-a-feature"></a>How to: Lokalisieren eines Features
  Standardmäßig verwenden Funktions Titel und Beschreibungen hart codierte Zeichen folgen Werte. Um den Titel und die Beschreibung der Funktion zu lokalisieren, ersetzen Sie die Zeichen folgen durch Ausdrücke, die auf lokalisierte Ressourcen verweisen.

## <a name="localize-a-feature"></a>Lokalisieren einer Funktion

#### <a name="to-localize-a-feature"></a>So lokalisieren Sie ein Feature

1. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für den Knoten **Feature1** , und wählen Sie dann **Funktions Ressource hinzufügen** aus.

2. Wählen Sie im Dialogfeld **Ressource hinzufügen** in der Liste die Option **invariante Sprache** aus, als Kultur für die Ressourcen Datei der Standard Sprachfunktion.

3. Wiederholen Sie den vorherigen Schritt für jede lokalisierte Sprache, und wählen Sie die Sprachen Ihrer Wahl für die lokalisierten featureressourcendateien aus.

     Es werden separate featureressourcendateien erstellt: eine für die Standardsprache und eine für jede lokalisierte Sprache, die Sie unterstützen möchten.

4. Öffnen Sie jede Ressourcen Datei im Ressourcen-Editor, und geben Sie dann alle Zeichen folgen-IDs und deren Werte ein.

     Geben Sie z. b. in der standardmäßigen featureressourcendatei eine Zeichen folgen-ID des **Titels** mit dem Wert " **My Feature Title**" und eine zweite Zeichen folgen-ID der **Beschreibung** mit dem Wert " **My Feature Description**" ein. Verwenden Sie für jede lokalisierte Ressourcen Datei dieselben Zeichen folgen-IDs, die in der Standard Funktions Ressource verwendet werden, aber geben Sie lokalisierte Zeichen folgen für die Werte ein.

5. Nachdem Sie alle Ressourcen Werte eingegeben haben, öffnen Sie das Kontextmenü für das Feature (z *. Feature1. Feature*), und wählen Sie dann **Ansicht-Designer** aus, um die Funktion im Funktions-Designer zu öffnen.

6. Um die **Titel** -und **Beschreibungs** Felder in der Funktion zu lokalisieren, verwenden Sie das folgende Format, um Werte in Ihre Felder einzugeben:

     `$Resources:` *Zeichenfolgen-ID*

     Geben Sie z. b. $Resources:**Title** in das Feld **Funktions Titel** ein, und $Resources:**Description** im Feld **Funktionsbeschreibung** .

     Die Zeichen folgen-IDs müssen mit den in den Ressourcen Dateien verwendeten Zeichen folgen identisch sein.

7. Drücken Sie die Taste **F5** , um die Anwendung zu erstellen und auszuführen.

8. Öffnen Sie in SharePoint das Menü **Website Aktionen** , wählen Sie **Website Einstellungen** aus, und wählen Sie dann im Abschnitt **Website Aktionen** den Link **Website Features verwalten** aus.

9. Legen Sie die Anzeigesprache in SharePoint auf eine Sprache fest, die nicht der Standardsprache entspricht.

     Der lokalisierte Titel und die Beschreibung der Funktion werden in der Anwendung angezeigt. Zum Anzeigen lokalisierter Ressourcen muss auf dem SharePoint-Server ein Sprachpaket installiert sein, das der Kultur der Ressourcendatei entspricht.

## <a name="see-also"></a>Siehe auch
- [Lokalisieren von SharePoint-Lösungen](../sharepoint/localizing-sharepoint-solutions.md)
- [How to: Hinzufügen einer Ressourcendatei](../sharepoint/how-to-add-a-resource-file.md)
- [How to: Lokalisieren von ASPX-Markup](../sharepoint/how-to-localize-aspx-markup.md)
- [How to: Lokalisieren von Code](../sharepoint/how-to-localize-code.md)
