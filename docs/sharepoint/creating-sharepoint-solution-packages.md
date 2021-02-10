---
title: Erstellen von SharePoint-Lösungs Paketen | Microsoft-Dokumentation
description: Erstellen und Anpassen von Bereitstellungs Paketen für SharePoint-Lösungen mithilfe des Paket-Designers. Erkunden Sie die Paket Erstellungs Tools, Designer Optionen und die Ordnerstruktur.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
- packages [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 423fcaf54d1d46ddf92352f4ff8bdbb637bbe514
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949089"
---
# <a name="create-sharepoint-solution-packages"></a>Erstellen von SharePoint-Lösungs Paketen
  Mithilfe des Paket-Designers können Sie Bereitstellungspakete erstellen und anpassen. Beispielsweise können Sie SharePoint-Projektelemente und -Funktionen hinzufügen, den IIS-Server zurücksetzen, Funktionsaktivierungsbereiche festlegen und Funktionsabhängigkeiten identifizieren. Der Designer generiert außerdem ein Manifest, eine XML-Datei, die jedes Paket beschreibt.

## <a name="packaging-tools"></a>Paket Erstellungs Tools
 Sie können den **Paket-Designer** verwenden, um das Paket anzupassen und das Manifest zu generieren. Sie können SharePoint-Projektelemente einschließen, konfigurieren, ob der Webserver zurückgesetzt werden soll, und den Bereitstellungsservertyp festlegen. Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen und Entfernen von Features und Elementen in einem Paket mit dem Paket-Designer](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md).

 Alternativ können Sie den Paket- **Explorer** verwenden, um die Features und Elemente in der Paketdatei (*. wsp*) zu ändern. Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen und Entfernen von Features und Elementen in einem Paket mit dem Paket-Explorer](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).

 Sie können Visual Studio und MSBuild verwenden, um Paketdateien (*. wsp*) zum Bereitstellen der SharePoint-Lösung zu erstellen. Bei diesem Vorgang werden die für die SharePoint-Bereitstellung benötigten Manifestdateien generiert. Weitere Informationen finden Sie unter Gewusst [wie: Erstellen eines SharePoint-Lösungs Pakets mithilfe von MSBuild-Tasks](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md).

## <a name="package-designer-options"></a>Paket-Designer-Optionen
 In der folgenden Tabelle sind die Eigenschaften aufgeführt, die Sie in SharePoint-Paketen mit dem **Paket-Designer** anpassen können.

|Eigenschaft des Paket-Designers|Beschreibung der Standardeinstellung|
|-------------------------------|------------------------------------|
|Name|Erforderlich. Der Standardname des Pakets ist auf *ProjectName* festgelegt.|
|Webserver zurücksetzen|Dies ist optional. Wählen Sie diese Option aus, wenn Sie den Webserver neu starten möchten, nachdem die *wsp* -Datei auf dem SharePoint-Server installiert wurde.|
|Bereitstellungsservertyp|Dies ist optional. Stellt den Typ des Servers dar, auf dem das Paket gehostet wird. Wenn diese Einstellung nicht festgelegt ist, wird standardmäßig Webfrontend verwendet.<br /><br /> ApplicationServer: Beschreibt einen Server, der Dienste hostet.<br /><br /> Webfrontend: Beschreibt einen Server, der Websites hostet.|
|Elemente in der Lösung|Alle SharePoint-Projektelemente und -Funktionen, die dem Paket hinzugefügt werden können.|
|Elemente in diesem Paket|Dies ist optional. Alle SharePoint-Elemente und -Funktionen, die Sie im Paket bereitstellen möchten.|

## <a name="configure-the-packaging-process"></a>Konfigurieren des Paket Erstellungs Prozesses
 Nachdem Sie SharePoint-Lösungen in Visual Studio entwickelt haben, können Sie anpassen, wie die Projekte gepackt werden.

 In der folgenden Tabelle sind die beiden MSBuild-Ziele aufgeführt, mit denen Sie anpassen können, wie die *wsp* -Datei erstellt wird.

|Target|Beschreibung|
|------------|-----------------|
|BeforeLayout|Das Ziel, das sofort Aufgaben ausführt, bevor die Dateien in ein Zwischenverzeichnis kopiert werden. Sie können die Dateien vor dem Erstellen einer Paketdatei (*. wsp*) ändern.|
|AfterLayout|Das Ziel, das sofort Aufgaben ausführt, nachdem die Dateien in ein Zwischenverzeichnis kopiert wurden.|

 Weitere Informationen finden Sie unter Gewusst [wie: Anpassen eines SharePoint-Lösungs Pakets mithilfe von MSBuild-Zielen](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md).

## <a name="packaging-architecture"></a>Verpackungs Architektur
 Die folgenden Schritte werden ausgeführt, wenn Sie ein SharePoint-Paket (*. wsp*) in Visual Studio erstellen.

1. Der Funktionen und Pakete werden überprüft, um sicherzustellen, dass die physikalische und semantische Struktur des Pakets richtig ist.

2. Der Funktionen, Projektelemente und Paketdateien im Paket werden aufgelistet. Manifestdateien für Pakete und Funktionen werden umgewandelt, damit alle erforderlichen Informationen für die Bereitstellung und Aktivierung eingeschlossen sind. Die Token werden durch den vollqualifizierten Wert ersetzt.

3. Das anpassbare MSBuild-Ziel BeforeLayout wird ausgeführt. Sie können diesen Schritt erstellen, um benutzerdefinierte Änderungen am Paket vorzunehmen, bevor die *wsp* -Datei erstellt wird.

4. Die aufgelisteten Dateien werden in ein Zwischenverzeichnis kopiert.

5. Das anpassbare MSBuild-Ziel AfterLayout wird ausgeführt. Sie können diesen Schritt erstellen, um benutzerdefinierte Änderungen am Paket vorzunehmen, bevor die *wsp* -Datei erstellt wird.

6. Die Dateien im zwischen Verzeichnis werden der *wsp* -Datei hinzugefügt.

## <a name="package-folder-structure"></a>Paketordnerstruktur
 Wenn Sie das SharePoint-Projekt Verpacken, wird für Sie eine *wsp* -Datei im Ordner *solutionfolder\bin \\ \<BuildConfiguration>* erstellt. Wenn sich Ihre Projekt Mappe beispielsweise in " *c:\Visual Studio 2013 \ Projects\ListDefinition1* " befindet und die Buildkonfiguration auf "Release" festgelegt ist, befindet sich die *wsp* -Datei unter " *c:\Visual Studio 2013 \ Projects\ListDefinition1\bin\Release*".

## <a name="see-also"></a>Weitere Informationen
- [Vorgehensweise: Anpassen eines SharePoint-Lösungs Pakets](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [Vorgehensweise: Hinzufügen und Entfernen von Features und Elementen zu einem Paket mit dem Paket-Designer](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)
- [Vorgehensweise: Erstellen eines SharePoint-Lösungs Pakets mithilfe von MSBuild-Aufgaben](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)
- [Vorgehensweise: Erstellen eines SharePoint-Lösungs Pakets mithilfe von MSBuild-Aufgaben](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)
- [Vorgehensweise: Anpassen eines SharePoint-Lösungs Pakets mithilfe von MSBuild-Zielen](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md)
