---
title: Tipi di dati SQL Server predefinito | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- default data types
- converting data types
ms.assetid: 65c7c211-96d3-4e65-a1de-1fe8d21348e7
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b71a28f48cdbfe9e70079abfc392f53976c90c87
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="default-sql-server-data-types"></a>Tipi di dati di SQL Server predefiniti
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Se l'utente non ha specificato alcun tipo di dati di SQL Server, quando si inviano dati al server, i [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] convertono i dati dal tipo di dati PHP a un tipo di dati di SQL Server. Nella tabella seguente sono elencati il tipo di dati PHP (il tipo di dati inviato al server) e il tipo di dati di SQL Server predefinito (il tipo di dati in cui i dati vengono convertiti). Per informazioni dettagliate su come specificare i tipi di dati quando si inviano dati al server, vedere [Procedura: Specificare i tipi di dati di SQL Server con il driver SQLSRV](../../connect/php/how-to-specify-sql-server-data-types-when-using-the-sqlsrv-driver.md).  
  
|Tipo di dati PHP|Tipo di dati di Server SQL predefinito nel driver SQLSRV|Tipo di dati di Server SQL predefinito nel driver PDO_SQLSRV|  
|-----------------|------------------------------------------------|-----------------------------------------------------|  
|NULL|varchar(1)|non supportato|  
|Boolean|bit|bit|  
|Integer|int|int|  
|Float|float(24)|non supportato|  
|Stringa (lunghezza minore di 8000 byte)|varchar (<string length>)|varchar (<string length>)|  
|Stringa (lunghezza maggiore di 8000 byte)|varchar(max)|varchar(max)|  
|Risorsa|Non supportato.|Non supportato.|  
|Flusso (codifica: non binaria)|varchar(max)|varchar(max)|  
|Flusso (codifica: binaria)|varbinary|varbinary|  
|Array|Non supportato.|Non supportato.|  
|Oggetto|Non supportato.|Non supportato.|  
|DateTime (1)|datetime|Non supportato.|  
  
## <a name="see-also"></a>Vedere anche  
[Costanti &#40;driver Microsoft per PHP per SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)  
[Converting Data Types](../../connect/php/converting-data-types.md)  
[sqlsrv_field_metadata](../../connect/php/sqlsrv-field-metadata.md)  
[Tipi PHP](http://go.microsoft.com/fwlink/?LinkId=109071)  
[Tipi di dati (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=109068)  
  

