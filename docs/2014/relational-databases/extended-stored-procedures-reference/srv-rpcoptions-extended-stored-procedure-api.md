---
title: srv_rpcoptions (API Stored procedure estesa) | Microsoft Docs
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
- srv_rpcoptions
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_rpcoptions
ms.assetid: dbcce5d1-d5a1-4379-9597-04e43af5923d
caps.latest.revision: 30
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 085e3d0f0b51abaebc626e0caf74ff38f37e99a2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36064947"
---
# <a name="srvrpcoptions-extended-stored-procedure-api"></a>srv_rpcoptions (API delle stored procedure estese)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Usare in alternativa l'integrazione CLR.  
  
 Restituisce le opzioni di runtime per la stored procedure remota corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DBUSMALLINT srv_rpcoptions ( SRV_PROC *  
srvproc   
);  
  
```  
  
## <a name="arguments"></a>Argomenti  
 *srvproc*  
 Puntatore alla struttura SRV_PROC che rappresenta l'handle di una determinata connessione client. In questo caso, l'handle che ha ricevuto la stored procedure remota. La struttura contiene informazioni utilizzate dalla libreria di API delle stored procedure estese per gestire le comunicazioni e i dati tra l'applicazione e il client.  
  
## <a name="returns"></a>Valori di codice restituiti  
 Una bitmap che contiene i flag di esecuzione uniti in un'operazione con OR logico per la stored procedure remota corrente. Se non è presente alcuna stored procedure remota corrente, viene restituito 0 e viene generato un messaggio.  
  
## <a name="remarks"></a>Remarks  
 Nella tabella seguente viene descritto ciascun flag di esecuzione.  
  
|Flag di esecuzione|Description|  
|--------------------|-----------------|  
|SRV_NOMETADATA|Il client ha richiesto risultati senza informazioni sui metadati. Questo flag viene usato solo quando il client comunica con un'istanza di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Un'applicazione API delle stored procedure estese non può omettere le informazioni sui metadati.|  
|SRV_RECOMPILE|Il client ha richiesto di ricompilare la stored procedure remota prima di eseguirla. Questo flag non può essere applicato a un'applicazione API delle stored procedure estese.|  
  
> [!IMPORTANT]  
>  È necessario esaminare con attenzione il codice sorgente delle stored procedure estese e testare le DLL compilate prima di installarle in un server di produzione. Per informazioni sui test e sull'analisi della sicurezza, visitare questo [sito Web Microsoft](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
  