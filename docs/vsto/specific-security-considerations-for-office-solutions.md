---
title: Besondere Sicherheitsüberlegungen für Office-Lösungen
description: Erfahren Sie, wie die vom Microsoft .NET Framework und Microsoft Office bereitgestellten Sicherheitsfeatures Ihnen helfen können, Ihre Office-Lösungen vor Sicherheitsbedrohungen zu schützen.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- troubleshooting Office development in Visual Studio, security
- trusted code [Office development in Visual Studio]
- blocked code [Office development in Visual Studio]
- Outlook [Office development in Visual Studio], object model guard
- malicious code [Office development in Visual Studio]
- Outlook object model guard [Office development in Visual Studio]
- security [Office development in Visual Studio], troubleshooting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0da77067931d35ee63a9ccc9b0de85752157772b
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524302"
---
# <a name="specific-security-considerations-for-office-solutions"></a>Besondere Sicherheitsüberlegungen für Office-Lösungen
  Die von Microsoft .NET Framework und Microsoft Office bereitgestellten Sicherheitsfeatures können in Office-Projektmappen zum Schutz vor möglichen Sicherheitsbedrohungen beitragen. In diesem Thema werden einige dieser Bedrohungen erläutert und Empfehlungen bereitgestellt, wie sich vor diesen Bedrohungen schützen lässt. Es beinhaltet auch Informationen dazu, wie sich Microsoft Office-Sicherheitseinstellungen auf Office-Projektmappen auswirken.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="trusted-code-is-repurposed-in-a-new-malicious-document"></a>Vertrauenswürdiger Code wird in einem neuen, bösartigen Dokument neu entworfen.
 Ein Angreifer könnte vertrauenswürdigen Code, der für einen bestimmten Zweck vorgesehen ist, etwa Herunterladen persönlicher Daten für eine Bewerbung, übernehmen und in einem anderen Dokument, z. B. einem Arbeitsblatt, erneut verwenden. Der Code weiß nicht, dass nicht das Originaldokument ausgeführt wird, und begünstigt möglicherweise andere Bedrohungen, etwa Offenlegung persönlicher Daten oder Ausführen von Code mit erweiterten Berechtigungen, wenn er von einem anderen Benutzer geöffnet wird. Alternativ kann der Angreifer die Daten im Arbeitsblatt so ändern, dass er sich beim Senden an das Opfer unerwartet verhält. Durch Ändern der Werte, Formeln oder Darstellungsmerkmale eines mit Code verknüpften Arbeitsblatts wird es einem böswilligen Benutzer ermöglicht, einen anderen Benutzer durch Senden einer geänderten Datei anzugreifen. Außerdem können Benutzer durch Ändern von Werten auf dem Arbeitsblatt möglicherweise auf Informationen zugreifen, die nicht für sie bestimmt sind.

 Da sowohl der Speicherort der Assembly als auch der des Dokuments über ausreichende Beweise verfügen müssen, damit die Ausführung erfolgt, ist dieser Angriff nicht leicht zu bewerkstelligen. Beispielsweise haben Dokumente in E-Mail-Anhängen oder auf nicht vertrauenswürdigen Intranetservern nicht genügend Berechtigungen, um ausgeführt zu werden.

 Damit dieser Angriff möglich ist, muss der Code selbst so geschrieben sein, dass er Entscheidungen auf der Grundlage potenziell nicht vertrauenswürdiger Daten trifft. Ein Beispiel hierfür ist das Erstellen eines Arbeitsblatts mit einer ausgeblendeten Zelle, die den Namen eines Datenbankservers enthält. Der Benutzer übermittelt das Arbeitsblatt an eine ASPX-Seite, die versucht, mit der SQL-Authentifizierung und einem hardcodierten SA-Kennwort eine Verbindung zu diesem Server aufzubauen. Ein Angreifer könnte den Inhalt der ausgeblendeten Zelle durch einen anderen Computernamen ersetzen und so das SA-Kennwort abrufen. Um dieses Problem zu vermeiden, sollten Sie niemals Kennwörter hartcodieren und stets die Server-IDs vor dem Zugriff auf den Server mit einer internen Liste vertrauenswürdiger Server abgleichen.

