---
title: 'Vorgehensweise: Lokalisieren von Code | Microsoft-Dokumentation'
description: Erfahren Sie, wie Sie Code in SharePoint lokalisieren, indem Sie hart codierte Zeichen folgen durch Aufrufe von GetGlobalResourceObject ersetzen, eine Methode, die auf lokalisierte Ressourcen verweist.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- localizing code [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e76b8cfb2e9fcb513905918bd4ae87524078f6c6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931642"
---
# <a name="how-to-localize-code"></a>How to: Lokalisieren von Code
  In nicht lokalisiertem Code werden hartcodierte Zeichenfolgenwerte verwendet. Zum Lokalisieren der Codezeichenfolgen werden diese durch Aufrufe von <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> ersetzt – einer Methode zum Verweisen auf lokalisierte Ressourcen.

## <a name="localize-code"></a>Lokalisieren von Code

#### <a name="to-localize-code"></a>So lokalisieren Sie Code

1. Öffnen Sie in **Projektmappen-Explorer** das Kontextmenü für ein Projekt Element, und wählen Sie dann Modul **Hinzufügen** aus  >  .

     Wählen Sie die Vorlage **Ressourcen Datei** aus.

    > [!NOTE]
    > Fügen Sie die Ressourcendatei einem SharePoint-Projektelement hinzu, damit die Eigenschaft "Bereitstellungstyp" verfügbar ist. Diese Eigenschaft ist später in dieser Prozedur erforderlich.

2. Benennen Sie die Ressourcen Datei der Standardsprache mit einer *RESX* -Erweiterung, z. b. *myappresources. resx*.

3. Wiederholen Sie die Schritte 1 und 2, um dem SharePoint-Projektelement separate Ressourcendateien hinzuzufügen: jeweils eine für jede lokalisierte Sprache.

     Verwenden Sie für jede lokalisierte Ressourcendatei den gleichen Basisnamen, aber fügen Sie jeweils die Kultur-ID hinzu. Benennen Sie z. b. eine deutsch lokalisierte Ressource *MyAppResources.de-de. resx*.

4. Öffnen Sie die einzelnen Ressourcendateien, und fügen Sie ihnen lokalisierte Zeichenfolgen hinzu. Verwenden Sie in jeder Datei die gleichen Zeichenfolgen-IDs.

5. Ändern Sie den Wert der Eigenschaft **Bereitstellungstyp** jeder Ressourcen Datei in **appglobalresource** , damit jede Datei im App_GlobalResources Ordner des Servers bereitgestellt wird.

6. Belassen **Sie den Wert der Eigenschaft** Buildvorgang der einzelnen Dateien als **eingebettete Ressource**.

     Eingebettete Ressourcen werden in die DLL des Projekts kompiliert.

7. Erstellen Sie das Projekt, um die Satelliten-DLLs für die Ressource zu erstellen.

8. Wählen Sie im **Paket-Designer** die Registerkarte **erweitert** aus, und fügen Sie dann die Satellitenassembly hinzu.

9. Stellen Sie im Feld **Speicherort** einen Kultur-ID-Ordner dem Speicherort Pfad voran, z. b. *de-de \\ \<Project Item Name>.resources.dll*.

10. Sofern von der Lösung nicht bereits auf die Assembly "System.Web" verwiesen wird, fügen Sie einen entsprechenden Verweis hinzu, und fügen Sie im Code eine Anweisung zu <xref:System.Web> ein.

11. Suchen Sie im Code nach allen hartcodierten Zeichenfolgen, die Benutzern angezeigt werden, z. B. Benutzeroberflächentexte, Fehler und Meldungstexte. Ersetzen Sie diese durch einen Aufruf der <xref:System.Web.HttpContext.GetGlobalResourceObject%2A>-Methode mit der folgenden Syntax:

    ```csharp
    HttpContext.GetGlobalResourceObject("Resource File Name", "String ID")
    ```

12. Drücken Sie die Taste **F5** , um die Anwendung zu erstellen und auszuführen.

13. Legen Sie die Anzeigesprache in SharePoint auf eine Sprache fest, die nicht der Standardsprache entspricht.

     In der Anwendung werden die lokalisierten Zeichenfolgen angezeigt. Zum Anzeigen lokalisierter Ressourcen muss auf dem SharePoint-Server ein Sprachpaket installiert sein, das der Kultur der Ressourcendatei entspricht.

## <a name="see-also"></a>Weitere Informationen
- [Lokalisieren von SharePoint-Lösungen](../sharepoint/localizing-sharepoint-solutions.md)
- [How to: Lokalisieren eines Features](../sharepoint/how-to-localize-a-feature.md)
- [How to: Lokalisieren von ASPX-Markup](../sharepoint/how-to-localize-aspx-markup.md)
- [How to: Hinzufügen einer Ressourcendatei](../sharepoint/how-to-add-a-resource-file.md)
