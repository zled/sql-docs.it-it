---
title: 'Ibcpsession:: BCPExec (OLE DB) | Documenti Microsoft'
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-interfaces
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IBCPSession::BCPExec (OLE DB)
apitype: COM
helpviewer_keywords:
- BCPExec method
ms.assetid: 0f4ebb63-cf03-4e53-846e-6c3021cde007
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d746c01ed19368ab4502681d946cc3f06a61be35
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2018
---
# <a name="ibcpsessionbcpexec-ole-db"></a>IBCPSession::BCPExec (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Esegue l'operazione di copia bulk.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
HRESULT BCPExec(   
      DBROWCOUNT *pRowsCopied);  
```  
  
## <a name="remarks"></a>Osservazioni  
 Il **BCPExec** metodo copia i dati da un file utente in una tabella di database o viceversa, a seconda del valore del *eDirection* parametro utilizzato con il [ibcpsession:: BCPInit](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpinit-ole-db.md)metodo.  
  
 Prima di chiamare **BCPExec**, chiamare il **BCPInit** metodo con un nome di file utente valido. In caso contrario, viene generato un errore. L'unica eccezione riguarda le query da utilizzare per operazioni di copia bulk per l'esportazione. In questo caso specificare NULL per il nome della tabella nel **BCPInit** (metodo) e quindi specificare la query utilizzando l'opzione BCP_OPTION_HINTS.  
  
 Il **BCPExec** metodo è l'unico metodo di copia che è probabile che sia in attesa per un periodo di tempo bulk. pertanto è l'unico metodo di copia bulk che supporta la modalità asincrona. Per utilizzare la modalità asincrona, impostare la proprietà di sessione ssprop_asynch_bulkcopy specifica del provider su VARIANT_TRUE prima di chiamare il **BCPExec** metodo. Questa proprietà è disponibile nel set di proprietà DBPROPSET_SQLSERVERSESSION. Per testare il completamento, chiamare il **BCPExec** (metodo) con gli stessi parametri. Se la copia di massa non è ancora completata, il **BCPExec** metodo viene restituito DB_S_ASYNCHRONOUS. Restituisce inoltre nel *pRowsCopied* argomento un conteggio del numero di righe che sono stati inviati o ricevuti dal server di stato. Il commit delle righe inviate al server non viene eseguito fino a quando non viene raggiunta la fine di un batch.  
  
## <a name="arguments"></a>Argomenti  
 *pRowsCopied*[out]  
 Puntatore a DWORD. Il **BCPExec** metodo inserisce in DWORD il numero di righe copiate correttamente. Se il *pRowsCopied* argomento è impostato su NULL, viene ignorato dal **BCPExec** metodo.  
  
## <a name="return-code-values"></a>Valori restituiti  
 S_OK  
 Il metodo è riuscito.  
  
 E_FAIL  
 Si è verificato un errore specifico del provider; Per informazioni dettagliate, utilizzare il [ISQLServerErrorInfo](http://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1) interfaccia.  
  
 E_UNEXPECTED  
 La chiamata al metodo non era prevista. Non è stato ad esempio chiamato il metodo **BCPInit** prima della chiamata a questo metodo. Si verifica anche se l'operazione è stata interrotta mediante l'opzione BCP_OPTION_ABORT e **BCPExec** metodo è stato chiamato in un secondo momento.  
  
 E_OUTOFMEMORY  
 Errore di memoria insufficiente.  
  
 DB_S_ENDOFROWSET  
 L'operazione di copia bulk è terminata e il trasferimento dei dati è stato completato.  
  
 DB_S_ASYNCHRONOUS  
 Il batch corrente di righe è stato copiato. Chiamare il **BCPExec** metodo per trasferire il batch successivo.  
  
 DB_S_ERRORSOCCURRED  
 Si sono verificati errori durante l'operazione di copia bulk ed è possibile che alcune righe non siano state copiate. Il numero di errori è ancora al di sotto del numero massimo di errori consentiti.  
  
## <a name="see-also"></a>Vedere anche  
 [OLE DB IBCPSession &#40; &#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-ole-db.md)   
 [Esecuzione di operazioni di copia bulk](../../relational-databases/native-client/features/performing-bulk-copy-operations.md)  
  
  
