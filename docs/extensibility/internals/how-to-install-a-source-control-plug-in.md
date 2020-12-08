---
title: 'Gewusst wie: Installieren eines Quellcodeverwaltungs-Plug-ins | Microsoft-Dokumentation'
description: Erfahren Sie, wie Sie ein Quellcodeverwaltungs-Plug-in in Visual Studio installieren, indem Sie es in die Plug-in-API für die Visual Studio-Quell Code Verwaltung integrieren und seine dll registrieren.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- installation [Visual Studio SDK], source control plug-ins
- source control plug-ins, installing
ms.assetid: 9e2e01d9-7beb-42b2-99b2-86995578afda
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2496de5d1139d66e4ae9072b551ada990cf856dd
ms.sourcegitcommit: 2f964946d7044cc7d49b3fc10b413ca06cb2d11b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2020
ms.locfileid: "96761217"
---
# <a name="how-to-install-a-source-control-plug-in"></a>Gewusst wie: Installieren eines Quellcodeverwaltungs-Plug-ins
Das Erstellen eines Quellcodeverwaltungs-Plug-ins umfasst drei Schritte:

1. Erstellen Sie eine DLL mit den im Quellcodeverwaltungs-Plug-in-API-Referenz Abschnitt dieser Dokumentation definierten Funktionen.

2. Implementieren Sie die API-definierten Funktionen für das Quellcodeverwaltungs-Plug-in. Wenn [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dies aufgerufen wird, stellen Sie Schnittstellen und Dialogfelder über das Plug-in zur Verfügung.

3. Registrieren Sie die dll, indem Sie entsprechende Registrierungseinträge erstellen.

## <a name="integration-with-visual-studio"></a>Integration in Visual Studio
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] unterstützt Quellcodeverwaltungs-Plug-ins, die der Quellcodeverwaltungs-Plug-in-API entsprechen.

### <a name="register-the-source-control-plug-in"></a>Quellcodeverwaltungs-Plug-in registrieren
 Bevor eine integrierte Entwicklungsumgebung (Integrated Development Environment, IDE) in das Quell Code Verwaltungssystem aufgerufen werden kann, muss zuerst die Quellcodeverwaltungs-Plug-in-dll gefunden werden, die die API exportiert.

#### <a name="to-register-the-source-control-plug-in-dll"></a>So registrieren Sie die Quellcodeverwaltungs-Plug-in-dll

1. Fügen Sie unter dem **HKEY_LOCAL_MACHINE** Schlüssel im **Software** Unterschlüssel, der den Unterschlüssel für den Firmennamen, gefolgt von ihrem Produktnamen Unterschlüssel, zwei Einträge hinzu. Das Muster ist **\\ \<company name> \\ \<product name>HKEY_LOCAL_MACHINE\SOFTWARE\\ Wert \<entry>**  =  *value*. Die beiden Einträge werden immer als **sccservername** und **sccserverpath** bezeichnet. Jede ist eine reguläre Zeichenfolge.

    Wenn der Name Ihres Unternehmens beispielsweise Microsoft lautet und das Quell Code Verwaltungs Produkt SourceSafe heißt, wird dieser Registrierungs Pfad **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe**. In diesem Unterschlüssel ist der erste Eintrag, **sccservername**, eine vom Benutzer lesbare Zeichenfolge, die Ihr Produkt benennt. Der zweite Eintrag, **sccserverpath**, ist der vollständige Pfad zu der Quellcodeverwaltungs-Plug-in-dll, mit der die IDE eine Verbindung herstellen soll. Im folgenden finden Sie Beispiel Registrierungseinträge:

   |Beispiel Registrierungs Eintrag|Beispielwert|
   |---------------------------|------------------|
   |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerName|Microsoft Visual SourceSafe|
   |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerPath|*c:\vss\win32\ssscc.dll*|

   > [!NOTE]
   > Sccserverpath ist der vollständige Pfad zum SourceSafe-Plug-in. Ihr Quellcodeverwaltungs-Plug-in verwendet unterschiedliche Firmen-und Produktnamen, aber dieselben Registrierungs Einstiegs Pfade.

