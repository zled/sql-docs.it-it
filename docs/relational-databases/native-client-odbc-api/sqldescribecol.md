---
title: SQLDescribeCol | Microsoft Docs
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-api
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLDescribeCol function
ms.assetid: ffbf34c6-8268-434f-829a-82009a6cda59
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 06d4431256c20928a053f8d913b961bb38c99409
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2018
---
# <a name="sqldescribecol"></a>SQLDescribeCol
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Per le istruzioni eseguite, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client non è necessario eseguire query sul server per descrivere le colonne in un set di risultati. In questo caso, **SQLDescribeCol** non provoca un round trip del server. Ad esempio [SQLColAttribute](../../relational-databases/native-client-odbc-api/sqlcolattribute.md)e[SQLNumResultCols](../../relational-databases/native-client-odbc-api/sqlnumresultcols.md), la chiamata **SQLDescribeCol** via preparate, ma le istruzioni non eseguite genera un round trip del server.  
  
 Quando un'istruzione o un batch di istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] restituisce più set di righe di risultati, è possibile che una colonna, a cui fa riferimento un numero ordinale, provenga da una tabella separata o faccia riferimento a una colonna completamente diversa nel set di risultati. **SQLDescribeCol** deve essere chiamato per ogni set. Quando il set di risultati cambia, l'applicazione deve riassociare i valori dei dati prima di recuperare i risultati delle righe. Per ulteriori informazioni sulla gestione di più risultati set restituiti, vedere [SQLMoreResults](../../relational-databases/native-client-odbc-api/sqlmoreresults.md).  
  
 Gli attributi di colonna vengono indicati solo per il primo set di risultati quando più set di risultati vengono generati da un batch preparato di istruzioni SQL.  
  
 Per i tipi di dati di valori di grandi dimensioni, il valore restituito in *DataTypePtr* è SQL_VARCHAR, SQL_VARBINARY o SQL_NVARCHAR. Il valore SQL_SS_LENGTH_UNLIMITED in *ColumnSizePtr* indica che la dimensione è "illimitata".  
  
 Miglioramenti nel motore di database a partire da [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] consentire SQLDescribeCol ottenere descrizioni più accurate dei risultati previsti. Questi risultati più accurati differiscano dai valori restituiti da SQLDescribeCol nelle versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per ulteriori informazioni, vedere [Metadata Discovery](../../relational-databases/native-client/features/metadata-discovery.md).  
  
## <a name="sqldescribecol-support-for-enhanced-date-and-time-features"></a>Supporto di SQLDescribeCol per le caratteristiche avanzate di data e ora  
 I valori restituiti per i tipi di data/ora sono i seguenti:  
  
||*DataTypePtr*|*ColumnSizePtr*|*DecimalDigitsPtr*|  
|-|-------------------|---------------------|------------------------|  
|datetime|SQL_TYPE_TIMESTAMP|23|3|  
|smalldatetime|SQL_TYPE_TIMESTAMP|16|0|  
|data|SQL_TYPE_DATE|10|0|  
|time|SQL_SS_TIME2|8, 10..16|0..7|  
|datetime2|SQL_TYPE_TIMESTAMP|19, 21..27|0..7|  
|datetimeoffset|SQL_SS_TIMESTAMPOFFSET|26, 28..34|0..7|  
  
 Per ulteriori informazioni, vedere [data e ora miglioramenti &#40; ODBC &#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqldescribecol-support-for-large-clr-udts"></a>Supporto di SQLDescribeCol per tipi CLR definiti dall'utente di grandi dimensioni  
 **SQLDescribeCol** supporta i tipi CLR grandi dimensioni definito dall'utente (UDT). Per ulteriori informazioni, vedere [Large CLR User-Defined tipi &#40; ODBC &#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione SQLDescribeCol](http://go.microsoft.com/fwlink/?LinkID=59338)   
 [Dettagli di implementazione di API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
