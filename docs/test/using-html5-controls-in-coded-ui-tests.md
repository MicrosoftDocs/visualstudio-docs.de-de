---
title: Verwenden von HTML5-Steuerelementen in Tests der programmierten UI
description: Erfahren Sie mehr über Tests der programmierten UI, die HTML5-Steuerelemente unterstützen, die in Internet Explorer 9 und Internet Explorer 10 enthalten sind.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: d902d31b0d417c32b7b3e1a2067a8bb5bcf77451
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/24/2020
ms.locfileid: "95598379"
---
# <a name="using-html5-controls-in-coded-ui-tests"></a>Verwenden von HTML5-Steuerelementen in Tests der programmierten UI

Bei Tests der programmierten UI werden einige HTML5-Steuerelemente unterstützt, die in Internet Explorer 9 und in Internet Explorer 10 enthalten sind.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Anforderungen**

- Visual Studio Enterprise

> [!WARNING]
> In Versionen vor Internet Explorer 10 konnten Tests der programmierten UI im Vergleich zum Internet Explorer-Prozess mit einer höheren Berechtigungsstufe ausgeführt werden. Beim Ausführen von Tests der programmierten UI in Internet Explorer 10 müssen sowohl der Prozess für Tests der programmierten UI als auch der Internet Explorer-Prozess dieselbe Berechtigungsstufe aufweisen. Dies liegt an sichereren AppContainer-Features in Internet Explorer 10.

> [!WARNING]
> Wenn Sie einen Test der programmierten UI in Internet Explorer 10 erstellen, wird dieser mit Internet Explorer 9 oder Internet Explorer 8 möglicherweise nicht ausgeführt. Der Grund hierfür ist, dass Internet Explorer 10 HTML5-Steuerelemente wie Audio, Video, ProgressBar und Schieberegler enthält. Diese HTML5-Steuerelemente werden von Internet Explorer 9 oder Internet Explorer 8 nicht erkannt. Entsprechend kann der Test der codierten UI unter Verwendung von Internet Explorer 9 einige HTML5-Steuerelemente enthalten, die auch nicht von Internet Explorer 8 erkannt werden.

## <a name="audio-control"></a>Audio-Steuerelement

**Audio-Steuerelement:** Aktionen im HTML5-Audiosteuerelement werden ordnungsgemäß aufgezeichnet und wiedergegeben.

![HTML5-Audiosteuerelement](../test/media/codedui_html5_audio.png)

|Aktion|Aufzeichnung|Generierter Code|
|-|---------------|-|
|**Audiowiedergabe**<br /><br /> Direkt über das Steuerelement oder über das Steuerelement-Kontextmenü.|Audio \<name> ab 00:00:00 wiedergeben|HtmlAudio.Play(TimeSpan)|
|**Einen bestimmten Zeitpunkt in der Audiodatei auswählen**|Audio \<name> bis 00:01:48 suchen|HtmlAudio.Seek(TimeSpan)|
|**Audiodatei anhalten**<br /><br /> Direkt über das Steuerelement oder über das Steuerelement-Kontextmenü.|Audio \<name> bei 00:01:53 anhalten|HtmlAudio.Pause(TimeSpan)|
|**Ton ausschalten**<br /><br /> Direkt über das Steuerelement oder über das Steuerelement-Kontextmenü.|Audio \<name> stummschalten|HtmlAudio.Mute()|
|**Stummschaltung der Audiodatei aufheben**<br /><br /> Direkt über das Steuerelement oder über das Steuerelement-Kontextmenü.|Stummschaltung des Audios \<name> aufheben|HtmlAudio.Unmute()|
|**Ändern der Lautstärke der Audiodatei**|Lautstärke des Audios \<name> auf 79 % festlegen|HtmlAudio.SetVolume(float)|

