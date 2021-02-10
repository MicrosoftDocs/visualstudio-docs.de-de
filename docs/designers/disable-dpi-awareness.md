---
title: Deaktivieren der DPI-Fähigkeit in Visual Studio
description: Erläutert die Einschränkungen von Windows Forms-Designer für HDPI-Monitore und die Vorgehensweise beim Ausführen von Visual Studio als Prozess ohne DPI-Fähigkeit.
ms.date: 09/28/2020
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.topic: conceptual
ms.openlocfilehash: f63d831127951815f28955e72ae29b1a4d7f5a3e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917090"
---
# <a name="disable-dpi-awareness-in-visual-studio"></a>Deaktivieren der DPI-Fähigkeit in Visual Studio

Visual Studio ist eine DPI-fähige Anwendung (Dots per Inch), d.h. die Anzeige wird automatisch skaliert. Wenn eine Anwendung angibt, dass sie nicht DPI-fähig ist, skaliert das Betriebssystem die Anwendung als Bitmap. Dieses Verhalten wird auch als DPI-Virtualisierung bezeichnet. Die Anwendung geht immer noch davon aus, dass sie mit 100 % Skalierung oder 96 DPI ausgeführt wird.

In diesem Artikel werden die Einschränkungen von Windows Forms-Designer für HDPI-Monitore und die Vorgehensweise beim Ausführen von Visual Studio als Prozess ohne DPI-Fähigkeit erläutert.

## <a name="windows-forms-designer-on-hdpi-monitors"></a>Windows Forms-Designer auf HDPI-Monitoren

Der **Windows Forms-Designer** in Visual Studio verfügt nicht über Skalierungsunterstützung. Dies verursacht Anzeigeprobleme, wenn Sie einige Formulare im **Windows Forms-Designer** auf HDPI-Monitoren (High Dots per Inch) öffnen. Beispielsweise können sich Steuerelemente wie in der folgenden Abbildung gezeigt überlappen:

![Windows Forms-Designer auf HDPI-Monitor](./media/win-forms-designer-hdpi.png)

Wenn Sie ein Formular im **Windows Forms-Designer** in Visual Studio auf einem HDPI-Monitor öffnen, zeigt Visual Studio eine gelbe Informationsleiste am oberen Rand des Designers an:

![Informationsleiste in Visual Studio für den Neustart im nicht DPI-fähigen Modus](./media/scaling-gold-bar.png)

Die folgende Meldung wird angezeigt: **Die Skalierung für Ihre Hauptanzeige wurde auf 200 % (192 DPI) festgelegt. Dies kann zu Renderingproblemen im Designer-Fenster führen.**

> [!NOTE]
> Diese Informationsleiste wurde in Visual Studio 2017 (Version 15.8) eingeführt.

