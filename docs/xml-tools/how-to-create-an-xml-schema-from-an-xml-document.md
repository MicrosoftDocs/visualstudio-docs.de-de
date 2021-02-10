---
title: Erstellen eines XML-Schemas
description: In diesem Artikel erfahren Sie, wie Sie den XML-Editor in Visual Studio verwenden, um eine XSD-Schema (XML-Schemadefinitionssprache) aus einem XML-Dokument zu erstellen.
ms.custom: SEO-VS-2020
ms.date: 03/05/2019
ms.topic: how-to
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e33a4add7ebc6a3e323331731f3183d7a0dce26f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970282"
---
# <a name="how-to-create-an-xml-schema-from-an-xml-document"></a>Vorgehensweise: Erstellen eines XML-Schemas aus einem XML-Dokument

Der XML-Editor ermöglicht Ihnen, ein XSD-Schema (XML Schema Definition Language) aus einem XML-Dokument zu erstellen. Die XML-Datei bestimmt wie folgt, auf welche Weise das Schema generiert wird:

- Wenn dem XML-Dokument kein Schema oder keine DTD (Document Type Definition) zugeordnet ist, wird mithilfe der Daten im XML-Dokument ein neues XML-Schema abgeleitet.

- Wenn das XML-Dokument eine zugeordnete DTD enthält, werden die externe DTD und die interne Teilmenge in ein entsprechendes XML-Schema konvertiert.

- Wenn das XML-Dokument ein XDR-Inlineschema (XML-Data Reduced) enthält, wird das XDR-Schema in ein entsprechendes XML-Schema konvertiert.

Mit den erstellten Schemata wird anschließend IntelliSense für die XML-Datei bereitgestellt.

Weitere Informationen zur Schemarückschluss-Engine finden Sie unter [Ableiten eines XML-Schemas](/dotnet/standard/data/xml/inferring-an-xml-schema).

## <a name="to-create-an-xml-schema"></a>So erstellen Sie ein XML-Schema

1. Öffnen Sie eine XML-Datei in Visual Studio.

2. Wählen Sie auf der Menüleiste **XML** > **Schema erstellen** aus.

   Ein XML-Schemadokument wird für jeden in der XML-Datei gefundenen Namespace erstellt und geöffnet. Jedes Schema wird als sonstige temporäre Datei geöffnet. Die Schemata können auf Datenträger gespeichert, dem Projekt hinzugefügt oder verworfen werden.

## <a name="see-also"></a>Siehe auch

- [XML-Editor](../xml-tools/xml-editor.md)
