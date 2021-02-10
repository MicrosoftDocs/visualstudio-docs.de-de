---
title: 'Vorgehensweise: Erstellen eines Atom-Feeds für einen privaten Katalog | Microsoft-Dokumentation'
description: Sie können einen Atom (RSS)-Feed an einem Intranetspeicherort erstellen, der Erweiterungen enthält, und den Feed zu Erweiterungen und Updates als privaten Katalog hinzufügen.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Atom feed, VSIX private galleries
- VSIX private galleries, Atom feed
ms.assetid: 5897f538-9c41-486f-97d9-a1976d20d9fd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 81167b1e2e9f7959398b30b89796913520c48fac
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967448"
---
# <a name="how-to-create-an-atom-feed-for-a-private-gallery"></a>Vorgehensweise: Erstellen eines Atom-Feeds für einen privaten Katalog
Sie können einen Atom (RSS)-Feed an einem Intranetspeicherort erstellen, der Erweiterungen enthält, und den Feed zu **Erweiterungen und Updates** als privaten Katalog hinzufügen. Weitere Informationen finden Sie unter [Private Kataloge](../extensibility/private-galleries.md).

## <a name="create-an-atom-feed"></a>Erstellen eines Atom-Feeds
 Um einen Atom-Feed als privaten Katalog zu erstellen, erfassen Sie zunächst die Erweiterungen (*VSIX* -Dateien) in einem Ordner. Wenn Sie möchten, können Sie Sie in Unterordnern organisieren. Außerdem benötigen Sie die folgenden Ressourcen:

- Eine *atom.xml* Datei, die die Erweiterungen als private Galerie verfügbar macht. Informationen dazu, wie Sie die *atom.xml* Datei mit **Erweiterungen und Updates** verbinden, finden Sie unter [private Galerien](../extensibility/private-galleries.md).

- Ein Ordner, der alle Bilddateien enthält, die aus den Erweiterungen extrahiert wurden (z. b. Bildschirmaufnahmen). Die *atom.xml* Datei enthält relative Links zu diesen Bildern, sodass Sie in **Erweiterungen und Updates** verfügbar sind.

  Nehmen Sie beispielsweise an, dass Sie die folgenden beiden Erweiterungen in einem Ordner gesammelt haben:

- *Template_Wizard_239. vsix*, eine leere VSIX-Projektvorlage.

- *Selectionhighlight. vsix*, bei dem es sich um ein Tool zum Hervorheben aller Instanzen eines ausgewählten Worts handelt.

  Der Inhalt der *atom.xml* Datei ähnelt dem folgenden Beispiel:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<feed xmlns="http://www.w3.org/2005/Atom">
  <title type="text" />
  <id>uuid:bcecded5-97c8-4d24-96f1-7d9e16652433;id=1</id>
  <updated>2011-04-14T21:25:48Z</updated>
  <entry>
    <id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</id>
    <title type="text">Highlight all occurrences of selected word</title>
    <summary type="text">This extends the editor to highlight ....</summary>
    <published>2011-04-14T14:24:51-07:00</published>
    <updated>2011-04-14T14:24:22-07:00</updated>
    <author>
      <name>Microsoft</name>
    </author>
    <link rel="icon" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_Icon_SelectionHighlightIcon.jpg" />
    <link rel="previewimage" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_PreviewImage_SelectionHighlight.jpg" />
    <content type="application/octet-stream" src="SelectionHighlight.vsix" />
    <Vsix xmlns="http://schemas.microsoft.com/developer/vsx-syndication-schema/2010" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
      <Id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</Id>
      <Version>1.31</Version>
      <References />
      <Rating xsi:nil="true" />
      <RatingCount xsi:nil="true" />
      <DownloadCount xsi:nil="true" />
    </Vsix>
  </entry>
  <entry>
    <id>Template_Wizard_239.Microsoft.3b38a7e3-5cbc-4389-a92a-d82tyc2ed592</id>
    ...
  </entry>
</feed>
```

 Beachten Sie, dass sich die beiden Linktags auf Screenshots im generierten Ordner von Images beziehen.

## <a name="see-also"></a>Weitere Informationen
- [Private Kataloge](../extensibility/private-galleries.md)
