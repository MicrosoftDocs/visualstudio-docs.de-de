---
title: Anwendungs-und Bereitstellungs Manifeste in Office-Lösungen
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- manifests [Office development in Visual Studio]
- deployment manifests [Office development in Visual Studio]
- application manifests [Office development in Visual Studio]
- assemblies [Office development in Visual Studio], updating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d22d58eb8a2264d5c7765a15726db556c7d5569f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62942901"
---
# <a name="application-and-deployment-manifests-in-office-solutions"></a>Anwendungs-und Bereitstellungs Manifeste in Office-Lösungen
  Ein Anwendungsmanifest ist eine XML-Datei, über die Informationen bereitgestellt werden, mit denen eine Office-Projektmappe nach ihren Assemblys sucht und diese aktualisiert. Ein Anwendungsmanifest kann zusammen mit einem Bereitstellungsmanifest verwendet werden. Dabei handelt es sich um eine XML-Datei, die auf dem Server gespeichert ist und die Informationen bereitstellt, die zum Auffinden der aktuellsten Version des Anwendungsmanifests und der Assemblys verwendet werden.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="manifest-structure-for-office-solutions"></a>Manifeste für Office-Projektmappen
 Für Microsoft Office-Projektmappen, die mit den Office-Entwicklungstools in Visual Studio erstellt wurden, basieren alle Manifeste auf dem standardmäßigen ClickOnce-Schema. Beim Bereitstellen von Office-Projektmappen befinden sich die Anwendungsmanifeste sowohl für Projekte auf Dokumentebene als auch für VSTO-Add-In-Projekte im ClickOnce-Cache. Die Bereitstellungsmanifeste werden nicht auf den Clientcomputer kopiert.

 Informationen zum Inhalt von Anwendungs-und Bereitstellungs Manifesten für Office-Projekte finden Sie unter [Anwendungs Manifeste für Office-Lösungen](../vsto/application-manifests-for-office-solutions.md) und [Bereitstellungs Manifeste für Office-Lösungen](../vsto/deployment-manifests-for-office-solutions.md).

## <a name="create-application-and-deployment-manifests"></a>Anwendungs-und Bereitstellungs Manifeste erstellen
 Anwendungsmanifeste werden automatisch als Teil des Buildprozesses erstellt. Bei jeder Erstellung eines Projekts auf Dokumentebene wird der Speicherort des Bereitstellungsmanifests als benutzerdefinierte Dokumenteigenschaft in das Dokument eingebettet. Für VSTO-Add-Ins wird der Speicherort des Bereitstellungsmanifests in der Registrierung gespeichert.

 Weitere Informationen zum **Webpublishing-Assistenten**finden Sie unter Bereitstellen einer Office-Projekt Mappe [mithilfe von ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).

 Weitere Informationen zur Funktionsweise von Manifesten mit Office-Lösungen finden Sie unter Bereitstellen [einer Office](../vsto/deploying-an-office-solution.md)-Projekt Mappe.

## <a name="see-also"></a>Weitere Informationen

- [Architektur von Anpassungen auf Dokument Ebene](../vsto/architecture-of-document-level-customizations.md)
- [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)
- [Entwerfen und Erstellen von Office-Lösungen](../vsto/designing-and-creating-office-solutions.md)
- [Anwendungs Manifeste für Office-Lösungen](../vsto/application-manifests-for-office-solutions.md)
- [Bereitstellungs Manifeste für Office-Lösungen](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce-Anwendungs Manifest](../deployment/clickonce-application-manifest.md)
- [ClickOnce-Bereitstellungs Manifest](../deployment/clickonce-deployment-manifest.md)