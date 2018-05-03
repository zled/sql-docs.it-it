---
title: Utilizzando i metadati dei Database | Documenti Microsoft
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
ms.assetid: 8b048371-e912-4ed1-afd7-436978f48888
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f7a93692028a5debc94d6bb35d38e2a4a64f01de
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="using-database-metadata"></a>Utilizzo dei metadati del database
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Query su un database per informazioni sugli oggetti supportati, il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] implementa il [SQLServerDatabaseMetaData](../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md) classe. Questa classe contiene vari metodi che restituiscono informazioni sotto forma di singolo valore o come set di risultati.  
  
 Per creare un oggetto SQLServerDatabaseMetaData, è possibile utilizzare il [getMetaData](../../connect/jdbc/reference/getmetadata-method-sqlserverconnection.md) metodo il [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) classe per ottenere informazioni sul database di cui è connesso.  
  
 Nell'esempio seguente, una connessione aperta per la [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] database di esempio viene passato alla funzione, viene utilizzato il metodo getMetaData della classe SQLServerConnection per restituire un oggetto SQLServerDatabaseMetadata e quindi vari metodi del Oggetto SQLServerDatabaseMetaData vengono utilizzati per visualizzare informazioni su driver, versione del driver, nome del database e versione del database.  
  
 [!code[JDBC#UsingDBMetaData1](../../connect/jdbc/codesnippet/Java/using-database-metadata_1.java)]  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione dei metadati con il driver JDBC](../../connect/jdbc/handling-metadata-with-the-jdbc-driver.md)  
  
  
