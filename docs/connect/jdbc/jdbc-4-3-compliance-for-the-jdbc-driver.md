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
ms.openlocfilehash: 44ec3198bfb6f9898406688df2544dd2e243294b
ms.sourcegitcommit: e02c28b0b59531bb2e4f361d7f4950b21904fb74
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 08/02/2018
ms.locfileid: "39459485"
---
# <a name="jdbc-43-compliance-for-the-jdbc-driver"></a>Conformità a JDBC 4.3 per il driver JDBC

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

> [!NOTE]  
> Le versioni precedenti a Microsoft JDBC Driver 6.4 per SQL Server sono compatibili solo con le specifiche Java Database Connectivity (JDBC) API 4.2. Questa sezione non è applicabile per la versione 6.4 e versioni precedenti.

A partire dalla versione 6.4, Microsoft JDBC Driver per SQL Server è compatibile con JAVA 9 e genera `SQLFeatureNotSupportedException` per nuove API 4.3 JDBC che hanno non implementati i metodi.

Con Microsoft JDBC Driver 7.0 per la versione di SQL Server, il driver è ora JAVA 10 compatibile e supporta riportato di seguito indicato le API. Il driver genera `SQLFeatureNotSupportedException` per altri metodi non implementate dalle specifiche di JDBC 4.3.

|Nuova API|Descrizione|Implementazione significativa|  
|-----------------|-----------------|-------------------------------|  
|java.sql.connection.beginRequest() void|Suggerimenti per il driver che sta iniziando una richiesta, un'unità indipendente di lavoro, per la connessione. Per altre informazioni, vedere [java.sql.Connection](https://docs.oracle.com/javase/9/docs/api/java/sql/Connection.html#beginRequest--).|Salva i valori dei campi connessione modificabili tramite i metodi API pubblici: `databaseAutoCommitMode`, `transactionIsolationLevel`, `networkTimeout`, `holdability`, `sendTimeAsDatetime`, `statementPoolingCacheSize`, `disableStatementPooling`, `serverPreparedStatementDiscardThreshold`, `enablePrepareOnFirstPreparedStatementCall `, `catalogName`, `sqlWarnings`, `useBulkCopyForBatchInsert `.|
|java.sql.connection.endRequest() void|Suggerimenti per il driver in una richiesta, un'unità indipendente di lavoro, è stata completata. Per altre informazioni, vedere [java.sql.Connection](https://docs.oracle.com/javase/9/docs/api/java/sql/Connection.html#endRequest--).|Chiude le istruzioni che vengono create durante l'unità di lavoro ed eseguire il rollback delle transazioni aperte. Il metodo ripristina inoltre le modifiche apportate ai campi connessione elencate in precedenza.|
