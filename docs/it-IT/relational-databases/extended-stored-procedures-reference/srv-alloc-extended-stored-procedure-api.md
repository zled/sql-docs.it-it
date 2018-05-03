---
title: srv_alloc (API Stored procedure estesa) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
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
- srv_alloc
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_alloc
ms.assetid: 91505c59-a273-452f-b71d-5e8205c21863
caps.latest.revision: 32
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 0f8cde2903b5e4e0f83af4372f1731b70f35e58e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="srvalloc-extended-stored-procedure-api"></a>srv_alloc (API delle stored procedure estese)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Usare in alternativa l'integrazione CLR.  
  
 Alloca memoria dinamicamente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
void * srv_alloc ( DBINT  
size  
);  
```  
  
## <a name="arguments"></a>Argomenti  
 *size*  
 Specifica il numero di byte da allocare.  
  
## <a name="returns"></a>Valori di codice restituiti  
 Un puntatore al nuovo spazio allocato. Se i byte di *size* non possono essere allocati, viene restituito un puntatore Null.  
  
## <a name="remarks"></a>Remarks  
 La funzione **srv_alloc** è equivalente alla funzione **GlobalAlloc** dell'API [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows. Normali funzioni di gestione della memoria di runtime del linguaggio C dell'API Windows possono essere utilizzate in un'applicazione API di stored procedure estese.  
  
> [!IMPORTANT]  
>  È necessario esaminare con attenzione il codice sorgente delle stored procedure estese e testare le DLL compilate prima di installarle in un server di produzione. Per informazioni sui test e sull'analisi della sicurezza, visitare questo [sito Web Microsoft](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
  
