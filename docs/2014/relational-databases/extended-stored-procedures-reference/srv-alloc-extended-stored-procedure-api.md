---
title: srv_alloc (API Stored procedure estesa) | Microsoft Docs
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
- srv_alloc
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_alloc
ms.assetid: 91505c59-a273-452f-b71d-5e8205c21863
caps.latest.revision: 32
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9c821df66c6599dd3e7e3fecdff637d250f965c2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36063601"
---
# <a name="srvalloc-extended-stored-procedure-api"></a>srv_alloc (API delle stored procedure estese)
    
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
  
  