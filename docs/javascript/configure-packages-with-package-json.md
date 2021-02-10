---
title: Konfigurieren von npm-Paketen mit package.json
description: Angeben von npm-Paketversionen mithilfe von package.json
ms.date: 09/06/2018
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 891822d0b79cbfd53cf14229f11e003bf740c660
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969489"
---
# <a name="packagejson-configuration"></a>package.json-Konfiguration

Beim Entwickeln einer Node.js-App mit einer Vielzahl von npm-Paketen ist es nicht ungewöhnlich, dass beim Erstellen des Projekts Warnungen oder Fehler auftreten, wenn ein oder mehrere Pakete aktualisiert wurden. Manchmal tritt ein Versionskonflikt auf, oder eine Paketversion ist veraltet. Hier finden Sie einige einfache Tipps zum Konfigurieren Ihrer [package.json](https://docs.npmjs.com/files/package.json)-Datei, und Sie erfahren, was es mit Warnungen und Fehlern auf sich hat. Dies ist keine vollständige Anleitung für *package.json* und konzentriert sich nur auf die npm-Paketversionsverwaltung.

Die npm-Paketversionsverwaltung enthält strenge Regeln. Das Versionsformat lautet wie folgt:

```
[major].[minor].[patch]
```

Nehmen wir an, Sie verwenden in Ihrer App ein Paket der Version 5.2.1. Die Hauptversion ist 5, die Nebenversion 2, das Patch 1.

* Bei einem Hauptversionsupdate enthält das Paket neue Features, die nicht abwärtskompatibel sind, also Breaking Changes.
* Bei einem Nebenversionsupdate werden dem Paket neue Features hinzugefügt, die abwärtskompatibel mit früheren Paketversionen sind.
* In einem Patchupdate ist mindestens eine Fehlerbehebung enthalten. Fehlerbehebungen sind immer abwärtskompatibel.

Beachten Sie, dass einige npm-Paketfeatures über Abhängigkeiten verfügen. Um beispielsweise ein neues Feature des TypeScript-Compilerpakets (ts-loader) mit Webpack zu verwenden, müssen Sie möglicherweise auch das Webpack-npm-Paket und das Webpack-CLI-Paket aktualisieren.

Hinsichtlich der Paketversionsverwaltung unterstützt npm mehrere Notationen, die Sie in *package.json* verwenden können. Sie können diese Notationen zum Steuern des Paketupdatetyps verwenden, den Sie für Ihre App verwenden möchten.

Nehmen wir an, Sie verwenden React und müssen die npm-Pakete **react** und **react-dom** einschließen. Sie können dies auf verschiedene Arten in Ihrer *package.json*-Datei angeben. Beispielsweise können Sie die Verwendung der genauen Version eines Pakets wie folgt angeben.

  ```json
  "dependencies": {
    "react": "16.4.2",
    "react-dom": "16.4.2",
  },
  ```

Bei Verwendung der vorherigen Notation ruft npm immer die genau angegebene Version 16.4.2 ab.

Sie können eine besondere Notation verwenden, um Updates auf Patchupdates (Fehlerbehebungen) zu beschränken. In diesem Beispiel:

  ```json
  "dependencies": {
    "react": "~16.4.2",
    "react-dom": "~16.4.2",
  },
  ```

Verwenden Sie das Tilde-Zeichen (~), um npm zu informieren, dass ein Paket nur dann aktualisiert werden soll, wenn es gepatcht wurde. So kann npm React von Version 16.4.2 auf Version 16.4.3 (oder 16.4.4 usw.) aktualisieren, akzeptiert dabei aber kein Update auf eine höhere Haupt- oder Nebenversion. Version 16.4.2 wird also nicht auf Version 16.5.0 aktualisiert.

Sie können auch das Einfügemarkensymbol (^) verwenden, um anzugeben, dass npm die Nummer der Nebenversion aktualisieren kann.

  ```json
  "dependencies": {
    "react": "^16.4.2",
    "react-dom": "^16.4.2",
  },
  ```

Unter Verwendung dieser Notation kann npm React von Version 16.4.2 auf Version 16.5.0 (oder 16.5.1, 16.6.0 usw.) aktualisieren, akzeptiert dabei aber kein Update auf eine höhere Hauptversion. Version 16.4.2 wird also nicht auf Version 17.0.0 aktualisiert.

Beim Aktualisieren von Paketen generiert npm eine *package-lock.json*-Datei, die die tatsächlich in Ihrer App verwendeten npm-Paketversionen einschließlich aller geschachtelten Pakete aufführt. Zwar steuert *package.json* die direkten, nicht aber die geschachtelten Abhängigkeiten für Ihre App (andere npm-Pakete für bestimmtes npm-Paket erforderlich). Sie können die *package-lock.json*-Datei im Entwicklungszyklus verwenden, um sicherzustellen, dass andere Entwickler und Tester genau die gleichen Pakete (einschließlich geschachtelte Pakete) verwenden wie Sie. Weitere Informationen finden Sie in der [package-lock.json](https://docs.npmjs.com/files/package-lock.json)-Datei in der npm-Dokumentation.

Für Visual Studio wird die *-Paket-lock.json* Datei dem Projekt nicht hinzugefügt, aber Sie finden es im Projektordner.
