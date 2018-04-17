---
title: 'Ibcpsession:: Bcpreadfmt (OLE DB) | Documenti Microsoft'
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client-ole-db-interfaces
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IBCPSession::BCPReadFmt (OLE DB)
apitype: COM
helpviewer_keywords:
- BCPReadFmt method
ms.assetid: e2a12050-94e4-48a3-8a48-b780d646f116
caps.latest.revision: 26
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: e9bc5e21716f030c3d963fee7454df26e163e9a4
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="ibcpsessionbcpreadfmt-ole-db"></a>IBCPSession::BCPReadFmt (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Legge le informazioni sul formato per ogni colonna dal file di formato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
HRESULT BCPReadFmt(   
      const wchar_t *pwszFormatFile);  
```  
  
## <a name="remarks"></a>Osservazioni  
 Il **BCPReadFmt** metodo viene utilizzato per la lettura dei dati da un file di formato che specifica il formato dei dati nel file di dati. Questo metodo è in grado di rilevare la versione corretta del file di formato. Può rilevare automaticamente se il file è in formato xml o testo stile antico e comportarsi di conseguenza. Le versioni di file di formato supportate dal [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] BCP del provider OLE DB Native Client sono versione 6.0 o versione successiva.  
  
 Dopo il **BCPReadFmt** metodo legge i valori di formato, effettua le chiamate appropriate al [ibcpsession:: BCPColumns](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcolumns-ole-db.md) e [ibcpsession:: BCPColFmt](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcolfmt-ole-db.md) metodi. L'utente può evitare di analizzare un file di formato ed effettuare queste chiamate.  
  
 Per salvare un file di formato, chiamare il [ibcpsession:: Bcpwritefmt](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpwritefmt-ole-db.md) metodo. Le chiamate al **BCPReadFmt** metodo può fare riferimento a formati salvati. In alternativa, l'utilità di copia bulk (**bcp**) può salvare i formati di dati definito dall'utente nei file che possono fare riferimento il **BCPReadFmt** metodo.  
  
 Il **BCP_OPTION_DELAYREADFMT** valore il *eOption* parametro di [ibcpsession:: Bcpcontrol](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcontrol-ole-db.md) modifica il comportamento di ibcpsession:: Bcpreadfmt.  
  
## <a name="arguments"></a>Argomenti  
 *pwszFormatFile*[in]  
 Percorso e nome del file contenente i valori di formato per il file di dati.  
  
## <a name="return-code-values"></a>Valori restituiti  
 S_OK  
 Il metodo è riuscito.  
  
 E_FAIL  
 Si è verificato un errore specifico del provider, per informazioni dettagliate, utilizzare il [ISQLServerErrorInfo](http://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1) interfaccia.  
  
 E_OUTOFMEMORY  
 Errore di memoria insufficiente.  
  
 E_UNEXPECTED  
 La chiamata al metodo non era prevista. Ad esempio, il [ibcpsession:: BCPInit](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpinit-ole-db.md) (metodo) non è stato chiamato prima di chiamare questo metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [IBCPSession &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-ole-db.md)   
 [Esecuzione di operazioni di copia bulk](../../relational-databases/native-client/features/performing-bulk-copy-operations.md)  
  
  
