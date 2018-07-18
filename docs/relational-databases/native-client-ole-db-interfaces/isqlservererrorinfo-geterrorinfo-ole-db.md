---
title: 'ISQLServerErrorInfo:: GetErrorInfo (OLE DB) | Microsoft Docs'
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISQLServerErrorInfo::GetErrorInfo (OLE DB)
apitype: COM
helpviewer_keywords:
- GetErrorInfo method
ms.assetid: 83265c9c-eaf9-41f0-9f73-b0ae0972f0d5
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 0a157d42f4bb464cef821f344d0218ecd150e76f
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37410602"
---
# <a name="isqlservererrorinfogeterrorinfo-ole-db"></a>ISQLServerErrorInfo::GetErrorInfo (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Restituisce un puntatore a un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] struttura SSERRORINFO del provider OLE DB Native Client contenente i [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] i dettagli dell'errore.  
  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client definisce le **ISQLServerErrorInfo** interfaccia degli errori. Questa interfaccia restituisce dettagli di un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] errore, inclusi la gravità e stato.  

  
## <a name="syntax"></a>Sintassi  
  
```  
  
HRESULT GetErrorInfo(  
   SSERRORINFO**ppSSErrorInfo,  
   OLECHAR**ppErrorStrings);  
```  
  
## <a name="arguments"></a>Argomenti  
 *ppSSErrorInfo*[out]  
 Puntatore a una struttura SSERRORINFO. Se il metodo ha esito negativo o è presente alcun [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le informazioni associate all'errore, il provider non alloca alcuna memoria e assicura che il *ppSSErrorInfo* argomento è un puntatore null nell'output.  
  
 *ppErrorStrings*[out]  
 Puntatore a un puntatore stringa carattere Unicode. Se il metodo ha esito negativo o è presente alcun [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le informazioni associate a un errore, il provider non alloca alcuna memoria e assicura che il *ppErrorStrings* argomento è un puntatore null nell'output. Liberando il *ppErrorStrings* argomento con la **IMalloc:: Free** metodo libera i tre singoli membri della stringa della struttura SSERRORINFO restituita, come la memoria viene allocata in un blocco.  
  
## <a name="return-code-values"></a>Valori restituiti  
 S_OK  
 Il metodo è riuscito.  
  
 E_INVALIDARG  
 Entrambi i *ppSSErrorInfo* o nella *ppErrorStrings* argomento era NULL.  
  
 E_OUTOFMEMORY  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client non è riuscito ad allocare memoria sufficiente per completare la richiesta.  
  
## <a name="remarks"></a>Note  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client alloca memoria per le stringhe SSERRORINFO e OLECHAR restituite tramite i puntatori passati dal consumer. Il consumer deve deallocare questa memoria usando il **IMalloc:: Free** metodo quando non è più necessario l'accesso ai dati dell'errore.  
  
 La struttura SSERRORINFO viene definita nel modo seguente:  
  
```  
typedef struct tagSSErrorInfo  
   {  
   LPOLESTR pwszMessage;  
   LPOLESTR pwszServer;  
   LPOLESTR pwszProcedure;  
   LONG lNative;  
   BYTE bState;  
   BYTE bClass;  
   WORD wLineNumber;  
   }  
SSERRORINFO;  
```  
  
|Membro|Description|  
|------------|-----------------|  
|*pwszMessage*|Messaggio di errore di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Viene restituito il messaggio tramite il **IErrorInfo:: GetDescription** (metodo).|  
|*pwszServer*|Nome dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in cui si è verificato l'errore.|  
|*pwszProcedure*|Nome della stored procedure che genera l'errore se esso si è verificato all'interno della stessa, in caso contrario, una stringa vuota.|  
|*lNative*|Numero di errore di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il numero di errore è identico a quello restituito nel *plNativeError* parametro delle **ISQLErrorInfo:: Getsqlinfo** (metodo).|  
|*bState*|Stato dell'errore di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|*bClass*|Gravità dell'errore di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|*wLineNumber*|Quando applicabile, riga di una stored procedure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che ha generato il messaggio di errore. Se non è coinvolta alcuna procedura, il valore predefinito è 1.|  
  
 I puntatori nella struttura di fare riferimento a indirizzi nella stringa restituita nel *ppErrorStrings* argomento.  
  
## <a name="see-also"></a>Vedere anche  
 [ISQLServerErrorInfo &#40;OLE DB&#41;](http://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1)   
 [RAISERROR &#40;Transact-SQL&#41;](../../t-sql/language-elements/raiserror-transact-sql.md)  
  
  
