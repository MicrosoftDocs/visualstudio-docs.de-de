---
title: Hinzufügen von Ebeneninteraktionsdaten über die Befehlszeile | Microsoft-Dokumentation
description: Verwenden Sie für Anwendungen mit mehreren Ebenen, die mit mindestens einer Datenbank kommunizieren, die Profilerstellung für die Ebeneninteraktionsdaten zur Ausführungszeit von synchronen Aufrufen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tier interaction profiling method
- profiling tools,tier interaction method
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 9070e515fd59f7b29427f20322ef6cb1a01afaee
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99901329"
---
# <a name="add-tier-interaction-data-from-the-command-line"></a>Hinzufügen von Ebeneninteraktionsdaten über die Befehlszeile

Die Profilerstellung für Ebeneninteraktion stellt weitere Informationen zu den Ausführungszeiten der [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)]-Aufrufe von Anwendungen mit mehreren Ebenen, die mit einer oder mehreren Datenbanken kommunizieren.

**Windows 8 und Windows Server 2012**

Um Ebeneninteraktionsdaten für Windows 8-Desktop-Apps und Windows Server 2012-Apps zu erfassen, müssen Sie die Instrumentierungsmethode verwenden. Das Erfassen von Ebeneninteraktionsdaten in UWP-Apps wird nicht unterstützt.

**Visual Studio-Editionen**

Profilerstellungsdaten für die Ebeneninteraktion können mit einer beliebigen Visual Studio-Edition erfasst werden. Allerdings können Profilerstellungsdaten für die Ebeneninteraktion nur in Visual Studio Enterprise angezeigt werden.

**Sammeln von TIP-Daten auf einem Remotecomputer**

Sie müssen Sie die Datei **vs_profiler\_** _\<Platform>_ **\_** _\<Language>_ **.exe** aus dem Ordner _%VInstallDir%_ **\Team Tools\Performance Tools\Setups** eines Visual Studio-Computers auf den Remotecomputer kopieren und dort installieren, um Ebeneninteraktionsdaten auf einem Remotecomputer zu erfassen. Sie können nicht die Profilerstellungstools im Downloadpaket der [Visual Studio-Remotetools](../debugger/remote-debugging.md) verwenden.

**TIP-Berichte**

Ebeneninteraktionsdaten können nur in Visual Studio Enterprise angezeigt werden. Dateibasierte Ebeneninteraktionsberichte über [VSPerfReport](../profiling/vsperfreport.md) sind nicht verfügbar.

## <a name="add-tier-interaction-data-with-vsperfcmd"></a>Hinzufügen von Ebeneninteraktionsdaten mit VSPerfCmd

Mit dem Befehlszeilentool VSPerfASPNETCmd können Sie auf die vollständige, im Profilerstellungstool verfügbare Funktionalität zugreifen. Sie können den mit VSPerfCmd erfassten Profilerstellungsdaten Interaktionsebene hinzufügen, indem Sie das Hilfsprogramm **VSPerfCLREnv** verwenden, um Umgebungsvariablen festzulegen oder zu entfernen. Dieses Programm aktiviert Ebeneninteraktionsdaten. Die von Ihnen vorgenommenen Optionen und die für das Erfassen von Daten erforderlichen Prozeduren sind von der Art der Anwendung, für die Sie gerade ein Profil erstellen, abhängig.

## <a name="profile-stand-alone-applications"></a>Profilerstellung für eigenständige Anwendungen

Um Ebeneninteraktionsdaten einer Anwendung hinzuzufügen, die nicht von einem anderen Prozess, wie z.B. einer Windows-Desktopanwendung, die synchrone [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)]-Aufrufe an eine SQLServer-Datenbank durchführt, ausgeführt wird, verwenden Sie die Option **VSPerfClrEnv /InteractionOn**, um Umgebungsvariablen festzulegen, und die Option **VSPerfClrEnv /InteractionOff**, um diese zu entfernen.

Im folgenden Beispiel wird das Profil mithilfe der Instrumentierungsmethode für eine Windows-Desktopanwendung erstellt und Ebeneninteraktionsdaten werden erfasst.

### <a name="profile-a-windows-desktop-application-example"></a>Beispiel für die Profilerstellung einer Windows-Desktopanwendung

1. Öffnen Sie die Eingabeaufforderungsfenster mit Administratorrechten. Klicken Sie auf **Start**, zeigen Sie auf **Alle Programme**, und zeigen Sie dann auf **Zubehör**. Klicken Sie mit der rechten Maustaste auf **Eingabeaufforderung**, und klicken Sie dann auf **Als Administrator ausführen**.

2. Initialisieren Sie die .TIP-Umgebungsvariablen für die .NET-Profilerstellung. Geben Sie folgende Befehle ein:

    ```cmd
    vsperfclrenv /traceon
    vsperfclrenv /interactionon
    ```

3. Starten Sie den Profiler. Geben Sie folgenden Befehl ein:

    ```cmd
    vsperfcmd /start:trace /output:Desktop_tip.vsp
    ```

