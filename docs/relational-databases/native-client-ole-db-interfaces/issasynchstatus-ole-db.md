---
title: ISSAsynchStatus (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISSAsynchStatus (OLE DB)
apitype: COM
helpviewer_keywords:
- ISSAsynchStatus interface
ms.assetid: c643f09f-9ccc-4d8b-9243-3cde86c2bd46
caps.latest.revision: 33
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 298d4cc68472939e6c6cba360c795a99a5aa1696
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37421140"
---
# <a name="issasynchstatus-ole-db"></a>ISSAsynchStatus (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  **ISSAsynchStatus** espone il supporto per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] operazioni asincrone. Si tratta di un'interfaccia facoltativa eredita dall'interfaccia OLE DB principale **IDBAsynchStatus**. Oltre al **Abort** e **GetStatus** metodi ereditati dalla **IDBAsynchStatus**, **ISSAsynchStatus** fornisce un nuovo metodo che viene usato per attendere fino a quando non è stata completata un'operazione asincrona o si verifica un timeout.  
  
|Metodo|Description|  
|------------|-----------------|  
|[Issasynchstatus:: Abort &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/issasynchstatus-abort-ole-db.md)|Annulla un'operazione di esecuzione asincrona.|  
|[Issasynchstatus:: GetStatus &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/issasynchstatus-getstatus-ole-db.md)|Restituisce lo stato di un'operazione in esecuzione in modo asincrono.|  
|[Issasynchstatus:: Waitforasynchcompletion &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/issasynchstatus-waitforasynchcompletion-ole-db.md)|Resta in attesa fino al completamento dell'operazione di esecuzione asincrona o fino al verificarsi di un timeout.|  
  
## <a name="remarks"></a>Note  
 Il **ISSAsynchStatus** implementazione delle **issasynchstatus:: GetStatus** metodo è identico il **idbasynchstatus:: GetStatus** metodo ad eccezione che se la inizializzazione di un oggetto origine dati viene interrotta, viene restituito E_UNEXPECTED anziché DB_E_CANCELED (benché **issasynchstatus:: Waitforasynchcompletion** restituisce DB_E_CANCELED). Ciò è dovuto al fatto che l'oggetto origine dati non viene lasciato nello stato consueto in seguito a un'operazione di interruzione, in modo da consentire ulteriori tentativi di operazioni di inizializzazione.  
  
 I metodi seguenti supportano l'utilizzo dell'esecuzione asincrona in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
-   **ICommand:: Execute**  
  
-   **IOpenRowset::OpenRowset**  
  
-   **IMultipleResults:: GetResult**  
  
## <a name="see-also"></a>Vedere anche  
 [Le interfacce &#40;OLE DB&#41;](http://msdn.microsoft.com/library/34c33364-8538-45db-ae41-5654481cda93)   
 [Esecuzione di operazioni asincrone](../../relational-databases/native-client/features/performing-asynchronous-operations.md)  
  
  
