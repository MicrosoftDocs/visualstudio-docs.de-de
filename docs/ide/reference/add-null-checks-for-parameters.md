---
title: Hinzufügen von Überprüfungen auf NULL für alle Parameter
description: Lernen Sie, if-Anweisungen zu erstellen und Ihrem Code hinzuzufügen, die alle nicht geprüften, Nullwerte zulassenden Parameter auf den NULL-Wert überprüfen.
ms.custom: SEO-VS-2020
ms.date: 09/17/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 5828a2bb28f7b3085cd5d43c452c520a730b8175
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/25/2020
ms.locfileid: "95870962"
---
# <a name="add-null-checks-for-all-parameters"></a>Hinzufügen von Überprüfungen auf NULL für alle Parameter 

Dieses Refactoring gilt für: 

- C# 

**Beschreibung:** Erstellt und fügt `if`-Anweisungen hinzu, die den NULL-Wert aller nicht geprüften Nullable-Parameter überprüfen. 

**Hintergrund:** Sie möchten schnell Überprüfungen auf NULL für alle anwendbaren Methodenparameter hinzufügen.

**Vorteile**: Das Schreiben von Überprüfungen auf NULL für viele Parameter kann zeitaufwändig sein und viele, sich wiederholenden Aufgaben umfassen sein. Die Verwendung dieses Refactorings ist schnell und macht das Programm stabiler.  

## <a name="how-to"></a>Vorgehensweise 

1. Platzieren Sie den Cursor auf einem beliebigen Parameter innerhalb der Methode.

2. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen.

   ![Schnellaktionen und Refactorings](media/add-null-checks-for-all-parameters.png)
   
3. Wählen Sie die Option, um **Überprüfungen auf NULL für alle Parameter hinzuzufügen**.

   ![Überprüfungen auf NULL für alle Parameter hinzufügen](media/add-null-checks-for-all.png) 

## <a name="see-also"></a>Weitere Informationen 

- [Refactoring](../refactoring-in-visual-studio.md)
