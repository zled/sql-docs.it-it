---
title: 'Procedura: connettersi a una porta specifica | Documenti Microsoft'
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: php
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: connecting to the server, specifying a port
ms.assetid: 65a154d1-375c-439b-a653-7815c9d70ff3
caps.latest.revision: "20"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c8f5fcabd257f602c9ceba97806b031e95142a76
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2017
---
# <a name="how-to-connect-on-a-specified-port"></a>Procedura: Connessione a una porta specifica
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

In questo argomento viene descritto come connettersi a SQL Server mediante una porta specifica con i [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
### <a name="to-connect-on-a-specified-port"></a>Per connettersi a una porta specifica  
  
1.  Verificare la porta del server configurata per accettare le connessioni. Per informazioni sulla configurazione di un server per accettare le connessioni a una porta specifica, vedere [procedura: configurare un Server per l'attesa su una porta TCP specifica (Gestione configurazione SQL Server)](http://go.microsoft.com/fwlink/?LinkId=121865).  
  
2.  Aggiungere la porta desiderata per il *$serverName* parametro del [sqlsrv_connect](../../connect/php/sqlsrv-connect.md) (funzione). Separare il nome del server e la porta con una virgola. Ad esempio, le righe di codice seguente usano il driver SQLSRV per illustrare come connettersi a un server denominato *myServer* sulla porta 1521:  
  
    ```  
    $serverName = "myServer, 1521";  
    sqlsrv_connect( $serverName );  
    ```  
  
    Le righe di codice seguente usano il driver PDO_SQLSRV per illustrare come connettersi a un server denominato *myServer* sulla porta 1521:  
  
    ```  
    $serverName = "(local), 1521";  
    $database = "AdventureWorks";  
    $conn = new PDO( "sqlsrv:server=$serverName;Database=$database", "", "");  
    ```  
  
## <a name="see-also"></a>Vedere anche  
[Connessione al server](../../connect/php/connecting-to-the-server.md)  
[Guida di programmazione per il driver SQL PHP](../../connect/php/programming-guide-for-php-sql-driver.md)
[Introduzione al driver SQL PHP](../../connect/php/getting-started-with-the-php-sql-driver.md) 
[Riferimento all'API del driver SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  
[Guida di riferimento del driver PDO_SQLSRV](../../connect/php/pdo-sqlsrv-driver-reference.md)  
  
