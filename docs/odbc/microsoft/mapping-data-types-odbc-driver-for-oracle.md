---
title: Mapping dei tipi di dati, il Driver ODBC per Oracle | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- mapping data types [ODBC]
- data types [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], data types
ms.assetid: a5d9ce12-19da-4943-8493-e3d56fa08348
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0b0b6013678fff79d1db55018a9c1a93b537c043
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="mapping-data-types-odbc-driver-for-oracle"></a>Mapping dei tipi di dati (Driver ODBC per Oracle)
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. In alternativa, utilizzare il driver ODBC fornito da Oracle.  
  
 Il Server Oracle supporta un set di tipi di dati. Il Driver ODBC per Oracle esegue il mapping di questi tipi di dati per i tipi di dati SQL ODBC appropriati. Nella tabella seguente sono elencati i tipi di dati Oracle Server 7.3 e i relativi tipi di dati SQL ODBC corrispondenti.  
  
 Il Driver ODBC per Oracle supporta Oracle 7.3 e alcuni tipi di dati Oracle8. Per ulteriori informazioni sui tipi di dati Oracle8 supportati, vedere [Supported Data Types](../../odbc/microsoft/supported-data-types-odbc-driver-for-oracle.md).  
  
|Tipo di dati del Server Oracle|Tipo di dati SQL ODBC|  
|-----------------------------|------------------------|  
|CHAR|SQL_CHAR|  
|DATE|SQL_TIMESTAMP|  
|FLOAT|SQL_DOUBLE|  
|INTEGER|SQL_DECIMAL|  
|LONG|SQL_LONGVARCHAR|  
|LONG RAW|SQL_LONGVARBINARY|  
|NUMBER|SQL_DECIMAL|  
|RAW|SQL_VARBINARY|  
|VARCHAR2|SQL_VARCHAR|  
  
> [!NOTE]  
>  Per ulteriori informazioni sulle dimensioni consentita della colonna VARCHAR, vedere [dimensioni colonne VARCHAR](../../odbc/microsoft/varchar-column-size-odbc-driver-for-oracle.md) in questa Guida.
