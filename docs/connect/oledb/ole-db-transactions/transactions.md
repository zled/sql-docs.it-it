---
title: Le transazioni | Documenti Microsoft
description: Transazioni in OLE DB Driver per SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-transactions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- transactions [OLE DB]
- OLE DB Driver for SQL Server, transactions
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: dd2978ab1778467561c4fab9f246922fb4dfdea2
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2018
---
# <a name="transactions"></a>Transazioni
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Il Driver OLE DB per SQL Server implementa il supporto delle transazioni locali. Il consumer può utilizzare transazioni distribuite o coordinate tramite Microsoft Distributed Transaction Coordinator (MS DTC). Per i consumer che necessitano di controllo delle transazioni che si estende su più sessioni, il Driver OLE DB per SQL Server può partecipare alle transazioni avviate e gestite da MS DTC.  
  
 Per impostazione predefinita, il Driver OLE DB per SQL Server utilizza una modalità di transazione con autocommit, in cui ogni azione discreta in una sessione del consumer comprende una transazione completa su un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Il Driver OLE DB per la modalità autocommit di SQL Server è locale, e transazioni con autocommit non coinvolgono mai più di una singola sessione.  
  
 Il Driver OLE DB per SQL Server espone il **ITransactionLocal** interfaccia, consentendo al consumer di utilizzare in modo esplicito e implicito le transazioni iniziali in un'unica connessione a un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Il Driver OLE DB per SQL Server non supporta le transazioni locali nidificate.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
  
-   [Supporto delle transazioni locali](../../oledb/ole-db-transactions/supporting-local-transactions.md)  
  
-   [Supporto di transazioni distribuite](../../oledb/ole-db-transactions/supporting-distributed-transactions.md)  
  
-   [I livelli di isolamento &#40;OLE DB&#41;](../../oledb/ole-db-transactions/isolation-levels-ole-db.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Driver OLE DB per SQL Server &#40;OLE DB&#41;](../../oledb/ole-db/oledb-driver-for-sql-server-ole-db.md)  
  
  
