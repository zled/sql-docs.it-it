---
title: MSSQLSERVER_7916 | Microsoft Docs
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
helpviewer_keywords: 7916 (Database Engine error)
ms.assetid: 9bac3536-de14-4e98-84c2-bde9a59ba0d1
caps.latest.revision: "16"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 623e22492ef6cc668f1ddacdfa2d3a4974fc1336
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver7916"></a>MSSQLSERVER_7916
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|7916|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|DBCC2_REPAIR_RECORD|  
|Testo del messaggio|Correzione: record eliminato per l'oggetto con ID O_ID, indice con ID I_ID, partizione con ID PN_ID, unità allocazione con ID A_ID (tipo TYPE), a pagina P_ID, slot S_ID. Gli indici verranno ricompilati.|  
  
## <a name="explanation"></a>Spiegazione  
Messaggio informativo inviato da REPAIR che indica che il record specificato è stato eliminato dalla pagina.  
  
## <a name="user-action"></a>Azione dell'utente  
Nessuno  
  