2. Die folgenden optionalen Registrierungseinträge können verwendet werden, um das Verhalten des Quellcodeverwaltungs-Plug-ins zu ändern. Diese Einträge werden in den gleichen Unterschlüssel wie " **sccservername** " und " **sccserverpath**" eingefügt.

   - Der Eintrag **hideinvisualstudioregistry** kann verwendet werden, wenn Sie nicht möchten, dass das Quellcodeverwaltungs-Plug-in in der **Plug-in-Auswahl** Liste von angezeigt wird [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Dieser Eintrag wirkt sich auch auf den automatischen Wechsel zum Quellcodeverwaltungs-Plug-in aus. Eine mögliche Verwendung für diesen Eintrag ist, wenn Sie ein Quell Code Verwaltungspaket bereitstellen, das das Quellcodeverwaltungs-Plug-in ersetzt, Sie den Benutzer jedoch leichter von der Verwendung des Quellcodeverwaltungs-Plug-ins zum Quell Code Verwaltungspaket migrieren möchten. Wenn das Quell Code Verwaltungspaket installiert ist, wird dieser Registrierungs Eintrag festgelegt, der das Plug-in ausblendet.

      **Hideinvisualstudio** ist ein DWORD-Wert, der auf *1* festgelegt wird, um das Plug-in auszublenden, oder auf *0* , um das Plug-in anzuzeigen. Wenn der Registrierungs Eintrag nicht angezeigt wird, besteht das Standardverhalten darin, das Plug-in anzuzeigen.

   - Der Registrierungs Eintrag **disablesccmanager** kann verwendet werden, um die **\<Source Control Server> Startmenü-** Option zu deaktivieren oder auszublenden, die normalerweise im Untermenü **Datei**  >  **Quell** Code Verwaltung angezeigt wird. Wenn Sie diese Menüoption auswählen, wird die [sccrunscc](../../extensibility/sccrunscc-function.md) -Funktion aufgerufen. Das Quellcodeverwaltungs-Plug-in unterstützt möglicherweise kein externes Programm. Daher sollten **Sie die** Startmenü-Option deaktivieren oder sogar ausblenden.

      **Disablesccmanager** ist ein DWORD-Wert, und wird auf *0* festgelegt, um die Menüoption **\<Source Control Server> Start** zu aktivieren. Legen Sie auf *1* fest, um die Menüoption zu deaktivieren, und legen Sie auf *2* fest, um die Menüoption auszublenden. Wenn dieser Registrierungs Eintrag nicht angezeigt wird, ist das Standardverhalten, die Menüoption anzuzeigen.

   | Beispiel Registrierungs Eintrag | Beispielwert |
   | - |--------------|
   | HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\HideInVisualStudio | 1 |
   | HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\DisableSccManager | 1 |

3. Fügen Sie den Unterschlüssel **sourcecodecontrolprovider** unter dem **HKEY_LOCAL_MACHINE** Schlüssel im **Software** Unterschlüssel hinzu.

    Unter diesem Unterschlüssel wird der Registrierungs Eintrag **providerregkey** auf eine Zeichenfolge festgelegt, die den Unterschlüssel darstellt, den Sie in der Registrierung in Schritt 1 abgelegt haben. Bei dem Muster handelt es sich um **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey**  =  *Software \\<Firmennamen \> \\<Produktnamen \>*.

    Im folgenden finden Sie Beispiel Inhalt für diesen Unterschlüssel.

   |Registrierungseintrag|Beispielwert|
   |--------------------|------------------|
   |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey|Software\microsoft\sourcesafe|

   > [!NOTE]
   > Das Quellcodeverwaltungs-Plug-in verwendet die gleichen Unterschlüssel-und Eintrags Namen, der Wert ist jedoch anders.

4. Erstellen Sie unter dem Unterschlüssel **sourcecodecontrolprovider** einen Unterschlüssel namens **installedsccproviders** , und platzieren Sie dann einen Eintrag unter diesem Unterschlüssel.

    Der Name dieses Eintrags ist der vom Benutzer lesbare Name des Anbieters (identisch mit dem Wert, der für den Eintrag sccservername angegeben wurde), und der Wert ist wieder einmal der Unterschlüssel, der in Schritt 1 erstellt wurde. Das Muster ist **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\\<Anzeige Name \>**  =  *Software \\<Firmenname \> \\<Produktnamen \>*.

    Beispiel:

   |Beispiel Registrierungs Eintrag|Beispielwert|
   |---------------------------|------------------|
   |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\Microsoft Visual SourceSafe|Software\microsoft\sourcesafe|

   > [!NOTE]
   > Auf diese Weise können mehrere Plug-Ins für die Quell Code Verwaltung registriert werden. So [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] findet alle installierten API-basierten Plug-Ins für Quellcodeverwaltungs-Plug-ins.

## <a name="how-an-ide-locates-the-dll"></a>Wie eine IDE die dll lokalisiert
 Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE bietet zwei Möglichkeiten, die Plug-in-dll der Quell Code Verwaltung zu finden:

- Suchen Sie das Standard-Quellcodeverwaltungs-Plug-in, und stellen Sie eine automatische Verbindung her

- Alle registrierten Quellcodeverwaltungs-Plug-ins suchen, von denen der Benutzer eine Auswahl wählt.

  Um die dll auf die erste Weise zu finden, sucht die IDE unter dem **HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider** Unterschlüssel für den Eintrag **providerregkey**. Der Wert dieses Eintrags verweist auf einen anderen Unterschlüssel. Die IDE sucht dann in diesem zweiten Unterschlüssel unter **HKEY_LOCAL_MACHINE** nach einem Eintrag mit dem Namen **sccserverpath** . Der Wert dieses Eintrags zeigt die IDE auf die dll.

> [!NOTE]
> Die IDE lädt keine DLLs aus relativen Pfaden (z. b. *.\NewProvider.DLL*). Es muss ein vollständiger Pfad zur DLL angegeben werden (z. b. *c:\Providers\NewProvider.DLL*). Dadurch wird die Sicherheit der IDE verbessert, indem verhindert wird, dass nicht autorisierte oder nicht autorisierte Plug-in-DLLs geladen werden.

 Um die dll auf die zweite Weise zu finden, sucht die IDE unter dem **HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider\InstalledSCCProviders** Unterschlüssel für alle Einträge. Jeder Eintrag hat einen Namen und einen Wert. Die IDE zeigt dem Benutzer eine Liste mit diesen Namen. Wenn der Benutzer einen Namen auswählt, findet die IDE den Wert für den ausgewählten Namen, der auf einen Unterschlüssel zeigt. Die IDE sucht in diesem Unterschlüssel unter **HKEY_LOCAL_MACHINE** nach einem Eintrag mit dem Namen **sccserverpath** . Der Wert dieses Eintrags verweist auf die richtige dll der IDE.

 Ein Quellcodeverwaltungs-Plug-in muss beide Methoden zum Auffinden der DLL unterstützen und daher **providerregkey** festlegen und jede vorherige Einstellung überschreiben. Noch wichtiger ist, dass es sich selbst der Liste der **installedsccproviders** hinzufügen muss, damit der Benutzer entscheiden kann, welches Quellcodeverwaltungs-Plug-in verwendet werden soll.

> [!NOTE]
> Da der **HKEY_LOCAL_MACHINE** Schlüssel verwendet wird, kann nur ein Quellcodeverwaltungs-Plug-in als Standard-Quellcodeverwaltungs-Plug-in auf einem bestimmten Computer registriert werden ( [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ermöglicht Benutzern jedoch, zu bestimmen, welches Quellcodeverwaltungs-Plug-in für eine bestimmte Lösung tatsächlich verwendet werden soll). Überprüfen Sie während des Installationsvorgangs, ob ein Quellcodeverwaltungs-Plug-in bereits festgelegt ist. Wenn dies der Fall ist, Fragen Sie den Benutzer, ob das neue Quellcodeverwaltungs-Plug-in, das als Standard installiert wird, festgelegt werden soll. Entfernen Sie während der Installation keine anderen Registrierungs Unterschlüssel, die allen Quellcodeverwaltungs-Plug-ins in **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider** gemeinsam sind. Entfernen Sie nur Ihren speziellen SCC-Unterschlüssel.

## <a name="how-the-ide-detects-version-1213-support"></a>Erkennen der Unterstützung der Version 1.2/1.3 durch die IDE
 Wie wird von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] erkannt, ob ein Plug-in die API der Quell Code Verwaltung-Plug-in-API Version 1,2 und 1,3 unterstützt? Um erweiterte Funktionen zu deklarieren, muss das Quellcodeverwaltungs-Plug-in die entsprechende Funktion implementieren:

 Zuerst [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] überprüft den Wert, der zurückgegeben wird, indem [sccgetversion](../../extensibility/sccgetversion-function.md)aufgerufen wird. Der Wert muss größer oder gleich 1,2 sein.

 Anschließend [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bestimmt, ob die neue Funktion unterstützt wird, indem das- `lpSccCaps` Argument auf [sccinitialize](../../extensibility/sccinitialize-function.md)überprüft wird.

 Wenn beide Bedingungen erfüllt sind, können die neuen Funktionen, die in den Versionen 1,2 und 1,3 unterstützt werden, aufgerufen werden.

## <a name="see-also"></a>Weitere Informationen
- [Einstieg in die Quellcodeverwaltungs-Plug-ins](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)
