---
title: MSSQLSERVER_9001 | Microsoft Docs
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
- 9001 (Database Engine error)
ms.assetid: a54de936-90c6-4845-aa96-29d32f154601
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0ed271aa4c3be211d2ced1b20e8fc739f637514e
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver9001"></a>MSSQLSERVER_9001
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|9001|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|LOG_NOT_AVAIL|  
|Testo del messaggio|Il log per il database '%.*ls' non è disponibile. Controllare il registro eventi per i messaggi di errore correlati. Risolvere eventuali errori e riavviare il database.|  
  
## <a name="explanation"></a>Spiegazione  
Il log del database è stato messo offline. In genere questa situazione implica un errore irreversibile per cui è necessario riavviare il database.  
  
## <a name="user-action"></a>Azione dell'utente  
Diagnosticare altri errori e riavviare l'istanza di SQL Server qualora il riavvio non sia già stato eseguito automaticamente.  
  
