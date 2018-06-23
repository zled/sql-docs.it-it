---
title: Esecuzione delle transazioni distribuite | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- MS DTC, performing distributed transactions
- SQL Server Native Client ODBC driver, transactions
- distributed transactions [ODBC]
- transactions [ODBC]
- ODBC, transactions
ms.assetid: 2c17fba0-7a3c-453c-91b7-f801e7b39ccb
caps.latest.revision: 35
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2d6c03f674722e817fc8c16dd712572c3236e73d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36066728"
---
# <a name="performing-distributed-transactions"></a>Esecuzione delle transazioni distribuite
  Microsoft Distributed Transaction Coordinator (MS DTC) consente alle applicazioni di estendere le transazioni su due o più istanze di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], nonché di partecipare a transazioni gestite da gestori transazioni conformi allo standard DTP XA dell'Open Group.  
  
 In genere tutti i comandi di gestione delle transazioni vengono inviati al server tramite il driver ODBC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. L'applicazione avvia una transazione chiamando [SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md) con la modalità autocommit disabilitata. Esegue quindi gli aggiornamenti che comprendono la transazione e chiama [SQLEndTran](../../native-client-odbc-api/sqlendtran.md) con l'opzione SQL_COMMIT o SQL_ROLLBACK.  
  
 Quando si utilizza MS DTC, tuttavia, MS DTC diventa il gestore delle transazioni e l'applicazione non viene più usata **SQLEndTran**.  
  
 Dopo aver eseguito l'integrazione in una transazione distribuita e, successivamente, aver effettuato la stessa operazione in una seconda transazione distribuita, il driver ODBC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client viene escluso dalla transazione distribuita originale e ne viene eseguita l'integrazione nella nuova transazione. Per altre informazioni, vedere [di riferimento per programmatori di DTC](http://msdn.microsoft.com/library/ms686108\(VS.85\).aspx).  
  
## <a name="see-also"></a>Vedere anche  
 [L'esecuzione di transazioni &#40;ODBC&#41;](../../../database-engine/dev-guide/performing-transactions-odbc.md)  
  
  