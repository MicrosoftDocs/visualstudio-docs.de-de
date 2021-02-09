---
title: Aktualisieren von MDF-Dateien
description: Überprüfen Sie die Optionen zum Aktualisieren einer Datenbankdatei (. mdf), nachdem Sie eine neuere Version von Visual Studio installiert haben.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- SQL Server Express
- SQL Server LocalDB
- LocalDB
- SQLEXPRESS
- upgrading SQLExpress to SQLExpress
- upgrading to LocalDB
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: cbea7761ed5f36265464f2afe9a64550ddc5e62a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866306"
---
# <a name="upgrade-mdf-files"></a>Aktualisieren von MDF-Dateien

In diesem Thema werden die Optionen zum Aktualisieren einer Datenbankdatei (*. mdf*) nach der Installation einer neueren Version von Visual Studio beschrieben. Es enthält Anweisungen für die folgenden Aufgaben:

- Aktualisieren einer Datenbankdatei auf die Verwendung einer neueren Version von SQL Server Express localdb

- Aktualisieren einer Datenbankdatei auf die Verwendung einer neueren Version von SQL Server Express

- Arbeiten Sie mit einer Datenbankdatei in Visual Studio, behalten Sie jedoch die Kompatibilität mit einer älteren Version von SQL Server Express oder localdb bei

- Erstellen SQL Server Express der Standarddatenbank-Engine

Sie können Visual Studio verwenden, um ein Projekt zu öffnen, das eine Datenbankdatei (*. mdf*) enthält, die mit einer älteren Version von SQL Server Express oder localdb erstellt wurde. Wenn Sie Ihr Projekt jedoch weiterhin in Visual Studio entwickeln möchten, müssen Sie diese Version von SQL Server Express oder localdb auf dem gleichen Computer wie Visual Studio installiert haben, oder Sie müssen ein Upgrade für die Datenbankdatei durchführen. Wenn Sie die Datenbankdatei aktualisieren, können Sie nicht mit älteren Versionen von SQL Server Express oder localdb darauf zugreifen.

Möglicherweise werden Sie auch aufgefordert, eine Datenbankdatei zu aktualisieren, die mit einer früheren Version von SQL Server Express oder localdb erstellt wurde, wenn die Version der Datei nicht mit der Instanz von SQL Server Express oder localdb kompatibel ist, die derzeit installiert ist. Um das Problem zu beheben, werden Sie von Visual Studio aufgefordert, die Datei zu aktualisieren.

> [!IMPORTANT]
> Es wird empfohlen, dass Sie die Datenbankdatei sichern, bevor Sie Sie aktualisieren.

> [!WARNING]
> Wenn Sie ein Upgrade einer *MDF* -Datei durchführen, die in localdb 2014 (V12) 32 Bit auf localdb 2016 (v13) oder höher erstellt wurde, können Sie die Datei nicht erneut in der 32-Bit-Version von localdb öffnen.

Berücksichtigen Sie die folgenden Kriterien, bevor Sie ein Upgrade für eine Datenbank durchführen:

- Aktualisieren Sie nicht, wenn Sie an Ihrem Projekt sowohl in einer älteren Version als auch in einer neueren Version von Visual Studio arbeiten möchten.

- Aktualisieren Sie nicht, wenn Ihre Anwendung in Umgebungen verwendet wird, in denen anstelle von localdb SQL Server Express verwendet wird.

- Aktualisieren Sie nicht, wenn Ihre Anwendung Remote Verbindungen verwendet, da Sie von localdb nicht akzeptiert wird.

- Aktualisieren Sie nicht, wenn Ihre Anwendung auf Internetinformationsdienste (IIS) basiert.

- Sie sollten ein Upgrade durchführen, wenn Sie Datenbankanwendungen in einer Sandkasten Umgebung testen möchten, aber keine Datenbank verwalten möchten.

### <a name="to-upgrade-a-database-file-to-use-the-localdb-version"></a>So aktualisieren Sie eine Datenbankdatei für die Verwendung der localdb-Version

1. Wählen Sie in **Server-Explorer** die Schaltfläche **Verbindung mit Datenbank herstellen** aus.