Wenn Sie nicht im Designer arbeiten und das Layout des Formulars nicht anpassen müssen, können Sie die Informationsleiste ignorieren und Ihre Arbeit im Code-Editor oder in anderen Designer-Typen fortsetzen. (Sie können auch [Benachrichtigungen deaktivieren](#disable-notifications), sodass die Informationsleiste nicht mehr angezeigt wird.) Nur der **Windows Forms-Designer** ist betroffen. Wenn Sie im **Windows Forms-Designer** arbeiten müssen, hilft Ihnen der nächste Abschnitt beim [Beheben des Problems](#to-resolve-the-display-problem).

## <a name="to-resolve-the-display-problem"></a>So beheben Sie das Anzeigeproblem

Es gibt drei Möglichkeiten, das Anzeigeproblem zu beheben:

- [Neustarten von Visual Studio als nicht DPI-fähigen Prozess](#restart-visual-studio-as-a-dpi-unaware-process)
- [Hinzufügen eines Registrierungseintrags](#add-a-registry-entry)
- [Festlegen der Skalierungseinstellung für die Anzeige auf 100 %](#set-your-display-scaling-setting-to-100)

> [!TIP]
> Wenn Sie die Einstellungen lieber über die Befehlszeile verwalten, akzeptiert [`devenv.exe`](../ide/reference/devenv-command-line-switches.md) den Befehlszeilenparameter `/noscale` für die Ausführung im Modus mit 100 % Skalierung.

### <a name="restart-visual-studio-as-a-dpi-unaware-process"></a>Neustarten von Visual Studio als nicht DPI-fähigen Prozess

Sie können Visual Studio als einen nicht DPI-fähigen Prozess neu starten, indem Sie diese Option auf der gelben Informationsleiste auswählen. Dies ist die bevorzugte Methode, um das Problem zu beheben.

Wenn Visual Studio als ein nicht DPI-fähiger Prozess ausgeführt wird, werden die Designer-Layoutprobleme behoben, aber Schriftarten werden möglicherweise unscharf angezeigt. Visual Studio zeigt eine andere gelbe Informationsmeldung an, wenn die Ausführung als nicht DPI-fähiger Prozess erfolgt: **Visual Studio wird als nicht DPI-fähiger Prozess ausgeführt. WPF- und XAML-Designer werden möglicherweise nicht ordnungsgemäß angezeigt.** Die Informationsleiste bietet auch eine Option zum **Neustarten von Visual Studio als DPI-fähiger Prozess**.

> [!NOTE]
> - Wenn Sie Toolfenster in Visual Studio nicht angedockt hatten, als Sie die Option zum Neustart als nicht DPI-fähiger Prozess ausgewählt haben, kann sich die Position dieser Toolfenster ändern.
> - Wenn Sie das Visual Basic-Standardprofil verwenden oder Sie die Option **Neue Projekte beim Erstellen speichern** unter **Extras** > **Optionen** > **Projekte und Projektmappen** deaktiviert haben, kann Visual Studio Ihr Projekt nicht erneut öffnen, wenn die Anwendung als nicht DPI-fähiger Prozess neu gestartet wird. Allerdings können Sie das Projekt öffnen, indem Sie es unter **Datei** > **Zuletzt verwendete Projekte und Projektmappen** auswählen.

Es ist wichtig, Visual Studio als DPI-fähigen Prozess neu zu starten, wenn Sie die Arbeit im **Windows Forms-Designer** abgeschlossen haben. Wenn die Ausführung als nicht DPI-fähiger Prozess erfolgt, können Schriftarten verschwommen aussehen, und es werden möglicherweise Probleme in anderen Designern angezeigt, z.B. im **XAML-Designer**. Wenn Sie Visual Studio schließen und erneut öffnen, wenn die Anwendung im nicht DPI-fähigen Modus ausgeführt wird, wird Visual Studio erneut DPI-fähig. Sie können auch die Option **Neustarten von Visual Studio als DPI-fähiger Prozess** in der Informationsleiste auswählen.

### <a name="add-a-registry-entry"></a>Hinzufügen eines Registrierungseintrags

Sie können Visual Studio als nicht DPI-fähig markieren, indem Sie die Registrierung ändern. Öffnen Sie den **Registrierungs-Editor**, und fügen Sie einen Eintrag zum Unterschlüssel **HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Layers** hinzu:

**Eintrag**: Abhängig davon, ob Sie Visual Studio 2017 oder 2019 verwenden, verwenden Sie einen der folgenden Werte:

- C:\Programme (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE\devenv.exe
- C:\Programme (x86)\Microsoft Visual Studio\2019\Community\Common7\IDE\devenv.exe

> [!NOTE]
> Wenn Sie die Professional oder Enterprise Edition von Visual Studio verwenden, ersetzen Sie **Community** im Eintrag durch **Professional** oder  **Enterprise**. Ersetzen Sie außerdem den Laufwerkbuchstaben, wenn erforderlich.

**Typ**: REG_SZ

**Wert**: DPIUNAWARE

> [!NOTE]
> Visual Studio verbleibt im nicht DPI-fähigen Modus, bis Sie den Registrierungseintrag entfernen.

### <a name="set-your-display-scaling-setting-to-100"></a>Festlegen der Skalierungseinstellung für die Anzeige auf 100 %

Um die Skalierungseinstellung für die Anzeige in Windows 10 auf 100 % festzulegen, geben Sie **Anzeigeeinstellungen** in das Suchfeld der Taskleiste ein, und wählen Sie dann **Anzeigeeinstellungen ändern** aus. Legen Sie im Fenster **Einstellungen** die Option **Größe von Text, Apps und anderen Elementen ändern** auf **100 %** fest.

Das Festlegen der Skalierung der Anzeige auf 100 % ist möglicherweise nicht wünschenswert, da die Benutzeroberfläche zu klein werden und damit die die Verwendbarkeit einschränken kann.

## <a name="disable-notifications"></a>Deaktivieren von Benachrichtigungen

Sie können auswählen, dass Sie nicht über Probleme mit der DPI-Skalierung in Visual Studio benachrichtigt werden möchten. Möglicherweise möchten Sie Benachrichtigungen deaktivieren, wenn Sie z.B. nicht im Designer arbeiten.

Um Benachrichtigungen zu deaktivieren, wählen Sie **Extras** > **Optionen** aus, um das Dialogfeld **Optionen** zu öffnen. Wählen Sie dann **Windows Forms-Designer** > **Allgemein** aus, und legen Sie **DPI-Skalierungsbenachrichtigungen** auf **False** fest.

![Option „DPI-Skalierungsbenachrichtigungen“ in Visual Studio](./media/notifications-option.png)

Wenn Sie die Skalierungsbenachrichtigungen später erneut aktivieren möchten, legen Sie die Eigenschaft auf **True** fest.

## <a name="troubleshoot"></a>Problembehandlung

Wenn der Übergang der DPI-Fähigkeit in Visual Studio nicht wie erwartet funktioniert, überprüfen Sie, ob Sie den Wert `dpiAwareness` im Unterschlüssel **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image File Execution Options\devenv.exe** des Registrierungs-Editors verwenden. Löschen Sie den Wert, wenn dieser vorhanden ist.

## <a name="see-also"></a>Siehe auch

- [Automatische Skalierung in Windows Forms](/dotnet/framework/winforms/automatic-scaling-in-windows-forms)
