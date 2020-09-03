---
title: Aktualisieren von Tests der programmierten UI
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 11232a83-73ea-46bd-bc0c-46f74f6e3a42
caps.latest.revision: 35
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3a29e531ca9b2a74e67abf80a0e3017a0f5b0b07
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "74298001"
---
# <a name="upgrading-coded-ui-tests-from-visual-studio-2010"></a>Upgrade der Tests der programmierten UI von Visual Studio 2010
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tests der programmierten UI enthaltende Testprojekte, die in [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] erstellt wurden, werden unbeaufsichtigt repariert, wenn sie in Visual Studio 2012 geöffnet werden. Wenn Testprojekte in das Quellsteuerelement eingecheckt werden, werden die Projektdateien für diese Reparatur ausgecheckt. Nach der Reparatur können die Tests der programmierten UI enthaltende Testprojekte sowohl in [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] SP1 als auch in [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]verwendet werden.

 **Anforderungen**

- Visual Studio Enterprise

> [!NOTE]
> Visual Studio enthält mehr als ein Typ des Testprojekts. Wenn Sie einen neuen Test der programmierten UI erstellen, wird er in einem Projekttyp für den Test der programmierten UI erstellt. Weitere Informationen finden Sie unter [Upgrade der Tests von früheren Visual Studio-Versionen](https://msdn.microsoft.com/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52).

> [!WARNING]
> Tests der programmierten UI enthaltende[!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] -Testprojekte müssen neu erstellt werden, wenn Sie das Testprojekt in [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] oder [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] oder zusammen mit [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]öffnen.

> [!WARNING]
> Wenn ein in [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] erstelltes Testprojekt, das nur Komponententests enthält, in [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]geöffnet wird, ist es nicht möglich, Tests der programmierten UI hinzuzufügen. Auf ähnliche Weise können Sie einem in [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]erstellten Komponententestprojekt keinen Test der programmierten UI hinzufügen.

## <a name="compatibility-issues-between-visual-studio-2010-and-visual-studio-2012"></a>Kompatibilitätsprobleme mit Visual Studio 2010 und Visual Studio 2012
 In der folgenden Tabelle werden Probleme aufgeführt, die beim Migrieren von Tests der programmierten UI zwischen [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] und [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]beachtet werden sollten.

> [!CAUTION]
> Es ist ein bekanntes Problem, dass Verweise in Projekten für Tests der programmierten UI im Projektmappen-Explorer nicht angezeigt werden. Weitere Informationen finden Sie in der auf den [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] -Installationsmedien enthaltenen Infodatei.

|Funktionalität der programmierten UI|Problem|Lösung|
|----------------------------|-----------|--------------|
|Testen der Benutzeroberfläche von Silverlight wird in [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]nicht unterstützt.|**Fehlerhafter Build.**<br /><br /> Wenn Sie über [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] Feature Pack 2 verfügen und Projekte für den Test der programmierten UI für Silverlight-Anwendungen erstellt haben, können diese Projekte in [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]nicht geöffnet werden.|Es wird empfohlen, dass Sie diese Projekte nur in [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] Feature Pack 2 verwalten.|
|Testen der Benutzeroberfläche von Firefox wird in [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]nicht unterstützt.|**Build wurde erfolgreich erstellt, fehlerhafter Testlauf**<br /><br /> Wenn Sie über [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] Feature Pack 2 verfügen und Projekte für den Test der programmierten UI für Webanwendungen in Firefox erstellt haben, können diese Projekte in [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]nicht geöffnet werden.|Es wird empfohlen, dass Sie diese Projekte nur in [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] Feature Pack 2 verwalten.|
|Neue APIs zum Testen des Benutzeroberflächencodes wurden in [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]hinzugefügt.|**Fehlerhafter Build.**<br /><br /> Wenn Sie Tests der programmierten UI mithilfe der neuen API zum Testen der Benutzeroberfläche in [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]erstellen, können diese Projekte in [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)]nicht geöffnet werden.|Projekte mit der neuen API sollten nur in [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] verwaltet werden.|
|In [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)]wurden Verweise in einer „Choose“-Anweisung in der CSPROJ-Datei hinzugefügt. In [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]verwenden wir eine Feedbackzieldatei zum Einbeziehen der Assemblyverweise für Tests der programmierten UI.|In [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]kann einem in [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] (oder SP1) erstellten Testprojekt kein Test der programmierten UI hinzugefügt werden, der keinen Test der programmierten UI enthielt.<br /><br /> Der Reparaturvorgang fügt die Zieldatei und die „Choose“-Anweisung hinzu. Wenn sich ein Test der programmierten UI nicht im Testprojekt befindet, wird das Projekt als repariert markiert, und die entsprechenden Verweise werden nicht hinzugefügt, wenn der Test der programmierten UI in [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]hinzugefügt wird.|Sie müssen mithilfe von [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] ein neues Testprojekt in derselben Projektmappe erstellen und Ihren neuen Test der programmierten UI darin hinzufügen. Alternativ können Sie Tests der programmierten UI in [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] SP1 hinzufügen und dieses Projekt in [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]öffnen.|

