---
title: Le transazioni | Documenti Microsoft
description: Transazioni in OLE DB Driver per SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-transactions
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- transactions [OLE DB]
- OLE DB Driver for SQL Server, transactions
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 1f1e0b252960468e443b157c7c95213809a4d318
ms.sourcegitcommit: 03ba89937daeab08aa410eb03a52f1e0d212b44f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/16/2018
ms.locfileid: "35689314"
---
# <a name="transactions"></a>Transazioni
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Il Driver OLE DB per SQL Server implementa il supporto delle transazioni locali. Il consumer può utilizzare transazioni distribuite o coordinate tramite Microsoft Distributed Transaction Coordinator (MS DTC). Per i consumer che necessitano di controllo delle transazioni che si estende su più sessioni, il Driver OLE DB per SQL Server può partecipare alle transazioni avviate e gestite da MS DTC.  
  
 Per impostazione predefinita, il Driver OLE DB per SQL Server utilizza una modalità di transazione con autocommit, in cui ogni azione discreta in una sessione del consumer comprende una transazione completa su un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Il Driver OLE DB per la modalità autocommit di SQL Server è locale, e transazioni con autocommit non coinvolgono mai più di una singola sessione.  
  
 Il Driver OLE DB per SQL Server espone il **ITransactionLocal** interfaccia, consentendo al consumer di utilizzare in modo esplicito e implicito le transazioni iniziali in un'unica connessione a un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Il Driver OLE DB per SQL Server non supporta le transazioni locali nidificate.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
-   [Supporto delle transazioni locali](../../oledb/ole-db-transactions/supporting-local-transactions.md)  
  
-   [Supporto di transazioni distribuite](../../oledb/ole-db-transactions/supporting-distributed-transactions.md)  
  
-   [I livelli di isolamento &#40;OLE DB&#41;](../../oledb/ole-db-transactions/isolation-levels-ole-db.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Driver OLE DB per programmazione con SQL Server](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)  
  
  
