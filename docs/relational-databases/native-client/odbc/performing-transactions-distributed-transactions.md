---
title: Esecuzione di transazioni distribuite | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client|ODBC
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- MS DTC, performing distributed transactions
- SQL Server Native Client ODBC driver, transactions
- distributed transactions [ODBC]
- transactions [ODBC]
- ODBC, transactions
ms.assetid: 2c17fba0-7a3c-453c-91b7-f801e7b39ccb
caps.latest.revision: 36
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 2e75f8506a1bb7d58dd9e9669b241031d118ea4b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="performing-transactions---distributed-transactions"></a>Esecuzione di transazioni - transazioni distribuite
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Microsoft Distributed Transaction Coordinator (MS DTC) consente alle applicazioni di estendere le transazioni su due o più istanze di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], nonché di partecipare a transazioni gestite da gestori transazioni conformi allo standard DTP XA dell'Open Group.  
  
 In genere tutti i comandi di gestione delle transazioni vengono inviati al server tramite il driver ODBC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. L'applicazione viene avviata una transazione chiamando [SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) con la modalità autocommit disabilitata. Esegue quindi gli aggiornamenti che comprendono la transazione e chiama [SQLEndTran](../../../relational-databases/native-client-odbc-api/sqlendtran.md) con l'opzione SQL_COMMIT o SQL_ROLLBACK.  
  
 Quando si utilizza MS DTC, tuttavia, MS DTC diventa il gestore delle transazioni e l'applicazione non utilizza più **SQLEndTran**.  
  
 Dopo aver eseguito l'integrazione in una transazione distribuita e, successivamente, aver effettuato la stessa operazione in una seconda transazione distribuita, il driver ODBC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client viene escluso dalla transazione distribuita originale e ne viene eseguita l'integrazione nella nuova transazione. Per ulteriori informazioni, vedere [di riferimento per programmatori di DTC](http://msdn.microsoft.com/library/ms686108\(VS.85\).aspx).  
  
## <a name="see-also"></a>Vedere anche  
 [Esecuzione di transazioni & #40; ODBC & #41;](http://msdn.microsoft.com/library/f431191a-5762-4f0b-85bb-ac99aff29724)  
  
  
