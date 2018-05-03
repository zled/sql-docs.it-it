---
title: srv_rpcparams (API Stored procedure estesa) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: extended-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- srv_rpcparams
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_rpcparams
ms.assetid: 96a5e6f6-d320-4623-b96e-0a856e3abebb
caps.latest.revision: 30
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: f5f9fb4104518ff128e1f558668fb9cb9dea4e08
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="srvrpcparams-extended-stored-procedure-api"></a>srv_rpcparams (API delle stored procedure estese)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Usare in alternativa l'integrazione CLR.  
  
 Restituisce il numero di parametri per la chiamata alla stored procedure remota corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
int srv_rpcparams ( SRV_PROC *  
srvproc   
);  
```  
  
## <a name="arguments"></a>Argomenti  
 *srvproc*  
 Puntatore alla struttura SRV_PROC che rappresenta l'handle di una determinata connessione client. In questo caso, l'handle che ha ricevuto la stored procedure remota. La struttura contiene informazioni utilizzate dalla libreria dell'API Stored procedure estesa per gestire le comunicazioni e i dati tra l'applicazione e il client.  
  
## <a name="returns"></a>Valori di codice restituiti  
 Numero di parametri nella stored procedure remota. Se nella stored procedure remota non sono inclusi parametri o se non è presente una stored procedure remota corrente, viene restituito -1 e viene generato un messaggio di errore informativo.  
  
## <a name="remarks"></a>Remarks  
 Questa funzione restituisce il numero di parametri nella stored procedure remota corrente. La funzione viene in genere chiamata dalla stored procedure remota.  
  
 Quando viene effettuata una chiamata a una stored procedure remota con parametri, tali parametri possono essere passati per nome o per posizione (senza nome). Se la chiamata alla stored procedure è stata eseguita con alcuni parametri passati per nome e alcuni passati per posizione, si verifica un errore. Quando si verifica questo errore, viene chiamato il gestore delle stored procedure remote, ma non vengono ricevuti i parametri e **srv_rpcparams** restituisce 0.  
  
> [!IMPORTANT]  
>  È necessario esaminare con attenzione il codice sorgente delle stored procedure estese e testare le DLL compilate prima di installarle in un server di produzione. Per informazioni sui test e sull'analisi della sicurezza, visitare questo [sito Web Microsoft](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
  
