---
title: 'Issabort:: Abort (OLE DB) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- ISSAbort::Abort (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- Abort method
ms.assetid: a5bca169-694b-4895-84ac-e8fba491e479
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 05673bb90cd0958344a6a12550f15c122489219a
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37416290"
---
# <a name="issabortabort-ole-db"></a>ISSAbort::Abort (OLE DB)
  Annulla il set di righe corrente oltre a qualsiasi comando eseguito in batch associato al comando corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
HRESULT Abort(void);  
```  
  
## <a name="remarks"></a>Note  
 Se il comando interrotto è in una stored procedure, l'esecuzione della stored procedure (e di qualsiasi procedura che ha chiamato la procedura) verrà terminata insieme al batch di comandi che contiene la chiamata alla stored procedure. Se nel server è in corso il trasferimento di un set di risultati al client, questo processo verrà arrestato. Se il client non desidera utilizzare un set di risultati, chiamare **issabort:: Abort** prima di rilasciare il set di righe accelererà il rilascio di set di righe, ma se è presente una transazione aperta e XACT_ABORT è impostata su ON, verrà eseguito il rollback della transazione quando **Issabort:: Abort** viene chiamato  
  
 Dopo aver **issabort:: Abort** restituisce S_OK, associato **IMultipleResults** interfaccia entra in uno stato inutilizzabile e restituisce DB_E_CANCELED a tutte le chiamate al metodo (ad eccezione dei metodi definiti per il **IUnknown** interface) fino a quando non viene rilasciato. Se un' **IRowset** era stato ottenuto da **IMultipleResults** prima di una chiamata a **Abort**, inoltre entra in uno stato inutilizzabile e restituisce DB_E_CANCELED a all (metodo) chiama ( ad eccezione dei metodi definiti per il **IUnknown** interfaccia e **:: ReleaseRows**) fino a quando non viene rilasciato dopo una chiamata al **issabort:: Abort** .  
  
> [!NOTE]  
>  A partire [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], se il server di stato XACT_ABORT è ON, l'esecuzione **issabort:: Abort** terminerà e il rollback di qualsiasi transazione di implicita o esplicita corrente quando si è connessi a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Nelle versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la transazione corrente non viene interrotta.  
  
## <a name="arguments"></a>Argomenti  
 Nessuna.  
  
## <a name="return-code-values"></a>Valori restituiti  
 S_OK  
 Il **issabort:: Abort** metodo restituisce S_OK se il batch è stato annullato e DB_E_CANTCANCEL in caso contrario. Se il batch è già stato annullato, viene restituito DB_E_CANCELED.  
  
 DB_E_CANCELED  
 Il batch è già stato annullato.  
  
 DB_E_CANTCANCEL  
 Il batch non è stato annullato.  
  
 E_FAIL  
 Si è verificato un errore specifico del provider; Per informazioni dettagliate, usare il [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) interfaccia.  
  
 E_UNEXPECTED  
 La chiamata al metodo non era prevista. Ad esempio, l'oggetto è in uno stato non valido perché **issabort:: Abort** è già stato chiamato.  
  
 E_OUTOFMEMORY  
 Errore di memoria insufficiente.  
  
## <a name="see-also"></a>Vedere anche  
 [ISSAbort &#40;OLE DB&#41;](../../database-engine/dev-guide/issabort-ole-db.md)  
  
  