## <a name="visual-studio-2010-sp1-update"></a><a name="UpgradingCodedUIFromVS2010_Update"></a> Visual Studio 2010 SP1 Update
 Ein Update für [!INCLUDE[vs2010](../includes/vs2010-md.md)] SP1 mit Kompatibilitätsunterstützung für Visual Studio 2012 und Windows 8 steht als Download im [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=34677) und als Visual Studio-Update bereit.

 Nach dem Anwenden des Updates werden die folgenden [!INCLUDE[vs2010](../includes/vs2010-md.md)] SP1-Toolfeatures für den Test der programmierten UI für Windows 8 verbessert:

- Sie können einen Test der programmierten UI für die Microsoft .NET Framework 4.5-basierten Windows Presentation Foundation-Steuerelemente (WPF) auf einem Computer unter Windows 8 ausführen.

- Sie können einen Test der programmierten UI für Internet Explorer 10 (64 Bit, x64) auf einem Computer unter Windows 8 ausführen.

  Das Update enthält zudem Fixes für die folgenden Probleme:

- **Codeabdeckung:** Unfähigkeit eine durch Visual Studio 2012 in [!INCLUDE[vs2010](../includes/vs2010-md.md)] SP1 erstellte Codeabdeckungsdatei (.coverage) zu öffnen.

- **Isolierte Testartefakte:** Ihr Team verfügt über ein Testartefakt, das in TFS 2010 (Team Foundation Server) einem ungültigen Benutzer zugewiesen ist. Dies ist beispielsweise der Fall, wenn ein Benutzer das Unternehmen verlassen hat, diesem jedoch weiterhin ein Testfall zugewiesen ist. Sie aktualisieren TFS 2010 auf TFS 2012. Sie verwenden [!INCLUDE[TCMext](../includes/tcmext-md.md)] 2010, um eine Verbindung zum aktualisierten TFS-Server herzustellen. Sie können das Testartefakt mithilfe von [!INCLUDE[TCMext](../includes/tcmext-md.md)] 2010 anderen TFS-Benutzern nicht zuweisen.

- **Auslastungstest:** Wenn Sie einen Auslastungstest zusammen mit einem Netzwerktyp ausführen, der nicht dem LAN-Profil auf einem Computer unter Windows 8 entspricht, führt der Netzwerkemulatortreiber dazu, dass das Betriebssystem abstürzt. Weitere Informationen finden Sie unter [KB-Artikel 2736182](https://support.microsoft.com/help/2736182/a-gdr-update-for-visual-studio-2010-sp1-is-available-to-add-compatibil).

## <a name="see-also"></a>Weitere Informationen
 [Portieren, migrieren und Aktualisieren von Visual Studio-Projekten](../porting/porting-migrating-and-upgrading-visual-studio-projects.md) [Aktualisieren von Tests aus früheren Versionen von Visual Studio](https://msdn.microsoft.com/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52) [Verwenden von Benutzeroberflächen Automatisierung zum Testen des Codes](../test/use-ui-automation-to-test-your-code.md) erzeugen eines Tests der programmierten [UI aus einer vorhandenen Aktion aufzeichnen von](https://msdn.microsoft.com/library/56736963-9027-493b-b5c4-2d4e86d1d497) [unterstützten Konfigurationen und Plattformen für Tests](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md) der programmierten UI und Aktions Aufzeichnungen
