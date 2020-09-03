---
title: Anpassen der Art und Weise, wie Visual Studio 2015 Beschriftungen für Daten gebundene Steuerelemente erstellt | Microsoft-Dokumentation
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- Label captions, Data Sources window
- smart captions
- captions, data-bound
- Data Sources Window, label captions
ms.assetid: 6d4d15f8-4d78-42fd-af64-779ae98d62c8
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c0e54f68ab7e34f1cfb6abb228f552cc3792a8b7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "77476920"
---
# <a name="customize-how-visual-studio-creates-captions-for-data-bound-controls"></a>Anpassen der Erstellung von Beschriftungen für datengebundene Steuerelemente durch Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie Elemente aus dem [Datenquellen Fenster](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) auf den Windows Forms-Designer ziehen, wird ein besonderes Augenmerk berücksichtigt: die Spaltennamen in den Beschriftungs Bezeichnungen werden in eine besser lesbare Zeichenfolge umformatiert, wenn zwei oder mehr Wörter gefunden werden, die miteinander verkettet werden sollen. Sie können die Art und Weise anpassen, in der diese Bezeichnungen erstellt werden, indem Sie die Werte " **SmartCaptionExpression**", " **smartcaptionreplace**" und " **SmartCaptionSuffix** " im Registrierungsschlüssel " **HKEY_CURRENT_USER \software\microsoft\visualstudio\10.0\Data Designers** " festlegen.

