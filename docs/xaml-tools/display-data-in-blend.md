---
title: Visualisieren von Beispieldaten in einer XAML-Benutzeroberfläche
titleSuffix: Blend for Visual Studio
description: Erfahren Sie, wie Sie Stichprobendaten von Grund auf neu oder in einer vorhandenen Klasse in Blend für Visual Studio generieren.
ms.custom: SEO-VS-2020
ms.date: 03/06/2018
ms.topic: conceptual
ms.assetid: 87d31b6c-4607-4121-bb7d-cfc80390ab93
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 927779e6d58de9eeaacd43b6b03f837dbc3281e2
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796679"
---
# <a name="display-data-in-blend-for-visual-studio"></a>Anzeigen von Daten in Blend für Visual Studio

Sie können Beispieldaten im Designer anzeigen, um das Layout der Seiten anzupassen. Sie können Beispieldaten von Grund auf neu oder mithilfe einer vorhandenen Klasse generieren. Sie können sich auch mit *Livedaten* verbinden, die beim Ausführen der Anwendung angezeigt werden.

> [!NOTE]
> Das **Daten** Panel in Blend wird nur für Projekte unterstützt, die auf .NET Framework abzielen. Dies wird nicht für UWP-Projekte oder-Projekte unterstützt, die auf .net Core abzielen.

## <a name="generate-sample-data"></a>Generieren von Beispieldaten

Öffnen Sie ein XAML-Dokument zum Generieren von Beispieldaten. Wählen Sie im Bereich **Daten** die Schaltfläche **Beispieldaten erstellen** ![Symbol Beispieldaten erstellen](../designers/media/30540d76-7256-43ce-b5d9-4b2edf3d339f.png) und anschließend **Neue Beispieldaten** aus.

Definieren Sie die Struktur der Daten im Bereich **Daten** und binden Sie sie dann an die UI-Elemente auf einer beliebigen Seite.

![Datenbereich](../designers/media/496d7ebc-fe46-42f6-95a8-57b0e5be5d49.png)

Wenn die Beispieldaten beim Ausführen der Anwendung auf Ihren Seiten angezeigt werden sollen, wählen Sie **Datenquelloptionen** ![Symbol Datenquelloptionen](../designers/media/ae1fd260-4f84-420d-b196-45fde357d81d.png) und dann **Beim Ausführen der Anwendung aktivieren** aus.

![Menüelement „Beim Ausführen der Anwendung aktivieren“](../designers/media/05d5356d-91bb-4e6b-b3f7-29b76852c4b3.png)

**Sehen Sie sich dieses kurze Video an:** ![Play-Symbol](../designers/media/bldadminconsoleinitialconfigicon.PNG) [Neuerstellen von Beispieldaten](https://www.bing.com/videos/search?q=blend%20data&qs=n&form=QBVR&pq=blend%20data&sc=8-7&sp=-1&sk=#view=detail&mid=F8F2449A76956D480FD2F8F2449A76956D480FD2&preserve-view=true).

## <a name="generate-sample-data-from-a-class"></a>Generieren von Beispieldaten aus einer Klasse

Wenn Sie bereits Klassen erstellt haben, die die Struktur Ihrer Daten beschreiben, können Sie hieraus die Beispieldaten generieren.

Öffnen Sie zum Generieren von Beispieldaten aus einer Klasse ein XAML-Dokument, klicken Sie im Bereich **Daten** auf die Schaltfläche **Beispieldaten erstellen** ![Beispieldaten erstellen Symbol](../designers/media/30540d76-7256-43ce-b5d9-4b2edf3d339f.png) und anschließend auf **Beispieldaten aus Klasse erstellen** .

**Sehen Sie sich dieses kurze Video an:** ![Play-Symbol](../designers/media/bldadminconsoleinitialconfigicon.PNG) [Zusammenführen von Datenbindungen mit Blend](https://www.youtube.com/watch?v=LSwPB6CAvjg).

## <a name="see-also"></a>Weitere Informationen:

- [Erstellen einer Benutzeroberfläche mit Blend für Visual Studio](../xaml-tools/creating-a-ui-by-using-blend-for-visual-studio.md)