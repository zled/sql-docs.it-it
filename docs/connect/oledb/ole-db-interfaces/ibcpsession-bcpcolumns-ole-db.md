---
title: 'Ibcpsession:: BCPColumns (OLE DB) | Documenti Microsoft'
description: IBCPSession::BCPColumns (OLE DB)
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
- IBCPSession::BCPColumns (OLE DB)
apitype: COM
helpviewer_keywords:
- BCPColumns method
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 201692b9ec795fd2ca472b2cd1eb1a938b5e1854
ms.sourcegitcommit: 03ba89937daeab08aa410eb03a52f1e0d212b44f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/16/2018
ms.locfileid: "35690234"
---
# <a name="ibcpsessionbcpcolumns-ole-db"></a>IBCPSession::BCPColumns (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Imposta il numero di campi da associare alle colonne di una tabella di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
HRESULT BCPColumns(   
      DBCOUNTITEM nColumns);  
```  
  
## <a name="remarks"></a>Remarks  
 Chiama internamente [ibcpsession:: BCPColFmt](../../oledb/ole-db-interfaces/ibcpsession-bcpcolfmt-ole-db.md) per impostare i valori predefiniti per i dati del campo. Questi valori predefiniti vengono ottenuti dalle informazioni di colonna SQL Server che il provider recupera internamente quando il nome della tabella viene specificato tramite [ibcpsession:: BCPInit](../../oledb/ole-db-interfaces/ibcpsession-bcpinit-ole-db.md).  
  
> [!NOTE]  
>  Questo metodo può essere chiamato solo dopo aver **BCPInit** è stata chiamata con un nome file valido.  
  
 È consigliabile chiamare questo metodo solo se si intende utilizzare un formato di file utente diverso da quello predefinito. Per ulteriori informazioni su una descrizione del formato di file utente predefinito, vedere la **BCPInit** metodo.  
  
 Dopo la chiamata di **BCPColumns** metodo, è necessario chiamare il **BCPColFmt** metodo per ogni colonna nel file utente per definire completamente un formato di file personalizzato.  
  
## <a name="arguments"></a>Argomenti  
 *nColumns*[in]  
 Numero totale di campi nel file utente. Anche se ci si prepara a copia bulk di dati dal file utente a un Server SQL di tabella e non si intende copiare tutti i campi nel file utente, è comunque necessario impostare il *nColumns* argomento per il numero totale di campi del file utente. I campi ignorati possono quindi essere specificati tramite **BCPColFmt**.  
  
## <a name="return-code-values"></a>Valori restituiti  
 S_OK  
 Il metodo è riuscito.  
  
 E_FAIL  
 Si è verificato un errore specifico del provider; Per informazioni dettagliate, utilizzare il [ISQLServerErrorInfo](http://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1) interfaccia.  
  
 E_UNEXPECTED  
 La chiamata al metodo non era prevista. Non è stato ad esempio chiamato il metodo **BCPInit** prima della chiamata a questo metodo. Si verifica inoltre quando questo metodo viene chiamato più volte per un'operazione di copia bulk.  
  
 E_OUTOFMEMORY  
 Errore di memoria insufficiente.  
  
## <a name="see-also"></a>Vedere anche  
 [IBCPSession &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/ibcpsession-ole-db.md)   
 [Esecuzione di operazioni di copia bulk](../../oledb/features/performing-bulk-copy-operations.md)  
  
  
