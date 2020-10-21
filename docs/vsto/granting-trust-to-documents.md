---
title: Gewähren von Vertrauenswürdigkeit für Dokumente
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], trust
- inclusion lists [Office development in Visual Studio], about inclusion lists
- trust [Office development in Visual Studio], 2007 Office system
- granting trust [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a631e8d8cffe6bfde925dfbae4a7350e6a0ef95a
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/19/2020
ms.locfileid: "92298615"
---
# <a name="grant-trust-to-documents"></a>Gewähren von Vertrauenswürdigkeit für Dokumente
  Ein Projekt auf Dokumentebene verfügt über die gleichen Sicherheitsanforderungen wie Projekte auf Anwendungsebene: Signieren der Manifeste mit einem Zertifikat oder durch Klicken auf die vertrauenswürdige Eingabeaufforderung. Darüber hinaus muss sich das Dokument oder die Arbeitsmappe in einem Verzeichnis befinden, das als vertrauenswürdiger Speicherort festgelegt ist.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="trusted-locations"></a>Vertrauenswürdige Standorte
 Anwendungen in [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] und Office 2010 verfügen über Vertrauens Stellungen, in denen Benutzer Sicherheits-und Datenschutzeinstellungen konfigurieren können, z. b. vertrauenswürdige Standorte. Bei Office-Projektmappen wird der lokale Computer als vertrauenswürdiger Speicherort eingestuft. Aufgrund des höheren Risikos gibt es bestimmte Verzeichnisse, die niemals als vertrauenswürdig eingestuft werden, z. B. die temporären Ordner für das System, für jeden Benutzer und für Internet Explorer.

 Weitere Informationen zum Trust Center finden Sie unter [Sicherheit und Richtlinien und Einstellungen in Office 2010](/previous-versions/office/office-2010/cc178946(v=office.14)). Weitere Informationen zum Erstellen, verwalten, entfernen und Konfigurieren vertrauenswürdiger Ordner finden Sie unter Konfigurieren von [vertrauenswürdigen Speicherorten und Einstellungen für vertrauenswürdige Herausgeber im 2007 Office-System](/previous-versions/office/office-2007-resource-kit/cc178948(v=office.12)) und [erstellen, entfernen oder Ändern eines vertrauenswürdigen Speicher Orts für Ihre Dateien](https://support.office.com/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).

## <a name="security-considerations-for-office-solutions"></a>Sicherheitsüberlegungen für Office-Lösungen
 Es gibt mehrere Sicherheitsaspekte, wenn man überlegt, welche Ordner den vertrauenswürdigen Speicherorten hinzugefügt werden sollen:

- Lokale Ordner werden als sicherer und implizit vertrauenswürdig betrachtet. Remotespeicherorte, wie beispielsweise Dateifreigaben, müssen als vertrauenswürdige Speicherorte festgelegt werden.

- Wenn Sie den vertrauenswürdigen Speicherorten ein Verzeichnis hinzufügen, wird auf diese Weise nicht nur den Office-Projektmappen, sondern auch dem VBA- und ActiveX-Code die volle Vertrauenswürdigkeit gewährt. Aus diesem Grund sollten das Stammverzeichnis und die Ordner *eigene* Dateien nicht als vertrauenswürdig eingestuft werden.

- Obwohl das Dokument selbst durch die Verwendung der vertrauenswürdigen Speicherorte vertrauenswürdig ist, sind zusätzliche Berechtigungen erforderlich, damit die Anpassung als vertrauenswürdig eingestuft wird. Sie können der Anpassung volle Vertrauenswürdigkeit gewähren, indem Sie die Manifeste mit einem Zertifikat signieren, auf die Vertrauensstellungs Aufforderung klicken oder die Office-Projekt Mappe im Verzeichnis " *Programme* " installieren.

- Sie können das Dokument oder die Arbeitsmappe einer Projektmappe auf Dokumentebene im selben Verzeichnis wie die Assembly oder in einem anderen Verzeichnis speichern. Beispielsweise könnte sich das Dokument auf einem SharePoint-Server befinden, und die Assembly könnte auf einer Dateifreigabe im Netzwerk vorhanden sein. Weitere Informationen finden Sie unter Gewusst [wie: Veröffentlichen einer Office-Projekt Mappe auf Dokument Ebene auf einem SharePoint-Server mithilfe von ClickOnce](/previous-versions/bb608595(v=vs.110)).

## <a name="see-also"></a>Weitere Informationen
- [Gewähren von Vertrauenswürdigkeit für Office-Lösungen](../vsto/granting-trust-to-office-solutions.md)
- [Behandeln von Problemen mit der Sicherheit von Office](../vsto/troubleshooting-office-solution-security.md)
- [Sichere Office-Lösungen](../vsto/securing-office-solutions.md)