---
title: 'Ibcpsession:: Bcpreadfmt (OLE DB) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- IBCPSession::BCPReadFmt (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- BCPReadFmt method
ms.assetid: e2a12050-94e4-48a3-8a48-b780d646f116
caps.latest.revision: 26
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: aa0f1501955db61889bb437e545cda95dfe8b31f
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37428258"
---
# <a name="ibcpsessionbcpreadfmt-ole-db"></a>IBCPSession::BCPReadFmt (OLE DB)
  Legge le informazioni sul formato per ogni colonna dal file di formato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
HRESULT BCPReadFmt(   
const wchar_t *pwszFormatFile);  
```  
  
## <a name="remarks"></a>Note  
 Il **BCPReadFmt** metodo viene utilizzato per la lettura dei dati da un file di formato che specifica il formato dei dati nel file di dati. Questo metodo è in grado di rilevare la versione corretta del file di formato. Può rilevare automaticamente se il file è in formato xml o testo stile antico e comportarsi di conseguenza. Le versioni di file di formato supportate dal [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] BCP del provider OLE DB Native Client sono versione 6.0 o versione successiva.  
  
 Dopo il **BCPReadFmt** metodo legge i valori di formato, effettua le chiamate appropriate per il [ibcpsession:: BCPColumns](ibcpsession-bcpcolumns-ole-db.md) e [ibcpsession:: BCPColFmt](ibcpsession-bcpcolfmt-ole-db.md) metodi. L'utente può evitare di analizzare un file di formato ed effettuare queste chiamate.  
  
 Per salvare un file di formato, chiamare il [ibcpsession:: Bcpwritefmt](ibcpsession-bcpwritefmt-ole-db.md) (metodo). Le chiamate al **BCPReadFmt** metodo può fare riferimento a formati salvati. In alternativa, l'utilità di copia bulk (**bcp**) può salvare i formati di dati definito dall'utente nei file che possono fare riferimento il **BCPReadFmt** (metodo).  
  
 Il `BCP_OPTION_DELAYREADFMT` pari al *eOption* parametro [ibcpsession:: Bcpcontrol](ibcpsession-bcpcontrol-ole-db.md) modifica il comportamento di ibcpsession:: Bcpreadfmt.  
  
## <a name="arguments"></a>Argomenti  
 *pwszFormatFile*[in]  
 Percorso e nome del file contenente i valori di formato per il file di dati.  
  
## <a name="return-code-values"></a>Valori restituiti  
 S_OK  
 Il metodo è riuscito.  
  
 E_FAIL  
 Si è verificato un errore specifico del provider, per informazioni dettagliate, utilizzare il [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) interfaccia.  
  
 E_OUTOFMEMORY  
 Errore di memoria insufficiente.  
  
 E_UNEXPECTED  
 La chiamata al metodo non era prevista. Ad esempio, il [ibcpsession:: BCPInit](ibcpsession-bcpinit-ole-db.md) (metodo) non è stato chiamato prima di chiamare questo metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md)   
 [Esecuzione di operazioni di copia bulk](../native-client/features/performing-bulk-copy-operations.md)  
  
  
