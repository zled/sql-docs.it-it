---
title: 'Ibcpsession:: BCPExec (OLE DB) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IBCPSession::BCPExec (OLE DB)
apitype: COM
helpviewer_keywords:
- BCPExec method
ms.assetid: 0f4ebb63-cf03-4e53-846e-6c3021cde007
caps.latest.revision: 23
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: c1dcfcc58a17382981cb8b282c86c71a890b00cf
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37419250"
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
  
## <a name="remarks"></a>Note  
 Il **BCPExec** metodo copia i dati da un file utente a una tabella di database o viceversa, a seconda del valore della *eDirection* parametro utilizzato con il [ibcpsession:: BCPInit](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpinit-ole-db.md)metodo.  
  
 Prima di chiamare **BCPExec**, chiamare il **BCPInit** metodo con un nome di file utente valido. In caso contrario, viene generato un errore. L'unica eccezione riguarda le query da utilizzare per operazioni di copia bulk per l'esportazione. In questo caso specificare NULL per il nome della tabella nel **BCPInit** (metodo) e quindi specificare la query utilizzando l'opzione BCP_OPTION_HINTS.  
  
 Il **BCPExec** metodo è l'unico metodo di copia che probabilmente continuerà a rimanere in attesa per un periodo di tempo in blocco. pertanto è l'unico metodo di copia bulk che supporta la modalità asincrona. Per utilizzare la modalità asincrona, impostare la proprietà di sessione ssprop_asynch_bulkcopy specifica del provider su VARIANT_TRUE prima di chiamare il **BCPExec** (metodo). Questa proprietà è disponibile nel set di proprietà DBPROPSET_SQLSERVERSESSION. Per testare il completamento, chiamare il **BCPExec** metodo con gli stessi parametri. Se la copia bulk non ha ancora completato, il **BCPExec** metodo viene restituito DB_S_ASYNCHRONOUS. Restituisce inoltre nel *pRowsCopied* argomento un conteggio dello stato del numero di righe che sono stati inviati a o ricevuti dal server. Il commit delle righe inviate al server non viene eseguito fino a quando non viene raggiunta la fine di un batch.  
  
## <a name="arguments"></a>Argomenti  
 *pRowsCopied*[out]  
 Puntatore a DWORD. Il **BCPExec** metodo inserisce in DWORD il numero di righe copiate correttamente. Se il *pRowsCopied* argomento è impostato su NULL, viene ignorato per il **BCPExec** (metodo).  
  
## <a name="return-code-values"></a>Valori restituiti  
 S_OK  
 Il metodo è riuscito.  
  
 E_FAIL  
 Si è verificato un errore specifico del provider; Per informazioni dettagliate, usare il [ISQLServerErrorInfo](http://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1) interfaccia.  
  
 E_UNEXPECTED  
 La chiamata al metodo non era prevista. Non è stato ad esempio chiamato il metodo **BCPInit** prima della chiamata a questo metodo. Si verifica anche se l'operazione è stata interrotta mediante l'opzione BCP_OPTION_ABORT e il **BCPExec** metodo è stato chiamato in un secondo momento.  
  
 E_OUTOFMEMORY  
 Errore di memoria insufficiente.  
  
 DB_S_ENDOFROWSET  
 L'operazione di copia bulk è terminata e il trasferimento dei dati è stato completato.  
  
 DB_S_ASYNCHRONOUS  
 Il batch corrente di righe è stato copiato. Chiamare il **BCPExec** metodo per trasferire il batch successivo.  
  
 DB_S_ERRORSOCCURRED  
 Si sono verificati errori durante l'operazione di copia bulk ed è possibile che alcune righe non siano state copiate. Il numero di errori è ancora al di sotto del numero massimo di errori consentiti.  
  
## <a name="see-also"></a>Vedere anche  
 [IBCPSession &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-ole-db.md)   
 [Esecuzione di operazioni di copia bulk](../../relational-databases/native-client/features/performing-bulk-copy-operations.md)  
  
  
