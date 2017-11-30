---
title: srv_paramname (API Stored procedure estesa) | Microsoft Docs
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: extended-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname: srv_paramname
apilocation: opends60.dll
apitype: DLLExport
dev_langs: C++
helpviewer_keywords: srv_paramname
ms.assetid: 1a53d707-7b06-49cc-a0df-ac727cfe953f
caps.latest.revision: "30"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4f8744349a69b8388d6a4f11a19b7e0014866398
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="srvparamname-extended-stored-procedure-api"></a>srv_paramname (API Stored procedure estesa)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Usare in alternativa l'integrazione CLR.  
  
 Restituisce il nome di un parametro di chiamata a una stored procedure remota.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DBCHAR * srv_paramname (  
SRV_PROC * srvproc,intn, int *len );  
```  
  
## <a name="arguments"></a>Argomenti  
 *srvproc*  
 Puntatore alla struttura SRV_PROC che rappresenta l'handle di una determinata connessione client. In questo caso, l'handle che ha ricevuto la chiamata alla stored procedure remota. La struttura contiene informazioni utilizzate dalla libreria dell'API Stored procedure estesa per gestire le comunicazioni e i dati tra l'applicazione e il client.  
  
 *n*  
 Indica il numero del parametro. Il primo parametro è 1.  
  
 *len*  
 Specifica un puntatore a una variabile **int** che contiene la lunghezza, espressa in byte, del nome del parametro. Se *len* è NULL, la lunghezza del nome del parametro della stored procedure remota non viene restituita.  
  
## <a name="returns"></a>Valori di codice restituiti  
 Puntatore a una stringa di caratteri con terminazione di tipo Null che contiene il nome del parametro. La lunghezza del nome del parametro viene archiviata in *len*. In assenza di un parametro in posizione *n* o di una stored procedure remota, restituisce NULL, *len* viene impostato su -1 e viene inviato un messaggio informativo di errore. Se il nome del parametro è NULL, *len* viene impostato su 0 e viene restituita una stringa vuota con terminazione di tipo Null.  
  
## <a name="remarks"></a>Osservazioni  
 Questa funzione ottiene il nome di un parametro di chiamata alla stored procedure remota. Quando viene effettuata una chiamata a una stored procedure remota con parametri, tali parametri possono essere passati per nome o per posizione (senza nome). Se invece viene effettuata con alcuni parametri passati per nome e altri passati per posizione, si verifica un errore. Il gestore SRV_RPC viene comunque chiamato, ma risulta che non sono presenti parametri e **srv_rpcparams** restituisce 0.  
  
> [!IMPORTANT]  
>  È necessario esaminare con attenzione il codice sorgente delle stored procedure estese e testare le DLL compilate prima di installarle in un server di produzione. Per informazioni sui test e sull'analisi della sicurezza, visitare questo [sito Web Microsoft](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
## <a name="see-also"></a>Vedere anche  
 [srv_rpcparams &#40;API delle stored procedure estese&#41;](../../relational-databases/extended-stored-procedures-reference/srv-rpcparams-extended-stored-procedure-api.md)  
  
  
