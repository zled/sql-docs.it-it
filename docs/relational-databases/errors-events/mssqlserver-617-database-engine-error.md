---
title: MSSQLSERVER_617 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 617 (Database Engine error)
ms.assetid: 213545d9-08a7-4427-bfd1-8b7e16644281
caps.latest.revision: 14
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: be55b075e2abcbbe76031f23a4de27557766c167
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
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
  
