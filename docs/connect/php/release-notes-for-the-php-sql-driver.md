---
title: Note sulla versione per il Driver SQL PHP | Documenti Microsoft
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
- what's new in version 1.1
ms.assetid: 91cca3d2-ba99-4a6d-b0de-beb9699cb3f8
caps.latest.revision: 37
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2c63079bda91844995540aade94bac397be6b94c
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="release-notes-for-the-php-sql-driver"></a>Note sulla versione per il driver SQL PHP
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

In questo argomento illustra ciò che è stato aggiunto in ogni versione di [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  

## <a name="whats-new-in-version-43"></a>Novità nella versione 4.3

- Supporto per PHP 7.1
- Supporto per Mac OS Sierra e montagna di El Capitan Mac OS
- Supporto per Ubuntu 15.10 e Debian 8
- Eliminato il supporto per Ubuntu 15.04
- Supporto per i gruppi di disponibilità Always On tramite la risoluzione IP di rete Transparent. Per altre informazioni, vedere [Connection Options](../../connect/php/connection-options.md). 
- Aggiunta del supporto per il tipo di dati sql_variant con limitazione.
- Supporto di resilienza delle connessioni inattivo in Windows. Per altre informazioni, vedere [Connection Options](../../connect/php/connection-options.md).
- Supporto per Linux e macOS pool di connessioni. Per ulteriori informazioni, vedere [il pool di connessioni](../../connect/php/connection-pooling-microsoft-drivers-for-php-for-sql-server.md).
- Supporto per l'autenticazione di Azure Active Directory con ActiveDirectoryPassword e SqlPassword. Per altre informazioni, vedere [Connection Options](../../connect/php/connection-options.md).
  
## <a name="whats-new-in-version-40"></a>Novità nella versione 4.0 

- Supporto per PHP 7.0  
- Supporto a 64 bit
- Supporto di Ubuntu 15.04, Ubuntu 16.04 e RedHat 7

## <a name="whats-new-in-version-32"></a>Novità della versione 3.2 

- Supporto per PHP 5.6   
- Include gli aggiornamenti più recenti per le versioni precedenti di PHP, la 5.5 e la 5.4   
- Richiede Microsoft ODBC Driver 11 for SQL Server  
  
## <a name="whats-new-in-version-31"></a>Novità della versione 3.1
 
- Supporto per PHP 5.5  
- Richiede Microsoft ODBC Driver 11 for SQL Server. Le versioni precedenti richiedono SQL Native Client.  
  
## <a name="whats-new-in-version-30"></a>Novità della versione 3.0  

- Supporto per PHP 5.4  PHP 5.2 non è supportato nella versione 3 di [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
- È stata aggiunta l'opzione di connessione AttachDBFileName. Per altre informazioni, vedere [Connection Options](../../connect/php/connection-options.md).  
- Supporto per LocalDB, aggiunto in [!INCLUDE[ssSQL11](../../includes/sssql11_md.md)]. Per altre informazioni, vedere [PHP Driver for SQL Server Support for LocalDB](../../connect/php/php-driver-for-sql-server-support-for-localdb.md).
- È stata aggiunta l'opzione di connessione AttachDBFileName. Per altre informazioni, vedere [Connection Options](../../connect/php/connection-options.md).  
- Supporto per le funzionalità di ripristino di emergenza a disponibilità elevata. Per altre informazioni, vedere [PHP Driver for SQL Server Support for High Availability, Disaster Recovery (Driver PHP per il supporto di SQL Server per il ripristino di emergenza a disponibilità elevata)](../../connect/php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).
- Supporto per i cursori sul lato client (memorizzazione nella cache di un set di risultati in memoria). Per ulteriori informazioni, vedere [tipi di cursore &#40; Driver SQLSRV &#41; ](../../connect/php/cursor-types-sqlsrv-driver.md) e [tipi di cursore &#40; Driver PDO_SQLSRV &#41; ](../../connect/php/cursor-types-pdo-sqlsrv-driver.md).
- È stato aggiunto l'attributo PDO::ATTR_EMULATE_PREPARES. Per ulteriori informazioni, vedere [PDO:: Prepare](../../connect/php/pdo-prepare.md).  
  
## <a name="whats-new-in-version-20"></a>Novità della versione 2.0  
Nella versione 2.0 è stato aggiunto il supporto per il driver PDO_SQLSRV. Per altre informazioni, vedere [Guida di riferimento del driver PDO_SQLSRV](../../connect/php/pdo-sqlsrv-driver-reference.md).  
  
## <a name="see-also"></a>Vedere anche  
[Panoramica del driver SQL PHP](../../connect/php/overview-of-the-php-sql-driver.md)
  

