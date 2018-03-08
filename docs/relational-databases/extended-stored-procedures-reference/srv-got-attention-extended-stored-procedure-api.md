---
title: srv_got_attention (API Stored procedure estesa) | Microsoft Docs
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: extended-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- srv_got_attention
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_got_attention
ms.assetid: 805e68e1-d17f-41bd-8b9f-a27283bb6fbe
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 541d9ebe6bb7752a9025f65f1570df28f253bb88
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="srvgotattention-extended-stored-procedure-api"></a>srv_got_attention (API Stored procedure estesa)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] In alternativa, usare l'integrazione con CLR.  
  
 Controlla se l'attività o la connessione corrente deve essere interrotta e restituisce TRUE se la connessione viene terminata o il batch interrotto  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
BOOL srv_got_attention (SRV_PROC *   
srvproc  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 *srvproc*  
 Puntatore che identifica una connessione al database.  
  
## <a name="return-value"></a>Valore restituito  
 TRUE se la connessione viene terminata o il batch interrotto. FALSE se la connessione o il batch è attivo.  
  
## <a name="remarks"></a>Osservazioni  
 Una stored procedure estesa con esecuzione prolungata deve controllare l'attenzione del server chiamando periodicamente **srv_got_attention** in modo che la procedura possa terminare se stessa se la connessione viene terminata o il batch viene interrotto.  
  
> [!IMPORTANT]  
>  È necessario esaminare con attenzione il codice sorgente delle stored procedure estese e testare le DLL compilate prima di installarle in un server di produzione. Per informazioni sui test e sull'analisi della sicurezza, visitare questo [sito Web Microsoft](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
  
