---
title: MSSQLSERVER_3417 | Microsoft Docs
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
- 3417 (Database Engine error)
ms.assetid: 005829c8-cf57-4828-818a-bbe8ee2e00f0
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8b3e6b210231423d694bebbe1afa6c51544ea55b
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver3417"></a>MSSQLSERVER_3417
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|3417|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|REC_BADMASTER|  
|Testo del messaggio|Impossibile recuperare il database master. Impossibile eseguire SQL Server. Ripristinare il master da un backup completo, correggerlo o ricompilarlo. Per ulteriori informazioni sulla ricompilazione del database master, vedere la documentazione online di SQL Server.|  
  
## <a name="explanation"></a>Spiegazione  
Non è possibile avviare il database **master** in SQL Server. Se non è possibile portare online il database **master** o **tempdb**, non è possibile eseguire SQL Server. Questo errore in genere è preceduto da altri errori. Esaminare i log degli errori per individuare la causa radice.  
  
## <a name="user-action"></a>Azione dell'utente  
Ripristinare il backup del database oppure correggere il database.  
  
