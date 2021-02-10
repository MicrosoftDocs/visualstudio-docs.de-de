---
title: Richtlinien für die Entwicklercommunity
description: Dieser Artikel enthält einen Leitfaden für die Arbeit mit der Visual Studio-Entwicklercommunity.
ms.date: 6/30/2020
ms.topic: conceptual
author: madskristensen
ms.author: madsk
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0722716b086877d5522b9ef8fae79976fbdb0805
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894672"
---
# <a name="developer-community-guidelines"></a>Richtlinien für die Entwicklercommunity

Die Entwicklercommunity verfolgt Issues und Featurevorschläge für Visual Studio.

## <a name="submitting-problems-and-suggestions"></a>Erstellen von Issues und Vorschlägen

Die [Visual Studio-Entwicklercommunity](https://aka.ms/feedback/suggest?space=8) verfolgt Issues und Featurevorschläge für Visual Studio.

### <a name="before-submitting-an-issue"></a>Vor der Erstellung eines Issues

Suchen Sie in der Visual Studio-Entwicklercommunity nach Ihrem Issue, um sicherzustellen, dass es nicht bereits vorhanden ist. Wenn Sie feststellen, dass Ihr Issue bereits vorhanden ist, schreiben Sie einen relevanten Kommentar, und stimmen Sie ab.

Wenn Ihr Issue eine Frage ist, fragen Sie die [Stack Overflow](https://stackoverflow.com/questions/tagged/visual-studio?tab=Newest)-Community, indem Sie das Tag _visual-studio_ verwenden. Mitarbeiter unseres Kundensupports überwachen dieses Tag und helfen bei der Beantwortung der Fragen.

Wenn Ihr Fehler oder Vorschlag in keinem vorhandenen Issue beschrieben wird, erstellen Sie anhand des nachfolgenden Leitfadens ein Issue.

### <a name="writing-a-good-bug-report-or-feature-suggestion"></a>Schreiben eines guten Fehlerberichts bzw. Featurevorschlags

- Nehmen Sie in Ihr Issue immer nur ein Problem oder einen Featurevorschlag auf.

  - Das Aufnehmen mehrerer Probleme oder Featureanfragen in ein einzelnes Issue erschwert uns die Diagnose und anderen Benutzern das Abstimmen für Ihr Issue.
  - Sofern es sich nicht um die identische Eingabe handelt, fügen Sie Ihr Issue nicht als Kommentar zu einem vorhandenen Issue hinzu. Viele Issues erscheinen ähnlich, haben aber unterschiedliche Ursachen. Dies erschwert uns die Diagnose Ihres Issues.

- Je mehr Informationen Sie bereitstellen können, desto einfacher wird es für uns, den Fehler zu reproduzieren und zu beheben.
- Ihr Issue sollte Folgendes enthalten:

  - Reproduzierbare Schritte (1... 2... 3...) sowie das erwartete und das tatsächliche Ergebnis
  - Bilder, Animationen oder ein Link zu einem Video: Bilder und Animationen veranschaulichen die reproduzierbaren Schritte, ersetzen diese jedoch _nicht_.
  - Gegebenenfalls einen Codeausschnitt, in dem das Problem veranschaulicht wird, oder einen Link zu einem Coderepository, das wir einfach auf unserem Computer verwenden können, um den Fehler zu reproduzieren

- Vergessen Sie nicht, die folgenden Schritte durchzuführen:

  - Suchen Sie nach einem möglicherweise vorhandenen Duplikat. Falls ein solches vorhanden ist, stimmen Sie für das bestehende Issue ab, und fügen Sie ggf. zusätzliche Kommentare oder Erläuterungen hinzu.
  - Reproduzieren Sie den Fehler, nachdem Sie alle Erweiterungen deaktiviert haben. Wenn Sie herausfinden, dass der Fehler durch eine Erweiterung verursacht wird, die Sie installiert haben, erstellen Sie für die entsprechende Erweiterung ein Issue.
  - Vereinfachen Sie Ihren Code rund um den Fehler, sodass wir diesen besser isolieren können.

Selbst bei Issues mit ausführlichen Informationen kann es vorkommen, dass wir den Fehler nicht reproduzieren können und nach weiteren Informationen fragen.

## <a name="managing-problem-reports"></a>Verwalten von Problemberichten

Das Selektieren eines Issues ist ein mehrstufiger Prozess, der innerhalb des Featureteams gemeinsam durchgeführt wird. Die Selektierung dauert in der Regel eine Woche, kann aber auch länger dauern. Das Ziel der Selektierung ist es, Ihnen deutlich zu erläutern, was mit Ihrem Issue geschieht. Nach der Selektierung wissen Sie beispielsweise, ob wir planen, Ihr Issue zu beheben, oder auf weiteres Feedback aus der Community warten.

Nachdem Sie ein Problem gemeldet haben, wird durch einen Status angegeben, wo sich Ihre Übermittlung in ihrem Lebenszyklus gerade befindet. Wenn sich die Visual Studio-Produktteams Ihr Feedback ansehen, wird es mit einem geeigneten Status versehen. Verfolgen Sie den Status Ihrer Problemberichte unter Bezugnahme auf den [Problemstatus und die häufig gestellten Fragen](./report-a-problem.md).

### <a name="prioritizing-which-issues-to-fix"></a>Priorisieren zu behebender Probleme

Es können nicht alle gemeldeten Probleme behoben werden. Einige sind zu aufwändig oder könnten andere Funktionsbereiche beeinträchtigen, während wieder andere nur geringe Auswirkungen haben. Dies kann natürlich enttäuschend sein, wenn Sie sich die Zeit genommen haben, einen Problembericht zu senden. Jeder war schon einmal in einer solchen Situation, entweder im Zusammenhang mit diesem oder einem anderen Projekt. Wenn ein Problem geschlossen wurde und Sie der Meinung sind, dass der angegebene Grund nicht zufriedenstellend ist, können Sie Ihren Anwendungsfall noch genauer beschreiben und anfordern, dass das Problem im Rahmen einer wiederholten Untersuchung reaktiviert wird. An diesem Punkt werden Sie möglicherweise aufgefordert, weitere Informationen bereitzustellen.

### <a name="missing-important-information"></a>Fehlende wichtige Informationen

Wenn bei einem Issue wichtige Informationen fehlen, weisen wir den Status _Needs More Info_ (Mehr Info nötig) zu. Wir schreiben einen Kommentar zum Issue mit den genauen erforderlichen Informationen, und Sie erhalten eine Benachrichtigung per E-Mail. Wenn wir die Informationen nicht innerhalb von sieben Tagen erhalten, schicken wir Ihnen eine Erinnerung. Nach weiteren 14 Tagen ohne Aktivität schließen wir das Ticket.

### <a name="other-product"></a>Anderes Produkt

Manchmal stellt sich bei einem gemeldeten Issue heraus, dass die Ursache bei einem anderen Produkt als Visual Studio liegt. Dies könnte beispielsweise eine andere verwandte Anwendung oder eine Erweiterung sein. 

In einem solchen Fall schließen wir das Issue und bitten Sie, es für das andere Produkt zu erstellen. Im Folgenden finden Sie einige bekannte Seiten für die Erstellung von Issues:

* [SQL Server](https://feedback.azure.com/forums/908035-sql-server)
* [Support für Visual Studio Subscription](https://feedback.azure.com/forums/908035-sql-server)
* [Office](https://support.office.com/article/how-do-i-give-feedback-on-microsoft-office-2b102d44-b43f-4dd2-9ff4-23cf144cfb11)
* [Windows](https://support.microsoft.com/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app)

#### <a name="additional-information"></a>Zusätzliche Informationen

- [Erhöhen der Wahrscheinlichkeit der Behebung eines Leistungsproblems](./how-to-increase-chances-of-performance-issue-being-fixed.md)
- [Behandeln von MSBuild-Problemen und Erstellen von Protokollen](./msbuild-logs.md)

## <a name="managing-feature-suggestions"></a>Verwalten von Featurevorschlägen

Featurevorschläge sind ein Mittel der Kommunikation zwischen uns und den Mitgliedern der Entwicklercommunity. Theoretisch könnten wir alle Featureanfragen unbegrenzt offen lassen. Würden wir die Issues jedoch offen lassen, würde dies den Einblick der Community in den jeweiligen Status eines Features einschränken. Daher schließen wir Featureanfragen, die wir nicht umsetzen werden. Features, die möglicherweise umgesetzt werden, versehen wir mit dem Status _In Bearbeitung_.

Wenn Sie ein Feature vorschlagen, sind Sie möglicherweise enttäuscht, dass wir nicht planen, Ihren Vorschlag umzusetzen. Das verstehen wir natürlich. Wir alle haben dies schon einmal erlebt – entweder in diesem Projekt oder in anderen, an denen wir mitgearbeitet haben. Daher können Sie sicher sein, dass wir alle Beiträge sehr schätzen. Nehmen Sie es nicht persönlich, wenn wir Ihren Vorschlag schließen oder diesen mit dem Status _In Bearbeitung_ versehen. Wenn Sie der Meinung sind, dass Ihr Featurevorschlag offen bleiben sollte, verdeutlichen Sie den Anwendungsfall, und kontaktieren Sie uns, oder sammeln Sie mehr Stimmen.

Folgendes beeinflusst unseren Entscheidungsfindungsprozess in Bezug auf Featurevorschläge:

- Entspricht er der allgemeinen Produktrichtung?
- Können wir uns die Erstellung und Verwaltung leisten?
- Passt es zu unserer Gesamt-[Roadmap](/visualstudio/productinfo/vs-roadmap)-Strategie?
- Findet es Unterstützung in der Community, worauf die Stimmen und Kommentare hindeuten?
- Gefällt uns der Vorschlag richtig gut, obwohl die Unterstützung in der Community eher gering ausfällt?

Wenn wir keine dieser Fragen mit „Ja“ beantworten können, schließen wir die Anfrage. In vielen Fällen bleibt der Vorschlag jedoch mit dem Status _In Bearbeitung_ offen, um mehr Feedback von der Community zu sammeln.

Wenn ein Vorschlag nicht mit unserer allgemeinen Produktrichtung übereinstimmt, schließen wir ihn als *Außerhalb des gültigen Bereichs*. Beispielsweise haben wir möglicherweise ähnliche Investitionen in andere Elemente der Visual Studio-Produktfamilie getätigt. Oder das vorgeschlagene Feature könnte nur für einige wenige Personen relevant sein, weshalb dafür eine Erweiterung besser geeignet ist.

Verfolgen Sie den Status Ihres Featurevorschlags unter Bezugnahme auf den [Status und die häufig gestellten Fragen](./report-a-problem.md).

## <a name="discussion-etiquette"></a>Diskussionsregeln

Damit die Konversation klar und transparent bleibt, diskutieren Sie bitte nur auf Englisch, und weichen Sie nicht vom Thema ab. Nehmen Sie Rücksicht auf Andere, und bleiben Sie stets höflich und professionell.

Weitere Informationen finden Sie unter [Verhaltensregeln für Microsoft Community](https://answers.microsoft.com/en-us/page/codeofconduct).

Jeglicher Verstoß gegen die Diskussionsregeln kann dazu führen, dass der Kommentar gelöscht und der Benutzer letztlich gesperrt wird.

## <a name="data-privacy"></a>Datenschutz

Kommentare und Antworten sind öffentlich sichtbar. Angefügte Dateien werden jedoch nur privat mit Microsoft geteilt. Diese Sichtbarkeit ist ein Vorteil, da die gesamte Community Einblick in die Probleme und die gefundenen Lösungen anderer Benutzer hat. Wenn Sie um den Schutz Ihrer Daten oder Ihrer Identität besorgt sind, haben wir Tipps für Sie. Weitere Informationen dazu finden Sie unter [Datenschutz in der Entwicklercommunity](./developer-community-privacy.md).

## <a name="next-steps"></a>Nächste Schritte

Wechseln Sie zur [Visual Studio-Entwicklercommunity](https://aka.ms/feedback/suggest?space=8), um Probleme zu melden, Features vorzuschlagen oder sich die vorhandenen Tickets durchzulesen. Viel Erfolg!
