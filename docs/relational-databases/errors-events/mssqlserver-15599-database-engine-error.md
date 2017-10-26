---
title: MSSQLSERVER_15599 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 15599 (Database Engine error)
ms.assetid: 97e427a9-8587-46ea-954b-974b5df9c223
caps.latest.revision: 8
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: aa0d5c203907702e20ca9c780baad266b3def320
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver15599"></a>MSSQLSERVER_15599
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|15599|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|SEC_LOCAL_TEMP_AUDIT_PERMISSIONS|  
|Testo del messaggio|Impossibile impostare controllo e autorizzazioni in oggetti temporanei locali.|  
  
## <a name="explanation"></a>Spiegazione  
Il controllo e le autorizzazioni non hanno alcuno effetto quando si impostano oggetti temporanei locali o globali. Le istruzioni non restituiscono un errore e verranno eseguite correttamente, ma non hanno effetto.  
  
Questo comportamento non viene modificato. Tuttavia, a partire da [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], il messaggio ha lo scopo informativo di avvisare l'utente.  
  
## <a name="user-action"></a>Azione dell'utente  
Non è necessaria alcuna azione, ma è opportuno prendere in considerazione la rimozione delle istruzioni che tentano di impostare controllo o autorizzazioni sugli oggetti temporanei locali o globali.  
  

