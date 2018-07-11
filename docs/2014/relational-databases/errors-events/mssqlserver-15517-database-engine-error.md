---
title: MSSQLSERVER_15517 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 15517 (Database Engine error)
ms.assetid: f94287f5-129f-4c52-9d34-62b996088001
caps.latest.revision: 5
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ebbc87a299cb55658c7a8506fa4a63a2e2d1d215
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37426470"
---
# <a name="mssqlserver15517"></a>MSSQLSERVER_15517
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID evento|15517|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|SEC_CANNOTEXECUTEASUSER|  
|Testo del messaggio|Non può essere eseguita come entità di database perché l'entità "*principal*" non esiste; questo tipo di entità non può essere rappresentato oppure non si ha l'autorizzazione.|  
  
## <a name="user-action"></a>Azione dell'utente  
 Utilizzare il nome di un'entità esistente oppure ottenere l'autorizzazione IMPERSONATE per tale entità.  
  
 L'errore 15517 si può verificare anche dopo l'esecuzione di un'operazione di collegamento e ripristino di un database da un utente diverso dal proprietario del database originale. Per risolvere il problema, impostare db_owner su un account di accesso nel server, eseguendo il comando indicato di seguito:  
  
```  
ALTER AUTHORIZATION ON DATABASE:: DBName TO [NewLogin]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [OLTP in memoria &#40;ottimizzazione per la memoria&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
