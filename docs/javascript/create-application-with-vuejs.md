---
title: Erstellen einer Vue.js-App mithilfe von Node.js
description: Node.js-Anwendungen können in Visual Studio mit dem Vue.js-Framework erstellt werden.
ms.custom: seodec18
ms.date: 07/06/2018
ms.topic: how-to
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 52281c403ceb0f2708aa546cbd73559593c419be
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942827"
---
# <a name="create-a-vuejs-application-using-nodejs-tools-for-visual-studio"></a>Erstellen einer Vue.js-Anwendung mit Node.js-Tools für Visual Studio

Visual Studio unterstützt die Entwicklung von Apps mit dem [Vue.js](https://vuejs.org/)-Framework in JavaScript oder TypeScript.

Mit den folgenden Features wird die Entwicklung von Vue.js-Anwendungen in Visual Studio unterstützt:

* Unterstützung für Skript-, Stil- und Vorlagenblöcken in *VUE*-Dateien
* Erkennung des `lang`-Attributs in *VUE*-Dateien
* Vorlagen für Vue.js-Projekte und -Dateien

## <a name="prerequisites"></a>Voraussetzungen

* Sie müssen Visual Studio 2017 Version 15.8 oder höher und die Workload **Node.js-Entwicklung** installiert haben.

    > [!IMPORTANT]
    > Für diesen Artikel sind Features erforderlich, die nur in Visual Studio 2017 Version 15.8 verfügbar sind.

    ::: moniker range=">=vs-2019"
    Falls die erforderliche Version noch nicht installiert ist, installieren Sie [Visual Studio 2019](https://visualstudio.microsoft.com/downloads).
    ::: moniker-end
    ::: moniker range="vs-2017"
    Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) kostenlos herunterladen.
    ::: moniker-end

    Wenn Sie die Workload installieren müssen, Visual Studio aber bereits besitzen, navigieren Sie zu **Tools** > **Tools und Features abrufen…** . Dadurch wird der Visual Studio-Installer geöffnet. Klicken Sie auf die Workload **Node.js-Entwicklung** und anschließend auf **Ändern**.

* Zum Erstellen des ASP.NET Core-Projekts müssen die Workloads „ASP.NET und Webentwicklung“ und „Plattformübergreifende .NET Core-Entwicklung“ installiert sein.

* Die Node.js-Laufzeit muss installiert sein.

    Wenn sie nicht bereits installiert ist, installieren Sie die LTS-Version über die [Node.js](https://nodejs.org/en/download/)-Website. Im Allgemeinen erkennt Visual Studio die installierte Node.js-Runtime automatisch. Wenn eine installierte Runtime nicht erkannt wird, können Sie Ihr Projekt so konfigurieren, dass es auf der Eigenschaftenseite auf die installierte Runtime verweist. (Klicken Sie nach dem Erstellen eines Projekts mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Eigenschaften** aus.)

## <a name="create-a-vuejs-project-using-nodejs"></a>Erstellen eines Vue.js-Projekts unter Verwendung von Node.js

Ein neues Projekt können Sie mithilfe der neuen Vue.js-Vorlage erstellen. Die Verwendung der Vorlage ist die einfachste Möglichkeit für den Einstieg. Eine ausführliche Anleitung finden Sie unter [Use Visual Studio to create your first Vue.js app (Verwenden von Visual Studio zum Erstellen der ersten Vue.js-App)](../javascript/quickstart-vuejs-with-nodejs.md).

## <a name="create-a-vuejs-project-with-aspnet-core-and-the-vue-cli"></a>Erstellen eines Vue.js-Projekts mit ASP.NET Core und der Vue-Befehlszeilenschnittstelle

Vue.js stellt eine offizielle Befehlszeilenschnittstelle zum schnellen Aufbau eines Gerüst für Projekte bereit. Wenn Sie Ihre Anwendung mit der Befehlszeilenschnittstelle erstellen möchten, verwenden Sie die Anleitung in diesem Artikel zum Einrichten der Entwicklungsumgebung.

> [!IMPORTANT]
> Für diese Anleitung wird vorausgesetzt, dass Sie bereits über Erfahrung mit dem Vue.js-Framework verfügen. Ist dies nicht der Fall, finden Sie unter [Vue.js](https://vuejs.org/) weitere Informationen zum Framework.

### <a name="create-a-new-aspnet-core-project"></a>Erstellen eines neuen ASP.NET Core-Projekts

Für dieses Beispiel wird eine leere ASP.NET Core-Anwendung (C#) verwendet. Sie können jedoch aus einer Vielzahl von Projekten und Programmiersprachen wählen.

#### <a name="create-an-empty-project"></a>Erstellen eines leeren Projekts

1. Öffnen Sie Visual Studio, und erstellen Sie ein neues Projekt.

    ::: moniker range=">=vs-2019"
    Drücken Sie **ESC**, um das Startfenster zu schließen. Geben Sie **STRG + Q** ein, um das Suchfeld zu öffnen, geben Sie **asp.net** ein, und wählen Sie dann **Neue ASP.NET Core-Webanwendung erstellen** aus. Geben Sie im Dialogfeld, das nun angezeigt wird, den Namen **client-app** ein, und wählen Sie dann **Erstellen** aus.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Klicken Sie oben in der Menüleiste auf **Datei** > **Neu** > **Projekt**. Erweitern Sie im linken Bereich des Dialogfelds **Neues Projekt** den Eintrag **Visual C#** , und wählen Sie dann **Web** aus. Wählen Sie im mittleren Bereich **ASP.NET Core-Webanwendung** aus, geben Sie den Namen **client-app** ein, und wählen Sie dann **OK** aus.
    ::: moniker-end

    Wenn die Projektvorlage **ASP.NET Core-Webanwendung** nicht vorhanden ist, installieren Sie zunächst die Workload **ASP.NET und Webentwicklung** und die Entwicklungsworkload .**NET Core**. Klicken Sie zum Installieren der Workloads auf den Link **Visual Studio-Installer öffnen** im linken Bereich des Dialogfelds **Neues Projekt** (wählen Sie **Datei** > **Neu** > **Projekt** aus). Der Visual Studio-Installer wird gestartet. Wählen Sie die erforderlichen Workloads aus.

1. Wählen Sie **Leer** aus, und klicken Sie dann auf **OK**.

    Visual Studio erstellt das Projekt, das im Projektmappen-Explorer (rechter Bereich) geöffnet wird.

#### <a name="configure-the-project-startup-file"></a>Konfigurieren der Startdatei des Projekts

* Öffnen Sie die Datei *./Startup.cs*, und fügen Sie der Configure-Methode die folgenden Zeilen hinzu:

    ```csharp
    app.UseDefaultFiles(); // Enables default file mapping on the web root.
    app.UseStaticFiles(); // Marks files on the web root as servable.
    ```

### <a name="install-the-vue-cli"></a>Installieren der Vue-Befehlszeilenschnittstelle

Öffnen Sie zum Installieren des NPM-Moduls vue-cli eine Eingabeaufforderung, und geben Sie `npm install --g vue-cli` oder `npm install -g @vue/cli` für Version 3.0 (derzeit als Betaversion) ein.

### <a name="scaffold-a-new-client-application-using-the-vue-cli"></a>Erstellen eines Gerüsts für eine neue Clientanwendung mit der Vue-Befehlszeilenschnittstelle

1. Wechseln Sie zur Eingabeaufforderung, und geben Sie als aktuelles Verzeichnis das Stammverzeichnis Ihres Projekts ein.

1. Geben Sie `vue init webpack client-app` ein, und führen Sie die entsprechenden Schritte aus, wenn Sie aufgefordert werden, weitere Fragen zu beantworten.

    > [!NOTE]
    > Bei *.vue*-Dateien müssen Sie WebPack oder ein ähnliches Framework mit einem Ladeprogramm für die Konvertierung verwenden. TypeScript und Visual Studio ist nicht bekannt, wie *.vue*-Dateien kompiliert werden. Das Gleiche gilt für die Bündelung. TypeScript ist nicht bekannt, wie ES2015-Module (d. h. `import`- und `export`-Anweisungen) in eine einzige endgültige *.js*-Datei zum Laden im Browser konvertiert werden. Auch in diesem Fall ist WebPack die beste Wahl. Damit dieser Vorgang innerhalb von Visual Studio mithilfe von MSBuild ausgeführt werden kann, müssen Sie mit einer Visual Studio-Vorlage beginnen. Derzeit ist keine ASP.NET-Vorlage für die Vue.js-Entwicklung im Lieferumfang enthalten.

#### <a name="modify-the-webpack-configuration-to-output-the-built-files-to-wwwroot"></a>Ändern der Webpack-Konfiguration, sodass die kompilierten Dateien in wwwroot ausgegeben werden

* Öffnen Sie die Datei *./client-app/config/index.js*, und ändern Sie `build.index` und `build.assetsRoot` in den wwwroot-Pfad:

    ```js
    // Template for index.html
    index: path.resolve(__dirname, '../../wwwroot/index.html'),

    // Paths
    assetsRoot: path.resolve(__dirname, '../../wwwroot'),
    ```

#### <a name="indicate-the-project-to-build-the-client-app-each-time-that-a-build-is-triggered"></a>Angeben des Projekts, um die Client-App bei jedem Auslösen eines Builds zu erstellen

1. Wechseln Sie in Visual Studio zu **Projekt** > **Eigenschaften** > **Buildereignisse**.

1. Geben Sie `npm --prefix ./client-app run build` in der **Befehlszeile für Präbuildereignis** ein.

#### <a name="configure-webpacks-output-module-names"></a>Konfigurieren von Namen für Webpack-Ausgabemodule

* Öffnen Sie die Datei *./client-app/build/webpack.base.conf.js*, und fügen Sie der Ausgabeeigenschaft folgende Eigenschaften hinzu:

    ```js
    devtoolModuleFilenameTemplate: '[absolute-resource-path]',
    devtoolFallbackModuleFilenameTemplate: '[absolute-resource-path]?[hash]'
    ```

### <a name="add-typescript-support-with-the-vue-cli"></a>Erweitern der Vue-Befehlszeilenschnittstelle um TypeScript-Unterstützung

Für diese Schritte ist vue-cli 3.0 erforderlich, das derzeit als Betaversion vorliegt.

1. Wechseln Sie zur Eingabeaufforderung, und geben Sie als aktuelles Verzeichnis das Stammverzeichnis des Projekts ein.

1. Geben Sie `vue create client-app` ein, und wählen Sie anschließend **Manually select features** (Features manuell auswählen) aus.

1. Wählen Sie zunächst **Typescript** und anschließend weitere gewünschte Optionen aus.

1. Führen Sie die verbleibenden Schritte aus, und beantworten Sie die Fragen.

#### <a name="configure-a-vuejs-project-for-typescript"></a>Konfigurieren eines Vue.js-Projekts für TypeScript

1. Öffnen Sie die Datei *./client-app/tsconfig.json*, und fügen Sie `noEmit:true` den Compileroptionen hinzu.

    Durch Festlegen dieser Option verhindern Sie, dass Ihr Projekt mit jedem Kompilieren in Visual Studio überladen wird.

1. Erstellen Sie als Nächstes die Datei *vue.config.js* file in *./client-app/* , und fügen Sie folgenden Code hinzu.

    ```js
    module.exports = {
        outputDir: '../wwwroot',

        configureWebpack: {
            output: {
                devtoolModuleFilenameTemplate: '[absolute-resource-path]',
                devtoolFallbackModuleFilenameTemplate: '[absolute-resource-path]?[hash]'
            }
        }
    };
    ```

    Mit dem vorstehenden Code wird Webpack konfiguriert und der Ordner „wwwroot“ festgelegt.

#### <a name="build-with-vue-cli-30"></a>Kompilieren mit vue-cli 3.0

Die Automatisierung des Buildprozesses wird ggf. durch einen unbekannten Fehler bei vue-cli 3.0 verhindert. Jedes Mal, wenn Sie den Ordner „wwwroot“ aktualisieren, müssen Sie für den Ordner „client-app“ den Befehl `npm run build` ausführen.

Alternativ können Sie das vue-cli 3.0-Projekt mithilfe der ASP.NET-Projekteigenschaften als Präbuildereignis erstellen. Klicken Sie mit der rechten Maustaste auf das Projekt. Wählen Sie **Eigenschaften**, und fügen Sie die folgenden Befehle auf der Registerkarte **Build** im Textfeld **Befehlszeile für Präbuildereignis** ein.

``` cmd
cd ./client-app
npm run build
cd ../
```

## <a name="limitations"></a>Einschränkungen

* Das Attribut `lang` unterstützt nur die Sprachen JavaScript und TypeScript. Zulässige Werte: js, jsx, ts und tsx.
* Das Attribut `lang` kann nicht mit Template- oder Style-Tags verwendet werden.
* Das Debuggen von Skriptblöcken in *VUE*-Dateien wird aufgrund der Vorverarbeitung nicht unterstützt.
* TypeScript erkennt *VUE*-Dateien nicht als Module. Sie benötigen eine Datei, die Code wie etwa den folgenden enthält, um TypeScript mitzuteilen, wie *VUE*-Dateien aussehen (diese Datei ist in der vue-cli 3.0-Vorlage bereits enthalten).

    ```js
    // ./client-app/vue-shims.d.ts
    declare module "*.vue" {
        import Vue from "vue";
        export default Vue;
    }
    ```

* Der Befehl `npm run build` kann bei Verwendung von vue-cli 3.0 nicht als Präbuildereignis für die Projekteigenschaften ausgeführt werden.

## <a name="see-also"></a>Siehe auch

- [Erste Schritte – Leitfaden für Vue](https://vuejs.org/v2/guide).
- [[Vue-CLI-Projekt]](https://github.com/vuejs/vue-cli)
- [Dokumentation zur Konfiguration von Webpack](https://webpack.js.org/configuration/).
