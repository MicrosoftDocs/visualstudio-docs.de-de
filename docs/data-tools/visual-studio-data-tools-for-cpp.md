---
title: Datentools für C++
description: Machen Sie sich mit Visual Studio-Datentools für C++ vertraut. Stellen Sie über ODBC und SQL Native Client von einer C++-Anwendung aus eine Verbindung mit LocalDB her.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
dev_langs:
- CPP
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
- cplusplus
ms.openlocfilehash: 4cf316e0d892e8c6ba229a7a46ee0439797d032f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866345"
---
# <a name="visual-studio-data-tools-for-c"></a>Visual Studio-Datentools für C++

Native C++-Anwendungen bieten beim Zugreifen auf Datenquellen häufig die beste Leistungsfähigkeit. Datentools für C++-Anwendungen in Visual Studio sind jedoch nicht so umfangreich wie für .NET-Anwendungen. Beispielsweise kann das Fenster **Datenquellen** nicht zum Ziehen und Ablegen von Datenquellen auf eine C++-Entwurfsoberfläche verwendet werden. Wenn Sie eine objektrelationale Ebene benötigen, müssen Sie Ihre eigene Ebene erstellen oder ein Produkt von einem Drittanbieter verwenden. Das Gleiche gilt für Datenbindungsfunktionen, obwohl Anwendungen, die die Microsoft Foundation Class-Bibliothek verwenden, einige Datenbankklassen zusammen mit Dokumenten und Ansichten verwenden können, um Daten im Arbeitsspeicher zu speichern und für den Benutzer anzuzeigen. Weitere Informationen finden Sie unter [Datenzugriff in Visual C++](/cpp/data/data-access-in-cpp).

Native C++-Anwendungen können die im Lieferumfang von Windows enthaltenen ODBC- und OLE DB-Treiber sowie den ADO-Anbieter verwenden, um eine Verbindung mit SQL-Datenbanken herzustellen. Diese können eine Verbindung mit jeder Datenbank herstellen, die diese Schnittstellen unterstützt. Der ODBC-Treiber ist der Standardtreiber. OLE DB wird zu Zwecken der Abwärtskompatibilität bereitgestellt. Weitere Informationen zu diesen Datentechnologien finden Sie unter [Windows Data Access Components](/previous-versions/windows/desktop/ms692897(v=vs.85)).

Verwenden Sie [SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client), um die benutzerdefinierte Funktionalität in SQL Server 2005 und höher zu nutzen. Der native Client enthält auch den SQL Server-ODBC-Treiber und den SQL Server-OLE DB-Anbieter in einer Dynamic Link Library (DLL). Diese unterstützen Anwendungen mithilfe von APIs mit nativem Code (ODBC, OLE DB und ADO) für Microsoft SQL Server. SQL Server Native Client wird mit SQL Server-Datentools installiert. Das Programmierhandbuch finden Sie hier: [Programmierung für SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client-programming).

## <a name="to-connect-to-localdb-through-odbc-and-sql-native-client-from-a-c-application"></a>Herstellen einer Verbindung zwischen einer C++-Anwendung und LocalDB über ODBC und SQL Server Native Client

1. Installieren Sie SQL Server Data Tools.

2. Wenn Sie eine SQL-Beispieldatenbank für die Verbindung benötigen, laden Sie die Northwind-Datenbank herunter, und entpacken Sie sie an einem neuen Speicherort.

3. Verwenden Sie SQL Server Management Studio, um die entpackte *Northwind.mdf*-Datei an LocalDB anzufügen. Wenn SQL Server Management Studio gestartet wird, stellen Sie eine Verbindung mit „(localdb)\MSSQLLocalDB“ her.

   ![SSMS-Dialogfeld „Mit Server verbinden“](../data-tools/media/raddata-ssms-connect-dialog.png)

   Klicken Sie dann im linken Bereich mit der rechten Maustaste auf den LocalDB-Knoten und dann auf **Anfügen**.

   ![SSMS-Dialogfeld „Anfügen“ zum Anfügen der Datenbank](../data-tools/media/raddata-ssms-attach-database.png)

4. Laden Sie das ODBC-Windows SDK-Beispiel herunter, und entpacken Sie es an einem neuen Speicherort. Dieses Beispiel zeigt die grundlegenden ODBC-Befehle, die verwendet werden, um eine Verbindung mit einer Datenbank herzustellen und Abfragen und Befehle auszugeben. Weitere Informationen zu diesen Funktionen finden Sie unter [Microsoft Open Database Connectivity (ODBC)](/sql/odbc/microsoft-open-database-connectivity-odbc). Wenn Sie die Lösung zum ersten Mal laden (diese befindet sich im C++-Ordner), bietet Visual Studio ein Upgrade der Lösung auf die aktuelle Version von Visual Studio an. Klicken Sie auf **Ja**.

5. Damit Sie den nativen Client verwenden können, benötigen Sie dessen *Header*- und *Bibliotheksdatei*. Diese Dateien enthalten Funktionen und Definitionen, die für SQL Server spezifisch sind und über die in sql.h definierten ODBC-Funktionen hinausgehen. Fügen Sie unter **Projekt** > **Eigenschaften** > **VC++-Verzeichnisse** das folgende Includeverzeichnis ein:

   **%ProgramFiles%\Microsoft SQL Server\110\SDK\Include**

   Fügen Sie auch dieses Bibliotheksverzeichnis hinzu:

   **%ProgramFiles%\Microsoft SQL Server\110\SDK\Lib**

6. Fügen Sie diese Zeilen in *odbcsql.cpp* hinzu. Mit #define wird verhindert, dass irrelevante OLE DB-Definitionen kompiliert werden.

   ```cpp
   #define _SQLNCLI_ODBC_
   #include <sqlncli.h>
   ```

    Beachten Sie, dass im Beispiel tatsächlich keine nativen Clientfunktionen verwendet werden, sodass die vorangehenden Schritte für die Kompilierung und Ausführung nicht erforderlich sind. Das Projekt ist nun jedoch so konfiguriert, dass Sie diese Funktion verwenden können. Weitere Informationen finden Sie unter [SQL Server Native Client-Programmierung](/sql/relational-databases/native-client/sql-server-native-client).

7. Geben Sie an, welcher Treiber im ODBC-Subsystem verwendet werden soll. Im Beispiel wird das DRIVER-Verbindungszeichenfolgenattribut als Befehlszeilenargument übergeben. Fügen Sie unter **Projekt** > **Eigenschaften** > **Debuggen** dieses Befehlszeilenargument hinzu:

   ```cpp
   DRIVER="SQL Server Native Client 11.0"
   ```

8. Drücken Sie **F5**, um die Anwendung zu erstellen und auszuführen. Es sollte ein Dialogfeld des Treibers angezeigt werden, in dem Sie aufgefordert werden, eine Datenbank einzugeben. Geben Sie `(localdb)\MSSQLLocalDB` ein, und aktivieren Sie **Vertrauenswürdige Verbindung verwenden**. Klicken Sie auf **OK**. Es sollte eine Konsole mit Meldungen angezeigt werden, die auf eine erfolgreiche Verbindung hinweisen. Außerdem sollte eine Eingabeaufforderung angezeigt werden, in der Sie eine SQL-Anweisung eingeben können. Der folgende Bildschirm zeigt eine Beispielabfrage und die Ergebnisse:

   ![Ausgabe der ODBC-Beispielabfrage](../data-tools/media/raddata-odbc-sample-query-output.png)

## <a name="see-also"></a>Weitere Informationen

- [Zugreifen auf Daten in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
