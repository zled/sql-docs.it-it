---
title: srv_senddone (API Stored Procedure estesa) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
api_name:
- srv_senddone
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_senddone
ms.assetid: 1fc4f1d5-56d4-43f6-b5e4-0c0cc295cba3
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 51589cea0306f7a9fe3e4074c586c7c89892d9c9
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48157941"
---
# <a name="srvsenddone-extended-stored-procedure-api"></a>srv_senddone (API delle stored procedure estese)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Usare in alternativa l'integrazione CLR.  
  
 Invia messaggio di completamento dei risultati al client.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
int srv_senddone (  
SRV_PROC *  
srvproc  
,  
DBUSMALLINT   
status  
,  
DBUSMALLINT  
info  
,  
DBINT  
count   
);  
  
```  
  
## <a name="arguments"></a>Argomenti  
 *srvproc*  
 Puntatore alla struttura SRV_PROC che rappresenta l'handle di una determinata connessione client, in questo caso l'handle che ha ricevuto la richiesta del linguaggio. La struttura contiene informazioni utilizzate dalla libreria dell'API Stored procedure estesa per gestire le comunicazioni e i dati tra l'applicazione e il client.  
  
 *status*  
 Campo a 2 byte per vari flag di *status*. È possibile impostare più flag usando gli operatori logici AND e OR con i valori dei flag di *status*. Nella tabella seguente sono elencati i possibili flag di *status*.  
  
|Flag di stato|Description|  
|-----------------|-----------------|  
|SRV_DONE_COUNT|Il parametro *count* contiene un conteggio valido.|  
|SRV_DONE_ERROR|Il comando client corrente ha ricevuto un errore.|  
  
 *info*  
 Campo a 2 byte riservato. Impostare questo valore su 0.  
  
 *count*  
 Campo a 4 byte utilizzato per indicare un conteggio per il set di risultati corrente. Se il flag SRV_DONE_COUNT è impostato nel campo *status*, *count* include un conteggio valido.  
  
## <a name="returns"></a>Valori di codice restituiti  
 SUCCEED o FAIL  
  
## <a name="remarks"></a>Note  
 Una richiesta del client può provocare l'esecuzione da parte del server di alcuni comandi e la restituzione di alcuni set di risultati. Per ogni set di risultati, **srv_senddone** deve restituire un messaggio di completamento dei risultati al client.  
  
 Il campo *count* indica il numero di righe interessate da un comando. Se il campo *count* contiene un conteggio, il flag SRV_DONE_COUNT deve essere impostato nel campo *status*. Questa impostazione consente al client di distinguere tra un valore di *count* pari a 0 e un campo *count* inutilizzato.  
  
 Non chiamare **srv_senddone** dal gestore SRV_CONNECT.  
  
> [!IMPORTANT]  
>  È necessario esaminare con attenzione il codice sorgente delle stored procedure estese e testare le DLL compilate prima di installarle in un server di produzione. Per informazioni sui test e sull'analisi della sicurezza, visitare questo [sito Web Microsoft](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
  
