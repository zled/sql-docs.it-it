---
title: ISSAsynchStatus (OLE DB) | Microsoft Docs
description: ISSAsynchStatus (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-interfaces
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISSAsynchStatus (OLE DB)
apitype: COM
helpviewer_keywords:
- ISSAsynchStatus interface
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: c228250560dd5e2e9dd3d3fd0ebf0d44f1651d9a
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "43032296"
---
# <a name="issasynchstatus-ole-db"></a>ISSAsynchStatus (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  L'interfaccia **ISSAsynchStatus** espone il supporto per operazioni asincrone di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Questa interfaccia facoltativa eredita dall'interfaccia OLE DB principale **IDBAsynchStatus**. Oltre ai metodi **Abort** e **GetStatus** ereditati da **IDBAsynchStatus**, **ISSAsynchStatus** fornisce un nuovo metodo, utilizzato per attendere il completamento dell'operazione asincrona o il verificarsi di un timeout.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Issasynchstatus:: Abort &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/issasynchstatus-abort-ole-db.md)|Annulla un'operazione di esecuzione asincrona.|  
|[Issasynchstatus:: GetStatus &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/issasynchstatus-getstatus-ole-db.md)|Restituisce lo stato di un'operazione in esecuzione in modo asincrono.|  
|[Issasynchstatus:: Waitforasynchcompletion &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/issasynchstatus-waitforasynchcompletion-ole-db.md)|Resta in attesa fino al completamento dell'operazione di esecuzione asincrona o fino al verificarsi di un timeout.|  
  
## <a name="remarks"></a>Remarks  
 L'implementazione **ISSAsynchStatus** del metodo **ISSAsynchStatus::GetStatus** coincide con quella del metodo **IDBAsynchStatus::GetStatus**, ad eccezione del fatto che se l'inizializzazione di un'origine dati viene interrotta, viene restituito E_UNEXPECTED anziché DB_E_CANCELED (benché **ISSAsynchStatus::WaitForAsynchCompletion** restituisca DB_E_CANCELED). Ciò è dovuto al fatto che l'oggetto origine dati non viene lasciato nello stato consueto in seguito a un'operazione di interruzione, in modo da consentire ulteriori tentativi di operazioni di inizializzazione.  
  
 I metodi seguenti supportano l'utilizzo dell'esecuzione asincrona in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]:  
  
-   **ICommand::Execute**  
  
-   **IOpenRowset::OpenRowset**  
  
-   **IMultipleResults::GetResult**  
  
## <a name="see-also"></a>Vedere anche  
 [Le interfacce &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/oledb-driver-for-sql-server-ole-db-interfaces.md)    
 [Esecuzione di operazioni asincrone](../../oledb/features/performing-asynchronous-operations.md)  
  
  
