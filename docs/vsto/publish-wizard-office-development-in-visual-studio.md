---
title: Veröffentlichungs-Assistent (Office-Entwicklung in Visual Studio)
description: Erfahren Sie, wie Sie mit dem Veröffentlichungs-Assistenten Projektmappendateien an einen angegebenen Speicherort kopieren, die Manifest-Dateien erstellen und in Visual Studio ein Setup Programm erstellen.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ProjectProperties.PublishWizard
- VST.PublishWizard.Publish.2007System
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ClickOnce deployment [Office development in Visual Studio], Publish Wizard
- deploying applications [Office development in Visual Studio], Publish Wizard
- Office applications [Office development in Visual Studio], Publish Wizard
- Publish Wizard, Office solutions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 25821a0f245f2f0ed30fcbfb10137a772dd0dd01
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528010"
---
# <a name="publish-wizard-office-development-in-visual-studio"></a>Veröffentlichungs-Assistent (Office-Entwicklung in Visual Studio)
  Verwenden Sie den **Veröffentlichungs-Assistenten** , um Projektmappendateien an einen angegebenen Speicherort zu kopieren, die Manifest-Dateien zu erstellen und ein Setup Programm zu erstellen.

 Um auf diesen Assistenten zuzugreifen, wählen Sie im Menü **Erstellen** die Option " *SolutionName* **veröffentlichen** " aus. Sie können auch über **Projektmappen-Explorer** auf den **Veröffentlichungs-Assistenten** zugreifen. Öffnen Sie das Kontextmenü für den Projekt Knoten, und wählen Sie dann **veröffentlichen** aus.

 In jedem Abschnitt unten wird eine Seite des Assistenten beschrieben.

## <a name="where-do-you-want-to-publish-the-application"></a>Wo möchten Sie die Anwendung veröffentlichen?
 **Geben Sie den Speicherort für die Veröffentlichung dieser Anwendung an** . Erforderlich. Der Speicherort für die Veröffentlichung ist das Verzeichnis, in dem der **Veröffentlichungs-Assistent** die Projektmappendateien kopiert, z. b. die Manifeste, Assemblys, das temporäre Zertifikat und andere Dateien Sie benötigen Schreibzugriff auf dieses Verzeichnis.

 Geben Sie den Speicherort als Datenträger Pfad, Dateifreigabe, FTP-Site oder Website-URL ein, oder klicken Sie auf die Schaltfläche **Durchsuchen** , um nach dem Speicherort zu suchen. Der Pfad kann die folgenden Formate aufweisen:

- Ein relativer oder absoluter Pfad im standardmäßigen Windows-Format, z. b. " *c:\Deploy\MyApplication* " oder " *\MyApplication*".

- Ein UNC-Pfad (Universal Naming Convention), z. b. *\\ \servername\meineanwendung \\*.

- Eine URL einer Website, z `http://www.contoso.com/MyApplication` . b..

  Standardmäßig ist der Veröffentlichungs Speicherort *http://localhost/projectname/* , wenn IIS installiert ist, oder das Verzeichnis Publish \, wenn IIS nicht installiert ist.

> [!NOTE]
> Es gibt weitere Überlegungen, wenn auf dem Bereitstellungs Zielcomputer Windows Vista ausgeführt wird. Sie müssen ein Administrator auf dem Windows Vista-Computer sein, um die lokale Veröffentlichungs Option zu verwenden. Außerdem ist der Standard Speicherort immer das *Veröffentlichungs \\* Verzeichnis, unabhängig davon, ob IIS installiert ist.

## <a name="what-is-the-default-installation-path-on-end-user-computers"></a>Was ist der Standard Installationspfad auf Endbenutzer Computern?
 Der Installationspfad ist optional. Sie können den Installationspfad später festlegen, wenn Sie dies bevorzugen. Weitere Informationen finden Sie unter Gewusst [wie: Ändern des Installations Pfads einer Office](/previous-versions/bb608626(v=vs.110))-Projekt Mappe.

 Der Installationspfad ist das Verzeichnis, in dem der Endbenutzer die Anpassung installiert. Hierbei handelt es sich ebenfalls um den Pfad, der von der Projektmappe für die Suche nach Updates verwendet wird. Die Projekt Mappe wird vom **Veröffentlichungs-Assistenten** nicht an diesem Speicherort bereitgestellt, es sei denn, der Pfad ist identisch mit dem Pfad, den Sie im Feld **Geben Sie den Speicherort für die Veröffentlichung dieser Anwendung** eingegeben auf der vorherigen Seite eingegeben haben.

 **Von einer Website** Geben Sie die URL an, die Endbenutzer befolgen, um die Lösung zu installieren.

 **Von einem UNC-Pfad oder einer Dateifreigabe** Geben Sie den UNC-Pfad an, nach dem die Endbenutzer die Lösung installieren.

 **Von einer CD-ROM oder DVD-ROM** Diese Option erfordert keinen Installationspfad.

 Visual Studio verbrennt die CD oder DVD nicht. Sie müssen die Ausgabe manuell auf eine CD oder DVD kopieren.

## <a name="see-also"></a>Weitere Informationen
- [Bereitstellen einer Office-Projekt Mappe mithilfe von ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Seite "veröffentlichen", Projekt-Designer &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/publish-page-project-designer-office-development-in-visual-studio.md)
- [Bereitstellen einer Office-Projekt Mappe](../vsto/deploying-an-office-solution.md)