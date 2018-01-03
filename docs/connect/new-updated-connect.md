---
title: Aggiornato - connettersi a documenti di SQL Server | Documenti Microsoft
description: Visualizzare i frammenti di contenuto aggiornato per la documentazione modificato di recente in, per connettersi a Microsoft SQL Server.
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: 
ms.suite: sql
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.topic: article
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 12/02/2017
ms.author: genemi
ms.workload: connect-to-sql
ms.openlocfilehash: d8fb5f5cfbd94cc9d2bd86c4dfe1cbc15bc68d34
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="new-and-recently-updated-connect-to-sql-server"></a>Nuovi e aggiornati: connettersi a SQL Server



Microsoft aggiorna quasi quotidianamente alcuni degli articoli presenti nel sito Web della documentazione [Docs.Microsoft.com](http://docs.microsoft.com/). Questo articolo contiene estratti degli articoli aggiornati di recente. Possono essere indicati anche collegamenti a nuovi articoli.

Questo articolo è generato da un programma che viene rieseguito periodicamente. In alcuni casi un estratto può avere una formattazione imperfetta o essere visualizzato come markdown dell'articolo di origine. Qui le immagini non vengono mai visualizzate.

Sono riportati gli aggiornamenti recenti per l'intervallo di date e l'area di interesse seguenti:



- *Intervallo di date degli aggiornamenti:* &nbsp; **28/09/2017** &nbsp; - &nbsp; **02/12/2017**
- *Area di interesse:* &nbsp; **Connetti al Server SQL**.




&nbsp;

## <a name="new-articles-created-recently"></a>Nuovi articoli creati di recente

I collegamenti seguenti consentono di visualizzare nuovi articoli aggiunti di recente.


1. [Schermata di creazione guidata origine dati 1](odbc/windows/dsn-wizard-1.md)
2. [Schermata di creazione guidata origine dati 2](odbc/windows/dsn-wizard-2.md)
3. [Schermata di creazione guidata origine dati 3](odbc/windows/dsn-wizard-3.md)
4. [Schermata di creazione guidata origine dati 4](odbc/windows/dsn-wizard-4.md)
5. [Finestra di dialogo account di accesso SQL Server (ODBC)](odbc/windows/sql-server-login-dialog.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articoli aggiornati con estratti

In questa sezione sono visualizzati gli estratti degli aggiornamenti raccolti dagli articoli che recentemente sono stati sottoposti a un aggiornamento di grande entità.

Gli estratti visualizzati qui sono separati dal relativo contesto semantico. Inoltre è possibile che un estratto sia talvolta separato da importanti elementi di sintassi markdown che lo circondano nell'articolo vero e proprio. Di conseguenza, questi estratti devono essere usati solo come indicazioni generali. Gli estratti consentono solo di comprendere se sia utile o meno consultare l'articolo completo.

Per queste e altre ragioni, non copiare codice da questi estratti e non prendere come verità assoluta ciò che si legge negli estratti. Consultare gli articoli completi.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Elenco compatto degli articoli aggiornati di recente

Questo elenco compatto include i collegamenti a tutti gli articoli aggiornati elencati nella sezione degli estratti.

1. [PDOStatement::bindParam](#TitleNum_1)
2. [PDOStatement::bindValue](#TitleNum_2)
3. [sqlsrv_prepare](#TitleNum_3)
4. [sqlsrv_query](#TitleNum_4)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-pdostatementbindparamphppdostatement-bindparammd"></a>1. &nbsp;[Pdostatement:: Bindparam](php/pdostatement-bindparam.md)

*Ultimo aggiornamento: 2017-10-25* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Avanti](#TitleNum_2))

<!-- Source markdown line 119.  ms.author= "genemi".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 2792d149331f5326f6914721c86687d545685488 e363544e2c6f73277b7f2ca05b9269a4139d1fac  (PR=3663  ,  Filename=pdostatement-bindparam.md  ,  Dirpath=docs\connect\php\  ,  MergeCommitSha40=e9caa51a68c2f03fb9f3a0354b5eab1eed43bdf1) -->



> [!NOTE]
> È consigliabile utilizzare le stringhe come input durante l'associazione di valori da un [colonna decimal o numeric](https://docs.microsoft.com/en-us/sql/t-sql/data-types/decimal-and-numeric-transact-sql) per garantire la precisione e l'accuratezza PHP limitate precisione per [numeri a virgola mobile](http://php.net/manual/en/language.types.float.php).

**Esempio**

In questo esempio di codice viene illustrato come associare un valore decimale come parametro di input.

```php
<?php
$database = "Test";
$server = "(local)";
$conn = new PDO("sqlsrv:server=$server ; Database = $database", "", "");

// Assume TestTable exists with a decimal field
$input = 9223372036854.80000;
$stmt = $conn->prepare("INSERT INTO TestTable (DecimalCol) VALUES (?)");
// by default it is PDO::PARAM_STR, rounding of a large input value may
// occur if PDO::PARAM_INT is specified
$stmt->bindParam(1, $input, PDO::PARAM_STR);
$stmt->execute();
```




&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-pdostatementbindvaluephppdostatement-bindvaluemd"></a>2. &nbsp;[PDOStatement::bindValue](php/pdostatement-bindvalue.md)

*Ultimo aggiornamento: 2017-10-25* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([precedente](#TitleNum_1) | [Avanti](#TitleNum_3))

<!-- Source markdown line 77.  ms.author= "genemi".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 c1d5ff4d5bfdbfbf1635cf14d71b4d583164075a 6cd5fc88860ae9ffca25ee15e8eeaeba29991fda  (PR=3663  ,  Filename=pdostatement-bindvalue.md  ,  Dirpath=docs\connect\php\  ,  MergeCommitSha40=e9caa51a68c2f03fb9f3a0354b5eab1eed43bdf1) -->



> [!NOTE]
> È consigliabile utilizzare le stringhe come input durante l'associazione di valori da un [colonna decimal o numeric](https://docs.microsoft.com/en-us/sql/t-sql/data-types/decimal-and-numeric-transact-sql) per garantire la precisione e l'accuratezza PHP limitate precisione per [numeri a virgola mobile](http://php.net/manual/en/language.types.float.php).

**Esempio**

In questo esempio di codice viene illustrato come associare un valore decimale come parametro di input.

```php
<?php
$database = "Test";
$server = "(local)";
$conn = new PDO("sqlsrv:server=$server ; Database = $database", "", "");

// Assume TestTable exists with a decimal field
$input = 9223372036854.80000;
$stmt = $conn->prepare("INSERT INTO TestTable (DecimalCol) VALUES (?)");
// by default it is PDO::PARAM_STR, rounding of a large input value may
// occur if PDO::PARAM_INT is specified
$stmt->bindValue(1, $input, PDO::PARAM_STR);
$stmt->execute();
```



&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-sqlsrvpreparephpsqlsrv-preparemd"></a>3. &nbsp; [sqlsrv_prepare](php/sqlsrv-prepare.md)

*Ultimo aggiornamento: 2017-10-25* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([precedente](#TitleNum_2) | [Avanti](#TitleNum_4))

<!-- Source markdown line 219.  ms.author= "genemi".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 7811e459efec90ef79340375d5fb34364130466b 3d28b3d320dc7fe5df12300da5cb9579abf6839a  (PR=3663  ,  Filename=sqlsrv-prepare.md  ,  Dirpath=docs\connect\php\  ,  MergeCommitSha40=e9caa51a68c2f03fb9f3a0354b5eab1eed43bdf1) -->



> [!NOTE]
> È consigliabile utilizzare le stringhe come input durante l'associazione di valori da un [colonna decimal o numeric](https://docs.microsoft.com/en-us/sql/t-sql/data-types/decimal-and-numeric-transact-sql) per garantire la precisione e l'accuratezza PHP limitate precisione per [numeri a virgola mobile](http://php.net/manual/en/language.types.float.php).

**Esempio**

In questo esempio di codice viene illustrato come associare un valore decimale come parametro di input.

```php
<?php
$serverName = "(local)";
$connectionInfo = array("Database"=>"YourTestDB");
$conn = sqlsrv_connect($serverName, $connectionInfo);
if ($conn === false) {
    echo "Could not connect.\n";
    die(print_r(sqlsrv_errors(), true));
}

// Assume TestTable exists with a decimal field
$input = "9223372036854.80000";
$params = array($input);
$stmt = sqlsrv_prepare($conn, "INSERT INTO TestTable (DecimalCol) VALUES (?)", $params);
sqlsrv_execute($stmt);

sqlsrv_free_stmt($stmt);
sqlsrv_close($conn);

?>
```



&nbsp;

&nbsp;

---

<a name="TitleNum_4"/>

### <a name="4-nbsp-sqlsrvqueryphpsqlsrv-querymd"></a>4. &nbsp; [sqlsrv_query](php/sqlsrv-query.md)

*Ultimo aggiornamento: 2017-10-25* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([precedente](#TitleNum_3))

<!-- Source markdown line 163.  ms.author= "genemi".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 07a84878c07af0b6ad7e247337be5b4567ce03c3 127af26a8a054a45dda51d90f43f08652949ba18  (PR=3663  ,  Filename=sqlsrv-query.md  ,  Dirpath=docs\connect\php\  ,  MergeCommitSha40=e9caa51a68c2f03fb9f3a0354b5eab1eed43bdf1) -->



> [!NOTE]
> È consigliabile utilizzare le stringhe come input durante l'associazione di valori da un [colonna decimal o numeric](https://docs.microsoft.com/en-us/sql/t-sql/data-types/decimal-and-numeric-transact-sql) per garantire la precisione e l'accuratezza PHP limitate precisione per [numeri a virgola mobile](http://php.net/manual/en/language.types.float.php).

**Esempio**

In questo esempio di codice viene illustrato come associare un valore decimale come parametro di input.

```php
<?php
$serverName = "(local)";
$connectionInfo = array("Database"=>"YourTestDB");
$conn = sqlsrv_connect($serverName, $connectionInfo);
if ($conn === false) {
     echo "Could not connect.\n";
     die(print_r(sqlsrv_errors(), true));
}

// Assume TestTable exists with a decimal field
$input = "9223372036854.80000";
$params = array($input);
$stmt = sqlsrv_query($conn, "INSERT INTO TestTable (DecimalCol) VALUES (?)", $params);

sqlsrv_free_stmt($stmt);
sqlsrv_close($conn);

?>
```








## <a name="similar-articles"></a>Articoli simili

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
    2017-12-02  23:00pm
-->

In questa sezione sono elencati articoli molto simili ad articoli aggiornati di recente in altre aree di interesse all'interno del repository GitHub pubblico di Microsoft: [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>Aree di interesse con articoli nuovi o aggiornati di recente

- [Nuovo + aggiornato (3+14): documentazione di **Advanced Analytics per SQL**](../advanced-analytics/new-updated-advanced-analytics.md)
- [Nuovo + aggiornato (1+0): **Analysis Services for SQL (Analysis Services per SQL)** Docs](../analysis-services/new-updated-analysis-services.md)
- [Nuovo + aggiornato (87+0): documentazione della **piattaforma di strumenti analitici per SQL**](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [Nuovo + aggiornato (5+4): documentazione della **connessione a SQL Server**](../connect/new-updated-connect.md)
- [Nuovo + aggiornato (0+1): documentazione del **motore di database di SQL Server**](../database-engine/new-updated-database-engine.md)
- [Nuovo + aggiornato (2+2): documentazione di **SQL Server Integration Services**](../integration-services/new-updated-integration-services.md)
- [Nuovo + aggiornato (10+9): documentazione di **Linux per SQL Server**](../linux/new-updated-linux.md)
- [Nuovo + aggiornato (2+4): documentazione dei **database relazionali per SQL Server**](../relational-databases/new-updated-relational-databases.md)
- [Nuovo + aggiornato (4+2): documentazione di **SQL Server Reporting Services**](../reporting-services/new-updated-reporting-services.md)
- [Nuovo + aggiornato (0+1): documentazione degli **esempi per SQL Server**](../sample/new-updated-sample.md)
- [Nuovo + aggiornato (21+0): documentazione di **SQL Operations Studio**](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [Nuovo + aggiornato (5+1): documentazione di **Microsoft SQL Server**](../sql-server/new-updated-sql-server.md)
- [Nuovo + aggiornato (0+1): **SQL Server Data Tools (SSDT)** Docs](../ssdt/new-updated-ssdt.md)
- [Nuovo + aggiornato (1+0): documentazione di **SQL Server Migration Assistant (SSMA)**](../ssma/new-updated-ssma.md)
- [Nuovo + aggiornato (0+1): **SQL Server Management Studio (SSMS)** Docs](../ssms/new-updated-ssms.md)
- [Nuovo + aggiornato (0+2): documentazione di **Transact-SQL**](../t-sql/new-updated-t-sql.md)

#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>Aree di interesse senza articoli nuovi o aggiornati di recente

- [Nuovo + aggiornato (0 + 0): documentazione di **Data Migration Assistant (DMA) per SQL Server**](../dma/new-updated-dma.md)
- [Nuovo + aggiornato (0+0): **ActiveX Data Objects (ADO) for SQL (ActiveX Data Objects (ADO) per SQL)** Docs](../ado/new-updated-ado.md)
- [Nuovo + aggiornato (0+0): **Data Quality Services for SQL (Data Quality Services per SQL)** Docs](../data-quality-services/new-updated-data-quality-services.md)
- [Nuovo + aggiornato (0+0): **Data Mining Extensions (DMX) for SQL (Estensioni di data mining (DMX) per SQL)** Docs](../dmx/new-updated-dmx.md)
- [Nuovo + aggiornato (0+0): documentazione di **Master Data Services (MDS) per SQL**](../master-data-services/new-updated-master-data-services.md)
- [Nuovo + aggiornato (0+0): **Multidimensional Expressions (MDX) for SQL(Espressioni MDX per SQL)** Docs](../mdx/new-updated-mdx.md)
- [Nuovo + aggiornato (0+0): **ODBC (Open Database Connectivity) for SQL (ODBC (Open Database Connectivity) per SQL)** Docs](../odbc/new-updated-odbc.md)
- [Nuovo + aggiornato (0+0): **PowerShell for SQL (PowerShell per SQL)** Docs](../powershell/new-updated-powershell.md)
- [Nuovo + aggiornato (0+0): documentazione degli **strumenti per SQL**](../tools/new-updated-tools.md)
- [Nuovo + aggiornato (0+0): **XQuery for SQL (XQuery per SQL)** Docs](../xquery/new-updated-xquery.md)


