---
title: ExecuteOptionEnum | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- ExecuteOptionEnum
helpviewer_keywords:
- ExecuteOptionEnum enumeration [ADO]
ms.assetid: 68bfa83a-5df4-4bef-8736-0f88ae8c29ea
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8e4d901326e801d9c6724dfd05d7a14bb7acd8b7
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="executeoptionenum"></a>ExecuteOptionEnum
Specifica come un provider deve eseguire un comando.  
  
|Costante|Valore|Description|  
|--------------|-----------|-----------------|  
|**adAsyncExecute**|0x10|Indica che il comando deve essere eseguito in modo asincrono.<br /><br /> Questo valore non può essere combinato con il [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md) valore **adCmdTableDirect**.|  
|**adAsyncFetch**|0x20|Indica che le altre righe dopo la quantità iniziale specificato nel [CacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md) proprietà deve essere recuperata in modo asincrono.|  
|**adAsyncFetchNonBlocking**|0x40|Indica che il thread principale non si blocca durante il recupero. Se la riga richiesta non è stata recuperata, la riga corrente verrà spostato automaticamente alla fine del file.<br /><br /> Se si apre un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) da un [flusso](../../../ado/reference/ado-api/stream-object-ado.md) contenente memorizzato in modo permanente **Recordset**, **adAsyncFetchNonBlocking** non avrà un effetto. l'operazione verrà ritentata sincrono e di blocco.<br /><br /> **adAsynchFetchNonBlocking** non ha alcun effetto quando il [adCmdTableDirect](../../../ado/reference/ado-api/commandtypeenum.md) opzione viene utilizzata per aprire la **Recordset**.|  
|**adExecuteNoRecords**|0x80|Indica che il testo del comando è un comando o stored procedure che non restituisce righe (ad esempio, un comando che viene inserito solo dati). Se tutte le righe vengono recuperate, sono ignorati e non viene restituiti.<br /><br /> **adExecuteStream** può solo essere passato come parametro facoltativo per il **comando** o **connessione eseguire** metodo.|  
|**adExecuteStream**|0x400|Indica che i risultati di un'esecuzione del comando devono essere restituiti come flusso.<br /><br /> **adExecuteStream** può solo essere passato come parametro facoltativo per il **comando eseguito** metodo.|  
|**adExecuteRecord**||Indica che il **CommandText** è un comando o stored procedure che restituisce una singola riga che deve essere restituita come un **Record** oggetto.|  
|**adOptionUnspecified**|-1|Indica che il comando non è specificato.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC equivalente  
 Package: **com.ms.wfc.data**  
  
|Costante|  
|--------------|  
|AdoEnums.ExecuteOption.ASYNCEXECUTE|  
|AdoEnums.ExecuteOption.ASYNCFETCH|  
|AdoEnums.ExecuteOption.ASYNCFETCHNONBLOCKING|  
|AdoEnums.ExecuteOption.NORECORDS|  
|AdoEnums.ExecuteOption.UNSPECIFIED|  
  
## <a name="applies-to"></a>Si applica a  
  
|||  
|-|-|  
|[Metodo Execute (comando ADO)](../../../ado/reference/ado-api/execute-method-ado-command.md)|[Metodo Execute (connessione ADO)](../../../ado/reference/ado-api/execute-method-ado-connection.md)|  
|[Metodo Open (Recordset ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)|[Metodo Requery](../../../ado/reference/ado-api/requery-method.md)|
