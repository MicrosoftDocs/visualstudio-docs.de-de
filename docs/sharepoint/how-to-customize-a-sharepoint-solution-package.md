---
title: 'Vorgehensweise: Anpassen eines SharePoint-Lösungs Pakets | Microsoft-Dokumentation'
description: Verwenden Sie den Paket-Designer, um ein SharePoint-Lösungspaket (. wsp) zu erstellen und anzupassen. Anzeigen oder Überschreiben der Paket Manifest-Datei. Ändern Sie die Manifest-Vorlage.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.RAD.PackageDesignerAdvanced
- VS.SharePointTools.RAD.PackageDesigner.Manifest
- VS.SharePointTools.RAD.PackageDesignerProperties
- VS.SharePointTools.RAD.PackageDesigner.SwitchView
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 149e99a3ba86f1eec22d90618abfd8972ed68e97
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99959895"
---
# <a name="how-to-customize-a-sharepoint-solution-package"></a>Vorgehensweise: Anpassen eines SharePoint-Lösungs Pakets
  Sie können den Paket-Designer verwenden, um ein Paket (*. wsp*) zu erstellen und anzupassen. Beispielsweise können Sie SharePoint-Projekt Elemente und-Funktionen hinzufügen, angeben, ob der Webserver zurückgesetzt wird, wenn die Lösung bereitgestellt wird, und den bereitstellungservertyp festlegen.

## <a name="open-the-package-designer"></a>Öffnen des Paket-Designers

#### <a name="to-open-the-package-designer"></a>So öffnen Sie den Paket-Designer

- Doppelklicken Sie in **Projektmappen-Explorer** auf **Paket**, oder wählen Sie im Kontextmenü des **Pakets** **Sicht-Designer** aus.

## <a name="view-the-packaged-manifestffile"></a>Anzeigen des paketierten manifestfFile
 Sie können den Paket-Designer verwenden, um die gepackte Manifest-Datei zu ändern und zu generieren. Anschließend können Sie den XML-Code für diese Datei in Visual Studio anzeigen.

#### <a name="to-view-the-xml-source-file"></a>So zeigen Sie die XML-Quelldatei an

1. Wählen Sie im **Paket**-Designer **Manifest** aus.

#### <a name="to-view-the-packaged-manifest-file-by-using-solution-explorer"></a>So zeigen Sie die Paketdatei mit Projektmappen-Explorer an

1. Klicken Sie im **Projektmappen-Explorer** auf **Alle Dateien anzeigen**.

2. Erweitern Sie Paket, erweitern Sie Package. Package, und öffnen Sie dann die Datei *Package.Template.xml* .

    > [!NOTE]
    > Wenn Sie die Manifest-XML-Datei für die Paket Vorlage öffnen, werden die Dateien automatisch überprüft, und Sie können die Warnungen ignorieren, die im Fehlerliste Fenster angezeigt werden.

## <a name="change-the-manifest-template"></a>Ändern der Manifest-Vorlage
 Sie können den XML-Code für die gepackte Manifest-Datei im XML-Editor von Visual Studio oder im Bereich "Manifest Template" ändern. Alle Änderungen am XML-Code werden in der Paket Manifest-Datei für das Paket zusammengeführt.

#### <a name="to-change-the-manifest-template-by-using-the-xml-editor"></a>So ändern Sie die Manifest-Vorlage mithilfe des XML-Editors

1. Wählen Sie **im Paket-Designer** die Registerkarte **Manifest** aus, erweitern Sie den Knoten **Optionen bearbeiten** , und wählen Sie dann den Link **in XML-Editor öffnen aus** .

     Änderungen an der XML-Datei werden in der Paket Manifest-Datei zusammengeführt.

#### <a name="to-change-the-manifest-template-by-using-the-manifest-template-pane"></a>So ändern Sie die Manifest-Vorlage mithilfe des Bereichs "Manifest-Vorlage"

1. Wählen Sie im **Paket-Designer** die Registerkarte **Manifest** aus, erweitern Sie den Knoten **Optionen bearbeiten** , und ändern Sie dann den XML-Code, der im Bereich Manifest-Vorlage angezeigt wird.

     Änderungen an der XML-Datei werden im Bereich " **Vorschau des gepackten Manifests** " angezeigt.

## <a name="overwrite-the-packaged-manifest-file"></a>Überschreiben der Paket Manifest-Datei
 Sie können den Paket-Designer deaktivieren und die *manifest.xml* Datei manuell erstellen. Wenn Sie dieses Verfahren zum ersten Mal ausführen, werden die aktuellen Einstellungen im Paket-Designer in der XML-Datei der Paket Vorlage gespeichert. Anschließend können Sie den XML-Code ändern oder überschreiben.

> [!NOTE]
> Wenn Sie SharePoint-Projekt Elemente und-Funktionen in der XML-Datei hinzufügen oder entfernen, während der Paket-Designer deaktiviert ist, werden diese Projekt Elemente und-Funktionen nicht gepackt.

#### <a name="to-overwrite-packaged-manifest-file-by-disabling-the-designer"></a>So überschreiben Sie die Datei mit einem Paket, indem Sie den Designer deaktivieren

1. Wählen Sie im **Paket-Designer** die Registerkarte **Manifest** aus.

2. Erweitern Sie den Knoten **Optionen bearbeiten** , wählen Sie **im Link generierten XML-Code überschreiben aus** , und klicken Sie dann auf die Schaltfläche **Ja** .

     Die Vorlage wird mit der aktuellen Paket Manifest-Datei aktualisiert.

## <a name="enable-the-package-designer"></a>Aktivieren des Paket-Designers
 Sie können den Paket-Designer erneut aktivieren, um die *manifest.xml* Datei anzupassen.

#### <a name="to-re-enable-the-designer"></a>So aktivieren Sie den Designer erneut

1. Wählen Sie im **Paket-Designer** den Link **Manifest verwerfen und den Designer erneut aktivieren** aus, und klicken Sie dann auf die Schaltfläche **Ja** .

     Die Vorlage wird mit dem ursprünglichen Text aktualisiert, und alle Änderungen an der XML-Datei gehen verloren.

## <a name="see-also"></a>Weitere Informationen
- [Packen und Bereitstellen von SharePoint-Lösungen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
