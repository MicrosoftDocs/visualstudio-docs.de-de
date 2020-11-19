---
title: 'Vorgehensweise: Anpassen eines SharePoint-Features | Microsoft-Dokumentation'
description: Passen Sie SharePoint-Funktionen in Visual Studio an. Der Funktions-Designer wird geöffnet, wenn Sie eine neue Funktion in Projektmappen-Explorer oder im SharePoint-Paket-Explorer hinzufügen.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.RAD.FeatureDesigner.SwitchView
- VS.SharePointTools.RAD.featureDesigner.Manifest
- VS.SharePointTools.RAD.FeatureDesignerProperties
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b4846d79af7a031970e8870626f88450e8a3e647
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94903662"
---
# <a name="how-to-customize-a-sharepoint-feature"></a>Vorgehensweise: Anpassen einer SharePoint-Funktion
  Sie können SharePoint-Funktionen erstellen und anpassen, indem Sie den Funktions-Designer in Visual Studio verwenden. Beispielsweise können Sie den Funktionsbereich festlegen und weitere Features als Abhängigkeiten hinzufügen. Standardmäßig wird der Funktions-Designer geöffnet, wenn Sie eine neue Funktion in Projektmappen-Explorer oder im SharePoint-Paket-Explorer hinzufügen.

## <a name="opening-the-feature-designer"></a>Öffnen des Funktions-Designers
 Sie können SharePoint-Projekt Elemente zu einem Feature hinzufügen oder entfernen, indem Sie den Funktions-Designer verwenden.

#### <a name="to-open-the-feature-designer"></a>So öffnen Sie den Funktions-Designer

1. Erweitern Sie in **Projektmappen-Explorer** den Knoten **Features**.

2. Doppelklicken Sie auf das *Feature1* -Element, oder öffnen Sie das Kontextmenü für das *Feature1* -Element, und wählen Sie dann **Ansicht-Designer** aus.

## <a name="view-the-packaged-manifest-file"></a>Anzeigen der Paket Manifest-Datei
 Sie können den Funktions-Designer verwenden, um die Paket Manifest-Datei für die Funktion (*feature.xml*) zu ändern und zu generieren. Anschließend können Sie den XML-Code für diese Datei in Visual Studio anzeigen.

#### <a name="to-view-the-packaged-manifest-file"></a>So zeigen Sie die Paket Manifest-Datei an

1. Wählen Sie im **Funktions-Designer** die Registerkarte **Manifest** aus.

#### <a name="to-view-the-packaged-manifest-file-by-using-solution-explorer"></a>So zeigen Sie die Paketdatei mit Projektmappen-Explorer an

1. Wählen Sie in **Projektmappen-Explorer** das Symbol **alle Dateien anzeigen** aus.

2. Erweitern Sie Features, erweitern Sie Featurename, erweitern Sie Featurename. Feature, und öffnen Sie dann die Datei *\<FeatureName>.Template.xml* .

    > [!NOTE]
    > Wenn Sie die XML-Datei mit den featurevorlagen-Manifesten öffnen, werden die Dateien automatisch überprüft, und die Warnungen, die im Fehlerliste Fenster angezeigt werden, können ignoriert werden.

## <a name="change-the-manifest-template"></a>Ändern der Manifest-Vorlage
 Sie können den XML-Code für die FeatureManifest-Datei im XML-Editor von Visual Studio oder im Bereich "Manifest Template" ändern. Alle Änderungen am XML-Code werden in der Paket Manifest-Datei für das Feature zusammengeführt. Beispielsweise möchten Sie möglicherweise die Manifest-Vorlage ändern, um eine Funktions Eigenschaft anzupassen.

#### <a name="to-change-the-manifest-template-by-using-the-xml-editor"></a>So ändern Sie die Manifest-Vorlage mithilfe des XML-Editors

1. Wählen Sie **im Funktions-Designer** die Registerkarte **Manifest** aus, erweitern Sie den Knoten **Bearbeitungs Optionen** , und wählen Sie dann den Link **in XML-Editor öffnen aus** .

     Änderungen an der XML-Datei werden in der Paket Manifest-Datei zusammengeführt.

#### <a name="to-change-the-manifest-template-by-using-the-manifest-template-pane"></a>So ändern Sie die Manifest-Vorlage mithilfe des Bereichs "Manifest-Vorlage"

1. Wählen Sie im **Funktions-Designer** die Registerkarte **Manifest** aus, erweitern Sie den Knoten **Bearbeitungs Optionen** , und ändern Sie dann den XML-Code, der im Bereich Manifest-Vorlage angezeigt wird.

     Änderungen an der XML-Datei werden im Bereich " **Vorschau des gepackten Manifests** " angezeigt.

## <a name="overwrite-the-packaged-manifest-file"></a>Überschreiben der Paket Manifest-Datei
 Sie können den Funktions-Designer deaktivieren und die *feature.xml* Datei manuell erstellen. Wenn Sie dieses Verfahren zum ersten Mal ausführen, werden die aktuellen Einstellungen im Funktions-Designer in der XML-Datei der Funktions Vorlage gespeichert. Anschließend können Sie den XML-Code ändern oder überschreiben.

> [!NOTE]
> Wenn Sie SharePoint-Projekt Elemente in der XML-Datei hinzufügen oder entfernen, während der Funktions-Designer deaktiviert ist, werden diese Projekt Elemente nicht gepackt.

#### <a name="to-overwrite-packaged-manifest-file-by-disabling-the-designer"></a>So überschreiben Sie die Datei mit einem Paket, indem Sie den Designer deaktivieren

1. Wählen Sie im **Funktions-Designer** die Registerkarte **Manifest** aus.

2. Erweitern Sie den Knoten **Optionen bearbeiten** , wählen Sie **im Link generierten XML-Code überschreiben aus** , und klicken Sie dann auf die Schaltfläche **Ja** .

     Die Vorlage wird mit der aktuellen Paket Manifest-Datei aktualisiert.

## <a name="enable-the-feature-designer"></a>Aktivieren des Funktions-Designers
 Sie können den Funktions-Designer erneut aktivieren, um die *feature.xml* Datei anzupassen.

#### <a name="to-re-enable-the-designer"></a>So aktivieren Sie den Designer erneut

1. Wählen Sie im **Funktions-Designer** die **Änderungen auf Manifest verwerfen und den Designer erneut aktivieren** aus, und klicken Sie dann auf die Schaltfläche **Ja** .

2. Die Vorlage wird mit dem ursprünglichen Text aktualisiert, und alle Änderungen an der XML-Datei gehen verloren.

## <a name="see-also"></a>Weitere Informationen
- [Packen und Bereitstellen von SharePoint-Lösungen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