2. Geben Sie im Dialogfeld **Verbindung hinzufügen** die folgenden Informationen an:

    - **Datenquelle**: `Microsoft SQL Server (SqlClient)`

    - **Servername**:

        - So verwenden Sie die Standardversion: `(localdb)\MSSQLLocalDB` .  Dadurch wird entweder ProjectV12 oder ProjectV13 angegeben, je nachdem, welche Version von Visual Studio installiert ist und wann die erste localdb-Instanz erstellt wurde. Der Knoten **mssqllocaldb** in **SQL Server-Objekt-Explorer** zeigt an, auf welche Version er verweist.

        - Verwenden Sie, um eine bestimmte Version zu verwenden: `(localdb)\ProjectsV12` oder `(localdb)\ProjectsV13` , wobei V12 localdb 2014 und V13 localdb 2016 ist.

    - **Anfügen einer Datenbankdatei**: der physische Pfad der primären *MDF* -Datei.

    - **Logischer Name**: der Name, den Sie mit der Datei verwenden möchten.

3. Klicken Sie auf die Schaltfläche **OK**.

4. Wenn Sie dazu aufgefordert werden, klicken Sie auf die Schaltfläche **Ja** , um die Datei zu aktualisieren.

    Die Datenbank wird aktualisiert, an die localdb-Datenbank-Engine angefügt und ist nicht mehr mit der älteren Version von localdb kompatibel.

Sie können auch eine SQL Server Express Verbindung ändern, um localdb zu verwenden, indem Sie das Kontextmenü für die Verbindung öffnen und dann **Verbindung ändern** auswählen. Ändern Sie im Dialogfeld **Verbindung ändern** den Servernamen in `(LocalDB)\MSSQLLocalDB` . Stellen Sie im Dialogfeld **Erweiterte Eigenschaften** sicher, dass die **Benutzer Instanz** auf **false** festgelegt ist.

### <a name="to-upgrade-a-database-file-to-use-the-sql-server-express-version"></a>So aktualisieren Sie eine Datenbankdatei für die Verwendung der SQL Server Express Version

1. Wählen Sie im Kontextmenü für die Verbindung mit der Datenbank **Verbindung ändern** aus.

2. Klicken Sie im Dialogfeld **Verbindung ändern** auf die Schaltfläche **erweitert** .

3. Wählen Sie im Dialogfeld **Erweiterte Eigenschaften** die Schaltfläche **OK** aus, ohne den Servernamen zu ändern.

    Die Datenbankdatei wird entsprechend der aktuellen Version von SQL Server Express aktualisiert.

### <a name="to-work-with-the-database-in-visual-studio-but-retain-compatibility-with-sql-server-express"></a>So arbeiten Sie in Visual Studio mit der Datenbank, behalten jedoch die Kompatibilität mit SQL Server Express bei

- Öffnen Sie in Visual Studio das Projekt, ohne es zu aktualisieren.

  - Drücken Sie die Taste **F5** , um das Projekt auszuführen.

  - Um die Datenbank zu bearbeiten, öffnen Sie die *MDF* -Datei in **Projektmappen-Explorer**, und erweitern Sie den Knoten in **Server-Explorer** , um mit der Datenbank zu arbeiten.

### <a name="to-make-sql-server-express-the-default-database-engine"></a>So erstellen Sie SQL Server Express der Standarddatenbank-Engine

1. Wählen Sie in der Menüleiste **Tools** > **Optionen** aus.

2. Erweitern Sie im Dialogfeld **Optionen** die Optionen **Daten Bank Tools** , und wählen Sie dann **Datenverbindungen** aus.

3. Geben Sie im Textfeld **SQL Server Instanzname** den Namen der Instanz von SQL Server Express oder localdb an, die Sie verwenden möchten. Wenn die-Instanz nicht benannt ist, geben Sie an `.\SQLEXPRESS or (LocalDB)\MSSQLLocalDB` .

4. Klicken Sie auf die Schaltfläche **OK**.

    SQL Server Express ist die Standarddatenbank-Engine für Ihre Anwendungen.

## <a name="see-also"></a>Weitere Informationen

- [Zugreifen auf Daten in Visual Studio](accessing-data-in-visual-studio.md)
