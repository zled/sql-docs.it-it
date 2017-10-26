---
title: Requisiti di sistema per il Driver SQL PHP | Documenti Microsoft
ms.custom: 
ms.date: 07/12/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- requirements
ms.assetid: 5db4b75f-c605-4785-9560-399a533c0fc9
caps.latest.revision: 93
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ba7e8cde4b8d3b77effca06b00303984223551f5
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="system-requirements-for-the-php-sql-driver"></a>Requisiti di sistema per il driver SQL PHP
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Per accedere ai dati in un Database SQL di Azure o di SQL Server tramite il [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)], è necessario disporre installati nel computer i componenti seguenti:  
  
-   PHP è obbligatorio. Per informazioni su come scaricare e installare i file binari stabili più recenti, vedere [http://php.net](http://go.microsoft.com/fwlink/?LinkId=101876).  Microsoft Drivers for PHP per SQL Server richiedono le versioni seguenti:
  
|Versione del driver Microsoft per PHP per SQL Server|Versioni PHP supportate|  
|----------------------------------------------------|--------------------------|  
|4.3|PHP 7.0 e 7.1 PHP| 
|4.0|PHP 7.0|  
|3.2|PHP 5.6.4+ oppure<br /><br />PHP 5.5.16+ oppure<br /><br />PHP 5.4.32|  
|3.1|PHP 5.5.16+ oppure<br /><br />PHP 5.4.32|  
|3.0|PHP 5.4.32 oppure<br /><br />PHP 5.3.0|  
|2.0|PHP 5.3.0 oppure<br /><br />PHP 5.2.4 oppure<br /><br />PHP 5.2.13|  
  
-   È necessario che la directory dell'estensione PHP includa una versione del file del driver. Per informazioni sui diversi file di driver, vedere Versioni dei driver più avanti in questo argomento. Per informazioni sulla configurazione del driver per il runtime PHP, vedere [Caricamento del driver SQL PHP](../../connect/php/loading-the-php-sql-driver.md)  . Per scaricare i driver, vedere [Driver Microsoft per PHP per SQL Server](http://www.microsoft.com/download/details.aspx?id=20098).  
  
-   È necessario un server Web. Il server Web deve essere configurato per eseguire PHP. Per informazioni sull'hosting di applicazioni PHP con Internet Information Services (IIS) 6.0, vedere [Using FastCGI to Host PHP Applications on IIS 6.0](http://go.microsoft.com/fwlink/?LinkId=117131). Per informazioni sull'hosting di applicazioni PHP con IIS 7.0, vedere [Uso di FastCGI per l'hosting di applicazioni PHP in IIS 7.0](http://go.microsoft.com/fwlink/?LinkId=117132).  
  
    I [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] sono stati testati usando IIS 6 e IIS 7 con FastCGI.  
  
    > [!NOTE]  
    > Microsoft fornisce il supporto solo per IIS.  
  
-   La versione corretta di Microsoft ODBC Driver for SQL Server o SQL Server Native Client è necessario nel computer in cui viene eseguito PHP.  Se si utilizza un sistema operativo a 64 bit, il programma di installazione di ODBC a 64 bit vengono installati i driver ODBC sia a 32 bit e a 64 bit. Se si utilizza un sistema operativo a 32 bit, utilizzare ODBC x86 programma di installazione.

|Versione del driver Microsoft per PHP per SQL Server|Versione di Microsoft ODBC Driver for SQL Server o SQL Server Native Client|  
|----------------------------------------------------|--------------------------|
|4.3|Microsoft ODBC Driver 11 for SQL Server o Microsoft ODBC Driver 13.1 for SQL Server. Per scaricare Microsoft ODBC Driver, vedere il [Microsoft ODBC Driver 11 per la pagina di SQL Server](http://www.microsoft.com/download/details.aspx?id=36434) o [Microsoft ODBC Driver 13.1 per la pagina di SQL Server](https://www.microsoft.com/en-us/download/details.aspx?id=53339)|    
|4.0|Microsoft ODBC Driver 11 for SQL Server o Microsoft ODBC Driver 13 for SQL Server. Per scaricare Microsoft ODBC Driver, vedere il [Microsoft ODBC Driver 11 per la pagina di SQL Server](http://www.microsoft.com/download/details.aspx?id=36434) o [Microsoft ODBC Driver 13 per la pagina di SQL Server](https://www.microsoft.com/download/details.aspx?id=50420)|  
|3.2 o <br><br> 3.1|Microsoft ODBC Driver 11 for SQL Server. Per scaricare Microsoft ODBC Driver, vedere il [Microsoft ODBC Driver 11 per la pagina di SQL Server](http://www.microsoft.com/download/details.aspx?id=36434)|   
|3.0|Microsoft [!INCLUDE[ssSQL11](../../includes/sssql11_md.md)] Native Client. È possibile scaricare Microsoft [!INCLUDE[ssSQL11](../../includes/sssql11_md.md)] Native Client dalla [pagina Feature Pack di Microsoft SQL Server 2012](http://go.microsoft.com/fwlink/?LinkID=236805)| 
|2.0|Microsoft [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro_md.md)] Native Client:<br /><br />[Scarica il pacchetto X86](http://go.microsoft.com/fwlink/?LinkID=188400&clcid=0x409) per sistemi operativi a 32 bit <br /><br />[Scarica il pacchetto X64](http://go.microsoft.com/fwlink/?LinkID=188401&clcid=0x409) per i sistemi operativi a 64 bit|  

  
Se si utilizza il driver SQLSRV, [sqlsrv_client_info](../../connect/php/sqlsrv-client-info.md) restituisce informazioni sulla versione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Native Client o il Driver ODBC di Microsoft per SQL Server viene utilizzato per il [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]. Se si utilizza il driver PDO_SQLSRV, è possibile utilizzare [PDO:: GetAttribute](../../connect/php/pdo-getattribute.md) per individuare la versione.  



## <a name="database-versions"></a>Versioni del database
-   Database SQL di Azure sono supportati. Per informazioni, vedere [connessione al Database SQL di Microsoft Azure](../../connect/php/connecting-to-microsoft-azure-sql-database.md). 

- [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]versione 4.3 supporta SQL Server 2008 R2 e versioni successive
- [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]supporto della versione 4.0 SQL Server 2008 e versioni successive
- [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]supporto della versione 3.1 SQL Server 2008 e versioni successive
- [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]supporto della versione 2.0 e 3.0 SQL Server 2005 e versioni successive


## <a name="driver-versions"></a>Versioni dei driver  
In questa sezione vengono elencati i driver inclusi in ogni versione di [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
Per configurare il driver per l'utilizzo con il runtime PHP, seguire le istruzioni di installazione in [durante il caricamento del Driver SQL PHP](../../connect/php/loading-the-php-sql-driver.md).  
  
**Driver Microsoft 4.3 per PHP per SQL Server:**  

In Windows, per 4.3 siano installate le versioni seguenti del driver:
  
|File del driver|Versione PHP|Thread-safe?|Uso con PHP .dll|  
|---------------|---------------|----------------|---------------------|  
|php_sqlsrv_7_nts_x86.dll<br /><br />php_pdo_sqlsrv_7_nts_x86.dll|7.0|no|php7.dll a 32 bit| 
|php_sqlsrv_7_ts_x86.dll<br /><br />php_pdo_sqlsrv_7_ts_x86.dll|7.0|sì|php7ts.dll a 32 bit| 
|php_sqlsrv_7_nts_x64.dll<br /><br />php_pdo_sqlsrv_7_nts_x64.dll|7.0|no|php7.dll a 64 bit|  
|php_sqlsrv_7_ts_x64.dll<br /><br />php_pdo_sqlsrv_7_ts_x64.dll|7.0|sì|php7ts.dll a 64 bit| 
|php_sqlsrv_71_nts_x86.dll<br /><br />php_pdo_sqlsrv_71_nts_x86.dll|7.1|no|php7.dll a 32 bit|  
|php_sqlsrv_71_ts_x86.dll<br /><br />php_pdo_sqlsrv_71_ts_x86.dll|7.1|sì|php7ts.dll a 32 bit|  
|php_sqlsrv_71_nts_x64.dll<br /><br />php_pdo_sqlsrv_71_nts_x64.dll|7.1|no|php7.dll a 64 bit|  
|php_sqlsrv_71_ts_x64.dll<br /><br />php_pdo_sqlsrv_71_ts_x64.dll|7.1|sì|php7ts.dll a 64 bit|   
  
**Microsoft driver 4.0 per PHP per SQL Server:**  

In Windows, per la versione 4.0 siano installate le versioni seguenti del driver:
  
|File del driver|Versione PHP|Thread-safe?|Uso con PHP .dll|  
|---------------|---------------|----------------|---------------------|  
|php_sqlsrv_7_nts_x86.dll<br /><br />php_pdo_sqlsrv_7_nts_x86.dll|7.0|no|php7.dll a 32 bit|  
|php_sqlsrv_7_ts_x86.dll<br /><br />php_pdo_sqlsrv_7_ts_x86.dll|7.0|sì|php7ts.dll a 32 bit|  
|php_sqlsrv_7_nts_x64.dll<br /><br />php_pdo_sqlsrv_7_nts_x64.dll|7.0|no|php7.dll a 64 bit|  
|php_sqlsrv_7_ts_x64.dll<br /><br />php_pdo_sqlsrv_7_ts_x64.dll|7.0|sì|php7ts.dll a 64 bit|   
  
In versioni supportate di Linux, è possibile installare la versione appropriata di sqlsrv e/o pdo_sqlsrv utilizzando sistema pacchetto PECL di PHP. 
  
**I driver Microsoft 3.2 per PHP per SQL Server installano le seguenti versioni del driver:**  
  
|File del driver|Versione PHP|Thread-safe?|Uso con PHP .dll|  
|---------------|---------------|----------------|---------------------|  
|php_sqlsrv_54_nts.dll<br /><br />php_pdo_sqlsrv_54_nts.dll|5.4|no|php5.dll|  
|php_sqlsrv_54_ts.dll<br /><br />php_pdo_sqlsrv_54_ts.dll|5.4|sì|php5ts.dll|  
|php_sqlsrv_55_nts.dll<br /><br />php_pdo_sqlsrv_55_nts.dll|5.5|no|php5.dll|  
|php_sqlsrv_55_ts.dll<br /><br />php_pdo_sqlsrv_55_ts.dll|5.5|sì|php5ts.dll|  
|php_sqlsrv_56_nts.dll<br /><br />php_pdo_sqlsrv_56_nts.dll|5.6|no|php5.dll|  
|php_sqlsrv_56_ts.dll<br /><br />php_pdo_sqlsrv_56_ts.dll|5.6|sì|php5ts.dll|  
  
**I driver Microsoft 3.1 per PHP per SQL Server installano le seguenti versioni del driver:**  
  
|File del driver|Versione PHP|Thread-safe?|Uso con PHP .dll|  
|---------------|---------------|----------------|---------------------|  
|php_sqlsrv_54_nts.dll<br /><br />php_pdo_sqlsrv_54_nts.dll|5.4|no|php5.dll|  
|php_sqlsrv_54_ts.dll<br /><br />php_pdo_sqlsrv_54_ts.dll|5.4|sì|php5ts.dll|  
|php_sqlsrv_55_nts.dll<br /><br />php_pdo_sqlsrv_55_nts.dll|5.5|no|php5.dll|  
|php_sqlsrv_55_ts.dll<br /><br />php_pdo_sqlsrv_55_ts.dll|5.5|sì|php5ts.dll|  
  
**I driver Microsoft 3.0 per PHP per SQL Server installano le seguenti versioni del driver:**  
  
|File del driver|Versione PHP|Thread-safe?|Uso con PHP .dll|  
|---------------|---------------|----------------|---------------------|  
|php_sqlsrv_53_nts.dll<br /><br />php_pdo_sqlsrv_53_nts.dll|5.3|no|php5.dll|  
|php_sqlsrv_53_ts.dll<br /><br />php_pdo_sqlsrv_53_ts.dll|5.3|sì|php5ts.dll|  
|php_sqlsrv_54_nts.dll<br /><br />php_pdo_sqlsrv_54_nts.dll|5.4|no|php5.dll|  
|php_sqlsrv_54_ts.dll<br /><br />php_pdo_sqlsrv_54_ts.dll|5.4|sì|php5ts.dll|  
  
**I driver Microsoft 2.0 per PHP per SQL Server installano le seguenti versioni del driver:**  
  
|File del driver|Versione PHP|Thread-safe?|Uso con PHP .dll|  
|---------------|---------------|----------------|---------------------|  
|php_sqlsrv_53_nts_vc6.dll<br /><br />php_pdo_sqlsrv_53_nts_vc6.dll|5.3|no|php5.dll|  
|php_sqlsrv_53_nts_vc9.dll<br /><br />php_pdo_sqlsrv_53_nts_vc9.dll|5.3|no|php5.dll|  
|php_sqlsrv_53_ts_vc6.dll<br /><br />php_pdo_sqlsrv_53_ts_vc6.dll|5.3|sì|php5ts.dll|  
|php_sqlsrv_53_ts_vc9.dll<br /><br />php_pdo_sqlsrv_53_ts_vc9.dll|5.3|sì|php5ts.dll|  
|php_sqlsrv_52_nts_vc6.dll<br /><br />php_pdo_sqlsrv_52_nts_vc6.dll|5.2|no|php5.dll|  
|php_sqlsrv_52_ts_vc6.dll<br /><br />php_pdo_sqlsrv_52_ts_vc6.dll|5.2|sì|php5ts.dll|  
  
Se il nome del file del driver contiene "vc9", è necessario usare una versione PHP compilata con Visual C++ 9.0.  
## <a name="operating-systems"></a>Sistemi operativi 
Come indicato di seguito sono riportati i sistemi operativi supportati per le versioni del driver:

-   4.3:
    -   Windows Server 2012  
    -   Windows Server 2012 R2
    -   Windows Server 2016 
    -   Windows 8  
    -   Windows 8.1   
    -   Windows 10
    -   Ubuntu 15.10 (64 bit)
    -   Ubuntu 16.04 (64 bit)
    -   Debian 8 (64 bit)
    -   Red Hat Enterprise Linux 7 (64 bit)
    -   Mac OS Sierra (64 bit)
    -   Mac OS montagna di El Capitan (64 bit)
    
-   4.0:  
    -   Windows Server 2008 SP2
    -   Windows Server 2008 R2 SP1  
    -   Windows Server 2012  
    -   Windows Server 2012 R2  
    -   Windows Vista SP2  
    -   Windows 7 SP1  
    -   Windows 8  
    -   Windows 8.1   
    -   Windows 10 
    -   Ubuntu 15.04 (64 bit)
    -   Ubuntu 16.04 (64 bit)
    -   Red Hat Enterprise Linux 7 (64 bit)

 
-   3.2 e 3.1:  
    -   Windows Server 2008 R2 SP1  
    -   Windows Vista SP2  
    -   Windows Server 2008 SP2  
    -   Windows 7 SP1  
    -   Windows Server 2012  
    -   Windows Server 2012 R2  
    -   Windows 8  
    -   Windows 8.1  
  
  
-   3.0:  
    -   Windows Server 2008 R2 SP1  
    -   Windows Vista SP2  
    -   Windows Server 2008 SP2  
    -   Windows 7 SP1  


-   2.0:
    -   [!INCLUDE[winxpsvr](../../includes/winxpsvr_md.md)] Service Pack 1  
    -   Windows XP Service Pack 3  
    -   Windows Vista Service Pack 1 o versione successiva  
    -   Windows Server 2008  
    -   Windows Server 2008 R2  
    -   Windows 7  
  
## <a name="see-also"></a>Vedere anche  
[Introduzione al driver SQL PHP](../../connect/php/getting-started-with-the-php-sql-driver.md)
[Guida di programmazione per il driver SQL PHP](../../connect/php/programming-guide-for-php-sql-driver.md)
[Riferimento all'API del driver SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  
  

