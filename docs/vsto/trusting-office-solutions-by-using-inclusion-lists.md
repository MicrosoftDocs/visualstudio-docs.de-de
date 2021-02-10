---
title: Vertrauen von Office-Projektmappen mithilfe von Inklusions Listen
description: Erfahren Sie, wie mit Einschluss Listen Benutzer Office-Projektmappen, die mit einem Zertifikat signiert sind, das den Verleger identifiziert, Vertrauenswürdigkeit gewähren können.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio]
- inclusion lists [Office development in Visual Studio], about inclusion lists
- security [Office development in Visual Studio], inclusion lists
- inclusion lists [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9a084ad152f178b4dd03e986eb06718b0fb47c98
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99968801"
---
# <a name="trust-office-solutions-by-using-inclusion-lists"></a>Vertrauen von Office-Projektmappen mithilfe von Inklusions Listen
  Mithilfe von Aufnahmelisten können Benutzer Office-Projektmappen, die mit einem Zertifikat signiert sind, das den Herausgeber identifiziert, Vertrauenswürdigkeit gewähren. Aufnahmelisten sind benutzerspezifisch und können für Anpassungen auf Dokumentebene und VSTO-Add-Ins verwendet werden.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Wenn ein Benutzer eine Office-Projektmappe startet, der keine Vertrauensstellung für diesen Benutzer gewährt wurde, wird er von der Microsoft Office-Projektmappe mit einer [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] -Vertrauensaufforderung zu einer Sicherheitsentscheidung aufgefordert. Wenn der Benutzer entscheidet, der Projektmappe zu vertrauen, wird die Anpassung ausgeführt, und beim nächsten Mal wird der Benutzer nicht zu einer Entscheidung aufgefordert.

## <a name="inclusion-list-and-windows-installer"></a>Aufnahme Liste und Windows Installer
 Zum Installieren von Office-Projektmappen im Verzeichnis " *Programme* " mithilfe von Windows Installer sind Administratorrechte erforderlich. Bei Office-Projektmappen im Verzeichnis " *Programme* " überprüft die Visual Studio-Tools für Office Runtime nicht mehr die Aufnahme Liste, da den Office-Projektmappen bereits die Berechtigung "FullTrust" gewährt wurde.

## <a name="clickonce-trust-prompt"></a>ClickOnce-Vertrauensaufforderung
 Mit der [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] -Implementierung für Office-Projektmappen können Administratoren die Vertrauensaufforderungsstufe so konfigurieren, dass Aufforderung aktiviert oder deaktiviert oder dass ein vertrauenswürdiges Zertifikat gefordert wird. Diese Konfiguration wird mit einem Registrierungsschlüssel vorgenommen, der den Zugriff auf die Aufnahmeliste steuert.

 Ist Anzeigen der Aufforderung deaktiviert, können nur Projektmappen installiert werden, die ein vertrauenswürdiges und bekanntes Zertifikat haben. Ist die Aufforderungsstufe (PromptingLevel) so festgelegt , dass ein Authenticode erforderlich ist, muss die Projektmappe mit einem Zertifikat einer bekannten Zertifizierungsstelle signiert sein, es ist aber kein Zertifikat erforderlich, das zu einer vertrauenswürdigen Stammzertifizierungsstelle (einem vertrauenswürdigem Zertifikat) führt. Ist Anzeigen der Aufforderung aktiviert, kann die Projektmappe mit einem Zertifikat mit einer unbekannten Identität signiert sein. In diesem Fall wird die Entscheidung über die Vertrauenswürdigkeit an den Endbenutzer weitergegeben, und für die Installation der Projektmappe genügt ein temporäres Zertifikat.

 Weitere Informationen finden Sie unter Gewusst [wie: Konfigurieren der Sicherheit für die Inklusions Liste](../vsto/how-to-configure-inclusion-list-security.md) und in Tabelle 2 mit der Bezeichnung "Start Effekte für Registrierungsschlüssel Werte für den Registrierungsschlüssel" unter [Konfigurieren von ClickOnce-vertrauenswürdigen](/previous-versions/dotnet/articles/ms996418(v=msdn.10))

## <a name="structure-of-the-inclusion-list"></a>Struktur der Aufnahme Liste
 Ein gültiger Eintrag der Aufnahmeliste besteht aus zwei Teilen: einem Pfad zum Bereitstellungsmanifest und dem öffentlichen Schlüssel, der zum Signieren der Projektmappe verwendet wird. Nachdem eine Projektmappe zur Aufnahmeliste hinzugefügt wurde, wird sie als vertrauenswürdig eingestuft. Wenn die Office-Projektmappe ausgeführt wird, vergleicht die Office-Anwendung den öffentlichen Schlüssel in der Aufnahmeliste mit dem signierenden Schlüssel im Bereitstellungsmanifest, um zu überprüfen, ob die derzeit aktive Projektmappe mit der ursprünglich als vertrauenswürdig eingestuften Version identisch ist.

## <a name="see-also"></a>Weitere Informationen
- [Gewähren von Vertrauenswürdigkeit für Office-Lösungen](../vsto/granting-trust-to-office-solutions.md)
- [Sichere Office-Lösungen](../vsto/securing-office-solutions.md)
