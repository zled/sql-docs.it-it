---
title: Le transazioni in ODBC | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client  - "database-engine" - "docset-sql-devref"
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, transactions
- transactions [ODBC]
- ODBC, transactions
ms.assetid: c5a87fa5-827a-4e6f-a0d9-924bac881eb0
caps.latest.revision: 29
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cc91460599df7fff2bed9c7a7a20991b8bae3b57
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37425670"
---
# <a name="transactions-in-odbc"></a>Transazioni in ODBC
  Le transazioni in ODBC vengono gestite a livello di connessione. Quando un'applicazione completa una transazione, esegue il commit o il rollback di tutte le operazioni effettuate tramite tutti gli handle di istruzione nella connessione. Per eseguire il commit o rollback della transazione, le applicazioni devono chiamare [SQLEndTran](../../native-client-odbc-api/sqlendtran.md) anziché inviare un'istruzione COMMIT o ROLLBACK.  
  
 Un'applicazione chiama [SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md) per passare tra le due modalità ODBC di gestione delle transazioni:  
  
-   Modalità autocommit  
  
     Di ogni istruzione completata correttamente viene automaticamente eseguito il commit. Quando si utilizza la modalità autocommit, non sono necessarie altre funzioni di gestione delle transazioni.  
  
-   Modalità di commit manuale  
  
     Tutte le istruzioni eseguite sono inclusi nella stessa transazione fino a quando non viene arrestata in modo chiamando **SQLEndTran**.  
  
 La modalità autocommit è la modalità di esecuzione delle transazioni predefinita per ODBC. Quando viene stabilita una connessione, è in modalità autocommit finché **SQLSetConnectAttr** viene chiamato per passare alla modalità di commit manuale modalità autocommit off. Quando un'applicazione disattiva l'autocommit, l'istruzione successiva inviata al database avvia una transazione. La transazione rimane attiva finché l'applicazione chiama **SQLEndTran** con l'opzione SQL_COMMIT o SQL_ROLLBACK. Il comando inviato al database dopo aver **SQLEndTran** avvia la transazione successiva.  
  
 Se un'applicazione passa dalla modalità di commit manuale alla modalità autocommit, il driver esegue il commit di tutte le transazioni attualmente aperte nella connessione.  
  
 Le applicazioni ODBC non devono utilizzare istruzioni per transazioni Transact-SQL quali BEGIN TRANSACTION, COMMIT TRANSACTION o ROLLBACK TRANSACTION, in quanto tali istruzioni possono provocare un comportamento imprevedibile nel driver. Un'applicazione ODBC deve eseguita in modalità autocommit e non utilizzare eventuali funzioni di gestione della transazione o più istruzioni, oppure eseguire in modalità di commit manuale e utilizzare ODBC **SQLEndTran** funzione per eseguire il commit o il rollback delle transazioni.  
  
## <a name="see-also"></a>Vedere anche  
 [Esecuzione di transazioni di &#40;ODBC&#41;](../../../database-engine/dev-guide/performing-transactions-odbc.md)  
  
  
