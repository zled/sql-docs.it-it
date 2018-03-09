---
title: "Compatibilità tra versioni | Documenti Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-table-valued-parameters
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), cross-version compatibility
ms.assetid: 5f14850b-b85c-41e2-8116-6f5b3f5e0856
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3fd2c2240e014fa4b7ff9d51ce94419b6cde839a
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2018
---
# <a name="cross-version-compatibility"></a>Compatibilità tra versioni
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Possono verificarsi conflitti tra versioni quando è previsto che istanze client o server di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] precedenti a [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] elaborino parametri con valori di tabella.  
  
 In generale, la funzionalità dei parametri con valori di tabella è disponibile solo per i client [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] che utilizzano SQL Server Native Client 10.0 o versione successiva e che sono connessi a server [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] o versione successiva. Le nuove colonne nei set di risultati di funzione di catalogo saranno presenti solo quando si è connessi a un [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (o versione successiva) server.  
  
 Se un'applicazione client compilata con una versione precedente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client esegue istruzioni per le quali sono previsti parametri con valori di tabella, il server rileva questa condizione mediante un errore di conversione dei dati e ODBC restituisce l'errore SQLSTATE 07006 e il messaggio "Violazione dell'attributo del tipo di dati".  
  
 Se un'applicazione client che è stata compilata con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 10.0 o versione successiva tenta di utilizzare i parametri con valori di tabella quando si è connessi a un'istanza del server precedente a [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client rileva il problema, SQLBindCol e Chiamate di SQLBindParameter SQLSetDescFields e SQLSetDescRec avranno esito negativo con SQLSTATE 07006 e il messaggio "Violazione dell'attributo tipo dati (la versione di SQL Server per questa connessione non supporta i parametri con valori di tabella) con restrizioni".  
  
## <a name="see-also"></a>Vedere anche  
 [Table-Valued parametri &#40; ODBC &#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
  
