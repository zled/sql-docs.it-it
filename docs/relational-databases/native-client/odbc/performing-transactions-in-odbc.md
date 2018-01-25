---
title: Le transazioni in ODBC | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client|ODBC
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, transactions
- transactions [ODBC]
- ODBC, transactions
ms.assetid: c5a87fa5-827a-4e6f-a0d9-924bac881eb0
caps.latest.revision: "30"
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e2984304ae15715e5a105fa5d6b3272f518cde28
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="performing-transactions-in-odbc"></a>Esecuzione di transazioni in ODBC
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Le transazioni in ODBC vengono gestite a livello di connessione. Quando un'applicazione completa una transazione, esegue il commit o il rollback di tutte le operazioni effettuate tramite tutti gli handle di istruzione nella connessione. Per eseguire il commit o rollback della transazione, le applicazioni devono chiamare [SQLEndTran](../../../relational-databases/native-client-odbc-api/sqlendtran.md) anziché inviare un'istruzione COMMIT o ROLLBACK.  
  
 Un'applicazione chiama [SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) per passare tra le due modalità ODBC di gestione delle transazioni:  
  
-   Modalità autocommit  
  
     Di ogni istruzione completata correttamente viene automaticamente eseguito il commit. Quando si utilizza la modalità autocommit, non sono necessarie altre funzioni di gestione delle transazioni.  
  
-   Modalità di commit manuale  
  
     Tutte le istruzioni eseguite sono inclusi nella stessa transazione fino a quando non è stato arrestato in modo specifico chiamando **SQLEndTran**.  
  
 La modalità autocommit è la modalità di esecuzione delle transazioni predefinita per ODBC. Quando viene stabilita una connessione, è in modalità autocommit fino a **SQLSetConnectAttr** viene chiamato per disattivare la modalità di commit manuale modalità autocommit. Quando un'applicazione disattiva l'autocommit, l'istruzione successiva inviata al database avvia una transazione. La transazione rimane attiva fino a quando l'applicazione chiama **SQLEndTran** con le opzioni di SQL_COMMIT o SQL_ROLLBACK. Il comando inviato al database dopo **SQLEndTran** avvia la transazione successiva.  
  
 Se un'applicazione passa dalla modalità di commit manuale alla modalità autocommit, il driver esegue il commit di tutte le transazioni attualmente aperte nella connessione.  
  
 Le applicazioni ODBC non devono utilizzare istruzioni per transazioni Transact-SQL quali BEGIN TRANSACTION, COMMIT TRANSACTION o ROLLBACK TRANSACTION, in quanto tali istruzioni possono provocare un comportamento imprevedibile nel driver. Un'applicazione ODBC deve eseguita in modalità autocommit e non utilizzare le funzioni di gestione delle transazioni o istruzioni, oppure eseguire in modalità di commit manuale e utilizzare ODBC **SQLEndTran** funzione per eseguire il commit o il rollback delle transazioni.  
  
## <a name="see-also"></a>Vedere anche  
 [Esecuzione di transazioni &#40; ODBC &#41;](http://msdn.microsoft.com/library/f431191a-5762-4f0b-85bb-ac99aff29724)  
  
  
