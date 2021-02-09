---
title: Packen und Bereitstellen von SharePoint-Lösungen | Microsoft-Dokumentation
description: Verwenden Sie eine Lösungspaketdatei (.wsp), um SharePoint-Lösungen zu packen und auf einem SharePoint-Server bereitzustellen.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- packaging [SharePoint development in Visual Studio]
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, packaging and deploying
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ae74aa3cf759ba006acd36c168eecceac4b2ee4a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99916547"
---
# <a name="package-and-deploy-sharepoint-solutions"></a>Packen und Bereitstellen von SharePoint-Lösungen
  In der Regel wird eine SharePoint-Lösung auf einem SharePoint-Server bereitgestellt, indem eine Lösungspaketdatei (WSP) verwendet wird. Sie können Visual Studio verwenden, um die SharePoint-Projektelemente in Funktionen zu organisieren und ein Paket zum Bereitstellen der SharePoint-Features zu erstellen.

 Dieses Thema enthält die folgenden Informationen:

- [Erstellen von Features und Paketen](#create-features-and-packages)

- [Unterstützung für Features und Pakettools](#feature-and-packaging-tool-support)

- [Bereitstellen von SharePoint-Lösungen](#deploy-sharepoint-solutions)

- [Bereitstellen von Dateien in SharePoint-Lösungen](#deploy-files-in-sharepoint-solutions)

## <a name="create-features-and-packages"></a>Erstellen von Features und Paketen
 Sie können Visual Studio verwenden, um verwandte SharePoint-Elemente in ein *Feature* zu gruppieren. Beispielsweise kann ein Feature für eine Kontaktlistendefinition die Listeninstanz und die Listendefinition enthalten. Sie können diese beiden Elemente zu Bereitstellungszwecken in einem einzigen Feature kombinieren. Weitere Informationen zu diesen Features finden Sie unter [Baustein: Features](/previous-versions/office/developer/sharepoint-2010/ee537350(v=office.14)).

 Als Nächstes können Sie ein SharePoint-Lösungspaket (*WSP*) erstellen, um mehrere Features, Websitedefinitionen, Assemblys und andere Dateien in einem einzelnen Paket zu bündeln, das die Dateien in einem von SharePoint benötigten Format speichert, um die Dateien auf dem Server bereitzustellen. Weitere Informationen finden Sie unter [Baustein: Lösungen](/previous-versions/office/developer/sharepoint-2010/ee537008(v=office.14)).

## <a name="feature-and-packaging-tool-support"></a>Unterstützung für Features und Pakettools
 Sie können die SharePoint-Entwicklungstools in Visual Studio verwenden, um Ihre SharePoint-Dateien für die einfachere Bereitstellung schnell in Features und Lösungspaketen zu organisieren. Sie können die folgenden Tools verwenden, um das Feature und das Lösungspaket zu konfigurieren.

- Feature- und Paket-Designer

- Paket-Explorer (ein Toolfenster)

- Projektmappen-Explorer.

### <a name="feature-designer-and-package-designer"></a>Feature- und Paket-Designer
 Mithilfe des Feature-Designers können Sie Features erstellen, Bereiche festlegen und andere Features als Abhängigkeiten markieren. Der Designer zeigt außerdem die endgültige XML-Datei an, in der die einzelnen Features beschrieben werden. Weitere Informationen finden Sie unter [Erstellen von SharePoint-Features](../sharepoint/creating-sharepoint-features.md).

 Wenden Sie das Feature auf eine bestimmte Website oder Gruppe von Websites an, indem Sie den *Bereich* im Feature-Designer festlegen. Wenn ein Feature für eine einzelne Website aktiviert ist, kann es nur auf dieser speziellen Website verwendet werden. Wenn ein Feature für eine Websitesammlung aktiviert ist, gelten die Elemente im Feature für die gesamte Websitesammlung. Weitere Informationen finden Sie unter [Elementbereich](/previous-versions/office/developer/sharepoint-2010/ms476615(v=office.14)).

 Wenn das Feature von anderen Features abhängig ist, können Sie eine *Abhängigkeit bei der Funktionsaktivierung* festlegen, um die abhängigen Features zu markieren, bevor Ihr Feature verfügbar gemacht wird. Eine Abhängigkeit bei der Funktionsaktivierung prüft, ob die abhängigen Features in diesem Bereich bereits aktiviert wurden. Weitere Informationen finden Sie unter [Aktivierungsabhängigkeiten und Bereich](/previous-versions/office/developer/sharepoint-2010/aa543162(v=office.14)).

 Im Paket-Designer können Sie SharePoint-Elemente in ein einzelnes Lösungspaket gruppieren und konfigurieren, ob der Webserver während der Bereitstellung zurückgesetzt werden soll. Verwenden Sie zum Festlegen des Bereitstellungsservertyps das Fenster **Eigenschaften**. Der Designer generiert außerdem die XML-Datei, die den jeweiligen Paketinhalt beschreibt. Weitere Informationen finden Sie unter [Erstellen von SharePoint-Lösungspaketen](../sharepoint/creating-sharepoint-solution-packages.md).

 Während der Bereitstellung wird der Internetinformationsdienste-Dienst (IIS) beendet, um die Lösungsdateien auf den SharePoint-Server zu kopieren. Wenn Sie den Paket-Designer in Visual Studio verwenden, können Sie auswählen, ob der Webserver neu gestartet werden soll. Verwenden Sie das Fenster **Eigenschaften**, um zu konfigurieren, ob die Lösung auf einem Front-End-Webserver oder einem Anwendungsserver bereitgestellt wird. Weitere Informationen finden Sie unter [Solution-Element (Lösung)](/previous-versions/office/developer/sharepoint-2010/ms412929(v=office.14)).

### <a name="packaging-explorer"></a>Paket-Explorer
 Sie können den Paket-Explorer verwenden, um die SharePoint-Dateien in Features und Pakete zu gruppieren und somit die Feature- und Paket-Designer zu ergänzen. Außerdem können Sie die hierarchische Ansicht des Pakets, der Features, der SharePoint-Projektelemente und der Dateien anzeigen. Der Paket-Explorer ist ein Toolfenster, das Sie verwenden können, um die folgenden Aufgaben auszuführen:

- Öffnen von SharePoint-Projektelementen und -dateien

- Verschieben von SharePoint-Projektelementen aus einem Feature in ein anderes per Drag & Drop

- Verschieben von SharePoint-Projektelementen und Features aus einem Paket in ein anderes per Drag & Drop

- Hinzufügen neuer Features zu einem Paket

- Öffnen des Feature- oder Paket-Designers

- Überprüfen von Features und Paketen

  Die SharePoint-Entwicklungstools in Visual Studio umfassen Validierungsregeln, die dabei helfen, die ordnungsgemäße Formatierung des Lösungspakets sicherzustellen. Außerdem überprüfen die Regeln, ob die *WSP*-Lösungsdatei erfolgreich auf einem SharePoint-Server bereitgestellt und aktiviert werden kann. Weitere Informationen zum XML-Schema für Features finden Sie unter [Featureschemas](/previous-versions/office/developer/sharepoint-2010/ms414322(v=office.14)).

  Sie können dem SharePoint-Projektsystem benutzerdefinierte Feature- und Paketvalidierungsregeln hinzufügen. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von benutzerdefinierten Feature- und Paketvalidierungsregeln für SharePoint-Lösungen](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).

  Weitere Informationen zum Paket-Explorer finden Sie unter [Vorgehensweise: Hinzufügen und Entfernen von Features und Elementen zu bzw. aus einem Paket mit dem Paket-Explorer](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).

### <a name="solution-explorer"></a>Projektmappen-Explorer
 Sie können den Projektmappen-Explorer verwenden, um zu den Dateien des SharePoint-Projekts zu navigieren und diese zu öffnen. Verwenden Sie das Kontextmenü im Projektmappen-Explorer, um Features, Funktionsereignisempfänger und Featureressourcen hinzuzufügen. Außerdem können Sie die Feature- und Paket-Designer öffnen, um die Features und Pakete für die Bereitstellung zu konfigurieren.

## <a name="deploy-sharepoint-solutions"></a>Bereitstellen von SharePoint-Lösungen
 Nachdem Sie die Features und das Paket in Visual Studio angepasst haben, können Sie eine *WSP*-Datei erstellen, die auf SharePoint-Servern bereitgestellt werden soll. Sie können Visual Studio verwenden, um die *WSP*-Datei nur auf dem SharePoint-Server auf dem Entwicklungscomputer zu debuggen und zu testen. Weitere Informationen zum Bereitstellen von SharePoint-Lösungen auf einem SharePoint-Remoteserver finden Sie unter [Installieren und Bereitstellen einer Farmlösung](/previous-versions/office/developer/sharepoint-2010/aa544500(v=office.14)).

 Sie können auch die Bereitstellungsschritte auf dem Entwicklungscomputer anpassen. Weitere Informationen finden Sie unter [Bereitstellen, Veröffentlichen und Aktualisieren von SharePoint-Lösungspaketen](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).

## <a name="deploy-files-in-sharepoint-solutions"></a>Bereitstellen von Dateien in SharePoint-Lösungen
 Wenn Sie der SharePoint-Lösung ein SharePoint-Projektelement hinzufügen, werden in der Regel alle erforderlichen Dateien eingeschlossen. Dateien, die kompiliert werden können (Codedateien), werden in die Ausgabeassembly der Lösung integriert. Möglicherweise müssen Sie jedoch auch nicht kompilierbare Dateien (z. B. *XML*-, *TXT*- oder Ressourcendateien) einem SharePoint-Projekt hinzufügen. Diese Dateien werden nicht automatisch in die Lösung gepackt. Fügen Sie die Dateien entweder einem zugeordneten Ordner oder einem SharePoint-Projektelement hinzu, um sicherzustellen, dass sie gepackt werden.

 Dateien, die zugeordneten Ordnern hinzugefügt werden, werden bei der Bereitstellung der Lösung automatisch in die SharePoint-Struktur kopiert. Dateien, die zu einem SharePoint-Projektelement hinzugefügt werden, werden an dem Speicherort bereitgestellt, der in der Eigenschaft **Bereitstellungsort** für jede Datei angegeben wurde, die teilweise basierend auf der Eigenschaft **Bereitstellungstyp** festgelegt ist. Der Eigenschaftswert **Bereitstellungstyp** ist standardmäßig **NoDeployment**, was bedeutet, dass die Datei nicht mit der Lösung bereitgestellt wird. Sie müssen einen anderen Wert für die Eigenschaft festlegen, um die Datei in das Paket aufzunehmen.

 Führen Sie beispielsweise eine der folgenden Aktionen aus, um eine *XML*-Datei zu einem SharePoint-Projekt hinzuzufügen:

- Fügen Sie dem Projekt den zugeordneten SharePoint-Ordner „Layouts“ hinzu. Dadurch wird im **Projektmappen-Explorer** ein Ordner namens **Layouts** erstellt, der einen Unterordner für das Projekt enthält. Fügen Sie dem neuen Unterordner die *XML*-Datei hinzu. Die Datei wird standardmäßig im SharePoint-Dateisystem unter *..\TEMPLATE\LAYOUTS\\\<Folder Name>* bereitgestellt. Weitere Informationen zum Hinzufügen von zugeordneten Ordnern finden Sie unter [Vorgehensweise: Hinzufügen und Entfernen zugeordneter Ordner](../sharepoint/how-to-add-and-remove-mapped-folders.md).

- Fügen Sie dem Ordner eines SharePoint-Projektelements die *XML*-Datei hinzu, und ändern Sie dann die Eigenschaft **Bereitstellungstyp** der *XML*-Datei von **NoDeployment** in eine andere Einstellung wie **RootFile** oder **ElementFile**. Die geeignete Einstellung für den **Bereitstellungstyp** hängt von der Datei und dem Projekt ab. Weitere Informationen zu den Einstellungen für die Eigenschaft **Bereitstellungstyp** finden Sie unter [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md).

  Wenn eine hinzugefügte Datei nicht auf ein bestimmtes Projekt in der Projektmappe angewendet wird, können Sie der Lösung ein leeres SharePoint-Projekt und dann die zusätzlichen Dateien hinzufügen. Eine weitere Alternative zum Bereitstellen von Dateien für SharePoint, insbesondere für die Inhaltsdatenbank, besteht darin, dem Projekt ein Modul hinzuzufügen und die Dateien dem Modul hinzuzufügen. Weitere Informationen finden Sie unter [Verwenden von Modulen zum Einbinden von Dateien in eine Projektmappe](../sharepoint/using-modules-to-include-files-in-the-solution.md).

## <a name="see-also"></a>Weitere Informationen
- [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)
- [Erstellen und Debuggen von SharePoint-Lösungen](../sharepoint/building-and-debugging-sharepoint-solutions.md)
