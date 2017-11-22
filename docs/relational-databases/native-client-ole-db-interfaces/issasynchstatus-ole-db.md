---
title: ISSAsynchStatus (OLE DB) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-interfaces
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname: ISSAsynchStatus (OLE DB)
apitype: COM
helpviewer_keywords: ISSAsynchStatus interface
ms.assetid: c643f09f-9ccc-4d8b-9243-3cde86c2bd46
caps.latest.revision: "33"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0f97d1ca363452b6f8b91cc1d70794df200539e7
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="issasynchstatus-ole-db"></a>ISSAsynchStatus (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  **ISSAsynchStatus** espone il supporto per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] operazioni asincrone. Si tratta di un'interfaccia facoltativa eredita dall'interfaccia OLE DB principale **IDBAsynchStatus**. Oltre al **Abort** e **GetStatus** metodi ereditati da **IDBAsynchStatus**, **ISSAsynchStatus** fornisce un nuovo metodo utilizzato per attendere il completamento di un'operazione asincrona o si verifica un timeout.  
  
|Metodo|Description|  
|------------|-----------------|  
|[Issasynchstatus:: Abort &#40; OLE DB &#41;](../../relational-databases/native-client-ole-db-interfaces/issasynchstatus-abort-ole-db.md)|Annulla un'operazione di esecuzione asincrona.|  
|[Issasynchstatus:: GetStatus &#40; OLE DB &#41;](../../relational-databases/native-client-ole-db-interfaces/issasynchstatus-getstatus-ole-db.md)|Restituisce lo stato di un'operazione in esecuzione in modo asincrono.|  
|[Issasynchstatus:: &#40; OLE DB &#41;](../../relational-databases/native-client-ole-db-interfaces/issasynchstatus-waitforasynchcompletion-ole-db.md)|Resta in attesa fino al completamento dell'operazione di esecuzione asincrona o fino al verificarsi di un timeout.|  
  
## <a name="remarks"></a>Osservazioni  
 Il **ISSAsynchStatus** implementazione del **issasynchstatus:: GetStatus** metodo è identico di **idbasynchstatus:: GetStatus** la differenza che, se il inizializzazione di un oggetto origine dati viene interrotta, viene restituito E_UNEXPECTED anziché DB_E_CANCELED (benché **issasynchstatus::** restituisce DB_E_CANCELED). Ciò è dovuto al fatto che l'oggetto origine dati non viene lasciato nello stato consueto in seguito a un'operazione di interruzione, in modo da consentire ulteriori tentativi di operazioni di inizializzazione.  
  
 I metodi seguenti supportano l'utilizzo dell'esecuzione asincrona in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
-   **ICommand:: Execute**  
  
-   **IOpenRowset:: OPENROWSET**  
  
-   **IMultipleResults:: GetResult**  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce &#40; OLE DB &#41;](http://msdn.microsoft.com/library/34c33364-8538-45db-ae41-5654481cda93)   
 [Esecuzione di operazioni asincrone](../../relational-databases/native-client/features/performing-asynchronous-operations.md)  
  
  
