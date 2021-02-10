---
title: Verwenden von KubernetesLocalProcessConfig.yaml zur zusätzlichen Konfiguration mit Bridge to Kubernetes
services: azure-dev-spaces
ms.date: 07/28/2020
ms.topic: conceptual
description: Hier werden die zusätzlichen Konfigurationsoptionen für Bridge to Kubernetes bei Verwendung von KubernetesLocalProcessConfig.yaml beschrieben.
keywords: Bridge to Kubernetes, Azure Dev Spaces, Dev Spaces, Docker, Kubernetes, Azure, AKS, Azure Kubernetes Service, container
monikerRange: '>=vs-2019'
author: ghogen
ms.author: ghogen
manager: jmartens
ms.openlocfilehash: b250454fe5e80ec18f75add92c8c2f653893e994
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867619"
---
# <a name="configure-bridge-to-kubernetes"></a>Konfigurieren von Bridge to Kubernetes

Mit der Datei `KubernetesLocalProcessConfig.yaml` können Sie Umgebungsvariablen und eingebundene Dateien replizieren, die für Pods in Ihrem AKS-Cluster verfügbar sind. Sie können die folgenden Aktionen in einer `KubernetesLocalProcessConfig.yaml`-Datei angeben:

* Laden Sie ein Volume herunter, und legen Sie den Pfad zu diesem Volume als Umgebungsvariable fest.
* Machen Sie einen in Ihrem Cluster ausgeführten Dienst für Prozesse verfügbar, die auf Ihrem Entwicklungscomputer ausgeführt werden.
* Erstellen Sie eine Umgebungsvariable mit einem konstanten Wert.

Eine `KubernetesLocalProcessConfig.yaml`-Standarddatei wird nicht automatisch erstellt, daher müssen Sie die Datei manuell im Stammverzeichnis des Projekts erstellen.

## <a name="download-a-volume"></a>Herunterladen eines Volumes

Geben Sie unter *env* einen Wert für *name* und *value* für jedes Volume an, das Sie herunterladen möchten. *name* ist die Umgebungsvariable, die auf Ihrem Entwicklungscomputer verwendet wird. *value* gibt den Namen des Volumes und einen Pfad auf Ihrem Entwicklungscomputer an. Der Wert für *value* weist das Format *$(volumeMounts:VOLUME_NAME)/PATH/TO/FILES* auf.

Zum Beispiel:

```yaml
version: 0.1
env:
  - name: ALLOW_LIST_PATH
    value: $(volumeMounts:allow-list)/allow-list
```

Das obige Beispiel lädt das Volume *allow-list* aus dem Container herunter und legt den Speicherort sowie den Pfad zur Umgebungsvariable *ALLOW_LIST_PATH* fest. Gemäß Standardverhalten werden die Dateien in den Pfad heruntergeladen, den Sie in einem temporären Verzeichnis auf Ihrem Entwicklungscomputer angeben. Im obigen Beispiel ist *ALLOW_LIST_PATH* auf `/TEMPORARY_DIR/allow-list` festgelegt. 

> [!NOTE]
> Beim Herunterladen eines Volumes wird unabhängig von dem von Ihnen festgelegten Pfad der gesamte Inhalt dieses Volumes heruntergeladen. Der Pfad wird nur verwendet, um die Umgebungsvariable festzulegen, die auf dem Entwicklungscomputer verwendet werden soll. Das Hinzufügen von */allow-list* oder */path/to/files* am Ende des Tokens wirkt sich nicht darauf aus, wo das Volume dauerhaft gespeichert wird. Die Umgebungsvariable ist einfach eine praktische Lösung, falls Ihre App einen Verweis auf eine bestimmte Datei innerhalb des Volumes benötigt.

Sie haben auch die Möglichkeit, einen Speicherort zum Herunterladen der Volumebereitstellung auf Ihren Entwicklungscomputer anzugeben, anstatt ein temporäres Verzeichnis zu verwenden. Geben Sie unter *volumeMounts* für jeden Speicherort einen Wert für *name* und *localPath* an. *name* ist der Volumename, der abgeglichen werden soll, und *localPath* ist der absolute Pfad auf Ihrem Entwicklungscomputer. Zum Beispiel:

```yaml
version: 0.1
volumeMounts:
  - name: default-token-*
    localPath: /var/run/secrets/kubernetes.io/serviceaccount
env:
  - name: KUBERNETES_IN_CLUSTER_CONFIG_OVERRIDE
    value: $(volumeMounts:default-token-*)
```

Das obige Beispiel verwendet den Eintrag in *env*, um ein Volume herunterladen, das mit *default-token-\** übereinstimmt, wie z. B *default-token-1111* oder *default-token-1234-5678-90abcdef*. In Fällen, in denen mehrere Volumes übereinstimmen, wird die erste Übereinstimmung verwendet. Alle Dateien werden unter Verwendung des Eintrags *volumeMounts* in den Pfad `/var/run/secrets/kubernetes.io/serviceaccount` auf Ihrem Entwicklungscomputer heruntergeladen. Die Umgebungsvariable *KUBERNETES_IN_CLUSTER_CONFIG_OVERRIDE* ist auf `/var/run/secrets/kubernetes.io/serviceaccount` festgelegt.

