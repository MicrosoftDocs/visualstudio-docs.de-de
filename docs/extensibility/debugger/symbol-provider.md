---
title: Symbol Anbieter | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Symbol Anbieter, die Visual Studio bereitstellt, um eine Ausdrucks Auswertung zum Auswerten von Variablen und Ausdrücken zu aktivieren.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 043014ebababd990c9cae03f28cb1b642d576071
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996044"
---
# <a name="symbol-provider"></a>Symbol Anbieter
Eine Ausdrucks Auswertungs Implementierung muss auf die symbolischen Debuginformationen zugreifen, die vom sprach Compiler generiert werden, um Variablen und Ausdrücke auszuwerten. Dies erfolgt durch die Verwendung der Schnittstellen eines Symbol Anbieters (SP), auch als Symbol Handler bezeichnet.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bietet SPS für verwalteten Code sowie systemeigenen Code unter Verwendung des Symbol Datei Formats der Programmdatenbank (PDB). Es wird empfohlen, dass Sie die von bereitgestellten SPS verwenden, es sei denn, es besteht die Notwendigkeit, dass Ihr Programm in einem benutzerdefinierten Format gespeicherte Symbole verwendet [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="implementation-notes"></a>Hinweise zur Implementierung
 Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debug-engines erwarten mit dem SPS mithilfe von CLR-Schnittstellen (Common Language Runtime). Folglich muss ein SP, der mit den Visual Studio-debuggingmodulen arbeiten wird, die CLR unterstützen. Eine vollständige Liste aller CLR-Debugschnittstellen finden Sie in debugref.doc, die Teil von ist [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)] .

 Wenn Ihr SP nur mit der benutzerdefinierten Debug-Engine funktioniert, können Sie den SP abhängig von den Anforderungen Ihrer Debug-Engine entsprechend implementieren.

## <a name="see-also"></a>Weitere Informationen
- [Debugger-Komponenten](../../extensibility/debugger/debugger-components.md)
