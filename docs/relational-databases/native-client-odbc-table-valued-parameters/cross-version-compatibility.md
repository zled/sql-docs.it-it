---
title: Compatibilità tra versioni | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), cross-version compatibility
ms.assetid: 5f14850b-b85c-41e2-8116-6f5b3f5e0856
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: e124885ed8acb240a004d255c6d5b1f49ee30bf3
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2018
ms.locfileid: "35697502"
---
# <a name="cross-version-compatibility"></a>Compatibilità tra versioni
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Possono verificarsi conflitti tra versioni quando è previsto che istanze client o server di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] precedenti a [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] elaborino parametri con valori di tabella.  
  
 In generale, la funzionalità dei parametri con valori di tabella è disponibile solo per i client [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] che utilizzano SQL Server Native Client 10.0 o versione successiva e che sono connessi a server [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] o versione successiva. Le nuove colonne nei set di risultati di funzione di catalogo saranno presenti solo quando si è connessi a un [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (o versione successiva) server.  
  
 Se un'applicazione client compilata con una versione precedente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client esegue istruzioni per le quali sono previsti parametri con valori di tabella, il server rileva questa condizione mediante un errore di conversione dei dati e ODBC restituisce l'errore SQLSTATE 07006 e il messaggio "Violazione dell'attributo del tipo di dati".  
  
 Se un'applicazione client che è stata compilata con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 10.0 o versione successiva tenta di utilizzare i parametri con valori di tabella quando si è connessi a un'istanza del server precedente a [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client rileverà la situazione, SQLBindCol e Chiamate di SQLBindParameter SQLSetDescFields e SQLSetDescRec avranno esito negativo con SQLSTATE 07006 e il messaggio "Violazione dell'attributo tipo dati (la versione di SQL Server per questa connessione non supporta i parametri con valori di tabella) Restricted".  
  
## <a name="see-also"></a>Vedere anche  
 [Table-Valued Parameters &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
  
