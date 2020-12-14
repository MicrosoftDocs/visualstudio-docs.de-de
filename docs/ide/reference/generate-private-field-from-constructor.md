---
title: Generieren eines privaten Felds und einer privaten Eigenschaft anhand eines Konstruktors
description: Hier erfahren Sie, wie Sie über das Menü „Schnellaktionen und Refactorings...“ ein privates Feld oder eine private Eigenschaft über einen Konstruktor generieren.
ms.custom: SEO-VS-2020
ms.date: 06/20/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: e989efed8b58746312ed5f5a510efa049393f3db
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2020
ms.locfileid: "96617460"
---
# <a name="generate-private-field-and-property-from-constructor"></a>Generieren eines privaten Felds und einer privaten Eigenschaft anhand eines Konstruktors

Dieses Refactoring gilt für: 

- C# 

**Beschreibung:** Dient zum Generieren eines privaten Felds oder einer privaten Eigenschaft anhand eines Konstruktors. 

**Hintergrund:** Sie möchten schnell ein privates Feld oder eine private Eigenschaft anhand eines Konstruktors hinzufügen und initialisieren.

**Vorteile**: Das Schreiben privater Felder und Eigenschaften kann zeitaufwändig und monoton sein. Die Verwendung dieses Refactorings ist schnell und macht das Programm stabiler.

## <a name="how-to"></a>Vorgehensweise 

1. Platzieren Sie Ihren Cursor auf dem Parameternamen im Konstruktor.

2. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen.
   
3. Wählen Sie als Nächstes eine der folgenden Optionen aus:

- **Feld erstellen und initialisieren** oder **Eigenschaft erstellen und initialisieren**.

   ![Generieren eines privaten Felds aus einem Konstruktor](media/generate-private-field-from-constructor.png)

## <a name="see-also"></a>Siehe auch 

- [Refactoring](../refactoring-in-visual-studio.md)
