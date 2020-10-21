---
title: Konfigurationen und Plattformen für Tests der programmierten UI
ms.date: 10/04/2015
ms.topic: reference
helpviewer_keywords:
- coded UI tests
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 3636f87db5c395f1660d9271d0eed5cacec99161
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/11/2020
ms.locfileid: "90036898"
---
# <a name="supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings"></a>Unterstützte Konfigurationen und Plattformen für Tests der programmierten UI und Aktionsaufzeichnungen

Die unterstützten Konfigurationen und Plattformen für Tests der codierten UI für Visual Studio Enterprise werden in der folgenden Tabelle aufgeführt. Diese Konfigurationen gelten auch für Aktionsaufzeichnungen, die mit [!INCLUDE[MTRlong](../test/includes/mtrlong_md.md)]erstellt wurden.

> [!NOTE]
> Der Prozess für den Test der codierten UI muss über die gleichen Rechte wie die getestete App verfügen.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Voraussetzungen**

- Visual Studio Enterprise

## <a name="supported-configurations"></a>Unterstützte Konfigurationen

| Konfiguration | Unterstützt |
|-| - |
| Betriebssysteme | [!INCLUDE[win7](../debugger/includes/win7_md.md)]<br /><br /> [!INCLUDE[winsvr08_r2](../debugger/includes/winsvr08_r2_md.md)]<br /><br /> [!INCLUDE[win8](../debugger/includes/win8_md.md)]<br /><br /> Windows 10 |
| 32-/64-Bit-Unterstützung | Windows-Betriebssysteme (32-Bit), auf denen [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] (32-Bit) ausführt wird, können 32-Bit-Anwendungen testen.<br /><br /> Windows-Betriebssysteme (64-Bit), auf denen [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] (32-Bit) ausführt wird, können 32-Bit-WOW-Anwendungen mit Benutzeroberflächensynchronisierung testen.<br /><br /> Windows-Betriebssysteme (64-Bit), auf denen [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] (32-Bit) ausgeführt wird, können Windows Forms- und WPF-Anwendungen (64-Bit) ohne Benutzeroberflächensynchronisierung testen. |
| Architektur | x86 und x64 **Hinweis:** Internet Explorer wird im 64-Bit-Modus nur bei Ausführung unter [!INCLUDE[win8](../debugger/includes/win8_md.md)] oder höheren Versionen unterstützt. |
| .NET | .NET 2.0, 3.0, 3.5, 4 und 4.5. **Hinweis:** [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] und Visual Studio setzen .NET 4 voraus. Mit den aufgeführten .NET-Versionen entwickelte Anwendungen werden jedoch unterstützt. |

> [!NOTE]
> Die*Benutzeroberflächensynchronisierung* ist eine Funktion, bei der die Wiedergabe in die Nachrichtenwarteschlange jedes Steuerelements überprüft wird. Wenn ein Steuerelement nicht auf das Ereignis reagierte, das an es gesendet wurde, wird das Ereignis erneut gesendet.

## <a name="platform-support"></a>Plattformunterstützung

