---
title: srv_got_attention (API Stored procedure estesa) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
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
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 3fc22bf79a05b354ff63987b348af99f484053cf
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47798079"
---
# <a name="srvgotattention-extended-stored-procedure-api"></a>srv_got_attention (API Stored procedure estesa)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Usare in alternativa l'integrazione CLR.  
  
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
  
## <a name="remarks"></a>Remarks  
 Una stored procedure estesa con esecuzione prolungata deve controllare l'attenzione del server chiamando periodicamente **srv_got_attention** in modo che la procedura possa terminare se stessa se la connessione viene terminata o il batch viene interrotto.  
  
> [!IMPORTANT]  
>  È necessario esaminare con attenzione il codice sorgente delle stored procedure estese e testare le DLL compilate prima di installarle in un server di produzione. Per informazioni sui test e sull'analisi della sicurezza, visitare questo [sito Web Microsoft](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
  