> [!NOTE]
> Dieser Registrierungsschlüssel ist erst vorhanden, wenn Sie ihn erstellt haben.

 Smarttags werden vom regulären Ausdruck gesteuert, der in den Wert des Werts " **SmartCaptionExpression** " eingegeben wird. Durch Hinzufügen des Registrierungsschlüssels für **Daten-Designer** wird der reguläre Standardausdruck zum Steuern von Beschriftungs Bezeichnungen überschrieben. Weitere Informationen zu regulären Ausdrücken finden Sie unter [Verwenden von regulären Ausdrücken in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

 In der folgenden Tabelle werden die Registrierungs Werte beschrieben, die Beschriftungs Bezeichnungen steuern.

|Registrierungs Element|BESCHREIBUNG|
|-------------------|-----------------|
|**SmartCaptionExpression**|Der reguläre Ausdruck, der zum Abgleichen ihrer Muster verwendet wird.|
|**SmartCaptionReplacement**|Das Format, in dem alle Gruppen angezeigt werden, die in **SmartCaptionExpression**übereinstimmen.|
|**SmartCaptionSuffix**|Eine optionale Zeichenfolge, die an das Ende der Beschriftung angefügt werden soll.|

 In der folgenden Tabelle sind die internen Standardeinstellungen für diese Registrierungs Werte aufgeführt.

|Registrierungs Element|Standardwert|Erklärung|
|-------------------|-------------------|-----------------|
|**SmartCaptionExpression**|( \\ \p{ll}) ( \\ \p{LU}) &#124;_ +|Entspricht einem Kleinbuchstaben, gefolgt von einem Großbuchstaben oder einem Unterstrich.|
|**SmartCaptionReplacement**|$1 $2|$1 stellt alle Zeichen dar, die in den ersten Klammern des Ausdrucks übereinstimmen, und $2 stellt alle Zeichen dar, die in den zweiten Klammern übereinstimmen. Die Ersetzung ist die erste Übereinstimmung, ein Leerzeichen und dann die zweite Entsprechung.|
|**SmartCaptionSuffix**|:|Stellt ein an die zurückgegebene Zeichenfolge angefügtes Zeichen dar. Wenn die Beschriftung beispielsweise ist `Company Name` , wird Sie durch das Suffix `Company Name:`|

> [!CAUTION]
> Sie sollten sehr vorsichtig sein, wenn Sie im Registrierungs-Editor etwas tun. Sichern Sie die Registrierung, bevor Sie Sie bearbeiten. Wenn Sie den Registrierungs-Editor nicht ordnungsgemäß verwenden, können Sie schwerwiegende Probleme verursachen, die möglicherweise eine Neuinstallation des Betriebssystems erforderlich machen. Microsoft garantiert nicht, dass Probleme, die Sie durch die Verwendung des Registrierungs-Editors verursacht haben, nicht ordnungsgemäß aufgelöst werden können. Die Verwendung des Registrierungs-Editors erfolgt auf Ihr eigenes Risiko.

### <a name="to-modify-the-smart-captioning-behavior-of-the-data-sources-window"></a>So ändern Sie das Verhalten von intelligenten Untertiteln im Datenquellen Fenster

1. Öffnen Sie ein Befehlsfenster, indem Sie auf **Start** und dann auf **Ausführen**klicken.

2. Geben `regedit` Sie im Dialogfeld **Ausführen** ein, und klicken Sie auf **OK**.

3. Erweitern Sie den Knoten **HKEY_CURRENT_USER** .

4. Erweitern Sie den Knoten **Software** .

5. Erweitern Sie den Knoten **Microsoft** .

6. Erweitern Sie den Knoten **VisualStudio** .

7. Klicken Sie mit der rechten Maustaste auf den Knoten **10,0** , und erstellen Sie einen neuen **Schlüssel** namens `Data Designers` .

8. Klicken Sie mit der rechten Maustaste auf den Knoten **Daten-Designer** , und erstellen Sie einen neuen **Zeichen folgen Wert** namens `SmartCaptionExpression` .

9. Klicken Sie mit der rechten Maustaste auf den Knoten **Daten-Designer** , und erstellen Sie einen neuen **Zeichen folgen Wert** namens `SmartCaptionReplacement` .

10. Klicken Sie mit der rechten Maustaste auf den Knoten **Daten-Designer** , und erstellen Sie einen neuen **Zeichen folgen Wert** namens `SmartCaptionSuffix` .

11. Klicken Sie mit der rechten Maustaste auf das Element **SmartCaptionExpression** , und wählen Sie **ändern**aus.

12. Geben Sie den regulären Ausdruck ein, der vom **Datenquellen** Fenster verwendet werden soll.

13. Klicken Sie mit der rechten Maustaste auf das Element **smartcaptionreplace** , und wählen Sie **ändern**aus.

14. Geben Sie die Ersetzungs Zeichenfolge ein, die so formatiert ist, wie die im regulären Ausdruck übereinstimmenden Muster angezeigt werden

15. Klicken Sie mit der rechten Maustaste auf das Element **SmartCaptionSuffix** , und wählen Sie **ändern**aus.

16. Geben Sie die Zeichen ein, die am Ende der Beschriftung angezeigt werden sollen.

     Wenn Sie Elemente das nächste Mal aus dem **Datenquellen** Fenster ziehen, werden die Beschriftungs Bezeichnungen mithilfe der neuen Registrierungs Werte erstellt.

### <a name="to-turn-off-the-smart-captioning-feature"></a>So deaktivieren Sie die Funktion "intelligenter Titel"

1. Öffnen Sie ein Befehlsfenster, indem Sie auf **Start** und dann auf **Ausführen**klicken.

2. Geben `regedit` Sie im Dialogfeld **Ausführen** ein, und klicken Sie auf **OK**.

3. Erweitern Sie den Knoten **HKEY_CURRENT_USER** .

4. Erweitern Sie den Knoten **Software** .

5. Erweitern Sie den Knoten **Microsoft** .

6. Erweitern Sie den Knoten **VisualStudio** .

7. Klicken Sie mit der rechten Maustaste auf den Knoten **10,0** , und erstellen Sie einen neuen **Schlüssel** namens `Data Designers` .

8. Klicken Sie mit der rechten Maustaste auf den Knoten **Daten-Designer** , und erstellen Sie einen neuen **Zeichen folgen Wert** namens `SmartCaptionExpression` .

9. Klicken Sie mit der rechten Maustaste auf den Knoten **Daten-Designer** , und erstellen Sie einen neuen **Zeichen folgen Wert** namens `SmartCaptionReplacement` .

10. Klicken Sie mit der rechten Maustaste auf den Knoten **Daten-Designer** , und erstellen Sie einen neuen **Zeichen folgen Wert** namens `SmartCaptionSuffix` .

11. Klicken Sie mit der rechten Maustaste auf das Element **SmartCaptionExpression** , und wählen Sie **ändern**aus.

12. Geben Sie als `(.*)` Wert ein. Dies entspricht der gesamten Zeichenfolge.

13. Klicken Sie mit der rechten Maustaste auf das Element **smartcaptionreplace** , und wählen Sie **ändern**aus.

14. Geben Sie als `$1` Wert ein. Dadurch wird die Zeichenfolge durch den übereinstimmenden Wert ersetzt. dabei handelt es sich um die gesamte Zeichenfolge, sodass Sie unverändert bleibt.

     Wenn Sie Elemente das nächste Mal aus dem **Datenquellen** Fenster ziehen, werden die Beschriftungs Bezeichnungen mit unveränderten Beschriftungen erstellt.

## <a name="see-also"></a>Weitere Informationen
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
