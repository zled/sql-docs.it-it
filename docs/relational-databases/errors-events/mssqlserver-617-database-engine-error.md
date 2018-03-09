---
title: MSSQLSERVER_617 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 617 (Database Engine error)
ms.assetid: 213545d9-08a7-4427-bfd1-8b7e16644281
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: aad0f7b77dbf806a9f8db57d134f5e662720988f
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver617"></a>MSSQLSERVER_617
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|617|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|NODESHASH|  
|Testo del messaggio|Impossibile trovare nella tabella hash il descrittore per l'ID di oggetto %ld nel database con ID %d durante il tentativo di annullare l'hashing. Voce mancante in una tabella di lavoro. Eseguire nuovamente la query. Se viene utilizzato un cursore, chiuderlo e riaprirlo.|  
  
## <a name="explanation"></a>Spiegazione  
SQL Server non è in grado di trovare la tabella di lavoro per una voce specifica.  
  
## <a name="user-action"></a>Azione dell'utente  
  
1.  Se viene utilizzato un cursore, chiuderlo e riaprirlo.  
  
2.  Eseguire nuovamente la query.  
  
