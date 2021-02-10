---
title: 'Vorgehensweise: Erstellen mehrerer Konfigurationen'
description: Hier erfahren Sie, wie Sie die meisten Projekttypen mit mehreren oder sogar allen Buildkonfigurationen mit nur einer IDE-Aktion erstellen können.
ms.custom: SEO-VS-2020
ms.date: 05/13/2020
ms.technology: vs-ide-compile
ms.topic: how-to
ms.assetid: ba830937-3317-4674-8cc2-c0cd565603c5
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cabaf226742d867e9d5eccbaf391b723cfbed5d1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967669"
---
# <a name="how-to-build-multiple-configurations-in-a-single-build-request"></a>Vorgehensweise: Erstellen mehrerer Konfigurationen in einer einzelnen Buildanforderung

Über das Dialogfeld **Batch erstellen** können Sie die meisten Projekttypen mit mehreren oder sogar allen Buildkonfigurationen mit einer IDE-Aktion erstellen. Die folgenden Projekttypen können Sie jedoch nicht gleichzeitig in mehreren Buildkonfigurationen erstellen:

1. Für Windows erstellte [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]-Apps mit JavaScript.

2. Für Visual Basic-Projekte.

3. CMake-Projekte.

Wenn eine Projektmappe ein beliebiges Projekt dieser zwei Projekttypen enthält, steht **Batch erstellen** für diese Projektmappe nicht zur Verfügung. In diesem Fall wird der Befehl nicht im Menü **Erstellen** angezeigt.

   Weitere Informationen zu Buildkonfigurationen finden Sie unter [Grundlagen der Buildkonfigurationen](../ide/understanding-build-configurations.md).

## <a name="to-build-a-project-in-multiple-build-configurations"></a>Erstellen eines Projekts in mehreren Buildkonfigurationen

1. Klicken Sie in der Menüleiste auf **Erstellen** > **Batch erstellen**. Alternativ können Sie **STRG**+**Q** drücken, um das Suchfeld zu öffnen und nach `Batch Build` zu suchen.

2. Aktivieren Sie in der Spalte **Erstellen** die Kontrollkästchen für die Konfigurationen, in denen Sie ein Projekt erstellen möchten.

    > [!TIP]
    > Klicken Sie zum Bearbeiten oder Erstellen einer Buildkonfiguration für eine Projektmappe in der Menüleiste auf **Erstellen** > **Konfigurations-Manager**, um das Dialogfeld **Konfigurations-Manager** zu öffnen. Nachdem Sie eine Buildkonfiguration für eine Projektmappe bearbeitet haben, klicken Sie im Dialogfeld **Batch erstellen** auf die Schaltfläche **Neu erstellen**, um alle Buildkonfigurationen für die Projekte in der Projektmappe zu aktualisieren.

3. Klicken Sie auf **Erstellen** oder **Neu erstellen**, um das Projekt mit den von Ihnen angegebenen Konfigurationen zu erstellen.

## <a name="see-also"></a>Siehe auch

- [How to: Erstellen und Bearbeiten von Konfigurationen](../ide/how-to-create-and-edit-configurations.md)
- [Grundlagen der Buildkonfiguration](../ide/understanding-build-configurations.md)
- [Paralleles Erstellen von mehreren Projekten](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)