| Plattform | Unterstützungsebene |
|-| - |
| Windows Phone-Apps | Nur auf WinRT-XAML basierende Phone-Apps werden unterstützt. |
| UWP-Apps | Es werden nur XAML-basierte UWP-Apps unterstützt. |
| Universelle Windows-Apps | Nur XAML-basierte universelle Windows-Apps für Phone und Desktop werden unterstützt. |
| Edge | Aufzeichnung von Aktionsschritten oder Verwendung des Generators, um Objekteigenschaften anzuzeigen, die nicht unterstützt werden. Tests können im Microsoft Edge-Browser mithilfe von Visual Studio 2015 Update 2 und höheren Versionen und mithilfe der [Erweiterung der programmierten UI für Browsertests](https://marketplace.visualstudio.com/items?itemName=AtinBansal.SeleniumcomponentsforCodedUICrossBrowserTesting) erneut abgespielt werden. |
| Internet Explorer 8<br /><br /> Internet Explorer 9<br /><br /> Internet Explorer 10 **Wichtig:** Internet Explorer 10 wird nur auf dem Desktop unterstützt. <br /><br /> Internet Explorer 11 **Wichtig:** Internet Explorer 11 wird nur auf dem Desktop unterstützt. | Vollständige Unterstützung<br /><br /> -   **Unterstützung für HTML5 in Internet Explorer 9 und Internet Explorer 10:** Tests der codierten UI unterstützen Aufzeichnung, Wiedergabe und Überprüfung der HTML5-Steuerelemente: Audio, Video, ProgressBar und Schieberegler. Weitere Informationen finden Sie unter [Verwenden von HTML5-Steuerelementen in Tests der programmierten UI](../test/using-html5-controls-in-coded-ui-tests.md). **Warnung:** Wenn Sie einen Test der programmierten UI in Internet Explorer 10 erstellen, wird dieser mit Internet Explorer 9 oder Internet Explorer 8 möglicherweise nicht ausgeführt. Der Grund hierfür ist, dass Internet Explorer 10 HTML5-Steuerelemente wie Audio, Video, ProgressBar und Schieberegler enthält. Diese HTML5-Steuerelemente werden von Internet Explorer 9 oder Internet Explorer 8 nicht erkannt. Entsprechend kann der Test der codierten UI unter Verwendung von Internet Explorer 9 einige HTML5-Steuerelemente enthalten, die auch nicht von Internet Explorer 8 erkannt werden.<br />-   **Unterstützung für die Rechtschreibprüfung von Internet Explorer 10:** Internet Explorer 10 enthält Rechtschreibprüfungsfunktionen für alle Textfelder. Dadurch können Sie aus einer Liste vorgeschlagener Korrekturen wählen. Der Test der codierten UI ignoriert Benutzeraktionen wie das Auswählen eines alternativen Rechtschreibvorschlags. Nur der endgültige in das Textfeld eingegebene Text wird aufgezeichnet.<br />     Die folgenden Aktionen werden beim Test der codierten UI aufgezeichnet, bei denen das Steuerelement zur Rechtschreibprüfung verwendet wird: "Zum Wörterbuch hinzufügen", "Kopieren", "Alle auswählen" und "Ignorieren".<br />-   **Unterstützung für Internet Explorer (64-Bit) unter Windows 8:** Zuvor wurden 64-Bit-Versionen von Internet Explorer für Aufzeichnung und Wiedergabe nicht unterstützt. Mit [!INCLUDE[win8](../debugger/includes/win8_md.md)] und [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] können Tests der codierten UI für 64-Bit-Versionen von Internet Explorer ausgeführt werden. **Warnung:** Die 64-Bit-Unterstützung für Internet Explorer gilt nur unter [!INCLUDE[win8](../debugger/includes/win8_md.md)] oder höher.<br />-   **Unterstützung für angeheftete Sites in Internet Explorer 9:** In Internet Explorer 9 wurden angeheftete Sites eingeführt. Mit angehefteten Websites können Sie Ihre Lieblingssites direkt über die Windows-Taskleiste aufrufen, ohne Internet Explorer zuerst öffnen zu müssen. Tests der codierten UI können nun absichtbewusste Aktionen für angeheftete Sites generieren. Weitere Informationen über angeheftete Sites finden Sie unter [Angeheftete Sites](https://support.microsoft.com/hub/4230784/internet-explorer-help).<br />-   **Unterstützung für semantische Tags in Internet Explorer 9:** Mit Internet Explorer 9 wurden die folgenden semantischen Tags eingeführt: section, nav, article, aside, hgroup, header, footer, figure, figcaption und mark. Tests der codierten UI ignorieren all diese semantischen Tags während der Aufzeichnung. Sie können mit dem Test-Generator für codierte UI Assertionen für diese Tags hinzufügen. Mit der Navigationssteuerung im Test-Generator für codierte UI können Sie zu all diesen Elementen navigieren und die zugehörigen Eigenschaften anzeigen.<br />-   **Nahtlose Behandlung von Leerzeichen zwischen Versionen von Internet Explorer:** Bei der Behandlung von Leerzeichen gibt es Unterschiede zwischen Internet Explorer 8, Internet Explorer 9 und Internet Explorer 10. Der Test der codierten UI behandelt diese Unterschiede nahtlos. Daher wird ein Test der codierten UI, der in Internet Explorer 8 erstellt wurde, beispielsweise problemlos in Internet Explorer 9 und Internet Explorer 10 wiedergegeben.<br />-   **Der Infobereich von Internet Explorer wird nun mit dem festgelegten Attribut „Bei Fehler fortsetzen“ aufgezeichnet:** Alle Aktionen im Infobereich von Internet Explorer werden nun mit dem festgelegten Attribut „Bei Fehler fortsetzen“ aufgezeichnet. Wenn der Infobereich während der Wiedergabe nicht angezeigt wird, werden die Aktionen darin ignoriert, und der Test der codierten UI wird mit der nächsten Aktion fortgesetzt. |
| Steuerelemente von Drittanbietern für Windows Forms und WPF | Vollständige Unterstützung<br /><br /> Um Steuerelemente von Drittanbietern in Windows Forms- und WPF-Anwendungen zu aktivieren, müssen Sie Verweise und Code hinzufügen. Weitere Informationen finden Sie unter [Aktivieren von Tests der programmierten UI Ihrer Steuerelemente](../test/enable-coded-ui-testing-of-your-controls.md). |
| Internet Explorer 6<br /><br /> Internet Explorer 7 | Wird nicht unterstützt. |
| Chrome<br /><br /> Firefox | Die Aufzeichnung von Aktionsschritten wird nicht unterstützt. Coded UI-Tests können auf den Browsern Chrome und Firefox mit Visual Studio 2012 Update 4 oder höher wiedergegeben werden. Klicken Sie [hier](using-different-web-browsers-with-coded-ui-tests.md) , um weitere Informationen zu erhalten. |
| Opera<br /><br /> Safari | Wird nicht unterstützt. |
| Silverlight | Wird nicht unterstützt.<br /><br /> Für Visual Studo 2013 können Sie jedoch das [Microsoft Visual Studio 2013 Coded UI Test Plugin for Silverlight](https://marketplace.visualstudio.com/items?itemName=PrachiBoraMSFT.MicrosoftVisualStudio2013CodedUITestPluginforSilve) aus der Visual Studio Gallery herunterladen. |
| Flash/Java | Wird nicht unterstützt. |
| Windows Forms 2.0 und höher | Vollständige Unterstützung **Hinweis:** NetFx-Steuerelemente werden vollständig unterstützt, dies gilt jedoch nicht für alle Steuerelemente von Drittanbietern. |
| WPF 3.5 und höher | Vollständige Unterstützung<br /><br /> **Hinweis** NetFx-Steuerelemente werden vollständig unterstützt, dies gilt jedoch nicht für alle Steuerelemente von Drittanbietern. |
| Windows Win32 | Funktioniert möglicherweise mit einigen bekannten Problemen, wird jedoch nicht offiziell unterstützt. |
| MFC | Teilweise unterstützt. Unter [UITest Framework – MFC support in VS 2010 (UITest Framework – MFC-Unterstützung in VS 2010)](/archive/blogs/vstsqualitytools/uitest-framework-mfc-support-in-vs-2010) finden Sie nähere Informationen zu unterstützten Funktionen. |
| SharePoint | Vollständige Unterstützung |
| Office-Clientanwendungen | Wird nicht unterstützt. |
| Dynamics CRM-Webclient | Vollständige Unterstützung |
| Dynamics (Ax) 2012-Client | Aktionsaufzeichnung und -wiedergabe werden teilweise unterstützt. Unter [Visual Studio 10 Coded UI / Action Recordings support for Microsoft Dynamics (Visual Studio 10 – programmierte UI / Unterstützung von Aktionsaufzeichnungen für Microsoft Dynamics)](/archive/blogs/dave_froslie/visual-studio-10-coded-ui-action-recordings-support-for-microsoft-dynamics-ax-2012) finden Sie weitere Informationen zu unterstützten Funktionen. |
| SAP | Wird nicht unterstützt. |
| Citrix/Terminaldienste | Das Aufzeichnen von Aktionen auf einem Terminalserver wird nicht empfohlen. Die Aufzeichnung unterstützt nicht, dass mehrere Instanzen gleichzeitig ausgeführt werden. |
| PowerBuilder | Teilweise unterstützt.<br /><br /> Die Unterstützung erfolgt in dem Umfang, in dem der Zugang zu PowerBuilder-Steuerelementen ermöglicht wird. |

Informationen zum Erstellen von Erweiterungen zur Unterstützung anderer Plattformen finden Sie unter [Aktivieren von Tests der programmierten UI Ihrer Steuerelemente](../test/enable-coded-ui-testing-of-your-controls.md) und [Erweitern von Tests der programmierten UI und Aktionsaufzeichnungen](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md).

## <a name="see-also"></a>Weitere Informationen

- [Verwenden der Benutzeroberflächenautomatisierung zum Testen des Codes](../test/use-ui-automation-to-test-your-code.md)