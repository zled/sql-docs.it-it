---
title: L'aggiornamento dei dati nei cursori SQL Server | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-rowsets
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- updating data [SQL Server]
- isolation levels [SQL Server]
- delayed update mode [OLE DB]
- immediate update mode [OLE DB]
- cursors [OLE DB]
- data updates [SQL Server], OLE DB
ms.assetid: 732dafee-f2d5-4aef-aad7-3a8bf3b1e876
caps.latest.revision: "31"
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 50086b561ecc6487e9cb13a04e33a8cb8ca8fdad
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2018
---
# <a name="updating-data-in-sql-server-cursors"></a>Aggiornamento dei dati nei cursori di SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Durante il recupero e l'aggiornamento dei dati tramite [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] i cursori, un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] applicazione consumer del provider OLE DB Native Client è associato mediante le stesse considerazioni e vincoli che si applicano a qualsiasi altra applicazione client.  
  
 Solo le righe dei cursori [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] partecipano al controllo di accesso ai dati simultaneo. Quando il consumer richiede un set di righe modificabile, il controllo della concorrenza viene effettuato da DBPROP_LOCKMODE. Per modificare il livello di controllo di accesso simultaneo, il consumer imposta la proprietà DBPROP_LOCKMODE prima di aprire il set di righe.  
  
 I livelli di isolamento della transazione possono provocare ritardi significativi nel posizionamento delle righe se la progettazione delle applicazioni client lascia aperte le transazioni per lunghi periodi di tempo. Per impostazione predefinita, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client utilizza il livello di isolamento read committed specificato da DBPROPVAL_TI_READCOMMITTED. Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client supporta l'isolamento di lettura dirty quando la concorrenza del set di righe è di sola lettura. In un set di righe modificabile il consumer può pertanto richiedere un livello di isolamento superiore ma non inferiore.  
  
## <a name="immediate-and-delayed-update-modes"></a>Modalità di aggiornamento immediato e posticipato  
 In modalità di aggiornamento immediato ogni chiamata a **IRowsetChange:: SetData** provoca un round trip per il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Se il consumer apporta più modifiche a una singola riga, risulta più efficiente per inviare tutte le modifiche con una singola **SetData** chiamare.  
  
 In modalità di aggiornamento posticipato viene effettuato un round trip di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per ogni riga indicata nel *cRows* e *rghRows* parametri di **IRowsetUpdate:: Update**.  
  
 In entrambe le modalità un round trip rappresenta una transazione distinta quando per il set di righe non è aperto alcun oggetto transazione.  
  
 Quando si utilizza **IRowsetUpdate:: Update**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client tenta di elaborare ogni riga indicata. Errore che si verifica a causa di valori di dati, la lunghezza o lo stato non validi per tutte le righe non Arresta [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dell'elaborazione del provider OLE DB Native Client. È possibile che vengano modificate tutte o nessuna delle altre righe che partecipano all'aggiornamento. Il consumer deve esaminare la *prgRowStatus* matrice per determinare l'errore per una specifica riga quando il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client restituisce DB_S_ERRORSOCCURRED.  
  
 Un consumer non deve presupporre che le righe vengano elaborate in base a un ordine specifico. Se un consumer richiede un'elaborazione ordinata di modifica dei dati su più di una riga, deve stabilire l'ordine nella logica dell'applicazione e aprire una transazione per includere il processo.  
  
## <a name="see-also"></a>Vedere anche  
 [L'aggiornamento dei dati nei set di righe](../../relational-databases/native-client-ole-db-rowsets/updating-data-in-rowsets.md)  
  
  
