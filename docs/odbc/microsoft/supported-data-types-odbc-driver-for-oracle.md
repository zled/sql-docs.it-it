---
title: Tipi di dati, il Driver ODBC per Oracle, supportati | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], data types
ms.assetid: 21d5f8d9-a3aa-4aa4-bc37-ff8bc90c0870
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fdaf1256c358f5623ef7b9d7bdfeb22f333a8606
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="supported-data-types-odbc-driver-for-oracle"></a>Tipi di dati supportati (Driver ODBC per Oracle)
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. In alternativa, utilizzare il driver ODBC fornito da Oracle.  
  
 Il Driver ODBC per Oracle supporta tutti i tipi di dati Oracle 7.3. Tuttavia, non supporta i nuovi tipi di dati Oracle8 elencati di seguito.  
  
|Tipo di dati|Oracle 7.3|Oracle8|  
|---------------|----------------|-------------|  
|BFILE|n/d|Non supportato|  
|BLOB|n/d|Non supportato|  
|CHAR|Supported|Supported|  
|CLOB|n/d|Non supportato|  
|DATE|Supported|Supported|  
|FLOAT|Supported|Supported|  
|INTEGER|Supported|Supported|  
|LONG|Supported|Supported|  
|LONG RAW|Supported|Supported|  
|NCHAR|n/d|Non supportato|  
|NCLOB|n/d|Non supportato|  
|NUMBER|Supported|Supported|  
|NVARCHAR2|n/d|Non supportato|  
|RAW|Supported|Supported|  
|VARCHAR2|Supported|Supported|  
|MLSLABEL|Non supportato.|Non supportato.|  
  
> [!NOTE]  
>  Per ulteriori informazioni sulle dimensioni consentita della colonna VARCHAR, vedere [dimensioni colonne VARCHAR](../../odbc/microsoft/varchar-column-size-odbc-driver-for-oracle.md) in questa Guida.
