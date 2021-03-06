---
title: srv_setcollen (API Stored procedure estesa) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
apiname:
- srv_setcollen
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_setcollen
ms.assetid: 3c60f1c3-4562-463a-a259-12df172788bd
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 8dff06b97ddf1ad5b54581d373109bc3372a6dfc
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2018
ms.locfileid: "51657000"
---
# <a name="srvsetcollen-extended-stored-procedure-api"></a>srv_setcollen (API Stored procedure estesa)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Usare in alternativa l'integrazione CLR.  
  
 Specifica la lunghezza in byte della data corrente di una colonna a lunghezza variabile o di una colonna che consente valori Null.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
int srv_setcollen (  
SRV_PROC *  
srvproc  
,  
int   
column  
,  
int  
len   
);  
```  
  
## <a name="arguments"></a>Argomenti  
 *srvproc*  
 Puntatore alla struttura SRV_PROC che rappresenta l'handle di una determinata connessione client. La struttura contiene informazioni utilizzate dalla libreria dell'API Stored procedure estesa per gestire le comunicazioni e i dati tra l'applicazione e il client.  
  
 *column*  
 Indica il numero della colonna per la quale viene specificata la lunghezza dei dati. Le colonne sono numerate a partire da 1.  
  
 *len*  
 Indica la lunghezza in byte dei dati della colonna. Alla lunghezza 0 corrisponde un valore Null per i dati della colonna.  
  
## <a name="returns"></a>Valori di codice restituiti  
 SUCCEED o FAIL.  
  
## <a name="remarks"></a>Remarks  
 Ogni colonna della riga deve essere definita prima con **srv_describe**. La lunghezza della colonna dei dati viene impostata dall'ultima chiamata a **srv_describe** o **srv_setcollen**. Se viene modificata una riga dei dati a lunghezza variabile (dati con terminazione null), è necessario usare **srv_setcollen** per impostarli sulla nuova lunghezza prima di chiamare **srv_sendrow**. Per una colonna che consente valori Null è necessario che sia stato chiamato **srv_describe** con *desttype* impostato su un tipo di dati che consente valori Null (ad esempio SRVINTN) e che i dati Null siano stati specificati chiamando **srv_setcollen** con *len* impostato su 0. Quando si utilizza l'API Stored procedure estesa, non è possibile specificare dati di lunghezza zero.  
  
 Quando il tipo di dati della colonna è a lunghezza variabile, *len* non viene controllato. Questa funzione restituisce FAIL se chiamata per una colonna a lunghezza fissa.  
  
> [!IMPORTANT]  
>  È necessario esaminare con attenzione il codice sorgente delle stored procedure estese e testare le DLL compilate prima di installarle in un server di produzione. Per informazioni sui test e sull'analisi della sicurezza, visitare questo [sito Web Microsoft](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
## <a name="see-also"></a>Vedere anche  
 [srv_describe &#40;API Stored procedure estesa&#41;](../../relational-databases/extended-stored-procedures-reference/srv-describe-extended-stored-procedure-api.md)  
  
  