### <a name="recommendations"></a>Empfehlungen

- Überprüfen Sie immer Eingaben und Daten, egal, ob sie vom Benutzer, aus dem Dokument, aus einer Datenbank, von einem Webdienst oder aus einer anderen Quelle stammen.

- Achten Sie darauf, dass Sie bestimmte Arten von Funktionen nicht offen zugänglich machen, beispielsweise das Abrufen privilegierter Daten im Namen des Benutzers und Ablegen dieser Daten auf einem ungeschützten Arbeitsblatt.

- Je nach Typ der Anwendung ist es möglicherweise sinnvoll, vor dem Ausführen von irgendwelchem Code zu überprüfen, ob das Originaldokument ausgeführt wird. Vergewissern Sie sich sich beispielsweise, dass der Code aus einem Dokument ausgeführt wird, das in einem bekannten, sicheren Speicherort gespeichert ist.

- Eventuell ist es sinnvoll, beim Öffnen des Dokuments eine Warnung anzuzeigen, wenn Ihre Anwendung privilegierte Aktionen ausführt. Sie können zum Beispiel einen Begrüßungsbildschirm oder ein Startdialogfeld erstellen, in dem mitgeteilt wird, dass die Anwendung auf persönliche Daten zugreift, und dem Benutzer die Entscheidung zum Fortsetzen oder Abbrechen überlassen. Wenn ein Endbenutzer eine solche Warnung aus einem scheinbar unverfänglichen Dokument erhält, kann er die Anwendung beenden, bevor es irgendeine Beeinträchtigung gibt.

## <a name="code-is-blocked-by-the-outlook-object-model-guard"></a>Der Code wird durch den Outlook-Objekt Modellschutz blockiert.
 In Microsoft Office kann verhindert werden, dass Code bestimmte Eigenschaften, Methoden und Objekte im Objektmodell verwendet. Durch Einschränken des Zugriffs auf diese Objekte verhindert Outlook, dass e-Mail-Würmer und Viren das Objektmodell für schädliche Zwecke verwenden. Dieses Sicherheitsfeature wird als Outlook-Objektmodellschutz bezeichnet. Wenn ein VSTO-Add-in versucht, eine beschränkte Eigenschaft oder Methode zu verwenden, während der Objekt Modellschutz aktiviert ist, zeigt Outlook eine Sicherheitswarnung an, die es dem Benutzer ermöglicht, den Vorgang zu beenden, oder ermöglicht es dem Benutzer, der Eigenschaft oder Methode für einen begrenzten Zeitraum Zugriff zu gewähren. Wenn der Benutzer den Vorgang beendet, lösen Outlook-VSTO-Add-Ins, die als Office-Projektmappen in Visual Studio erstellt wurden, eine <xref:System.Runtime.InteropServices.COMException>aus.

 Der Objektmodellschutz kann VSTO-Add-Ins auf unterschiedliche Weise beeinflussen, abhängig davon, ob Outlook mit Microsoft Exchange Server verwendet wird:

- Wird Outlook ohne Exchange verwendet, kann ein Administrator den Objektmodellschutz für alle VSTO-Add-Ins auf dem Computer aktivieren bzw. deaktivieren.

- Wenn Outlook mit Exchange verwendet wird, kann ein Administrator den Objektmodellschutz für alle VSTO-Add-Ins auf dem Computer aktivieren bzw. deaktivieren, oder er kann angeben, dass bestimmte VSTO-Add-Ins unabhängig vom Objektmodellschutz ausgeführt werden können. Administratoren können auch das Verhalten des Objektmodellschutzes für bestimmte Bereiche des Objektmodells ändern. So können Administratoren z. b. automatisch zulassen, dass VSTO-Add-Ins eine e-Mail Programm gesteuert senden, auch wenn der Objekt Modellschutz aktiviert ist.

  Beginnend mit Outlook 2007 wurde das Verhalten des Objektmodellschutzes geändert, um die Entwickler- und Benutzerfreundlichkeit zu verbessern, aber gleichzeitig Outlook zu schützen. Weitere Informationen finden Sie unter [Code Security Changes in Outlook 2007](/previous-versions/office/developer/office-2007/bb226709(v=office.12)).