4. Starten Sie die Anwendung mit VSPerfCmd. Geben Sie folgenden Befehl ein:

    ```cmd
    vsperfcmd /launch:DesktopApp.exe
    ```

5. Führen Sie die Anwendung aus, um Profilerstellungsdaten zu erfassen; schließen Sie dann die Anwendung wie gewohnt.

6. Löschen Sie die TIP-Umgebungsvariablen. Geben Sie folgenden Befehl ein:

    ```cmd
    vsperfclrenv /off
    ```

Weitere Informationen finden Sie unter [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md).

## <a name="profile-services"></a>Profilerstellung für Dienste

Um Dienstprofile, einschließlich [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Anwendungen, zu erstellen,verwenden Sie die Option **VSPerfClrEnv /GlobalInteractionOn**, um Umgebungsvariablen festzulegen, und verwenden Sie die Option **VSPerfClrEnv /GlobalInteractionOff**, um diese zu entfernen.

Während Sie Dienstprofile erstellen, einschließlich [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Webanwendungen, müssen Sie wahrscheinlich den Computer neu starten, um die Profilerstellung zu aktivieren.

Im folgenden Beispiel wird mithilfe der Instrumentierungsmethode ein Profil für einen Windows-Dienst erstellt, und Ebeneninteraktionsdaten werden erfasst.

### <a name="profile-a-windows-service-example"></a>Beispiel für die Profilerstellung für einen Windows-Dienst

1. Installieren Sie den Dienst, falls notwendig.

2. Öffnen Sie die Eingabeaufforderungsfenster mit Administratorrechten. Klicken Sie auf **Start**, zeigen Sie auf **Alle Programme**, und zeigen Sie dann auf **Zubehör**. Klicken Sie mit der rechten Maustaste auf **Eingabeaufforderung**, und klicken Sie dann auf **Als Administrator ausführen**.

3. Initialisieren Sie die .NET-Umgebungsvariablen für die Profilerstellung. Geben Sie folgenden Befehl ein:

    ```cmd
    vsperfclrenv /globaltraceon
    ```

4. Initialisieren Sie die TIP-Umgebungsvariablen. Geben Sie folgenden Befehl ein:

    ```cmd
    vsperfclrenv /globalinteractionon
    ```

5. Starten Sie den Computer neu, damit die Umgebungsvariablen registriert werden.

6. Öffnen Sie die Eingabeaufforderungsfenster mit Administratorrechten.

7. Starten Sie den Profiler. Geben Sie folgenden Befehl ein:

    ```cmd
    vsperfcmd /start:trace /output:MiddleTier_tip.vsp /user:SYSTEM /crosssession
    ```

8. Starten Sie den Dienst bei Bedarf.

9. Fügen Sie den Profiler an den Dienst an. Geben Sie folgenden Befehl ein:

    ```cmd
    vsperfcmd /attach:MiddleTier.exe /output:MyService_tip.vsp /user:SYSTEM /crosssession
    ```

10. Führen Sie den Dienst aus, und erfassen Sie Profilerstellungsdaten.

11. Beenden der Profilerstellung. Geben Sie folgenden Befehl ein:

     `vsperfcmd /detach`

12. Löschen Sie die Umgebungsvariablen für die .NET- und TIP-Profilerstellung. Geben Sie folgenden Befehl ein:

    ```cmd
    vsperfclrenv /globaloff
    ```

13. Starten Sie den Computer neu, damit die gelöschten Umgebungsdaten registriert werden.

Weitere Informationen finden Sie in einem der folgenden Themen:

[Profilerstellung für ASP.NET-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)

[Profilerstellung für Dienste](../profiling/command-line-profiling-of-services.md)

## <a name="add-tier-interaction-data-with-vsperfaspnetcmd"></a>Hinzufügen von Ebeneninteraktionsdaten mit VSPerfASPNETCmd

Mit dem Befehlszeilentool VSPerfASPNETCmd können Sie problemlos Profile für [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Webanwendungen erstellen. Verglichen mit dem Befehlszeilentool **VSPerfCmd** stehen weniger Optionen zur Verfügung, es müssen keine Umgebungsvariablen festgelegt werden, und ein Neustart des Computers ist nicht erforderlich. Die Features von VSPerfASPNETCmd ermöglichen ein besonders einfaches Erfassen von Ebeneninteraktionsdaten.

Um den Profilerstellungsdaten mithilfe von VSPerfASPNETCmd erfasste Ebeneninteraktionsdaten hinzuzufügen, fügen Sie die Option **/TIP** in die Befehlszeile ein. Sie können z.B. folgende Befehlszeile verwenden, um Ebeneninteraktionsdaten für eine [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Webanwendung mithilfe der Instrumentierungsmethode hinzuzufügen:

```cmd
vsperfaspnetcmd /tip /trace http://localhost/MyWebApp
```

Weitere Informationen zu VSPerfASPNETCmd finden Sie unter [Schnelle Website-Profilerstellung mit VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).
