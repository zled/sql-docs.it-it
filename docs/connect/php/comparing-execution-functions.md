---
title: Confronto tra funzioni di esecuzione | Documenti Microsoft
ms.custom: ''
ms.date: 03/26/2018
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
- executing queries
ms.assetid: 130fc0fd-87dd-46b2-918f-de9dc572c769
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 921f96668cab29ad6fa2e8b43b8c3908f83e01ab
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MTE
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="comparing-execution-functions"></a>Confronto delle funzioni di esecuzione
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

I [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] offrono diverse opzioni per l'esecuzione di funzioni.  

## <a name="sqlsrv-execution-functions"></a>Esecuzione di funzioni di SQLSRV  
Se si usa il driver SQLSRV, usare [sqlsrv_query](../../connect/php/sqlsrv-query.md) per eseguire una query singola e [sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md) con [sqlsrv_execute](../../connect/php/sqlsrv-execute.md) per eseguire un'istruzione preparata più volte con valori di parametro diversi per ogni esecuzione.  

## <a name="pdosqlsrv-execution-functions"></a>Esecuzione di funzioni di PDO_SQLSRV 
Se si usa il driver PDO_SQLSRV, è possibile eseguire una query con una delle funzioni seguenti:  
  
-   [PDO::exec](../../connect/php/pdo-exec.md)  
  
-   [PDO::query](../../connect/php/pdo-query.md)  
  
-   [PDO::prepare](../../connect/php/pdo-prepare.md) e [PDOStatement::execute](../../connect/php/pdostatement-execute.md).  
  
## <a name="see-also"></a>Vedere anche  
[Riferimento all'API del driver SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)

[Guida di riferimento del driver PDO_SQLSRV](../../connect/php/pdo-sqlsrv-driver-reference.md)

[Guida di programmazione per i driver Microsoft per PHP per SQL Server](../../connect/php/programming-guide-for-php-sql-driver.md)
  