### <a name="minimize-object-model-guard-warnings"></a>Minimieren von Warnungen des Objekt modellschutzes
 Damit Sicherheitswarnungen vermieden werden, wenn Sie beschränkte Eigenschaften und Methoden verwenden, müssen Sie sicherstellen, dass das VSTO-Add-In Outlook-Objekte aus dem `Application` -Feld der `ThisAddIn` -Klasse im Projekt abruft. Weitere Informationen zu diesem Feld finden Sie unter [Program VSTO Add-ins](../vsto/programming-vsto-add-ins.md).

 Nur Outlook-Objekten, die aus diesem Objekt abgerufen wurden, kann vom Objektmodellschutz vertraut werden. Im Gegensatz dazu sind Objekte, die aus einem neuen `Microsoft.Office.Interop.Outlook.Application`-Objekt abgerufen wurden, nicht vertrauenswürdig, sodass die beschränkten Eigenschaften und Methoden Sicherheitswarnungen auslösen, wenn der Objektmodellschutz aktiviert ist.

 Im folgenden Codebeispiel wird eine Sicherheitswarnung angezeigt, wenn der Objektmodellschutz aktiviert wird. Die `To`-Eigenschaft der `Microsoft.Office.Interop.Outlook.MailItem`-Klasse wird durch den Objektmodellschutz beschränkt. Das- `Microsoft.Office.Interop.Outlook.MailItem` Objekt ist nicht vertrauenswürdig, da der Code es aus einem abruft `Microsoft.Office.Interop.Outlook.Application` , das mit dem **New** -Operator erstellt wird, anstatt es aus dem-Feld zu erhalten `Application` .

 [!code-csharp[Trin_VstcoreOutlookSecurity#1](../vsto/codesnippet/CSharp/Trin_VstcoreOutlookSecurity/ThisAddIn.cs#1)]
 [!code-vb[Trin_VstcoreOutlookSecurity#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreOutlookSecurity/ThisAddIn.vb#1)]

 Im folgenden Codebeispiel wird veranschaulicht, wie die Eigenschaft eingeschränkt auf eines- `Microsoft.Office.Interop.Outlook.MailItem` Objekts verwendet wird, das vom Objekt Modellschutz als vertrauenswürdig eingestuft wird. Im Code wird das vertrauenswürdige `Application`-Feld verwendet, um das `Microsoft.Office.Interop.Outlook.MailItem`-Objekt abzurufen.

 [!code-csharp[Trin_VstcoreOutlookSecurity#2](../vsto/codesnippet/CSharp/Trin_VstcoreOutlookSecurity/ThisAddIn.cs#2)]
 [!code-vb[Trin_VstcoreOutlookSecurity#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreOutlookSecurity/ThisAddIn.vb#2)]

> [!NOTE]
> Wenn Outlook mit Exchange verwendet wird, ist es nicht möglich, durch ein Abrufen aller Outlook-Objekte aus `ThisAddIn.Application` sicherzustellen, dass Ihr VSTO-Add-In auf das gesamte Outlook-Objektmodell zugreifen kann. Wenn z. b. ein Exchange-Administrator Outlook so festlegt, dass alle Zugriffsversuche auf die Adressinformationen mithilfe des Outlook-Objektmodells automatisch verweigert werden, gestattet Outlook dem vorherigen Codebeispiel nicht den Zugriff auf die Eigenschaft "to", obwohl das Codebeispiel das vertrauenswürdige `ThisAddIn.Application` Feld verwendet.

### <a name="specify-which-add-ins-to-trust-when-using-exchange"></a>Angeben, welche Add-ins vertrauenswürdig sind, wenn Exchange verwendet wird
 Wenn Outlook mit Exchange verwendet wird, können Administratoren angeben, dass bestimmte VSTO-Add-Ins unabhängig vom Objektmodellschutz ausgeführt werden können. Outlook-VSTO-Add-Ins, die als Office-Projektmappen in Visual Studio erstellt wurden, können nicht einzeln als vertrauenswürdig festgelegt werden, sondern nur als Gruppe.

 Outlook vertraut ein VSTO-Add-in auf der Grundlage eines Hashcodes der Einstiegspunkt-DLL des VSTO-Add-Ins. Alle Outlook-VSTO-Add-Ins, die auf abzielen, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] verwenden dieselbe Einstiegspunkt-DLL (*VSTOLoader.dll*). Dies bedeutet Folgendes: Wenn ein Administrator einem VSTO-Add-in, das als Ziel hat, vertraut, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ohne dass der Objekt Modellschutz ausgeführt wird, werden alle anderen VSTO-Add-Ins, die auf ausgerichtet [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] sind, ebenfalls als vertrauenswürdig eingestuft. Weitere Informationen zu Vertrauensstellungen für spezielle VSTO-Add-Ins, damit diese unabhängig vom Objektmodellschutz ausgeführt werden können, finden Sie unter [Angeben der Methode zur Verwaltung von Virenschutzfeatures in Outlook](/previous-versions/office/office-2007-resource-kit/cc179194(v=office.12)).

## <a name="permission-changes-do-not-take-effect-immediately"></a>Berechtigungs Änderungen werden nicht sofort wirksam.
 Wenn der Administrator Berechtigungen für ein Dokument oder eine Assembly ändert, müssen die Benutzer alle Office-Anwendungen beenden und dann neu starten, damit die Änderungen wirksam werden.

 Andere Anwendungen, die als Host für Microsoft Office-Anwendungen fungieren, können ebenfalls verhindern, dass die neuen Berechtigungen wirksam werden. Benutzer sollten alle Anwendungen beenden, die Office verwenden (gehostete oder eigenständige), wenn die Sicherheitsrichtlinien geändert wurden.

## <a name="trust-center-settings-in-the-microsoft-office-system-do-not-affect-add-ins-or-document-level-customizations"></a>Trust Center-Einstellungen im Microsoft Office System haben keine Auswirkungen auf Add-Ins oder Anpassungen auf Dokument Ebene.
 Benutzer können verhindern, dass VSTO-Add-Ins geladen werden, indem sie eine Option im **Trust Center** festlegen. Allerdings wirken sich diese Vertrauenseinstellungen nicht auf VSTO-Add-Ins aus, die als Office-Projektmappen in Visual Studio erstellt wurden.

 Wenn Benutzer das Laden von VSTO-Add-Ins über das **Trust Center** verhindern, werden die folgenden Typen von VSTO-Add-Ins nicht geladen:

- Verwaltete und nicht verwaltete COM-VSTO Add-Ins

- Verwaltete und nicht verwaltete SmartDocuments

- Verwaltete und nicht verwaltete Automatisierungs-VSTO Add-Ins

- Verwaltete und nicht verwaltete Echtzeitdatenkomponenten

  Die folgenden Verfahren beschreiben, wie Benutzer das **Trust Center** verwenden können, um zu verhindern, dass VSTO-Add-Ins in Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] und Microsoft Office 2010 geladen werden. Diese Verfahren wirken sich nicht auf VSTO-Add-Ins oder Anpassungen aus, die mit den Office-Entwicklungstools in Visual Studio erstellt wurden.

#### <a name="to-disable-vsto-add-ins-in-microsoft-office-2010-and-microsoft-office_15_short-applications"></a>So deaktivieren Sie VSTO-Add-Ins in Microsoft Office 2010- und Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] -Anwendungen

1. Wählen Sie die Registerkarte **Datei** aus.

2. Wählen Sie die **options** Schaltfläche *ApplicationName* aus.

3. Wählen Sie im Kategorienbereich den Eintrag **Trust Center** aus.

4. Wählen Sie im Detailbereich die Option **Einstellungen für das Trust Center** aus.

5. Wählen Sie im Kategorienbereich den Eintrag **Add-Ins** aus.

6. Wählen Sie im Detailbereich die Option **Anwendungs-Add-Ins müssen von einem vertrauenswürdigen Herausgeber signiert sein** oder **Alle Anwendungs-Add-Ins deaktivieren** aus.

## <a name="see-also"></a>Weitere Informationen
- [Sichere Office-Lösungen](../vsto/securing-office-solutions.md)
