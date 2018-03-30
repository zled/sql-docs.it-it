---
title: 'Issabort:: Abort (OLE DB) | Documenti Microsoft'
description: ISSAbort::Abort (OLE DB)
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
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
- ISSAbort::Abort (OLE DB)
apitype: COM
helpviewer_keywords:
- Abort method
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 81792a3eefe5d29b63614c3be71562de8540a1fd
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2018
---
# <a name="issabortabort-ole-db"></a>ISSAbort::Abort (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Annulla il set di righe corrente oltre a qualsiasi comando eseguito in batch associato al comando corrente.  
  
Il **ISSAbort** interfaccia, esposta nel Driver OLE DB per SQL Server, fornisce il **issabort:: Abort** metodo che viene utilizzato per annullare il set di righe corrente oltre a qualsiasi comando batch con il comando che ha inizialmente generato il set di righe e non ha ancora completato l'esecuzione.  
  
 **ISSAbort** è disponibile un Driver OLE DB per l'interfaccia di specifiche di SQL Server usando **QueryInterface** sul **IMultipleResults** oggetto restituito da **ICommand:: Execute**  oppure **IOpenRowset:: OPENROWSET**.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
HRESULT Abort(void);  
```  
  
## <a name="remarks"></a>Osservazioni  
 Se il comando interrotto è in una stored procedure, l'esecuzione di stored procedure (e le procedure che ha chiamato la procedura) verrà terminata insieme al batch di comandi che contiene la chiamata di stored procedure. Se il server è in corso il trasferimento di un set di risultati al client, il trasferimento verrà arrestato. Se il client non desidera utilizzare un set di risultati, la chiamata **issabort:: Abort** prima di rilasciare il set di righe accelererà il rilascio di set di righe, ma se è presente una transazione aperta e XACT_ABORT è impostata su ON, sarà possibile il rollback della transazione quando **issabort:: Abort** viene chiamato  
  
 Dopo aver **issabort:: Abort** restituisce S_OK, associato **IMultipleResults** interfaccia entra in uno stato inutilizzabile e restituisce DB_E_CANCELED a tutte le chiamate di metodo (ad eccezione dei metodi definiti per il **IUnknown** interface) fino a quando non viene rilasciato. Se un **IRowset** ottenuto dal **IMultipleResults** prima una chiamata al metodo **interrompere**, inoltre entra in uno stato inutilizzabile e restituisce DB_E_CANCELED a tutte le chiamate di metodo (ad eccezione dei metodi definiti per il **IUnknown** interfaccia e **IRowset:: ReleaseRows**) fino a quando non viene rilasciato dopo una chiamata a **issabort:: Abort**.  
  
> [!NOTE]  
>  A partire da [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], se il server di stato XACT_ABORT è ON, l'esecuzione di **issabort:: Abort** terminerà e rollback di transazioni corrente implicita o esplicita quando connesso a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Nelle versioni precedenti di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] la transazione corrente non viene interrotta.  
  
## <a name="arguments"></a>Argomenti  
 Nessuno  
  
## <a name="return-code-values"></a>Valori restituiti  
 S_OK  
 Il **issabort:: Abort** restituisce S_OK se il batch è stato annullato e DB_E_CANTCANCEL in caso contrario. Se il batch è già stato annullato, viene restituito DB_E_CANCELED.  
  
 DB_E_CANCELED  
 Il batch è già stato annullato.  
  
 DB_E_CANTCANCEL  
 Il batch non è stato annullato.  
  
 E_FAIL  
 Si è verificato un errore specifico del provider; Per informazioni dettagliate, utilizzare il [ISQLServerErrorInfo](http://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1) interfaccia.  
  
 E_UNEXPECTED  
 La chiamata al metodo non era prevista. Ad esempio, l'oggetto è in uno stato non valido perché **issabort:: Abort** è già stato chiamato.  
  
 E_OUTOFMEMORY  
 Errore di memoria insufficiente.  
  
  
