---
title: Recupero della versione del Driver | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 5e241d72-16da-4ada-ac67-e6308394108f
caps.latest.revision: 21
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d3828c04f418a31e2dacddb97472ec3b2f776a5e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="getting-the-driver-version"></a>Recupero della versione del driver
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  La versione installata di [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] sono reperibili nei modi seguenti:  
  
-   Chiamare il [SQLServerDatabaseMetaData](../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md) metodi [getDriverMajorVersion](../../connect/jdbc/reference/getdrivermajorversion-method-sqlserverdatabasemetadata.md), [getDriverMinorVersion](../../connect/jdbc/reference/getdriverminorversion-method-sqlserverdatabasemetadata.md), o [getDriverVersion](../../connect/jdbc/reference/getdriverversion-method-sqlserverdatabasemetadata.md).  
  
-   La versione viene visualizzata nel file readme.txt della distribuzione del prodotto.  
  
 Inoltre, il nome del driver JDBC può essere restituito dal [getDriverName](../../connect/jdbc/reference/getdrivername-method-sqlserverdatabasemetadata.md) chiamata al metodo nella classe SQLServerDatabaseMetaData. Verrà restituito, ad esempio, "Microsoft JDBC Driver 6.4 per SQL Server".  
  
 Di seguito è riportato un esempio dell'output da chiamate ai metodi della classe SQLServerDatabaseMetaData:  
  
 `getDriverName = Microsoft JDBC Driver 6.4 for SQL Server`  
  
 `getDriverMajorVersion = 6`  
  
 `getDriverMinorVersion = 4`  
  
 `getDriverVersion = 6.4.` *xxx.x*  
  
 Dove "xxx.x" è il numero della versione finale.  
  
## <a name="see-also"></a>Vedere anche  
 [Diagnosi dei problemi relativi al driver JDBC](../../connect/jdbc/diagnosing-problems-with-the-jdbc-driver.md)  
  
  
