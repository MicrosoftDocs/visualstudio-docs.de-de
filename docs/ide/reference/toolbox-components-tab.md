---
title: Toolbox, Registerkarte „Komponenten“
description: Hier erfahren Sie mehr über die Komponenten auf der Registerkarte „Komponenten“ im Fenster „Toolbox“.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.CHOOSEITEMS.FrameworkComponents
- VS.CHOOSEITEMS.COMComponents
- VS.CHOOSEITEMS.UniversalWindowsComponents
helpviewer_keywords:
- Toolbox, Components tab
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: adbc2611cf0d0e08ef356e91e25ed0c4854c4386
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965043"
---
# <a name="toolbox-components-tab"></a>Toolbox, Registerkarte „Komponenten“

Zeigt die Komponenten an, die Sie zu Visual Basic- und C#-Designern für Windows Forms hinzufügen können. Zusätzlich zu den .NET-Komponenten, die in Visual Studio enthalten sind (z.B. die Komponenten <xref:System.Messaging.MessageQueue> und <xref:System.Diagnostics.EventLog>), können Sie eigene Komponenten oder Drittanbieterkomponenten zu dieser Registerkarte hinzufügen.

Öffnen Sie einen Windows Forms-Designer, um diese Registerkarte anzuzeigen. Klicken Sie auf **Ansicht** > **Toolbox**. Wählen Sie in der **Toolbox** die Registerkarte **Komponenten** aus.

## <a name="components"></a>Komponenten

**BackgroundWorker**

Erstellt eine <xref:System.ComponentModel.BackgroundWorker>-Komponenteninstanz, die einen Vorgang auf einem separaten, dedizierten Thread ausführen kann. Weitere Informationen finden Sie unter [BackgroundWorker Component (BackgroundWorker-Komponente)](/dotnet/framework/winforms/controls/backgroundworker-component).

**DirectoryEntry**

Erstellt eine <xref:System.DirectoryServices.DirectoryEntry>-Komponenteninstanz, die einen Knoten oder ein Objekt in der Active Directory-Hierarchie kapselt und für die Interaktion mit Active Directory-Dienstanbietern verwendet werden kann.

**DirectorySearcher**

Erstellt eine <xref:System.DirectoryServices.DirectorySearcher>-Komponenteninstanz, mit der Sie Active Directory-Abfragen durchführen können.

**ErrorProvider**

Erstellt eine <xref:System.Windows.Forms.ErrorProvider>-Komponenteninstanz, die dem Endbenutzer anzeigt, dass für ein Steuerelement auf einem Formular ein Fehler vorliegt. Weitere Informationen finden Sie unter [ErrorProvider Component (ErrorProvider-Komponente)](/dotnet/framework/winforms/controls/errorprovider-component-windows-forms).

**EventLog**

Erstellt eine <xref:System.Diagnostics.EventLog>-Komponenteninstanz, mit der sie mit nativen und benutzerdefinierten Ereignisprotokollen interagieren und unter anderem Ereignisse in ein Protokoll schreiben und Protokolldaten lesen können.

**FileSystemWatcher**

Erstellt eine <xref:System.IO.FileSystemWatcher>-Komponenteninstanz, mit der Sie Verzeichnisse oder Dateien, auf die Sie Zugriff haben, auf Veränderungen überwachen können.

**HelpProvider**

Erstellt eine <xref:System.Windows.Forms.HelpProvider>-Komponenteninstanz, die Popup- oder Onlinehilfe für Steuerelemente bereitstellt. Weitere Informationen finden Sie unter [HelpProvider Component (HelpProvider-Komponente)](/dotnet/framework/winforms/controls/helpprovider-component-windows-forms).

**ImageList**

Erstellt eine <xref:System.Windows.Forms.ImageList>-Komponenteninstanz, die Methoden zur Verwaltung einer Auflistung von <xref:System.Drawing.Image>-Objekten bereitstellt. Weitere Informationen finden Sie unter [ImageList Component (ImageList-Komponente)](/dotnet/framework/winforms/controls/imagelist-component-windows-forms).

**MessageQueue**

Erstellt eine <xref:System.Messaging.MessageQueue>-Komponenteninstanz, mit der Sie mit Meldungswarteschlangen interagieren und unter anderem Nachrichten von Warteschlangen lesen und an diese schreiben, Transaktionen verarbeiten und Verwaltungsaufgaben für die Warteschlange ausführen können.

**PerformanceCounter**

Erstellt eine <xref:System.Diagnostics.PerformanceCounter>-Komponenteninstanz, mit der sie mit Windows-Leistungsindikatoren interagieren und unter anderem neue Kategorien und Instanzen erstellen, Werte von Leistungsindikatoren lesen und Berechnungen zu Indikatorendaten durchführen können.

**Prozess**

Erstellt eine <xref:System.Diagnostics.Process>-Komponenteninstanz, mit der Sie die Daten von Prozessen auf Ihrem System beenden, starten und bearbeiten können.

**SerialPort**

Erstellt eine <xref:System.IO.Ports.SerialPort>-Komponenteninstanz, die synchrone und ereignisgesteuerte E/A-Vorgänge, Zugriff auf Pin- und Unterbrechungszustände sowie Zugriff auf die Treibereigenschaften für den seriellen Anschluss bietet.

**ServiceController**

Erstellt eine <xref:System.ServiceProcess.ServiceController>-Komponenteninstanz, mit der Sie vorhandene Dienste bearbeiten und unter anderem Dienste starten und beenden sowie Befehle an sie senden können.

**Timer**

Erstellt eine <xref:System.Windows.Forms.Timer>-Komponenteninstanz, mit der Sie zeitbasierte Funktionen zu Ihren Windows-basierten Anwendungen hinzufügen können. Weitere Informationen finden Sie unter [Timer Component (Timer-Komponente)](/dotnet/framework/winforms/controls/timer-component-windows-forms).

> [!NOTE]
> Es gibt auch eine systembasierte <xref:System.Timers.Timer>, die Sie zur **Toolbox** hinzufügen können. Diese <xref:System.Timers.Timer> ist für Serveranwendungen optimiert, und die <xref:System.Windows.Forms.Timer> eignet sich am besten für die Verwendung in Windows Forms.

## <a name="see-also"></a>Weitere Informationen

- [Controls to use on Windows Forms (Steuerelemente für Windows Forms)](/dotnet/framework/winforms/controls/controls-to-use-on-windows-forms)
- [Toolboxelemente auswählen, WPF-Komponenten](choose-toolbox-items-wpf-components.md)
- [Werkzeugkasten](../../ide/reference/toolbox.md)
