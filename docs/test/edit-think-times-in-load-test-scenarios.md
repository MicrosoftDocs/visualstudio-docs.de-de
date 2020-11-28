---
title: Reaktionszeit für Auslastungstests
description: Lernen Sie, Reaktionszeiten zu bearbeiten, die zur Simulation des menschlichen Verhaltens verwendet werden, bei dem eine gewisse Zeit zwischen einzelnen Interaktionen mit einer Website vergeht.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, think times
- load tests, adding delays
- load tests, changing think times
ms.assetid: 8e03bee5-ab7b-4b40-9497-9dbe91ccb90e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a1c0c1ef98a77b83c49ca69fd70e38238ed4ded0
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2020
ms.locfileid: "95441299"
---
# <a name="edit-think-times-to-simulate-website-human-interaction-delays-in-load-tests-scenarios"></a>Bearbeiten der Reaktionszeit zum Simulieren menschlicher Interaktionsverzögerungen in Auslastungstestszenarios für Websites

Reaktionszeiten werden zur Simulation des menschlichen Verhaltens verwendet, bei dem eine gewisse Zeit zwischen einzelnen Interaktionen mit einer Website vergeht. Reaktionszeiten treten zwischen den Anforderungen in einem Webleistungstest und zwischen Testiterationen in einem Auslastungstestszenario auf. Die Verwendung von Reaktionszeiten in einem Auslastungstest kann bei der Erzeugung genauerer Auslastungssimulationen nützlich sein. Sie können angeben, ob Reaktionszeiten in Auslastungstests verwendet oder ignoriert werden. Sie können die Verwendung von Reaktionszeiten für Auslastungstests im **Auslastungstest-Editor** einstellen.

Das *Reaktionsprofil* ist eine Einstellung für ein Szenario in einem Auslastungstest. Durch die Einstellung wird festgelegt, ob die in den einzelnen Webleistungstests gespeicherten Reaktionszeiten während des Auslastungstests verwendet werden. Wenn Sie Reaktionszeiten in einigen Webleistungstests verwenden möchten, in anderen jedoch nicht, müssen Sie diese in verschiedenen Szenarien anordnen. Weitere Informationen zu Szenarios finden Sie unter [Bearbeiten von Auslastungstestszenarios](../test/edit-load-test-scenarios.md).

Beim Erstellen des Auslastungstests mit dem **Assistenten für neuen Auslastungstest** legen Sie anfangs fest, ob Reaktionszeiten in Ihren Auslastungstests verwendet werden. Weitere Informationen finden Sie unter [Bearbeiten von Auslastungstestszenarios](../test/edit-load-test-scenarios.md).

Die **Reaktionsprofil**-Optionen werden in der folgenden Liste beschrieben:

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**Deaktiviert**

Reaktionszeiten werden ignoriert. Verwenden Sie diese Einstellung, wenn Sie eine maximale Auslastung und eine hohe Belastung des Webservers simulieren möchten. Sie sollten diese Option nicht verwenden, wenn Sie versuchen, realistischere Benutzerinteraktionen mit einem Webserver zu generieren.

**Ein**

Reaktionszeiten werden exakt gemäß ihrer Aufzeichnung im Webleistungstest verwendet. Es wird simuliert, dass mehrere Benutzer Webleistungstests genau wie aufgezeichnet ausführen. Da bei einem Auslastungstest mehrere Benutzer simuliert werden, könnte die Verwendung derselben Reaktionszeit ein unnatürliches Auslastungsmuster bei den synchronisierten virtuellen Benutzern ergeben.

**Normalverteilung**

Reaktionszeiten werden verwendet, variieren jedoch im Rahmen einer Normalverteilung. Durch die leichte Veränderung der Reaktionszeit bei verschiedenen Anforderungen wird die Simulation virtueller Benutzer realistischer.

> [!NOTE]
> Eine vollständige Liste der Auslastungstest-Szenarioeigenschaften finden Sie unter [Load test scenario properties (Eigenschaften von Auslastungstestszenarios)](../test/load-test-scenario-properties.md).

## <a name="change-the-think-profile"></a>Ändern des Reaktionsprofils

### <a name="to-change-a-think-profile-in-a-load-test-scenario"></a>So ändern Sie ein Reaktionsprofil in einem Auslastungstestszenario

1. Öffnen Sie im Webleistungs- und Auslastungstestprojekt einen Auslastungstest.

2. Klicken Sie im **Auslastungstest-Editor** auf den Szenarioknoten, für den Sie das **Reaktionsprofil** ändern möchten. Das **Reaktionsprofil** wird im Fenster **Eigenschaften** angezeigt. Drücken Sie **F4**, um das Fenster **Eigenschaften** anzuzeigen.

3. Ändern Sie die Eigenschaft **Reaktionsprofil** im Fenster **Eigenschaften**.

4. Nachdem die Änderungen der Eigenschaften abgeschlossen sind, klicken Sie im Menü **Datei** auf **Speichern**. Anschließend können Sie den Auslastungstest mit dem neuen Reaktionsprofil ausführen.

## <a name="see-also"></a>Weitere Informationen

- [Bearbeiten von Auslastungstestszenarios](../test/edit-load-test-scenarios.md)
