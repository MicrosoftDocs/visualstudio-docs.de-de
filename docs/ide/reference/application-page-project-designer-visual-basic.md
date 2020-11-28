---
title: Seite „Anwendung“ der VB-Projekteigenschaften
description: Erfahren Sie, wie Sie auf der Seite „Anwendung“ des Visual Basic-Projekt-Designers die Anwendungseinstellungen und -eigenschaften des Projekts festlegen können.
ms.custom: SEO-VS-2020
ms.date: 10/30/2018
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesApplicationWPF
- vb.ProjectPropertiesApplication
helpviewer_keywords:
- Project Designer, Application page
- Application page in Project Designer
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 675c3fbaaf1a3e49648befebca4927299649b057
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/25/2020
ms.locfileid: "95871417"
---
# <a name="application-page-project-designer-visual-basic"></a>Application Page, Project Designer (Visual Basic)

Legen Sie auf der Seite **Anwendung** des Projekt-Designers die Anwendungseinstellungen und -eigenschaften eines Projekts fest.

Um auf die Seite **Anwendung** zuzugreifen, wählen Sie im **Projektmappen-Explorer** einen Projektknoten (nicht den Knoten **Projektmappen** aus. Wählen Sie dann in der Menüleiste **Projekt** > **Eigenschaften** aus. Wenn der **Projekt-Designer** angezeigt wird, klicken Sie auf die Registerkarte **Anwendung**.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="general-application-settings"></a>Allgemeine Anwendungseinstellungen

Mit den folgenden Optionen können Sie allgemeine Einstellungen für eine Anwendung konfigurieren.

### <a name="assembly-name"></a>Assemblyname

Gibt den Namen der Ausgabedatei an, in der das Assemblymanifest enthalten ist. Wenn Sie diese Eigenschaft ändern, wird auch die Eigenschaft **Ausgabename** geändert.

Sie können den Namen der Ausgabedatei auch an einer Eingabeaufforderung mit dem Compilerschalter [/out (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/out) angeben.

Informationen zum programmgesteuerten Zugreifen auf diese Eigenschaft finden Sie unter <xref:VSLangProj.ProjectProperties.AssemblyName%2A>.

### <a name="root-namespace"></a>Stammnamespace

Legt den Basisnamespace für alle Dateien im Projekt fest. Wenn Sie beispielsweise den **Stammnamespace** auf `Project1` festgelegt haben und eine `Class1` außerhalb aller Namespaces im Code vorhanden ist, würde deren Namespace `Project1.Class1` lauten. Wäre eine `Class2` in einem Namespace `Order` im Code vorhanden ist, würde deren Namespace `Project1.Order.Class2` lauten.

Wenn Sie den **Stammnamespace** löschen, können Sie die Namespacestruktur Ihres Projekts im Code festlegen.

> [!NOTE]
> Wenn Sie das `Global`-Schlüsselwort in einer [Namespaceanweisung](/dotnet/visual-basic/language-reference/statements/namespace-statement) verwenden, können Sie einen Namespace außerhalb des Stammnamespaces Ihres Projekts definieren. Wenn Sie den **Stammnamespace** löschen, wird der Namespace `Global` der Namespace der obersten Ebene, wodurch die Notwendigkeit entfällt, das `Global`-Schlüsselwort in einer `Namespace`-Anweisung zu verwenden. Weitere Informationen finden Sie unter „Global-Schlüsselwort in Namespace-Anweisungen“ unter [Namespaces in Visual Basic](/dotnet/visual-basic/programming-guide/program-structure/namespaces).

Informationen zum Erstellen von Namespaces im Code finden Sie unter [Namespace-Anweisung](/dotnet/visual-basic/language-reference/statements/namespace-statement).

Weitere Informationen zur Stammnamespace-Eigenschaft finden Sie unter [/rootnamespace](/dotnet/visual-basic/reference/command-line-compiler/rootnamespace).

Informationen zum programmgesteuerten Zugreifen auf diese Eigenschaft finden Sie unter <xref:VSLangProj.ProjectProperties.RootNamespace%2A>.

### <a name="target-framework-all-configurations"></a>Zielframework (alle Konfigurationen)

Gibt die .NET-Version an, auf die die Anwendung ausgerichtet ist. Diese Option kann unterschiedliche Werte aufweisen, je nachdem, welche Versionen von .NET auf Ihrem Computer installiert sind.

Für .NET Framework-Projekte entspricht der Standardwert dem Zielframework, das Sie beim Erstellen des Projekts angegeben haben.

> [!NOTE]
> Die im Dialogfeld [Erforderliche Komponenten](../../ide/reference/prerequisites-dialog-box.md) aufgelisteten Pakete mit erforderlichen Komponenten werden automatisch festgelegt, wenn Sie das Dialogfeld zum ersten Mal öffnen. Wenn im Nachhinein Änderungen am Zielframework des Projekts vorgenommen werden, müssen Sie die erforderlichen Komponenten entsprechend dem neuen Zielframework manuell auswählen.

Weitere Informationen finden Sie unter [Übersicht über Frameworkziele](../../ide/visual-studio-multi-targeting-overview.md).

### <a name="application-type"></a>Anwendungstyp

Gibt den Typ der zu erstellenden Anwendung an. Die Werte unterscheiden sich je nach Projekttyp. Für ein **Windows Forms-App**-Projekt können Sie zum Beispiel **Windows Forms-Anwendung**, **Klassenbibliothek**, **Konsolenanwendung**, **Windows-Dienst** oder **Websteuerelementbibliothek** angeben.

Für ein Webanwendungsprojekt müssen Sie **-Klassenbibliothek** angeben.

Weitere Informationen zur Eigenschaft **Anwendungstyp** finden Sie unter [/target (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/target). Informationen zum programmgesteuerten Zugreifen auf diese Eigenschaft finden Sie unter <xref:VSLangProj.ProjectProperties.OutputType%2A>.

### <a name="auto-generate-binding-redirects"></a>Bindungsumleitungen automatisch generieren

Bindungsumleitungen werden zu Ihrem Projekt hinzugefügt, wenn Ihre App oder die zugehörigen Komponenten auf mehrere Versionen derselben Assembly verweisen. Wenn Sie Bindungsumleitungen manuell in der Projektdatei definieren möchten, deaktivieren Sie **Bindungsumleitungen automatisch generieren**.

Weitere Informationen zur Umleitung finden Sie unter [Umleiten von Assemblyversionen](/dotnet/framework/configure-apps/redirect-assembly-versions).

### <a name="startup-form--startup-object--startup-uri"></a>Startformular/Startobjekt/Start-URI

Gibt das Startformular oder den Einstiegspunkt der Anwendung an.

Wenn **Anwendungsframework aktivieren** ausgewählt ist (Standard), heißt diese Liste **Startformular** und zeigt nur Formulare an, da das Anwendungsframework ausschließlich Startformulare und keine Objekte unterstützt.

Wenn es sich bei dem Projekt um eine WPF-Browseranwendung handelt, heißt diese Liste **Start-URI**, und der Standardwert lautet **Page1.xaml**. Die Mithilfe der Liste **Start-URI** können Sie die Benutzeroberflächenressource (ein XAML-Element) angeben, die beim Start der Anwendung angezeigt wird. Weitere Informationen finden Sie unter <xref:System.Windows.Application.StartupUri%2A>.

Wenn **Anwendungsframework aktivieren** deaktiviert ist, wird diese Liste zu **Startobjekt** und zeigt sowohl Formulare als auch Klassen oder Module mit einer `Sub Main` an.

**Startobjekt**  definiert den Einstiegspunkt, der aufgerufen werden soll, wenn die Anwendung geladen wird. Dieser wird üblicherweise entweder auf das Hauptformular der Anwendung oder auf die `Sub Main`-Prozedur festgelegt, die beim Start der Anwendung ausgeführt werden soll. Da Klassenbibliotheken über keinen Einstiegspunkt verfügen, ist ihre einzige Option für diese Eigenschaft **(Keine)** . Weitere Informationen finden Sie unter [/main](/dotnet/visual-basic/reference/command-line-compiler/main). Informationen zum programmgesteuerten Zugriff auf diese Eigenschaft finden Sie unter <xref:VSLangProj.ProjectProperties.StartupObject%2A>.

### <a name="icon"></a>Symbol

Legt die ICO-Datei fest, die als Programmsymbol verwendet werden soll. Wählen Sie **\<Browse...>** aus, um nach einer vorhandenen Grafik zu suchen. Weitere Informationen finden Sie unter [/win32icon](/dotnet/visual-basic/reference/command-line-compiler/win32icon) (oder [/win32icon (C#-Compileroptionen)](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option)). Informationen zum programmgesteuerten Zugriff auf diese Eigenschaft finden Sie unter <xref:VSLangProj.ProjectProperties.ApplicationIcon%2A>.

### <a name="assembly-information"></a>Assemblyinformationen

Klicken Sie auf diese Schaltfläche, um das Dialogfeld[Assemblyinformationen](../../ide/reference/assembly-information-dialog-box.md) anzuzeigen.

### <a name="enable-application-framework"></a>Anwendungsframework aktivieren

Gibt an, ob ein Projekt das Anwendungsframework verwendet. Die Einstellung dieser Option wirkt sich auf die unter **Startformular**/**Startobjekt** verfügbaren Optionen aus.

Ist dieses Kontrollkästchen aktiviert, verwendet die Anwendung die Standard-`Sub Main`. Durch Aktivieren dieses Kontrollkästchens werden die Features im Abschnitt **Eigenschaften des Windows-Anwendungsframeworks** aktiviert, und Sie müssen ein Startformular auswählen.

Ist dieses Kontrollkästchen deaktiviert, verwendet die Anwendung die benutzerdefinierte `Sub Main`, die Sie unter **Startformular** angegeben haben. In diesem Fall können Sie entweder ein Startobjekt (eine benutzerdefinierte `Sub Main` in einer Methode oder Klasse) oder ein Formular angeben. Außerdem sind die Optionen im Abschnitt **Eigenschaften des Windows-Anwendungsframeworks** nicht mehr verfügbar.

### <a name="view-windows-settings"></a>Windows-Einstellungen anzeigen

Klicken Sie auf diese Schaltfläche, um die Datei *app.manifest* zu erstellen und zu öffnen. Visual Studio verwendet diese Datei zum Generieren von Manifestdaten für die Anwendung. Legen Sie dann die von der Benutzerkontensteuerung angeforderte Ausführungsebene fest, indem Sie das `<requestedExecutionLevel>`-Tag in *app.manifest* wie folgt ändern:

`<requestedExecutionLevel level="asInvoker" />`

ClickOnce funktioniert mit der Ebene `asInvoker` oder im virtualisierten Modus (keine Generierung von Manifesten). Um den virtualisierten Modus anzugeben, entfernen Sie das gesamte Tag aus „app.manifest“.

Weitere Informationen zum Generieren von Manifesten finden Sie unter [ClickOnce-Bereitstellung unter Windows Vista](../../deployment/clickonce-deployment-on-windows-vista.md).

## <a name="windows-application-framework-properties"></a>Eigenschaften des Windows-Anwendungsframeworks

Die folgenden Einstellungen sind im Abschnitt **Eigenschaften des Windows-Anwendungsframeworks** verfügbar. Diese Optionen sind nur verfügbar, wenn das Kontrollkästchen **Anwendungsframework aktivieren** aktiviert ist.

> [!TIP]
> Im folgenden Abschnitt werden die Einstellungen **Eigenschaften des Windows-Anwendungsframeworks** beschrieben, die für Windows Presentation Foundation-Apps (WPF) spezifisch sind.

### <a name="enable-xp-visual-styles"></a>Visuelle XP-Stile aktivieren

Aktiviert oder deaktiviert die visuellen Windows XP-Stile, auch als *Windows XP-Designs* bezeichnet. Die visuellen Windows XP-Stile aktivieren z.B. Steuerelemente mit gerundeten Ecken und dynamischen Farben. Die Option ist standardmäßig aktiviert.

### <a name="make-single-instance-application"></a>Einzelinstanzanwendung erstellen

Aktivieren Sie dieses Kontrollkästchen, um zu verhindern, dass Benutzer mehrere Instanzen der Anwendung ausführen. Standardmäßig ist dieses Kontrollkästchen *deaktiviert*, sodass mehrere Instanzen der Anwendung ausgeführt werden können. Weitere Informationen finden Sie beim <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>-Ereignis.

### <a name="save-mysettings-on-shutdown"></a>My.Settings beim Herunterfahren speichern

Aktivieren Sie dieses Kontrollkästchen, um anzugeben, dass die `My.Settings`-Einstellungen der Anwendung beim Herunterfahren des Computers gespeichert werden. Das Kontrollkästchen ist standardmäßig aktiviert. Wird diese Option deaktiviert, können Anwendungseinstellungen manuell durch Aufrufen von `My.Settings.Save` gespeichert werden.

### <a name="authentication-mode"></a>Authentifizierungsmodus

Wählen Sie **Windows** (Standard) aus, um festzulegen, dass der aktuell angemeldete Benutzer über die Windows-Authentifizierung identifiziert wird. Sie können diese Informationen mit dem `My.User`-Objekt zur Laufzeit abrufen. Wählen Sie **Anwendungsdefiniert**, wenn Sie anstelle der standardmäßigen Windows-Authentifizierungsmethoden eigenen Code zum Authentifizieren der Benutzern bereitstellen.

### <a name="shutdown-mode"></a>Modus für das Herunterfahren

Wählen Sie **Beim Schließen des Startformulars** (Standard) aus, um festzulegen, dass die Anwendung beendet wird, wenn das als Startformular festgelegte Formular geschlossen wird, auch wenn andere Formulare geöffnet sind. Wählen Sie **Beim Schließen des letzten Formulars** aus, um festzulegen, dass die Anwendung beendet wird, wenn das letzte Formular geschlossen oder die `My.Application.Exit`- bzw. die `End`-Anweisung explizit aufgerufen wird.

Wählen Sie **Beim expliziten Herunterfahren** aus, um festzulegen, dass die Anwendung bei einem expliziten Aufruf von `Shutdown` beendet wird.

Wählen Sie **Beim Schließen des letzten Fensters** aus, um festzulegen, dass die Anwendung beendet wird, wenn das letzte Fenster geschlossen oder `Shutdown` explizit aufgerufen wird. Dies ist die Standardeinstellung.

Wählen Sie **Beim Schließen des Hauptfensters** aus, um festzulegen, dass die Anwendung beendet wird, wenn das Hauptfenster geschlossen oder `Shutdown` explizit aufgerufen wird.

### <a name="splash-screen"></a>Begrüßungsbildschirm

Wählen Sie das Formular aus, das Sie als Begrüßungsbildschirm verwenden möchten. Sie müssen zuvor mithilfe eines Formulars oder einer Vorlage einen Begrüßungsbildschirm erstellt haben. Der Standardwert lautet **(Keine)** .

### <a name="view-application-events"></a>Anwendungsereignisse anzeigen

Klicken Sie auf diese Schaltfläche, um eine Ereigniscodedatei anzuzeigen, in die Sie Ereignisse für die Anwendungsframeworkereignisse `Startup`, `Shutdown`, `UnhandledException`, `StartupNextInstance` und `NetworkAvailabilityChanged` schreiben können. Sie können auch bestimmte Anwendungsframeworkmethoden überschreiben. Beispielsweise können Sie das Anzeigeverhalten des Begrüßungsbildschirms ändern, indem Sie `OnInitialize` überschreiben.

## <a name="windows-application-framework-properties-for-windows-presentation-foundation-wpf-apps"></a>Eigenschaften des Windows-Anwendungsframeworks für Windows Presentation Foundation-Apps (WPF)

Die folgenden Einstellungen sind im Abschnitt **Eigenschaften des Windows-Anwendungsframeworks** verfügbar, wenn das Projekt eine Windows Presentation Foundation-App (WPF) ist. Diese Optionen sind nur verfügbar, wenn das Kontrollkästchen **Anwendungsframework aktivieren** aktiviert ist. Die in dieser Tabelle aufgeführten Optionen sind nur für WPF oder WPF-Browseranwendungen verfügbar. Sie sind nicht für WPF-Benutzersteuerelement- oder benutzerdefinierte Steuerelementbibliotheken verfügbar.

### <a name="shutdown-mode"></a>Modus für das Herunterfahren

Diese Eigenschaft gilt nur für Windows Presentation Foundation-Anwendungen (WPF).

Wählen Sie **Beim expliziten Herunterfahren** aus, um festzulegen, dass die Anwendung bei einem expliziten Aufruf von <xref:System.Windows.Application.Shutdown%2A> beendet wird.

Wählen Sie **Beim Schließen des letzten Fensters** aus, um festzulegen, dass die Anwendung beendet wird, wenn das letzte Fenster geschlossen oder <xref:System.Windows.Application.Shutdown%2A> explizit aufgerufen wird. Dies ist die Standardeinstellung.

Wählen Sie **Beim Schließen des Hauptfensters** aus, um festzulegen, dass die Anwendung beendet wird, wenn das Hauptfenster geschlossen oder <xref:System.Windows.Application.Shutdown%2A> explizit aufgerufen wird.

Weitere Informationen über die Verwendung diese Einstellung finden Sie unter <xref:System.Windows.Application.Shutdown%2A>.

### <a name="edit-xaml"></a>XAML bearbeiten

Durch Klicken auf diese Schaltfläche wird die Anwendungsdefinitionsdatei („Application.xaml“) im XAML-Editor geöffnet. Wenn Sie auf diese Schaltfläche klicken, wird der Anwendungsdefinitionsknoten von *Application.xaml* geöffnet. Möglicherweise müssen Sie diese Datei bearbeiten, um bestimmte Aufgaben auszuführen, wie z.B. das Definieren von Ressourcen. Wenn keine Anwendungsdefinitionsdatei vorhanden ist, wird sie vom Projekt-Designer erstellt.

### <a name="view-application-events"></a>Anwendungsereignisse anzeigen

Durch Klicken auf diese Schaltfläche wird die `Application`-Klassendatei (*Application.xaml.vb*) in einem Code-Editor geöffnet. Wenn die Datei nicht vorhanden ist, wird sie vom Projekt-Designer mit dem entsprechenden Namen und Namespace erstellt.

Das Objekt <xref:System.Windows.Application> löst Ereignisse aus, wenn bestimmte Anwendungszustandsänderungen stattfinden (z.B. beim Starten oder Herunterfahren der Anwendung). Eine vollständige Liste der Ereignisse, die diese Klasse verfügbar macht, finden Sie unter <xref:System.Windows.Application>. Diese Ereignisse werden im Benutzercodeabschnitt der partiellen `Application`-Klasse verarbeitet.
