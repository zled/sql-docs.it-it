---
title: 'IRowsetFastLoad:: InsertRow (OLE DB) | Documenti Microsoft'
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- IRowsetFastLoad::InsertRow (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- InsertRow method
ms.assetid: 594d3461-34d2-41e7-8ad4-bd2753601ab6
caps.latest.revision: 36
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 03aa7d6c574d77bab0b5771f0f68623eae468051
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36055256"
---
# <a name="irowsetfastloadinsertrow-ole-db"></a>IRowsetFastLoad::InsertRow (OLE DB)
  Aggiunge una riga al set di righe della copia bulk. Per esempi, vedere [Bulk copia i dati mediante IRowsetFastLoad &#40;OLE DB&#41; ](../native-client-ole-db-how-to/bulk-copy-data-using-irowsetfastload-ole-db.md) e [inviare dati BLOB a SQL SERVER utilizzando IROWSETFASTLOAD e ISEQUENTIALSTREAM &#40;OLE DB&#41;](../native-client-ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
HRESULT InsertRow(  
HACCESSOR  
hAccessor  
,  
void*  
pData  
);  
  
```  
  
## <a name="arguments"></a>Argomenti  
 *hAccessor*[in]  
 Handle della funzione di accesso che definisce i dati delle righe per la copia bulk. La funzione di accesso a cui viene fatto riferimento è una funzione di accesso di riga, che specifica l'associazione alla memoria del consumer contenente valori di dati.  
  
 *pData*[in]  
 Puntatore alla memoria del consumer contenente valori di dati. Per altre informazioni, vedere [strutture DBBINDING](http://go.microsoft.com/fwlink/?LinkId=65955).  
  
## <a name="return-code-values"></a>Valori restituiti  
 S_OK  
 Il metodo è riuscito. I valori di stato associati per tutte le colonne hanno il valore DBSTATUS_S_OK o DBSTATUS_S_NULL.  
  
 E_FAIL  
 Si è verificato un errore. Le informazioni sull'errore sono disponibili nelle interfacce degli errori del set di righe.  
  
 E_INVALIDARG  
 Il *pData* argomento è stato impostato su un puntatore NULL.  
  
 E_OUTOFMEMORY  
 SQLNCLI11 non è stato in grado di allocare memoria sufficiente per completare la richiesta.  
  
 E_UNEXPECTED  
 Il metodo è stato chiamato su un set di righe copia bulk precedentemente invalidato dal [IRowsetFastLoad:: commit](irowsetfastload-commit-ole-db.md) metodo.  
  
 DB_E_BADACCESSORHANDLE  
 Il *hAccessor* argomento fornito dal consumer non è valido.  
  
 DB_E_BADACCESSORTYPE  
 La funzione di accesso specificata non è una funzione di accesso di riga o non specifica la memoria del consumer.  
  
## <a name="remarks"></a>Remarks  
 Un errore durante la conversione dei dati del consumer per il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipo di dati per una colonna determina E_FAIL dal [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client. I dati possono essere trasmessi a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] su qualsiasi **InsertRow** metodo o solo **Commit** (metodo). L'applicazione consumer può chiamare la **InsertRow** metodo più volte con dati non corretti prima di ricevere notifica dell'esistenza di un errore di conversione di tipo di dati. Poiché il **eseguire il Commit** metodo assicura che tutti i dati vengano specificati correttamente dal consumer, il consumer può utilizzare il **Commit** metodo in modo appropriato per convalidare i dati in base alle esigenze.  
  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] set di righe copia bulk del provider OLE DB Native Client sono di sola scrittura. Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client non espone alcun metodo che consenta di query di tipo consumer del set di righe. Per terminare l'elaborazione, il consumer può rilasciare il riferimento al [IRowsetFastLoad](irowsetfastload-ole-db.md) interfaccia senza chiamare il **Commit** metodo. Non sono disponibili funzioni per accedere alle righe inserite dal consumer nel set di righe e modificarne i valori o per rimuoverle singolarmente dal set di righe.  
  
 Le righe oggetto di copia bulk vengono formattate sul server per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le opzioni eventualmente impostate per la connessione o per la sessione, ad esempio ANSI_PADDING, influiscono sul formato di riga. Questa opzione è attivata per impostazione predefinita per qualsiasi connessione stabilita tramite il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client.  
  
## <a name="see-also"></a>Vedere anche  
 [IRowsetFastLoad &#40;OLE DB&#41;](irowsetfastload-ole-db.md)  
  
  