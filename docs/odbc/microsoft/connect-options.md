---
title: Opzioni di connessione | Documenti Microsoft
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
- connection options [ODBC]
- ODBC driver for Oracle [ODBC], connection options
- custom connection options [ODBC]
ms.assetid: abfdc133-cb33-435f-a467-fbe15444f687
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 43cb42e7d77cbf3471f2475af5290ba045db05fa
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="connect-options"></a>Opzioni di connessione
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. In alternativa, utilizzare il driver ODBC fornito da Oracle.  
  
 Queste opzioni consentono la personalizzazione della connessione di database all'interno di un'applicazione.  
  
|Opzione di connessione|Note|  
|--------------------|-----------|  
|SQL_AUTOCOMMIT|Se si sceglie SQL_AUTOCOMMIT_OFF, l'applicazione deve esplicitamente eseguire il commit o il rollback delle transazioni con [SQLTransact](../../odbc/microsoft/core-level-api-functions-odbc-driver-for-oracle.md).|  
|SQL_ODBC_CURSORS|L'attributo di connessione viene implementato in Gestione Driver.|  
|SQL_OPT_TRACE|L'attributo di connessione viene implementato in Gestione Driver.|  
|SQL_OPT_TRACEFILE|L'attributo di connessione viene implementato in Gestione Driver.|  
|SQL_TRANSLATE_DLL|Restituisce l'errore: "Driver non valido".|  
|SQL_TRANSLATE_OPTION|La DLL di conversione passato un valore a 32 bit.|  
|SQL_TXN_ISOLATION|Il driver consente solo SQL_TXN_READ_COMMITTED.<br /><br /> Non sono supportati i seguenti vParams:<br /><br /> SQL_TXN_READ_UNCOMMITTED<br /><br /> SQL_TXN_REAPEATABLE_READ<br /><br /> SQL_TXN_SERIALIZABLE|  
|SQL_ATTR_ENLIST_IN_DTC|Questo attributo di connessione ODBC 3.0 consente di utilizzare il Driver ODBC per Oracle in transazioni distribuite coordinate da Servizi componenti di Microsoft (o MTS, se si utilizza Windows NT). Fornisce il puntatore di interfaccia *pITransaction* alla transazione come il *vParam* argomento.|  
|SQL_ATTR_CONNECTION_DEAD|L'attributo di connessione ODBC 3.5 di sola lettura consente di determinare se la connessione al server Oracle non è riuscita. Get di sola lettura. Impossibile impostare.|
