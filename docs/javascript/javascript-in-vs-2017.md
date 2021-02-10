---
title: JavaScript
description: Hier erfahren Sie, dass Sie zum Schreiben von JavaScript-Code in der Visual Studio-IDE die meisten oder alle Standardbearbeitungshilfen (Codeausschnitte, IntelliSense usw.) verwenden können.
ms.custom: SEO-VS-2020
ms.date: 01/15/2019
ms.technology: vs-javascript
ms.topic: conceptual
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 74dca14c-5071-416f-a92b-d09f95e3dfb8
caps.latest.revision: 1
author: bowdenk7
ms.author: jillfra
manager: jmartens
ms.openlocfilehash: b39ee716c5092f41ef3ea8f05c529509ceca3717
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936859"
---
# <a name="javascript-in-visual-studio-2017"></a>JavaScript in Visual Studio 2017

JavaScript ist eine der Hauptprogrammiersprachen in Visual Studio. Zum Schreiben von JavaScript-Code in der Visual Studio-IDE können Sie die meisten oder alle Standardbearbeitungshilfen (Codeausschnitte, IntelliSense, usw.) verwenden. Sie können JavaScript-Code für viele Arten von Anwendungen und Dienste schreiben.

> [!NOTE]
> In dem Bemühen, die [MDN-Webdokumentation](https://developer.mozilla.org/en-US/) als führende zentrale Entwicklungsressource zu etablieren, werden alle Verweise auf die JavaScript-API von Microsoft (über 500 Seiten) von „docs.microsoft.com“ zu den jeweiligen MDN-Entsprechungen umgeleitet. Weitere Einzelheiten finden Sie in dieser [Ankündigung](https://blogs.windows.com/msedgedev/2018/06/26/chakra-docs-mdn-web-docs/).

## <a name="support-for-ecmascript-2015-es6-and-beyond"></a><a name="ES6"></a> Unterstützung für ECMAScript 2015 (ES6) und höher

Visual Studio unterstützt nun die Syntax für ECMAScript-Updates wie ECMAScript 2015/2016.

### <a name="what-is-ecmascript-2015"></a>Was ist ECMAScript 2015?

JavaScript wird als Programmiersprache ständig weiterentwickelt. Für Updates ist die Arbeitsgruppe [TC39](https://www.ecma-international.org/memento/tc39-m.htm) verantwortlich.
ECMAScript 2015 ist ein Update für JavaScript, das hilfreiche neue Syntaxelemente und Funktionen einführt. Ausführliche Informationen zu ES6-Funktionen finden Sie auf der entsprechenden [Referenzseite](http://es6-features.org/#Constants).

Visual Studio unterstützt neben ECMAScript 2015 auch ECMAScript 2016 und wird auch zukünftige ECMAScript-Versionen bei deren Release unterstützen. Die neuesten Änderungen der Arbeitsgruppe TC39 an ECMAScript können Sie mit [GitHub](https://github.com/tc39) im Blick behalten.

### <a name="transpile-javascript"></a>Transpilieren von JavaScript

Ein häufiges Problem mit JavaScript ist, dass Sie die neuesten ES6+-Sprachfunktionen zur Steigerung Ihrer Produktivität verwenden möchten, Ihre Laufzeitumgebungen (oft Browser) diese neuen Features jedoch noch nicht unterstützen. Sie müssen also entweder darauf achten, welche Features von Ihren Browsern unterstützt werden (was mühsam ist), oder Sie konvertieren Ihren ES6+-Code in eine Version, die mit den verwendeten Laufzeitumgebungen kompatibel ist (üblicherweise ES5). Die Konvertierung von Code in eine Version, die mit der Laufzeit kompatibel ist, wird gemeinhin als „Transpilierung“ bezeichnet.

Ein wesentliches Feature von TypeScript besteht darin, ES6+-Code in ES5- oder ES3-Code zu transpilieren. Auf diese Weise können Sie leistungsfähigen Code schreiben, der auf jeder Plattform ausgeführt werden kann. Da JavaScript in [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] den gleichen Sprachdienst wie TypeScript verwendet, kann auch JavaScript Vorteile aus der Transpilierung von ES6+ zu ES5 ziehen.

Bevor eine Transpilierung eingerichtet werden kann, ist ein Verständnis für die Konfigurationsoptionen erforderlich.
TypeScript ist über eine `tsconfig.json`-Datei konfiguriert.
Wenn eine solche Datei nicht vorhanden ist, werden einige Standardwerte verwendet.
Aus Gründen der Kompatibilität unterscheiden sind diese Standards in einem Kontext, in dem nur JavaScript-Dateien (und optional `.d.ts`-Dateien) vorhanden sind.
Um JavaScript-Dateien zu kompilieren, muss eine `tsconfig.json`-Datei hinzugefügt werden, und einige Einstellungen müssen explizit festgelegt werden.

Die erforderlichen Einstellungen für die tsconfig-Datei werden im Folgenden beschrieben:

- `allowJs`: Dieser Wert muss auf `true` festgelegt werden, damit JavaScript-Dateien erkannt werden. Der Standardwert ist `false`, da TypeScript in JavaScript kompiliert, und der Compiler sollte keine Dateien enthalten, die sie soeben kompiliert haben.
- `outDir`: Dieser Wert sollte auf einen Speicherort festgelegt werden, der nicht im Projekt enthalten ist, damit die ausgegebenen JavaScript-Dateien nicht erkannt und anschließend in das Projekt einbezogen werden (siehe `exclude`).
- `module`: Wenn Sie Module verwenden, weist diese Einstellung den Compiler an, welches Modulformat der ausgegebene Code verwenden sollte (z.B. `commonjs` für Knoten oder Bundler wie Browserify).
- `exclude`: Diese Einstellung gibt die Ordner an, die nicht im Projekt eingeschlossen werden sollen.
Sowohl der Ausgabeort als auch Ordner, die nicht Teil des Projekts sind, wie z.B. `node_modules` oder `temp`, sollten zu dieser Einstellung hinzugefügt werden.
- `enableAutoDiscovery`: Diese Einstellung ermöglicht die automatische Erkennung und das Herunterladen von Definitionsdateien, wie zuvor beschrieben.
- `compileOnSave`: Diese Einstellung weist den Compiler an, ob er jederzeit neu kompilieren soll, wenn eine Quelldatei in Visual Studio gespeichert ist.
- `typeAcquisition`: Diese Einstellungen legen das Verhalten der automatischen Typübernahme fest. Weitere Informationen finden Sie in [diesem Abschnitt](../ide/javascript-intellisense.md#Auto).

Um JavaScript-Dateien in CommonJS-Module zu konvertieren und diese in einen `./out`-Ordner abzulegen, können Sie z.B. die folgende `tsconfig.json`-Datei verwenden:

```json
{
  "compilerOptions": {
    "module": "commonjs",
    "allowJs": true,
    "outDir": "out"
  },
  "exclude": [
    "node_modules",
    "wwwroot",
    "out"
  ],
  "compileOnSave": true,
  "typeAcquisition": {
    "enable": true
  }
}
```

Wenn Sie die Einstellungen vorgenommen haben und eine Quelldatei (`./app.js`) vorhanden ist, können Sie in dieser die folgenden ECMAScript 2015-Sprachfeatures verwenden:

```js
import {Subscription} from 'rxjs/Subscription';  // ES6 import

class Foo {  // ES6 Class
    sayHi(name) {
        return `Hi ${name}, welcome to Salsa!`;  // ES6 template string
    }
}

export let sqr = x => x * x;  //ES6 export, let, and arrow function
export default Subscription;  //ES6 default export
```

Dann würde eine Datei in `./out/app.js` mit ECMAScript 5 (Standard) als Ziel ausgegeben werden, die etwa wie folgt aussieht:

```js
"use strict";
var Subscription_1 = require('rxjs/Subscription');
var Foo = (function () {
    function Foo() {
    }
    Foo.prototype.sayHi = function (name) {
        return "Hi " + name + ", welcome to Salsa!";
    };
    return Foo;
}());
exports.sqr = function (x) { return x * x; };
Object.defineProperty(exports, "__esModule", { value: true });
exports.default = Subscription_1.Subscription;
```

## <a name="better-intellisense"></a>Verbesserte IntelliSense-Funktion

JavaScript IntelliSense zeigt nun in [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] deutlich mehr Informationen zu Parametern und Memberlisten an. Diese neuen Informationen werden vom TypeScript-Sprachdienst bereitgestellt, der statische Analyse im Hintergrund verwendet, um Ihren Code besser zu verstehen. Weitere Informationen zu Neuerungen und zur Funktionsweise von IntelliSense finden Sie [hier](../ide/javascript-intellisense.md).

## <a name="jsx-syntax-support"></a><a name="JSX"></a> Support für JSX-Syntax

JavaScript in [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] bietet eine umfangreiche Unterstützung für die JSX-Syntax. JSX ist ein Syntaxset, das HTML-Tags in JavaScript-Dateien erlaubt.

Die folgende Abbildung zeigt eine React-Komponente, die in der `comps.tsx`-TypeScript-Datei definiert ist, und anschließend wird diese Komponente von der `app.jsx`-Datei verwendet, die mit IntelliSense für Abschlüsse und Dokumentation in die JSX-Ausdrücke ausgeführt wird.
Sie brauchen hier kein TypeScript, dieses spezielle Beispiel enthält hier nur auch einige TypeScript-Codes.

![JSX-Syntax](../javascript/media/js-react.png)

> [!NOTE]
> Für die Konvertierung der JSX-Syntax in React-Aufrufe muss die Einstellung `"jsx": "react"` in `compilerOptions` in der `tsconfig.json`-Datei hinzugefügt werden.

Der JavaScript-Datei, die in `./out/app.js' beim Build erstellt wird, würde diesen Code enthalten:

```js
"use strict";
var comps_1 = require('./comps');
var x = React.createElement(comps_1.RepoDisplay, {description: "test"});
```

## <a name="configure-your-javascript-project"></a>Konfigurieren eines JavaScript-Projekts

Der Sprachdienst basiert auf einer statischen Analyse, bei der Ihr Quellcode analysiert, aber nicht ausgeführt wird. Hierdurch werden die Ergebnisse von IntelliSense und weitere Bearbeitungsfeatures zur Verfügung gestellt.
Je mehr Dateien Sie in Ihrem Projektkontext verwenden und je größer diese sind, desto mehr Arbeitsspeicher und CPU werden während der Analyse verwendet.
Aus diesem Grund werden einige Annahmen über Ihre Projektform getroffen:

- `package.json` und `bower.json` listen Abhängigkeiten auf, die in Ihrem Projekt verwendet werden und standardmäßig Teil der automatischen Typübernahme (Automatic Type Acquisition, ATA) enthalten sind.
- Ein `node_modules`-Ordner der obersten Ebene enthält Quellcode einer Bibliothek. Die Inhalte des Ordners werden standardmäßig aus dem Projektkontext ausgeschlossen.
- Alle anderen `.js`-, `.jsx`-, `.ts`- und `.tsx`-Dateien sind vermutlich *Ihre eigenen* Quelldateien und müssen im Projektkontext enthalten sein.

In den meisten Fällen können Sie Ihr Projekt einfach öffnen und die Standardprojektkonfiguration problemlos verwenden. In Projekten mit großen oder unterschiedlichen Ordnerstrukturen kann es hingegen sinnvoll sein, den Sprachdienst zu konfigurieren, um den Schwerpunkt auf Ihre eigenen Quelldateien zu legen.

### <a name="override-defaults"></a>Überschreiben von Standardwerten

Sie können die obige Standardkonfiguration überschreiben, indem Sie dem Projektstamm eine `tsconfig.json`-Datei hinzufügen.
Eine `tsconfig.json`-Datei verfügt über mehrere Optionen, mit denen der Projektkontext bearbeitet werden kann.
Einige davon werden im Folgenden aufgeführt. Einen Überblick über alle verfügbaren Optionen finden Sie im [Schema Store](http://json.schemastore.org/tsconfig).

## <a name="important-tsconfigjson-options"></a>Wichtige `tsconfig.json`-Optionen

```json
{
  "compilerOptions": {
    "allowJs": true,          // include .js and .jsx in project context (defaults to only .ts and .tsx)
    "noEmit": true            // turns off downlevel compiler
  },
  "files": [],                // list of explicit files to include in the project context. Highest priority.
  "include": [],              // list of folders or glob patterns to include in the project context.
  "exclude": [],              // list of folders or glob patterns to exclude. Overridden by files array.
  "typeAcquisition": {
    "enable": true,           // Defaulted to "false" with a tsconfig. Enables better IntelliSense in JS.
    "include": [ "jquery" ],  // Specific libs to fetch .d.ts files that weren't picked up by ATA
    "exclude": [ "node" ]     // Specific libs to not fetch .d.ts files for
  }
}
```

### <a name="example-project-configuration"></a>Konfigurieren eines Beispielprojekts

Für dieses Beispiel wird ein Projekt mit der folgenden Einrichtung vorausgesetzt:

- Die Quelldateien des Projekts befinden sich in `wwwroot/js`.
- Die LIB-Dateien des Projekts befinden sich in `wwwroot/lib`.
- `bootstrap`, `jquery`, `jquery-validation` und `jquery-validation-unobtrusive` werden in der `bower.json`-Datei aufgeführt.
- `kendo-ui` wurde manuell dem Ordner „lib“ hinzugefügt.

![Ordnerstruktur](../javascript/media/js-folderstructure.png)

Sie können z.B. die folgende `tsconfig.json`-Datei verwenden, um sicherzustellen, dass der Sprachdienst nur Ihre Quelldateien im `js`-Ordner analysiert und dabei ausschließlich `.d.ts`-Dateien für die Bibliotheken in Ihrem `lib`-Ordner abruft und verwendet.

```json
{
  "compilerOptions": {
    "allowJs": true,
    "noEmit": true
  },
  "exclude": ["wwwroot/lib"],  //ignore lib folders, we will get IntelliSense via ATA
  "typeAcquisition": {
    "enable": true,
    "include": [ "kendo-ui" ]  //kendo-ui wasn't added via bower, so we need to list it here
  }
}
```

## <a name="troubleshooting-the-javascript-language-service-has-been-disabled-for-the-following-projects"></a>Problembehandlung: „JavaScript Language Service wurde für die folgenden Projekte deaktiviert.“
Wenn Sie ein JavaScript-Projekt mit umfangreichen Inhalten öffnen, erhalten Sie möglicherweise die Meldung „JavaScript Language Service wurde für die folgenden Projekte deaktiviert“. Die häufigste Ursache für eine umfassende JavaScript-Quelle ist, dass Bibliotheken mit Quellcode, der einen Projektgrenzwert von 20 MB überschreitet, enthalten sind.

Eine einfache Möglichkeit zur Optimierung Ihres Projekts besteht darin, eine `tsconfig.json`-Datei in Ihren Projektstamm hinzufügen, um dem Sprachdienst mitzuteilen, welche Dateien bedenkenlos ignoriert werden können. Verwenden Sie das Beispiel unten, um die am häufigsten verwendeten Verzeichnisse, in denen Bibliotheken gespeichert werden, auszuschließen:

```json
{
  "compilerOptions": {
    "allowJs": true,
    "allowSyntheticDefaultImports": true,
    "maxNodeModuleJsDepth": 2,
    "noEmit": true,
    "skipLibCheck": true
  },
  "exclude": [
    "**/bin",
    "**/bower_components",
    "**/jspm_packages",
    "**/node_modules",
    "**/obj",
    "**/platforms"
  ]
}
```

Fügen Sie weitere Verzeichnisse nach Bedarf hinzu. Einige weitere Beispiele sind „vendor“- oder „wwwroot/lib“-Verzeichnisse.

> [!NOTE]
> Die Compilereigenschaft `disableSizeLimit` kann ebenfalls verwendet werden, um den 20-MB-Überprüfungsgrenzwert zu deaktivieren. Gehen Sie besonders vorsichtig bei der Verwendung dieser Eigenschaft vor, da die Begrenzung zum Abstürzen des Sprachdiensts führen kann.

## <a name="notable-changes-from-visual-studio-2015"></a>Wichtige Unterschiede zu Visual Studio 2015

Da [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)] über einen völlig neuen Sprachdienst verfügt, fehlen oder unterscheiden sich einige Verhalten im Gegensatz zur bisherigen Version von Visual Studio.
Zu den wichtigsten Änderungen zählen das Ersetzen von VSDoc mit JSDoc, das Entfernen von benutzerdefinierten `.intellisense.js`-Erweiterungen sowie Einschränkungen bei IntelliSense im Fall von bestimmten Codemustern.

### <a name="no-more-references-or-_referencesjs"></a>`///<references/>` und `_references.js` nicht mehr verfügbar

Bisher war es schwierig nachzuvollziehen, welche Dateien zu einem bestimmten Zeitpunkt im IntelliSense-Bereich waren. In einigen Fällen war es wünschenswert, dass sich alle Dateien im Bereich befinden; in anderen Fällen hingegen nicht. Hierdurch waren komplexe Konfigurationen wie die manuelle Verweisverwaltung erforderlich. In der neuen Version von Visual Studio müssen Sie sich keine Gedanken mehr um die Verweisverwaltung machen. Sie benötigen nun nicht mehr Kommentare mit drei Schrägstrichen oder `_references.js`-Dateien.

Auf der Seite [JavaScript IntelliSense](../ide/javascript-intellisense.md) finden Sie weitere Informationen zur Funktionsweise von IntelliSense.

### <a name="vsdoc"></a>VSDoc

Durch XML-Dokumentationskommentare, auch als VSDocs bekannt, konnte Ihr Quellcode um zusätzliche Daten ergänzt werden, die Ihre IntelliSense-Ergebnisse verbesserten.
VSDoc wird nun nicht mehr unterstützt. Stattdessen kommt die Auszeichnungssprache [JSDoc](https://jsdoc.app/about-getting-started.html)zum Einsatz, die einfacher anzuwenden und der akzeptierte Standard für JavaScript ist.

### <a name="intellisensejs-extensions"></a>`.intellisense.js`-Erweiterungen

Bisher konnten Sie [IntelliSense-Erweiterungen](/previous-versions/visualstudio/visual-studio-2015/ide/extending-javascript-intellisense) erstellen, mit denen Sie benutzerdefinierte Vervollständigungsergebnisse für Bibliotheken von Drittanbietern hinzufügen konnten.
Die Entwicklung dieser Erweiterungen war aber eher umständlich. Außerdem war die Installation und die Erstellung von Verweisen mühsam, weswegen der neue Sprachdienst diese Dateien nicht mehr unterstützt.
Eine einfachere Alternative ist die Erstellung einer TypeScript-Definitionsdatei, mit der Sie von den gleichen Vorteilen von IntelliSense profitieren, die Sie von den vorherigen `.intellisense.js`-Erweiterungen kennen.
Weitere Informationen zur Erstellung von `.d.ts`-Deklarationsdateien [ finden Sie hier](http://www.typescriptlang.org/docs/handbook/declaration-files/introduction.html).

### <a name="unsupported-patterns"></a>Nicht unterstützte Muster

Da der neue Sprachdienst nicht auf einer Ausführungs-Engine, sondern auf einer statischen Analyse basiert (weitere Informationen zu den Unterschieden finden Sie in [diesem Thema](https://github.com/Microsoft/TypeScript/issues/4789)), gibt es einige JavaScript-Muster, die nicht mehr erkannt werden.
Das bekannteste Muster ist das „Expando“-Muster.
Derzeit kann der Sprachdienst IntelliSense nicht für Objekte bereitstellen, denen nach der Deklaration Eigenschaften zugewiesen werden.
Zum Beispiel:

```js
var obj = {};
obj.a = 10;
obj.b = "hello world";
obj. // IntelliSense won't show properties a or b
```

Sie können dieses Problem umgehen, indem Sie die Eigenschaften während der Erstellung des Objekts deklarieren:

```js
var obj = {
    "a": 10,
    "b": "hello world"
}
obj. // IntelliSense shows properties a and b
```

Sie können auch, wie oben gezeigt, einen JSDoc-Kommentar hinzufügen:

```js
/**
 * @type {{a: number, b: string}}
 */
var obj = {};
obj.a = 10;
obj.b = "hello world";
obj. // IntelliSense shows properties a and b
```