---
title: srv_got_attention (API Stored procedure estesa) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- srv_got_attention
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_got_attention
ms.assetid: 805e68e1-d17f-41bd-8b9f-a27283bb6fbe
caps.latest.revision: 17
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9553592c01e318de3e090900d2f6b4260301146f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36167870"
---
# <a name="srvgotattention-extended-stored-procedure-api"></a>srv_got_attention (API Stored procedure estesa)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Usare in alternativa l'integrazione CLR.  
  
 Controlla se l'attività o la connessione corrente deve essere interrotta e restituisce TRUE se la connessione viene terminata o il batch interrotto  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
BOOL srv_got_attention  
(SRV_PROC *  
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
  
  