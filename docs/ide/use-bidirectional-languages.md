---
title: Unterstützung für Arabisch und Hebräisch
description: Hier erfahren Sie, wie Sie arabischen und hebräischen Text anzeigen und bidirektionalen Text für Objektnamen und Werte eingeben können.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Hebrew character display [Visual Studio]
- bidirectional language support
- Arabic, creating applications
ms.assetid: b56f9795-ed8d-4452-9d49-8ca0b0145d86
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a16aa4d445878ac8d357fa551e46552a1465bfe1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971348"
---
# <a name="support-for-bidirectional-languages-in-visual-studio"></a>Unterstützung für bidirektionale Sprachen in Visual Studio

Visual Studio kann arabischen und hebräischen Text korrekt anzeigen und ermöglicht die Eingabe von bidirektionalem Text für Objektnamen und Werte.

> [!NOTE]
> Wenn Sie bidirektionale Sprachen anzeigen und eingeben möchten, müssen Sie mit einer Windows-Version arbeiten, in der die entsprechende Sprache konfiguriert ist. Entweder sollten Sie also eine englischsprachige Windows-Version und das entsprechende Sprachpaket installiert haben, oder Sie verwenden die entsprechende lokalisierte Windows-Version.

## <a name="fully-supported-features"></a>Vollständig unterstützte Funktionen

Zur Entwurfszeit können Sie in Visual Studio beim Eingeben von Text, Benennen von Objekten sowie beim Speichern und Öffnen von Dateien bidirektionale Sprachen verwenden.

### <a name="text-entry"></a>Texteintrag

Visual Studio unterstützt Unicode. Wenn in Ihrem System also das entsprechende Gebietsschema und die entsprechende Eingabesprache eingestellt sind, können Sie Text auf Arabisch oder Hebräisch eingeben. (Ebenso werden auch Kashida und Diakritika unterstützt.)

### <a name="arabic-or-hebrew-object-names"></a>Arabische oder hebräische Objektnamen

Mithilfe von bidirektionalen Sprachen können Sie unter anderem Projektmappen, Projekten, Dateien und Ordern Namen zuweisen. Im Code können Sie bidirektionale Sprachen zum Benennen von Variablen, Klassen, Objekten, Attributen, Metadaten und anderen Elementen einsetzen. Wenn Sie mit Arabisch arbeiten, können Sie alle arabischen Zeichen verwenden, einschließlich Kashida und Diakritika.

Folgende Elemente können auf Arabisch oder Hebräisch benannt werden und werden von Visual Studio korrekt gehandhabt:

- Projektmappen-, Projekt- und Dateinamen, einschließlich aller dem Projektpfad hinzugefügten Ordner.

   Die Namen der Projektmappen und Elemente werden dann im **Projektmappen-Explorer** korrekt angezeigt.

- Dateiinhalt.

   Sie können mit Unicode codierte Dateien oder Dateien mit einer ausgewählten Codepage öffnen und speichern.

- Datenelemente.

   Der **Server-Explorer** zeigt diese Elemente korrekt an, und Sie können sie bearbeiten.

- In die Windows-Zwischenablage kopierte Elemente.

- Attribute und Metadaten.

- Eigenschaftswerte

   Sie können im Fenster **Eigenschaften** arabischen oder hebräischen Text eingeben. In diesem Fenster können Sie mit den üblichen Windows-Tastenkombinationen zwischen der Leserichtung von rechts nach links und der Leserichtung von links nach rechts wechseln (**STRG**+**RECHTE UMSCHALTTASTE** für von rechts nach links bzw. **STRG**+**LINKE UMSCHALTTASTE** für von links nach rechts).

- Code und normaler Text.

   Im Code-Editor können Sie mithilfe von Arabisch oder Hebräisch Klassen, Funktionen, Variablen, Eigenschaften, Zeichenfolgenliterale, Attribute usw. benennen. Allerdings unterstützt der Editor keine Lesefolge von rechts nach links; der Text beginnt immer am linken Rand.

   > [!TIP]
   > Es wird empfohlen, Zeichenfolgenliterale in Ressourcendateien abzulegen und sie nicht fest in Programmen zu codieren. Weitere Informationen finden Sie unter [Ressourcen in Desktop-Apps](/dotnet/framework/resources/index).

   > [!NOTE]
   > Die Verweise auf die benannten Objekte in Arabisch und Hebräisch müssen konsistent sein. Wenn Sie z.B. bei der Benennung einer arabischen Variablen Kashida verwenden, müssen Sie dies auch tun, wenn Sie auf diese Variable verweisen, sonst werden Fehler verursacht.

- Codekommentare. Sie können Kommentare in Arabisch oder Hebräisch erstellen. Sie können diese Sprachen auch im Kommentarerstellungstool verwenden.

### <a name="file-encoding"></a>Dateicodierung

Sie können Dateien mit sprachspezifischer oder Unicode-Codierung speichern und öffnen. Weitere Informationen finden Sie unter [Vorgehensweise: Speichern und Öffnen von Dateien mit Codierung](../ide/how-to-save-and-open-files-with-encoding.md).

## <a name="right-to-left-reading-order"></a>Leserichtung von rechts nach links

Visual Studio bietet eingeschränkte Unterstützung für die Leserichtung von rechts nach links. Die Steuerelemente für die Texteingabe von Visual Studio verwenden standardmäßig die Leserichtung von links nach rechts. Meist können Sie die Lesefolge mit Windows-Standardfunktionen ändern. So können Sie z.B. mit **STRG**+**RECHTE UMSCHALTTASTE** das **Eigenschaftenfenster** umschalten, sodass für die Eigenschaftswerte die Leserichtung von rechts nach links unterstützt wird.

Die Leserichtung von rechts nach links wird an folgenden Stellen in Visual Studio nicht unterstützt:

- Kontrollkästchen, Dropdownlisten und andere Steuerelemente verwenden in Visual Studio immer die Lesefolge von links nach rechts.

- Der Code-Editor (und der Text-Editor) unterstützen die Lesefolge von rechts nach links nicht. Sie können zwar Text in einer bidirektionalen Sprache eingeben, doch die Lesefolge bleibt stets von links nach rechts.

## <a name="see-also"></a>Siehe auch

- [Entwickeln von globalisierten und lokalisierten Apps](globalizing-and-localizing-applications.md)