Unter [HTMLAudioElement](https://developer.mozilla.org/docs/Web/API/HTMLAudioElement) finden Sie eine Liste der Eigenschaften, zu denen Sie eine Assertion hinzufügen können.

**Sucheigenschaften:** Die Sucheigenschaften für `HtmlAudio` sind `Id`, `Name` und `Title`.

**Filtereigenschaften:** Die Filtereigenschaften für `HtmlAudio` sind `Src`, `Class`, `ControlDefinition` und `TagInstance`.

> [!NOTE]
> Die Zeitdauer für das Suchen und Anhalten kann erheblich sein. Während der Wiedergabe wartet der Test der programmierten UI bis zur in `(TimeSpan)` angegebenen Zeit, bevor die Audiodatei angehalten wird. Wenn die angegebene Zeit unter bestimmten Ausnahmefällen verstrichen ist, bevor der Befehl „Pause“ aktiviert wurde, wird eine Ausnahme zurückgegeben.

## <a name="video-control"></a>Videosteuerelement
**Videosteuerelement:** Aktionen im HTML5-Videosteuerelement werden ordnungsgemäß aufgezeichnet und wiedergegeben.

![HTML5-Videosteuerelement](../test/media/codedui_html5_video.png)

|Aktion|Aufzeichnung|Generierter Code|
|-|---------------|-|
|**Videowiedergabe**<br /><br /> Direkt über das Steuerelement oder über das Steuerelement-Kontextmenü.|Video \<name> ab 00:00:00 wiedergeben|HtmlVideo.Play(TimeSpan)|
|**Einen bestimmten Zeitpunkt im Video auswählen**|Video \<name> bis 00:01:48 suchen|HtmlVideo.Seek(TimeSpan)|
|**Video anhalten**<br /><br /> Direkt über das Steuerelement oder über das Steuerelement-Kontextmenü.|Video \<name> bei 00:01:53 anhalten|HtmlVideo.Pause(TimeSpan)|
|**Video stummschalten**<br /><br /> Direkt über das Steuerelement oder über das Steuerelement-Kontextmenü.|Video \<name> stummschalten|HtmlVideo.Mute()|
|**Stummschaltung des Videos aufheben**<br /><br /> Direkt über das Steuerelement oder über das Steuerelement-Kontextmenü.|Stummschaltung des Videos \<name> aufheben|HtmlVideo.Unmute()|
|**Ändern der Lautstärke des Videos**|Lautstärke des Videos \<name> auf 79 % festlegen||

Unter [HTMLVideoElement](https://developer.mozilla.org/docs/Web/HTML/Element/video) finden Sie eine Liste der Eigenschaften, zu denen Sie eine Assertion hinzufügen können.

**Sucheigenschaften:** Die Sucheigenschaften für `HtmlVideo` sind `Id`, `Name` und `Title`.

**Filtereigenschaften:** Die Filtereigenschaften für `HtmlVideo` sind `Src`, `Poster`, `Class`, `ControlDefinition` und `TagInstance`.

> [!NOTE]
> Wenn Sie das Video mithilfe der Bezeichnung „-30s“ oder „+30s“ zurück- bzw. vorspulen, wird dies aggregiert, um nach der entsprechenden Zeit zu suchen.

## <a name="progressbar"></a>ProgressBar
**ProgressBar-Steuerelement:** ProgressBar ist ein Steuerelement ohne Interaktionen. Sie können Assertionen für die `Value`- und `Max`-Eigenschaften dieses Steuerelements hinzufügen. Weitere Informationen finden Sie unter [HTMLProgressElement](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/progress).

![HTML5 ProgressBar-Steuerelement](../test/media/codedui_html5_progressbar.png)

## <a name="see-also"></a>Siehe auch

- [HTML-Elemente](https://developer.mozilla.org/docs/Web/HTML/Element)
- [Verwenden der Benutzeroberflächenautomatisierung zum Testen des Codes](../test/use-ui-automation-to-test-your-code.md)
- [Erstellen von Tests der programmierten UI](../test/use-ui-automation-to-test-your-code.md)
- [Unterstützte Konfigurationen und Plattformen für Tests der programmierten UI und Aktionsaufzeichnungen](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
