---
title: Utilizzare Microsoft Distributed Transaction Coordinator (ODBC) | Documenti di Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- MS DTC, using
ms.assetid: 12a275e1-8c7e-436d-8a4e-b7bee853b35c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 02c1c7196134d1ffc5f268d8f2d4a162fbec6e5c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48144751"
---
# <a name="use-microsoft-distributed-transaction-coordinator-odbc"></a>Utilizzare Microsoft Distributed Transaction Coordinator (ODBC).
    
### <a name="to-update-two-or-more-sql-servers-by-using-ms-dtc"></a>Per aggiornare due o più computer SQL Server mediante MS DTC  
  
1.  Connettersi a MS DTC utilizzando la funzione MS DTC OLE DtcGetTransactionManager. Per informazioni su MS DTC, vedere Microsoft Distributed Transaction Coordinator.  
  
2.  Chiamare SQL DriverConnect una volta per ogni connessione Microsoft® SQL Server™ che si desidera stabilire.  
  
3.  Chiamare la funzione MS DTC OLE ITransactionDispenser::BeginTransaction per iniziare una transazione MS DTC e ottenere un oggetto Transaction che rappresenta la transazione.  
  
4.  Chiamare [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) una o più volte per ogni connessione ODBC che si desidera integrare nella transazione MS DTC. Il secondo parametro [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) deve essere SQL_ATTR_ENLIST_IN_DTC mentre il terzo parametro deve essere l'oggetto Transaction, ottenuto nel passaggio 3.  
  
5.  Chiamare [SQLExecDirect](http://go.microsoft.com/fwlink/?LinkId=58399) una volta per ogni computer SQL Server da aggiornare.  
  
6.  Chiamare la funzione MS DTC OLE ITransaction::Commit per eseguire il commit della transazione MS DTC. L'oggetto Transaction non è più valido.  
  
 Per eseguire una serie di transazioni MS DTC, ripetere i passaggi da 3 a 6.  
  
 Per rilasciare il riferimento all'oggetto Transaction, chiamare la funzione MS DTC OLE ITransaction::Return.  
  
 Per usare una connessione ODBC con una transazione MS DTC e quindi usare la stessa connessione con una transazione di SQL Server locale, chiamare [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) con SQL_DTC_DONE.  
  
> [!NOTE]  
>  È inoltre possibile chiamare [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) e [SQLExecDirect](http://go.microsoft.com/fwlink/?LinkId=58399) per ogni computer SQL Server anziché come suggerito nei passaggi 4 e 5.  
  
## <a name="see-also"></a>Vedere anche  
 [Esecuzione di transazioni di &#40;ODBC&#41;](../../database-engine/dev-guide/performing-transactions-odbc.md)  
  
  
