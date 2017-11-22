---
title: MSSQLSERVER_2511 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 2511 (Database Engine error)
ms.assetid: 9a00c0ed-eb4b-4fae-8016-192396006c37
caps.latest.revision: "12"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8b7c7da552aee4357d98e05597bffef3ca5f08ad
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver2511"></a>MSSQLSERVER_2511
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|2511|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|DBCC_KEYS_OUT_OF_ORDER|  
|Testo del messaggio|Errore di tabella: ID di oggetto %d, ID di indice %d, ID di partizione %I64d, ID di unità di allocazione %I64d (tipo %.*ls). Chiavi non ordinate alla pagina %S_PGID, slot %d e %d.|  
  
## <a name="explanation"></a>Spiegazione  
Nell'indice specificato sono state rilevate chiavi non ordinate. La pagina in cui sono contenute le chiavi può essere danneggiata.  
  
## <a name="user-action"></a>Azione dell'utente  
Ricompilare l'indice specificato utilizzando l'istruzione ALTER INDEX REBUILD.  
  
