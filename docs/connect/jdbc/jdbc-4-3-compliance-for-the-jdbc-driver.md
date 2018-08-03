---
title: JDBC 4.3 conformità per il Driver JDBC | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 36025ec0-3c72-4e68-8083-58b38e42d03b
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f529c88044444f3fb6e428b6c69f5a5cf5917251
ms.sourcegitcommit: 6fa72c52c6d2256c5539cc16c407e1ea2eee9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/27/2018
ms.locfileid: "39278912"
---
# <a name="jdbc-43-compliance-for-the-jdbc-driver"></a>Conformità a JDBC 4.3 per il driver JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

    
> [!NOTE]  
>  Le versioni precedenti a Microsoft JDBC Driver 6.4 per SQL Server sono compatibili con le specifiche Java Database Connectivity (JDBC) API 4.2. Questa sezione non è applicabile per le versioni precedenti alla 6.4.  
  
 A partire dalla versione 6.4, Microsoft JDBC Driver per SQL Server è JAVA 10 compatibile, ma non è completamente conforme con JDBC 4.3 di API specifiche. Il driver genera un'eccezione SQLFeatureNotSupportedException per i metodi non implementati. 
 
 I metodi API JDBC 4.3 seguenti vengono implementati in Microsoft JDBC Driver 6.4 per SQL Server.
 
  **Classe SQLServerConnection**  
  
|Nuovi metodi|Descrizione|Implementazione significativa|  
|-----------------|-----------------|-------------------------------|  
|void BeginRequest)|Suggerimenti per il driver che sta iniziando una richiesta, un'unità indipendente di lavoro, per la connessione. Per altre informazioni, vedere [java.sql.Connection](https://docs.oracle.com/javase/9/docs/api/java/sql/Connection.html#beginRequest--).|Salva i valori dei campi connessione modificabili tramite i metodi API pubblici: `databaseAutoCommitMode`, `transactionIsolationLevel`, `networkTimeout`, `holdability`, `sendTimeAsDatetime`, `statementPoolingCacheSize`, `disableStatementPooling`, `serverPreparedStatementDiscardThreshold`, `enablePrepareOnFirstPreparedStatementCall `, `catalogName`, `sqlWarnings`, `useBulkCopyForBatchInsert `.|
|endRequest() void|Suggerimenti per il driver in una richiesta, un'unità indipendente di lavoro, è stata completata. Per altre informazioni, vedere [java.sql.Connection](https://docs.oracle.com/javase/9/docs/api/java/sql/Connection.html#endRequest--).|Chiude le istruzioni che vengono create durante l'unità di lavoro ed eseguire il rollback delle transazioni aperte. Il metodo ripristina inoltre le modifiche apportate ai campi connessione elencate in precedenza.|