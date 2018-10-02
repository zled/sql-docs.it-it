---
title: MSSQLSERVER_8621 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 8621 (Database Engine error)
ms.assetid: 67f59865-becd-4999-8bb0-90aedd7effbf
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1bae7c376307aee10024fba364ba1a2fe9eabd01
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47678209"
---
# <a name="mssqlserver8621"></a>MSSQLSERVER_8621
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|8621|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|OPTIMIZER_STACK_OVERFLOW_ERR|  
|Testo del messaggio|Spazio di stack esaurito durante l'ottimizzazione della query da parte di Query Processor. Semplificare la query.|  
  
## <a name="explanation"></a>Spiegazione  
La causa più probabile dell'errore risiede nelle dimensioni della query espansa, che sostituisce nella query originale le definizioni di ogni vista, colonna calcolata, funzione [!INCLUDE[tsql](../../includes/tsql-md.md)] ed espressione di tabella comune a cui fa riferimento, nonché di ogni operazione di propagazione, ad esempio l'aggiornamento di indici secondari, viste e trigger.  
  
Probabilmente la query presenta alcune dimensioni grandi, ad esempio il numero di tabelle a cui fanno riferimento le definizioni delle viste o un'espressione scalare di dimensioni molto estese.  
  
## <a name="user-action"></a>Azione dell'utente  
Semplificare la query suddividendola in più query secondo la dimensione più grande. Rimuovere innanzitutto qualsiasi elemento della query non strettamente necessario, quindi provare ad aggiungere una tabella temporanea e separare la query in due parti.  Non è sufficiente spostare semplicemente una parte della query in una subquery, funzione o espressione di tabella comune, poiché verrebbero ricombinate dal compilatore [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
