---
title: Trasferimento dati in forma binaria | Documenti Microsoft
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
- data types [ODBC], transferring in binary form
- transferring data in binary form [ODBC]
- binary data transfers [ODBC]
ms.assetid: 4b12a9de-51d0-416a-87f4-9bf84959cad9
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d2d1227af9eeb303bc0d9bc56733e6bda9b5325c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="transferring-data-in-its-binary-form"></a>Trasferimento dei dati in forma binaria
In modo sicuro, un'applicazione può trasferire i dati (nel formato interno usato da un sistema DBMS specificato) tra due origini dati che utilizzano la stessa DBMS e la piattaforma hardware. Per una determinata parte dei dati, i tipi di dati SQL devono essere uguale nelle origini dei dati di origine e di destinazione. Il tipo di dati C è SQL_C_BINARY.  
  
 Quando l'applicazione chiama **SQLFetch**, **SQLFetchScroll**, o **SQLGetData** per recuperare i dati dall'origine dei dati di origine, il driver recupera i dati dai dati origine e li trasferisce, senza conversione, in un percorso di archiviazione di tipo SQL_C_BINARY. Quando l'applicazione chiama **SQLBulkOperations**, **SQLExecute**, **SQLExecDirect**, **SQLPutData o SQLSetPos** per inviare i dati origine dati di destinazione, il driver recupera i dati dal percorso di archiviazione e lo trasferisce, senza conversione, all'origine dati di destinazione.  
  
> [!NOTE]  
>  Le applicazioni che trasferiscono i dati (tranne i dati binari) in questo modo non sono interoperativi tra DBMS.  
  
 **SQLCopyDesc** può essere utilizzato per copiare le associazioni di riga da DBMS di origine per le associazioni di parametri nel sistema DBMS di destinazione.
