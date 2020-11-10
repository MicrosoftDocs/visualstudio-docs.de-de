---
title: Anpassen von Beschriftungen für Daten gebundene Steuerelemente
description: Passen Sie an, wie Visual Studio Beschriftungen für Daten gebundene Steuerelemente erstellt. Ändern Sie das Verhalten von intelligenten Untertiteln im Datenquellen Fenster. Deaktivieren Sie den intelligenten Titel.
ms.custom: SEO-VS-2020
ms.date: 11/03/2017
ms.topic: how-to
helpviewer_keywords:
- Label captions, Data Sources window
- smart captions
- captions, data-bound
- Data Sources Window, label captions
ms.assetid: 6d4d15f8-4d78-42fd-af64-779ae98d62c8
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 65c0f1146549dfbee6f84fab06be12053b174aeb
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94436627"
---
# <a name="customize-how-visual-studio-creates-captions-for-data-bound-controls"></a>Anpassen der Erstellung von Beschriftungen für datengebundene Steuerelemente durch Visual Studio

Wenn Sie Elemente aus dem [Datenquellen Fenster](add-new-data-sources.md#data-sources-window) auf einen Designer ziehen, wird ein besonderes Augenmerk berücksichtigt: die Spaltennamen in den Beschriftungs Bezeichnungen werden in eine besser lesbare Zeichenfolge umformatiert, wenn zwei oder mehr Wörter gefunden werden, die miteinander verkettet werden sollen.

::: moniker range="vs-2017"

Sie können die Art und Weise anpassen, in der diese Bezeichnungen erstellt werden, indem Sie die Werte **SmartCaptionExpression** , **smartcaptionreplace** und **SmartCaptionSuffix** im Registrierungsschlüssel **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Data Designers** festlegen.

::: moniker-end

::: moniker range=">=vs-2019"

Sie können die Art und Weise anpassen, in der diese Bezeichnungen erstellt werden, indem Sie die Werte **SmartCaptionExpression** , **smartcaptionreplace** und **SmartCaptionSuffix** im Registrierungsschlüssel **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\16.0\Data Designers** festlegen.

::: moniker-end

> [!NOTE]
> Dieser Registrierungsschlüssel ist erst vorhanden, wenn Sie ihn erstellt haben.

Smarttags werden vom regulären Ausdruck gesteuert, der in den Wert des Werts " **SmartCaptionExpression** " eingegeben wird. Durch Hinzufügen des Registrierungsschlüssels für **Daten-Designer** wird der reguläre Standardausdruck zum Steuern von Beschriftungs Bezeichnungen überschrieben. Weitere Informationen zu regulären Ausdrücken finden Sie unter [Verwenden von regulären Ausdrücken in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

In der folgenden Tabelle werden die Registrierungs Werte beschrieben, die Beschriftungs Bezeichnungen steuern.

|Registrierungs Element|BESCHREIBUNG|
|-------------------|-----------------|
|**SmartCaptionExpression**|Der reguläre Ausdruck, den Sie verwenden, um die Muster abzugleichen.|
|**SmartCaptionReplacement**|Das Format, in dem alle Gruppen angezeigt werden, die in **SmartCaptionExpression** übereinstimmen.|
|**SmartCaptionSuffix**|Eine optionale Zeichenfolge, die an das Ende der Beschriftung angefügt werden soll.|

In der folgenden Tabelle sind die internen Standardeinstellungen für diese Registrierungs Werte aufgeführt.

|Registrierungs Element|Standardwert|Erklärung|
|-------------------|-------------------|-----------------|
|**SmartCaptionExpression**|**( \\ \p{ll}) ( \\ \p{LU}) &#124;_ +**|Entspricht einem Kleinbuchstaben, gefolgt von einem Großbuchstaben oder einem Unterstrich.|
|**SmartCaptionReplacement**|**$1 $2**|**$1** stellt alle Zeichen dar, die in den ersten Klammern des Ausdrucks übereinstimmen, und **$2** stellt alle Zeichen dar, die in den zweiten Klammern übereinstimmen. Die Ersetzung ist die erste Übereinstimmung, ein Leerzeichen und dann die zweite Entsprechung.|
|**SmartCaptionSuffix**|**:**|Stellt ein an die zurückgegebene Zeichenfolge angefügtes Zeichen dar. Wenn die Beschriftung beispielsweise ist `Company Name` , wird Sie durch das Suffix `Company Name:`|

> [!CAUTION]
> Gehen Sie sehr vorsichtig vor, wenn Sie im Registrierungs-Editor etwas tun. Sichern Sie die Registrierung, bevor Sie Sie bearbeiten. Wenn Sie den Registrierungs-Editor nicht ordnungsgemäß verwenden, können Sie schwerwiegende Probleme verursachen, die möglicherweise eine Neuinstallation des Betriebssystems erforderlich machen. Microsoft garantiert nicht, dass Probleme, die Sie durch die Verwendung des Registrierungs-Editors verursacht haben, nicht ordnungsgemäß aufgelöst werden können. Die Verwendung des Registrierungs-Editors erfolgt auf Ihr eigenes Risiko.
>
> Informationen zum Sichern, bearbeiten und Wiederherstellen der Registrierung finden Sie unter [Windows-Registrierungsinformationen für fortgeschrittene Benutzer](https://support.microsoft.com/help/256986/windows-registry-information-for-advanced-users).

## <a name="modify-the-smart-captioning-behavior-of-the-data-sources-window"></a>Ändern des intelligenten Beschriftungs Verhaltens des Datenquellen Fensters

1. Öffnen Sie ein Befehlsfenster, indem Sie auf **Start** und dann auf **Ausführen** klicken.

2. Geben `regedit` Sie im Dialogfeld **Ausführen** ein, und klicken Sie auf **OK**.

3. Erweitern Sie den Knoten **HKEY_CURRENT_USER**  >  **Software**  >  **Microsoft**  >  **VisualStudio** .

::: moniker range="vs-2017"

4. Klicken Sie mit der rechten Maustaste auf den Knoten **15,0** , und erstellen Sie einen neuen **Schlüssel** namens `Data Designers` .

::: moniker-end

::: moniker range=">=vs-2019"

4. Klicken Sie mit der rechten Maustaste auf den Knoten **16,0** , und erstellen Sie einen neuen **Schlüssel** namens `Data Designers` .

::: moniker-end

5. Klicken Sie mit der rechten Maustaste auf den Knoten **Daten-Designer** , und erstellen Sie drei neue Zeichen folgen Werte:

    - `SmartCaptionExpression`
    - `SmartCaptionReplacement`
    - `SmartCaptionSuffix`

6. Klicken Sie mit der rechten Maustaste auf den Wert **SmartCaptionExpression** , und wählen Sie **ändern** aus.

7. Geben Sie den regulären Ausdruck ein, der vom **Datenquellen** Fenster verwendet werden soll.

8. Klicken Sie mit der rechten Maustaste auf den Wert **smartcaptionreplace** , und wählen Sie **ändern** aus.

9. Geben Sie die Ersetzungs Zeichenfolge ein, die so formatiert ist, wie die im regulären Ausdruck übereinstimmenden Muster angezeigt werden

10. Klicken Sie mit der rechten Maustaste auf den Wert **SmartCaptionSuffix** , und wählen Sie **ändern** aus.

11. Geben Sie die Zeichen ein, die am Ende der Beschriftung angezeigt werden sollen.

    Wenn Sie Elemente das nächste Mal aus dem **Datenquellen** Fenster ziehen, werden die Beschriftungs Bezeichnungen mithilfe der neuen Registrierungs Werte erstellt.

## <a name="turn-off-the-smart-captioning-feature"></a>Deaktivieren Sie die Funktion zum Übertragen von intelligenten Titeln.

1. Öffnen Sie ein Befehlsfenster, indem Sie auf **Start** und dann auf **Ausführen** klicken.

2. Geben `regedit` Sie im Dialogfeld **Ausführen** ein, und klicken Sie auf **OK**.

3. Erweitern Sie den Knoten **HKEY_CURRENT_USER**  >  **Software**  >  **Microsoft**  >  **VisualStudio** .

::: moniker range="vs-2017"

4. Klicken Sie mit der rechten Maustaste auf den Knoten **15,0** , und erstellen Sie einen neuen **Schlüssel** namens `Data Designers` .

::: moniker-end

::: moniker range=">=vs-2019"

4. Klicken Sie mit der rechten Maustaste auf den Knoten **16,0** , und erstellen Sie einen neuen **Schlüssel** namens `Data Designers` .

::: moniker-end

5. Klicken Sie mit der rechten Maustaste auf den Knoten **Daten-Designer** , und erstellen Sie drei neue Zeichen folgen Werte:

    - `SmartCaptionExpression`
    - `SmartCaptionReplacement`
    - `SmartCaptionSuffix`

6. Klicken Sie mit der rechten Maustaste auf das Element **SmartCaptionExpression** , und wählen Sie **ändern** aus.

7. Geben Sie als `(.*)` Wert ein. Dies entspricht der gesamten Zeichenfolge.

8. Klicken Sie mit der rechten Maustaste auf das Element **smartcaptionreplace** , und wählen Sie **ändern** aus.

9. Geben Sie als `$1` Wert ein. Dadurch wird die Zeichenfolge durch den übereinstimmenden Wert ersetzt. dabei handelt es sich um die gesamte Zeichenfolge, sodass Sie unverändert bleibt.

    Wenn Sie Elemente das nächste Mal aus dem **Datenquellen** Fenster ziehen, werden die Beschriftungs Bezeichnungen mit unveränderten Beschriftungen erstellt.

## <a name="see-also"></a>Siehe auch

- [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
