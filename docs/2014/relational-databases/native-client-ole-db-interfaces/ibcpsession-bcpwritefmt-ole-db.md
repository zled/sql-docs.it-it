---
title: 'Ibcpsession:: Bcpwritefmt (OLE DB) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- IBCPSession::BCPWriteFmt (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- BCPWriteFmt method
ms.assetid: add50425-2ed6-411a-a391-4ce63c364892
caps.latest.revision: 24
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 68be3cd9b1296ed1f9e3530c4aadcc5a28cea891
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37431050"
---
# <a name="ibcpsessionbcpwritefmt-ole-db"></a>IBCPSession::BCPWriteFmt (OLE DB)
  Scrive informazioni sul formato per ogni colonna nel file di formato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
HRESULT BCPWriteFmt(   
const wchar_t *pwszFormatFile);  
```  
  
## <a name="remarks"></a>Note  
 Il file di formato specifica il formato dei dati di un file di dati creato dalla copia bulk. Le chiamate al [ibcpsession:: BCPColumns](ibcpsession-bcpcolumns-ole-db.md) e [ibcpsession:: BCPColFmt](ibcpsession-bcpcolfmt-ole-db.md) metodi definiscono il formato del file di dati. Il **BCPWriteFmt** metodo Salva questa definizione nel file di cui fa riferimento l'argomento pwszFormatFile.  
  
 Il **BCPWriteFmt** metodo può salvare i file di formato in formato xml o testo. Si devono essere contrassegnato con l'opzione di controllo BCP_OPTION_XML con il [ibcpsession:: Bcpcontrol](ibcpsession-bcpcontrol-ole-db.md) (metodo).  
  
 Per caricare un file di formato salvato, utilizzare il [ibcpsession:: Bcpreadfmt](ibcpsession-bcpreadfmt-ole-db.md) (metodo).  
  
## <a name="arguments"></a>Argomenti  
 *pwszFormatFile*[in]  
 Percorso e nome del file contenente i valori di formato per il file di dati.  
  
## <a name="return-code-values"></a>Valori restituiti  
 S_OK  
 Il metodo è riuscito.  
  
 E_FAIL  
 Si è verificato un errore specifico del provider; Per informazioni dettagliate, usare il [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) interfaccia.  
  
 E_OUTOFMEMORY  
 Errore di memoria insufficiente.  
  
 E_UNEXPECTED  
 La chiamata al metodo non era prevista. Ad esempio, il [ibcpsession:: BCPInit](ibcpsession-bcpinit-ole-db.md) (metodo) non è stato chiamato prima di chiamare questo metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md)   
 [Esecuzione di operazioni di copia bulk](../native-client/features/performing-bulk-copy-operations.md)  
  
  
