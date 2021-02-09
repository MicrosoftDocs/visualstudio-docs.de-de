---
title: Gewähren von Vertrauenswürdigkeit für Office-Lösungen
description: Um Office-Projektmappen Vertrauenswürdigkeit zu gewähren, müssen Sie die Sicherheitsrichtlinie der einzelnen Zielcomputer so ändern, dass Sie der Projektmappenassembly, dem Bereitstellungs Manifest und dem Dokument
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f98f3154a0708ce7a01603968f0f5774dd86f40e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910230"
---
# <a name="grant-trust-to-office-solutions"></a>Gewähren von Vertrauenswürdigkeit für Office-Lösungen
  Gewähren von Vertrauenswürdigkeit für Office-Projektmappen bedeutet, dass die Sicherheitsrichtlinien der einzelnen Zielcomputer so geändert werden, dass die Projektmappenassembly, das Anwendungs Manifest, das Bereitstellungs Manifest Die Vertrauensstellung kann der Office-Projekt Mappe entweder von Ihnen oder dem Endbenutzer erteilt werden.

 Sie können der Office-Projekt Mappe volles Vertrauen gewähren, indem Sie die Anwendungs-und Bereitstellungs Manifeste signieren.

 Endbenutzer können der Office-Projekt Mappe Vertrauenswürdigkeit gewähren, indem Sie in der Vertrauensstellungs Aufforderung eine Vertrauensstellungs Entscheidung treffen [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] .

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="trust-the-solution-by-signing-the-application-and-deployment-manifests"></a><a name="Signing"></a> Vertrauen der Lösung durch Signieren der Anwendungs-und Bereitstellungs Manifeste
 Alle Anwendungs-und Bereitstellungs Manifeste für Office-Projektmappen müssen mit einem Zertifikat signiert werden, das den Verleger identifiziert. Zertifikate bilden eine Grundlage für die Entscheidung über Vertrauens Stellungen.

 Ein temporäres Zertifikat wird für Sie erstellt, dem während der Buildzeit eine Vertrauensstellung gewährt wird, damit die Lösung während des Debuggens ausgeführt wird. Wenn Sie eine Lösung veröffentlichen, die mit einem temporären Zertifikat signiert ist, wird der Endbenutzer aufgefordert, eine Vertrauens Entscheidung zu treffen.

 Wenn Sie die Lösung mit einem bekannten und vertrauenswürdigen Zertifikat signieren, wird die Lösung automatisch installiert, ohne dass der Endbenutzer aufgefordert wird, eine Vertrauens Entscheidung zu treffen. Weitere Informationen zum Abrufen eines Zertifikats für die Signierung finden Sie unter [ClickOnce und Authenticode](../deployment/clickonce-and-authenticode.md). Nachdem ein Zertifikat abgerufen wurde, muss dem Zertifikat explizit vertraut werden, indem es der Liste vertrauenswürdiger Herausgeber hinzugefügt wird. Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen eines vertrauenswürdigen Herausgebers zu einem Client Computer für ClickOnce-Anwendungen](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md).

 Wenn ein Entwickler die Projekt Mappe mit einem temporären Zertifikat signiert, kann ein Administrator die Anpassung mit einem bekannten und vertrauenswürdigen Zertifikat erneut signieren, indem er die Manifest Generation and Editing Tool (*mage.exe*) verwendet, bei der es sich um eines der Microsoft .NET Framework-Tools handelt. Weitere Informationen zu Signaturlösungen finden Sie unter Gewusst [wie: Signieren von Office](../vsto/how-to-sign-office-solutions.md) -Projektmappen und Gewusst [wie: Signieren von Anwendungs-und Bereitstellungs Manifesten](../ide/how-to-sign-application-and-deployment-manifests.md)

## <a name="trust-the-solution-by-using-the-clickonce-trust-prompt"></a><a name="TrustPrompt"></a>Vertrauen der Lösung mithilfe der ClickOnce-Vertrauens Aufforderung
 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] fordert den Endbenutzer auf, die Entscheidung über die Vertrauenswürdigkeit zu treffen, wenn keine Organisations weite Richtlinie vorhanden ist, die dem Zertifikat der Lösung vertraut. Wenn der Endbenutzer der Projekt Mappe Vertrauenswürdigkeit gewährt, wird ein Eintrag mit einer Aufnahme Liste erstellt, der eine URL und einen öffentlichen Schlüssel zum Speichern dieser Vertrauensstellungs Entscheidung enthält. Wenn eine vertrauenswürdige Anpassung zu einem späteren Zeitpunkt ausgeführt wird, wird der Endbenutzer nicht erneut aufgefordert.

 Administratoren können die [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] Vertrauensstellungs Aufforderung deaktivieren oder verlangen, dass die Eingabeaufforderung nur bei Lösungen auftritt, die mit einem Authenticode-Zertifikat signiert sind. Weitere Informationen zum Ändern dieser Einstellungen für die Zonen "MyComputer", "LocalIntranet", "Internet", "Vertrauensstellungs Sites" und "untrustdsites" finden Sie unter Gewusst [wie: Konfigurieren des ClickOnce-Eingabe](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)Aufforderungs Verhaltens.

## <a name="see-also"></a>Weitere Informationen

- [Sichere Office-Lösungen](../vsto/securing-office-solutions.md)
- [Gewähren von Vertrauenswürdigkeit für Dokumente](../vsto/granting-trust-to-documents.md)
- [Behandeln von Problemen mit der Sicherheit von Office](../vsto/troubleshooting-office-solution-security.md)
- [Besondere Sicherheitsüberlegungen für Office-Lösungen](../vsto/specific-security-considerations-for-office-solutions.md)