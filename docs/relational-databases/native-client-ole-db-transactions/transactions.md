---
title: Le transazioni | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client-ole-db-transactions
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- transactions [OLE DB]
- SQL Server Native Client OLE DB provider, transactions
ms.assetid: 3b41e33a-c1ca-4b2a-9464-312b0ed3ca89
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: ba537cca1ab2d746f12247019c0fa52d701e2d8e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="transactions"></a>Transazioni
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client implementa il supporto delle transazioni locali. Il consumer può utilizzare transazioni distribuite o coordinate tramite Microsoft Distributed Transaction Coordinator (MS DTC). Per i consumer che necessitano di controllo delle transazioni che si estende su più sessioni, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client può partecipare alle transazioni avviate e gestite da MS DTC.  
  
 Per impostazione predefinita, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client utilizza una modalità di transazione con autocommit, in cui ogni azione discreta in una sessione del consumer comprende una transazione completa su un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] modalità autocommit del provider OLE DB Native Client è locale, e le transazioni con autocommit non coinvolgono mai più di una singola sessione.  
  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client espone la **ITransactionLocal** interfaccia, che consente al consumer di utilizzare in modo esplicito e implicito le transazioni iniziali in un'unica connessione a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client non supporta le transazioni locali nidificate.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
  
-   [Supporto delle transazioni locali](../../relational-databases/native-client-ole-db-transactions/supporting-local-transactions.md)  
  
-   [Supporto di transazioni distribuite](../../relational-databases/native-client-ole-db-transactions/supporting-distributed-transactions.md)  
  
-   [I livelli di isolamento &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-transactions/isolation-levels-ole-db.md)  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
