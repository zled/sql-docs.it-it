---
title: I messaggi di errore | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-error-messages
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, errors
- messages [ODBC], types
- ODBC error handling, message types
- errors [ODBC], types
ms.assetid: 46c0c22e-d105-4d5b-bb9d-5694472e8651
caps.latest.revision: "34"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b983536d9b7214816623bbd0c086674d75599263
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="error-messages"></a>messaggi di errore
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Il testo dei messaggi restituiti dal [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client viene inserito nella *MessageText* parametro di **SQLGetDiagRec**. L'origine di un errore viene indicata dall'intestazione del messaggio:  
  
 [Microsoft][Gestione driver ODBC]  
 Questi errori vengono generati da Gestione driver ODBC.  
  
 [Microsoft][Libreria di cursori ODBC]  
 Questi errori vengono generati dalla libreria di cursori ODBC.  
  
 [Microsoft][SQL Server Native Client]  
 Questi errori vengono generati dal [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client. Se non sono presenti altri nodi con il nome di una libreria di rete o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], l'errore è stato rilevato nel driver.  
  
 [Microsoft] [SQL Server Native Client] [*Net-Transportname*]  
 Questi errori vengono generati dal [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] libreria di rete, in cui *Net-Transportname* è il nome visualizzato di un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] trasporto di rete client (ad esempio, Named Pipes, Shared Memory, TCP/IP Sockets o VIA). Il resto del messaggio di errore contiene la funzione della libreria di rete chiamata e la funzione chiamata nell'API di rete sottostante dalla funzione TDS. Il *pfNative* codice di errore restituito con questi errori è il codice di errore dallo stack di protocolli di rete sottostante.  
  
 [Microsoft][SQL Server Native Client][[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]]  
 Questi errori vengono generati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il resto del messaggio di errore corrisponde al testo del messaggio di errore restituito da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il *pfNative* codice restituito con questi errori è il numero di errore [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per ulteriori informazioni su un elenco di messaggi di errore (e i relativi numeri) che può essere restituito da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vedere le colonne della descrizione e l'errore il **sysmessages** tabella di sistema di **master** database in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione di errori e messaggi](../../relational-databases/native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
  
