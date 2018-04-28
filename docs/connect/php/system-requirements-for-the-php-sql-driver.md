---
title: Requisiti di sistema per i driver Microsoft per PHP per SQL Server | Documenti Microsoft
ms.custom: ''
ms.date: 03/23/2018
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- requirements
ms.assetid: 5db4b75f-c605-4785-9560-399a533c0fc9
caps.latest.revision: 93
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Active
ms.openlocfilehash: 44a18257abc758ee910fb9c4953cbdef02239fbd
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="system-requirements-for-the-microsoft-drivers-for-php-for-sql-server"></a>Requisiti di sistema per i driver Microsoft per PHP per SQL Server
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Questo documento vengono elencati i componenti che devono essere installati nel sistema per accedere ai dati in un Database SQL di Azure o SQL Server tramite il [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].

Le versioni 3.1 e successive dei driver Microsoft PHP per SQL Server sono ufficialmente supportate. Per informazioni dettagliate su cicli di vita del supporto e requisiti, incluse le versioni precedenti di driver di PHP, vedere la [matrice del supporto](../../connect/php/microsoft-php-drivers-for-sql-server-support-matrix.md).

## <a name="php"></a>PHP

Per informazioni su come scaricare e installare i file binari PHP stabili più recenti, vedere [il sito web PHP](http://php.net).  Microsoft Drivers for PHP per SQL Server richiedono le seguenti versioni di PHP:

|PHP per la versione del driver SQL Server&#8594;<br />&#8595;Versione PHP|5.2<br />&nbsp;|4.3<br />&nbsp;|4.0<br />&nbsp;|3.2<br />&nbsp;|3.1<br />&nbsp;|
|---|---|---|---|---|---|
|7.2|7.2.1+ in Windows<br/>7.2.0+ su altre piattaforme | | | | |
|7.1|7.1.0+ |7.1.0+ |       |        |        |
|7.0|7.0.0+ |7.0.0+ |7.0.0+ |        |        |
|5.6|       |       |       |5.6.4 +  |        |
|5.5|       |       |       |5.5.16+ |5.5.16+ |
|5.4|       |       |       |5.4.32  |5.4.32  |

-   È necessario che la directory dell'estensione PHP includa una versione del file del driver. Vedere [le versioni del Driver](#driver-versions) per informazioni sui diversi file di driver.  Per scaricare i driver, vedere [scaricare Microsoft Drivers for PHP for SQL Server](download-drivers-php-sql-server.md). Per informazioni sulla configurazione del driver per PHP, vedere [Loading the Microsoft Drivers for PHP per SQL Server](../../connect/php/loading-the-php-sql-driver.md).

-   È necessario un server Web. Il server Web deve essere configurato per eseguire PHP. Per informazioni sull'hosting di applicazioni PHP con IIS, vedere la [esercitazione sul sito web PHP](http://php.net/manual/fa/install.windows.iis.php).  

    Il [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] sono stati testati usando IIS 10 con FastCGI.  

    > [!NOTE]  
    > Microsoft fornisce il supporto solo per IIS.  

## <a name="odbc-driver"></a>Driver ODBC

La versione corretta di Microsoft ODBC Driver for SQL Server è necessario nel computer in cui viene eseguito PHP. Scaricare dai collegamenti seguenti:
- [Microsoft ODBC Driver 17 per SQL Server](https://www.microsoft.com/en-us/download/details.aspx?id=56567)
- [Microsoft ODBC Driver 13.1 for SQL Server](https://www.microsoft.com/en-us/download/details.aspx?id=53339)
- [Microsoft ODBC Driver 13 for SQL Server](https://www.microsoft.com/download/details.aspx?id=50420)
- [Microsoft ODBC Driver 11 for SQL Server](http://www.microsoft.com/download/details.aspx?id=36434)

Se si utilizza un sistema operativo a 64 bit, il programma di installazione di ODBC a 64 bit vengono installati i driver ODBC sia a 32 bit e a 64 bit. Se si utilizza un sistema operativo a 32 bit, utilizzare ODBC x86 programma di installazione.

|PHP per la versione del driver SQL Server&#8594;<br />&#8595;Versione del Driver ODBC|5.2<br />&nbsp;|4.3<br />&nbsp;|4.0<br />&nbsp;|3.2<br />&nbsp;|3.1<br />&nbsp;|
|---|---|---|---|---|---|
|Driver ODBC 17  |S| | | | |
|ODBC Driver 13.1|S|S|S| | |
|ODBC Driver 13  | | |S| | |
|ODBC Driver 11  |S|S|S|S|S|

Se si utilizza il driver SQLSRV, [sqlsrv_client_info](../../connect/php/sqlsrv-client-info.md) restituisce informazioni sulla versione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Microsoft ODBC Driver for SQL Server è in uso dal [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]. Se si utilizza il driver PDO_SQLSRV, è possibile utilizzare [PDO:: GetAttribute](../../connect/php/pdo-getattribute.md) per individuare la versione.  

## <a name="sql-server"></a>SQL Server

Database SQL di Azure sono supportati. Per informazioni, vedere [connessione al Database SQL di Microsoft Azure](../../connect/php/connecting-to-microsoft-azure-sql-database.md).

|PHP per la versione del driver SQL Server&#8594;<br />&#8595;Versione di SQL Server|5.2<br />&nbsp;|4.3<br />&nbsp;|4.0<br />&nbsp;|3.2<br />&nbsp;|3.1<br />&nbsp;|
|---|---|---|---|---|---|
|Istanza gestita di SQL Azure<br/> (Extended anteprima privata)|S|S| | | |
|Azure SQL Data Warehouse|S|S| | | |
|SQL Server 2017   |S|S| | | |
|SQL Server 2016   |S|S|S| | |
|SQL Server 2014   |S|S|S|S|S|
|SQL Server 2012   |S|S|S|S|S|
|SQL Server 2008 R2|S|S|S|S|S|
|SQL Server 2008   | | |S|S|S|

## <a name="operating-systems"></a>Sistemi operativi
Come indicato di seguito sono riportati i sistemi operativi supportati per le versioni del driver:

|PHP per la versione del driver SQL Server&#8594;<br />&#8595;Sistema operativo|5.2<br />&nbsp;|4.3<br />&nbsp;|4.0<br />&nbsp;|3.2<br />&nbsp;|3.1<br />&nbsp;|
|---|---|---|---|---|---|
|Windows Server 2016                      |S|S| | | |
|Windows Server 2012 R2                   |S|S|S|S|S|
|Windows Server 2012                      |S|S|S|S|S|
|Windows Server 2008 R2 SP1               | | |S|S|S|
|Windows Server 2008 SP2                  | | |S|S|S|
|Windows 10                               |S|S|S| | |
|Windows 8.1                              |S|S|S|S|S|
|Windows 8                                | |S|S|S|S|
|Windows 7 SP1                            | | |S|S|S|
|Windows Vista SP2                        | | |S|S|S|
|Ubuntu 17.10 (64 bit)                    |S| | | | |
|Ubuntu 16.04 (64 bit)                    |S|S|S| | |
|Ubuntu 15.10 (64 bit)                    | |S| | | |
|Ubuntu 15.04 (64 bit)                    | | |S| | |
|Debian 9 (64 bit)                        |S| | | | |
|Debian 8 (64 bit)                        |S|S| | | |
|Red Hat Enterprise Linux 7 (64 bit)      |S|S|S| | |
|Linux SUSE Enterprise 12 (64 bit)        |S| | | | |
|macOS Sierra (64 bit)                    |S|S| | | |
|macOS montagna di El Capitan (64 bit)                |S|S| | | |

## <a name="driver-versions"></a>Versioni dei driver  
In questa sezione sono elencati i file di driver che sono inclusi con ogni versione del [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]. Ogni pacchetto di installazione contiene file di driver SQLSRV e PDO_SQLSRV in varianti con modello di threading e non a thread singolo. In Windows, sono anche disponibili in varianti a 32 e 64 bit. Per configurare il driver per l'utilizzo con il runtime PHP, seguire le istruzioni di installazione in [Loading the Microsoft Drivers for PHP per SQL Server](../../connect/php/loading-the-php-sql-driver.md).

Nelle versioni supportate di Linux e macOS, i driver desiderati possono essere installati usando sistema dei pacchetti PECL PHP, seguendo il [le istruzioni di installazione di Linux e macOS](../../connect/php/installation-tutorial-linux-mac.md). In alternativa, è possibile scaricare i file binari predefiniti per la piattaforma nella [Microsoft Drivers for PHP per SQL Server](https://github.com/Microsoft/msphpsql/releases) Github progetto pagina - tabelle riportate di seguito elencano i file disponibili nei pacchetti binari predefiniti.

**Driver Microsoft 5.2 per PHP per SQL Server:**  

In Windows, le seguenti versioni del driver sono incluse:

|File del driver|Versione PHP|Thread-safe?|Uso con PHP .dll|  
|---------------|---------------|----------------|---------------------|  
|32 bit php_sqlsrv_7_nts.dll <br />32 bit php_pdo_sqlsrv_7_nts.dll |7.0|no |php7.dll a 32 bit|
|32 bit php_sqlsrv_7_ts.dll  <br />32-bit php_pdo_sqlsrv_7_ts.dll  |7.0|sì|php7ts.dll a 32 bit|
|php_sqlsrv_7_nts.dll a 64 bit <br />php_pdo_sqlsrv_7_nts.dll a 64 bit |7.0|no |php7.dll a 64 bit|  
|php_sqlsrv_7_ts.dll a 64 bit  <br />64-bit php_pdo_sqlsrv_7_ts.dll  |7.0|sì|php7ts.dll a 64 bit|
|32 bit php_sqlsrv_71_nts.dll<br />32-bit php_pdo_sqlsrv_71_nts.dll|7.1|no |php7.dll a 32 bit|  
|32-bit php_sqlsrv_71_ts.dll <br />32-bit php_pdo_sqlsrv_71_ts.dll |7.1|sì|php7ts.dll a 32 bit|  
|php_sqlsrv_71_nts.dll a 64 bit<br />64-bit php_pdo_sqlsrv_71_nts.dll|7.1|no |php7.dll a 64 bit|  
|64-bit php_sqlsrv_71_ts.dll <br />64-bit php_pdo_sqlsrv_71_ts.dll |7.1|sì|php7ts.dll a 64 bit|   
|32 bit php_sqlsrv_72_nts.dll<br />32 bit php_pdo_sqlsrv_72_nts.dll|7.2|no |php7.dll a 32 bit|  
|32 bit php_sqlsrv_72_ts.dll <br />32-bit php_pdo_sqlsrv_72_ts.dll |7.2|sì|php7ts.dll a 32 bit|  
|php_sqlsrv_72_nts.dll a 64 bit<br />php_pdo_sqlsrv_72_nts.dll a 64 bit|7.2|no |php7.dll a 64 bit|  
|php_sqlsrv_72_ts.dll a 64 bit <br />64-bit php_pdo_sqlsrv_72_ts.dll |7.2|sì|php7ts.dll a 64 bit|  

In Linux, le seguenti versioni del driver sono incluse:

|File del driver|Versione PHP|Thread-safe?|
|---------------|---------------|----------------|
|php_sqlsrv_7_nts.so <br />php_pdo_sqlsrv_7_nts.so |7.0|no |
|php_sqlsrv_7_ts.so  <br />php_pdo_sqlsrv_7_ts.so  |7.0|sì|
|php_sqlsrv_71_nts.so<br />php_pdo_sqlsrv_71_nts.so|7.1|no |
|php_sqlsrv_71_ts.so <br />php_pdo_sqlsrv_71_ts.so |7.1|sì|  
|php_sqlsrv_72_nts.so<br />php_pdo_sqlsrv_72_nts.so|7.2|no |
|php_sqlsrv_72_ts.so <br />php_pdo_sqlsrv_72_ts.so |7.2|sì|

**Driver Microsoft 4.3 per PHP per SQL Server:**  

In Windows, le seguenti versioni del driver sono incluse:

|File del driver|Versione PHP|Thread-safe?|Uso con PHP .dll|  
|---------------|---------------|----------------|---------------------|  
|32 bit php_sqlsrv_7_nts.dll <br />32 bit php_pdo_sqlsrv_7_nts.dll |7.0|no |php7.dll a 32 bit|
|32 bit php_sqlsrv_7_ts.dll  <br />32-bit php_pdo_sqlsrv_7_ts.dll  |7.0|sì|php7ts.dll a 32 bit|
|php_sqlsrv_7_nts.dll a 64 bit <br />php_pdo_sqlsrv_7_nts.dll a 64 bit |7.0|no |php7.dll a 64 bit|  
|php_sqlsrv_7_ts.dll a 64 bit  <br />64-bit php_pdo_sqlsrv_7_ts.dll  |7.0|sì|php7ts.dll a 64 bit|
|32 bit php_sqlsrv_71_nts.dll<br />32-bit php_pdo_sqlsrv_71_nts.dll|7.1|no |php7.dll a 32 bit|  
|32-bit php_sqlsrv_71_ts.dll <br />32-bit php_pdo_sqlsrv_71_ts.dll |7.1|sì|php7ts.dll a 32 bit|  
|php_sqlsrv_71_nts.dll a 64 bit<br />64-bit php_pdo_sqlsrv_71_nts.dll|7.1|no |php7.dll a 64 bit|  
|64-bit php_sqlsrv_71_ts.dll <br />64-bit php_pdo_sqlsrv_71_ts.dll |7.1|sì|php7ts.dll a 64 bit|   

In Linux, le seguenti versioni del driver sono incluse:

|File del driver|Versione PHP|Thread-safe?|
|---------------|---------------|----------------|
|php_sqlsrv_7_nts.so <br />php_pdo_sqlsrv_7_nts.so |7.0|no |
|php_sqlsrv_7_ts.so  <br />php_pdo_sqlsrv_7_ts.so  |7.0|sì|
|php_sqlsrv_71_nts.so<br />php_pdo_sqlsrv_71_nts.so|7.1|no |
|php_sqlsrv_71_ts.so <br />php_pdo_sqlsrv_71_ts.so |7.1|sì|  

**Microsoft driver 4.0 per PHP per SQL Server:**  

In Windows, le seguenti versioni del driver sono incluse:

|File del driver|Versione PHP|Thread-safe?|Uso con PHP .dll|  
|---------------|---------------|----------------|---------------------|  
|php_sqlsrv_7_nts_x86.dll<br />php_pdo_sqlsrv_7_nts_x86.dll|7.0|no|php7.dll a 32 bit|  
|php_sqlsrv_7_ts_x86.dll<br />php_pdo_sqlsrv_7_ts_x86.dll|7.0|sì|php7ts.dll a 32 bit|  
|php_sqlsrv_7_nts_x64.dll<br />php_pdo_sqlsrv_7_nts_x64.dll|7.0|no|php7.dll a 64 bit|  
|php_sqlsrv_7_ts_x64.dll<br />php_pdo_sqlsrv_7_ts_x64.dll|7.0|sì|php7ts.dll a 64 bit|   

In Linux, le seguenti versioni del driver sono incluse:

|File del driver|Versione PHP|Thread-safe?|
|---------------|---------------|----------------|
|php_sqlsrv_7_nts.so <br />php_pdo_sqlsrv_7_nts.so |7.0|no |
|php_sqlsrv_7_ts.so  <br />php_pdo_sqlsrv_7_ts.so  |7.0|sì|

**Driver Microsoft 3.2 per PHP per SQL Server:**  

In Windows, le seguenti versioni del driver sono incluse:

|File del driver|Versione PHP|Thread-safe?|Uso con PHP .dll|  
|---------------|---------------|----------------|---------------------|  
|php_sqlsrv_54_nts.dll<br />php_pdo_sqlsrv_54_nts.dll|5.4|no|php5.dll|  
|php_sqlsrv_54_ts.dll<br />php_pdo_sqlsrv_54_ts.dll|5.4|sì|php5ts.dll|  
|php_sqlsrv_55_nts.dll<br />php_pdo_sqlsrv_55_nts.dll|5.5|no|php5.dll|  
|php_sqlsrv_55_ts.dll<br />php_pdo_sqlsrv_55_ts.dll|5.5|sì|php5ts.dll|  
|php_sqlsrv_56_nts.dll<br />php_pdo_sqlsrv_56_nts.dll|5.6|no|php5.dll|  
|php_sqlsrv_56_ts.dll<br />php_pdo_sqlsrv_56_ts.dll|5.6|sì|php5ts.dll|  

**Driver Microsoft 3.1 per PHP per SQL Server:**  

In Windows, le seguenti versioni del driver sono incluse:

|File del driver|Versione PHP|Thread-safe?|Uso con PHP .dll|  
|---------------|---------------|----------------|---------------------|  
|php_sqlsrv_54_nts.dll<br />php_pdo_sqlsrv_54_nts.dll|5.4|no|php5.dll|  
|php_sqlsrv_54_ts.dll<br />php_pdo_sqlsrv_54_ts.dll|5.4|sì|php5ts.dll|  
|php_sqlsrv_55_nts.dll<br />php_pdo_sqlsrv_55_nts.dll|5.5|no|php5.dll|  
|php_sqlsrv_55_ts.dll<br />php_pdo_sqlsrv_55_ts.dll|5.5|sì|php5ts.dll|  

## <a name="see-also"></a>Vedere anche  
[Guida introduttiva con i driver Microsoft per PHP per SQL Server](../../connect/php/getting-started-with-the-php-sql-driver.md)

[Guida di programmazione per i driver Microsoft per PHP per SQL Server](../../connect/php/programming-guide-for-php-sql-driver.md)

[Riferimento all'API del driver SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)

[Riferimento all'API del Driver PDO_SQLSRV](../../connect/php/pdo-sqlsrv-driver-reference.md)  
