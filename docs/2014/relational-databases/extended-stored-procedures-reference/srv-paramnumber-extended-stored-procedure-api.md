---
title: srv_paramnumber (API Stored procedure estesa) | Microsoft Docs
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
- srv_paramnumber
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_paramnumber
ms.assetid: d7a6dbff-71d9-4297-8a4f-bfd2876fe204
caps.latest.revision: 30
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c0037b53bb5454aa703a1d1c006c2ad4f49e99ad
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36063345"
---
# <a name="srvparamnumber-extended-stored-procedure-api"></a>srv_paramnumber (API delle stored procedure estese)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Usare in alternativa l'integrazione CLR.  
  
 Restituisce il numero di un parametro di chiamata a una stored procedure remota.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
int srv_paramnumber (  
SRV_PROC *  
srvproc  
,  
DBCHAR *  
name  
,   
int  
namelen   
);  
  
```  
  
## <a name="arguments"></a>Argomenti  
 *srvproc*  
 Puntatore alla struttura SRV_PROC che rappresenta l'handle di una determinata connessione client. In questo caso, l'handle che ha ricevuto la chiamata alla stored procedure remota. La struttura contiene informazioni utilizzate dalla libreria dell'API Stored procedure estesa per gestire le comunicazioni e i dati tra l'applicazione e il client.  
  
 *name*  
 Puntatore al parametro *name*.  
  
 *namelen*  
 Lunghezza di *name*. Se *name* è con terminazione Null, impostare *namelen* su SRV_NULLTERM.  
  
## <a name="returns"></a>Valori di codice restituiti  
 Numero di parametro del parametro denominato. Il primo parametro è 1. Se non è presente alcun parametro denominato *name* o alcuna stored procedure remota, viene restituito 0 e viene generato un messaggio.  
  
## <a name="remarks"></a>Remarks  
 Quando viene effettuata una chiamata a una stored procedure remota con parametri, tali parametri possono essere passati per nome o per posizione (senza nome). Se invece viene effettuata con alcuni parametri passati per nome e altri passati per posizione, si verifica un errore. Il gestore SRV_RPC viene comunque chiamato, ma risulta che non sono presenti parametri e **srv_rpcparams** restituisce 0.  
  
> [!IMPORTANT]  
>  È necessario esaminare con attenzione il codice sorgente delle stored procedure estese e testare le DLL compilate prima di installarle in un server di produzione. Per informazioni sui test e sull'analisi della sicurezza, visitare questo [sito Web Microsoft](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
## <a name="see-also"></a>Vedere anche  
 [srv_rpcparams &#40;API delle stored procedure estese&#41;](srv-rpcparams-extended-stored-procedure-api.md)  
  
  