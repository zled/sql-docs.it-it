---
title: srv_paramsetoutput (API Stored procedure estesa) | Microsoft Docs
ms.custom: 
ms.date: 03/04/2017
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
- srv_paramsetoutput
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_paramsetoutput
ms.assetid: f2810e19-e513-458b-8925-5756b6ee1313
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f2436a716d379cb9a5d9eef61d628b8ffed59720
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="srvparamsetoutput-extended-stored-procedure-api"></a>srv_paramsetoutput (API Stored procedure estesa)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] In alternativa, usare l'integrazione con CLR.  
  
 Imposta il valore di un parametro restituito. Questa funzione sostituisce la funzione **srv_paramset**.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
int srv_paramsetoutput (  
SRV_PROC *  
srvproc  
,  
int  
n  
,  
BYTE *  
pbData  
,  
ULONG   
cbLen  
,  
BOOL  
fNull   
);  
```  
  
## <a name="arguments"></a>Argomenti  
 *srvproc*  
 Handle per una connessione client.  
  
 *n*  
 Numero ordinale del parametro da impostare. Il primo parametro è 1.  
  
 *pbData*  
 Puntatore al valore dei dati da inviare di nuovo al client come parametro restituito della stored procedure.  
  
 *cbLen*  
 Lunghezza effettiva dei dati da restituire. Se il tipo di dati del parametro specifica i valori di una lunghezza costante e non consente valori Null (ad esempio, *srvbit* or *srvint1*), *cbLen* viene ignorato. Il valore 0 significa dati di lunghezza zero se *fNull* è FALSE.  
  
 *fNull*  
 Flag che indica se il valore del parametro restituito è NULL. Impostare questo flag su TRUE se il parametro deve essere impostato su NULL. Il valore predefinito è FALSE. Se *fNull* è impostato su TRUE, *cbLen* deve essere impostato su 0; in caso contrario la funzione avrà esito negativo.  
  
## <a name="returns"></a>Valori di codice restituiti  
 Se le informazioni sul parametro sono state impostate correttamente, viene restituito SUCCEED; in caso contrario, FAIL. FAIL viene restituito nei seguenti casi:  
  
-   Il parametro non è un parametro restituito.  
  
-   L'argomento *cbLen* non è valido.  
  
## <a name="remarks"></a>Osservazioni  
 **Nota sulla sicurezza** È necessario esaminare con attenzione il codice sorgente delle stored procedure estese e testare le DLL compilate prima di installarle in un server di produzione. Per informazioni sui test e sull'analisi della sicurezza, visitare questo [sito Web Microsoft](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
  