## <a name="make-a-service-available"></a>Verfügbarmachen eines Diensts

Geben Sie unter *env* einen Wert für *name* und *value* für jeden Dienst an, den Sie auf Ihrem Entwicklungscomputer verfügbar machen möchten. *name* ist die Umgebungsvariable, die auf Ihrem Entwicklungscomputer verwendet wird. *value* gibt den Namen des Diensts aus Ihrem Cluster und einen Pfad an. Der Wert für *value* weist das Format *$(services:SERVICE_NAME)/PATH* auf.

Zum Beispiel:

```yaml
version: 0.1
env:
  - name: MYAPP1_SERVICE_HOST
    value: $(services:myapp1)/api/v1/
```

Das obige Beispiel macht den Dienst *myapp1* für Ihren Entwicklungscomputer verfügbar, und die Umgebungsvariable *MYAPP1_SERVICE_HOST* ist auf die lokale IP-Adresse des Diensts *myapp1* mit dem Pfad `/api/v1` festgelegt, also auf `127.1.1.4/api/v1`. Auf den Dienst *myapp1* kann über die Umgebungsvariable, *myapp1* oder *myapp1.svc.cluster.local* zugegriffen werden.

> [!NOTE]
> Wenn Sie einen Dienst auf Ihrem Entwicklungscomputer verfügbar machen, wird unabhängig von dem von Ihnen festgelegten Pfad der gesamte Dienst verfügbar. Der Pfad wird nur verwendet, um die Umgebungsvariable festzulegen, die auf dem Entwicklungscomputer verwendet werden soll.
Mit *$(services:SERVICE_NAME.NAMESPACE_NAME)* können Sie auch einen Dienst aus einem bestimmten Kubernetes-Namespace verfügbar machen. Zum Beispiel:

```yaml
version: 0.1
env:
  - name: MYAPP2_SERVICE_HOST
    value: $(services:myapp2.mynamespace)
```

Das obige Beispiel macht *myapp2* aus dem Namespace *mynamespace* auf Ihrem Entwicklungscomputer verfügbar und legt die Umgebungsvariable *MYAPP2_SERVICE_HOST* auf die lokale IP-Adresse von *myapp2* aus dem Namespace *mynamespace* fest.

## <a name="create-an-environment-variable-with-a-constant-value"></a>Erstellen einer Umgebungsvariable mit einem konstanten Wert

Geben Sie unter *env* einen Wert für *name* und *value* für jede Umgebungsvariable an, die Sie auf Ihrem Entwicklungscomputer erstellen möchten. *name* ist die Umgebungsvariable, die auf Ihrem Entwicklungscomputer verwendet wird, und *value* ist der Wert. Zum Beispiel:

```yaml
version: 0.1
env:
  - name: DEBUG_MODE
    value: "true"
```

Das obige Beispiel erstellt eine Umgebungsvariable namens *DEBUG_MODE* mit dem Wert *true*.

## <a name="example-kuberneteslocalprocessconfigyaml"></a>KubernetesLocalProcessConfig.yaml-Beispieldatei

Hier sehen Sie ein Beispiel einer vollständigen `KubernetesLocalProcessConfig.yaml`-Datei:

```yaml
version: 0.1
volumeMounts:
  - name: default-token-*
    localPath: /var/run/secrets/kubernetes.io/serviceaccount
env:
  - name: KUBERNETES_IN_CLUSTER_CONFIG_OVERRIDE
    value: $(volumeMounts:default-token-*)
  - name: ALLOW_LIST_PATH
    value: $(volumeMounts:allow-list)/allow-list
  - name: MYAPP1_SERVICE_HOST
    value: $(services:myapp1)/api/v1/
  - name: MYAPP2_SERVICE_HOST
    value: $(services:myapp2.mynamespace)
  - name: DEBUG_MODE 
    value: "true"
```

## <a name="next-steps"></a>Nächste Schritte

Wenn Sie mit der Verwendung von Bridge to Kubernetes beginnen möchten, um Ihren lokalen Entwicklungscomputer mit Ihrem Cluster zu verbinden, finden Sie unter [Verwenden von Bridge to Kubernetes mit Visual Studio Code][bridge-to-kubernetes-vs-code] und [Verwenden von Bridge to Kubernetes mit Visual Studio][bridge-to-kubernetes-vs] weitere Informationen.

[bridge-to-kubernetes-vs-code]: https://code.visualstudio.com/docs/containers/bridge-to-kubernetes
[bridge-to-kubernetes-vs]: bridge-to-kubernetes.md
