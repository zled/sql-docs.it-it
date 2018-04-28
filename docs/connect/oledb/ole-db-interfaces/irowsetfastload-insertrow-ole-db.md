---
title: 'IRowsetFastLoad:: InsertRow (OLE DB) | Documenti Microsoft'
description: IRowsetFastLoad::InsertRow (OLE DB)
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-interfaces
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRowsetFastLoad::InsertRow (OLE DB)
apitype: COM
helpviewer_keywords:
- InsertRow method
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 287e277983086cb1c03b4296cd81c213268473f7
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="irowsetfastloadinsertrow-ole-db"></a>IRowsetFastLoad::InsertRow (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Aggiunge una riga al set di righe della copia bulk. Per esempi, vedere [Bulk copia i dati mediante IRowsetFastLoad &#40;OLE DB&#41; ](../../oledb/ole-db-how-to/bulk-copy-data-using-irowsetfastload-ole-db.md) e [inviare dati BLOB a SQL SERVER utilizzando IROWSETFASTLOAD e ISEQUENTIALSTREAM &#40;OLE DB&#41;](../../oledb/ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
HRESULT InsertRow(  
      HACCESSOR hAccessor,  
      void* pData);  
```  
  
## <a name="arguments"></a>Argomenti  
 *hAccessor*[in]  
 Handle della funzione di accesso che definisce i dati delle righe per la copia bulk. La funzione di accesso a cui viene fatto riferimento è una funzione di accesso di riga, che specifica l'associazione alla memoria del consumer contenente valori di dati.  
  
 *pData*[in]  
 Puntatore alla memoria del consumer contenente valori di dati. Per ulteriori informazioni, vedere [strutture DBBINDING](http://go.microsoft.com/fwlink/?LinkId=65955).  
  
## <a name="return-code-values"></a>Valori restituiti  
 S_OK  
 Il metodo è riuscito. I valori di stato associati per tutte le colonne hanno il valore DBSTATUS_S_OK o DBSTATUS_S_NULL.  
  
 E_FAIL  
 Si è verificato un errore. Le informazioni sull'errore sono disponibili nelle interfacce degli errori del set di righe.  
  
 E_INVALIDARG  
 Il *pData* argomento è stato impostato su un puntatore NULL.  
  
 E_OUTOFMEMORY  
 MSOLEDBSQL: Impossibile allocare memoria sufficiente per completare la richiesta.  
  
 E_UNEXPECTED  
 Il metodo è stato chiamato su un set di righe copia bulk precedentemente invalidato dal [IRowsetFastLoad:: commit](../../oledb/ole-db-interfaces/irowsetfastload-commit-ole-db.md) metodo.  
  
 DB_E_BADACCESSORHANDLE  
 Il *hAccessor* argomento fornito dal consumer non è valido.  
  
 DB_E_BADACCESSORTYPE  
 La funzione di accesso specificata non è una funzione di accesso di riga o non specifica la memoria del consumer.  
  
## <a name="remarks"></a>Osservazioni  
 Un errore durante la conversione dei dati del consumer per il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tipo di dati per una colonna determina una restituzione E_FAIL dal Driver OLE DB per SQL Server. Dati possono essere trasmessi a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] su qualsiasi **InsertRow** (metodo) o solo **Commit** metodo. L'applicazione consumer può chiamare il **InsertRow** metodo più volte con dati non corretti prima di ricevere notifica dell'esistenza di un errore di conversione di tipo di dati. Poiché il **Commit** metodo assicura che tutti i dati sia specificato correttamente dal consumer, il consumer può utilizzare il **Commit** metodo in modo appropriato per convalidare i dati in base alle esigenze.  
  
 Il Driver OLE DB per set di righe copia bulk SQL Server sono in sola lettura. Il Driver OLE DB per SQL Server non espone alcun metodo che consenta di query di tipo consumer del set di righe. Per terminare l'elaborazione, il consumer può rilasciare il riferimento di [IRowsetFastLoad](../../oledb/ole-db-interfaces/irowsetfastload-ole-db.md) interfaccia senza chiamare il **Commit** metodo. Non sono disponibili funzioni per accedere alle righe inserite dal consumer nel set di righe e modificarne i valori o per rimuoverle singolarmente dal set di righe.  
  
 Le righe oggetto di copia bulk vengono formattate sul server per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Le opzioni eventualmente impostate per la connessione o per la sessione, ad esempio ANSI_PADDING, influiscono sul formato di riga. Questa opzione è impostata su per impostazione predefinita per qualsiasi connessione stabilita tramite il Driver OLE DB per SQL Server.  
  
## <a name="see-also"></a>Vedere anche  
 [IRowsetFastLoad &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/irowsetfastload-ole-db.md)  
  
  
