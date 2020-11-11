---
title: Versionskompatibilität für die Eincheckrichtlinien der Codeanalyse
ms.date: 11/04/2016
description: Erfahren Sie, wie Team System 2008 Team Foundation Server und Team Foundation Server 2010 die Check-in-Richtlinien von Visual Studio unterschiedlich auswerten.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- version compatibility, code analysis check-in policy
- check-in policies, version compatibility for code analysis
ms.assetid: 1af376e3-3be7-4445-803b-76a858567a5b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3a681f510da270bc22ae4bc983103f9a5735a127
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94436874"
---
# <a name="version-compatibility-for-code-analysis-check-in-policies"></a>Versionskompatibilität für die Eincheckrichtlinien der Codeanalyse

Wenn Sie Eincheck Richtlinien für die Code Analyse mithilfe verschiedener Versionen von auswerten und verfassen müssen [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] , müssen Sie die Unterschiede in der Art und Weise der [!INCLUDE[vstsTfsOrcasLong](../code-quality/includes/vststfsorcaslong_md.md)] Auswertung von [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] Eincheck Richtlinien kennen.

## <a name="version-compatibility-for-evaluating-check-in-policies"></a>Versions Kompatibilität für das Auswerten von Check-In-Richtlinien

- Wenn Eincheck Richtlinien für die Code Analyse in ausgewertet werden [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] , werden alle Regeln ignoriert, die in vorhanden sind, [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] jedoch nicht in vorhanden [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] sind.

- Wenn Eincheck Richtlinien für die Code Analyse in ausgewertet werden [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] , werden alle neuen Regeln, die exklusiv für sind, [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] ignoriert.

- Wenn die Eincheck Richtlinie für die Code Analyse Regelassemblys angibt, [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] ignoriert alle Regeln, die von den nicht erkannten Assemblys angegeben werden.

- Wenn die Eincheck Richtlinie für die Code Analyse Regelassemblys angibt, die von [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] nicht erkannt werden, wird eine Meldung angezeigt.

## <a name="version-compatibility-for-authoring-check-in-policies"></a>Versions Kompatibilität für die Erstellung von Check-In-Richtlinien

- Wenn Sie eine Eincheck Richtlinie für die Code Analyse mithilfe der- [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] Version von erstellt [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] haben, können Sie Sie nicht mit der- [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] Version von [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] ändern. Außerdem [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] kann die Richtlinie nicht auswerten.

- Wenn Sie eine Eincheck Richtlinie für die Code Analyse mithilfe von [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] in erstellt [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] haben, können Sie Sie in verwenden, [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] um Sie zu ändern, und die Richtlinie kann auch von ausgewertet werden [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] . Nachdem Sie die Richtlinie mithilfe von [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] in geändert [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] haben, können Sie die Richtlinie nicht mehr mithilfe von [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] in bearbeiten [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] . [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] kann die Richtlinien ohne Probleme mit nicht übereinstimmenden starken Namen auswerten.

- Zum Erstellen einer Eincheck Richtlinie für die Code Analyse mit Regel Einstellungen, die sowohl für [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] als auch gelten [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] , müssen Sie die Richtlinie in Erstellen [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] , alle benötigten Änderungen vornehmen und die Richtlinie speichern. Wenn die Änderungen an Regeln nur in vorhanden [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] sind, ändern und speichern Sie die Richtlinie in [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] .

   Nachdem Sie die Richtlinie in gespeichert [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] haben, können Sie die Einstellungen für Regeln, die nur in vorhanden sind, nicht mehr ändern [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] .
