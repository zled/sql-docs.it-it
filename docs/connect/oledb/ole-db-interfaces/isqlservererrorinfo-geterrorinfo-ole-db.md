---
title: 'ISQLServerErrorInfo:: GetErrorInfo (OLE DB) | Documenti Microsoft'
description: ISQLServerErrorInfo::GetErrorInfo (OLE DB)
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
- ISQLServerErrorInfo::GetErrorInfo (OLE DB)
apitype: COM
helpviewer_keywords:
- GetErrorInfo method
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 936924540c5c55f8e333a64d794e54af098f7279
ms.sourcegitcommit: 03ba89937daeab08aa410eb03a52f1e0d212b44f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/16/2018
ms.locfileid: "35690194"
---
# <a name="isqlservererrorinfogeterrorinfo-ole-db"></a>ISQLServerErrorInfo::GetErrorInfo (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Restituisce un puntatore a un Driver OLE DB per SQL Server SSERRORINFO struttura che contiene il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] i dettagli dell'errore.  
  
 Il Driver OLE DB per SQL Server definisce la **ISQLServerErrorInfo** interfaccia degli errori. Questa interfaccia restituisce dettagli di un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] errore, inclusi la gravità e stato.  

  
## <a name="syntax"></a>Sintassi  
  
```  
  
HRESULT GetErrorInfo(  
   SSERRORINFO**ppSSErrorInfo,  
   OLECHAR**ppErrorStrings);  
```  
  
## <a name="arguments"></a>Argomenti  
 *ppSSErrorInfo*[out]  
 Puntatore a una struttura SSERRORINFO. Se il metodo ha esito negativo o non esiste alcuna [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] informazioni associate all'errore, il provider non alloca alcuna memoria e assicura che il *ppSSErrorInfo* argomento è un puntatore null nell'output.  
  
 *ppErrorStrings*[out]  
 Puntatore a un puntatore stringa carattere Unicode. Se il metodo ha esito negativo o non esiste alcuna [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] le informazioni associate a un errore, il provider non alloca alcuna memoria e assicura che il *ppErrorStrings* argomento è un puntatore null nell'output. Liberando il *ppErrorStrings* argomento con il **IMalloc:: Free** metodo libera i tre singoli membri della stringa della struttura SSERRORINFO restituita, come la memoria viene allocata in un blocco.  
  
## <a name="return-code-values"></a>Valori restituiti  
 S_OK  
 Il metodo è riuscito.  
  
 E_INVALIDARG  
 Entrambi i *ppSSErrorInfo* o il *ppErrorStrings* argomento è NULL.  
  
 E_OUTOFMEMORY  
 Il Driver OLE DB per SQL Server non è stato possibile allocare memoria sufficiente per completare la richiesta.  
  
## <a name="remarks"></a>Remarks  
 Il Driver OLE DB per SQL Server consente di allocare memoria per le stringhe SSERRORINFO e OLECHAR restituite tramite i puntatori passati dal consumer. Il consumer deve deallocare questa memoria usando il **IMalloc:: Free** metodo quando non è più necessario l'accesso ai dati dell'errore.  
  
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
|*pwszMessage*|Messaggio di errore di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Viene restituito il messaggio tramite il **IErrorInfo:: GetDescription** metodo.|  
|*pwszServer*|Nome dell'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in cui si è verificato l'errore.|  
|*pwszProcedure*|Nome della stored procedure che genera l'errore se esso si è verificato all'interno della stessa, in caso contrario, una stringa vuota.|  
|*lNative*|Numero di errore di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Il numero di errore è identico a quello restituito nel *plNativeError* parametro del **ISQLErrorInfo:: Getsqlinfo** metodo.|  
|*bState*|Stato dell'errore di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|*bClass*|Gravità dell'errore di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|*wLineNumber*|Quando applicabile, riga di una stored procedure [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] che ha generato il messaggio di errore. Se non è coinvolta alcuna procedura, il valore predefinito è 1.|  
  
 Puntatori nella struttura di indirizzi nella stringa restituita di riferimento il *ppErrorStrings* argomento.  
  
## <a name="see-also"></a>Vedere anche  
 [ISQLServerErrorInfo &#40;OLE DB&#41;](http://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1)   
 [RAISERROR &#40;Transact-SQL&#41;](../../../t-sql/language-elements/raiserror-transact-sql.md)  
  
  
